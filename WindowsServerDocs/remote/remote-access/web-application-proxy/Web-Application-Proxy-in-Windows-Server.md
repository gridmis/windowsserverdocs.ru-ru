---
ms.assetid: 0b3587b2-219f-43d8-88b4-1254eaa8b910
title: Прокси-служба веб-приложения в Windows Server
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.service: ''
ms.suite: na
ms.technology: web-app-proxy
ms.tgt_pltfrm: na
ms.topic: article
author: kgremban
ms.openlocfilehash: bfa57a18ee74e1e54f6e7c1ed85d4bfbccb8937b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404249"
---
# <a name="web-application-proxy-in-windows-server"></a>Прокси-служба веб-приложения в Windows Server

>Область применения: Windows Server&reg; 2016

**Это содержимое относится к локальной версии прокси веб-приложения. Чтобы обеспечить безопасный доступ к локальным приложениям в облаке, ознакомьтесь с [содержимым AD application proxy Azure](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-get-started/).**  
  
В этом разделе описано, что нового и изменено в прокси веб-приложения для Windows Server 2016. Новые функции и изменения, перечисленные здесь, скорее всего, оказывают наибольшее влияние на работу с предварительной версией.  
  
## <a name="web-application-proxy-new-features"></a>Новые возможности прокси веб-приложения  
  
- Предварительная проверка подлинности при публикации приложений HTTP Basic  
  
  HTTP Basic — это протокол авторизации, используемый многими протоколами, включая ActiveSync, для подключения полнофункциональных клиентов, включая смартфоны, с почтовым ящиком Exchange. Прокси веб-приложения обычно взаимодействует с AD FS с использованием перенаправлений, которые не поддерживаются клиентами ActiveSync. Эта новая версия прокси веб-приложения обеспечивает поддержку публикации приложения с помощью HTTP Basic, позволяя приложению HTTP получить отношение доверия с проверяющей стороной, не относящейся к утверждениям, для приложения с служба федерации.  
  
  Дополнительные сведения о публикации HTTP Basic см. в статье [Публикация приложений с помощью AD FS Предварительная проверка подлинности](../web-application-proxy/../web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication.md) .  
  
- Доменная публикация приложений с подстановочными знаками  
  
  Для поддержки таких сценариев, как SharePoint 2013, внешний URL-адрес приложения теперь может содержать подстановочный знак, позволяющий публиковать несколько приложений в определенном домене, например https://*. SP-Apps. contoso. com. Это упростит публикацию приложений SharePoint.  
  
- Перенаправление HTTP в HTTPS  
  
  Чтобы пользователи могли получить доступ к приложению, даже если в URL-адресе не введено значение HTTPS, прокси веб-приложения теперь поддерживает перенаправление HTTP в HTTPS.  
  
- Публикация HTTP  
  
  Теперь можно опубликовать приложения HTTP, используя сквозную предварительную проверку подлинности.  
  
- Публикация приложений шлюза удаленный рабочий стол  
  
  Дополнительные сведения о RDG в прокси веб-приложения см. в статье [Публикация приложений с помощью SharePoint, Exchange и RDG](../web-application-proxy/Publishing-Applications-with-SharePoint,-Exchange-and-RDG.md) .  
  
- Новый журнал отладки для улучшения устранения неполадок и Улучшенный журнал службы для полного аудита и улучшенной обработки ошибок  
  
  Дополнительные сведения об устранении неполадок см. в разделе [Устранение неполадок прокси веб-приложения](https://technet.microsoft.com/library/dn770156.aspx) .  
  
- Улучшения пользовательского интерфейса консоль администратора  
  
- Распространение IP-адреса клиента в серверные приложения  
  
## <a name="see-also"></a>См. также  
  
-   [Что нового в Windows Server 2016?](https://technet.microsoft.com/library/dn765472.aspx)  
  
-   [Публикация приложений с использованием предварительной проверки подлинности AD FS](../web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication.md)  
  
-   [Диагностика прокси-службы веб-приложения](https://technet.microsoft.com/library/dn770156.aspx)  
  


