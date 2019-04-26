---
title: select volume
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d70d776-80ad-4f20-8288-a7997fb1df28
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0ebf9896621268c384ea8129d32c985028054d9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59890735"
---
# <a name="select-volume"></a>select volume

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выбирает указанный том и перемещает фокус на него. Эта команда также может использоваться для отображения в том, который в данный момент имеет фокус в выбранный диск.  
  
  
  
## <a name="syntax"></a>Синтаксис  
  
```  
select volume={<n>|<d>}  
```  
  
## <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|<n>|Номер тома, получающего фокус. Можно просмотреть номера всех томов на диске, выделенного с помощью **список томов** в DiskPart.|  
|<d>|Путь к диску букву или монтирования точки тома, получать фокус.|  
  
## <a name="remarks"></a>Примечания  
  
-   Если том не указан, эта команда отображает том, который в данный момент имеет фокус в выбранный диск.  
  
-   На базовом диске также выборе тома передает фокус элементу соответствующая секция.  
  
-   Если том с соответствующей секции, секции выбирается автоматически.  
  
-   Если выбрана секция с соответствующим томом, том будет определяться автоматически.  
  
## <a name="BKMK_examples"></a>Примеры  
Для перемещения фокуса в томе 2, введите следующую команду:  
  
```  
select volume=2  
```  
  
Чтобы переместить фокус на диск C, введите следующую команду:  
  
```  
select volume=c  
```  
  
Чтобы переместить фокус на томе, подключенном к папку с именем «mountpath», введите следующую команду:  
  
```  
select volume=c:\mountpath  
```  
  
Чтобы отобразить том, который в данный момент имеет фокус в выбранный диск, введите следующую команду:  
  
```  
select volume  
```  
  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  

  
