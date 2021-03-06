---
title: Использовать все виртуальные функции для работы в сети, если они доступны
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: bf895484-6a0d-4aa4-9a42-9fac739e875d
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 8798a7021b3df0113b8d957340d6d688acead5c7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393345"
---
# <a name="use-all-virtual-functions-for-networking-when-they-are-available"></a>Использовать все виртуальные функции для работы в сети, если они доступны

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Warning|  
|**Категория**|Настройка|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблема  
*Некоторые возможности аппаратного ускорения не используются*  
  
## <a name="impact"></a>Влияние  
*Эта конфигурация может привести к тому, что общая загрузка ЦП будет выше, чем требуется. Производительность сети может быть неоптимальной на следующих виртуальных машинах:*  
  
\<список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
*Рассмотрите возможность настройки виртуального сетевого адаптера для SR-IOV, если физическое оборудование поддерживает SR-IOV, и если эта конфигурация не конфликтует с сетевыми компонентами, необходимыми для виртуальной машины.*  
  


