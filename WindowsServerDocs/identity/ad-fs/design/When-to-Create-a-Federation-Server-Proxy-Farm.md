---
ms.assetid: ad0bf21d-2ace-4565-b1f5-ce57c8eb2689
title: Когда следует создавать ферму прокси-серверов федерации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 247daf1b9b49124188f6bb16bce7da381fe997ef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402425"
---
# <a name="when-to-create-a-federation-server-proxy-farm"></a>Когда следует создавать ферму прокси-серверов федерации

Рассмотрите возможность установки дополнительных прокси-серверов федерации при наличии большого службы федерации Active Directory (AD FS) \(AD FS\) развертывания и необходимости обеспечения отказоустойчивости, балансировки нагрузки\-и масштабируемости для развертывания прокси-сервера. Процесс создания двух или более прокси-серверов федерации в одной сети периметра и настройки каждого из них для защиты одного AD FS служба федерации создает ферму прокси сервера федерации.  
  
Вы можете создать ферму прокси-сервера федерации или установить дополнительные прокси-серверы федерации в существующую ферму с помощью мастера настройки прокси сервера AD FS Федерации. Дополнительные сведения см. в разделе [When to Create a Federation Server Proxy](When-to-Create-a-Federation-Server-Proxy.md).  
  
Прежде чем все прокси-серверы федерации смогут работать в качестве фермы, их необходимо сначала объединить с одним IP-адресом и одной системой доменных имен \(DNS\) полное доменное имя \(\)FQDN. Вы можете выполнить кластеризацию серверов, развернув балансировку сетевой нагрузки Майкрософт \(NLB\) в сети периметра. Для задач в следующей таблице требуется, чтобы NLB была настроена соответствующим образом для кластеризации прокси-серверов федерации в ферме.  
  
Дополнительные сведения о настройке полного доменного имени кластера с помощью технологии балансировки сетевой нагрузки Майкрософт см. [в разделе Указание параметров кластера](https://go.microsoft.com/fwlink/?linkid=74651).  
  
## <a name="configuring-federation-server-proxies-for-a-farm"></a>Настройка прокси-серверов федерации для фермы  
В следующей таблице описаны задачи, которые необходимо выполнить, чтобы каждый прокси-сервер федерации мог участвовать в ферме.  
  
|Задача|Описание|  
|--------|---------------|  
|Укажите для всех прокси-серверов в ферме одно и то же имя AD FS служба федерации|При создании прокси-серверов федерации необходимо ввести одно и то же имя служба федерации в мастере настройки прокси сервера AD FS Федерации для всех прокси сервера федерации, которые будут участвовать в ферме. Прокси-сервер федерации использует URL-адрес, который образует это имя узла DNS, чтобы определить, какой AD FS служба федерации экземпляр, к которому он обращается.<br /><br />Дополнительные сведения см. в разделе [Configure a Computer for the Federation Server Proxy Role](../../ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md).|  
|Получение и совместное использование сертификатов|Сертификат проверки подлинности сервера можно получить из общедоступного центра сертификации \(CA\)(например, VeriSign), а затем настроить сертификат таким образом, чтобы все прокси-серверы федерации могли использовать одну и ту же частную часть одного и того же сертификата на сайте по умолчанию для каждого прокси сервера федерации. Чтобы предоставить общий доступ к сертификату, необходимо установить тот же сертификат проверки подлинности сервера на веб-сайте по умолчанию для каждого прокси-сервера федерации. Дополнительные сведения см. в разделе [Импорт сертификата проверки подлинности сервера на веб-сайт по умолчанию](../../ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md).<br /><br />Дополнительные сведения см. в разделе [Certificate Requirements for Federation Server Proxies](Certificate-Requirements-for-Federation-Server-Proxies.md).|  
  
Дополнительные сведения о добавлении новых прокси-серверов федерации для создания фермы прокси сервера федерации см. в разделе [Контрольный список: Настройка прокси-сервера федерации](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md).  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
