---
title: Обзор защищенной структуры и экранированных виртуальных машин
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 579012be66969ffc584b4b4ea021f11acbbdfb78
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59855905"
---
# <a name="guarded-fabric-and-shielded-vms-overview"></a>Обзор защищенной структуры и экранированных виртуальных машин

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

## <a name="overview-of-the-guarded-fabric"></a>Обзор защищенной структуры

Безопасность виртуализации — из основных областей инвестиций в Hyper-V. Помимо защиты узлов или других виртуальных машин от ВМ с вредоносными программами необходимо также защитить их от скомпрометированного узла. Это основные опасность для каждой платформы виртуализации сегодня, будь то Hyper-V, VMware или любой другой. Простыми словами, если файл виртуальной машины извлекается из системы организации (злонамеренно или случайно), его можно запустить в любой другой системе. Защита ценных ресурсов, таких как контроллеры домена, конфиденциальные файловые серверы и системы отдела кадров, — самая приоритетная задача в организации.

Для защиты от структуры скомпрометированных виртуализации Windows Server 2016 Hyper-V представлены экранированные виртуальные машины. Экранированная виртуальная машина является поколения 2 виртуальной Машины (поддерживается в Windows Server 2012 и более поздних версий), имеющий виртуальный доверенный платформенный модуль, шифруются с помощью BitLocker и можно запускать только на работоспособных и утвержденных узлах в структуре. Благодаря экранированным виртуальным машинам и защищенной структуре поставщики облачных служб или администраторы корпоративного частного облака предоставляют более безопасную среду для клиентских виртуальных машин. 

Защищенная структура состоит из:

- одной службы защиты узла (HGS) (как правило, кластера из 3-х узлов);
- одного или нескольких защищенных узлов;
- набора экранированных виртуальных машин. На схеме ниже показано, как служба защиты узла использует аттестации, чтобы обеспечить запуск экранированных виртуальных машин только на известных допустимых узлах, и безопасное освобождение ключей для этих виртуальных машин.

Когда клиент создает экранированные виртуальные машины, запущенные в защищенной структуре, узлы Hyper-V и эти виртуальные машины защищаются с помощью службы HGS. HGS предоставляет две различные службы: аттестации и защиты ключей. Служба аттестации гарантирует, что экранированные виртуальные машины могут запускаться только на доверенных узлах Hyper-V, тогда как служба защиты ключей предоставляет ключи, с помощью которых можно включить виртуальные машины и выполнить их динамическую миграцию на другие защищенные узлы.

![Структура защищенного узла](../media/Guarded-Fabric-Shielded-VM/Guarded-Host-Overview-Diagram.png)

## <a name="video-introduction-to-shielded-virtual-machines"></a>Видео Общие сведения об экранированных виртуальных машин 

<iframe src="https://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016/player" width="650" height="440" allowFullScreen frameBorder="0"></iframe>

## <a name="attestation-modes-in-the-guarded-fabric-solution"></a>Режимы аттестации в решении защищенной структуры

HGS поддерживает разных режима аттестации для защищенной структуры:

- Аттестацию с доверием TPM (на основе оборудования)
- Аттестация ключей узла (с учетом пары асимметричных ключей)

Рекомендуется использовать аттестацию по ключу доверенного платформенного модуля, так как она предоставляет более надежные гарантии, что описано в приведенной ниже таблице. Но в этом случае требуется, чтобы у узлов Hyper-V был доверенный платформенный модуль версии 2.0. Если в настоящее время у вас нет TPM 2.0 или любого доверенного платформенного МОДУЛЯ, можно использовать аттестацию ключей узла. Если вы приобретете новое оборудование и захотите перейти на аттестацию по ключу доверенного платформенного модуля, смените режим аттестации в службе защиты узла без прерывания или с минимальным прерыванием работы структуры.

