---
title: оперативный том
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5da073fd-578d-4691-ad0f-605ba66e0c7e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 06a3c81313180b2880c1e47c3b6c12236fda4245
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372516"
---
# <a name="online-volume"></a>оперативный том



Переводит тома, находящиеся в режиме «вне сети», в оперативный режим

> [!IMPORTANT]
> Эта команда недоступна ни в одном из выпусков Windows Vista.

> [!IMPORTANT]
> Эта команда завершится ошибкой, если она используется на томе, доступном только для чтения.

## <a name="syntax"></a>Синтаксис

```
online volume [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Эта команда работает с томами, которые завершились сбоем, завершаются сбоем или находятся в состоянии Отказавшая избыточность.
-   Для завершения этой команды необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы перевести том с фокусом в режим «в сети», введите:
```
online volume
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

