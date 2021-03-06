---
title: change logon
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41466260-aee9-4333-bcb6-178112c22afd Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c04eaffe366dce079aed53351589c1b5026954e3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379645"
---
>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="change-logon"></a>change logon
Включает или отключает вход из сеансов клиента или отображает текущее состояние входа.
Эта служебная программа полезна для обслуживания системы.
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).
> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.
> ## <a name="syntax"></a>Синтаксис
> ```
> change logon {/query | /enable | /disable | /drain | /drainuntilrestart}
> ```
> ## <a name="parameters"></a>Параметры
> 
> |     Параметр      |                                                       Описание                                                        |
> |--------------------|--------------------------------------------------------------------------------------------------------------------------|
> |       /Query       |                             Отображает текущее состояние входа в систему независимо от того, включено или отключено.                              |
> |      разрешение       |                              Включает вход из сеансов клиента, но не из консоли.                              |
> |      /Disable      |  Отключает Последующие входы в систему из клиентских сеансов, но не из консоли. Не влияет на пользователей, выполнивших вход в систему.   |
> |       /драин       |                 Отключает вход из новых клиентских сеансов, но разрешает повторное подключение к существующим сеансам.                 |
> | /драинунтилрестарт | Отключает вход из новых клиентских сеансов, пока компьютер не будет перезагружен, но допускает повторное подключение к существующим сеансам. |
> |         /?         |                                           Отображение справки в командной строке.                                           |
> 
> ## <a name="remarks"></a>Примечания
> - Только администраторы могут использовать команду " **изменить вход** ".
> - При перезагрузке системы снова включаются входы в систему. Если вы подключены к серверу узла сеансов удаленный рабочий стол (узел сеансов удаленных рабочих столов) из сеанса клиента и отключите вход в систему, а затем выйдете из системы перед повторным включением входов, вы не сможете повторно подключиться к сеансу. Чтобы повторно включить вход из сеансов клиента, войдите в систему в консоли.
>   ## <a name="BKMK_examples"></a>Примеров
> - Чтобы отобразить текущее состояние входа в систему, введите:
>   ```
>   change logon /query
>   ```
> - Чтобы включить вход из сеансов клиента, введите:
>   ```
>   change logon /enable
>   ```
> - Чтобы отключить вход клиентов, введите:
>   ```
>   change logon /disable
>   ```
>   #### <a name="additional-references"></a>Дополнительные ссылки
>   [Раздел синтаксиса командной строки](command-line-syntax-key.md)
>   [изменение](change.md)
>   [службы удаленных рабочих столов &#40;Справочник по&#41; командам служб терминалов](remote-desktop-services-terminal-services-command-reference.md)
