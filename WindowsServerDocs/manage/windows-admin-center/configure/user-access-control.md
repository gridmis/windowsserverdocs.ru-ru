---
title: Настройка управления доступом и разрешениями на уровне пользователей
description: Узнайте, как настроить управление доступом и разрешениями на уровне пользователей с помощью Active Directory или Azure AD (проект Honolulu).
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 06/07/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 39af45506ff7023cebe437992e90f6d4ec051333
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79323596"
---
# <a name="configure-user-access-control-and-permissions"></a>Настройка управления доступом и разрешениями на уровне пользователей

> Применяется к: Windows Admin Center, ознакомительная версия Windows Admin Center

Если вы еще не сделали этого, ознакомьтесь с [параметрами контроля доступом пользователей в Windows Admin Center](../plan/user-access-options.md)

> [!NOTE]
> В средах рабочей группы или в доменах, не являющихся доверенными, доступ на основе групп в Windows Admin Center не поддерживается.

## <a name="gateway-access-role-definitions"></a>Определения ролей доступа к шлюзу

Существует две роли для доступа к службе шлюза Windows Admin Center.

**Пользователи шлюза** могут подключаться к службе шлюза Windows Admin Center, чтобы через него управлять серверами, но не могут изменять разрешения доступа и механизм проверки подлинности, используемый для аутентификации шлюза.

**Администраторы шлюза** могут настраивать доступ, а также способ выполнения проверки подлинности для пользователей на шлюзе. Просматривать и настраивать параметры доступа в Windows Admin Center могут только администраторы шлюза. Локальные администраторы на компьютере шлюза всегда являются администраторами службы шлюза Windows Admin Center.

> [!NOTE]
> Доступ к шлюзу не подразумевает доступ к управляемым серверам, отображаемым шлюзом. Для управления целевым сервером подключающийся пользователь должен использовать учетные данные (через переданные учетные данные Windows или учетные данные, предоставленные в сеансе Windows Admin Center с помощью действия **Управлять как**) с административным доступом к этому целевому серверу.

## <a name="active-directory-or-local-machine-groups"></a>Active Directory или группы локальных компьютеров

По умолчанию для управления доступом к шлюзу используются Active Directory или группы локальных компьютеров. При наличии домена Active Directory доступом пользователей и администраторов шлюза можно управлять из интерфейса Windows Admin Center.

На вкладке **Пользователи** можно указать пользователя, которому нужно предоставить доступ к Windows Admin Center в качестве пользователя шлюза. По умолчанию, и если не указать группу безопасности, доступ будет иметь любой пользователь, обращающийся к URL-адресу шлюза. После добавления одной или нескольких групп безопасности в список пользователей доступ будет ограничен членами этих групп.

Если в вашей среде не используется домен Active Directory, доступ контролируется локальными группами `Users` и `Administrators` на компьютере шлюза Windows Admin Center.

### <a name="smartcard-authentication"></a>Проверка подлинности смарт-карты

Вы можете принудительно применить **проверку подлинности смарт-карты**, указав дополнительную _необходимую_ группу для групп безопасности на основе смарт-карты. После добавления группы безопасности на основе смарт-карты пользователь может получить доступ к службе Windows Admin Center, только если он является членом любой группы безопасности и группы смарт-карты, включенной в список пользователей.

На вкладке **Администраторы** можно указать пользователя, которому нужно предоставить доступ к Windows Admin Center в качестве администратора шлюза. Локальная группа администраторов на компьютере всегда будет иметь полный доступ администратора и ее не можно удалить из списка. Добавляя группы безопасности, вы даете членам этих групп разрешения на изменение параметров шлюза Windows Admin Center. Список администраторов поддерживает проверку подлинности смарт-карты такую же, как и для списка пользователей: с условием AND и для группы безопасности и для группы смарт-карт.

## <a name="azure-active-directory"></a>Azure Active Directory

