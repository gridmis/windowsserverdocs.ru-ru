---
title: Управление работоспособностью системы в Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3043f83b-389c-4f37-a1ff-85afe99314fa
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: bbe05c0564e706ef0227e723a52bd10b2f774756
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80311075"
---
# <a name="manage-system-health-in-windows-server-essentials"></a>Управление работоспособностью системы в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 В этом разделе описывается просмотр всех оповещений в сети и реагирование на них с помощью панели мониторинга.  
  
> [!NOTE]
>  В Windows Server Essentials и Windows Server 2012 R2 с установленной ролью Windows Server Essentials службы оповещения о работоспособности для сервера и клиентских компьютеров в сети больше не отображаются в средстве просмотра оповещений, но их можно просмотреть на вкладке **отчеты о работоспособности** на **домашней** странице.  
  
 Windows Server Essentials активно отслеживает каждый компьютер, подключенный к серверу, и оповещает администратора о проблемах, связанных с работоспособностью системы, включая критические обновления, отсутствие защиты от вредоносных программ, устаревшее определение вирусов на клиенте. Компьютеры и другие важные проблемы, требующие вмешательства. Эти проблемы отображаются как оповещения в средстве просмотра оповещений, которые можно запустить с панели мониторинга сервера или панели запуска клиентского компьютера в Windows Server Essentials или на вкладке **отчеты о работоспособности** в Windows Server Essentials. По умолчанию оповещения обновляются каждые 30 минут, но вы сможете проверить сеть на наличие оповещений в любое время, нажав кнопку **Обновить** в средстве просмотра оповещений или на вкладке **Отчеты о работоспособности**.  
  
 Следующие разделы содержат сведения об оповещениях, их просмотре и реагировании на них в средстве просмотра оповещений, а также инструкции по настройке сервера на получение уведомлений по электронной почте:  
  
-   [О надстройке отчета о работоспособности](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_AddIn)  
  
-   [Просмотр предупреждений с помощью средства просмотра предупреждений](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_View)  
  
-   [Упорядочение оповещений в средстве просмотра оповещений](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Organize)  
  
-   [Ответ на предупреждения](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Respond)  
  
-   [Настройка уведомлений по электронной почте для оповещений](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Email)  
  
-   [Потенциальные оповещения компьютера](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Potential)  
  
##  <a name="about-the-health-report-add-in"></a><a name="BKMK_AddIn"></a>О надстройке отчета о работоспособности  
 Надстройка отчета о работоспособности для Windows Server Essentials предоставляет общую информацию о сети Windows Server Essentials и позволяет распространить эту информацию другим пользователям. Эти сведения можно просматривать на вкладке **Отчеты** панели мониторинга. На вкладке **Отчеты** можно выполнить следующие действия:  
  
-   [Создание отчета по запросу или по расписанию](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Generate)  
  
-   [Настройка содержимого отчета](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Customize)  
  
-   [Отправить отчет по электронной почте](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_emailreport)  
  
> [!NOTE]
>  **Windows Server Essentials:** Вы можете скачать надстройку отчета о работоспособности для Windows Server Essentials из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=266342).  
>   
>  **Windows Server Essentials:** По умолчанию надстройка отчетов о работоспособности интегрирована с Windows Server Essentials или Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience, а отчеты о работоспособности отображаются на вкладке **отчеты о работоспособности** **домашней** страницы панели мониторинга.  
  
###  <a name="generate-a-report-on-demand-or-on-schedule"></a><a name="BKMK_Generate"></a>Создание отчета по запросу или по расписанию  
 После установки надстройки отчета о работоспособности и перезапуска панели мониторинга на панель добавляется новая вкладка **Отчеты**. Вы можете создать отчет о работоспособности по требованию в любое время, щелкнув задачу **Создать отчет о работоспособности** на вкладке **Отчеты**.  
  
 После создания отчета о работоспособности на панели списка создается новый элемент, идентифицируемый по дате и времени создания отчета. Чтобы открыть элемент, дважды щелкните его на панели списка или выберите его и щелкните **Открыть отчет о работоспособности** в области задач. Отчет отображается в новом окне в формате HTML.  
  
 Помимо создания отчета вручную, можно также настроить автоматическое создание отчета по расписанию ежедневно или каждый час. Для этого в области задач щелкните **Настройка параметров отчета о работоспособности**, а затем щелкните вкладку **Расписание и электронная почта** . По умолчанию функция **расписания** отключена, и ее можно включить, установив флажок **создать отчет о работоспособности в запланированное время** .  
  
