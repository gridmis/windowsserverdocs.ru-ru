---
title: copy
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9624d4a1-349a-4693-ad00-1d1d4e59e9ac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 102fd6b59516b04b8986ee47b52f521be73f04de
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379038"
---
# <a name="copy"></a>copy



Копирует один или несколько файлов из одного расположения в другое.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
copy [/d] [/v] [/n] [/y | /-y] [/z] [/a | /b] <Source> [/a | /b] [+<Source> [/a | /b] [+ ...]] [<Destination> [/a | /b]]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/d|Позволяет сохранить копируемые зашифрованные файлы в виде расшифрованных файлов в месте назначения.|
|/v|Проверяет, правильно ли записаны новые файлы.|
|параметра|Использует короткое имя файла (если доступно) при копировании файла с именем длиннее восьми символов или с расширением имени файла длиннее трех символов.|
|/y|Подавляет запрос на подтверждение перезаписи существующего целевого файла.|
|/-и|Выводит запрос на подтверждение перезаписи существующего целевого файла.|
|/z|Копирует сетевые файлы в перезапускаемый режим.|
|/|Указывает текстовый файл ASCII.|
|b|Указывает на двоичный файл.|
|> источника \<|Обязательный. Указывает расположение, из которого необходимо скопировать файл или набор файлов. *Источник* может состоять из буквы диска и двоеточия, имени каталога, имени файла или их сочетания.|
|> назначения \<|Обязательный. Указывает расположение, в которое необходимо скопировать файл или набор файлов. *Назначение* может состоять из буквы диска и двоеточия, имени каталога, имени файла или их сочетания.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

-   Можно скопировать текстовый файл ASCII, в котором используется символ конца файла (CTRL + Z), чтобы указать конец файла.
-   Использование **/a**

    Когда параметр **/a** предшествует или следует за списком файлов в командной строке, он применяется ко всем файлам, перечисленным до техпор, пока не встретится **копия** . В этом случае **/b** применяется к файлу, предшествующему **/b**.

    Действие **/a** зависит от его расположения в строке командной строки. Когда параметр **/a** стоит после *Source*, **Copy** обрабатывает файл как ASCII-файл и копирует данные, предшествующие первому символу конца файла (Ctrl + Z).

    Когда параметр **/a** следует за *назначением*, **Copy** добавляет символ конца файла (Ctrl + Z) в качестве последнего символа файла.
-   Использование **/b**

    **/b** указывает интерпретатору команд считывать число байтов, указанное размером файла в каталоге. **/b** — это значение по умолчанию для **Copy**, если только **копирование** не объединяет файлы.

    Когда **/b** предшествует или следует за списком файлов в командной строке, он применяется ко всем файлам в списке **до тех пор** , пока не встретится параметр **/a**. В этом случае **/a** применяется к файлу, предшествующему **/a**.

    Результат **/b** зависит от его расположения в строке команды. Когда **/b** следует *источник*, **копирование** копирует весь файл, включая любой символ конца файла (Ctrl + Z).

    Когда **/b** следует *назначение*, при **копировании** не добавляется символ конца файла (Ctrl + Z).
-   Использование **/v**

    Если операция записи не может быть проверена, появится сообщение об ошибке. Хотя ошибки записи редко возникают при **копировании**, можно использовать **/v** для проверки правильности записи важных данных. Параметр командной строки **/v** также замедляет команду **Copy** , так как необходимо проверить каждый сектор, записанный на диске.
-   Использование **/y** и **/-и**

    Если в переменной среды КОПИКМД предустановлен параметр **/y** , его можно переопределить с помощью **/-и** в командной строке. По умолчанию при замене этого параметра выводится запрос, если команда **Copy** не выполняется в пакетном скрипте.
-   Добавление файлов

    Чтобы добавить файлы, укажите один файл для *назначения*, но для *источника* — несколько файлов (используйте символы-шаблоны или *file1*+*file2*+формате *файл3* ).
-   Использование **/z**

    Если во время фазы копирования теряется соединение (например, если сервер переходит в автономный режим), **копирование/z** возобновляется после восстановления подключения. **/z** также отображает процент выполнения операции копирования для каждого файла.
-   Копирование на устройства и с устройств

    Имя устройства можно заменить одним или несколькими экземплярами *источника* или *назначения*.
