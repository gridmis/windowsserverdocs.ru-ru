---
title: Настройка удаленного доступа с проверкой подлинности OTP
description: Эта статья является частью руководств по развертыванию удаленного доступа с помощью проверки подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82505b18-dd77-4dd1-aa27-b2962b8241ca
ms.author: lizross
author: eross-msft
ms.openlocfilehash: d41d89c925c4741de51028678640143fa7618d87
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80313666"
---
# <a name="configure-remote-access-with-otp-authentication"></a>Настройка удаленного доступа с проверкой подлинности OTP

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

 Windows Server 2016 и Windows Server 2012 объединяют VPN DirectAccess и службы маршрутизации и удаленного доступа (RRAS) в одну роль удаленного доступа. В этом обзоре приводятся общие сведения о шагах настройки, необходимых для развертывания одного многосайтового развертывания Windows Server 2016 или Windows Server 2012 с удаленным доступом.  


- [Шаг 1. Реализация развертывания удаленного доступа с одним сервером](../../multisite/configure/Step-1-Implement-a-Single-Server-Remote-Access-Deployment.md). Установите и настройте отдельный сервер удаленного доступа. Инструкции см. в статье [развертывание одного сервера DirectAccess с дополнительными параметрами](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings).

- [Шаг 2. Настройка сервера RADIUS](Step-2-Configure-the-RADIUS-Server.md).

- [Шаг 3. Настройка сервера удаленного доступа для OTP](Step-3-Configure-the-Remote-Access-Server-for-OTP.md).

- [Шаг 4. Проверка DirectAccess с OTP](Step-4-Verify-DirectAccess-with-OTP.md).
  


