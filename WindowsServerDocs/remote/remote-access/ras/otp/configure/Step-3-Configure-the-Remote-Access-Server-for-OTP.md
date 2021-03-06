---
title: Шаг 3. Настройка сервера удаленного доступа для OTP
description: Эта статья является частью руководств по развертыванию удаленного доступа с помощью проверки подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df1e87f2-6a0f-433b-8e42-816ae75395f9
ms.author: lizross
author: eross-msft
ms.openlocfilehash: d588d9b8675dad8bffc9e020032bc66bebf503b0
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80313670"
---
# <a name="step-3-configure-the-remote-access-server-for-otp"></a>Шаг 3. Настройка сервера удаленного доступа для OTP

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

После настройки RADIUS-сервера с маркерами распространения программного обеспечения открыты порты связи, был создан общий секрет, учетные записи пользователей, соответствующие Active Directory, были созданы на сервере RADIUS, а сервер удаленного доступа — настроена как агент проверки подлинности RADIUS, сервер удаленного доступа должен быть настроен для поддержки OTP.  
  
|Задача|Описание|  
|----|--------|  
|[3,1 исключение пользователей из проверки подлинности OTP (необязательно)](#BKMK_Exempt)|Если конкретные пользователи будут исключены из DirectAccess с проверкой подлинности OTP, выполните эти подготовительные действия.|  
|[3,2. Настройка сервера удаленного доступа на поддержку OTP](#BKMK_Config)|На сервере удаленного доступа обновите конфигурацию удаленного доступа для поддержки двухфакторной проверки подлинности OTP.|  
|[3,3. смарт-карты для дополнительной авторизации](#BKMK_Smartcard)|Дополнительные сведения об использовании смарт-карт.|  
  
> [!NOTE]  
> В этом разделе приведены примеры командлетов Windows PowerShell, которые могут быть использованы для автоматизации некоторых описанных процедур. Дополнительные сведения см. в разделе [Командлеты](https://go.microsoft.com/fwlink/p/?linkid=230693).  
  
## <a name="31-exempt-users-from-otp-authentication-optional"></a><a name="BKMK_Exempt"></a>3,1 исключение пользователей из проверки подлинности OTP (необязательно)  
Если конкретные пользователи должны быть исключены из проверки подлинности OTP, необходимо выполнить эти действия до настройки удаленного доступа.  
  
> [!NOTE]  
> При настройке группы исключения OTP необходимо дождаться завершения репликации между доменами.  
  
#### <a name="create-user-exemption-security-group"></a>Создать группу безопасности для исключения пользователя  
  
1.  Создайте группу безопасности в Active Directory для исключения OTP.  
  
2.  Добавьте всех пользователей, которые будут исключены из проверки подлинности OTP, в группу безопасности.  
  
    > [!NOTE]  
    > Не забудьте включить в группу безопасности исключения OTP только учетные записи пользователей, а не учетные записи компьютеров.  
  
## <a name="32-configure-the-remote-access-server-to-support-otp"></a><a name="BKMK_Config"></a>3,2. Настройка сервера удаленного доступа на поддержку OTP  
Чтобы настроить удаленный доступ для использования двухфакторной проверки подлинности и OTP с сервером RADIUS и развертыванием сертификата из предыдущих разделов, выполните следующие действия.  
  
#### <a name="configure-remote-access-for-otp"></a>Настройка удаленного доступа для OTP  
  
1.  Откройте **Управление удаленным доступом** и щелкните **Конфигурация**.  
  
2.  В окне **Настройка DirectAccess** в разделе **Шаг 2 — сервер удаленного доступа**нажмите кнопку **изменить**.  
  
3.  Нажмите кнопку **Далее** три раза, в разделе **Проверка подлинности** выберите обе **проверки ПОдлинности** и **Используйте OTP**и убедитесь, что установлен флажок **использовать сертификаты компьютеров** .  
  
    > [!NOTE]  
    > После включения OTP на сервере удаленного доступа, если вы отключаете OTP путем отмены выбора **использования OTP**, расширения ISAPI и CGI будут удалены на сервере.  
  
4.  Если требуется поддержка Windows 7, установите флажок **разрешить клиентским компьютерам Windows 7 подключаться с помощью DirectAccess** . Примечание. как обсуждалось в разделе Planning, для поддержки DirectAccess с OTP на клиентах Windows 7 должен быть установлен DCA 2,0.  
  
5.  Нажмите кнопку **Далее**.  
  
6.  В разделе **RADIUS-сервер OTP** дважды щелкните поле пустое **имя сервера** .  
  
7.  В диалоговом окне **Добавление сервера RADIUS** введите имя сервера RADIUS в поле **имя сервера** . Нажмите кнопку **изменить** рядом с полем **общий секрет** и введите тот же пароль, который использовался при настройке сервера RADIUS в полях **новый секрет** и **Подтверждение нового** секрета. Дважды нажмите кнопку **ОК** и нажмите кнопку **Далее**.  
  
    > [!NOTE]  
    > Если сервер RADIUS находится в домене, отличном от сервера удаленного доступа, в поле **имя сервера** должно быть указано полное доменное имя сервера RADIUS.  
  
8.  В разделе **серверы ЦС OTP** выберите серверы ЦС, которые будут использоваться для регистрации сертификатов проверки подлинности клиента OTP, и нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  
  
9. В разделе **шаблоны сертификатов OTP** нажмите кнопку **Обзор** , чтобы выбрать шаблон сертификата, используемый для регистрации сертификатов, выданных для проверки подлинности OTP.  
  
    > [!NOTE]  
    > Шаблон сертификата для сертификатов OTP, выданных корпоративным ЦС, должен быть настроен без параметра "не включать сведения об отзыве в выданные сертификаты". Если этот параметр выбран во время создания шаблона сертификата, клиентские компьютеры OTP не смогут правильно войти в систему.  
  
    Нажмите кнопку **Обзор** , чтобы выбрать шаблон сертификата, который используется для регистрации сертификата, используемого сервером удаленного доступа, для подписания запросов на регистрацию сертификатов OTP. Нажмите кнопку **ОК**. Нажмите кнопку **Далее**.  
  
10. Если требуется исключить определенных пользователей из DirectAccess с OTP, в разделе **исключения OTP** выберите не **требовать проверку подлинности пользователей в указанной группе безопасности с помощью двухфакторной проверки подлинности**. Щелкните **Группа безопасности** и выберите группу безопасности, созданную для исключений OTP.  
  
11. На странице **Настройка сервера удаленного доступа** нажмите кнопку **Готово**.  
  
12. В окне **настройки DirectAccess** в разделе **Шаг 3 — серверы инфраструктуры**нажмите кнопку **изменить**.  
  
13. Нажмите кнопку **Далее** два раза, а затем в разделе **Управление** дважды щелкните поле **серверы управления** .  
  
14. Введите **имя компьютера** или **адрес** сервера ЦС, настроенного на выдачу сертификатов OTP, и нажмите кнопку **ОК**.  
  
15. В окне **настройки удаленного доступа** нажмите кнопку **Готово**.  
  
16. В **мастере Expert DirectAccess**нажмите кнопку **Готово** .  
  
17. В диалоговом окне **Проверка удаленного доступа** нажмите кнопку **Применить**, дождитесь обновления политики DirectAccess и нажмите кнопку **Закрыть**.  
  
18. На **начальном** экране введите**PowerShell. exe**, щелкните правой кнопкой мыши **PowerShell**, выберите пункт **Дополнительно**и щелкните **Запуск от имени администратора**. Если появится диалог **Контроль учетных записей**, подтвердите, что действие, которое оно отображает то, что нужно, затем щелкните **Да**.  
  
19. В окне Windows PowerShell введите **gpupdate/Force** и нажмите клавишу ВВОД.  
  
Чтобы настроить удаленный доступ для OTP с помощью команд PowerShell, выполните следующие действия.  
  
![](../../../../media/Step-3-Configure-the-Remote-Access-Server-for-OTP/PowerShellLogoSmall.gif)**эквивалентных команд Windows PowerShell Windows PowerShell**  
  
Следующие командлеты Windows PowerShell выполняют ту же функцию, что и предыдущая процедура. Введите каждый командлет на отдельной строке. Они могут отображаться с переносом на несколько строк из-за ограничений форматирования.  
  
Чтобы настроить удаленный доступ для использования двухфакторной проверки подлинности в развертывании, которое в настоящее время использует сертификат компьютера, выполните следующие действия.  
  
```  
Set-DAServer -UserAuthentication TwoFactor  
```  
  
Чтобы настроить удаленный доступ для использования проверки подлинности методом OTP, используйте следующие параметры:  
  
-   Сервер OTP с именем OTP.corp.contoso.com.  
  
-   Сервер CA с именем APP1. Corp. contoso. com\corp-APP1-CA1.  
  
-   Шаблон сертификата с именем Даотплогон используется для регистрации сертификатов, выданных для проверки подлинности методом OTP.  
  
-   Шаблон сертификата с именем ДАОТПРА, используемый для регистрации сертификата центра регистрации, используемого сервером удаленного доступа для подписания запросов на регистрацию сертификатов OTP.  
  
```  
Enable-DAOtpAuthentication -CertificateTemplateName 'DAOTPLogon' -SigningCertificateTemplateName 'DAOTPRA' -CAServer @('APP1.corp.contoso.com\corp-APP1-CA1') -RadiusServer OTP.corp.contoso.com -SharedSecret Abcd123$  
```  
  
После выполнения команд PowerShell выполните шаги 12-19 из предыдущей процедуры, чтобы настроить сервер удаленного доступа для поддержки OTP.  
  
> [!NOTE]  
> Прежде чем добавлять точку входа, убедитесь, что были применены параметры OTP на сервере удаленного доступа.  
  
## <a name="33-smart-cards-for-additional-authorization"></a><a name="BKMK_Smartcard"></a>3,3. смарт-карты для дополнительной авторизации  
На странице Проверка подлинности на шаге 2 в мастере настройки удаленного доступа можно потребовать использования смарт-карт для доступа к внутренней сети. Если выбран этот параметр, мастер настройки удаленного доступа настраивает правило безопасности подключения IPsec для туннеля интрасети на сервере DirectAccess, чтобы требовать разрешения туннельного режима с помощью смарт-карт. Авторизация в режиме туннелирования позволяет указать, что только авторизованные компьютеры или пользователи могут устанавливать входящий туннель.  
  
Чтобы использовать смарт-карты с авторизацией туннельного режима IPsec для туннеля интрасети, необходимо развернуть инфраструктуру открытых ключей (PKI) с инфраструктурой смарт-карт.  
  
Так как клиенты DirectAccess используют смарт-карты для доступа к интрасети, для управления доступом к ресурсам, таким как файлы, папки и принтеры, можно также использовать механизм проверки подлинности, компонент Windows Server 2008 R2. в зависимости от того, пользователь вошел в систему с сертификатом, основанным на смарт-карте. Для обеспечения надежности механизма проверки подлинности необходим функциональный уровень домена Windows Server 2008 R2.  
  
### <a name="allowing-access-for-users-with-unusable-smart-cards"></a>Разрешение доступа для пользователей с непригодными для использования смарт-картами  
Чтобы разрешить временный доступ для пользователей с непригодными для использования смарт-картами, выполните следующие действия.  
  
1.  Создайте Active Directory группу безопасности, которая будет содержать учетные записи пользователей, которые временно не могут использовать свои смарт-карты.  
  
2.  Для объекта групповая политика сервера DirectAccess Настройте глобальные параметры IPsec для авторизации туннеля IPsec и добавьте группу безопасности Active Directory в список авторизованных пользователей.  
  
Чтобы предоставить пользователю доступ, который не может использовать смарт-карту, временно добавьте свою учетную запись пользователя в группу безопасности Active Directory. Удалите учетную запись пользователя из группы, когда смарт-карта будет использоваться.  
  
### <a name="under-the-covers-smart-card-authorization"></a>На самом деле: авторизация смарт-карты  
Авторизация смарт-карт работает путем включения авторизации режима туннелирования в правиле безопасности подключения туннеля интрасети сервера DirectAccess для определенного идентификатора безопасности (SID) на основе Kerberos. Для авторизации смарт-карты это известный идентификатор безопасности (S-1-5-65-1), который сопоставляется с смарт-картами при входе в систему. Этот идентификатор безопасности имеется в токене Kerberos клиента DirectAccess и называется "Этот сертификат организации", если он настроен в параметрах авторизации в режиме глобального туннелирования IPsec.  
  
При включении авторизации смарт-карты на шаге 2 мастера установки DirectAccess мастер установки DirectAccess настраивает параметр авторизации глобального режима туннелирования IPsec на этот идентификатор безопасности для объекта сервера DirectAccess групповая политика. Чтобы просмотреть эту конфигурацию в оснастке "Брандмауэр Windows в режиме повышенной безопасности" для объекта групповая политика сервера DirectAccess, выполните следующие действия.  
  
1.  Щелкните правой кнопкой мыши Брандмауэр Windows в расширенной безопасности и выберите пункт Свойства.  
  
2.  На вкладке Параметры IPsec в окне Авторизация туннеля IPsec нажмите кнопку Настроить.  
  
3.  Перейдите на вкладку Пользователи. Вы должны увидеть сертификат "NT Аусорити\сис организации" в качестве полномочного пользователя.  
  


