---
title: оперативный диск
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc44a783-eaa4-40ca-be01-5703b5bf4eb3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3d798bf34ec2f9d2f01b5470c4ec52f936674135
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372513"
---
# <a name="online-disk"></a>оперативный диск



Переводит диски, находящиеся в режиме «вне сети», в оперативный режим.

> [!IMPORTANT]
> Эта команда недоступна ни в одном из выпусков Windows Vista.

> [!IMPORTANT]
> Эта команда завершится ошибкой, если она используется на диске, доступном только для чтения.

Инструкции по использованию этой команды см. в разделе Повторная [Активация отсутствующего или автономного динамического диска](https://go.microsoft.com/fwlink/?LinkId=207046) (https://go.microsoft.com/fwlink/?LinkId=207046) ).

## <a name="syntax"></a>Синтаксис

```
online disk [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   При использовании без параметров в Windows Vista эта команда работает с дисковой группой. Для базовых дисков в каждой группе не может быть больше одного диска. Для динамических дисков группа включает все динамические диски, не являющиеся внешними.
-   Для базовых дисков эта команда попытается подключить выбранный диск к сети и все тома на этом диске.
-   Для динамических дисков эта команда попытается перевести в оперативный режим все диски, не помеченные как внешние на локальном компьютере. Также будет предпринята попытка перевести в оперативный режим все тома на наборе динамических дисков.
-   Если динамический диск в группе дисков подключен к сети и является единственным диском в группе, то исходная группа создается заново и диск перемещается в эту группу. Если в группе есть другие диски и они находятся в сети, диск просто добавляется обратно в группу.
-   Если группа выбранного диска содержит зеркальные тома или диски RAID 5, эта команда также повторно синхронизирует эти тома.
-   Для завершения этой команды необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="BKMK_examples"></a>Примеров

Чтобы перевести диск с фокусом в режим «в сети», введите:
```
online disk
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

