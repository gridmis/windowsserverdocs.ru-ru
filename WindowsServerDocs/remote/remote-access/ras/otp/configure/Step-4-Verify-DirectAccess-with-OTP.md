---
title: Шаг 4. Проверка DirectAccess с OTP
description: Эта статья является частью руководств по развертыванию удаленного доступа с помощью проверки подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed49a0a3-1c45-42e5-8f13-cad20c1c1d68
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 9a3d3fadbe2f187ae6b5a77137393b7ad7be338b
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80313633"
---
# <a name="step-4-verify-directaccess-with-otp"></a>Шаг 4. Проверка DirectAccess с OTP

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки DirectAccess с помощью развертывания OTP.
  
### <a name="to-verify-otp-health-on-the-remote-access-server"></a>Проверка работоспособности OTP на сервере удаленного доступа

1. На сервере удаленного доступа откройте консоль **управления удаленным доступом** .  

2. В разделе **серверы удаленного доступа** выберите сервер удаленного доступа, который был настроен для поддержки OTP.  

3. Щелкните **состояние операции**.  

4. Убедитесь, что состояние OTP отображает зеленый значок и работает.  
  
    > [!NOTE]  
    > Интервал обновления состояния работоспособности будет иметь максимальную сумму значений из раздела реестра Хклм\систем\ккс\сервицес\рамгмтсвк\параметерс\хеалсрефрештимеаут и **интервал времени для активности сервера** , заданный в конфигурации удаленного доступа.  
  
### <a name="to-verify-access-to-internal-resources-using-otp-authentication"></a>Проверка доступа к внутренним ресурсам с помощью проверки подлинности OTP  
  
1.  Подключите клиентский компьютер DirectAccess к корпоративной сети и выполните в командной строке команду **gpupdate/Force** , чтобы получить групповую политику.  
  
2.  Отключите клиентский компьютер от корпоративной сети, подключитесь к внешней сети и попытайтесь получить доступ к внутренним ресурсам. У вас нет доступа к внутренним ресурсам.  
  
3.  В случае токена программного обеспечения получите доступ к токену клиента OTP с помощью инструкций поставщика и запишите текущий код маркера. При использовании маркера оборудования следуйте инструкциям поставщика для проверки подлинности.  
  
4.  В области уведомлений щелкните значок **Сетевые подключения** , чтобы получить доступ к диспетчеру мультимедиа DA.  
  
5.  Щелкните **подключение DirectAccess**и нажмите кнопку **продолжить**.  
  
6.  Введите код токена, указанный ранее, и нажмите кнопку **ОК**. Дождитесь завершения проверки подлинности. Теперь состояние подключения к рабочей области DirectAccess будет **подключено**.  
  
7.  Попытка доступа к внутренним ресурсам. Вам должны быть доступны все корпоративные ресурсы.  
  


