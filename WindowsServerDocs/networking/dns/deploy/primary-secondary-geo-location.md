---
title: Управление трафиком на основе географического расположения на основных и вспомогательных серверах с помощью политики DNS
description: Этот раздел является частью руководств по сценариям политики DNS для Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-dns
ms.topic: article
ms.assetid: a9ee7a56-f062-474f-a61c-9387ff260929
ms.author: lizross
author: eross-msft
ms.openlocfilehash: f9bc1a35016ca5946eddeada2088a83f1fa8ca05
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80317752"
---
# <a name="use-dns-policy-for-geo-location-based-traffic-management-with-primary-secondary-deployments"></a>Управление трафиком на основе географического расположения на основных и вспомогательных серверах с помощью политики DNS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела вы узнаете, как создать политику DNS для управления трафиком на основе географического расположения, если развертывание DNS включает как основной, так и дополнительный DNS-серверы.  

В предыдущем сценарии [используется политика DNS для управления трафиком на основе географического расположения с серверами-источниками](primary-geo-location.md). в этой статье приведены инструкции по настройке политики DNS для управления трафиком на основном сервере DNS на основе географического расположения. Однако в инфраструктуре Интернета DNS-серверы широко развертываются в модели «первичная-вторичная», где доступная для записи копия зоны хранится на выбранных и защищенных основных серверах, а доступные только для чтения копии зоны хранятся на нескольких серверах-получателях.   
  
Серверы-получатели используют протоколы зонных передач (AXFR) и добавочную зонную пересылку (IXFR) для запроса и получения обновлений зоны, содержащих новые изменения в зонах на основных DNS-серверах.   
  
