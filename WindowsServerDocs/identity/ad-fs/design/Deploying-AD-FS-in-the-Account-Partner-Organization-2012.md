---
ms.assetid: 9aaca9c5-ce44-495c-aad6-61aede87a83f
title: Развертывание служб федерации Active Directory в партнерской организации по учетным записям
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 62d7549f124b96cd7addf7e54cc5d0c1d9897098
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408127"
---
# <a name="deploying-ad-fs-in-the-account-partner-organization"></a>Развертывание служб федерации Active Directory в партнерской организации по учетным записям

Партнер по учетным записям в службы федерации Active Directory (AD FS) \(AD FS\) представляет организацию в отношении доверия федерации, которая физически хранит учетные записи пользователей в поддерживаемом хранилище атрибутов. Дополнительные сведения о поддерживаемых хранилищах атрибутов см. в разделе [роль хранилищ атрибутов](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md).  
  
Сервер федерации в организации партнера по учетным записям выполняет проверку подлинности локальных пользователей и создает маркеры безопасности, используемые партнером по ресурсам для принятия решений об авторизации. Затем проверяющие стороны, такие как веб-сайты и веб-службы, могут легко зарегистрироваться на сервере федерации и использовать выданные маркеры для проверки подлинности и контроля доступа.  
  
В сценариях, в которых необходимо предоставить пользователям доступ к нескольким федеративным приложениям или службам. Если каждое приложение или служба размещается в другой организации, можно настроить сервер федерации партнера по учетным записям, чтобы можно было развернуть несколько проверяющих сторон.  
  
Дополнительные сведения о настройке и настройке организации партнера по учетным записям см. в разделе [Контрольный список: Настройка организации партнера по учетным](../../ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md)записям.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Сведения о роли сервера федерации в организации партнера по учетным записям](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md)  
  
-   [Сведения о роли прокси-сервера федерации в организации партнера по учетным записям](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md)  
  
-   [Подготовка клиентских компьютеров к работе с партнером по учетным записям](Prepare-Client-Computers-in-the-Account-Partner.md)  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
