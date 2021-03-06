---
title: chcp
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc7b1c71-7b80-443d-9cf1-9bcf305aa1fd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5784b052ff1d7084d68cca0589caf518b8e44a8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379530"
---
# <a name="chcp"></a>chcp



Изменяет активную кодовую страницу консоли. Если используется без параметров, параметр **chcp** отображает номер активной кодовой страницы консоли.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
chcp [<NNN>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@NO__T 0NNN >|Задает кодовую страницу.|
|/?|Отображение справки в командной строке.|

В следующей таблице перечислены поддерживаемые кодовые страницы и их страны, регионы или языки.

|Кодовая страница|Страна, регион или язык|
|---------|--------------------------|
|437|США|
|850|Многоязычная (латиница I)|
|852|Славянские (латиница II)|
|855|Кириллица (Русский)|
|857|Турецкий|
|860|Португальский|
|861|Исландский|
|863|Канада — французский|
|865|Скандинавская|
|866|Русский|
|869|Современный греческий|
|936|Китайский|

## <a name="remarks"></a>Примечания

-   В окне командной строки, использующем растровые шрифты, правильно отображается только кодовая страница изготовителя оборудования (OEM), установленная вместе с Windows. Другие кодовые страницы отображаются правильно в полноэкранном режиме или в окнах командной строки, в которых используются шрифты TrueType.
-   Вам не нужно подготавливать кодовые страницы (как в MS-DOS).
-   Программы, запускаемые после назначения новой кодовой страницы, используют новую кодовую страницу. Однако программы (кроме cmd. exe), запускаемые до назначения новой кодовой страницы, используют исходную кодовую страницу.

## <a name="BKMK_examples"></a>Примеров

Чтобы просмотреть текущую настройку кодовой страницы, введите:
```
chcp
```
Появится сообщение следующего вида:

`Active code page: 437`

Чтобы изменить активную кодовую страницу на 850 (многоязычный), введите:
```
chcp 850
```
Если указанная кодовая страница является недопустимой, появляется следующее сообщение об ошибке:

`Invalid code page`

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
