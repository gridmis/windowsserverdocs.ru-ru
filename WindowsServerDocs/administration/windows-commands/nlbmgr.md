---
title: nlbmgr
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89cb8590-b7cf-4a27-89fa-0fa62ea1a1ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2843e303b296beca24132b62073b6776a343544b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373161"
---
# <a name="nlbmgr"></a>nlbmgr

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

С помощью диспетчера балансировки сетевой нагрузки можно настроить и управлять кластерами балансировки сетевой нагрузки и всеми узлами кластера с одного компьютера, а также реплицировать конфигурацию кластера на другие узлы. Диспетчер балансировки сетевой нагрузки можно запустить из командной строки с помощью команды **Nlbmgr. exe**, которая устанавливается в папку **SystemRoot\System32**
## <a name="syntax"></a>Синтаксис
```
nlbmgr [/help] [/noping] [/hostlist <filename>] [/autorefresh <interval>]
```
### <a name="parameters"></a>Параметры

|        Параметр        |                                                                                                                                                                                                Описание                                                                                                                                                                                                |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          /help          |                                                                                                                                                                                   Отображение справки в командной строке.                                                                                                                                                                                    |
|         /нопинг         | Предотвращает проверку связи между узлами с помощью диспетчера балансировки сетевой нагрузки, прежде чем пытаться связаться с ними через инструментарий управления Windows (WMI) (WMI). Используйте этот параметр, если на всех доступных сетевых адаптерах отключен протокол ICMP. Если диспетчер балансировки сетевой нагрузки пытается связаться с недоступным узлом, при использовании этого параметра будет возникать задержка. |
|  /хостлист <filename>   |                                                                                                                                                                Загружает узлы, указанные в файле filename, в Диспетчер балансировки сетевой нагрузки.                                                                                                                                                                 |
| /ауторефреш <interval> |                                                                                                          Заставляет Диспетчер балансировки сетевой нагрузки обновлять сведения об узле и кластере каждые <interval> секунд. Если интервал не указан, информация обновляется каждые 60 секунд.                                                                                                          |
|           /?            |                                                                                                                                                                                   Отображение справки в командной строке.                                                                                                                                                                                    |

## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

