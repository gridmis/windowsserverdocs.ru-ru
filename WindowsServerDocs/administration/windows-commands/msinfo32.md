---
title: msinfo32
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a38f31d7-1766-4103-becc-9d0b87c2826d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ec08171816476cf04bbfb70637ff8253192e21b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373379"
---
# <a name="msinfo32"></a>msinfo32

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Открывает средство «сведения о системе» для отображения полного представления об оборудовании, системных компонентах и программной среде на локальном компьютере. 
## <a name="syntax"></a>Синтаксис
```
msinfo32 [/pch] [/nfo <path>] [/report <path>] [/computer <computerName>] [/showcategories] [/category <CategoryID>] [/categories {+<CategoryID>(+<CategoryID>)|+all(-<CategoryID>)}]
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                                                                                                                 Описание                                                                                                                                  |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     <path>      | Указывает файл, который должен быть открыт в формате *C:\Folder1\File1.XXX*, где *C* — буква диска, *папка1* — папка, *file1* — имя файла, а *xxx* — это расширение имени файла.<br /><br />Этот файл может иметь формат **NFO**, **XML**, **txt**или **CAB** . |
| <computerName>  |                                                                             Указывает имя целевого или локального компьютера. Это может быть имя UNC, IP-адрес или полное имя компьютера.                                                                              |
|  <CategoryID>   |                                                                                     Указывает идентификатор элемента категории. Идентификатор категории можно получить с помощью **/шовкатегориес**.                                                                                      |
|      /пч       |                                                                                                       Отображает представление журнала системы в средстве "сведения о системе".                                                                                                       |
|      /нфо       |                                     Сохраняет экспортированный файл в виде **NFO** . Если имя файла, указанное в *пути* , не заканчивается расширением **. nfo** , расширение **. nfo** автоматически добавляется к имени файла.                                      |
|     /Report     |                                               Сохраняет файл в *пути* в виде текстового файла. Имя файла сохраняется в том виде, в котором оно указано в поле *путь*. Расширение txt не добавляется к файлу, если оно не указано в параметре Path.                                                |
|    /компутер    |                                                                запускает средство "сведения о системе" для указанного удаленного компьютера. Необходимо иметь соответствующие разрешения на доступ к удаленному компьютеру.                                                                |
| /шовкатегориес |                         запускает средство системных сведений со всеми доступными идентификаторами категорий, а не отображает понятные или локализованные имена. Например, Категория программная среда отображается как категория **свенв** .                         |
|    /Category    |                                                                     запускает сведения о системе с выбранной категорией. Используйте **/шовкатегориес** для вывода списка доступных идентификаторов категорий.                                                                     |
|   /категориес   |                          Запуск системных сведений с отображением только указанных категорий или категорий. Кроме того, выходные данные ограничиваются выбранной категорией или категориями. Используйте **/шовкатегориес** для вывода списка доступных идентификаторов категорий.                          |
|       /?        |                                                                                                                     Отображение справки в командной строке.                                                                                                                     |

## <a name="remarks"></a>Примечания
Некоторые категории сведений о системе содержат большие объемы данных. Для оптимизации производительности отчетов по этим категориям можно использовать команду **start/wait** . Дополнительные сведения см. в разделе [сведения о системе](https://technet.microsoft.com/library/cc783305(v=ws.10).aspx).
## <a name="BKMK_Examples"></a>Примеров
Чтобы получить список доступных идентификаторов категорий, введите:
```
msinfo32 /showcategories
```
Чтобы запустить средство «сведения о системе» со всеми доступными сведениями, за исключением загруженных модулей, введите:
```
msinfo32 /categories +all -loadedmodules
```
Чтобы отобразить только сводные данные системы и создать NFO файл с именем сиссум. nfo, содержащий сведения в категории Сводка по системе, введите:
```
msinfo32 /nfo syssum.nfo /categories +systemsummary
```
Чтобы отобразить сведения о конфликте ресурсов и создать NFO файл с именем reконфликты. nfo, содержащий сведения о конфликтах ресурсов, введите:
```
msinfo32 /nfo conflicts.nfo /categories    +componentsproblemdevices+resourcesconflicts+resourcesforcedhardware
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

