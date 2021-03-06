---
title: Настройка географической избыточности с помощью Репликация SQL Server
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: active-directory-federation-services
ms.author: billmath
ms.assetId: 7b9f9a4f-888c-4358-bacd-3237661b1935
ms.openlocfilehash: 16cf1a237043aa546d4fc24164045aa9f9a1e6ac
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359818"
---
# <a name="setup-geographic-redundancy-with-sql-server-replication"></a>Настройка географической избыточности с помощью Репликация SQL Server


> [!IMPORTANT]  
> Если вы хотите создать ферму AD FS и использовать SQL Server для хранения данных конфигурации, можно использовать SQL Server 2008 или более поздней версии.
  
При использовании SQL Server в качестве базы данных конфигурации AD FS можно настроить\-избыточность для фермы AD FS с помощью SQL Server репликации. Географическая\-ная избыточность реплицирует данные между двумя географически отдаленными сайтами, чтобы приложения могли переключаться с одного сайта на другой. Таким образом, в случае сбоя одного сайта все данные конфигурации можно будет получить на втором сайте. Дополнительные сведения см. в разделе "SQL Server географическая избыточность" в [ферме серверов федерации с помощью SQL Server](../design/Federation-Server-Farm-Using-SQL-Server.md).  
  
## <a name="prerequisites"></a>Предварительные условия  
Установите и настройте ферму SQL Server. Дополнительные сведения см. в разделе [https://technet.microsoft.com/evalcenter/hh225126.aspx](https://technet.microsoft.com/evalcenter/hh225126.aspx). На начальном SQL Server убедитесь, что служба агент SQL Server запущена и настроена на автоматический запуск.  
  
## <a name="create-the-second-replica-sql-server-for-geo-redundancy"></a>Создание второй реплики \(\) SQL Server для обеспечения избыточности гео\-  
  
1. Установка SQL Server \(дополнительные сведения см. в разделе [https://technet.microsoft.com/evalcenter/hh225126.aspx](https://technet.microsoft.com/evalcenter/hh225126.aspx). Скопируйте полученные файлы скриптов CreateDB. SQL и SetPermissions. SQL на реплику SQL Server.  
  
2. Убедитесь, что служба агент SQL Server запущена и настроена на автоматический запуск.  
  
3. Выполните **Export\-адфсдеплойментсклскрипт** на основном узле AD FS, чтобы создать файлы CreateDB. SQL и SetPermissions. SQL.  Например:`PS:\>Export-AdfsDeploymentSQLScript -DestinationFolder . –ServiceAccountName CONTOSO\gmsa1$`.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql2.png)
  
4. Скопируйте сценарии на сервер-получатель.  Откройте скрипт CreateDB. SQL в **Management Studio SQL** и нажмите кнопку **выполнить**.
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql4.png)

5. Откройте скрипт SetPermissions. SQL в **Management Studio SQL** и нажмите кнопку **выполнить**.
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql6.png) 

   

> [!NOTE]
> Кроме того, можно использовать следующую команду из командной строки. 
> 
>    `c:\>sqlcmd –i CreateDB.sql`  
> 
>    `c:\>sqlcmd –i SetPermissions.sql` 
> 
> ## <a name="create-publisher-settings-on-the-initial-sql-server"></a>Создание параметров издателя на начальном SQL Server  
  
1. В SQL Server Management Studio в разделе **репликация**щелкните правой кнопкой мыши пункт **Локальные публикации** и выберите команду **создать публикацию...** 
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql7.png) </br>  

2. На экране мастера создания публикаций нажмите кнопку **Далее**.</br>
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql8.png) </br> 
  
3. На странице **распространителя** выберите локальный сервер в качестве распространителя и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql9.png) </br>   

4. На странице Папка **моментальных снимков** введите \\\SQL1\repldata вместо папки по умолчанию. \(Примечание. возможно, вам потребуется создать эту общую папку самостоятельно\).  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql10.png) </br>   
  
5. Выберите **AdfsConfigurationV3** в качестве базы данных публикации и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql11.png) </br>
  
