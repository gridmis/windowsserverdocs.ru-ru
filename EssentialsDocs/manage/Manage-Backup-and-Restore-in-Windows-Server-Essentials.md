---
title: Управление архивацией и восстановлением в Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 41000915-f6ff-4dbb-b7be-629ef36386d4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 37435b8b51bbc6ba4deb09a50f2c85045ecf0536
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80311363"
---
# <a name="manage-backup-and-restore-in-windows-server-essentials"></a>Управление архивацией и восстановлением в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Windows Server Essentials предоставляет надежные способы для выполнения регулярной архивации сервера и сетевых компьютеров. В случае потери данных можно восстановить данные из успешного архива на сервере без восстановления всего компьютера. При необходимости можно выполнить полное восстановление системы на сервере или клиентских компьютерах в сети. В следующей таблице описаны различные варианты архивации и их преимущества.  
  
|Возможность архивации|Описание|Преимущества|  
|--------------------|-----------------|----------------|  
|Архивация данных сервера|Архивация сервера под управлением Windows Server Essentials. Данные архивируются на внешний USB-накопитель.<br /><br /> Дополнительные сведения см. в разделе [Управление резервным копированием сервера](Manage-Server-Backup-in-Windows-Server-Essentials.md) , [восстановление или восстановление сервера](Restore-or-repair-your-server-running-Windows-Server-Essentials.md).|— Может восстанавливать файлы и папки на сервере.<br /><br /> — Может выполнить полное восстановление системы сервера.|  
|Архивация клиентских компьютеров|Архивация клиентских компьютеров в сети. Выполняется архивация данных на сервере, работающем под управлением Windows Server Essentials.<br /><br /> Дополнительные сведения см. в статьях [Управление резервным копированием клиентов](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md) и [восстановление полной системы из существующей резервной копии клиентского компьютера](Restore-a-full-system-from-an-existing-client-computer-backup.md).|— Может восстанавливать файлы и папки с сервера.<br /><br /> — Может выполнить полное восстановление системы клиентского компьютера.|  
| архивации Microsoft Azure|Выполнение оперативной архивации файлов или папок на сервере. При использовании Azure Backup для резервного копирования данных сервера эти данные шифруются с помощью парольной фразы перед их отправкой в защищенный центр обработки данных в Интернете.<br /><br /> Дополнительные сведения см. в статье [управление оперативной архивацией](Manage-Online-Backup-in-Windows-Server-Essentials.md).|— Может восстанавливать файлы и папки с сервера.<br /><br /> — При добавочном резервном копировании в облако передаются только изменения в файлах.<br /><br /> — Резервные копии хранятся в Microsoft Azure и находятся вне офиса, что снижает потребность в защите и защите носителей на сайте резервного копирования.|  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
