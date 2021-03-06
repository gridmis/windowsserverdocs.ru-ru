---
title: Шаг 2. Установка и Настройка компьютера МАРШРУТИЗАТОР1
description: 'Этот раздел является частью руководства по лаборатории тестирования: демонстрация многосайтового развертывания DirectAccess для Windows Server 2016'
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc20b1a0-540d-4531-a176-50b87c071600
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 3cd73f1a5e2612f4551be1f16e49e9645c5e12c0
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80308736"
---
# <a name="step-2-install-and-configure-router1"></a>Шаг 2. Установка и Настройка компьютера МАРШРУТИЗАТОР1

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом многосайтовом лабораторном практическом занятии компьютер маршрутизатора предоставляет мост IPv4 и IPv6 между корпоративной и 2 подсетями и выступает в качестве маршрутизатора для трафика IP-HTTPS и Teredo.  
  
- Установка операционной системы на компьютере МАРШРУТИЗАТОР1 
  
- Настройка свойств TCP/IP и переименование компьютера  
  
- Отключение брандмауэра
  
- Настройка маршрутизации и пересылки
  
## <a name="install-the-operating-system-on-router1"></a>Установка операционной системы на компьютере МАРШРУТИЗАТОР1  
Сначала установите Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012.  
  
### <a name="to-install-the-operating-system-on-router1"></a>Установка операционной системы на компьютере МАРШРУТИЗАТОР1  
  
1.  Запустите установку Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012 (полная установка).  
  
2.  Для завершения установки следуйте инструкциям и укажите надежный пароль для учетной записи локального администратора. Войдите в систему с помощью учетной записи локального администратора.  
  
3.  Подключите МАРШРУТИЗАТОР1 к сети с доступом к Интернету и запустите Центр обновления Windows, чтобы установить последние обновления для Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012, а затем отключитесь от Интернета.  
  
4.  Подключение компьютера МАРШРУТИЗАТОР1 к корпоративной сети и подсетям из двух сетей.  
  
## <a name="configure-tcpip-properties-and-rename-the-computer"></a>Настройка свойств TCP/IP и переименование компьютера  
Настройте параметры TCP/IP на маршрутизаторе и переименуйте компьютер в МАРШРУТИЗАТОР1.  
  
### <a name="to-configure-tcpip-properties-and-rename-the-computer"></a>Настройка свойств TCP/IP и переименование компьютера  
  
1.  В консоли диспетчер сервера щелкните **локальный сервер**, а затем в области **свойства** рядом с **проводным Ethernet подключением**щелкните ссылку.  
  
2.  В окне " **Сетевые подключения** " щелкните правой кнопкой мыши сетевой адаптер, подключенный к корпоративной сети, щелкните **Переименовать**, **введите "** Корпоративная сеть" и нажмите клавишу ВВОД.  
  
3.  Щелкните правой кнопкой **мыши элемент**Корпоративная сеть и выберите пункт **свойства**.  
  
4.  Щелкните пункт **IP версия 4 (TCP/IPv4)** и нажмите кнопку **Свойства**.  
  
5.  Выберите вариант **Использовать следующий IP-адрес**. В списке **IP-адрес**введите **10.0.0.254**. В списке **Маска подсети**введите **255.255.255.0**и нажмите кнопку **ОК**.  
  
6.  Выберите **Протокол IP версии 6 (TCP/IPv6)** , а затем **Свойства**.  
  
7.  Щелкните **использовать следующий IPv6-адрес**. В качестве **адреса IPv6**введите **2001: db8:1:: FE**. В качестве **длины префикса подсети**введите **64**и нажмите кнопку **ОК**.  
  
8.  В диалоговом окне **Свойства корпоративной** сети нажмите кнопку **Закрыть**.  
  
9. В окне " **Сетевые подключения** " щелкните правой кнопкой мыши сетевой адаптер, подключенный к 2 корпоративной сети, щелкните **Переименовать**, введите **2-** Корпоративная и нажмите клавишу ВВОД.  
  
10. Щелкните правой кнопкой мыши **2-** Корпоративная сеть и выберите пункт **свойства**.  
  
11. Щелкните пункт **IP версия 4 (TCP/IPv4)** и нажмите кнопку **Свойства**.  
  
12. Выберите вариант **Использовать следующий IP-адрес**. В списке **IP-адрес**введите **10.2.0.254**. В списке **Маска подсети**введите **255.255.255.0**и нажмите кнопку **ОК**.  
  