| **Режим аттестации, выбираемый для узлов**                                            | **Гарантии узла** |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|**Аттестация доверенного платформенного МОДУЛЯ:** Предлагает самую надежную защиту, но требует дополнительных шагов настройки. Серверное оборудование и встроенное по должно включать TPM 2.0 и UEFI 2.3.1 которых включена безопасная загрузка. | Защищенные узлы утверждаются на основе их удостоверений доверенного платформенного МОДУЛЯ, измеряемой загрузки последовательности и политик целостности кода, чтобы убедиться, что они выполняться только утвержденный код.| 
| **Аттестация ключей узла:** Предназначен для поддержки текущего серверного оборудования, где TPM 2.0 недоступен. Такая аттестация требует меньше этапов настройки и совместима со стандартным серверным оборудованием. | Защищенные узлы утверждаются на основании этого ключа. | 

Другой режим с именем **аттестацию с доверием администратора** является устаревшим, начиная с Windows Server 2019. Этот режим был основан на защищенный узел членство в группе безопасности доменных служб Active Directory (AD DS). Аттестация ключей узла содержит аналогичные Идентификация узла и легко настраивается. 

## <a name="assurances-provided-by-the-host-guardian-service"></a>Гарантии, предоставляемые службой защиты узла

HGS, а также методы создания экранированных виртуальных машин обеспечивают следующие гарантии.

| **Тип гарантии для виртуальных машин**                         | **Гарантии экранированной виртуальной Машины, предоставленные службой защиты ключей и методами создания экранированных виртуальных машин** |
|----------------------------|--------------------------------------------------|
| **Шифрование дисков (дисков операционной системы и дисков данных) с помощью BitLocker**   | Экранированные виртуальные машины используют BitLocker для защиты своих дисков. Ключи BitLocker, необходимые для загрузки виртуальной Машины и расшифровки дисков защищаются с помощью экранированной виртуальной Машины виртуальный доверенный платформенный модуль с помощью проверенной технологии, такие как защищенной измеряемой загрузки. Хотя экранированные виртуальные машины автоматически шифруют и защищают только диск операционной системы, можно также [шифровать диски с данными](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview), подключенные к этим машинам. |
| **Развертывание новых экранированных виртуальных машин из «доверенных» шаблонов образов и дисков** | При развертывании новых экранированных виртуальных машин клиенты могут указать, каким шаблонам дисков они доверяют. В экранированных шаблонах дисков есть подписи, которые определяются в тот момент, когда их содержимое распознается как надежное. Подписи дисков затем сохраняются в каталоге подписей, который безопасно передается клиентами структуре при создании экранированных виртуальных машин. Во время подготовки экранированных виртуальных машин подпись диска определяется снова и сравнивается с доверенными подписями в каталоге. Если подписи совпадают, машина развертывается. В противном случае шаблон диска такой машины считается ненадежным и происходит сбой развертывания. |
| **Защита паролей и других секретов при создании экранированной виртуальной Машины** | При создании виртуальных машин, это необходимо, чтобы гарантировать, что секреты виртуальной Машины, например доверенные подписи диска, сертификаты протокола удаленного рабочего СТОЛА и пароль виртуальной Машины учетной записи локального администратора, не раскрыты структуре. Эти секреты хранятся в файле данных экранирования (PDK-файле) — зашифрованном файле, который защищен ключами клиента и отправлен клиентом в структуру. При создании экранированной виртуальной машины клиент выбирает, какие данные экранирования использовать. При этом секреты безопасно передаются доверенным компонентам внутри защищенной структуры. |
| **Где можно запустить виртуальную Машину клиента управления** | Данные экранирования также содержат список защищенных структур, в которых разрешен запуск определенной экранированной виртуальной машины. Это полезно в случаях, когда экранированная виртуальная машина обычно находится в локальном частном облаке, но для аварийного восстановления ее нужно перенести в другое облако (частное или общедоступное). Целевое облако или структура должны поддерживать экранированные виртуальные машины, и эти машины должны разрешать запуск в этой структуре. |

## <a name="what-is-shielding-data-and-why-is-it-necessary"></a>Что такое данные экранирования и зачем они нужны

