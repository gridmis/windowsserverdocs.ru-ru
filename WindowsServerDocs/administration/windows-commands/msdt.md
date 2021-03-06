---
title: msdt
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ead1b672-a120-4e16-94aa-a8e13602c1d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4c4342cf0fe588f5b41cd98a38a459ac41ca212a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373454"
---
# <a name="msdt"></a>msdt



Вызывает пакет устранения неполадок в командной строке или в составе автоматизированного скрипта и включает дополнительные параметры без ввода данных пользователем.

## <a name="syntax"></a>Синтаксис

```
msdt </id <name> | /path <name> | /cab < name>> <</parameter> [options] … <parameter> [options]>>
```

## <a name="parameters"></a>Параметры

В следующей таблице приведены параметры и параметры, поддерживаемые средством MSDT. exe.


|      Параметр      |                                                                                            Описание                                                                                             |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /ID \<имя пакета > |        Указывает, какой пакет диагностики следует запустить. Список доступных пакетов см. в подразделе "Устранение неполадок с ИДЕНТИФИКАТОРом" раздела "доступные пакеты устранения неполадок" Далее в этом разделе.         |
|  каталог \</Path  |                                                                                           файл. диагпкг                                                                                            |
|   > \<ключа доступа/дЦи   |                                        Предварительно заполняет поле ключа доступа в MSDT. Этот параметр используется только в том случае, если поставщик услуг поддержки предоставил ключ доступа.                                         |
|  > \<каталога/DT   | Отображает журнал устранения неполадок в указанном каталоге. Результаты диагностики хранятся в каталогах **%локалаппдата%\диагностикс** или **%локалаппдата%\елеватеддиагностикс** пользователя. |
| > \<файла ответов/АФ  |                                               Указывает файл ответов в формате XML, который содержит ответы на одно или несколько диагностических действий.                                               |

