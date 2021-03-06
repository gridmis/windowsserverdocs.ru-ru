---
title: cd
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 932d9cc1-3dff-40da-835c-1cb0894874f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed0942232eb205a8198d4b3d366ca9482af1f4b3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379709"
---
# <a name="cd"></a>cd



Отображает имя или изменяет текущий каталог. Если используется только с буквой диска (например, `cd C:`), на **компакт-** диске отображаются имена текущего каталога на указанном диске. Если используется без параметров, на **компакт-диске** отображается текущий диск и каталог.

> [!NOTE]
> Эта команда аналогична команде **chdir** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
cd [/d] [<Drive>:][<Path>]
cd [..]
chdir [/d] [<Drive>:][<Path>]
chdir [..]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/d|Изменяет текущий диск, а также текущий каталог для диска.|
|> \<диска:|Указывает диск для вывода или изменения (если он отличается от текущего диска).|
|\<путь >|Указывает путь к каталогу, который требуется отобразить или изменить.|
|[..]|Указывает, что вы хотите перейти к родительской папке.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

Если расширения команд включены, для команды **CD** применяются следующие условия.
- Строка текущего каталога преобразуется в использование того же регистра, что и имена на диске. Например, `cd C:\TEMP` задаст текущий каталог C:\Temp, если это так на диске.
- Пробелы не считаются разделителями, поэтому *путь* может содержать пробелы, не заключенные в кавычки. Например:  
  ```
  cd username\programs\start menu
  ```  
  то же самое, что:  
  ```
  cd "username\programs\start menu"
  ```  
  Однако если расширения отключены, необходимо учитывать кавычки.

Чтобы отключить расширения команд, введите:
```
cmd /e:off
```

## <a name="BKMK_examples"></a>Примеров

Корневой каталог является вершиной иерархии каталогов для диска. Чтобы вернуться к корневому каталогу, введите:
```
cd\
```
Чтобы изменить каталог по умолчанию на диске, отличном от используемого, введите:
```
cd [<Drive>:\[<Directory>]]
```
Чтобы проверить изменение каталога, введите:
```
cd [<Drive>:]
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)