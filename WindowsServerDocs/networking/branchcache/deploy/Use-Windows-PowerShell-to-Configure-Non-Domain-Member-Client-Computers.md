---
title: Настройка клиентских компьютеров, не являющихся членами домена, с помощью Windows PowerShell
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 1b511e1a-686d-441f-a1c7-d4d029e1a061
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 9b31aa1eed6ccfb72aff012bf9483c90336d0f57
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319185"
---
# <a name="use-windows-powershell-to-configure-non-domain-member-client-computers"></a>Настройка клиентских компьютеров, не являющихся членами домена, с помощью Windows PowerShell

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Эту процедуру можно использовать для ручной настройки клиентского компьютера BranchCache для режима распределенного кэша или режима кэширования размещенного кэша.  
  
> [!NOTE]  
> Если вы настроили клиентские компьютеры BranchCache с помощью групповая политика, параметры групповая политика переопределяют любую ручную настройку клиентских компьютеров, к которым применяются политики.  
  
Членство в группах « **Администраторы**» или «эквивалентное» является минимальным требованием для выполнения этой процедуры.  
  
### <a name="to-enable-branchcache-distributed-or-hosted-cache-mode"></a>Включение распределенного или размещенного кэша BranchCache  
  
1.  На клиентском компьютере BranchCache, который требуется настроить, запустите Windows PowerShell от имени администратора, а затем выполните одно из следующих действий.  
  
    -   Чтобы настроить клиентский компьютер для режима распределенного кэша BranchCache, введите следующую команду и нажмите клавишу ВВОД.  
  
        `Enable-BCDistributed`  
  
    -   Чтобы настроить клиентский компьютер для режима кэширования, размещенного в BranchCache, введите следующую команду и нажмите клавишу ВВОД.  
  
        `Enable-BCHostedClient`  
  
        > [!TIP]  
        > Если необходимо указать доступные серверы размещенного кэша, используйте параметр `-ServerNames` с разделенным запятыми списком серверов кэширования в качестве значения параметра. Например, если у вас есть два сервера размещенного кэша с именами HCS1 и HCS2, настройте клиентский компьютер для режима размещенного кэша с помощью следующей команды.  
        >   
        > `Enable-BCHostedClient -ServerNames HCS1,HCS2`  
  


