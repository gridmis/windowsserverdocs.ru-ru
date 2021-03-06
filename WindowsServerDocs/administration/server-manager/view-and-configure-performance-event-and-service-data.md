---
title: Просмотр и настройка событий производительности и данных службы
description: Диспетчер серверов
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-server-manager
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccd59c35-4dbf-48e7-88a4-c519c00184d1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55ff19988cf502c2fdc968f08f207120956217df
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383041"
---
# <a name="view-and-configure-performance-event-and-service-data"></a>Просмотр и настройка данных о производительности, событиях и службе

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе описывается просмотр и настройка записей журнала событий, счетчиков производительности и предупреждений службы, которые отображаются для локальных и удаленных серверов в диспетчер сервера.  

Данные журнала событий, служб и производительности отображаются в двух местах консоли диспетчер сервера в Windows Server.  

-   На панели мониторинга можно щелкнуть столбцы " **события**", " **производительность**" и " **службы** ", чтобы настроить данные событий, производительности и журнала службы, которые необходимо просмотреть для ролей, весь пул серверов Диспетчер сервера, созданные пользователем группы серверов и локального сервера. При щелчке гипертекстовых строк открывается диалоговое окно **Просмотр подробностей** , в котором можно указать данные, о которых необходимо получать оповещения на панели мониторинга. После настройки данных журнала событий, служб и производительности, которые необходимо выделить в эскизах панели мониторинга, записи журнала, соответствующие заданным критериям, будут перечислены в нижней части диалоговых окон **подробного представления** .  

-   Плитки **События**, **Службы** и **Производительность** являются частью домашних страниц ролей и групп. Команды меню **Задачи** этих плиток позволяют указывать конкретные данные, подлежащие сбору с управляемых серверов. Плитки содержат фильтры и запросы, предназначенные для последующего ограничения записей журнала, отображаемых в определенной плитке, если это необходимо.  

Эта статья содержит следующие разделы.  

