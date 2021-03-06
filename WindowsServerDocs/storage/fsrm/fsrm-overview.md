---
title: Обзор диспетчера ресурсов файлового сервера (FSRM)
ms.prod: windows-server
ms.author: jgerend
ms.manager: brianlic
ms.technology: storage
ms.topic: article
author: jasongerend
ms.date: 5/14/2018
description: Файловый сервер диспетчер ресурсов (FSRM) — это средство, которое позволяет управлять данными и классифицировать их на файловый сервер Windows Server.
ms.openlocfilehash: 719176307afc320ad676fd1acfc07ad9d15920cf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394168"
---
# <a name="file-server-resource-manager-fsrm-overview"></a>Обзор диспетчера ресурсов файлового сервера (FSRM)

> Относится к: Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server (половина ежегодного канала). 

Диспетчер ресурсов файлового сервера (FSRM) — это служба роли в Windows Server, которая позволяет классифицировать данные, хранящиеся на файловых серверах, и управлять этими данными. Диспетчер ресурсов файлового сервера можно использовать для автоматической классификации файлов, выполнения задач на основе этих классификаций, установки квот на папки и создания отчетов, отслеживающих использование хранилища.

Это небольшая точка, но мы также [добавили возможность отключения журналов изменений](#whats-new) в Windows Server версии 1803.

## <a name="features"></a>Компоненты

Диспетчер ресурсов файлового сервера включает следующие компоненты.

-   [Управление квотами](quota-management.md) позволяет ограничить пространство, разрешенное для тома или папки, и они могут автоматически применяться к новым папкам, созданным на томе. Можно также определить шаблоны квот, которые могут применяться к новым томам или папкам.  
-   [Инфраструктура классификации файлов](classification-management.md) обеспечивает понимание данных за счет автоматизации процессов классификации, позволяющих более эффективно управлять данными. На основании классификации файлов можно применять политики. Примерами политик могут служить динамический контроль доступа для ограничения доступа к файлам, шифрование файлов и установка срока действия файлов. Классификация файлов может производиться автоматически с помощью правил классификации или вручную — изменением свойств выбранного файла или папки.
-   [Задачи управления файлами](file-management-tasks.md) позволяют применять к файлам условную политику или действие в зависимости от их классификации. Условия задачи управления файлами включают расположение файла, свойства классификации, дату создания файла, дату последнего изменения файла или время последнего доступа к файлу. Действия, доступные в задаче управления файлами, включают прекращение срока действия файлов, их шифрование или выполнение пользовательской команды.
-   [Управление блокировкой файлов](file-screening-management.md) помогает управлять типами файлов, которые пользователь может хранить на файловом сервере. Можно ограничить расширения, допустимые при сохранении файлов с общим доступом. Например, можно создать фильтр блокировки файлов, который не позволит сохранять файлы с расширением MP3 в личных папках с общим доступом на файловом сервере.
-   [Отчеты хранилища](storage-reports-management.md) помогают определить тенденции использования дискового пространства и способ классификации данных. Можно также контролировать попытки сохранять запрещенные файлы пользователями выбранной группы.  
  
Функции, включенные в файловый сервер диспетчер ресурсов можно настроить и управлять ими с помощью приложения файлового сервера диспетчер ресурсов или с помощью Windows PowerShell.
  
> [!IMPORTANT]
>  Диспетчер ресурсов файлового сервера поддерживает только тома, отформатированные с файловой системой NTFS. Файловая система Resilient File System не поддерживается.  
  
## <a name="practical-applications"></a>Практическое применение  
 Ниже приведены возможности практического применения диспетчера ресурсов файлового сервера.  
  
-   Использование инфраструктуры классификации файлов со сценарием динамического контроля доступа для создания политики, предоставляющей доступ к файлам и папкам на основании классификации файлов на файловом сервере.  
  
-   Создание правила классификации файлов, которое отмечает как содержащие персональные данные файлы, включающие хотя бы 10 номеров социального обеспечения.  
  
-   Прекращение срока действия файлов, которые не изменялись за последние 10 лет.  
  
-   Создайте квоту 200 МБ для домашнего каталога каждого пользователя и уведомите их при использовании 180 мегабайт.  
  
-   Запрет сохранения музыкальных файлов в личных папках с общим доступом.  
  
-   Создание в расписании отчета, который будет выполняться в полночь по воскресеньям и создавать список файлов, открывавшихся за предыдущие два дня. Это поможет обнаружить действия по сохранению файлов в выходные и соответственно планировать время отключения сервера.  

## <a name="whats-new"></a>Новые возможности — запретить диспетчеру FSRM создавать журналы изменений

Начиная с Windows Server версии 1803, вы можете запретить диспетчер ресурсов службе файлового сервера создавать журнал изменений (также известный как журнал USN) на томах при запуске службы. Это может освободить немного пространства на каждом томе, но будет отключать классификацию файлов в режиме реального времени.

Дополнительные сведения о новых возможностях см. [в разделе новые возможности файлового сервера диспетчер ресурсов](https://technet.microsoft.com/library/dn383587.aspx).

Чтобы предотвратить создание журнала изменений на некоторых или всех томах при запуске службы диспетчер ресурсов файлового сервера, выполните следующие действия. 

1. Завершите работу службы СРМСВК. Например, откройте сеанс PowerShell от имени администратора и введите `Stop-Service SrmSvc`.
2. Удалите журнал USN для томов, для которых требуется экономить место, с помощью команды fsutil: 

      ```
      fsutil usn deletejournal /d <VolumeName>
      ```
    Пример: `fsutil usn deletejournal /d c:`

3. Откройте редактор реестра, например, введя `regedit` в тот же сеанс PowerShell.
4. Перейдите к следующему разделу: **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SrmSvc\Settings**
5. Для необязательного пропуска создания журнала изменений для всего сервера (пропустите этот шаг, если вы хотите отключить его только на конкретных томах):
    1. Щелкните правой кнопкой мыши раздел **Параметры** и выберите пункт **новое** > **значение DWORD (32 бит)** . 
    1. Присвойте этому `SkipUSNCreationForSystem`значению имя.
    1. Установите значение **1** (в шестнадцатеричной кодировке).
6. Для необязательного пропуска создания журнала изменений для конкретных томов выполните следующие действия.
    1. Получите пути тома, которые нужно пропустить, с помощью `fsutil volume list` команды или следующей команды PowerShell:
        ```PowerShell
        Get-Volume | Format-Table DriveLetter,FileSystemLabel,Path
        ```
       Ниже приведен пример выходных данных:

       ```
        DriveLetter FileSystemLabel Path
        ----------- --------------- ----
                    System Reserved \\?\Volume{8d3c9e8a-0000-0000-0000-100000000000}\
        C                           \\?\Volume{8d3c9e8a-0000-0000-0000-501f00000000}\
       ```
    2. В редакторе реестра щелкните правой кнопкой мыши ключ **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SrmSvc\Settings** и выберите пункт **новое** > .**многострочное значение**.
    3. Присвойте этому `SkipUSNCreationForVolumes`значению имя.
    4. Введите путь к каждому тому, на котором вы пропускаете создание журнала изменений, размещая каждый путь на отдельной строке. Пример:

        ```
        \\?\Volume{8d3c9e8a-0000-0000-0000-100000000000}\
        \\?\Volume{8d3c9e8a-0000-0000-0000-501f00000000}\
        ```

        > [!NOTE] 
        > Редактор реестра может сообщить, что он удалил пустые строки, отображая это предупреждение, что можно спокойно проигнорировать: *Data типа REG_MULTI_SZ не может содержать пустые строки. Редактор реестра удалит все найденные пустые строки.*

7. Запустите службу СРМСВК. Например, в сеансе PowerShell введите `Start-Service SrmSvc`.



## <a name="see-also"></a>См. также

- [Динамический контроль доступа](https://technet.microsoft.com/library/dn408191(v=ws.11).aspx) 