###  <a name="customize-the-content-of-the-report"></a><a name="BKMK_Customize"></a>Настройка содержимого отчета  
 Отчет о работоспособности содержит следующее:  
  
- **Критические оповещения и предупреждения** Эти сведения соответствуют критическим оповещениям и предупреждениям, отображаемым в средстве просмотра оповещений на панели мониторинга. Информационные оповещения в отчет о работоспособности не включаются.  
  
- **Критические ошибки в журналах событий** Выполняется проверка журналов приложений и служб, а ошибки, зарегистрированные за последние 24 часа, отображаются в разделе **Сведения** отчета.  
  
- **Архивация данных сервера** Сведения о последней архивации сервера отображаются в разделе **Сведения** отчета.  
  
- **Службы, запускаемые автоматически, не работают** Если служба автоматического запуска не работает, во время создания отчета сведения об этой службе отображаются в разделе **Сведения** отчета.  
  
- **Обновления** Вы можете просмотреть состояние обновления сервера и всех клиентских компьютеров в разделе **Сведения**.  
  
- **Хранилище** Список дисков и их емкость представлены в разделе **Сведения**.  
  
  В отчете о работоспособности сначала просмотрите раздел **Сводка**, а затем проверьте наличие этих элементов с красным значком ошибки или желтым значком предупреждения, выберите ссылку **Сведения** в той же строке, чтобы просмотреть сведения об элементе.  
  
  Если вы не заинтересованы в некоторых точках данных, включаемых в отчет по умолчанию, можно настроить содержимое отчета, нажав кнопку **Настройка параметров отчетов о работоспособности** в области задач, а затем перейдя на вкладку **содержимое** . Снимите флажки для содержимого, которое не должно отображаться в отчете. Например, если имеется собственный план резервного копирования сервера и вы не хотите видеть предупреждения о резервных копиях сервера, можно исключить резервные копии сервера из отчета, сняв флажок **Архивация сервера** .  
  
###  <a name="email-the-report"></a><a name="BKMK_emailreport"></a>Отправить отчет по электронной почте  
 Потребность выполнять вход в панель мониторинга для чтения отчетов по-прежнему доставляет неудобства некоторым администраторам, особенно в том случае, если они управляют сразу несколькими серверами. Если включена возможность использования электронной почты, после создания отчета на определенный список адресов электронной почты отправляется сообщение с содержимым отчета. Администратор может легко просмотреть этот отчет с любого устройства или из любого клиентского приложения и убедиться, что сервер работает в оптимальном режиме.  
  
 После включения электронной почты измените параметры SMTP в диалоговом окне **Настроить параметры отчетов о работоспособности** и укажите список получателей сообщения электронной почты. После этого в области задач будет отображаться новая задача: **Отправить отчет о работоспособности по электронной почте**. Дополнительные сведения о параметрах SMTP см. в разделе [Настройка электронных уведомлений для оповещений](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Email).  
  
 Вы можете выбрать существующий отчет и затем нажать кнопку **Отправить отчет о работоспособности по электронной почте**. Вы также можете создать новый отчет и обеспечить его автоматическую отправку в папку "Входящие". Если вы настроили расписание для автоматического создания отчета, отчет будет каждый день (или каждый час) автоматически доставляться в папку "Входящие"  согласно расписанию.  
  
##  <a name="view-alerts-by-using-the-alert-viewer"></a><a name="BKMK_View"></a>Просмотр предупреждений с помощью средства просмотра предупреждений  
 В этом разделе описывается использование панели мониторинга или панели запуска для открытия средства просмотра оповещений в целях просмотра состояния работоспособности всех компьютеров в сети сервера.  
  
#### <a name="to-open-the-alert-viewer-by-using-the-dashboard"></a>Открытие средства просмотра оповещений с помощью панели мониторинга  
  
1.  Откройте Панель администрирования.  
  
2.  На панели навигации выберите любой из отображаемых значков оповещений (критических, предупреждающих или информационных). Откроется средство просмотра оповещений.  
  
#### <a name="to-open-the-alert-viewer-from-the-launchpad"></a>Открытие средства просмотра оповещений из панели запуска  
  
