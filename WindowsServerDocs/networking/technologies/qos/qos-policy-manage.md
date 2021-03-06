---
title: Управление политикой QoS
description: В этом разделе приводятся инструкции по созданию и управлению политикой качества обслуживания (QoS) в Windows Server 2016.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 04fdfa54-6600-43d4-8945-35f75e15275a
manager: brianlic
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 36c30372b6cac40b603658eca9636a265801fb1a
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315445"
---
# <a name="manage-qos-policy"></a>Управление политикой QoS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел посвящен использованию мастера политики качества обслуживания для создания, изменения и удаления политики качества обслуживания.

>[!NOTE]
>  Помимо этого раздела, доступна следующая документация по управлению политиками QoS.
> 
>  - [События и ошибки политики качества обслуживания](qos-policy-errors.md)

В операционных системах Windows политика QoS сочетает в себе функциональные возможности качества обслуживания на основе стандартов с управляемостью групповая политика. Настройка этой комбинации упрощает применение политик QoS к групповая политика объектам. В состав Windows входит мастер политики качества обслуживания, помогающий выполнять следующие задачи.

-  [Создание политики качества обслуживания](#bkmk_createpolicy)

-  [Просмотр, изменение и удаление политики качества обслуживания](#bkmk_editpolicy)

##  <a name="create-a-qos-policy"></a><a name="bkmk_createpolicy"></a>Создание политики качества обслуживания

Перед созданием политики качества обслуживания важно понимать два ключевых элемента управления QoS, которые используются для управления сетевым трафиком.

- Значение DSCP

-   Частота регулирования

### <a name="prioritizing-traffic-with-dscp"></a>Определение приоритетов трафика с помощью DSCP

Как отмечалось в примере предыдущего бизнес-приложения, можно определить приоритет исходящего сетевого трафика с помощью **указания значения DSCP** , чтобы настроить политику качества обслуживания с определенным значением DSCP. 

Как описано в RFC 2474, DSCP позволяет указывать значения от 0 до 63 в поле TOS пакета IPv4 и в поле класса трафика в IPv6. Сетевые маршрутизаторы используют значение DSCP для классификации сетевых пакетов и постановки их в очередь соответствующим образом.
  
> [!NOTE]
>  По умолчанию трафик Windows имеет значение DSCP, равное 0.
  
В рамках стратегии обеспечения качества обслуживания вашей организации необходимо предусмотреть количество очередей и поведение для пакетов с разными приоритетами. Например, в Организации может быть пять очередей: трафик, учитывающий задержку, трафик управления, критически важный для бизнеса трафик, трафик с наибольшей интенсивностью и трафик с объемом передачи данных.  
  
### <a name="throttling-traffic"></a>Регулируемый трафик

Кроме значений DSCP, регулирование — еще один ключевой элемент управления для управления пропускной способностью сети. Как упоминалось ранее, можно использовать параметр **указать частоту регулирования** , чтобы настроить политику качества обслуживания с заданной частотой регулирования для исходящего трафика. С помощью регулирования политика QoS ограничивает исходящий сетевой трафик на заданную частоту регулирования. Для эффективного управления трафиком можно одновременно использовать указание значений DSCP и регулирование количества запросов.

>[!NOTE]
>По умолчанию флажок **Укажите частоту глушителя** не установлен.

Чтобы создать политику качества обслуживания, измените параметры объекта групповая политика (GPO) в средстве консоль управления групповыми политиками (GPMC). Затем GPMC открывает редактор объектов групповой политики.

Имя политики QoS должно быть уникальным. Применение политик к серверам. конечные пользователи зависят от того, где хранится политика качества обслуживания в редактор объектов групповой политики.

- Политика качества обслуживания в параметре Computer конфигурация Сеттингс\кос применяется к компьютерам независимо от пользователя, выполнившего вход в систему. Как правило, политики QoS для компьютеров используются для серверов.

- Политика качества обслуживания в пользовательской конфигурациях Сеттингс\кос политики применяется к пользователям после входа в систему, независимо от того, на каком компьютере они вошли в систему.

#### <a name="to-create-a-new-qos-policy-with-the-qos-policy-wizard"></a>Создание новой политики качества обслуживания с помощью мастера политики качества обслуживания

-   В редактор объектов групповой политики щелкните правой кнопкой мыши любой из узлов **политики качества обслуживания** и выберите команду **создать новую политику**.

### <a name="wizard-page-1---policy-profile"></a>Страница мастера 1. профиль политики

На первой странице мастера политики качества обслуживания можно указать имя политики и настроить способ управления качеством исходящего сетевого трафика.

#### <a name="to-configure-the-policy-profile-page-of-the-qos-based-policy-wizard"></a>Настройка параметров на странице "Профиль политики" мастера QoS на основе политики

1. В поле **Имя политики** введите имя политики QoS. Имя должно уникальным образом идентифицировать политику.

2. При необходимости используйте параметр **указать значение DSCP** , чтобы включить пометку DSCP, а затем настройте значение DSCP в диапазоне от 0 до 63.

3. Также при желании можно установить флажок **Укажите частоту глушителя** для включения регулировки трафика и настройки ограничения скорости. Значение частоты регулирования должно быть больше 1, и можно указать единицы в килобайтах в секунду \(кбит/с\) или мегабайт в секунду \(Мбит/с\).

4. Нажмите кнопку **Далее**.

### <a name="wizard-page-2---application-name"></a>Страница мастера 2. имя приложения

На второй странице мастера политики качества обслуживания можно применить политику ко всем приложениям, к конкретному приложению, определяемому именем исполняемого файла, к пути и имени приложения либо к серверным приложениям HTTP, обрабатывающим запросы для определенного URL-адреса.

- **Все приложения** указывает, что параметры управления трафиком на первой странице мастера политики качества обслуживания применяются ко всем приложениям.

- **Только приложения с этим именем исполняемого файла** указывают, что параметры управления трафиком на первой странице мастера политики качества обслуживания предназначены для конкретного приложения. Имя исполняемого файла должно оканчиваться расширением имени файла exe.

- **Только приложения сервера HTTP, отвечающие на запросы этого URL-адреса** , указывают, что параметры управления трафиком на первой странице мастера политики качества обслуживания применяются только к определенным приложениям HTTP-сервера.

Дополнительно можно указать путь к каталогу приложения. Путь к приложению указывается вместе с именем приложения. Путь может включать в себя переменные среды. Например, %ProgramFiles%\Путь к моему приложению\MyApp.exe или c:\program files\путь к моему приложению\myapp.exe.

>[!NOTE]
>Путь к приложению не может содержать путь, который разрешается в символьную ссылку.

URL-адрес должен соответствовать [RFC 1738](https://tools.ietf.org/html/rfc1738)в виде `http[s]://<hostname\>:<port\>/<url-path>`. Можно использовать подстановочный знак `‘*'`, для `<hostname>` и (или) `<port>`, например `https://training.\*/, https://\*.\*`, но подстановочный знак не может обменять подстроку `<hostname>` или `<port>`.

Иными словами, ни `https://my\*site/`, ни `https://\*training\*/` не являются допустимыми. 

При необходимости можно установить флажок **включить подкаталоги и файлы** , чтобы выполнить сопоставление для всех подкаталогов и файлов, следующих за URL-адресом. Например, если этот параметр установлен и URL-адрес имеет `https://training`, то политика QoS будет считать запросы` https://training/video` подходящим совпадением.

#### <a name="to-configure-the-application-name-page-of-the-qos-policy-wizard"></a>Настройка страницы «имя приложения» в мастере политики качества обслуживания

1. В **этой политике качества обслуживания применяется к**выберите **все приложения** или **только приложения с именем этого исполняемого файла**.

2. Если вы выберете параметр **Только к приложениям с именем исполняемого файла**, укажите имя исполняемого файла с расширением .EXE.

3. Нажмите кнопку **Далее**.

### <a name="wizard-page-3---ip-addresses"></a>Страница мастера 3. IP-адреса

На третьей странице мастера политики качества обслуживания можно указать условия IP-адреса для политики качества обслуживания, включая следующие.

- ко всем исходным IPv4- или IPv6-адресам либо к определенным исходным IPv4- или IPv6-адресам;

- Все адреса назначения IPv4 или IPv6 или конкретные адреса IPv4 или IPv6.

При выборе вариантов **Только к следующему IP-адресу источника** или **Только к следующему конечному IP-адресу** необходимо указать одно из следующих значений:

- IPv4-адрес, например `192.168.1.1`

- Префикс IPv4-адреса, использующий нотацию длины префикса сети, например `192.168.1.0/24`

- IPv6-адрес, например `3ffe:ffff::1`

- Префикс IPv6-адреса, например `3ffe:ffff::/48`

Если выбрать оба варианта **только для следующего ИСХОДНОГО IP** -адреса и **только для следующего конечного IP-адреса**, то оба адреса или префиксы адресов должны быть на основе IPv4 или IPv6.

Если вы указали URL-адрес для серверных приложений HTTP на предыдущей странице мастера, вы заметите, что исходный IP-адрес для политики качества обслуживания на этой странице мастера неактивен. 

Это верно, так как исходный IP-адрес является адресом HTTP-сервера и не настраивается здесь. С другой стороны, вы по-прежнему можете настроить политику, указав IP-адрес назначения. Это позволяет создавать разные политики для разных клиентов с помощью одних и тех же серверных приложений HTTP.

#### <a name="to-configure-the-ip-addresses-page-of-the-qos-policy-wizard"></a>Настройка страницы «IP-адреса» в мастере политики качества обслуживания

1. В **этой политике качества обслуживания применяется к** (источнику), выберите **любой исходный IP-адрес** или **только для следующего IP-адреса источника**.

2. Если выбран **только следующий IP-адрес источника**, укажите адрес IPv4 или IPv6 или префикс.

3. В **этой политике качества обслуживания применяется к** (назначение), выберите **любой адрес назначения** или **только для следующего IP-адреса назначения.**

4. Если вы выбрали **только следующий IP-адрес назначения**, укажите адрес IPv4 или IPv6 или префикс, соответствующий типу адреса или префикса, указанного для адреса источника.

5.  Нажмите кнопку **Далее**.  

### <a name="wizard-page-4---protocols-and-ports"></a>Страница мастера 4. протоколы и порты

На четвертой странице мастера политики качества обслуживания можно указать типы трафика и порты, которые управляются параметрами на первой странице мастера. Можно указать:  
-   трафик TCP, трафик UDP или оба типа трафика;  

-   все исходные порты, диапазон исходных портов или определенный исходный порт;

-   Все порты назначения, диапазон портов назначения или указанный порт назначения  

#### <a name="to-configure-the-protocols-and-ports-page-of-the-qos-policy-wizard"></a>Настройка страницы протоколы и порты мастера политики качества обслуживания

1. В разделе **Выберите протокол, к которому применяется политика QoS:** выберите параметр **TCP**, **UDP** или **TCP и UDP**.

2. В разделе **Укажите номер исходного порта** выберите параметр **Любой исходный порт** или **Номер исходного порта**.

3. Если вы выбрали **из этого номера порта источника**, введите номер порта от 1 до 65535.

     При необходимости можно указать диапазон портов в формате "*низкий*:*высокий*", где *Low* и *High* представляют нижние границы и верхние границы диапазона портов включительно. *Низкие* и *высокие* значения должны быть числами от 1 до 65535. Между символом двоеточия (:) и числами не должно быть пробела.

4. В разделе **Укажите номер порта назначения** выберите параметр **Любой порт назначения** или **Номер целевого порта**.

5. Если на предыдущем этапе был выбран параметр **Номер целевого порта**, введите номер порта в диапазоне от 1 до 65535.

Чтобы завершить создание политики качества обслуживания, нажмите кнопку **Готово** на странице **протоколы и порты** мастера политики качества обслуживания. По завершении новая политика QoS появится в области сведений редактор объектов групповой политики.  
  
Чтобы применить параметры политики качества обслуживания к пользователям или компьютерам, свяжите объект групповой политики, в котором расположены политики качества обслуживания, с контейнером служб домен Active Directory Services, таким как домен, сайт или подразделение.  
  
##  <a name="view-edit-or-delete-a-qos-policy"></a><a name="bkmk_editpolicy"></a>Просмотр, изменение и удаление политики качества обслуживания

Страницы мастера политики качества обслуживания, описанные выше, соответствуют страницам свойств, которые отображаются при просмотре или изменении свойств политики.  
  
### <a name="to-view-the-properties-of-a-qos-policy"></a>Просмотр свойств политики QoS  
  
-   Щелкните правой кнопкой мыши имя политики в области сведений редактор объектов групповой политики и выберите пункт **Свойства**.  
  
     Редактор объектов групповой политики отображает страницу свойств со следующими вкладками:  
  
    -   "Профиль политики";  
  
    -   Имя приложения  
  
    -   "IP-адреса";  
  
    -   Протоколы и порты  
  
### <a name="to-edit-a-qos-policy"></a>Изменение политики QoS  
  
-   Щелкните правой кнопкой мыши имя политики в области сведений редактор объектов групповой политики и выберите **изменить существующую политику**.  
  
     В редактор объектов групповой политики отображается диалоговое окно **изменение существующей политики качества обслуживания** .  
  
### <a name="to-delete-a-qos-policy"></a>Удаление политики QoS  
  
-   Щелкните правой кнопкой мыши имя политики в области сведений редактор объектов групповой политики и выберите пункт **удалить политику**.  
  
### <a name="qos-policy-gpmc-reporting"></a>Отчеты GPMC политики QoS 

После применения нескольких политик качества обслуживания в Организации может быть полезно или необходимо периодически просматривать применение политик. Сводные данные о политиках QoS для конкретного пользователя или компьютера можно просмотреть с помощью модуля создания отчетов GPMC.  
  
#### <a name="to-run-the-group-policy-results-wizard-for-a-report-of-qos-policies"></a>Запуск мастера групповая политика результатов для отчета о политиках QoS  
  
-   В GPMC щелкните правой кнопкой мыши узел **результаты групповая политика** и выберите пункт меню для **мастера групповая политиканых результатов.**  
  
После создания результатов групповая политика перейдите на вкладку **Параметры** . На вкладке "Параметры" политики качества обслуживания можно найти в узлах "политика **конфигурации** компьютера \ конфигурация сеттингс\кос" и "политика пользователя \ конфигурация сеттингс\кос".  
  
На вкладке **Параметры** политики качества обслуживания перечисляются по именам политик качества обслуживания с их значением DSCP, частотой регулирования, условиями политики и победившим объектом групповой политики, перечисленным в той же строке.  
  
Представление результатов групповая политика уникальным образом определяет победивший объект GPO. Если несколько объектов групповой политики имеют политики QoS с одинаковым именем политики качества обслуживания, применяется объект групповой политики с самым высоким приоритетом GPO. Это наиболее выгодный объект групповой политики. Конфликтующие политики QoS (идентифицируемые по имени политики), присоединенные к GPO с более низким приоритетом, не применяются. Обратите внимание, что приоритеты GPO определяют, какие политики QoS развертываются в сайте, домене или подразделении соответствующим образом. После развертывания на уровне пользователя или компьютера [правила приоритета политики качества обслуживания](#BKMK_precedencerules) определяют, какой трафик разрешен и заблокирован.  
  
Значения DSCP, частота регулирования и условия политики качества обслуживания также отображаются в редактор объектов групповой политики (GPOE).  
  
### <a name="advanced-settings-for-roaming-and-remote-users"></a>Дополнительные параметры для перемещаемых и удаленных пользователей  
Политика QoS предназначена для управления трафиком в корпоративной сети. В сценариях для мобильных устройств пользователи могут отправлять или отключать трафик в корпоративной сети. Так как политики качества обслуживания не имеют отношения к сети предприятия, политики QoS включены только для сетевых интерфейсов, подключенных к корпоративной среде для Windows 8, Windows 7 или Windows Vista.  
  
Например, пользователь может подключить свой портативный компьютер к корпоративной сети через виртуальную частную сеть (VPN) из кафе. Для VPN-подключения физический сетевой интерфейс (например, беспроводная сеть) не будет применять политики QoS. Однако в интерфейсе VPN будут применяться политики качества обслуживания, так как он подключается к корпоративной сети. Если пользователь позже войдет в другую сеть предприятия, не имеющую отношения доверия AD DS, политики качества обслуживания не будут включены.  
  
Обратите внимание, что эти мобильные сценарии не применяются к рабочим нагрузкам сервера. Например, сервер с несколькими сетевыми адаптерами может находиться на границе сети предприятия. ИТ-отдел может использовать политики QoS для регулирования трафика, егрессес предприятие; Однако этот сетевой адаптер, отправляющий трафик исходящего трафика, не обязательно подключается к корпоративной сети. По этой причине политики QoS всегда включены во всех сетевых интерфейсах компьютера, работающего под Windows Server 2012.  
  
> [!NOTE]
>  Избирательное включение применяется только к политикам QoS, а не к дополнительным параметрам качества обслуживания, обсуждаемым далее в этом документе.  
  
### <a name="advanced-qos-settings"></a>Дополнительные параметры качества обслуживания

Дополнительные параметры качества обслуживания предоставляют ИТ администраторам дополнительные элементы управления для управления потреблением сети компьютеров и маркировками DSCP. Дополнительные параметры качества обслуживания применяются только на уровне компьютера, в то время как политики качества обслуживания можно применять как к компьютерам, так и к уровням пользователей.

#### <a name="to-configure-advanced-qos-settings"></a>Настройка дополнительных параметров QoS

1.  Щелкните **Конфигурация компьютера**и выберите **параметры Windows в групповая политика**.
  
2.  Щелкните правой кнопкой мыши **политику QoS**и выберите пункт **Дополнительные параметры качества обслуживания**.

     На следующем рисунке показаны две дополнительные вкладки параметров качества обслуживания: **входящий TCP-трафик** и **Переопределение разметки DSCP**.
  
> [!NOTE]
>  Дополнительные параметры качества обслуживания — это параметры групповая политика на уровне компьютера.
  
#### <a name="advanced-qos-settings-inbound-tcp-traffic"></a>Дополнительные параметры качества обслуживания: входящий трафик TCP

**Входящий TCP-трафик** контролирует использование пропускной способности TCP на стороне получателя, а политики QoS влияют на исходящий трафик TCP и UDP. 

Установив более низкий уровень пропускной способности на вкладке **входящий TCP-трафик** , TCP ограничит размер объявленного окна приема TCP. В результате этого параметра будут увеличены показатели пропускной способности и использование канала для TCP-подключений с более высокой пропускной способностью или задержками (продукт задержки пропускной способности). По умолчанию для компьютеров под управлением Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 2008 и Windows Vista устанавливается максимальный уровень пропускной способности.
  
Окно приема TCP изменилось в Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 2008 и Windows Vista из предыдущих версий Windows. В предыдущих версиях Windows размер окна приема TCP ограничен 64 килобайт (КБ), в то время как Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 2008 и Windows Vista динамически занимают окно приема до 16 мегабайт (МБ ). В элементе управления входящим TCP-трафиком можно управлять уровнем пропускной способности входящего трафика, установив максимальное значение, на которое может увеличиваться окно приема TCP. Уровни соответствуют следующим максимальным значениям. 
  
|Уровень входящей пропускной способности|Максимальное значение|  
|------------------------|-------|  
|0|64 КБ|
|1|256 КБ|
|2|1 MБ|
|3|16 МБ|

Фактический размер окна может быть больше или меньше максимального значения в зависимости от условий сети.

###### <a name="to-set-the-tcp-receive-side-window"></a>Установка окна приема TCP

1. В редактор объектов групповой политики выберите **Политика локального компьютера**, щелкните **Параметры Windows**, щелкните правой кнопкой мыши пункт **политика QoS**и выберите пункт **Дополнительные параметры качества обслуживания**.
  
2. В поле **пропускная способность приема TCP**выберите **настроить TCP-передачу пропускной**способности, а затем выберите нужный уровень пропускной способности.

3.  Свяжите объект групповой политики с подразделением.

#### <a name="advanced-qos-settings-dscp-marking-override"></a>Дополнительные параметры качества обслуживания: изменение разметки DSCP

Переопределение разметки DSCP позволяет приложениям указывать или "помечать" — значения DSCP, отличные от указанных в политиках QoS. Указывая, что приложениям разрешено устанавливать значения DSCP, приложения могут задавать ненулевые значения DSCP. 

При указании параметра **Ignore**для приложений, использующих API-интерфейсы QoS, значения DSCP будут равны нулю, и только политики качества обслуживания могут устанавливать значения DSCP. 

По умолчанию компьютеры под управлением Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows Server 2008 и Windows Vista позволяют приложениям указывать значения DSCP; приложения и устройства, которые не используют API качества обслуживания, не переопределяются.

##### <a name="wireless-multimedia-and-dscp-values"></a>Беспроводные мультимедийные значения и DSCP

[Wi-Fi Alliance](https://go.microsoft.com/fwlink/?LinkId=160769) установила сертификацию для беспроводного мультимедиа \(WMM\), определяющего четыре категории доступа \(WMM_AC\) для определения приоритетов сетевого трафика, передаваемого в беспроводной сети Wi\-Fi. К категориям доступа относятся \(в порядке убывания приоритета\): голоса, видео, наилучших усилий и фона; соответственно, сокращения во, VI, BK. Спецификация WMM определяет, какие значения DSCP соответствуют каждой из четырех категорий доступа:
  
|Значение DSCP|Категория доступа WMM|
|----------|-------------------|
|48-63|Voice (во)|
|32-47|Видео (VI)|
|24-31, 0-7|Лучшие усилия (будьте)|
|8-23|Фон (BK)|

Вы можете создать политики QoS, которые используют эти значения DSCP, чтобы убедиться, что портативные компьютеры с сертифицированным Wi\-Fi™ для беспроводных адаптеров WMM получают приоритетную обработку при связи с сетью Wi\-Fi для точек доступа на WMM.
  
### <a name="qos-policy-precedence-rules"></a><a name="BKMK_precedencerules"></a>Правила приоритета политики качества обслуживания

Как и в случае с приоритетами GPO, политики QoS имеют правила приоритета для разрешения конфликтов, когда несколько политик качества обслуживания применяются к определенному набору трафика. Для исходящего трафика TCP или UDP в каждый момент времени может применяться только одна политика качества обслуживания. Это означает, что политики качества обслуживания не имеют совокупного эффекта, например, где будут суммироваться нормы регулирования.

Как правило, политика QoS с наиболее подходящими условиями — WINS. При применении нескольких политик качества обслуживания правила делятся на три категории: на уровне пользователя и на уровне компьютера; приложения и пятиэлементные сети; и в пятиэлементные сети.

По *сети пятиэлементные*мы имеем в виду, что IP-адрес источника, конечный IP-адрес, исходный порт, порт назначения и протокол \(TCP/UDP\).  

 **Политика качества обслуживания на уровне пользователя имеет приоритет над политикой качества обслуживания на уровне компьютера**

Это правило значительно облегчает управление групповыми политиками качества обслуживания сетевых администраторов, особенно для политик на основе групп пользователей. Например, если администратор сети хочет определить политику качества обслуживания для группы пользователей, он может просто создать и распространить объект групповой политики для этой группы. Им не нужно беспокоиться о том, на каких компьютерах эти пользователи входят в систему, а также о том, будут ли эти компьютеры иметь конфликтующие политики QoS, так как при наличии конфликта Политика уровня пользователя всегда имеет приоритет.

> [!NOTE]
>  Политика качества обслуживания уровня пользователя применима только к трафику, созданному этим пользователем. Другие пользователи определенного компьютера и самого компьютера не будут подвергаться политикам качества обслуживания, определенным для этого пользователя.

 **Особенности приложения и приоритет по сравнению с сетью пятиэлементные**

Когда несколько политик QoS соответствуют определенному трафику, применяется более конкретная политика. В политиках, определяющих приложения, политика, включающая в себя путь к файлу отправляющего приложения, считается более конкретной, чем другая политика, идентифицирующая только имя приложения (без пути). Если несколько политик с приложениями по-прежнему применяются, то правила приоритета используют пятиэлементные сети для поиска наилучшего соответствия.

Кроме того, несколько политик качества обслуживания могут применяться к одному и тому же трафику путем указания не перекрывающихся условий. Между условиями приложений и пятиэлементные сети политика, определяющая приложение, считается более специфичной и примененной. 

Например, policy_A указывает только имя приложения (App. exe), и policy_B Указывает конечный IP-адрес 192.168.1.0/24. Когда эти политики QoS конфликтуют \(приложение. exe отправляет трафик на IP-адрес в диапазоне от 192.168.4.0/24\), применяется policy_A.

 **Более конкретное преимущество имеет приоритет в пределах пятиэлементные сети.**

Для конфликтов политик в сети пятиэлементные приоритет имеет политика с наиболее подходящими условиями. Например, предположим, что policy_C указывает исходный IP-адрес "Any", IP-адрес назначения 10.0.0.1, порт источника "Any", порт назначения "Any" и протокол "TCP". 

Далее предположим, что policy_D указывает исходный IP-адрес "Any", IP-адрес назначения 10.0.0.1, порт источника "Any", порт назначения 80 и протокол "TCP". Затем policy_C и policy_D совпадают подключения к адресу назначения 10.0.0.1:80. Так как политика QoS применяет политику с наиболее конкретными условиями сопоставления, policy_D имеет приоритет в этом примере.  
  
Однако политики качества обслуживания могут иметь одинаковое число условий. Например, несколько политик могут указывать только одну (но не ту же) часть сети пятиэлементные. В пятиэлементные сети следующий порядок — от более высокого до более низкого приоритета:

- Исходный IP-адрес

- IP-адрес назначения

- Исходный порт

- Порт назначения

- Протокол (TCP или UDP).

В определенном условии, таком как IP-адрес, более конкретный IP-адрес обрабатывается с более высоким приоритетом. Например, IP-адрес 192.168.4.1 является более конкретным, чем 192.168.4.0/24.

Разработайте политики QoS как можно точнее, чтобы упростить способность Организации понять, какие политики действуют.

В следующем разделе этого раздела описаны [события и ошибки политики QoS](qos-policy-errors.md).

Для первого раздела в этом руководстве см. раздел [Политика качества обслуживания (QoS)](qos-policy-top.md).
