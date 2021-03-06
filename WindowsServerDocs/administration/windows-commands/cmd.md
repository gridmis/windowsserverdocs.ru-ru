---
title: Cmd
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ec588db-31a9-4a73-a970-65a2c6f4abbe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 032fbea2039faa09753ac0c2b51e4b62004d36ac
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379326"
---
# <a name="cmd"></a>Cmd

Запускает новый экземпляр интерпретатора команд Cmd. exe. Если используется без параметров, **Команда cmd** отображает версию и сведения об авторских правах операционной системы.

## <a name="syntax"></a>Синтаксис

```
cmd [/c|/k] [/s] [/q] [/d] [/a|/u] [/t:{<B><F>|<F>}] [/e:{on|off}] [/f:{on|off}] [/v:{on|off}] [<String>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/c|Выполняет команду, указанную в *строке* , а затем останавливается.|
|/k|Выполняет команду, указанную в *строке* , и продолжит.|
|/s|Изменяет обработку *строки* после **/c** или **/k**.|
|/q|Отключает вывод.|
|/d|Отключает выполнение команд AutoRun.|
|/|Форматирует выходные данные внутренней команды в канал или файл как Американский национальный институт стандартов (ANSI) (ANSI).|
|/u|Форматирует выходные данные внутренней команды в канал или файл в Юникоде.|
|/t: {\<B\>\<F\>\|\<F\>}|Задает цвета фона (*B*) и переднего плана (*F*).|
|/e: вкл.|Включает расширения команд.|
|/e: выкл.|Отключает расширения команд.|
|/f: вкл.|Включает завершение имени файла и каталога.|
|/f: выкл.|Отключает завершение имен файлов и каталогов.|
|/v: вкл.|Включает отложенное расширение переменных среды.|
|/v: выкл.|Отключает отложенное расширение переменных среды.|
|Строка \<>|Указывает команду, которую требуется выполнить.|
|/?|Отображение справки в командной строке.|

В следующей таблице перечислены допустимые шестнадцатеричные цифры, которые можно использовать в качестве значений для \<B\> и \<F\>

|Значение|Цвет|
|-----|-----|
|0|Черный|
|1|Выделен|
|2|Зеленый|
|3|Голубой|
|4|Красный|
|5|Пурпурный|
|6|Желтый|
|7|Белый|
|8|Серый|
|9|Светло-синий|
|a|Светло-зеленый|
|&|Светло-голубой|
|ц|Светло-красный|
|d|Светло-фиолетовый|
|&|Светло-желтый|
|f,|Светлое белое|

## <a name="remarks"></a>Замечания

-   Использование нескольких команд

    Чтобы использовать несколько команд для \<строкового >, разделите их по разделителю команд **&&** и заключите их в кавычки. Например:

    ```
    "<Command>&&<Command>&&<Command>"
    ``` 
 
-   Обработка кавычек

    При указании параметра **/c** или **/k** **Команда cmd** обрабатывает оставшуюся часть *строки,* и кавычки сохраняются только при соблюдении следующих условий.  
    -   Параметр **/s**не используется.
    -   Вы используете ровно один набор кавычек.
    -   В кавычках не используются специальные символы (например: & < > () @ ^ |).
    -   В кавычках используется один или несколько пробельных символов.
    -   *Строка* в кавычках — это имя исполняемого файла.

    Если предыдущие условия не выполнены, *строка* обрабатывается путем проверки первого символа, чтобы проверить, является ли он открывающей кавычкой. Если первый символ является открывающей кавычкой, он удаляется вместе с закрывающей кавычкой. Любой текст, следующий за закрывающими кавычками, сохраняется.
-   Выполняются подразделы реестра

    Если параметр **/d** в *строке*не указан, cmd. exe ищет следующие подразделы реестра:

    **HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\ауторун\ REG_SZ**

    **HKEY_CURRENT_USER \Софтваре\микрософт\комманд Процессор\ауторун\ REG_EXPAND_SZ**

    Если имеется один или оба подраздела реестра, они выполняются до всех остальных переменных.

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.

-   Включение и отключение расширений команд

    Расширения команд включены по умолчанию в Windows XP. Их можно отключить для определенного процесса с помощью команды **/e: Off**. Вы можете включить или отключить расширения для всех параметров командной строки **cmd** на компьютере или сеансе пользователя, задав следующие значения **REG_DWORD** .

    **HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\енабликстенсионс\ REG_DWORD**

    **HKEY_CURRENT_USER \Софтваре\микрософт\комманд Процессор\енабликстенсионс\ REG_DWORD**

    Присвойте параметру **REG_DWORD** значение **0 × 1** (включено) или **0 × 0** (отключено) в реестре с помощью программы Regedit. exe. Заданные пользователем параметры имеют приоритет над параметрами компьютера, а параметры командной строки имеют приоритет над параметрами реестра.

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.

    When you enable command extensions, the following commands are affected:  
    -  **assoc**
    -  **call**
    -  **chdir (cd)**
    -  **color**
    -  **del (erase)**
    -  **endlocal**
    -  **for**
    -  **ftype**
    -  **goto**
    -  **if**
    -  **mkdir (md)**
    -  **popd**
    -  **prompt**
    -  **pushd**
    -  **set**
    -  **setlocal**
    -  **shift**
    -  **start** (also includes changes to external command processes)

-   Включение отложенного расширения переменных среды

    При включении отложенного расширения переменных среды можно использовать символ восклицательного знака для замены значения переменной среды во время выполнения.
-   Включение завершения имен файлов и каталогов

    По умолчанию завершение имени файла и каталога не включено. Можно включить или отключить завершение имени файла для определенного процесса команды **cmd** с параметром **/f:** {**On**|**Off**}. Можно включить или отключить завершение имени файла и каталога для всех процессов команды **cmd** на компьютере или сеанса входа пользователя, задав следующие значения **REG_DWORD** .

    **HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\комплетиончар\ REG_DWORD**

    **HKEY_LOCAL_MACHINE \Софтваре\микрософт\комманд Процессор\паскомплетиончар\ REG_DWORD**

    **HKEY_CURRENT_USER \Софтваре\микрософт\комманд Процессор\комплетиончар\ REG_DWORD**

    **HKEY_CURRENT_USER \Софтваре\микрософт\комманд Процессор\паскомплетиончар\ REG_DWORD**

    Чтобы задать значение **REG_DWORD** , запустите regedit. exe и используйте шестнадцатеричное значение управляющего символа для конкретной функции (например, **0 × 9** — TAB, а **0 × 08** — Backspace). Заданные пользователем параметры имеют приоритет над параметрами компьютера, а параметры командной строки имеют приоритет над параметрами реестра.

> [!CAUTION]
> Неправильное изменение реестра может серьезно повредить систему. Перед внесением изменений следует сделать резервную копию всех ценных данных на компьютере.

Если включить завершение имен файлов и каталогов с помощью **/f: on**, используйте сочетание клавиш CTRL + D для завершения имен каталогов и Ctrl + f для завершения имени файла. Чтобы отключить определенный символ завершения в реестре, используйте значение пробела [**0 × 20**], так как оно не является допустимым управляющим символом.

При нажатии клавиш CTRL + D или CTRL + F **Команда cmd** обрабатывает завершение имен файлов и каталогов. Эти функции сочетания клавиш добавляют символ-шаблон к *строке* (если он отсутствует), создает список совпадающих путей, а затем отображает первый соответствующий путь. Если ни один из путей не соответствует, функция завершения имени файла и каталога выдает звуковой сигнал и не изменяет отображение. Для перемещения по списку совпадающих путей нажмите клавиши CTRL + D или CTRL + F несколько раз. Для перемещения по списку назад нажмите клавишу SHIFT и CTRL + D или CTRL + F одновременно. Чтобы отменить сохраненный список совпадающих путей и создать новый список, измените *строку* и нажмите клавиши CTRL + D или CTRL + F. Если переключиться между сочетаниями CTRL + D и CTRL + F, сохраненный список соответствующих путей отбрасывается и создается новый список. Единственное различие между сочетаниями клавиш CTRL + D и CTRL + F заключается в том, что сочетание клавиш CTRL + D соответствует именам каталогов, а сочетание клавиш CTRL + F соответствует именам файлов и каталогов. Если вы используете автозаполнение имен файлов и каталогов во всех встроенных командах каталога (т. е. **CD**, **MD**или **RD**), предполагается завершение каталога.

Имя файла и каталога правильно обрабатывает имена файлов, которые содержат пробелы или специальные символы, если они заключены в кавычки для соответствующего пути.

Для следующих специальных символов требуются кавычки: & < > [] {} ^ =;! ' +, ' ~ [пробел].

Если предоставленные сведения содержат пробелы, заключите его в кавычки (например, "имя компьютера").

Если обработка имени файла и каталога выполняется из *строки*, любая часть *пути* справа от курсора отбрасывается *(в точке, где* обработано завершение).

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