-   [Что такое эскизы?](#BKMK_thumb)  

-   [Просмотр и настройка событий](#BKMK_events)  

-   [Просмотр и Настройка счетчиков производительности](#BKMK_perf)  

-   [Управление службами и Настройка оповещений службы](#BKMK_services)  

-   [Просмотр и копирование записей событий или производительности](#BKMK_copy)  

## <a name="BKMK_thumb"></a>Что такое эскизы?  
*Эскизы* отображаются на панели мониторинга Диспетчер сервера для каждой роли (эскиз роли отражает данные, собранные по всем серверам в пуле Диспетчер сервера, на котором выполняется роль), для каждой группы серверов в группе " **все серверы** " (все серверов в пуле диспетчер сервера) и для локального сервера. После диспетчер сервера получения данных с управляемых серверов эскизы создаются автоматически для ролей, работающих на серверах в пуле серверов.  

Если консоль диспетчер сервера запущена на клиентском компьютере в составе средства удаленного администрирования сервера, эскиз **локального сервера** отсутствует.  

Эскиз отображает выборку данных о состоянии и управляемости ролей, серверов и групп серверов. В строке заголовка эскиза изменяется цвет (и выделенные номера отображаются в левом поле), когда события, счетчики производительности, анализатор соответствия рекомендациям результаты, службы или общие проблемы управляемости соответствуют критериям, настроенным в **подробных сведениях. Просмотр** диалоговых окон, открываемых щелчком строки эскиза. Приведенная ниже таблица содержит описание данных, отображаемых в эскизах.  

|Строка эскиза|Описание|  
|---------|--------|  
|Управляемость|Управляемость сервера включает несколько мер: вне зависимости от того, доступен ли сервер в режиме «в сети» или в режиме «вне сети», является ли он доступным и передает ли он данные в диспетчер сервера, будь то пользователь, выполнивший вход на локальный компьютер, имеет достаточные права для доступа или управления удаленный сервер, если на удаленном сервере выполняется все программное обеспечение, необходимое для удаленного управления, или если сервер настроен таким образом, что обеспечивает запрос и управление с помощью диспетчер сервера. Единственными данными по управлению, которые диспетчер сервера могут быть собраны с сервера под управлением Windows Server 2003, является доступность сервера в сети или вне сети. Подробные сведения об ошибках состояния управляемости и способы их устранения см. в [руководстве по устранению неполадок диспетчера серверов](https://social.technet.microsoft.com/wiki/contents/articles/13443.windows-server-2012-server-manager-troubleshooting-guide-part-i-overview.aspx).|  
|События|Вы можете настроить строку **События** эскиза на отображение оповещений при регистрации событий, соответствующих предварительно выбранным степеням серьезности, источникам, периодам времени, серверам или ИД событий. Просмотрите сведения о событиях и измените оповещения, которые нужно просмотреть, щелкнув строку **события** и открыв диалоговое окно **Просмотр подробных сведений о событиях** для роли или группы серверов.|  
|Службы|Можно настроить строку **службы** для отображения предупреждений при обнаружении служб в роли или группе серверов, соответствующих типам запуска, состоянию службы, именам служб и серверам, указанным в диалоговом окне **сведения о службах** .<br /><br />После добавления сервера в пул серверов диспетчер сервера можно отобразить оповещения службы о службе обнаружения оборудования оболочки, если нет пользователей, выполнивших вход на управляемый сервер. Это происходит потому, что служба "Определение оборудования оболочки" выполняется только тогда, когда пользователи выполнили вход на управляемом сервере или подключены к сеансу удаленного рабочего стола на управляемом сервере. Во избежание просмотра оповещений службы "Определение оборудования оболочки" в этом случае щелкните **Службы** в эскизах для групп серверов, включая группу **Все серверы**. В диалоговом окне **Просмотр сведений о службах** в раскрывающемся списке **службы** снимите флажок для **обнаружения оборудования оболочки**и нажмите кнопку **ОК**.|  
|Производительность|Можно настроить в строке **производительности** отображение предупреждений для роли или группы серверов при возникновении предупреждений о производительности, соответствующих типам ресурсов, серверам или периодам времени, указанным в диалоговом окне **подробный обзор производительности** .<br /><br />По умолчанию счетчики производительности отключены. Управляемые серверы под управлением операционных систем более поздних версий, чем Windows Server 2003, и для которых не запущены счетчики производительности, обычно отображаются ошибки состояния управляемости, **не запущенные** на **серверах.** плитка страниц ролей или групп. Чтобы включить счетчики производительности для управляемых серверов, на странице **все серверы** щелкните правой кнопкой мыши элемент элементы на плитке **производительность** , чтобы отобразить значение **состояния счетчика** **выкл**., а затем выберите команду **запустить счетчики производительности**. Счетчики производительности также можно запустить, щелкнув правой кнопкой мыши записи для серверов на плитке **серверы** на страницах роли или группы, а затем выбрав команду **запустить счетчики производительности**.|  
|Результаты BPA|Можно настроить строку **результатов BPA** для отображения предупреждений для роли или группы серверов при обнаружении результатов проверки BPA, которые соответствуют уровням серьезности, серверам или категориям BPA, указанным в диалоговом окне **подробный обзор результатов BPA** .|  

## <a name="BKMK_events"></a>Просмотр и настройка событий  
В этом разделе вы узнаете, как настроить сбор данных журнала событий с серверов в диспетчер сервера пуле серверов и какие события должны выделяться в эскизах.  

> [!NOTE]  
> События, о которых вы получаете оповещения в эскизах, представляют собой подмножество общих событий, которые вы указываете диспетчер сервера собираются с управляемых серверов. Хотя изменение условий событий в диалоговом окне **Настройка данных события** в плитках **событий** может изменить число оповещений, отображаемых на панели мониторинга Диспетчер сервера, изменение критериев оповещения о событиях в эскизах не влияет на данные журнала событий. , собираемых с управляемых серверов.  

#### <a name="to-configure-the-events-collected-from-managed-servers"></a>Настройка событий, собираемых с управляемых серверов  

1.  В консоли диспетчер сервера откройте любую страницу, кроме панели мониторинга. События, собираемые с управляемых серверов, можно настроить в плитке **События** на страницах роли, группы серверов или локального сервера.  

2.  В меню **Задачи** плитки **События** щелкните **Настройка данных события**.  

3.  Выберите уровни серьезности событий, которые необходимо собрать с серверов в выбранной группе. Степени серьезности **Критическая**, **Ошибка** и **Предупреждение** выбраны по умолчанию.  

4.  Укажите период времени для событий. По умолчанию срок жизни событий составляет 24 часа.  

5.  Выберите файлы журнала событий, из которых должны собираться события. По умолчанию это файлы **Приложение**, **Настройка**и **Система**.  

6.  Чтобы сохранить изменения и закрыть диалоговое окно **Настройка данных события** , нажмите кнопку **ОК** . Данные события автоматически обновляются при сохранении изменений.  

#### <a name="to-configure-the-events-highlighted-in-thumbnails"></a>Настройка событий, отображаемых в эскизах  

1.  Если диспетчер сервера уже открыт, перейдите к следующему шагу. Если диспетчер серверов еще не открыт, откройте его одним из следующих способов.  

    -   На рабочем столе Windows запустите диспетчер серверов, щелкнув **Диспетчер серверов** на панели задач Windows.  

    -   На **начальном экране** Windows выберите плитку "Диспетчер серверов".  

2.  На панели мониторинга, в плитке **Роли и группы серверов** эскиза, щелкните строку **События** .  

3.  В диалоговом окне **Просмотр подробных сведений о событиях** добавьте уровень серьезности к событиям, которые необходимо отобразить. По умолчанию в эскизах отображается только оповещение для критических событий. Обратите внимание, что количество событий, отображаемых в диалоговом окне **подробное представление** , увеличивается при добавлении уровня серьезности, о котором необходимо получать оповещения.  

4.  В поле **Источники событий** выберите источники событий для оповещения. Значение по умолчанию — **All**.  

5.  Если этот эскиз предназначен для роли, установленной на нескольких серверах, или группы из нескольких серверов, в раскрывающемся списке **серверы** можно выбрать серверы, для которых требуется создать оповещения о событиях.  

6.  В поле **период времени** укажите период времени до 1440 минут, 24 часа или 1 день.  

7.  В поле **ИД событий** введите кодовые числа определенных событий для оповещения. Вы можете вводить диапазон ИД событий, разделив их дефисом ( **-** ), а также исключать ИД событий из диапазона, вводя дефис перед исключаемым ИД события или диапазоном ИД событий. Например, значение **1,3,5-99,-76** означает, что оповещения вызываются для событий с идентификаторами 1 и 3, а также для всех событий с идентификаторами в диапазоне от 5 до 99, за исключением события с идентификатором 76.  

8.  При изменении условий отображения оповещений число оповещений о событиях, отображаемых в области результатов в нижней части диалогового окна, может измениться. Выберите записи в списке и щелкните **скрыть предупреждения** , чтобы они не влияли на число оповещений, отображаемых в исходном эскизе. Для выбора нескольких оповещений нажмите и удерживайте клавишу **CTRL** при выборе оповещений. Вы также можете сделать это для оповещений, соответствующих ранее выбранным условиям оповещения о событиях, которые не нужно отображать.  

9. Щелкните **Показать все** для возврата скрытых оповещений в список.  

10. Нажмите кнопку **ОК** , чтобы сохранить изменения, закрыть диалоговое окно « **подробное представление** » и просмотреть изменения предупреждения о событиях в исходном эскизе.  

## <a name="BKMK_perf"></a>Просмотр и Настройка данных журнала производительности  
В этом разделе вы узнаете, как настроить, какие данные журнала производительности собираются с серверов в пуле диспетчер сервера серверов, а также какие предупреждения счетчиков производительности должны выделяться в эскизах.  

По умолчанию счетчики производительности отключены. Управляемые серверы под управлением операционных систем более поздних версий, чем Windows Server 2003, и для которых не запущены счетчики производительности, обычно отображаются ошибки состояния управляемости, **не запущенные** на **серверах.** плитка страниц ролей или групп. Чтобы включить счетчики производительности для управляемых серверов, на странице **все серверы** щелкните правой кнопкой мыши элемент элементы на плитке **производительность** , чтобы отобразить значение **состояния счетчика** **выкл**., а затем выберите команду **запустить счетчики производительности**. Счетчики производительности также можно запустить, щелкнув правой кнопкой мыши записи для серверов на плитке **серверы** на страницах роли или группы, а затем выбрав команду **запустить счетчики производительности**.  

> [!NOTE]  
> Оповещения производительности, отображаемые в эскизах, представляют собой подмножество общих данных счетчиков производительности, которые указывают диспетчер сервера для получения от управляемых серверов. Несмотря на то, что изменение критериев оповещения о производительности в диалоговом окне **Настройка предупреждений производительности** в плитках **производительности** может изменить число оповещений, отображаемых на панели мониторинга Диспетчер сервера, изменение критериев оповещения о производительности в эскизах. не влияет на данные журнала производительности, собираемые с управляемых серверов.  
>   
> По этой причине максимальный срок хранения данных производительности, которые можно отобразить в виде эскизов, не может быть больше, чем максимальный период отображения графика, установленный в диалоговом окне **Настройка оповещений о производительности** . Например, если значение **периода отображения графика** в диалоговом **окне Настройка оповещений о производительности** составляет **1 день**, максимальное значение для поля **период времени** в диалоговых окнах **подробного представления о производительности** , которое было открыто из Диспетчер сервера панель мониторинга может иметь **один день**, **24 часа**или **1 440 минут**.  

#### <a name="to-configure-the-performance-log-data-collected-from-managed-servers"></a>Настройка данных журнала производительности, собираемых с управляемых серверов  

1.  В консоли диспетчер сервера откройте любую страницу, кроме панели мониторинга. Данные о производительности, собираемые с управляемых серверов, можно настроить в плитке **Производительность** на страницах роли, группы серверов или локального сервера.  

2.  Для сбора данных журнала производительности с управляемых серверов счетчики производительности должны быть включены. Если счетчики производительности отключены, щелкните правой кнопкой мыши запись в списке плиток **производительности** и выберите команду **запустить счетчики производительности**. На сбор данных счетчика производительности может потребоваться время, зависящее от числа серверов, с которых собираются данные, и пропускной способности сети. Просмотрите текущее состояние в столбце **Состояние счетчика** .  

3.  В меню **Задачи** плитки **Производительность** выберите **Настроить оповещения о производительности**.  

4.  для серверов в выбранной группе или, выполняющих выбранную роль, укажите процент использования ЦП, по которому будут собираться оповещения счетчиков производительности, диспетчер сервера. Значение по умолчанию — 85%.  

5.  Укажите в мегабайтах остаток доступной памяти серверов, при достижении которого должен начинаться сбор оповещений счетчика производительности. По умолчанию выбрано 2 МБ.  

6.  Укажите период времени, отображаемый на графиках ресурсов **Загрузка ЦП** и **Доступная память** в плитке **Производительность** на выбранной странице. По умолчанию используется период в 1 день. Нажмите кнопку **Сохранить**.  

    Помните, что число оповещений о производительности в плитке **Производительность** и отображение на графике сопоставленных оповещений по времени может измениться после нажатия кнопки **Сохранить**.  

    > [!NOTE]  
    > для виртуальных машин, в которых включен [Динамическая память](https://technet.microsoft.com/library/ff817651.aspx) , увеличение порога предупреждений о производительности может привести к ложным положительным оповещениям.  

7.  Для обновления списка оповещений о производительности, собираемых с серверов, в меню **Задачи** выберите **Обновить**.  

#### <a name="to-configure-the-performance-alerts-highlighted-in-thumbnails"></a>Настройка оповещений о производительности, отображаемых в эскизах  

1.  На панели мониторинга, в плитке **Роли и группы серверов** эскиза, щелкните строку **Производительность** .  

2.  В диалоговом окне **подробное представление о производительности** установите или снимите флажки для пороговых значений производительности ресурсов, о которых требуется получать оповещения в поле **тип ресурса** . Обратите внимание, что количество предупреждений производительности, отображаемых в диалоговом окне **подробное представление** , может увеличиваться при добавлении порогового значения производительности ресурса, о котором требуется получать оповещения.  

3.  Если этот эскиз предназначен для роли, установленной на нескольких серверах, или группы из нескольких серверов, в раскрывающемся списке **серверы** можно выбрать серверы, для которых требуется создать оповещения о производительности.  

4.  В поле **период времени** укажите период времени до 1440 минут, 24 часа или 1 день.  

5.  При изменении условий отображения оповещений число оповещений, отображаемых в области результатов в нижней части диалогового окна, может измениться. Щелкните **Скрыть оповещения** , чтобы скрыть все оповещения старше текущего времени во избежание их влияния на отображение счетчика оповещений, отображаемого в эскизе источника.  

6.  Щелкните **Показать все** для возврата скрытых оповещений в список.  

7.  Нажмите кнопку **ОК** , чтобы сохранить изменения, закрыть диалоговое окно **подробное представление** и просмотреть изменения предупреждения производительности в исходном эскизе.  

#### <a name="to-view-the-properties-of-performance-alerts"></a>Просмотр свойств оповещений о производительности  

1.  Выполните одно из указанных ниже действий.  

    -   На панели мониторинга, в плитке **Роли и группы серверов** эскиза, щелкните строку **Производительность** .  

    -   Откройте домашнюю страницу роли или группы и найдите плитку **Производительность** для данной роли или группы.  

2.  Дважды щелкните в списке любое оповещение о производительности для просмотра его свойств. Или щелкните любое оповещение о производительности правой кнопкой мыши и выберите **Просмотр свойств**.  

3.  В диалоговом окне **Свойства оповещений о производительности** выберите записи журнала для просмотра информации о процессах, связанных с записью в области **Процессы**.  

4.  По завершении просмотра свойств оповещений о производительности закройте диалоговое окно.  

### <a name="analyze-performance-data-and-solve-problems"></a>Анализ данных о производительности и решение проблем  
Дополнительные сведения о анализе данных счетчиков производительности, отображаемых в диспетчер сервера, и решении проблем с производительностью на управляемых серверах см. в следующих ресурсах.  

-   [Анализ данных производительности](https://go.microsoft.com/fwlink/?LinkId=239829)  

-   [Устранение проблем с производительностью](https://go.microsoft.com/fwlink/?LinkId=239831)  

Дополнительные сведения о расширенных средствах мониторинга производительности и анализа, доступных для Windows Server 2012 и более поздних версий Windows Server, включая советник по производительности сервера 3,0, см. в разделе [производительность](https://msdn.microsoft.com/windows/hardware/gg463374.aspx) на сайте MSDN.  

## <a name="BKMK_services"></a>Управление службами и Настройка оповещений службы  
В этом разделе вы узнаете, как запускать, останавливать, перезапускать, приостанавливать или возобновлять службы, отображаемые в плитке " **службы** " на страницах группы ролей и серверов в Диспетчер сервера. Вы также можете настроить службы, о которых вы получаете оповещения, в эскизах на панели мониторинга диспетчер сервера.  

> [!NOTE]  
> Невозможно изменить тип запуска для служб, зависимостей служб, параметров восстановления или других свойств службы в плитке "службы" в диспетчер сервера. Для изменения свойств службы, отличных от состояния службы, откройте оснастку **Службы**. Ярлык для открытия оснастки " **службы** " доступен в меню " **сервис** " в Диспетчер сервера.  

#### <a name="to-start-stop-restart-pause-or-resume-a-service"></a>Запуск, остановка, перезапуск, приостановка и возобновление службы  

1.  В консоли диспетчер сервера откройте любую страницу, кроме панели мониторинга (иными словами, на любой домашней странице роли или группы).  

2.  В плитке **Службы** данной роли или группы щелкните любую службу правой кнопкой мыши.  

3.  В контекстном меню выберите выполняемое действие для данной службы. Если служба остановлена, единственным доступным действием будет ее запуск. Аналогичным образом, если служба приостановлена, единственным доступным действием будет ее возобновление.  

4.  Помните, что при запуске, остановке, перезапуске, приостановке или возобновлении службы значение столбца **Состояние** в плитке **Службы** для данной службы изменяется.  

#### <a name="to-configure-service-alerts-highlighted-in-thumbnails"></a>Настройка служебных оповещений, отображаемых в эскизах  

1.  На панели мониторинга, в плитке **Роли и группы серверов** эскиза, щелкните строку **Службы**.  

2.  В диалоговом окне **Просмотр сведений о службах** выберите типы запуска для служб, о которых требуется получать оповещения. По умолчанию выбираются **автоматические (отложенное начало)** и **автоматически** .  

3.  Выберите состояния службы, о которых вы хотите получать оповещения. По умолчанию выбрано **Все** .  

4.  Выберите службы, о которых требуется получать оповещения. По умолчанию выбрано **Все** .  

5.  Выберите серверы, связанные с ролью или группой, для которых требуется получить оповещения о службах. По умолчанию выбрано **Все** .  

6.  При изменении условий отображения оповещений число оповещений, отображаемых в области результатов в нижней части диалогового окна, может измениться. Щелкните **Скрыть оповещения** , чтобы скрыть все оповещения старше текущего времени во избежание их влияния на отображение счетчика оповещений, отображаемого в эскизе источника.  

7.  Щелкните **Показать все** для возврата скрытых оповещений в список.  

8.  Нажмите кнопку **ОК** , чтобы сохранить изменения, закрыть диалоговое окно **подробное представление** и просмотреть изменения предупреждения службы в исходном эскизе.  

## <a name="BKMK_copy"></a>Просмотр и копирование записей событий, служб и производительности  
Вы можете скопировать свойства записи события, службы или производительности в диалоговых окнах " **подробное представление** " и " **события** " и " **производительность** " для роли или группы. Щелкните правой кнопкой мыши событие или запись производительности, а затем выберите команду **Копировать**.  

Кроме того, при выделении любого события в списке плитка **События** позволяет просмотреть записи свойств данного события в нижней половине плитки. Чтобы скопировать свойства, показанные в предварительной версии, щелкните правой кнопкой мыши панель предварительного просмотра и выберите команду **Копировать**.  

## <a name="see-also"></a>См. также  
[диспетчер сервера](server-manager.md)  
[Фильтрация, сортировка и запрос данных на плитках диспетчера серверов](filter-sort-and-query-data-in-server-manager-tiles.md)  
