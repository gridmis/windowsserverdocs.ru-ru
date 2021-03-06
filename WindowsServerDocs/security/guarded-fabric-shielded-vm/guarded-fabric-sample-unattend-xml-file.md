---
title: Создание специализированного файла ответов ОС
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 299aa38e-28d2-4cbe-af16-5b8c533eba1f
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 4920f9a90bd0190d390a9d35b3d265023d69efac
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386501"
---
# <a name="create-os-specialization-answer-file"></a>Создание специализированного файла ответов ОС

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

При подготовке к развертыванию экранированных виртуальных машин может потребоваться создать файл ответов специализации операционной системы. В Windows этот файл обычно называется файлом unattend. XML. Это можно сделать с помощью функции **New-шиелдингдатаансверфиле** Windows PowerShell. Затем можно использовать файл ответов при создании экранированных виртуальных машин из шаблона с помощью System Center Virtual Machine Manager (или любого другого контроллера структуры).

Общие рекомендации по использованию файлов автоматической установки для экранированных виртуальных машин см. [в разделе Создание файла ответов](guarded-fabric-tenant-creates-shielding-data.md#create-an-answer-file).
 
## <a name="downloading-the-new-shieldingdataanswerfile-function"></a>Скачивание функции New-Шиелдингдатаансверфиле

Функцию **New-шиелдингдатаансверфиле** можно получить из [коллекция PowerShell](https://aka.ms/gftools). Если компьютер подключен к Интернету, его можно установить из PowerShell с помощью следующей команды:

```powershell
Install-Module GuardedFabricTools -Repository PSGallery -MinimumVersion 1.0.0
```

Вывод `unattend.xml` можно упаковать в данные экранирования вместе с дополнительными артефактами, чтобы их можно было использовать для создания экранированных виртуальных машин из шаблонов.

В следующих разделах показано, как можно использовать параметры функции для файла `unattend.xml`, содержащего различные параметры.

- [Базовый файл ответов Windows](#basic-windows-answer-file)
- [Файл ответов Windows с присоединением к домену](#windows-answer-file-with-domain-join)
- [Файл ответов Windows со статическими IPv4-адресами](#windows-answer-file-with-static-ipv4-addresses)
- [Файл ответов Windows с пользовательским языковым стандартом](#windows-answer-file-with-a-custom-locale)
- [Основной файл ответов Linux](#basic-linux-answer-file)

## <a name="basic-windows-answer-file"></a>Базовый файл ответов Windows

Следующие команды создают файл ответов Windows, который просто задает пароль учетной записи администратора и имя узла.
Сетевые адаптеры виртуальной машины будут использовать DHCP для получения IP-адресов, а виртуальная машина не будет присоединена к домену Active Directory.
При появлении запроса на ввод учетных данных администратора укажите требуемое имя пользователя и пароль.
Используйте "Администратор" для имени пользователя, если вы хотите настроить встроенную учетную запись администратора.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred
```

## <a name="windows-answer-file-with-domain-join"></a>Файл ответов Windows с присоединением к домену

Следующие команды создают файл ответов Windows, который присоединяет экранированную виртуальную машину к домену Active Directory.
Сетевые адаптеры виртуальной машины будут использовать DHCP для получения IP-адресов.

В первом запросе учетных данных будет запрашиваться информация об учетной записи локального администратора.
Используйте "Администратор" для имени пользователя, если вы хотите настроить встроенную учетную запись администратора.

Во втором запросе учетных данных будет предложено ввести учетные данные, которые имеют право присоединить компьютер к домену Active Directory.

Не забудьте изменить значение параметра-имя_домена на полное доменное имя домена Active Directory.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"
$domainCred = Get-Credential -Message "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -DomainName 'my.contoso.com' -DomainJoinCredentials $domainCred
```
## <a name="windows-answer-file-with-static-ipv4-addresses"></a>Файл ответов Windows со статическими IPv4-адресами

Приведенные ниже команды создают файл ответов Windows, который использует статические IP-адреса, предоставленные диспетчером структуры в процессе развертывания, например System Center Virtual Machine Manager.

Virtual Machine Manager предоставляет три компонента для статического IP-адреса с помощью пула IP-адресов: IPv4-адрес, IPv6-адрес, адрес шлюза и адрес DNS. Если требуется включить дополнительные поля или запрашивать пользовательскую конфигурацию сети, необходимо вручную изменить файл ответов, созданный сценарием.

На следующих снимках экрана показаны пулы IP-адресов, которые можно настроить в Virtual Machine Manager. Эти пулы необходимы, если вы хотите использовать статический IP-адрес.

В настоящее время функция поддерживает только один DNS-сервер. Параметры DNS будут выглядеть следующим образом:

![Настройка DNS-сервера со статическим пулом IP-адресов](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-dns-settings.png)

Вот как будет выглядеть сводка по созданию пула статических IP-адресов. Вкратце, необходимо иметь только один сетевой маршрут, один шлюз и один DNS-сервер, и необходимо указать IP-адрес.

![Сводка по созданию пула статических IP-адресов](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-summary.png)

Необходимо настроить сетевой адаптер для виртуальной машины. На следующем снимке экрана показано, где задать эту конфигурацию и как переключить ее на статический IP-адрес.

![Настройка оборудования для использования статического IP-адреса](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-network-adapter-settings.png)

Затем можно использовать параметр `-StaticIPPool`, чтобы включить статические IP-элементы в файл ответов. Параметры `@IPAddr-1@`, `@NextHop-1-1@` и `@DNSAddr-1-1@` в файле ответов будут заменены реальными значениями, указанными в Virtual Machine Manager во время развертывания.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -StaticIPPool IPv4Address
```

## <a name="windows-answer-file-with-a-custom-locale"></a>Файл ответов Windows с пользовательским языковым стандартом

Следующие команды создают файл ответов Windows с настраиваемым языковым стандартом.

При появлении запроса на ввод учетных данных администратора укажите требуемое имя пользователя и пароль.
Используйте "Администратор" для имени пользователя, если вы хотите настроить встроенную учетную запись администратора.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"
$domainCred = Get-Credential -Message "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -Locale es-ES
```

## <a name="basic-linux-answer-file"></a>Основной файл ответов Linux

Начиная с Windows Server версии 1709, вы можете запускать определенные гостевые ОС Linux в экранированных виртуальных машинах.
Если вы используете Агент System Center Virtual Machine Manager Linux для специализации этих виртуальных машин, командлет New-Шиелдингдатаансверфиле может создать для него совместимые файлы ответов.

В файле ответов Linux, как правило, вы включаете корневой пароль, корневой ключ SSH и, при необходимости, сведения о пуле статических IP-адресов.
Перед выполнением приведенного ниже сценария замените путь к общедоступной половине ключа SSH.

```powershell
$rootPassword = Read-Host -Prompt "Root password" -AsSecureString

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -RootPassword $rootPassword -RootSshKey '~\.ssh\id_rsa.pub'
```

## <a name="see-also"></a>См. также

- [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