Если ваша организация использует Azure Active Directory (Azure AD), вы можете добавить **дополнительный** уровень безопасности в Windows Admin Center, требуя для доступа к шлюзу проверку подлинности Azure AD. Чтобы обеспечить доступ к Windows Admin Center, **учетной записи Windows** пользователя также следует предоставить доступ к серверу шлюза (даже при использовании проверки подлинности Azure AD). При использовании Azure AD управление правами доступа пользователя и администратора Windows Admin Center осуществляется на портале Azure, а не из пользовательского интерфейса Windows Admin Center.

### <a name="accessing-windows-admin-center-when-azure-ad-authentication-is-enabled"></a>Доступ к Windows Admin Center при включенной проверке подлинности Azure AD

В зависимости от используемого браузера некоторые пользователи, обращающиеся к Windows Admin Center с настроенной проверкой подлинности Azure AD, получат дополнительный запрос **из браузера**, в котором нужно будет указать данные учетной записи Windows для компьютера, на котором установлен Windows Admin Center. После ввода этих данных пользователи увидят дополнительный запрос на проверку подлинности Azure Active Directory, для которого требуются учетные данные учетной записи Azure, которой предоставлен доступ к приложению Azure AD в Azure.

> [!NOTE]
> Пользователи, учетная запись Windows которых имеет **права администратора** на компьютере шлюза, не будут получать запрос на проверку подлинности Azure AD.

### <a name="configuring-azure-active-directory-authentication-for-windows-admin-center-preview"></a>Настройка проверки подлинности Azure Active Directory для Windows Admin Center (Предварительная версия)

В Windows Admin Center последовательно выберите **Параметры** > **Доступ** и используйте выключатель, чтобы включить параметр "Use Azure Active Directory to add a layer of security to the gateway" (Использовать Azure Active Directory для добавления уровня безопасности в шлюз). Если вы не зарегистрировали шлюз в Azure, вам будет предложено сделать это в данный момент.

По умолчанию все участники клиента Azure AD имеют доступ пользователей к службе шлюза Windows Admin Center. Доступ администратора к шлюзу Windows Admin Center имеют только локальные администраторы на компьютере шлюза. Обратите внимание, что права локальных администраторов на компьютере шлюза нельзя ограничить. Локальные администраторы могут выполнять любые действия независимо от того, используется ли Azure AD для проверки подлинности или нет.

Если вы хотите предоставить доступ к службе Windows Admin Center определенным пользователям Azure AD, группам пользователей шлюза или администраторам шлюза, необходимо выполнить следующие действия.

1.  Перейдите в приложение Azure AD Windows Admin Center на портале Azure, используя гиперссылку, указанную в Параметрах доступа. Примечание. Эта гиперссылка доступна, только если включена проверка подлинности Azure Active Directory. 
    -   Приложение также можно найти на портале Azure, перейдя в **Azure Active Directory** > **Корпоративные приложения** > **Все приложения** и выполнив поиск по фразе **WindowsAdminCenter** (приложение Azure AD будет называться WindowsAdminCenter-<gateway name>). Если поиск не дает результатов, убедитесь, что для **Показать** задано значение **Все приложения**, а для **Состояние приложения**, а — **Любой** и нажмите кнопку "Применить", а затем повторите поиск. Найдя приложение, перейдите в раздел **Пользователи и группы**
2.  На вкладке "Свойства" задайте для параметра **Требуется назначение пользователей** значение "Да".
    После этого доступ к шлюзу Windows Admin Center смогут получить только участники, перечисленные на вкладке **Пользователи и группы**.
3.  На вкладке "Пользователи и группы" выберите **Добавить пользователя**. Для каждого добавляемого пользователя или группы необходимо назначить роль пользователя или администратора шлюза.

После включения проверки подлинности Azure AD служба шлюза перезапустится и вам потребуется обновить браузер. Вы можете в любое время обновить доступ пользователя к приложению SME Azure AD на портале Azure.

