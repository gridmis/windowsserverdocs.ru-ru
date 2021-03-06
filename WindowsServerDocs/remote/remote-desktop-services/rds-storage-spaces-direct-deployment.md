---
title: Развертывание двухузлового масштабируемого файлового сервера (SOFS) Локальных дисковых пространств для хранения дисков UPD
description: Узнайте, как использовать Локальные дисковые пространства с RDS.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1099f21d-5f07-475a-92dd-ad08bc155da1
author: haley-rowland
ms.author: harowl
ms.date: 07/17/2018
manager: scottman
ms.openlocfilehash: e320f0eb04e81d80f7288d4d7b20b5369e209932
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79319988"
---
# <a name="deploy-a-two-node-storage-spaces-direct-scale-out-file-server-for-upd-storage-in-azure"></a>Развертывание масштабируемого файлового сервера Локальных дисковых пространств с двумя узлами для хранения дисков UPD в Azure

>Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016

Службам удаленных рабочих столов (RDS) требуется присоединенный к домену файловый сервер для хранения дисков профилей пользователей (UPD). Для развертывания присоединенного к домену высокодоступного масштабируемого файлового сервера (SOFS) в Azure используйте Локальные дисковые пространства с Windows Server 2016. Если вы не работали с дисками UPD или службами удаленных рабочих столов, ознакомьтесь с разделом [Введение в службы удаленных рабочих столов](welcome-to-rds.md).