> [!NOTE]
> Дополнительные сведения о параметре AXFR см. в запросе IETF (Internet Engineering Task Force) [для получения комментариев 5936](https://tools.ietf.org/rfc/rfc5936.txt). Дополнительные сведения о IXFR см. в статье запрос в IETF (Internet Engineering Task Force) [для получения комментариев 1995](https://tools.ietf.org/html/rfc1995).  
  
## <a name="primary-secondary-geo-location-based-traffic-management-example"></a>Пример управления трафиком на основе дополнительного географического расположения  
Ниже приведен пример использования политики DNS в развертывании по первичному вторичному приложению для обеспечения перенаправления трафика на основе физического расположения клиента, выполняющего запрос DNS.  
  
В этом примере используются две вымышленные компании — облачные службы Contoso, которые предоставляют решения для веб-приложений и размещения в домене. и службы Woodgrove Food, которые предоставляют услуги по доставке пищи в нескольких городах по всему миру и имеют веб-сайт с именем woodgrove.com.  
  
Чтобы клиенты woodgrove.com могли отвечать на запросы с веб-сайта, компания Woodgrove хочет, чтобы европейские клиенты направлялись в центр обработки данных США и американские клиенты, направляемые в центре обработки данных. Клиенты, расположенные в любом месте мира, могут направляться в любой из центров обработки данных.  
  
Облачные службы Contoso имеют два центра обработки данных: один в США и другой в Европе, на котором Contoso размещает портал заказов на продукты для woodgrove.com.  
  
Развертывание Contoso DNS включает два вторичных сервера: **SecondaryServer1**с IP-адресом 10.0.0.2; и **SecondaryServer2**с IP-адресом 10.0.0.3. Эти серверы-получатели функционируют в качестве серверов имен в двух разных регионах, где SecondaryServer1 находится в Европе и SecondaryServer2, расположенном в США.
  
В **сервер** (IP-адрес 10.0.0.1) доступна запись основной зоны с возможностью записи, где вносятся изменения в зоны. При обычной передаче зоны на серверы-получатели серверы-получатели всегда обновляются в соответствии с новыми изменениями зоны в сервер.
  
Этот сценарий показан на следующем рисунке.
  
![Пример управления трафиком на основе дополнительного географического расположения](../../media/Dns-Policy_PS1/dns_policy_primarysecondary1.jpg)  
   
## <a name="how-the-dns-primary-secondary-system-works"></a>Как работает основная система DNS

При развертывании управления трафиком на основе географического расположения в первичном и вторичном развертывании DNS важно понимать, как обычная передача данных из основной зоны происходит перед изучением передачи уровня области зоны. В следующих разделах приведены сведения о передаче данных на уровне зоны и зоны.  
  
- [Зонные передачи в первичном и вторичном развертывании DNS](#zone-transfers-in-a-dns-primary-secondary-deployment)  
- [Передача на уровне области зоны в первичном и вторичном развертывании DNS](#zone-scope-level-transfers-in-a-dns-primary-secondary-deployment)  
  
### <a name="zone-transfers-in-a-dns-primary-secondary-deployment"></a>Зонные передачи в первичном и вторичном развертывании DNS

Вы можете создать DNS-сервер с первичным и вторичным развертыванием и синхронизировать зоны, выполнив следующие действия.  
1. При установке DNS основная зона создается на основном DNS-сервере.  
2. На сервере-получателе создайте зоны и укажите основные серверы.   
3. На основных серверах можно добавить серверы-получатели в качестве доверенных вторичных серверов в основной зоне.   
4. Дополнительные зоны выполняют полный запрос на зонную пересылку (AXFR) и получают копию зоны.   
5. При необходимости основные серверы отправляют уведомления на серверы-получатели об обновлениях зоны.  
6. Вторичные серверы выполняют добавочный запрос на зонную пересылку (IXFR). По этой причине серверы-получатели по-прежнему синхронизируются с сервером-источником.   
  
### <a name="zone-scope-level-transfers-in-a-dns-primary-secondary-deployment"></a>Передача на уровне области зоны в первичном и вторичном развертывании DNS

Сценарий управления трафиком требует дополнительных действий по секционированию зон в разные области зоны. По этой причине дополнительные действия необходимы для перемещения данных в областях зоны на серверы-получатели, а также для перемещения политик и подсетей клиентов DNS на серверы-получатели.   
  
После настройки инфраструктуры DNS с основным и дополнительным серверами передача уровня зоны выполняется автоматически службой DNS с помощью следующих процессов.  
  
Чтобы обеспечить перемещение на уровне зоны, DNS-серверы используют механизмы расширений для DNS (EDNS0) OPT RR. Все запросы на зонные зоны (AXFR или IXFR) из зон с областями исходят из-за неявной записи ресурса EDNS0, для параметра ID которого по умолчанию задано значение "65433". Дополнительные сведения о ЕДНСО см. в запросе IETF [о комментариях 6891](https://tools.ietf.org/html/rfc6891).  
  
Значение RR OPT — это имя области зоны, для которой отправляется запрос. Когда основной DNS-сервер получает этот пакет от доверенного вторичного сервера, он интерпретирует запрос как поступающий для этой области зоны.   
  
Если на сервере-источнике есть область зоны, она реагирует на данные перемещения (КСФР) из этой области. Ответ содержит RR с тем же параметром с ИДЕНТИФИКАТОРом "65433" и значением, заданным для той же области зоны. Серверы-получатели получают этот ответ, извлекают сведения об области из ответа и обновляют эту конкретную область зоны.  
  
После выполнения этого процесса сервер-источник будет поддерживать список доверенных получателей, которые отправили такой запрос области зоны для уведомлений.   
  
Для дальнейшего обновления в области зоны на серверы-получатели отправляется уведомление IXFR с той же ЗАПИСЬю OPT. Область зоны, получающая это уведомление, делает запрос IXFR, содержащий эту запись ресурса OPT, и тот же процесс, описанный выше.  
  
## <a name="how-to-configure-dns-policy-for-primary-secondary-geo-location-based-traffic-management"></a>Настройка политики DNS для управления трафиком на основе географического расположения

Прежде чем начать, убедитесь, что выполнены все действия, описанные в разделе [Использование политики DNS для управления трафиком на основе географического расположения с первичными серверами](../../dns/deploy/Scenario--Use-DNS-Policy-for-Geo-Location-Based-Traffic-Management-with-Primary-Servers.md), а основной DNS-сервер настроен с зонами, областями зоны, подсетями клиента DNS и политикой DNS.  
  
> [!NOTE]
> В этом разделе приведены инструкции по копированию подсетей клиентов DNS, областей зоны и политик DNS с основных серверов DNS на серверы-получатели DNS для начальной настройки DNS и проверки. В будущем может потребоваться изменить параметры подсети клиента DNS, области зоны и политики на сервере-источнике. В этом случае можно создать скрипты автоматизации для синхронизации серверов-получателей с сервером-источником.  
  
Чтобы настроить политику DNS для ответов основной реплики на основе географического расположения, необходимо выполнить следующие действия.  
  
- [Создание дополнительных зон](#create-the-secondary-zones)  
- [Настройка параметров зонных передач в основной зоне](#configure-the-zone-transfer-settings-on-the-primary-zone)  
- [Копирование подсетей клиента DNS](#copy-the-dns-client-subnets)  
- [Создание областей зоны на сервере-получателе](#create-the-zone-scopes-on-the-secondary-server)  
- [Настройка политики DNS](#configure-dns-policy)  
  
В следующих разделах приведены подробные инструкции по настройке.  
  
> [!IMPORTANT]
> В следующих разделах приведены примеры команд Windows PowerShell, которые содержат примеры значений для многих параметров. Перед выполнением этих команд обязательно замените примеры значений в этих командах значениями, подходящими для вашего развертывания.  
> 
> Членство в **DnsAdmins**(или аналогичное) требуется для выполнения следующих процедур.  
  
### <a name="create-the-secondary-zones"></a>Создание дополнительных зон

Можно создать вторичную копию зоны, которую необходимо реплицировать в SecondaryServer1 и SecondaryServer2 (при условии, что командлеты выполняются удаленно из одного клиента управления).   
  
Например, можно создать вторичную копию www.woodgrove.com в SecondaryServer1 и SecondarySesrver2.  
  
Для создания дополнительных зон можно использовать следующие команды Windows PowerShell.  
  
    
    Add-DnsServerSecondaryZone -Name "woodgrove.com" -ZoneFile "woodgrove.com.dns" -MasterServers 10.0.0.1 -ComputerName SecondaryServer1  
      
    Add-DnsServerSecondaryZone -Name "woodgrove.com" -ZoneFile "woodgrove.com.dns" -MasterServers 10.0.0.1 -ComputerName SecondaryServer2  
      

Дополнительные сведения см. в разделе [Add-днссерверсекондаризоне](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserversecondaryzone?view=win10-ps).  
  
### <a name="configure-the-zone-transfer-settings-on-the-primary-zone"></a>Настройка параметров зонных передач в основной зоне

Необходимо настроить параметры основной зоны таким образом, чтобы:

1. Разрешены зонные передачи с сервера-источника на указанные серверы-получатели.  
2. Уведомления об обновлении зоны отправляются сервером-источником на серверы-получатели.  
  
Для настройки параметров зонных передач в основной зоне можно использовать следующие команды Windows PowerShell.
  
> [!NOTE]
> В следующем примере команда NOTIFY указывает, что сервер **-** источник будет отправлять уведомления об обновлениях в список выбора получателей.  
  
    
    Set-DnsServerPrimaryZone -Name "woodgrove.com" -Notify Notify -SecondaryServers "10.0.0.2,10.0.0.3" -SecureSecondaries TransferToSecureServers -ComputerName PrimaryServer  
     
  
Дополнительные сведения см. в разделе [Set-днссерверпримаризоне](https://docs.microsoft.com/powershell/module/dnsserver/set-dnsserverprimaryzone?view=win10-ps).  
  
  
### <a name="copy-the-dns-client-subnets"></a>Копирование подсетей клиента DNS

Необходимо скопировать подсети клиента DNS с основного сервера на серверы-получатели.
  
Для копирования подсетей на серверы-получатели можно использовать следующие команды Windows PowerShell.
  
    
    Get-DnsServerClientSubnet -ComputerName PrimaryServer | Add-DnsServerClientSubnet -ComputerName SecondaryServer1  
      
    Get-DnsServerClientSubnet -ComputerName PrimaryServer | Add-DnsServerClientSubnet -ComputerName SecondaryServer2  
      

Дополнительные сведения см. в разделе [Add-днссерверклиентсубнет](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverclientsubnet?view=win10-ps).  
  
### <a name="create-the-zone-scopes-on-the-secondary-server"></a>Создание областей зоны на сервере-получателе

Необходимо создать области зоны на серверах-получателях. В DNS области зоны также начинают запрашивать Ксфрс с сервера-источника. При любом изменении областей зоны на сервере-источнике уведомление, содержащее сведения об области зоны, отправляется на серверы-получатели. Затем серверы-получатели могут обновить свои области зоны с помощью добавочного изменения.  
  
Для создания областей зоны на серверах-получателях можно использовать следующие команды Windows PowerShell.  
  
    
    Get-DnsServerZoneScope -ZoneName "woodgrove.com" -ComputerName PrimaryServer|Add-DnsServerZoneScope -ZoneName "woodgrove.com" -ComputerName SecondaryServer1 -ErrorAction Ignore  
      
    Get-DnsServerZoneScope -ZoneName "woodgrove.com" -ComputerName PrimaryServer|Add-DnsServerZoneScope -ZoneName "woodgrove.com" -ComputerName SecondaryServer2 -ErrorAction Ignore  
  

> [!NOTE]
> В этих примерах команд параметр **-ErrorAction Ignore** включен, так как область зоны по умолчанию существует в каждой зоне. Область зоны по умолчанию не может быть создана или удалена. Конвейеризация приведет к попытке создать эту область, и она завершится ошибкой. Кроме того, можно создать области зон, не заданные по умолчанию, в двух дополнительных зонах.  
  
Дополнительные сведения см. в разделе [Add-днссерверзонескопе](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverzonescope?view=win10-ps).  
  
### <a name="configure-dns-policy"></a>Настройка политики DNS

После создания подсетей, разделов (областей зоны) и добавления записей необходимо создать политики, соединяющие подсети и секции, чтобы при получении запроса из источника в одной из подсетей клиента DNS возвращался ответ запроса. правильная область действия зоны. Для сопоставления области зоны по умолчанию не требуются никакие политики.  
  
Для создания политики DNS, связывающей подсети клиента DNS и области зоны, можно использовать следующие команды Windows PowerShell.   
    
    $policy = Get-DnsServerQueryResolutionPolicy -ZoneName "woodgrove.com" -ComputerName PrimaryServer  
      
    $policy | Add-DnsServerQueryResolutionPolicy -ZoneName "woodgrove.com" -ComputerName SecondaryServer1  
      
    $policy | Add-DnsServerQueryResolutionPolicy -ZoneName "woodgrove.com" -ComputerName SecondaryServer2  
      

Дополнительные сведения см. в разделе [Add-днссерверкуериресолутионполици](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps).  
  
Теперь вторичные DNS-серверы настраиваются с помощью необходимых политик DNS для перенаправления трафика на основе географического расположения.  
  
Когда DNS-сервер получает запросы на разрешение имен, DNS-сервер оценивает поля в DNS-запросе на соответствие настроенным политикам DNS. Если исходный IP-адрес в запросе разрешения имен соответствует любой из политик, область связанной зоны используется для ответа на запрос, а пользователь направляется к ресурсу, который является географически ближайшим к ним.   
  
Вы можете создавать тысячи политик DNS в соответствии с требованиями к управлению трафиком, а все новые политики применяются динамически, без перезапуска DNS-сервера во входящих запросах.