6. В меню **Тип публикации**выберите пункт **Публикация слиянием** и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql12.png) </br>
  
7. На **типах подписчиков**выберите **SQL Server 2008 или более поздней версии** и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql13.png) </br> 

8. На странице **статьи** выберите узел **таблицы** , чтобы выбрать все таблицы, а затем **\-проверить таблицу синкпропертиес** , \(эту реплику не следует реплицировать\)</br>
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql14.png) </br>    
  
9. На странице **статьи** выберите элемент **определяемые пользователем функции** узел, чтобы выбрать все определяемые пользователем функции, и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql15.png) </br>    

10. На странице **проблемы с статьей** нажмите кнопку **Далее**.  
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql16.png) </br>   

11. На странице **Фильтрация строк таблицы** нажмите кнопку **Далее**.  
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql17.png) </br>   
12. На странице **Агент моментальных снимков** выберите значения по умолчанию немедленно и 14 дней, нажмите кнопку **Далее**.  
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql18.png) </br>   
    Возможно, потребуется создать учетную запись домена для агента SQL Server. Выполните действия, описанные в разделе [Настройка имени входа SQL для учетной записи домена CONTOSO\\](Set-up-Geographic-Redundancy-with-SQL-Server-Replication.md#sqlagent) , чтобы создать имя входа SQL для этого нового пользователя AD и назначить определенные разрешения.  
  
13. На странице **Безопасность агента** щелкните **настройки безопасности** и введите имя пользователя\/пароль учетной записи домена, \(не GMSA\), СОЗДАННОГО для агента SQL Server, и нажмите кнопку **ОК**.  Нажмите кнопку **Далее**.  
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql19.png) </br>  

14. На странице **действия мастера** нажмите кнопку **Далее**.   
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql20.png) </br>

15. На странице **Завершение работы мастера** введите имя публикации и нажмите кнопку **Готово**. 
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql21.png) </br>  

16. После создания публикации вы увидите состояние Success (успешно).  Нажмите кнопку **Закрыть**.
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql22.png) </br>  

17. Вернитесь в SQL Server Management Studio, щелкните новую публикацию правой кнопкой мыши и выберите пункт **запустить монитор репликации**.  
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql23.png) </br> 
  
## <a name="create-subscription-settings-on-the-replica-sql-server"></a>Создание параметров подписки на реплике SQL Server  
Убедитесь, что параметры издателя созданы на начальном SQL Server, как описано выше, а затем выполните следующую процедуру.  
  
1. В SQL Server реплики в SQL Server Management Studio в разделе **репликация**щелкните правой кнопкой мыши элемент **Локальные подписки** и выберите **создать подписку...** . ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql24.png) </br>  

2. На странице **Мастер создания подписки** нажмите кнопку **Далее**.
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql25.png) </br>   
  
3. На странице **Публикация** выберите издателя из раскрывающегося списка.  Разверните узел **AdfsConfigurationV3** и выберите имя созданной ранее публикации и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql26.png) </br> 
  
4. На странице **расположение агент слияния** выберите **выполнять каждый агент на своем подписчике \(подписки по запросу\)** \(\) по умолчанию и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql27.png) </br> Это, наряду с типом подписки ниже, определяет логику разрешения конфликтов. \(дополнительные сведения см. в разделе [Обнаружение и разрешение конфликтов репликации слиянием](https://technet.microsoft.com/library/ms151191.aspx). </br>
 
5. На странице **Подписчики** выберите **AdfsConfigurationV3** в качестве базы данных подписчика и нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql28.png) </br> 
  
6. На странице **безопасность агент слияния** щелкните.. **.** и введите имя пользователя и пароль учетной записи домена, \(не GMSA\), СОЗДАННОГО для агента SQL Server, с помощью поля с многоточием и нажмите кнопку **Далее**.
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql30.png) </br> 
  
7. В **расписанию синхронизации**выберите **выполнять непрерывно** и нажмите кнопку **Далее**. 
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql31.png) </br> 
 
8. В меню **инициализация подписок**нажмите кнопку **Далее**.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql32.png) </br> 
  
