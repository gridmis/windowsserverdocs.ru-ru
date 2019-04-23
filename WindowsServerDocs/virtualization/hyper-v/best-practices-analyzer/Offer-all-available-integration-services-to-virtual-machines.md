---
title: Предложения всех доступных интеграции служб на виртуальных машинах
description: Инструкции для устранения проблемы, о которых сообщает это правило анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 2c4b2043-ad81-495e-aa7a-467f813bb3d2
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: c2b5137594f78980f87f6520ae4b4af8203aef32
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883785"
---
# <a name="offer-all-available-integration-services-to-virtual-machines"></a>Предложения всех доступных интеграции служб на виртуальных машинах

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
  
*На виртуальных машинах не включены один или несколько доступных интеграции служб.*  
  
## <a name="impact"></a>Влияние  
  
*Некоторые возможности, не будут доступны для следующих виртуальных машин:*  
  
\<Список имен виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
  
*Если это сделано намеренно, никаких дополнительных действий не требуется. В противном случае рекомендуется, предлагая все службы интеграции в параметрах этих виртуальных машин.*  
  
Доступность некоторых служб integration services можно управлять с помощью параметров виртуальной машины.   
  
#### <a name="to-manage-the-availability-of-integration-services-to-a-virtual-machine"></a>Чтобы управлять доступностью служб integration Services к виртуальной машине  
  
1.  Откройте диспетчер Hyper-V. Нажмите кнопку **запустить**, пункты **Администрирование**, а затем нажмите кнопку **диспетчера Hyper-V**.  
  
2.  В области результатов в разделе **виртуальных машин**, выберите виртуальную машину, которую требуется настроить.  
  
3.  На панели **Действия** откройте раздел **Параметры** рядом с именем виртуальной машины.  
  
4.  В разделе **управления**, нажмите кнопку **служб Integration Services**.  
  
5.  В списке служб integration Services установите флажок для каждой службы, которые вы хотите предложить к виртуальной машине. В случае недоступности типа "флажок" этой определенной интеграции службы не поддерживается гостевой операционной системы, работающей на виртуальной машине.  
  