13. Выберите **Протокол IP версии 6 (TCP/IPv6)** , а затем **Свойства**.  
  
14. Щелкните **использовать следующий IPv6-адрес**. В качестве **адреса IPv6**введите **2001: db8:2:: FE**. В качестве **длины префикса подсети**введите **64**и нажмите кнопку **ОК**.  
  
15. В диалоговом окне **свойства 2 корпоративной** сети нажмите кнопку **Закрыть**.  
  
16. Закройте окно **Сетевые подключения**.  
  
17. В консоли диспетчер сервера в области **Свойства** на **локальном сервере**щелкните ссылку рядом с полем **имя компьютера**.  
  
18. В диалоговом окне **Свойства системы** на вкладке  **Имя компьютера** щелкните **Изменить**.  
  
19. В диалоговом окне **изменения имени компьютера или домена** в поле **имя компьютера**введите **МАРШРУТИЗАТОР1**и нажмите кнопку **ОК**.  
  
20. При появлении запроса на перезагрузку компьютера нажмите кнопку **ОК**.  
  
21. В диалоговом окне **Свойства системы** нажмите **Закрыть**.  
  
22. При появлении запроса на перезагрузку компьютера нажмите кнопку **Перезагрузить сейчас**.  
  
23. После перезагрузки компьютера войдите в систему с учетной записью локального администратора.  
  
## <a name="turn-off-the-firewall"></a>Отключение брандмауэра  
Этот компьютер настроен только для обеспечения маршрутизации между корпоративной и подсетями, работающими в двух подсетях. Поэтому брандмауэр должен быть отключен.  
  
### <a name="to-turn-off-the-firewall"></a>Отключение брандмауэра  
  
1.  На **начальном** экране введите**WF. msc**и нажмите клавишу ВВОД.  
  
2.  В окне Брандмауэр Windows в области повышенной безопасности на панели **действия** выберите пункт **свойства**.  
  
3.  В диалоговом окне **Брандмауэр Windows в режиме повышенной безопасности** на вкладке **профиль домена** в поле **состояние брандмауэра**щелкните **выкл**.  
  
4.  В диалоговом окне **Брандмауэр Windows в режиме повышенной безопасности** на вкладке **частный профиль** в поле **состояние брандмауэра**щелкните **выкл**.  
  
5.  В диалоговом окне **Брандмауэр Windows в режиме повышенной безопасности** на вкладке **Общий профиль** в поле **состояние брандмауэра**щелкните **выкл**., а затем нажмите кнопку **ОК**.  
  
6.  Закройте окно Брандмауэр Windows в режиме повышенной безопасности.  
  
## <a name="configure-routing-and-forwarding"></a>Настройка маршрутизации и пересылки  
Чтобы обеспечить маршрутизацию и пересылку служб между корпоративной сетью и подсетями, расположенными в двух подсетях, необходимо включить пересылку в сетевых интерфейсах и настроить статические маршруты между подсетями.  
  
### <a name="to-configure-static-routes"></a>Настройка статических маршрутов  
  
1.  На **начальном** экране введите**cmd. exe**и нажмите клавишу ВВОД.  
  
2.  Включите перенаправление для интерфейсов IPv4 и IPv6 обоих сетевых адаптеров с помощью следующих команд. После ввода каждой команды нажмите клавишу ВВОД.  
  
    ```  
    netsh interface IPv4 set interface Corpnet forwarding=enabled  
    netsh interface IPv4 set interface 2-Corpnet forwarding=enabled  
    netsh interface IPv6 set interface Corpnet forwarding=enabled  
    netsh interface IPv6 set interface 2-Corpnet forwarding=enabled  
    ```  
  
3.  Включите маршрутизацию IP-HTTPS между корпоративной и сетевой подсетями.  
  
    ```  
    netsh interface IPv6 add route 2001:db8:1:1000::/59 Corpnet 2001:db8:1::2  
    netsh interface IPv6 add route 2001:db8:2:2000::/59 2-Corpnet 2001:db8:2::20  
    ```  
  
4.  Включите маршрутизацию Teredo между корпоративной и подсетями, сопринятыми в двух подсетях.  
  
    ```  
    netsh interface IPv6 add route 2001:0:836b:2::/64 Corpnet 2001:db8:1::2  
    netsh interface IPv6 add route 2001:0:836b:14::/64 2-Corpnet 2001:db8:2::20  
    ```  
  
5.  Закройте окно командной строки.
