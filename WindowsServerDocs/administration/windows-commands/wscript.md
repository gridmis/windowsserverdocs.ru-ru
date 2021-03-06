---
title: wscript
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fbaf193-cdbd-414c-84c9-bb5720f84c29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: 5e33f3f626ddb2645643ef3bfa8971667f692295
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361801"
---
# <a name="wscript"></a>wscript



Сервер сценариев Windows предоставляет среду, в которой пользователи могут выполнять сценарии на различных языках, использующих разнообразные объектные модели для выполнения задач.

## <a name="syntax"></a>Синтаксис

```
wscript [<scriptname>] [/b] [/d] [/e:<engine>] [{/h:cscript|/h:wscript}] [/i] [/job:<identifier>] [{/logo|/nologo}] [/s] [/t:<number>] [/x] [/?] [<ScriptArguments>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|scriptname|Указывает путь и имя файла скрипта.|
|b|Задает пакетный режим, при котором не отображаются предупреждения, ошибки сценариев или входные запросы. Это противоположность **/i**.|
|/d|Запускает отладчик.|
|/e|Указывает подсистему, используемую для выполнения скрипта. Это позволяет выполнять сценарии, использующие расширение имени файла. Без параметра/e можно выполнять только скрипты, использующие зарегистрированные расширения имен файлов. Например, при попытке выполнить следующую команду:<br>```cscript test.admin```<br>Появится следующее сообщение об ошибке: ошибка ввода: обработчик скриптов для расширения файла ". admin" отсутствует.<br>Одним из преимуществ использования нестандартных расширений имен файлов является то, что оно защищает от случайного двойного щелчка сценария и выполнения чего-то, которое не нужно запускать. <br>Это не создает постоянную связь между расширением имени файла Admin и сценарием VBScript. Каждый раз при запуске скрипта, использующего расширение имени файла Admin, необходимо использовать параметр/e.|
|/h: cscript|Регистрирует **cscript. exe** в качестве сервера скриптов по умолчанию для выполнения скриптов.|
|/h: WScript|Регистрирует **WScript. exe** в качестве сервера скриптов по умолчанию для выполнения скриптов. Это значение по умолчанию, если параметр **/h** опущен.|
|/i|Указывает интерактивный режим, который отображает предупреждения, ошибки сценариев и входные запросы.</br>Это значение по умолчанию и противоположное значение **/b**.|
|/Задание: идентификатор\<>|Запускает задание, определяемое *идентификатором* в файле скрипта **. WSF** .|
|/лого|Указывает, что баннер сервера сценариев Windows отображается в консоли перед запуском скрипта.</br>Это значение по умолчанию и противоположное значение **/nologo**.|
|/nologo|Указывает, что баннер сервера сценариев Windows не отображается перед выполнением скрипта. Это противоположность **/лого**.|
|/s|Сохраняет текущие параметры командной строки для текущего пользователя.|
|/t: число\<>|Указывает максимальное время, в течение которого может выполняться скрипт (в секундах). Можно указать до 32 767 секунд.</br>Значение по умолчанию — без ограничения по времени.|
|/x|Запускает скрипт в отладчике.|
|скриптаргументс|Задает аргументы, передаваемые в скрипт. Каждому аргументу сценария должна предшествовать косая черта (/).|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Замечания

-   Для выполнения этой задачи не требуются права, соответствующие учетным данным администратора. Таким образом, по соображениям безопасности ее рекомендуется выполнять от имени пользователя, не обладающего правами на администрирование системы.
-   Чтобы открыть командную строку, на **начальном экране** введите **cmd** и щелкните **командная строка**.
-   Каждый параметр является необязательным; Однако нельзя указать аргументы скрипта без указания скрипта. Если не указать скрипт или какие-либо аргументы скрипта, **WScript. exe** выводит диалоговое окно **Параметры сервера сценариев Windows** , которое можно использовать для задания свойств глобальных скриптов для всех сценариев, выполняемых **WScript. exe** на локальном компьютере.
-   Параметр **/t** предотвращает чрезмерное выполнение скриптов путем установки таймера. Когда время превышает указанное значение, **Wscript** прерывает работу обработчика скриптов и завершает процесс.
-   Файлы сценариев Windows обычно имеют одно из следующих расширений имен файлов: **. WSF**, **. vbs**, **. js**.
-   Если дважды щелкнуть файл сценария с расширением, которое не имеет связи, откроется диалоговое окно **Открыть с помощью** . Выберите **Wscript** или **cscript**, а затем выберите **всегда использовать эту программу, чтобы открыть этот тип файлов**. Этот файл регистрирует **WScript. exe** или **cscript. exe** в качестве сервера сценариев по умолчанию для файлов этого типа.
-   Можно задать свойства для отдельных скриптов. Дополнительные сведения см. в разделе [Обзор сервера сценариев Windows](https://technet.microsoft.com/library/cc738350(v=ws.10).aspx) .
-   Сервер сценариев Windows может использовать файлы скриптов **. WSF** . Каждый файл **. WSF** может использовать несколько обработчиков скриптов и выполнять несколько заданий.

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
