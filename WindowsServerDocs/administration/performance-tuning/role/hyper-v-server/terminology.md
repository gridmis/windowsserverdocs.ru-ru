---
title: Терминология Hyper-V
description: Терминология Hyper-v, полезная для настройки производительности Hyper-V
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: Asmahi; SandySp; JoPoulso
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: acd61e9edef3ac88027d0cc89618c537fa6aa25f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385027"
---
# <a name="hyper-v-terminology"></a>Терминология Hyper-V
В этом разделе обобщены основные термины, относящиеся к технологиям виртуальных машин, используемым в рамках этой статьи по настройке производительности.

| Термин        | Определение           |
| ------------- |:------------|
|*Дочерний раздел* | Любая виртуальная машина, созданная с помощью корневого раздела.|
|*Виртуализация устройств* | Механизм, позволяющий создавать абстрактные ресурсы оборудования и предоставлять к ним общий доступ нескольким потребителям.|
|*Эмуляция устройства*|Виртуализированное устройство, которое имитирует фактическое физическое устройство, чтобы гости могли использовать стандартные драйверы для этого устройства.|
|*просвещение*|Оптимизация операционной системы на виртуальной машине для обеспечения осведомленности о средах виртуальных машин и настройке ее поведения для виртуальных машин.|
|*ведущи*|Программное обеспечение, выполняемое в разделе. Это может быть полнофункциональная операционная система или небольшой специализированный ядер. Гипервизор не зависит от гостя.|
|*оболочк*|Уровень программного обеспечения, который располагается над оборудованием и под одной или несколькими операционными системами. Его основной задачей является предоставление изолированных сред выполнения, называемых разделами. Каждая секция имеет собственный набор виртуализированных аппаратных ресурсов (центрального процессора, памяти и устройств). Гипервизор управляет доступом к базовому оборудованию и определяет его приоритет.|
|*логический процессор*| Единица обработки, которая обрабатывает один поток выполнения (поток инструкций). Для одного ядра процессора и одного или нескольких ядер на сокет процессора может быть один или несколько логических процессоров.|
| *транзитный доступ к диску*|Представление всего физического диска в виде виртуального диска в гостевой системе. Данные и команды передаются на физический диск (через собственный стек хранилища корневого раздела) без промежуточной обработки виртуального стека.|
|*корневой раздел*|Корневой раздел, который создается первым и владеет всеми ресурсами, не связанными с гипервизором, включая большинство устройств и системной памяти. В корневом разделе размещается стек виртуализации, а также создаются и управляются дочерние секции.|
|*Устройство, относящееся к Hyper-V*|Виртуальное устройство без аналогового оборудования, поэтому гостям может потребоваться драйвер (клиент службы виртуализации) для этого устройства, относящегося к Hyper-V. Драйвер может использовать шину виртуальной машины (VMBus) для связи с программным обеспечением виртуализированного устройства в корневом разделе.|
|*Виртуальная машина*|Виртуальный компьютер, созданный эмуляцией программного обеспечения и имеющий те же характеристики, что и реальный компьютер.|
| *коммутатор виртуальной сети*|(также называется виртуальным коммутатором) Виртуальная версия коммутатора физической сети. Виртуальную сеть можно настроить для предоставления доступа к локальным или внешним сетевым ресурсам для одной или нескольких виртуальных машин.|
|*виртуальный процессор*|Виртуальная абстракция процессора, запланированного для работы на логическом процессоре. Виртуальная машина может иметь один или несколько виртуальных процессоров.|
|*Клиент службы виртуализации (VSC)*|Программный модуль, загружаемый гостевым ОС для использования ресурса или службы. Для устройств ввода-вывода клиент службы виртуализации может быть драйвером устройства, загружаемым ядром операционной системы.|
| *Поставщик службы виртуализации (VSP)*|  Поставщик, предоставляемый стеком виртуализации в корневом разделе, который предоставляет ресурсы или службы, такие как ввод-вывод в дочерний раздел.|
| *стек виртуализации*|Коллекция программных компонентов в корневом разделе, которые работают вместе для поддержки виртуальных машин. Стек виртуализации работает с и располагается над гипервизором. Он также предоставляет возможности управления.|
|*VMBus*|Механизм связи на основе канала, используемый для обмена данными между секциями и перечисление устройств в системах с несколькими активными виртуальными секциями. VMBus устанавливается со службами интеграции Hyper-V.|

## <a name="see-also"></a>См. также

-   [Архитектура Hyper-V](architecture.md)

-   [Конфигурация сервера Hyper-V](configuration.md)

-   [Производительность процессоров Hyper-V](processor-performance.md)

-   [Производительность памяти Hyper-V](memory-performance.md)

-   [Производительность ввода-вывода хранилища Hyper-V](storage-io-performance.md)

-   [Производительность ввода-вывода сети Hyper-V](network-io-performance.md)

-   [Обнаружение узких мест в виртуализированной среде](detecting-virtualized-environment-bottlenecks.md)

-   [Виртуальные машины Linux](linux-virtual-machine-considerations.md)
