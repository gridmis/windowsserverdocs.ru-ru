---
title: Фильтрация, сортировка и запросы данных на плитках диспетчера серверов
description: Диспетчер серверов
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-server-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8786f791-73e5-4c75-8d12-46e88a196976
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 51c0e1f3af727c4e7ddf18024fab9a95808d2338
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868915"
---
# <a name="filter-sort-and-query-data-in-server-manager-tiles"></a>Фильтрация, сортировка и запросы данных на плитках диспетчера серверов

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В Windows Server, плитки диспетчера сервера позволяют фильтровать и сортировать данные, создавать и сохранять пользовательские запросы. Можно сортировать, использовать фильтры ключевых слов и запускать запросы для списка записей в плитках событий, производительности, анализатор соответствия рекомендациям, служб ролей и компонентов на сервере страниц роли или группы в диспетчере сервера.  
  
Эта статья содержит следующие разделы.  
  
-   [Фильтрация списка записей в плитках](#BKMK_tiles)  
  
-   [Сортировка списка записей в плитках](#BKMK_sort)  
  
-   [Создание и запуск пользовательских запросов для данных плитки](#BKMK_query)  
  
## <a name="BKMK_tiles"></a>Фильтрация списка записей в плитках  
С помощью текстового поля **Фильтр** можно ограничить отображаемый в плитке список записей только записями, содержащими указанную текстовую строку.  
  
#### <a name="to-apply-a-filter-to-the-list-of-entries-in-a-tile"></a>Применение фильтра к списку записей в плитке  
  
1.  Откройте страницу групп ролей или серверов в диспетчере сервера.  
  
2.  В **фильтра** текстовом поле появляется Плитка событий, производительности, анализатор соответствия рекомендациям, служб или ролей и компонентов введите строку, на котором нужно выполнить фильтрацию.  
  
    Например, если вы хотите найти события с кодом 1014, введите **1014** в **фильтра** текстовое поле. В результате будут возвращены все собранные события, содержащие строку **1014** хотя бы в одном поле.  
  
3.  Обратите внимание, что фильтр меняет текст описания под названием плитки. Вместо **Все результаты** текст описания содержит **Отфильтрованные результаты**.  
  
4.  Чтобы очистить фильтр, удалите строку в поле фильтрации или щелкните кнопку **X**.  
  
## <a name="BKMK_sort"></a>Сортировка списка записей в плитках  
Сортировка списка записей в плитках диспетчера серверов, нужно щелкнуть заголовок столбца. При первом щелчке заголовка значения столбца сортируются в буквенно-цифровом порядке по возрастанию (отображается стрелка вверх), при повторном щелчке заголовка значения столбца сортируются в том же порядке по убыванию (отображается стрелка вниз).  
  
## <a name="BKMK_query"></a>Создание и запуск пользовательских запросов для данных плитки  
Вы можете создавать пользовательские запросы в плитках событий, производительности, анализатор соответствия рекомендациям, служб или ролей и компонентов в диспетчере сервера. По умолчанию область панели инструментов плитки, в которой выбираются условия пользовательского запроса является скрытым; Нажмите кнопку **разверните** (кнопка шеврона на правом краю панели инструментов плитки) для отображения критериям запроса.  
  
#### <a name="to-create-a-custom-query-for-tile-data"></a>Создание пользовательских запросов для данных плитки  
  
1.  Откройте страницу групп ролей или серверов в диспетчере сервера.  
  
2.  В плитке событий, производительности, анализатор соответствия рекомендациям, служб или ролей и компонентов, разверните область создания запросов, нажав кнопку **разверните**.  
  
3.  Нажмите кнопку **добавить условие** чтобы открыть список атрибутов (или полей), применимых к записям в плитке.  
  
4.  Выберите критерии для добавления. Когда вы закончите, нажмите кнопку **добавить**. Выбранное условие добавится в область создания запросов.  
  
5.  Щелкните гипертекстовый оператор для его выбора. Например, для числовых условий и условий даты и времени оператором по умолчанию является **меньше или равно**.  
  
6.  Укажите допустимые значения для условия. Например, если вы выбрали **даты и времени**, укажите дату в формате *дд.мм.гггг*.  
  
7.  Чтобы добавить в запрос дополнительные условия, повторите шаги, начиная с третьего.  
  
    Вы можете добавлять условия, дублирующие уже существующие в запросе, но они будут добавлены с оператором **или**.  
  
    Например, для запроса идентификаторов событий 1003 или 1014, нужно сначала добавить в запрос условие идентификатора, сделать его значение равным **1003**, а затем добавьте второе условие идентификатора к запросу, сделав его значение второй идентификатор равен  **1014**. Конечный запрос будет выглядеть так: **и ID равно 1003 или ID равно 1014**.  
  
8.  Закончив добавлять условия и указывать операторы и значения, нажмите кнопку **Сохранить** , чтобы сохранить запрос.  
  
9. Введите понятное имя запроса. Например, запрос, созданный на предыдущем шаге, может иметь имя **События лицензирования**.  
  
10. После просмотра результатов запроса нажмите кнопку **Очистить все**, чтобы очистить все фильтры и запросы и отобразить все записи списка.  
  
11. Чтобы выполнить сохраненный запрос, щелкните **Сохраненные поисковые запросы**и выберите имя сохраненного запроса, который хотите выполнить.  
  
12. Чтобы удалить сохраненный запрос, щелкните **Сохраненные поисковые запросы**, затем щелкните **X** возле имени сохраненного запроса, который хотите удалить.  
  
## <a name="see-also"></a>См. также  
[Диспетчер серверов](server-manager.md)  
[Просмотр и настройка производительности, событий и служб данных](view-and-configure-performance-event-and-service-data.md)  
  

