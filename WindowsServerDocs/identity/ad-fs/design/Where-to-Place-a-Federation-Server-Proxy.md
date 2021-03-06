---
ms.assetid: ec26705c-4446-4226-b9b4-b775b642f0f4
title: Размещение прокси-сервера федерации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 73e68d03e4f2f76dbaf4a497da551640476d0438
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407822"
---
# <a name="where-to-place-a-federation-server-proxy"></a>Размещение прокси-сервера федерации

Вы можете поместить службы федерации Active Directory (AD FS) \(AD FS\)прокси-серверы федерации в сети периметра, чтобы обеспечить уровень защиты от злонамеренных пользователей, которые могут поступают из Интернета. Прокси-серверы федерации идеально подходят для среды сети периметра, так как они не имеют доступа к закрытым ключам, которые используются для создания токенов. Однако прокси-серверы федерации могут эффективно маршрутизировать входящие запросы к серверам федерации, которым разрешено создавать эти токены.  
  
Нет необходимости размещать прокси-сервер федерации в корпоративной сети для партнера по учетным записям или партнера по ресурсам, так как клиентские компьютеры, подключенные к корпоративной сети, могут напрямую взаимодействовать с сервером федерации. В этом сценарии сервер федерации также предоставляет функциональные возможности прокси-сервера федерации для клиентских компьютеров, поступающих из корпоративной сети.  
  
Как и в случае с демилитаризованными сетями, для сети периметра и корпоративной сети устанавливается брандмауэр\-с подключением к интрасети, а брандмауэр\-через Интернет часто устанавливается между сетью периметра и Интернетом. В этом сценарии прокси-сервер федерации располагается между обоими брандмауэрами в сети периметра.  
  
## <a name="configuring-your-firewall-servers-for-a-federation-server-proxy"></a>Настройка серверов брандмауэра для прокси-сервера федерации  
Чтобы процесс перенаправления прокси-сервера федерации был успешным, все серверы брандмауэра должны быть настроены таким же, чтобы разрешить протокол передачи гипертекста \(HTTPS\) трафик. Использование протокола HTTPS требуется, так как серверы брандмауэра должны опубликовать прокси-сервер федерации с помощью порта 443, чтобы прокси-сервер федерации в сети периметра мог получить доступ к серверу федерации в корпоративной сети.  
  
> [!NOTE]  
> Любой обмен данными с клиентскими компьютерами также выполняется по протоколу HTTPS.  
  
Кроме того, Интернет-\-сервер брандмауэра, например компьютер, на котором работает Microsoft Internet Security and Acceleration \(ISA\) Server, использует процесс, известный как публикация сервера, для распространения запросов интернет-клиентов к соответствующим периметру и сетевым серверам, таким как прокси-серверы федерации или сервера федерации.  
  
Правила публикации сервера определяют, как работает публикация сервера — по существу это фильтрация всех входящих и исходящих запросы через компьютер ISA Server. Правила публикации сервера назначают входящие клиентские запросы соответствующим серверам за компьютером ISA Server. Сведения о настройке ISA Server для публикации сервера см. в разделе [Создание защищенного правила веб-публикации](https://go.microsoft.com/fwlink/?LinkId=75182).  
  
В Федеративной жизни AD FS эти клиентские запросы обычно выполняются по определенному URL-адресу, например URL-адресу сервера федерации, например http:\//fs.fabrikam.com. Так как эти клиентские запросы приходят из Интернета, сервер межсетевого экрана, подключенный к Интернету\-, должен быть настроен на публикацию URL-адреса идентификатора сервера федерации для каждого прокси-сервера федерации, развернутого в сети периметра.  
  
### <a name="configuring-isa-server-to-allow-ssl"></a>Настройка ISA Server для протокола SSL  
Чтобы упростить безопасный обмен данными AD FS, необходимо настроить ISA Server, чтобы разрешить SSL \(соединений SSL\) между следующими:  
  
-   **Серверы федерации и учетные записи-посредники сервера федерации.** Канал SSL необходим для всех подключений между серверами федерации и прокси-серверами федерации. Таким образом, вы должны настроить ISA Server, чтобы разрешить SSL-соединение между корпоративной сетью и сетью периметра.  
  
-   **Клиентские компьютеры, серверы федерации и прокси-серверы федерации.** Таким образом, между клиентскими компьютерами и серверами федерации, а также между клиентскими компьютерами и серверами федерации можно размещаться компьютер, на котором работает ISA Server, перед сервером федерации или прокси-сервером федерации.  
  
    Если ваша организация выполняет проверку подлинности клиента SSL на сервере федерации или прокси-сервере федерации, то при помещении компьютера, на котором работает ISA Server, перед сервером федерации или прокси-сервером федерации, сервер должен быть настроен для передачи\-через SSL-соединение, так как соединение SSL должно завершиться на сервере федерации или прокси сервера федерации.  
  
    Если ваша организация не выполняет проверку подлинности клиента SSL на сервере федерации или прокси-сервере федерации, то дополнительным вариантом является завершение SSL-подключения на компьютере с ISA Server, а затем повторное\-установление SSL-соединения с сервером федерации или прокси сервера федерации.  
  
> [!NOTE]  
> Сервер федерации или прокси-сервер федерации требует, чтобы подключение было защищено протоколом SSL для защиты содержимого маркера безопасности.  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
