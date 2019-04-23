---
title: tasklist
description: Узнайте, как отобразить список процессов, запущенных на локальном или удаленном компьютере.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8dbe30ee-1484-46be-917b-5ca3ff4fdc9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: abb36c8c794836387af5547f3706e910dc06fa42
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843005"
---
# <a name="tasklist"></a>tasklist

Отображение списка процессов на локальном компьютере или на удаленном компьютере. **Tasklist** заменяет **tlist** средство.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
tasklist [/s <Computer> [/u [<Domain>\]<UserName> [/p <Password>]]] [{/m <Module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <Filter> [/fi <Filter> [ ... ]]]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/s \<компьютер >|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u [\<домена >\\\]\<имя пользователя >|Выполняет команду с разрешениями учетной записи пользователя, который задается параметром *UserName* или *домена*\*имя пользователя *. **/u** может быть указано только в том случае, если **/s** указан. По умолчанию используется разрешения пользователя, вошедшего в систему на компьютер, который выполняет команду.|
|/p \<пароль >|Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.|
|/m \<модуля >|Список всех задач с загруженными модулями библиотеки DLL, которые соответствуют указанному критерию. Если имя модуля не указан, данный параметр отображает все модули, загруженные каждой задачей.|
|/ SVC|Выводит все сведения службы для каждого процесса без усечения. Допустим, если **/fo** параметр имеет значение **таблицы**.|
|/v|Отображение подробных сведений о задании в выходных данных. Для завершения подробные выходные данные без усечения, используйте **/v** и **/SVC** друг с другом.|
|/FO {таблицы \| списка \| csv}|Задает формат выходных данных. Допустимые значения: **таблицы**, **списка**, и **csv**. Формат по умолчанию для выходных данных — **таблицы**.|
|/NH|Подавляет заголовки столбцов в выходных данных. Допустим, если **/fo** параметр имеет значение **таблицы** или **csv**.|
|/FI \<фильтра >|Указывает типы процессов, чтобы включить в или исключить из запроса. См. в следующей таблице допустимыми именами фильтров, операторов и значений.|
|/?|Отображение справки в командной строке.|

### <a name="filter-names-operators-and-values"></a>Фильтровать имена, операторы и значения

|Имя фильтра|Допустимые операторы|Допустимые значения|
|-----------|---------------|------------|
|СОСТОЯНИЕ|eq, ne|ПОД УПРАВЛЕНИЕМ | НЕ ОТВЕЧАЕТ | НЕИЗВЕСТНО|
|IMAGENAME|eq, ne|Имя образа|
|ИД процесса|eq, ne, gt, lt, ge, le|Значение PID|
|СЕАНС|eq, ne, gt, lt, ge, le|Номер сеанса|
|ИМЯ СЕАНСА|eq, ne|Имя сеанса|
|ВРЕМЯ ЦП|eq, ne, gt, lt, ge, le|Время ЦП в формате *HH ***:*** мм ***:*** SS*, где *мм* и *SS* находятся в диапазоне от 0 и 59 и *HH* является любой unsigned номер|
|MEMUSAGE|eq, ne, gt, lt, ge, le|Использование памяти в КБ|
|ИМЯ ПОЛЬЗОВАТЕЛЯ|eq, ne|Любое допустимое имя пользователя|
|СЛУЖБЫ|eq, ne|Служебное имя|
|ЗАГОЛОВОК ОКНА|eq, ne|Заголовок окна|
|МОДУЛИ|eq, ne|Имя DLL|

## <a name="remarks"></a>Примечания

Заголовок ОКНА и статус фильтры не поддерживаются при указании удаленной системы.

## <a name="BKMK_examples"></a>Примеры

Вывод списка всех задач с Идентификатором процесса, превышающую 1000, и отобразить их в формате CSV, введите следующую команду:
```
tasklist /v /fi "PID gt 1000" /fo csv
```
Чтобы получить список системных процессов, выполняющихся в данный момент, введите следующую команду:
```
tasklist /fi "USERNAME ne NT AUTHORITY\SYSTEM" /fi "STATUS eq running"
```
Чтобы просмотреть подробные сведения для всех процессов, работающих в данный момент, введите:
```
tasklist /v /fi "STATUS eq running"
```
Чтобы получить список всех сведения службы для процессов на удаленном компьютере «Srvmain», который DLL имя которых начинается с «ntdll», введите следующую команду:
```
tasklist /s srvmain /svc /fi "MODULES eq ntdll*"
```
Чтобы получить список процессов на удаленном компьютере «Srvmain», используя учетные данные учетной записи пользователя, вошедшего в систему, введите следующую команду:
```
tasklist /s srvmain 
```
Чтобы получить список процессов на удаленном компьютере «Srvmain», используя учетные данные учетной записи пользователя Hiropln, введите следующую команду:
```
tasklist /s srvmain /u maindom\hiropln /p p@ssW23
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)