1.  Откройте панель запуска с компьютера, подключенного к серверу. При получении запроса выполните вход в Панель запуска с помощью имени пользователя и пароля.  
  
2.  Щелкните любой из отображаемых значков оповещений (критические, предупреждающих и информационных) в нижней части панели запуска, чтобы открыть средство просмотра оповещений, и следуйте инструкциям, отображаемым в области сведений этого средство, для разрешения оповещения.  
  
##  <a name="organize-alerts-in-the-alert-viewer"></a><a name="BKMK_Organize"></a>Упорядочение оповещений в средстве просмотра оповещений  
 Вы можете упорядочить оповещения в средстве просмотра оповещений и отобразить их по степени серьезности (критические, предупреждающие или информационные) либо по имени компьютера.  
  
#### <a name="to-organize-alerts-in-the-alert-viewer"></a>Упорядочение оповещений в средстве просмотра оповещений  
  
1.  Откройте Панель администрирования.  
  
2.  На панели навигации выберите любой из отображаемых значков оповещений (критических, предупреждающих или информационных). Откроется средство просмотра оповещений.  
  
3.  Разверните раскрывающийся список **Упорядочить**, а затем выполните одно из следующих действий:  
  
    1.  Выберите **Фильтровать по компьютерам** и щелкните имя компьютера, для которого требуется просмотреть оповещения. При этом в средстве просмотра оповещений отображаются только оповещения для выбранного компьютера.  
  
    2.  Выберите **Фильтровать по типам оповещений** и выберите тип оповещений (критические, предупреждающие или информационные), которые требуется просмотреть. При этом в средстве просмотра оповещения отображаются только оповещения выбранного типа.  
  
##  <a name="respond-to-alerts"></a><a name="BKMK_Respond"></a>Ответ на предупреждения  
 При возникновении оповещения вы можете выполнить одно из следующих действий:  
  
-   [Разрешение предупреждения](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Resolve)  
  