> [!NOTE] 
> Корпорация Майкрософт недавно опубликовала [шаблон Azure для развертывания масштабируемого файлового сервера Локальных дисковых пространств](https://azure.microsoft.com/documentation/templates/301-storage-spaces-direct/). Вы можете использовать шаблон для создания развертывания или следовать инструкциям в этой статье. 

Мы рекомендуем развертывать сервер SOFS на виртуальных машинах серии DS и дисках данных хранилища ценовой категории "Премиум", настроив на всех виртуальных машинах одинаковое число и размер дисков данных. Вам потребуются как минимум две учетные записи хранения. 

Для небольших развертываний мы рекомендуем двухузловой кластер с облачным свидетелем, где используется зеркальное отображение тома в 2 копии. Чтобы увеличить масштаб небольших развертываний, добавляйте диски данных. Чтобы увеличить масштаб более крупных развертываний, добавляйте узлы (виртуальные машины). 

Эти инструкции предназначены для двухузлового развертывания. В таблице ниже приведены размеры виртуальных машин и дисков, которые потребуется для хранения дисков UPD множества пользователей в вашей организации. 

| Пользователи | Всего (ГБ) | Виртуальная машина | Число дисков | Тип диска | Размер диска (ГБ) | Конфигурация   |
|-------|------------|----|---------|-----------|----------------|-----------------|
| 10    | 50         | DS1 | 2       | P10       | 128            | 2 x (DS1 + 2 P10)  |
| 25    | 125        | DS1 | 2       | P10       | 128            | 2 x (DS1 + 2 P10)  |
| 50    | 250        | DS1 | 2       | P10       | 128            | 2 x (DS1 + 2 P10)  |
| 100   | 500        | DS1 | 2       | P20       | 512            | 2 x (DS1 + 2 P20)  |
| 250   | 1250       | DS1 | 2       | P30       | 1024           | 2 x (DS1 + 2 P30)  |
| 500   | 2500       | DS2 | 3       | P30       | 1024           | 2 x (DS2 + 3 P30)  |
| 1000  | 5000       | DS3 | 5       | P30       | 1024           | 2 x (DS3 + 5 P30)  |
| 2500  | 12 500      | DS4 | 13      | P30       | 1024           | 2 x (DS4 + 13 P30) |
| 5000  | 25 000      | DS5 | 25      | P30       | 1024           | 2 x (DS5 + 25 P30) | 

Следуйте инструкциям ниже, чтобы создать контроллер домена (ниже мы в используем контроллер домена my-dc) и две виртуальные машины узлов (my-fsn1 и my-fsn2), а также настроить эти виртуальные машины в качестве двухузлового сервера SOFS Локальных дисковых пространств.

1. Создайте [подписку Microsoft Azure](https://azure.microsoft.com).
2. Войдите на [портал Azure](https://ms.portal.azure.com).
3. Создайте [учетную запись хранения Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/#create-a-storage-account) в Azure Resource Manager. Создайте ее в новой группе ресурсов и используйте следующие параметры.
   - Модель развертывания: Resource Manager.
   - Учетная запись хранения: общего назначения.
   - Уровень производительности: "Премиум".
   - Способ репликации: LRS.
4. Установите лес Active Directory, воспользовавшись шаблоном быстрого запуска или развернув лес вручную. 
   - Развертывание с помощью шаблона быстрого запуска Azure:
      - [создайте виртуальную машину Azure с новым лесом AD](https://azure.microsoft.com/documentation/templates/active-directory-new-domain/);
      - [создайте домен AD с 2 контроллерами домена](https://azure.microsoft.com/documentation/templates/active-directory-new-domain-ha-2-dc/) (для обеспечения высокой доступности).
   - Вручную [разверните лес](https://azure.microsoft.com/documentation/articles/active-directory-new-forest-virtual-machine/) со следующими параметрами.
      - Создайте виртуальную сеть в той же группе ресурсов, что учетную запись хранения.
      - Рекомендуемый размер: DS2 (увеличьте размер, если контроллер домена будет содержать дополнительные объекты домена).
      - Используйте автоматически созданную виртуальную сеть.
      - Выполните шаги по установке AD DS.
5. Настройте узлы кластера файлового сервера. Это можно сделать, развернув [шаблон Azure кластера SOFS Локальных дисковых пространств для Windows Server 2016](https://azure.microsoft.com/resources/templates/301-storage-spaces-direct/) или выполнив приведенные ниже шаги 6–11, чтобы развернуть их вручную.
6. Чтобы вручную настроить узлы кластера файлового сервера, сделайте следующее.
   1. Создайте первый узел. 
      1. Создайте виртуальную машину из образа Windows Server 2016. (Щелкните **Создать > Виртуальные машины > Windows Server 2016**. Выберите **Resource Manager**, а затем нажмите кнопку **Создать**.)
      2. Настройте базовую конфигурацию следующим образом:
         - Имя: my-fsn1.
         - Тип диска виртуальной машины: SSD.
         - Используйте существующую группу ресурсов, созданную на шаге 3. 
      3. Размер: DS1, DS2, DS3, DS4 или DS5, в зависимости от потребностей пользователя (см. таблицу в начале этих инструкций). Убедитесь, что выбрана поддержка дисков ценовой категории "Премиум".
      4. Параметры: 
         - Учетная запись хранения: выберите учетную запись хранения, созданную на шаге 3.
         - Высокая доступность: создайте группу доступности. (Щелкните **Высокая доступность > Создать**, а затем введите имя (например, s2d-cluster). Используйте значения по умолчанию для параметров **Домены обновления** и **Домены сбоя**.)
   2. Создайте второй узел. Повторите приведенный выше шаг со следующими изменениями.
      - Имя: my-fsn2.
      - Высокая доступность: выберите группу доступности, созданную ранее.  
7. [Подключите диски данных](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-attach-disk-portal/) к виртуальным машинам узлов кластера в соответствии с потребностями пользователей (см. таблицу выше). После создания дисков данных и их подключения к виртуальной машине задайте для параметра **Кэширование узлов** значение **Нет**.
8. Настройте **статические** IP-адреса для всех виртуальных машин. 
   1. В группе ресурсов выберите виртуальную машину, а затем щелкните **Сетевые интерфейсы** (в разделе **Параметры**). Выберите доступный сетевой интерфейс и щелкните **Конфигурации IP**. Выберите доступную IP-конфигурацию, выберите **Статический**, а затем нажмите кнопку **Сохранить**.
   2. Запишите частный IP-адрес (10.x.x.x) контроллера домена (my-dc в нашем случае).
9. Задайте сервер my-dc в качестве основного адреса DNS-сервера на сетевых интерфейсах виртуальных машин узлов кластера. Выберите виртуальную машину и щелкните **Сетевые интерфейсы > DNS-серверы > Пользовательская служба DNS**. Введите частный IP-адрес, указанный выше, и нажмите кнопку **Сохранить**.
10. Создайте [учетную запись хранения Azure для облачного свидетеля](https://docs.microsoft.com/windows-server/failover-clustering/deploy-cloud-witness). (Если вы используете связанные инструкции, остановитесь, когда вы дойдете до раздела "Configuring Cloud Witness with Failover Cluster Manager GUI" (Настройка облачного свидетеля с помощью графического пользовательского интерфейса диспетчера отказоустойчивости кластеров). Мы выполним этот шаг ниже.)
11. Настройте файловый сервер Локальных дисковых пространств. Подключитесь к виртуальной машине узла и выполните следующие командлеты Windows PowerShell.
    1. Установите компонент отказоустойчивости кластеров и компонент файлового сервера на две виртуальные машины узлов кластера файлового сервера.

       ```powershell
       $nodes = ("my-fsn1", "my-fsn2")
       icm $nodes {Install-WindowsFeature Failover-Clustering -IncludeAllSubFeature -IncludeManagementTools} 
       icm $nodes {Install-WindowsFeature FS-FileServer} 
       ```
    2. Проверьте виртуальные машины узлов кластера и создайте двухузловой кластер SOFS.

       ```powershell
       Test-Cluster -node $nodes
       New-Cluster -Name MY-CL1 -Node $nodes –NoStorage –StaticAddress [new address within your addr space]
       ``` 
    3. Настройте облачный свидетель. Используйте имя и ключ учетной записи хранения облачного свидетеля.

       ```powershell
       Set-ClusterQuorum –CloudWitness –AccountName <StorageAccountName> -AccessKey <StorageAccountAccessKey> 
       ```
    4. Включите Локальные дисковые пространства.

       ```powershell
       Enable-ClusterS2D 
       ```
      
    5. Создайте том виртуального диска.

       ```powershell
       New-Volume -StoragePoolFriendlyName S2D* -FriendlyName VDisk01 -FileSystem CSVFS_REFS -Size 120GB 
       ```
       Чтобы просмотреть сведения об общем томе кластера в кластере SOFS, выполните следующий командлет.

       ```powershell
       Get-ClusterSharedVolume
       ```
   
    6. Создайте масштабируемый файловый сервер (SOFS).

       ```powershell
       Add-ClusterScaleOutFileServerRole -Name my-sofs1 -Cluster MY-CL1
       ```

    7. Создайте файловый ресурс SMB в кластере SOFS.

       ```powershell
       New-Item -Path C:\ClusterStorage\VDisk01\Data -ItemType Directory
       New-SmbShare -Name UpdStorage -Path C:\ClusterStorage\VDisk01\Data
       ```

Теперь у вас есть общая папка `\\my-sofs1\UpdStorage`, которую можно использовать для хранения дисков UPD, когда вы [включите возможности UPD](https://social.technet.microsoft.com/wiki/contents/articles/15304.installing-and-configuring-user-profile-disks-upd-in-windows-server-2012.aspx) для пользователей. 
