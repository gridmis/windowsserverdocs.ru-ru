---
title: nslookup set timeout
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b7a35a4a8e9e9cc10ea5548875f710fb5a86036
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837815"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет начальное количество секунд ожидания ответа на запрос поиска.
## <a name="syntax"></a>Синтаксис
```
set timeout=<Number>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<Number>|Указывает количество секунд ожидания ответа. Количество секунд ожидания, по умолчанию равно 5.|
|{help &#124; ?}|Отображает краткое описание **nslookup** подкоманды.|
## <a name="remarks"></a>Примечания
-   Если ответ на запрос не получен в течение указанного периода, время ожидания удваивается, и запрос отправляется еще раз. Можно использовать **повтора набора** команду, чтобы контролировать число повторных попыток.
## <a name="BKMK_examples"></a>Примеры
В следующем примере устанавливается время ожидания для получения ответа на 2 секунды:
```
set timeout=2
```
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[nslookup задать повторных попыток](nslookup-set-retry.md)