-   [Игнорировать оповещение](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [Включение предупреждения](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [Удаление оповещения](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_4)  
  
###  <a name="resolve-an-alert"></a><a name="BKMK_Resolve"></a>Разрешение предупреждения  
 Следуйте инструкциям в средстве просмотра оповещений для разрешения оповещения. После разрешения оповещения оно по-прежнему отображается в средстве просмотра оповещений до его обновления.  
  
###  <a name="ignore-an-alert"></a><a name="BKMK_3"></a>Игнорировать оповещение  
 Вы можете игнорировать оповещение, если собираетесь отреагировать на него позднее. Когда оповещение игнорируется, оно по-прежнему указывается в средстве просмотра оповещений, однако отключено и недоступно. Игнорируемое оповещение не включается в общую оценку работоспособности компьютера. Чтобы обработать игнорируемое оповещение, необходимо сначала включить его.  
  
##### <a name="to-ignore-an-alert"></a>Пропуск оповещения  
  
1. Откройте панель запуска на компьютере, подключенном к серверу Windows Server Essentials.  
  
2. В панели запуска щелкните любой из отображаемых значков оповещений (критически важных, предупреждающих и информационных). Откроется средство просмотра оповещений.  
  
3. В средстве просмотра оповещения выберите то оповещение, которое требуется игнорировать, а затем в разделе **Задачи** щелкните **Пропуск оповещения**.  
  
   Для реагирования на отключенное оповещение необходимо сначала включить его.  
  
###  <a name="enable-an-alert"></a><a name="BKMK_5"></a>Включение предупреждения  
 Можно включить оповещение, которое ранее вы решили игнорировать. После включения оповещения можно разрешить или удалить его по мере необходимости. Оповещение, помеченное в качестве игнорируемого, отображается как отключенное. При включении ранее отключенного оповещения оно становится активным и снова включается в общую оценку работоспособности компьютеров.  
  
##### <a name="to-enable-an-alert"></a>Включение оповещения  
  
1.  Откройте панель запуска с компьютера, подключенного к серверу.  
  
2.  В панели запуска щелкните любой из отображаемых значков оповещений (критически важных, предупреждающих и информационных), чтобы открыть средство просмотра оповещений.  
  
3.  В средстве просмотра оповещения, щелкните правой кнопкой мыши оповещение, которое необходимо включить, и выберите пункт **Включить оповещение**.  
  
###  <a name="delete-an-alert"></a><a name="BKMK_4"></a>Удаление оповещения  
 Если вы не хотите разрешать или игнорировать оповещение, его можно удалить. Оповещения, созданные для компьютера, можно удалить с помощью средства просмотра оповещений на панели запуска. Если после удаления оповещения сервер снова обнаруживает проблему в следующем цикле оценки работоспособности сети, он создает новое оповещение.  
  
##### <a name="to-delete-an-alert"></a>Удаление оповещения  
  
1.  Откройте панель запуска с компьютера, подключенного к серверу.  
  
2.  В панели запуска щелкните любой из отображаемых значков оповещений (критически важных, предупреждающих и информационных), чтобы открыть средство просмотра оповещений.  
  
3.  В средстве просмотра оповещения, щелкните правой кнопкой мыши оповещение, которое необходимо удалить, и выберите пункт **Удаление оповещения**.  
  
##  <a name="set-up-email-notifications-for-alerts"></a><a name="BKMK_Email"></a>Настройка уведомлений по электронной почте для оповещений  
 Вы можете настроить сервер на отправку уведомлений по электронной почте в случае возникновения оповещений. Электронные уведомления для таких оповещений содержат информацию о проблемах сети и мерах по их устранению; эти сведения аналогичны тем, которые отображаются в средстве просмотра оповещений. Некоторые оценки работоспособности сети выполняются программно.  
  
 При настройке сервера на отправку электронных уведомлений для оповещений уведомление отправляется для тех оповещений, которые были обнаружены во время оценки работоспособности сети. Однако в сообщении электронной почты отражены не все оповещения, зарегистрированные в средстве просмотра оповещений.  
  
 Каждые 30 минут на сервере выполняется задача оценки оповещений электронной почты, которая проверяет сеть на наличие оповещений. Электронное уведомление отправляется в том случае, если возникает какое-либо оповещение, для которого настроено уведомление по электронной почте. Если оповещение по-прежнему активно в следующем цикле оценки, второе сообщение не отправляется, чтобы предотвратить переполнение почтового ящика. Однако при обнаружении нового оповещения в будущем цикле оценки оповещений отправляется электронное уведомление, включающее в себя как новое, так и предыдущее оповещение.  
  
###  <a name="alerts-that-result-in-email-notifications"></a><a name="BKMK_list"></a>Оповещения, которые приводят к появлению уведомлений по электронной почте  
 Следующие оповещения в средстве просмотра оповещений вызывают отправку электронного уведомления, если сервер настроен на отправку электронных уведомлений для оповещений:  
  
-   В архиве клиентского компьютера имеются ошибки.  
  
-   Сервер перезагружен.  
  
-   Не запущена одна или несколько служб.  
  
-   Не выполняется служба хранилища Windows Server.  
  
-   Период ознакомления закончен.  
  
-   Активировать сейчас.  
  
-   Завершается работа исходного сервера.  
  
-   Результаты проверки BPA содержат ошибки.  
  
-   Результаты проверки BPA содержат предупреждения.  
  
-   Недоступен сертификат, используемый для повсеместного доступа.  
  
-   Истек срок действия сертификата, используемого для повсеместного доступа.  
  
-   Маршрутизатор настроен неправильно.  
  
-   Веб-сервер настроен неправильно.  
  
-   Службы удаленных рабочих столов настроены неправильно.  
  
-   Брандмауэр настроен неправильно.  
  
-   Срок действия имени домена в Интернете истек.  
  
-   Не удается обновить имя домена в Интернете.  
  
-   Ошибка лицензирования: проверка доверия леса.  
  
-   Ошибка лицензирования: проверка контроллера домена.  
  
-   Ошибка лицензирования: проверка роли FSMO.  
  
-   Ошибка лицензирования: принудительное применение политик FSMO.  
  
-   Ошибка лицензирования: принудительное применение политик загрузки.  
  
-   Ошибка лицензирования: доменные службы Active Directory.  
  
-   Срок действия подписки на Office 365 истек.  
  
-   Не удалось пройти проверку подлинности в Office 365.  
  
-   Неверная политика паролей.  
  
-   Службе синхронизации паролей не удалось синхронизировать пароль пользователя с Office 365.  
  
-   Изменение пароля Windows.  
  
-   Пароль Office 365 не совпадает с паролем Windows.  
  
-   Не удается подключиться к серверу Exchange Server.  
  
-   На сервере Microsoft Exchange Server возникла проблема.  
  
-   Не подключен один или несколько жестких дисков системы архивации данных сервера.  
  
-   а архивном жестком диске не хватает свободного пространства для архива сервера.  
  
-   Архивация сервера завершилась неудачей, так как не удалось сделать моментальный снимок сервера.  
  
-   Запланированная архивация не была успешно завершена.  
  
-   Отсутствует одна или несколько предопределенных папок сервера.  
  
-   На одном или нескольких жестких дисках сервера недостаточно свободного пространства.  
  
-   Не работает модуль записи VSS для службы хранилища.  
  
-   Недостаточно пространства хранения на жестких дисках.  
  
-   Один или несколько дисков неисправны и отключены.  
  
###  <a name="configuring-smtp-on-your-server-to-send-alert-notifications-by-email-in-windows-server-essentials"></a><a name="BKMK_SMTP"></a>Настройка SMTP на сервере для отправки уведомлений об оповещениях по электронной почте в Windows Server Essentials  
 В этом разделе описывается настройка сервера на отправку электронных уведомлений об оповещениях.  
  
> [!NOTE]
>  Вы можете скачать надстройку отчета о работоспособности для Windows Server Essentials из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=266342).  
  
##### <a name="to-set-up-email-notification-for-alerts"></a>Настройка электронного уведомления для оповещений  
  
1.  Откройте **Средство просмотра оповещений** в области **Панель мониторинга**.  
  
2.  В окне **Средство просмотра оповещений** щелкните **Настроить уведомления по электронной почте для оповещений**.  
  
3.  В окне **Настройка электронных уведомлений для оповещений** щелкните **Включить**.  
  
4.  В окне **Параметры SMTP** выполните следующие действия:  
  
    1.  В поле **Адрес электронной почты отправителя** введите адрес электронной почты, с которого вы хотите отправлять электронные уведомления. Этот адрес электронной почты будет отображаться как адрес отправителя в уведомлении о предупреждении.  
  
    2.  В текстовом поле **Адрес электронной почты отправителя** области **Имя SMTP-сервера** введите имя SMTP-сервера, указанное в шаге 4а. (Несколько имен SMTP-сервера приведено в таблице 1.)  
  
    3.  Для параметра **Порт SMTP** введите номер порта, используемый SMTP-сервером для отправки и получения электронной почты. (Номера портов, используемые некоторыми SMTP-серверами, приведены в таблице 1.)  
  
    4.  Выберите **Для данного сервера требуется безопасное подключение (SSL)** , если SMTP-сервер использует протокол SSL (см. таблицу 1).  
  
    5.  Выберите **Для данного сервера требуется проверка подлинности** , если SMTP-сервер требует указания имени и пароля пользователя (см. таблицу 1). Если этот флажок установлен, введите имя пользователя и пароль для адреса электронной почты, введенного в поле **Адрес электронной почты отправителя** в шаге 4а, а затем нажмите кнопку **ОК**.  
  
    > [!NOTE]
    >  Сведения об имени, номере порта и использовании протокола SSL для SMTP-сервера можно получить у поставщика услуг Интернета.  
  
     **Таблица 1** Примеры имен, потребности в проверке подлинности и шифровании SSL, а также номеров портов для SMTP-сервера  
  
    |SMTP Server|Требуется SSL|Требуется проверка подлинности|Номер порта|Имя учетной записи и имя для входа|  
    |-----------------|------------------|-----------------------------|-----------------|------------------------------|  
    |smtp.gmail.com|Да|Да|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.live.com|Да|Да|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.comcast.net|Да|Нет|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.mail.yahoo.com|Нет|Да|25|Укажите только адрес электронной почты без доменного имени для имени пользователя.|  
  
5.  В поле **Настройка электронных уведомлений для оповещений** для параметра **Получатели электронной почты** введите адреса электронной почты лиц, которые должны получать уведомления об оповещениях по электронной почте. Обязательно отделяйте каждый адрес электронной почты точкой с запятой (;).  
  
6.  Чтобы проверить правильность настройки параметров SMTP-сервера для отправки электронных уведомления для оповещений, щелкните **Применить и отправить сообщение электронной почты**.  
  
    > [!NOTE]
    >  При нажатии кнопки **Применить и отправить по электронной почте**, как правило, вы получите тестовое уведомление по электронной почте, не содержащие оповещений о работоспособности. Однако если в процессе тестирования выявляется оповещение о работоспособности, для которого настроена отправка электронного уведомления, это оповещение включается в тестовое сообщение электронной почты.  
  
### <a name="configuring-smtp-on-your-server-to-send-health-reports-in-windows-server-essentials"></a>Настройка SMTP на сервере для отправки отчетов о работоспособности в Windows Server Essentials  
 В этом разделе описывается настройка параметров SMTP для сервера, чтобы вы могли получать отчеты о работоспособности по электронной почте.  
  
> [!NOTE]
>  По умолчанию надстройка отчетов о работоспособности интегрирована с Windows Server Essentials или Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience, а отчеты о работоспособности отображаются на вкладке **отчеты о работоспособности** **домашней** страницы панели мониторинга.  
  
##### <a name="to-set-up-email-notification-for-health-reports"></a>Настройка электронного уведомления для отчетов о работоспособности  
  
1.  В окне**Панель мониторинга** откройте вкладку **Отчеты**.  
  
2.  В области задач **Задачи отчетов о работоспособности** щелкните элемент **Настроить параметры отчета о работоспособности**.  
  
3.  В окне **Настроить параметры отчетов о работоспособности** откройте вкладку **Расписание и электронная почта**.  
  
4.  На вкладке **Расписание и электронная почта** в разделе **Электронная почта** выполните следующие действия:  
  
    1.  Щелкните **Включить** и введите адрес электронной почты, с которого вы хотите отправлять отчеты о работоспособности. Этот адрес электронной почты будет отображаться как адрес отправителя в отчетах о работоспособности, которые были отправлены по электронной почте.  
  
        1.  Для параметра **Имя SMTP-сервера** введите имя SMTP-сервера. (Несколько имен SMTP-сервера приведено в таблице 1.)  
  
        2.  Для параметра **Порт SMTP** введите номер порта, используемый SMTP-сервером для отправки и получения электронной почты. (Номера портов, используемые некоторыми SMTP-серверами, приведены в таблице 1.)  
  
        3.  Выберите **Для данного сервера требуется безопасное подключение (SSL)** , если SMTP-сервер использует протокол SSL (см. таблицу 1).  
  
        4.  Выберите **Для данного сервера требуется проверка подлинности** , если SMTP-сервер требует указания имени и пароля пользователя (см. таблицу 1). Если этот флажок установлен, введите имя пользователя и пароль для адреса электронной почты, введенного в поле **Адрес электронной почты отправителя** в шаге 4а, а затем нажмите кнопку **ОК**.  
  
            > [!NOTE]
            >  Сведения об имени, номере порта и использовании протокола SSL для SMTP-сервера можно получить у поставщика услуг Интернета.  
  
            > [!NOTE]
            >  Корпорация Майкрософт настоятельно рекомендует использовать SSL, поскольку отчет может содержать состояние сервера, которое может использоваться злоумышленниками для обнаружения уязвимостей (например, отсутствие обновления Windows). При включении SSL выполняется шифрование передаваемых данных и снижается риск раскрытия уязвимости сервера.  
  
5.  После включения электронной почты отображается ссылка **Изменение параметров SMTP**. Кроме того, в области **Задачи отчетов о работоспособности**. отображается новая задача **Отправить отчет о работоспособности по электронной почте**.  
  
     **Таблица 1** Примеры имен, потребности в проверке подлинности и шифровании SSL, а также номеров портов для SMTP-сервера  
  
    |SMTP Server|Требуется SSL|Требуется проверка подлинности|Номер порта|Имя учетной записи и имя для входа|  
    |-----------------|------------------|-----------------------------|-----------------|------------------------------|  
    |smtp.gmail.com|Да|Да|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.live.com|Да|Да|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.comcast.net|Да|Нет|587|Укажите полный адрес электронной почты с доменным именем и паролем для проверки подлинности.|  
    |smtp.mail.yahoo.com|Нет|Да|25|Укажите только адрес электронной почты без доменного имени для имени пользователя.|  
  
6.  В поле **Настроить параметры отчета о работоспособности** для параметра **Автоматически отправлять отчет о работоспособности следующим получателям электронной почты:** введите адреса электронной почты лиц, которые должны получать отчеты о работоспособности по электронной почте. Обязательно отделяйте каждый адрес электронной почты точкой с запятой (;).  
  
7.  Чтобы проверить правильность настройки параметров SMTP-сервера для отправки отчетов о работоспособности по электронной почте, выберите отчет на вкладке "Отчет о работоспособности" панели мониторинга и щелкните **Отправить отчет о работоспособности по электронной почте** на панели задач.  
  
##  <a name="potential-computer-alerts"></a><a name="BKMK_Potential"></a>Потенциальные оповещения компьютера  
 В этом разделе рассматриваются общие сведения об использовании оповещений, которые относятся к определенному компьютеру, подключенному к серверу, и отображаются в панели запуска компьютера.  
  
 В следующей таблице перечислены некоторые оповещения компьютера, которые могут возникать и отображаться в средстве просмотра оповещений, если они применимы к вашему компьютеру.  
  
|Заголовок оповещения|Влияние и разрешение оповещения|  
|-----------------|---------------------------------|  
|Текущее состояние брандмауэра сети снижает защиту данного компьютера.|Если Брандмауэр Windows отключен, возможен несанкционированный доступ к данному компьютеру.|  
|Защита от вирусов отключена, не установлена или не обновлена.|Данные на компьютере находятся под угрозой, если параметр безопасности **Защита от вирусов** выключен или не обновлен. [Для защиты компьютера](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Protect) следуйте приведенным указаниям.|  
|Защита от программ-шпионов и нежелательных программ отключена, не установлена или не обновлена.|Данные на компьютере находятся под угрозой, если параметр **Защита от программ-шпионов и нежелательных программ** выключен или не обновлен. [Для защиты компьютера](Manage-System-Health-in-Windows-Server-Essentials.md#BKMK_Protect) следуйте приведенным указаниям.|  
|Центр обновления Windows отключен.|Вы не сможете использовать преимущества новых и исправленных функциональных возможностей, если Центр обновления Windows отключен. Чтобы включить Центр обновления Windows, щелкните **Открыть Центр обновления Windows** в средстве просмотра оповещений.<br /><br /> Если задача **Открыть Центр обновления Windows** не отображается, вы не выполнили вход на компьютер, где возникло оповещение. Для запуска задачи из средства просмотра оповещений необходимо войти в систему компьютера, на котором было создано оповещение.|  
|Необходимо установить важные обновления.|Вы не сможете использовать преимущества новых и исправленных функциональных возможностей, если Центр обновления Windows отключен. Чтобы включить Центр обновления Windows, щелкните **Открыть Центр обновления Windows** в средстве просмотра оповещений.<br /><br /> Если задача **Открыть Центр обновления Windows** не отображается, вы не выполнили вход на компьютер, где возникло оповещение. Для запуска задачи из средства просмотра оповещений необходимо войти в систему компьютера, на котором было создано оповещение.|  
|Для применения обновлений необходимо перезагрузить компьютер.|Вы не сможете использовать преимущества новых и исправленных функциональных возможностей до применения обновлений. Сохраните все данные и перезагрузить компьютер, чтобы применить обновления.|  
|На жестких дисках недостаточно свободного места.|Без освобождения пространства сохранение дополнительных данных будет невозможно. Рассмотрите следующие варианты увеличения свободного пространства на компьютере:<br /><br /> — Добавьте новый жесткий диск.<br /><br /> — Запустите программу **очистки диска** , чтобы удалить старые и временные файлы.<br /><br /> — Перемещение файлов в общую папку на другом компьютере.<br /><br /> — Архивные файлы на съемных носителях, например компакт-диск, DVD-диск или внешний жесткий диск.|  
|Агент **Журнал файлов** на сервере не настроен правильно для запуска на данном компьютере.|Не удается создать архивы журнала файлов.|  
|Не запущена одна или несколько служб.||  
|Изменение пароля Windows.||  
|Пароль Microsoft Office 365 не совпадает с паролем Windows.||  
  
###  <a name="to-protect-your-computer"></a><a name="BKMK_Protect"></a>Защита компьютера  
  
1.  Откройте центр обеспечения безопасности.  
  
2.  Определите состояние защиты от вирусов.  
  
3.  В зависимости от состояния защиты выполните одну из следующих задач:  
  
    -   Если защита не включена, включите ее.  
  
    -   Если защита не обновлена, выполните процесс обновления сигнатур.  
  
    -   Если защита от вирусов не установлена, установите ее.  
  
## <a name="see-also"></a>См. также:  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