Файл данных экранирования (также называемый файлом данных подготовки, или PDK-файлом) — это зашифрованный файл, который создает клиент или владелец виртуальной машины, чтобы защитить важную информацию о конфигурации виртуальной машины (пароль администратора, протокол удаленного рабочего стола и другие сертификаты с информацией об удостоверениях, учетные данные для присоединения домена и т. д.). Администратор структуры использует файл данных экранирования при создании экранированной виртуальной машины, но не может просматривать и использовать содержащиеся в нем сведения.

Кроме того, файлы данных экранирования содержат следующие секреты:

- Учетные данные администратора.
- Файл ответов (unattend.xml).
- Политика безопасности, определяет, созданы ли виртуальные машины с помощью этого данные экранирования настроенные как экранированные или шифрование поддерживается
    - Обратите внимание, что виртуальные машины, настроенные как экранированные, защищены от администраторов структуры, а виртуальные машины с поддержкой шифрования — нет.
- Сертификат протокола удаленного рабочего стола для безопасного взаимодействия с виртуальной машиной.
- Каталог подписей томов со списком доверенных подписанных шаблонов дисков, которые можно использовать для создания виртуальной машины.
- Предохранитель ключа, определяющий, в каких защищенных структурах может запускаться экранированная виртуальная машина.

Файл данных экранирования (PDK-файл) гарантирует, что виртуальная машина будет создана так, как предполагал клиент. Например, когда клиент размещает файл ответов (unattend.xml) в файле данных экранирования и передает его поставщику услуг размещения, последний не может просматривать файл ответов или вносить в него изменения. Поставщик услуг размещения также не может указать другой VHDX при создании экранированной виртуальной машины, так как файл данных экранирования содержит подписи доверенных дисков, на основе которых можно создать экранированные виртуальные машины.

На рисунке ниже показан файл данных экранирования и связанные с ним элементы конфигурации.

![Файл данных экранирования](../media/Guarded-Fabric-Shielded-VM/shielded-vms-shielding-data-file.png)

## <a name="what-are-the-types-of-virtual-machines-that-a-guarded-fabric-can-run"></a>Типы виртуальных машин, которые могут выполняться в защищенной структуре

В защищенной структуре могут запускаться виртуальные машины одного из следующих типов:

1.  Обычная виртуальная машина, которая не обеспечивает защиту, представленную только в предыдущих версиях Hyper-V.
2.  Виртуальная машина с поддержкой шифрования, защиту которой может настроить администратор структуры.
3.  Экранированная виртуальная машина, все средства защиты которой постоянно включены и не могут быть отключены администратором структуры.

Виртуальные машины с поддержкой шифрования предназначены для случаев, когда есть полное доверие к администратору структуры.  Например, предприятие может развернуть защищенную структуру, чтобы выполнять для дисков виртуальной машины шифрование неактивных данных с целью соответствия требованиям. Администраторы структуры по-прежнему могут использовать удобные средства управления, например подключения к консоли виртуальной машины, PowerShell Direct и другие повседневные средства управления и устранения неполадок.

Экранированные виртуальные машины предназначены для структур, где данные и состояние виртуальной машины должны быть защищены как от администраторов структуры, так и от ненадежного программного обеспечения, которое может выполняться на узлах Hyper-V. К примеру, экранированные виртуальные машины никогда не разрешат подключение к консоли виртуальной машины, тогда как для виртуальных машин с поддержкой шифрования администратор структуры может включить или отключить эту защиту.

В следующей таблице перечислены различия между поддержкой шифрования и экранированных виртуальных машин.