При попытке доступа к URL-адресу шлюза Windows Admin Center пользователям будет предложено войти, используя удостоверение Azure Active Directory. Помните, что пользователи также должны быть членами локальных "Пользователей" на сервере шлюза для доступа к центру администрирования Windows Admin Center.

Пользователи и администраторы могут просматривать текущую учетную запись, с которой они совершили вход, а также выйти из этой учетной записи Azure AD с вкладки **Учетная запись** в параметрах Windows Admin Center.

### <a name="configuring-azure-active-directory-authentication-for-windows-admin-center"></a>Настройка проверки подлинности Azure Active Directory для Windows Admin Center

[Чтобы настроить проверку подлинности Azure AD, необходимо сначала зарегистрировать шлюз в Azure](azure-integration.md) (это необходимо сделать только один раз для шлюза Windows Admin Center). На этом этапе создается приложение Azure AD, с помощью которого вы можете управлять доступом пользователей шлюза и администраторов шлюза.

Если вы хотите предоставить доступ к службе Windows Admin Center определенным пользователям Azure AD, группам пользователей шлюза или администраторам шлюза, необходимо выполнить следующие действия.

1.  Перейдите к приложению SME Azure AD на портале Azure. 
    -   Если щелкнуть **Изменить контроль доступа**, а затем выбрать **Azure Active Directory** из раздела параметров доступа Windows Admin Center, можно использовать гиперссылку, предоставленную в пользовательском интерфейсе, для доступа к приложению Azure AD на портале Azure. Эта гиперссылка также доступна в параметрах доступа после нажатия кнопки "Сохранить" и выбора Azure AD в качестве поставщика удостоверений управления доступом.
    -   Приложение также можно найти на портале Azure, перейдя в **Azure Active Directory** > **Корпоративные приложения** > **Все приложения** и выполнив поиск по фразе **SME** (приложение Azure AD будет называться SME-<gateway>). Если поиск не дает результатов, убедитесь, что для **Показать** задано значение **Все приложения**, а для **Состояние приложения**, а — **Любой** и нажмите кнопку "Применить", а затем повторите поиск. Найдя приложение, перейдите в раздел **Пользователи и группы**
2.  На вкладке "Свойства" задайте для параметра **Требуется назначение пользователей** значение "Да".
    После этого доступ к шлюзу Windows Admin Center смогут получить только участники, перечисленные на вкладке **Пользователи и группы**.
3.  На вкладке "Пользователи и группы" выберите **Добавить пользователя**. Для каждого добавляемого пользователя или группы необходимо назначить роль пользователя или администратора шлюза.

Как только вы сохраните контроль доступа Azure AD в панели **Изменить контроль доступа**, служба шлюза перезапустится и вам потребуется обновить свой браузер. Вы можете в любое время обновить доступ пользователя к приложению Windows Admin Center Azure AD на портале Azure. 

При попытке доступа к URL-адресу шлюза Windows Admin Center пользователям будет предложено войти, используя удостоверение Azure Active Directory. Помните, что пользователи также должны быть членами локальных "Пользователей" на сервере шлюза для доступа к центру администрирования Windows Admin Center. 

Используя вкладку **Azure** в общих параметрах Windows Admin Center, пользователи и администраторы могут просматривать текущую учетную запись, с которой они совершили вход, а также выйти из этой учетной записи Azure AD.

### <a name="conditional-access-and-multi-factor-authentication"></a>Условный доступ и многофакторная проверка подлинности

Одним из преимуществ использования Azure AD в качестве дополнительного уровня безопасности для контроля доступа к шлюзу Windows Admin Center является то, что вы можете использовать эффективные функции безопасности Azure AD, такие как условный доступ и многофакторная проверка подлинности. 

[Краткое руководство. Требование Многофакторной идентификации для конкретных приложений с помощью условного доступа Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)

## <a name="configure-single-sign-on"></a>Настройте единый вход

**Единый вход при развертывании в качестве службы в Windows Server**

