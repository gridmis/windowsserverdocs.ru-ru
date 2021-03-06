---
title: Обзор TLS/SSL (поставщик общих служб Schannel)
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: security-tls-ssl
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b7b0432-1bef-4912-8c9a-8989d47a4da9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/16/2018
ms.openlocfilehash: 51e3886339b7864951b322d210e1a05bef4dc1e1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403368"
---
# <a name="tlsssl-overview-schannel-ssp"></a>Обзор TLS/SSL (поставщик общих служб Schannel)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows 10

В этой статье для ИТ-специалистов представлены реализации TLS и SSL в Windows с помощью поставщика услуг безопасности SChannel (SSP) с описанием практических приложений, изменений в реализации Майкрософт и требований к программному обеспечению, а также Дополнительные ресурсы для Windows Server 2012 и Windows 8.

## <a name="BKMK_OVER"></a>Описание
Канал SCHANNEL — это поставщик поддержки безопасности (SSP), в котором реализованы стандартные интернет-протоколы проверки подлинности SSL и TLS.

Интерфейс поставщика поддержки безопасности (SSPI) является интерфейсом API, используемым системами Windows для выполнения функций, связанных с безопасностью, включая проверку подлинности. SSPI выступает в качестве общего интерфейса для нескольких SSP, включая поставщика общих служб SChannel.

Протоколы TLS версий 1,0, 1,1 и 1,2, SSL-версии 2,0 и 3,0, а также датаграмма транспорта транспортного уровня \(DTLS\) протокола версии 1,0, а частный обмен данными \(PCT\) Protocol основаны на криптографии с открытым ключом. Эти протоколы входят в набор протоколов проверки подлинности Schannel. Для всех протоколов канала SCHANNEL используется модель клиент-сервер.

## <a name="BKMK_APP"></a>Приложений
Одна из проблем при администрировании сети заключается в обеспечении безопасности данных, которые передаются между приложениями по сети без доверия. Вы можете использовать TLS и SSL для проверки подлинности серверов и клиентских компьютеров, а затем использовать протокол для шифрования сообщений между сторонами проверки подлинности.

Например, протоколы TLS и SSL позволяют реализовать следующие возможности.

-   Безопасные транзакции SSL c веб-сайтом электронной коммерции
-   Доступ клиента с проверкой подлинности к веб-сайту, защищенному протоколом SSL
-   Удаленный доступ.
-   Доступ к SQL
-   Электронная почта

## <a name="BKMK_SOFT"></a>Необходимость
Протоколы TLS и SSL используют модель "клиент-сервер" и основаны на проверке подлинности на основе сертификата, для которой требуется инфраструктура открытых ключей.

## <a name="BKMK_INSTALL"></a>Сведения о диспетчер сервера
Для реализации TLS, SSL или SChannel не требуется никаких действий по настройке.

## <a name="see-also"></a>См. также ##

-   [Пакет безопасности SChannel](https://docs.microsoft.com/windows/desktop/com/schannel)
-   [Безопасный канал](https://docs.microsoft.com/windows/desktop/SecAuthN/secure-channel)
-   [Протокол безопасности транспортного уровня](https://docs.microsoft.com/windows/desktop/SecAuthN/transport-layer-security-protocol)
