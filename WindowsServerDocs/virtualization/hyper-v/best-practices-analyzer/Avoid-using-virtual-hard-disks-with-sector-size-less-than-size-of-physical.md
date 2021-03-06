---
title: Избегайте использования виртуальных жестких дисков с размером сектора меньше размера сектора физического хранилища, в котором хранится файл виртуального жесткого диска.
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: b7cf994e-bf4b-4b1b-bad6-ecf7d46d105e
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 944fdce68a2f0b8e9c122f5f9134f0e07de18bbd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366410"
---
# <a name="avoid-using-virtual-hard-disks-with-a-sector-size-less-than-the-sector-size-of-the-physical-storage-that-stores-the-virtual-hard-disk-file"></a>Избегайте использования виртуальных жестких дисков с размером сектора меньше размера сектора физического хранилища, в котором хранится файл виртуального жесткого диска.

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**См** <br />**Системой**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Warning|  
|**Категория**|Настройка|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*Один или несколько виртуальных жестких дисков имеют физический размер сектора, меньший, чем размер физического сектора хранилища, на котором расположен файл виртуального жесткого диска.*  
  
## <a name="impact"></a>**Благоприятн**  
*На виртуальной машине или в приложении, использующем виртуальный жесткий диск, могут возникать проблемы с производительностью. Это влияет на следующие виртуальные машины:*  
  
\<список виртуальных машин >  
  
## <a name="resolution"></a>**Решение**  
*Выполните одно из следующих действий:*  
  
-   *Выполнение миграции хранилища для перемещения виртуального жесткого диска в новую физическую систему*  
  
-   *Использование Windows PowerShell или WMI для включения виртуального жесткого диска формата VHDX для сообщения определенного размера сектора*  
  
-   *Используйте параметр реестра, чтобы разрешить виртуальному жесткому диску виртуального жесткого диска отчитываться о размере физического сектора (4 КБ).*  
  


