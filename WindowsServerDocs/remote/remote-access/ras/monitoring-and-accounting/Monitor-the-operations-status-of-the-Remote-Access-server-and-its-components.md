---
title: Мониторинг статуса работы сервера удаленного доступа и его компонентов
description: Эта статья является частью руководств по мониторингу удаленного доступа и учету в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 077a3a64-2fa3-4994-9711-ec1fbdc081ba
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 64471ba81842fb91a7f6ef765e171949294102fa
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80314181"
---
# <a name="monitor-the-operations-status-of-the-remote-access-server-and-its-components"></a>Мониторинг статуса работы сервера удаленного доступа и его компонентов

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

**Примечание.** Windows Server 2012 объединяет DirectAccess и службы маршрутизации и удаленного доступа (RRAS) в единую роль удаленного доступа.  
  
Консоль управления на сервере удаленного доступа может использоваться для отслеживания состояния операций.  
  
> [!NOTE]  
> Для выполнения задачи, описанной в этом разделе, необходимо войти в систему как член группы "Администраторы домена" или член группы "Администраторы" на каждом компьютере. Если вы не можете выполнить задачу, войдя в учетную запись, которая является членом группы "Администраторы", попробуйте выполнить задачу, войдя в учетную запись, которая является членом группы "Администраторы домена".  
  
#### <a name="to-monitor-the-remote-access-server-operations-status"></a>Мониторинг состояния операций сервера удаленного доступа  
  
1.  В **диспетчере серверов** щелкните **Средства** и выберите пункт **Управление удаленным доступом**.  
  
2.  Щелкните **панель мониторинга** , чтобы перейти к **отчетам удаленного доступа** в **консоли управления удаленным доступом**.  
  
3.  На панели мониторинга мониторинга Обратите внимание на плитку **состояние операций** в плитке **состояние сервера** . На этой плитке перечислены состояние операций сервера и состояние всех компонентов сервера.  
  
4.  Нажмите кнопку **Обновить** в разделе **задачи** на правой панели, чтобы перезагрузить состояние операции. Состояние операций автоматически обновляется каждые пять минут, то есть интервалом обновления по умолчанию. Чтобы изменить интервал обновления по умолчанию, щелкните **настроить интервал обновления**.  
  
![](../../../media/Monitor-the-operations-status-of-the-Remote-Access-server-and-its-components/PowerShellLogoSmall.gif)***<em>эквивалентных команд Windows PowerShell Windows PowerShell</em>***  
  
Следующие командлеты Windows PowerShell выполняют ту же функцию, что и предыдущая процедура. Введите каждый командлет на отдельной строке. Они могут отображаться с переносом на несколько строк из-за ограничений форматирования.  
  
> [!NOTE]  
> Команда для состояния операций кластера включена для справки.  
  
```  
PS> Get-RemoteAccessHealth  
PS> Get-RemoteAccessHealth -Cluster  
```  
  


