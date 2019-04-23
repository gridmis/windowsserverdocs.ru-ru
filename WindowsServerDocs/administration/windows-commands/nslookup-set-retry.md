---
title: nslookup set retry
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 63d72a45c33da099c5936d625b27aa71ef002280
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857665"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает число повторных попыток.
## <a name="syntax"></a>Синтаксис
```
set retry=<Number>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<Number>|Указывает новое значение для числа повторных попыток. По умолчанию количество повторных попыток равно 4.|
|{help &#124; ?}|Отображает краткое описание **nslookup** подкоманды.|
## <a name="remarks"></a>Примечания
-   Если ответ на запрос не получен в течение отведенного времени, время ожидания удваивается, и повторном запросе. Этот параметр задает, сколько раз запрос будет повторен. Можно изменить период ожидания с **задать время ожидания** подкоманды.
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[nslookup задать время ожидания](nslookup-set-timeout.md)