| Возможности        | Второе поколение. Поддержка шифрования     | Второе поколение. Экранирование         |
|----------|--------------------|----------------|
|Безопасная загрузка        | Да, необходимо, но есть возможность настройки        | Да, необходимо, применяется принудительно    |
|Виртуальный доверенный платформенный модуль               | Да, необходимо, но есть возможность настройки        | Да, необходимо, применяется принудительно    |
|Шифрование состояния виртуальной машины и трафика динамической миграции | Да, необходимо, но есть возможность настройки |  Да, необходимо, применяется принудительно  |
|Компоненты интеграции | Настраивается администратором структуры      | Некоторые компоненты интеграции заблокированы (например, обмен данными, PowerShell Direct) |
|Подключение к виртуальной машине (консоль), HID-устройства (например, клавиатура, мышь) | Включено, не может быть отключено | Включена на узле, начиная с Windows Server версии 1803; Отключен на узлы более ранних версий |
|Последовательные или COM-порты   | Поддерживается                             | Отключено (не может быть включено) |
|Подключение отладчика (к процессу виртуальной Машины)<sup>1</sup>| Поддерживается          | Отключено (не может быть включено) |

<sup>1</sup> Традиционные отладчики, которые напрямую подключиться к процессу, например WinDbg.exe, блокируются для экранированных виртуальных машин, так как рабочий процесс виртуальной Машины (VMWP.exe) является свет защищенного процесса (PPL). Альтернативные методы отладки, например используемые LiveKd.exe, не блокируются. В отличие от экранированные виртуальные машины рабочий процесс для виртуальных машин с поддержкой шифрования не выполняет PPL, поэтому Традиционные отладчики, такие как WinDbg.exe продолжит работать нормально. 

Как экранированные виртуальные машины, так и виртуальные машины с поддержкой шифрования продолжают поддерживать стандартные возможности управления структуры, в том числе динамическую миграцию, реплику Hyper-V, контрольные точки виртуальной машины и т. д.

## <a name="the-host-guardian-service-in-action-how-a-shielded-vm-is-powered-on"></a>Служба защиты узла в действии: Как работает экранированной виртуальной Машины

![Файл данных экранирования](../media/Guarded-Fabric-Shielded-VM/shielded-vms-how-a-shielded-vm-is-powered-on.png)

1. Включается виртуальная машина VM01.

    Прежде чем защищенный узел сможет включить экранированную виртуальную машину, нужно подтвердить его работоспособность. Чтобы доказать, что он работоспособен, он должен предоставить сертификат работоспособности службе защиты ключей. Он передается в ходе аттестации.

2. Узел запрашивает аттестацию.

    Защищенный узел запрашивает аттестацию. Режим аттестации устанавливается службой защиты узла.

    **Аттестация доверенного платформенного МОДУЛЯ**: Узел Hyper-V отправляет сведения, включая:

       - сведения, определяющие доверенный платформенный модуль (ключ подтверждения);
       - сведения о процессах, запущенных в течение последней последовательности загрузки (журнал TCG);
       - Сведения о политике целостности кода (CI), которая была применена на узле. 

       Attestation happens when the host starts and every 8 hours thereafter. If for some reason a host doesn't have an attestation certificate when a VM tries to start, this also triggers attestation.

    **Аттестация ключей размещения**: Узел Hyper-V отправляет открытый половина пары ключей. HGS проверяет узел ключ зарегистрирован. 
    
    **Аттестация по группе доверенного администратора**: Узел Hyper-V отправляет билет Kerberos, который определяет группы безопасности, которые узел. HGS проверяет, принадлежит ли узел к группе безопасности, которую ранее настроил доверенный администратор HGS.

3. Аттестация завершается успешно (или с ошибкой).

    Режим аттестации определяет, какие проверки необходимы для успешного удостовериться, что узел находится в работоспособном состоянии. С Аттестация доверенного платформенного МОДУЛЯ проверяются хоста доверенного платформенного МОДУЛЯ identity измерения загрузки и политика целостности кода. В аттестации ключей узла проверяется только регистрации ключа узла. 

4. Сертификат аттестации отправляется на узел.

    Если Аттестация прошла успешно, сертификат работоспособности отправляется на узел и распознается как «защищенный» (имеющий право на запуск экранированных виртуальных машин). Узел использует сертификат работоспособности для авторизации службы защиты ключей, чтобы безопасно освободить ключи, необходимые для работы экранированных виртуальных машин.

