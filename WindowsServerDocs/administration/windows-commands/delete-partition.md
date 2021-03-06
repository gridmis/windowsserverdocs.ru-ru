---
title: удалить секцию
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65752312-cb16-46f6-870f-1b95c507b101
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 46a214f26e7c21f6ae08eb16d95fd898bd949b0f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378664"
---
# <a name="delete-partition"></a>удалить секцию



Удаляет раздел с фокусом.

## <a name="syntax"></a>Синтаксис

```
delete partition [noerr] [override]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|крывают|Позволяет программе DiskPart удалять любые разделы независимо от типа. Как правило, DiskPart позволяет удалять только известные разделы данных.|
|Noerr|только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!CAUTION]
> Удаление секции на динамическом диске может привести к удалению всех динамических томов на диске, тем самым удаляя все данные и оставляя диск в поврежденном состоянии. Чтобы удалить динамический том, вместо него следует использовать команду **Удалить том** . Секции можно удалять с динамических дисков, но они не должны создаваться. Например, можно удалить Нераспознанный раздел таблицы разделов GPT на динамическом диске GPT. Удаление такого раздела не приводит к тому, что полученное свободное место станет доступным. Эта команда позволяет рекламе пространство на поврежденном неработающем динамическом диске в аварийной ситуации, когда нельзя использовать команду **Clean** в DiskPart.
> -   Нельзя удалить системный раздел, загрузочный раздел или любой раздел, содержащий активный файл подкачки или данные аварийного дампа.
> -   Для выполнения этой операции необходимо выбрать секцию. Используйте команду **Выбор секции** , чтобы выбрать секцию и переместить фокус на нее.

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить раздел с фокусом, введите:
```
delete partition
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

