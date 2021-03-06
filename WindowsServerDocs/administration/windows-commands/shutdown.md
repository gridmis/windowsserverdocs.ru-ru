---
title: shutdown
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c432f5cf-c5aa-4665-83af-0ec52c87112e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8a5170fa214d4ed639ff3b817cf949a9f44ebd6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383890"
---
# <a name="shutdown"></a>shutdown



Позволяет завершить работу или перезагружать локальные или удаленные компьютеры по одному.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
shutdown [/i | /l | /s | /r | /a | /p | /h | /e] [/f] [/m \\<ComputerName>] [/t <XXX>] [/d [p|u:]<XX>:<YY> [/c "comment"]] 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/i|Отображает **диалоговое окно Удаленное завершение работы** . Параметр **/i** должен быть первым параметром после команды. Если указан параметр **/i** , все остальные параметры игнорируются.|
|/l|Немедленное отключение текущего пользователя без периода ожидания. Параметр **/l** нельзя использовать с **параметрами/m** и **/t**.|
|/s|Завершает работу компьютера.|
|/r|Перезапускает компьютер после завершения работы.|
|/|Прерывает завершение работы системы. Действует только в течение периода ожидания. Чтобы использовать **/a**, необходимо также использовать параметр **/m** .|
|/p|Отключает только локальный компьютер (не удаленный компьютер), без времени ожидания или предупреждения. Параметр **/p** можно использовать только с параметрами **/d** или **/f**. Если компьютер не поддерживает функции выключения питания, он будет выключен при использовании **/p**, но питание компьютера останется включенным.|
|/h|Перевод локального компьютера в режим гибернации, если включен режим гибернации. Параметр **/h** можно использовать только с параметром **/f**.|
|/e|Позволяет документировать причину неожиданного завершения работы на целевом компьютере.|
|/f|Принудительно закрывает выполнение приложений без предупреждения пользователей.</br>Предупреждение. Использование параметра **/f** может привести к утрате несохраненных данных.|
|/m \\\\\<ComputerName >|Указывает целевой компьютер. Не может использоваться с параметром **/l** .|
|/t \<XXX >|Устанавливает время ожидания или задержку до *xxx* секунд перед перезагрузкой или завершением работы. Это приводит к отображению предупреждения в локальной консоли. Можно указать 0-600 секунд. Если не используется параметр **/t**, по умолчанию время ожидания составляет 30 секунд.|
|/d [p\|u:]\<XX >:\<гг >|Список причин перезапуска или завершения работы системы. Ниже приведены значения параметров.</br>**p** указывает, что запланирована перезагрузка или завершение работы.</br>**u** указывает, что причина определяется пользователем.</br>Примечание. Если значение **p** или **u** не указано, перезагрузка или завершение работы не планируется.</br>*XX* указывает номер основной причины (положительное целое число меньше 256).</br>*Гг* Указывает дополнительный номер причины (положительное целое число меньше 65536).|
|/c "\<комментарий >"|Позволяет ввести подробный комментарий о причине завершения работы. Сначала необходимо указать причину с помощью параметра **/d** . Комментарии необходимо заключать в кавычки. Можно использовать до 511 символов.|
|/?|Отображает справку в командной строке, включая список основных и вспомогательных причин, определенных на локальном компьютере.|

## <a name="remarks"></a>Замечания

-   Пользователям должно быть назначено право " **Завершение работы системы"** для завершения работы локального или удаленного администрирования компьютера, использующего команду **Shutdown** .
-   Пользователи должны быть членами группы "Администраторы", чтобы закомментировать неожиданное завершение работы локального или удаленного администрирования компьютера. Если конечный компьютер присоединен к домену, эту процедуру могут выполнять члены группы "Администраторы домена". Дополнительные сведения см. в следующих разделах:  
    -   [Локальные группы по умолчанию](https://technet.microsoft.com/library/cc785098(v=ws.10).aspx)
    -   [Группы по умолчанию](https://technet.microsoft.com/library/cc756898(v=ws.10).aspx)
-   Если вы хотите одновременно завершить работу нескольких компьютеров, можно вызвать **Завершение работы** для каждого компьютера с помощью скрипта или использовать **Shutdown** **/I** для вывода диалогового окна удаленное завершение работы.
-   Если указываются коды основных и вспомогательных причин, необходимо сначала определить эти коды на каждом компьютере, где планируется использовать причины. Если коды причин не определены на целевом компьютере, средство регистрации событий завершения работы не сможет зарегистрировать правильный текст причины.
-   Не забудьте указать, что завершение работы запланировано с помощью параметра **p:** . Пропуск **p:** указывает, что завершение работы не запланировано. Если ввести **p:** , за которым следует код причины незапланированного отключения, команда не будет выполнять завершение работы. И наоборот, если опустить **p:** и ввести код причины для запланированного завершения работы, команда не будет выполнять завершение работы.

## <a name="BKMK_examples"></a>Примеров

Чтобы принудительно закрыть и перезапустить локальный компьютер по истечении одной минуты с причиной "приложение: обслуживание (запланированное)" и комментарий "перенастройка MyApp. exe", введите:
```
shutdown /r /t 60 /c "Reconfiguring myapp.exe" /f /d p:4:1
```
Чтобы перезагрузить удаленный компьютер \\\\ServerName с теми же параметрами, введите:
```
shutdown /r /m \\servername /t 60 /c "Reconfiguring myapp.exe" /f /d p:4:1
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