После установки Windows Admin Center в Windows 10 все готово к использованию единого входа. Однако если вы собираетесь использовать Windows Admin Center в Windows Server, то перед использованием единого входа необходимо настроить в среде некоторую форму делегирования Kerberos. Делегирование настраивает компьютер шлюза как доверенный для делегирования к целевому узлу. 

Используйте следующий пример PowerShell, чтобы настроить [ограниченное делегирование на основе ресурсов](https://docs.microsoft.com/windows-server/security/kerberos/kerberos-constrained-delegation-overview) в вашей среде. В этом примере показано, как настроить Windows Server [node01.contoso.com] для принятия делегирования из шлюза Windows Admin Center [wac.contoso.com] в домене contoso.com.

```powershell
Set-ADComputer -Identity (Get-ADComputer node01) -PrincipalsAllowedToDelegateToAccount (Get-ADComputer wac)
```

Чтобы удалить эту связь, выполните следующий командлет:

```powershell
Set-ADComputer -Identity (Get-ADComputer node01) -PrincipalsAllowedToDelegateToAccount $null
```

## <a name="role-based-access-control"></a>Управление доступом на основе ролей

Управление доступом на основе ролей позволяет предоставлять пользователям ограниченный доступ к компьютеру, не делая их полными локальными администраторами.
[Role-based access control](../plan/user-access-options.md#role-based-access-control) (Управление доступом на основе ролей)

Настройка RBAC состоит из 2 шагов: включения поддержки на целевых компьютерах и назначения пользователям соответствующих ролей.

> [!TIP]
> Убедитесь, что у вас есть права локального администратора на компьютерах, для которых вы настраиваете поддержку управления доступом на основе ролей.

### <a name="apply-role-based-access-control-to-a-single-machine"></a>Применение управления доступом на основе ролей к одному компьютеру

Модель развертывания на одном компьютере идеально подходит для простых сред, в которых управление нужно представить только нескольким компьютерам.
Настройка компьютера с поддержкой управления доступом на основе ролей приведет к следующим изменениям:

-   Модули PowerShell с функциями, необходимыми для Windows Admin Center, будут установлены на системный диск в `C:\Program Files\WindowsPowerShell\Modules`. Все модули будут начинаться с **Microsoft.Sme**
-   Desired State Configuration выполняет одноразовую настройку для конфигурации конечной точки профиля "Достаточно для администрирования" на компьютере с именем **Microsoft.Sme.PowerShell**. Эта конечная точка определяет 3 роли, используемые Windows Admin Center, и при подключении к нему пользователя будет запускаться как временный локальный администратор.
-   Чтобы управлять, каким пользователям назначен доступ к каким ролям, будут созданы 3 новые локальные группы:
    -   Администраторы Windows Admin Center
    -   Администраторы Hyper-V Windows Admin Center
    -   Читатели Windows Admin Center

Чтобы включить поддержку управления доступом на основе ролей на одном компьютере, выполните следующие действия.

1.  Откройте Windows Admin Center и подключитесь к компьютеру, который нужно настроить для управления доступом на основе ролей, используя на целевом компьютере учетную запись с правами локального администратора.
2.  В инструменте **Обзор** щелкните **Настройки** > **Контроль доступа на основе ролей**.
3.  Щелкните **Применить** в нижней части страницы, чтобы включить на целевом компьютере поддержку управления доступом на основе ролей. Процесс приложения включает копирование скриптов PowerShell и вызов конфигурации (с помощью Desired State Configuration PowerShell) на целевом компьютере. Выполнение может занять до 10 минут, и приведет к перезапуску WinRM. Это приведет к временному отключению пользователей Windows Admin Center, PowerShell и WMI.
4.  Обновите страницу, чтобы проверить состояние управления доступом на основе ролей. Когда оно будет готово к использованию, состояние изменится на **Применено**.

После применения конфигурации вы можете назначить пользователям приведенные ниже роли.

1.  Откройте средство **Локальные пользователи и группы** и перейдите на вкладку **Группы**.
2.  Выберите группу **Читатели Windows Admin Center**.
3.  В нижней части панели *Детали* нажмите **Добавить пользователя** и введите имя пользователя или группы безопасности, для которых следует настроить доступ к серверу через Windows Admin Center только для чтения. Пользователи и группы могут поступать с локального компьютера или домена Active Directory.
4.  Повторите шаги 2-3 для групп **Администраторы Hyper-V Windows Admin Center** и **Администраторы Windows Admin Center**.

Вы также можете последовательно заполнять эти группы по всему домену, настраивая объект групповой политики с помощью параметра [Restricted Groups Policy Setting](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc756802%28v=ws.10%29) (Настройка политики групп с ограниченным доступом).

### <a name="apply-role-based-access-control-to-multiple-machines"></a>Применение управления доступом на основе ролей к нескольким компьютерам

При развертывании на крупном предприятии вы можете использовать существующие средства автоматизации для распространения функции управления доступом на основе ролей на компьютеры, скачав пакет конфигурации со шлюза Windows Admin Center.
Пакет конфигурации предназначен для использования с Desired State Configuration PowerShell, но его можно адаптировать для работы с предпочтительным решением для автоматизации.

#### <a name="download-the-role-based-access-control-configuration"></a>Скачивание конфигурации управления доступом на основе ролей

Чтобы загрузить пакет конфигурации управления доступом на основе ролей, необходимо иметь доступ к Windows Admin Center и командной строке PowerShell.

Если вы используете шлюз Windows Admin Center в Windows Server в режиме службы, используйте следующую команду, чтобы скачать пакет конфигурации.
Не забудьте обновить адрес шлюза, указав подходящий для своей среды.

```powershell
$WindowsAdminCenterGateway = 'https://windowsadmincenter.contoso.com'
Invoke-RestMethod -Uri "$WindowsAdminCenterGateway/api/nodes/all/features/jea/endpoint/export" -Method POST -UseDefaultCredentials -OutFile "~\Desktop\WindowsAdminCenter_RBAC.zip"
```

Если вы используете шлюз Windows Admin Center на компьютере с Windows 10, выполните следующую команду:

```powershell
$cert = Get-ChildItem Cert:\CurrentUser\My | Where-Object Subject -eq 'CN=Windows Admin Center Client' | Select-Object -First 1
Invoke-RestMethod -Uri "https://localhost:6516/api/nodes/all/features/jea/endpoint/export" -Method POST -Certificate $cert -OutFile "~\Desktop\WindowsAdminCenter_RBAC.zip"
```

При развертывании ZIP-архива вы увидите следующую структуру папок:

- InstallJeaFeatures.ps1
- JustEnoughAdministration (каталог)
- Модули (каталог)
    - Microsoft.SME.\* (каталоги)
    - WindowsAdminCenter.Jea (каталог)

Чтобы настроить поддержку управления доступом на основе ролей на узле, необходимо выполнить следующие действия.

1.  Скопируйте JustEnoughAdministration, Microsoft.SME.\* и модули WindowsAdminCenter.Jea в каталог модуля PowerShell на целевом компьютере. Как правило, они расположены в `C:\Program Files\WindowsPowerShell\Modules`.
2.  Обновите файл **InstallJeaFeature.ps1** в соответствии с требуемой конфигурацией для конечной точки RBAC.
3.  Запустите InstallJeaFeature.ps1, чтобы скомпилировать ресурс DSC.
4.  Разверните конфигурацию DSC на всех компьютерах, чтобы применить ее.

В следующем разделе объясняется, как это сделать с помощью удаленного взаимодействия PowerShell.

#### <a name="deploy-on-multiple-machines"></a>Развертывание на нескольких компьютерах

Чтобы развернуть конфигурацию, загруженную на несколько компьютеров, необходимо обновить скрипт **InstallJeaFeatures.ps1**, чтобы включить соответствующие группы безопасности для среды, скопировать файлы на каждый из компьютеров и вызвать скрипты конфигурации.
Для этого можно использовать предпочтительные средства автоматизации, однако в этой статье основное внимание уделяется чистому подходу на основе PowerShell.

По умолчанию скрипт конфигурации будет создавать локальные группы безопасности на компьютере, чтобы управлять доступом к каждой из ролей.
Это подходит для компьютеров, присоединенных к рабочей группе и доменам, но если развертывание выполняется в среде только для домена, вам может потребоваться напрямую связать группу безопасности домена с каждой ролью.
Чтобы обновить конфигурацию для использования групп безопасности домена, откройте **InstallJeaFeatures.ps1** и внесите следующие изменения:

1.  Удалите из файла 3 ресурсы **группы**:
    1.  "Группа MS-Readers-Group"
    2.  "Группа MS-Hyper-V-Administrators-Group"
    3.  "Группа MS-Administrators-Group"
2.  Удалите 3 ресурса группы из свойства JeaEndpoint **DependsOn**
    1.  "[Group]MS-Readers-Group"
    2.  "[Group]MS-Hyper-V-Administrators-Group"
    3.  "[Group]MS-Administrators-Group"
3.  Измените имена групп в свойстве JeaEndpoint **RoleDefinitions** на нужные группы безопасности. Например, если у вас есть группа безопасности *CONTOSO\MyTrustedAdmins*, которой нужно назначить доступ с ролью администраторов Windows Admin Center, измените `'$env:COMPUTERNAME\Windows Admin Center Administrators'` на `'CONTOSO\MyTrustedAdmins'`. Ниже перечислены три строки, которые необходимо обновить.
    1.  '$env:COMPUTERNAME\Windows Admin Center Administrators'
    2.  '$env:COMPUTERNAME\Windows Admin Center Hyper-V Administrators'
    3.  '$env:COMPUTERNAME\Windows Admin Center Readers'

> [!NOTE]
> Обязательно используйте уникальные группы безопасности для каждой роли. Если одна и та же группа безопасности назначена нескольким ролям, настройка завершится ошибкой.

Затем в конце файла **InstallJeaFeatures.ps1** добавьте в нижнюю часть скрипта следующие строки PowerShell:

```powershell
Copy-Item "$PSScriptRoot\JustEnoughAdministration" "$env:ProgramFiles\WindowsPowerShell\Modules" -Recurse -Force
$ConfigData = @{
    AllNodes = @()
    ModuleBasePath = @{
        Source = "$PSScriptRoot\Modules"
        Destination = "$env:ProgramFiles\WindowsPowerShell\Modules"
    }
}
InstallJeaFeature -ConfigurationData $ConfigData | Out-Null
Start-DscConfiguration -Path "$PSScriptRoot\InstallJeaFeature" -JobName "Installing JEA for Windows Admin Center" -Force
```

Наконец, вы можете скопировать папку с модулями, ресурсом DSC и конфигурацией на каждый целевой узел и запустить скрипт **InstallJeaFeature.ps1**.
Чтобы сделать это удаленно с рабочей станции администратора, можно выполнить следующие команды:

```powershell
$ComputersToConfigure = 'MyServer01', 'MyServer02'

$ComputersToConfigure | ForEach-Object {
    $session = New-PSSession -ComputerName $_ -ErrorAction Stop
    Copy-Item -Path "~\Desktop\WindowsAdminCenter_RBAC\JustEnoughAdministration\" -Destination "$env:ProgramFiles\WindowsPowerShell\Modules\" -ToSession $session -Recurse -Force
    Copy-Item -Path "~\Desktop\WindowsAdminCenter_RBAC" -Destination "$env:TEMP\WindowsAdminCenter_RBAC" -ToSession $session -Recurse -Force
    Invoke-Command -Session $session -ScriptBlock { Import-Module JustEnoughAdministration; & "$env:TEMP\WindowsAdminCenter_RBAC\InstallJeaFeature.ps1" } -AsJob
    Disconnect-PSSession $session
}
```