9. В качестве **типа подписки**выберите **клиент** и нажмите кнопку **Далее**.  
  
   Последствия этого описаны [здесь](https://technet.microsoft.com/library/ms151191.aspx) и [здесь](https://technet.microsoft.com/library/ms151170.aspx).  По сути, мы принимаем простое разрешение конфликтов "первым и издателем", и нам не нужно повторно публиковать его на других подписчиках.  
   ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql33.png) </br>
   
10. На странице **действия мастера** убедитесь, что установлен флажок **создать подписку** , и нажмите кнопку **Далее**. 
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql34.png) </br>

11. На странице **Завершение работы мастера** нажмите кнопку **Готово**. 
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql35.png) </br>

12. После завершения процесса создания подписки вы увидите сообщение success (успешно). Нажмите кнопку **Закрыть**. 
    ![настроить географическую избыточность](media/Set-up-Geographic-Redundancy-with-SQL-Server-Replication/sql36.png) </br>
  
## <a name="verify-the-process-of-initialization-and-replication"></a>Проверка процесса инициализации и репликации  
  
1.  На основном сервере SQL Server щелкните правой кнопкой мыши\-узел **репликация** и выберите пункт **запустить монитор репликации**.  
  
2.  В **мониторе репликации**щелкните публикацию.  
  
3.  На вкладке **все подписки** щелкните правой кнопкой мыши и **Просмотрите сведения**.  
  
    Вы увидите множество записей в разделе **действия** для начальной репликации.  
  
4.  Кроме того, можно просмотреть узел **задания агент SQL Server\\** , чтобы просмотреть задания\(s\) запланированные для выполнения операций\/подписки на публикацию.  Отображаются только локальные задания, поэтому не забудьте проверить издателя и подписчика на устранение неполадок.  \-щелкните задание правой кнопкой мыши и выберите **Просмотреть журнал** , чтобы просмотреть журнал выполнения и результаты.  
  
## <a name="sqlagent"></a>Настройка имени входа SQL для учетной записи домена CONTOSO\\  
  
1.  Создайте новое имя входа на первичной и репликовой SQL Server с именем CONTOSO\\, \(имя нового пользователя домена, созданного и настроенного на странице **Безопасность агента** в процедурах, описанных выше.\)  
  
2.  В SQL Server\-щелкните правой кнопкой мыши созданное имя входа и выберите пункт Свойства, а затем на вкладке **Сопоставление пользователей** сопоставьте это имя входа с базами данных **адфсконфигуратион** и **адфсартифакт** с помощью общедоступных ролей и\_роли в базе данных женевасервице. Также сопоставьте это имя входа с базой данных распространителя и добавьте роль владельца\_DB для таблиц распределения и адфсконфигуратион.  Это необходимо сделать как для основного, так и для реплики SQL Server. Дополнительные сведения см. в разделе [модель безопасности агента репликации](https://technet.microsoft.com/library/ms151868.aspx).  
  
3.  Предоставьте соответствующей учетной записи домена разрешения на чтение и запись для общей папки, настроенной как распространитель.  Убедитесь, что разрешения на чтение и запись заданы как для разрешений общего ресурса, так и для разрешений локального файла.  
  
## <a name="configure-ad-fs-nodes-to-point-to-the-sql-server-replica-farm"></a>Настройка AD FS узла\(s\) для указания на ферму SQL Server реплики  
Теперь, когда геоизбыточность настроена, узлы AD FS фермы можно настроить так, чтобы они указывали на реплику SQL Server фермы с помощью стандартных возможностей фермы AD FS "присоединения" в пользовательском интерфейсе мастера настройки AD FS или с помощью Windows PowerShell.  
  
При использовании пользовательского интерфейса мастера настройки AD FS выберите **Добавить сервер федерации в ферму серверов федерации**. **Не** выбирайте параметр **создать первый сервер федерации в ферме серверов федерации**.  
  
При использовании Windows PowerShell выполните команду **Add\-адфсфармноде**. **Не** выполняйте команду **Install\-адфсфарм**.  
  
При появлении запроса укажите узел и имя экземпляра SQL Server реплики, а **не** исходного SQL Server.  
