---
title: Анализатор соответствия рекомендациям для Hyper-V
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 3747faa5-6e9f-499e-8a79-3fb9d73b6b92
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 671e1de78b390e1b595bb218ece375e88a47155b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365150"
---
# <a name="best-practices-analyzer-for-hyper-v"></a>Анализатор соответствия рекомендациям для Hyper-V

>Область применения. Windows Server 2016
  
*Рекомендации* по управлению Windows — это руководства, которые эксперты считают идеальным способом настройки сервера в обычных условиях. Необязательное возникновение проблем может привести к неоправданным нарушениям рекомендаций. Но они могут указывать на конфигурации серверов, которые могут привести к снижению производительности, снижению надежности, непредвиденным конфликтам, повышению угроз безопасности или другим потенциальным проблемам.  
  
Анализатор соответствия рекомендациям проверяет компьютер с помощью правил, основанных на этих рекомендациях, и сообщает о результатах. Каждое правило рекомендаций содержит сведения о соответствии правила. В этом разделе описываются эти правила, которые помогут вам разобраться с рекомендациями, применяемыми к Hyper-V, а также интерпретировать результаты при обнаружении условий, которые не соответствуют рекомендациям.  
  
Дополнительные сведения о анализатор соответствия рекомендациям и проверках см. в разделе [анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
## <a name="about-hyper-v"></a>Сведения о Hyper-V  
Hyper-V позволяет одновременно запускать несколько операционных систем на одном физическом компьютере, запустив каждую из них на виртуальной машине. Виртуальные машины позволяют более эффективно и гибко использовать вычислительные ресурсы. Дополнительные сведения о Hyper-V см. [в статье Hyper-v на Windows Server 2016](../Hyper-V-on-Windows-Server.md).  
  