5. Узел запрашивает ключ виртуальной машины.

    У защищенного узла отсутствуют ключи, необходимые для включения экранированной виртуальной машины (в этом случае VM01). Чтобы получить необходимые ключи, защищенный узел должен предоставить службе защиты ключей следующее:

    - текущий сертификат работоспособности;
    - зашифрованный секрет (предохранитель ключа), содержащий необходимые для включения VM01 ключи. Секрет зашифрован с использованием других ключей, известных только службе защиты ключей.

6. Ключ освобождается.

    Служба защиты ключей проверяет сертификат работоспособности на допустимость. Сертификат не должен быть просрочен, и служба защиты ключей должна доверять службе аттестации, выдавшей его.

7. Ключ возвращается на узел.

    Если сертификат работоспособности допустим, служба защиты ключей пытается расшифровать секрет и безопасно вернуть ключи, необходимые для включения виртуальной машины. Обратите внимание на то, что ключи шифруются для защищенного узла VBS.

8. Узел запускает VM01.

## <a name="guarded-fabric-and-shielded-vm-glossary"></a>Словарь терминов, касающихся защищенной структуры и экранированной виртуальной машины

| Термин              | Определение           |
|----------|------------|
| Служба защиты узла | Роль сервера Windows, который установлен на защищенном кластере серверов без операционной системы. Он может оценить работоспособность узла Hyper-V и освободить ключи для работоспособных узлов во время включения или динамической миграции экранированных виртуальных машин. Эти две возможности играют главную роль в решении экранированной виртуальной машины и называются **службой аттестации** и **службой защиты ключей** соответственно. |
| Защищенный узел | Узел Hyper-V, на котором могут запускаться экранированные виртуальные машины. Узел можно считать только _защищенных_ когда он определен как работоспособное службой аттестации HGS. Экранированные виртуальные машины невозможно включить на узле Hyper-V или динамически мигрировать на него, если он еще не прошел аттестацию или она завершилась неудачно. |
| Защищенная структура    | Это обобщающий термин для описания структуры узлов Hyper-V и их службы защиты. Структура может запускать экранированные виртуальные машины и управлять ими. |
| Экранированная виртуальная машина | Виртуальная машина, которая может запускаться только на защищенных узлах и защищена от просмотра, несанкционированного изменения и кражи данных администраторами вредоносных систем и вредоносными программами. |
| Администратор структуры | Администратор общедоступного или частного облака, который может управлять виртуальными машинами. В контексте защищенной структуры у администратора структуры нет доступа к экранированным виртуальным машинам или к политикам, определяющим узлы, на которых могут запускаться экранированные виртуальные машины. |
| Администратор службы защиты узла | Доверенный администратор общедоступного или частного облака, который может управлять политикой и материалами шифрования для защищенных узлов, то есть таких, на которых может запускаться экранированная виртуальная машина.|
| Файл данных подготовки или файл данных экранирования (PDK-файл) | Зашифрованный файл, который создается клиентом или пользователем для хранения важной информации о конфигурации виртуальной машины и защиты этой информации от несанкционированного доступа. Например, файл данных экранирования может содержать пароль, который будет назначен учетной записи локального администратора при создании виртуальной машины. |
| Безопасность на основе виртуализации | Hyper-V на основе обработки и хранения среды, защищенная от администраторов. Администратор операционной системы не может получить доступ к ключам операционной системы, которые сохранены в виртуальном безопасном режиме.|
| Виртуальный доверенный платформенный модуль | Виртуализированная версия доверенного платформенного модуля (TPM). Начиная с Hyper-V в Windows Server 2016, позволяет виртуальное устройство TPM 2.0, чтобы виртуальные машины могут быть зашифрованы, так же, как физического доверенного платформенного физического компьютера должны быть зашифрованы.|

## <a name="see-also"></a>См. также

- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
- Блог: [Центр обработки данных и блог по безопасности частного облака](https://blogs.technet.microsoft.com/datacentersecurity/)
- Видео [Общие сведения об экранированных виртуальных машин](https://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016)
- Видео [Погружение в экранированные виртуальные машины с Windows Server 2016 Hyper-V](https://channel9.msdn.com/events/Ignite/2016/BRK3124)