-   Использование или пропуск **/b** при копировании на устройство

    Если *назначением* является устройство (например, COM1 или LPT1), то **/b** данные копируются на устройство в двоичном режиме. В двоичном режиме **copy/b** копирует все символы (включая такие специальные символы, как CTRL + C, CTRL + S, CTRL + Z и Enter) на устройство как данные. Однако если параметр **/b**не указан, данные копируются на устройство в режиме ASCII. В режиме ASCII специальные символы могут привести к объединению файлов во время процесса копирования.
-   Использование файла назначения по умолчанию

    Если целевой файл не указан, создается копия с тем же именем, датой изменения и временем изменения, что и в исходном файле. Новая копия хранится в текущем каталоге на текущем диске. Если исходный файл находится на текущем диске и в текущем каталоге, и не указан другой диск или каталог для целевого файла, команда **Copy** остановится и отобразится следующее сообщение об ошибке:

    `File cannot be copied onto itself`

    `0 File(s) copied`
-   Объединение файлов

    Если в *источнике*указано более одного файла, **скопируйте** все они в один файл, используя имя файла, указанное в поле *назначение*. При **копировании** предполагается, что Объединенные файлы являются файлами ASCII, если не используется параметр **/b** .
-   Копирование файлов нулевой длины

    **Копирование** не приводит к копированию файлов, имеющих длину 0 байт. Скопируйте эти файлы с помощью **команды xcopy** .
-   Изменение времени и даты файла

    Если необходимо назначить в файл текущее время и дату без изменения файла, используйте следующий синтаксис:  
    ```
    copy /b <Source> +,,
    ```  
    Запятые обозначают опущение параметра *Destination* .
-   Копирование файлов в подкаталогах

    Чтобы скопировать все файлы и подкаталоги каталога, используйте команду **xcopy** .
-   Команда **копирования** с другими параметрами доступна в консоли восстановления.

## <a name="BKMK_examples"></a>Примеров

Чтобы скопировать файл с именем MEMO. doc в поле Letter. doc на текущем диске и убедиться, что символ конца файла (CTRL + Z) находится в конце скопированного файла, введите:
```
copy memo.doc letter.doc /a
```
Чтобы скопировать файл с именем перебора. Typ из текущего диска и каталога в существующий каталог с именем птиц, расположенный на диске C, введите:
```
copy robin.typ c:\birds
```
Если каталог птиц не существует, файл Renamed. Typ копируется в файл с именем птиц, расположенный в корневом каталоге на диске C.

Чтобы объединить Mar89. rpt, Apr89. rpt и May89. rpt, расположенные в текущем каталоге, и поместить их в файл с именем Report (также в текущем каталоге), введите:
```
copy mar89.rpt + apr89.rpt + may89.rpt Report
```
При объединении файлов **копирование** помечает конечный файл текущими датой и временем. Если параметр *Destination*не указан, файлы объединяются и сохраняются под именем первого файла в списке. Например, чтобы объединить все файлы в отчете, если файл с именем Report уже существует, введите:
```
copy report + mar89.rpt + apr89.rpt + may89.rpt
```
Чтобы объединить все файлы в текущем каталоге с расширением txt в один файл с именем Combine. doc, введите:
```
copy *.txt Combined.doc 
```
Если требуется объединить несколько двоичных файлов в один, используйте подстановочные знаки, включите **/b**. Это предотвращает расинтерпретацию CTRL + Z в качестве символа конца файла в Windows. Например, введите:
```
copy /b *.exe Combined.exe
```

> [!CAUTION]
> При объединении двоичных файлов результирующий файл может оказаться непригодным для использования из-за внутреннего форматирования.

В следующем примере **Copy** объединяет каждый файл с расширением txt с соответствующим ref-файлом. Результатом является файл с таким же именем файла, но с расширением doc. **Copy** объединяет file1. txt с file1. ref в формат file1. doc, а затем **Copy** объединяет file2. txt с file2. ref в Form file2. doc и т. д. Например, введите:
```
copy *.txt + *.ref *.doc
```
Чтобы объединить все файлы с расширением txt, а затем объединить все файлы с расширением. ref в один файл с именем Combine. doc, введите:
```
copy *.txt + *.ref Combined.doc
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)