---
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: Подготовка клиентских компьютеров для партнеров по учетным записям
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 5725f4a7761d08a25ee8c67c0568977e3646397e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407947"
---
# <a name="prepare-client-computers-in-the-account-partner"></a>Подготовка клиентских компьютеров для партнеров по учетным записям

Самый простой способ для администратора в организации партнера по учетным записям — подготовить клиентские компьютеры к службы федерации Active Directory (AD FS) \(AD FS\) Федеративные приложения — использовать групповая политика. Групповая политика обеспечивает удобный способ передачи конкретных сертификатов и параметров, необходимых для создания федерации на всех клиентских компьютерах, которые будут использоваться для доступа к федеративным приложениям.  
  
Чтобы клиентские компьютеры могли легко получать доступ к федеративным приложениям без запросов сертификатов или запросов, связанных с надежными сайтами, рекомендуется сначала подготовить каждый клиентский компьютер перед развертыванием AD FS в Организации. Рассмотрите возможность использования групповой политики для автоматической  
  
-   Настройте Internet Explorer на каждом клиентском компьютере, чтобы доверять серверу федерации учетной записи.  
  
    Дополнительные сведения см. в разделе [Configure Client Computers to Trust the Account Federation Server](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md).  
  
-   Установите соответствующий сервер федерации учетной записи, сервер федерации ресурсов и веб-сервер SSL \(SSL\) Certificates \(или аналогичные сертификаты, связанные с доверенными корневыми\) на каждом клиентском компьютере.  
  
    Дополнительные сведения см. в разделе [Распространение сертификатов на клиентские компьютеры с помощью групповая политика](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md).  
  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
