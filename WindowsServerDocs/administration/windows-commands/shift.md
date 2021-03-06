---
title: shift
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b56574e8-570a-4cc9-bbac-1b94fbf6a47a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f74e0f1f9041a4a7b95d83772ea79376c82876de
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371248"
---
# <a name="shift"></a>shift



Изменяет расположение пакетных параметров в пакетном файле.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
shift [/n <N>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/n \<N >|Задает начало сдвига с помощью *n*-го аргумента, где *n* — любое значение от 0 до 8. Требуются расширения команд, которые включены по умолчанию.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

- Команда **SHIFT** изменяет значения параметров пакета с **%0** по **%9** путем копирования каждого параметра в предыдущий — значение **%1** копируется в **%0**, значение **%2** копируется в **%1**и т. д. Это полезно для записи пакетного файла, выполняющего одну и ту же операцию с любым количеством параметров.
- Если расширения команд включены, команда **SHIFT** поддерживает параметр командной строки **/n** . Параметр **/n** задает начало сдвига в аргументе n, где **n** — любое значение от 0 до 8. Например, **SHIFT/2** поместит **%3** в **%2**, **%4** в **%3**и т. д., и оставьте **%0** и **%1** не затрагиваются. Расширения команд включены по умолчанию.
- С помощью команды **SHIFT** можно создать пакетный файл, который может принимать более 10 параметров пакета. Если в командной строке указано более 10 параметров, то, которые появляются после десятого ( **%9**), будут сдвинуты по одной за раз в **%9**.
- Команда **SHIFT** не влияет на параметр пакета **%\\** *.
- Команда обратного **сдвига** отсутствует. После реализации команды **SHIFT** невозможно восстановить параметр пакетной службы ( **%0**), который существовал до сдвига.

## <a name="BKMK_examples"></a>Примеров

Следующие строки из примера пакетного файла с именем Микопи. bat демонстрируют, как использовать **SHIFT** с любым количеством пакетных параметров. В этом примере Микопи. BAT копирует список файлов в указанный каталог. Параметры пакета представлены аргументами каталога и имени файла.
```
@echo off 
rem MYCOPY.BAT copies any number of files
rem to a directory.
rem The command uses the following syntax:
rem mycopy dir file1 file2 ... 
set todir=%1
:getfile
shift
if "%1"=="" goto end
copy %1 %todir%
goto getfile
:end
set todir=
echo All done
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)