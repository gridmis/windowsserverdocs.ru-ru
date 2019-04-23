---
title: robocopy
description: Узнайте, как использовать команду robocopy в Windows и Windows Server для копирования файлов
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4c6e8e9-fcb3-4a4a-9d04-2d8c367b6354
author: coreyp-at-msft
ms.author: coreyp
manager: lizapo
ms.date: 07/25/2018
ms.openlocfilehash: c4218331f716dc530e01f28a295cebd83c0e6616
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818115"
---
# <a name="robocopy"></a>robocopy



Копирует данные файла.

## <a name="syntax"></a>Синтаксис

```
robocopy <Source> <Destination> [<File>[ ...]] [<Options>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Источник >|Указывает путь к исходному каталогу.|
|\<Назначения >|Указывает путь к целевому каталогу.|
|\<Файл >|Указывает файл или файлы для копирования. Можно использовать подстановочные знаки (**&#42;** или **?**), если требуется. Если **файл** параметр не указан, **\*.\*** используется в качестве значения по умолчанию.|
|\<Параметры >|Указывает параметры для использования с **robocopy** команды.|

### <a name="copy-options"></a>Параметры копирования

|Параметр|Описание|
|------|-----------|
|/s|Копирование подкаталогов. Обратите внимание на то, что этот параметр исключает пустые каталоги.|
|/e|Копирование подкаталогов. Обратите внимание на то, что этот параметр включает пустые каталоги. Дополнительные сведения см. в разделе ["Примечания"](#BKMK_remarks).|
|/LEV:\<N >|Копирует только верхние *N* уровни исходного дерева папок.|
|/ z|Копирование файлов в режиме перезапуска.|
|/b|Копирование файлов в режиме резервного копирования.|
|/ZB|Использует режиме перезапуска. Если доступ запрещен, этот параметр использует режим резервного копирования.|
|/EFSRAW|Копирует все зашифрованные файлы в режиме RAW файловой системы EFS.|
|/copy:\<CopyFlags>|Задает свойства для копирования. Ниже приведены допустимые значения для этого параметра:</br>**D** данных</br>**Объект** атрибуты</br>**T** метки времени</br>**S** NTFS список управления доступом (ACL)</br>**O** информация о владельце</br>**U** информации аудита</br>Значение по умолчанию для **флаги копирования** — **DAT** (данных, атрибутов и меток времени).|
|/dcopy:\<флаги копирования\>|Определяет, что нужно скопировать для каталогов. Значение по умолчанию — DA. Варианты: D = данные, A = атрибуты и T = метки времени.|
|/ сек|Копирует файлы с безопасностью (эквивалентно **/Copy: DATS**).|
|/ COPYALL|Копирует все сведения о файле (эквивалентно **: datsou**).|
|/NOCOPY|Копирует не сведения о файле (полезна при работе с **/очистка**).|
|/ secfix|Безопасность файлов исправления для всех файлов, даже пропустить те, которые.|
|/timfix|Время исправления файлов для всех файлов, даже пропустить те, которые.|
|параметром/Purge|Удаляет целевые файлы и каталоги, которые больше не существуют в источнике. Дополнительные сведения см. в разделе ["Примечания"](#BKMK_remarks).|
|/ MIR|Зеркально отражает дереве папок (эквивалентно **/e** , а также **/очистка**). Дополнительные сведения см. в разделе ["Примечания"](#BKMK_remarks).|
|/MOV|Перемещение файлов и удаляет их из источника после их копирования.|
|/ Move|Перемещение файлов и каталогов и удаляет их из источника после их копирования.|
|/a+:[RASHCNET]|Добавляет указанные атрибуты скопированные файлы.|
|/a-:[RASHCNET]|Удаляет указанные атрибуты из скопированные файлы.|
|/ create|Создает дерево каталогов и только файлы нулевой длины.|
|/ fat|Создает целевые файлы с помощью знаков FAT имен файлов 8.3 только.|
|/256|Отключает поддержку очень длинные пути, (длиннее 256 символов).|
|/ мес:\<N >|Мониторинг источника и запускается снова, при более чем *N* обнаружения изменений.|
|/mot:\<M >|Отслеживает источника и запускается снова в *M* минут при обнаружении изменений.|
|/MT [: N]|Создает многопоточных копии с *N* потоков. *N* должно быть целым числом от 1 до 128. Значение по умолчанию для *N* — 8.</br>**/MT** параметр нельзя использовать с **/IPG** и **/EFSRAW** параметров.</br>Перенаправление выходных данных с помощью **/LOG** параметр для повышения производительности.</br>Примечание. Параметр/MT применяется к Windows Server 2008 R2 и Windows 7.|
|/RH:hhmm-ччмм|Указывает время начала новых копий.|
|/PF|Проверки выполняются раз на основе файлов (не на проход).|
|/ipg:n|Задает разрыв между пакетов, бесплатная полоса пропускания по медленной линии.|
|/SL|Следует символьную ссылку и копирует целевой объект.|

> [!IMPORTANT]
> При использовании **/secfix** скопируйте параметр, укажите тип возвращаемых данных безопасности, которые необходимо скопировать с помощью одного из этих дополнительных параметров копирования также:</br>&GT;-   **/COPYALL**</br>> -   **/COPY:O**</br>&GT;- **/COPY:S**</br>&GT;- **/COPY:U**</br>> -   **/SEC**

### <a name="file-selection-options"></a>Параметры выбора файла

|Параметр|Описание|
|------|-----------|
|/a|Копирует только файлы, для которого **архив** атрибут имеет значение.|
|/m|Копирует только файлы, для которого **архив** атрибут имеет значение и сбрасывает **архив** атрибута.|
|/ IA: [RASHCNETO]|Включает в себя только те файлы, для которых задано одно из указанных атрибутов.|
|/xa:[RASHCNETO]|Исключает файлы, для которых задано одно из указанных атрибутов.|
|/XF \<имя файла > [...]|Исключает файлы, которые соответствуют указанным имен или путей. Обратите внимание, что *FileName* может включать символы-шаблоны (**&#42;** и **?**).|
|/xd \<Directory>[ ...]|Исключает каталогов, соответствующих указанным имена и пути.|
|/xc|Исключает измененные файлы.|
|/xn|Исключает более новые файлы.|
|/xo|Исключает старых файлов.|
|/xx|Исключает дополнительные файлы и папки.|
|/xl|Исключает ничего «нет» файлы и каталоги.|
|/Is|Включает и те же файлы.|
|/IT|Включает файлы «использование».|
|/ max:\<N >|Указывает максимальный размер файла (чтобы исключить файлы больше *N* байт).|
|/MIN:\<N >|Указывает минимальный размер файла (чтобы исключить файлы размером менее *N* байт).|
|/MaxAge:\<N >|Определяет максимальный срок действия (чтобы исключить файлы старше чем *N* дней или дата).|
|/MINAGE:\<N >|Указывает минимальный возраст файла (исключить файлы новее, чем *N* дней или дата).|
|/maxlad:\<N>|Указывает максимально дату последнего обращения (исключает файлы, неиспользуемое с момента *N*).|
|/MINLAD:\<N >|Указывает минимальные дату последнего обращения (исключает файлы, используемые с момента *N*) Если *N* — меньше, чем 1900 *N* указывает число дней. В противном случае *N* указывает дату в формате ГГГГММДД.|
|/Xj|Исключает точек соединения, которые обычно включаются по умолчанию.|
|/FFT|Предполагается, что файл FAT раз (точность две секунды).|
|/DST|Компенсирует разница во времени перехода на летнее время один час.|
|/XJD|Исключает точки соединения для каталогов.|
|/xjf|Исключает точки соединения для файлов.|

### <a name="retry-options"></a>Параметры повтора

|Параметр|Описание|
|------|-----------|
|/r:\<N>|Указывает число повторных попыток для неудавшихся копий. Значение по умолчанию *N* составляет 1 000 000 (один миллион повторы).|
|/w:\<N >|Указывает время ожидания между повторными попытками в секундах. Значение по умолчанию *N* — 30 (30 секунд времени ожидания).|
|/ REG|Сохраняет значения, указанные в **/r** и **/w** параметры как параметры по умолчанию в реестре.|
|/TBD|Указывает, что система будет ожидать имена общих ресурсов определить (ошибка 67 при повторном).|

### <a name="logging-options"></a>Параметры ведения журнала

|Параметр|Описание|
|------|-----------|
|/l|Указывает, что файлы, которые будут указаны только (и не копируется, удаления или отметки времени).|
|/x|Сообщает все дополнительные файлы, не только те, которые выбраны.|
|/v|Создает подробные выходные данные и отображает все пропущенные файлы.|
|/TS|Включает в себя отметки времени исходного файла в выходных данных.|
|/ fp|Включает полный путь имена файлов в выходных данных.|
|/ bytes|Печать размеры, в байтах.|
|/NS|Указывает, что размер файла не в журнал.|
|/nc|Указывает, что классы файлов не для занесения в журнал.|
|/NFL|Указывает, что имена файлов не для занесения в журнал.|
|/ndl|Указывает, что имена каталогов не для занесения в журнал.|
|/NP|Указывает, что ход выполнения операции (число файлов или каталогов, копируются в данный момент) не будут отображаться.|
|/eta|Отображение предполагаемого времени прибытия (ETA), скопированных файлов.|
|/log:\<LogFile>|Записывает выходные данные о состоянии в файл журнала (перезаписывает существующий файл журнала).|
|/log+:\<LogFile>|Записывает выходные данные о состоянии в файл журнала (добавляет выходные данные в существующий файл журнала).|
|/ Unicode|Отображает вывод состояния в виде текста в Юникоде.|
|/unilog:\<LogFile>|Записывает выходные данные в файл журнала как текст в Юникоде (перезаписывает существующий файл журнала) состояние.|
|/unilog+:\<LogFile>|Записывает выходные данные в файл журнала как текст в Юникоде (добавляет выходные данные в существующий файл журнала) состояние.|
|/TEE|Записывает выходные данные о состоянии, в окне консоли, а также в файл журнала.|
|/NJH|Указывает, что отсутствует заголовок задания.|
|/NJS|Указывает, что не Сводка по заданию.|

### <a name="job-options"></a>Параметры задания

|Параметр|Описание|
|------|-----------|
|/ задания:\<имя_задания >|Указывает, что параметры должны быть производными от указанный файл задания.|
|/ Сохранение:\<имя_задания >|Указывает, что параметры должны быть сохранены в файле заданий.|
|/ выйти из программы|Завершает работу после обработки командной строки (для просмотра параметров).|
|/nosd|Указывает, что каталог источника не указан.|
|/NODD|Указывает, что каталог назначения не указан.|
|/If|Включает указанные файлы.|

### <a name="exit-return-codes"></a>Коды выхода (результат)
Значение | Описание
-- | --
0 | Файлы не скопированы. Ошибка не обнаружена.  Файлы не были несоответствие. Эти файлы уже существуют в каталоге назначения. Таким образом операция копирования была пропущена.
1 | Все файлы были успешно скопированы.
2 | Существуют некоторые дополнительные файлы в каталоге назначения, которые отсутствуют в исходном каталоге. Файлы не скопированы.
3 | Некоторые файлы были скопированы. Дополнительные файлы, не присутствует. Ошибка не обнаружена.
5 | Некоторые файлы были скопированы. Некоторые файлы были совпадают. Ошибка не обнаружена.
6 | Дополнительные файлы и несоответствующие файлы существуют. Файлы не были скопированы, и были обнаружены без ошибок. Это означает, что эти файлы уже существуют в каталоге назначения.
7 | Файлы были скопированы, несоответствие файлов присутствовал и присутствовали дополнительные файлы.
8 | Несколько файлов не был скопирован.

> [!NOTE]
> Значение, превышающее 8 указывает на наличие по крайней мере один сбой во время операции копирования.

### <a name="BKMK_remarks"></a>"Примечания"

-   **/MIR** параметр равнозначен параметру **/e** , а также **/очистка** параметры с помощью одного небольшого различия в поведении:  
    -   С помощью **/e** , а также **/очистка** параметры, если конечный каталог существует, параметры безопасности каталога назначения не будут перезаписаны.
    -   С помощью **/MIR** параметр, если конечный каталог существует, параметры безопасности каталога назначения будут перезаписаны.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)