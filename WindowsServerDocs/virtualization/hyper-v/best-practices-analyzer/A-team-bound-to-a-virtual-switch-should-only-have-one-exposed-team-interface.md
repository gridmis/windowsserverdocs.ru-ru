---
title: Команда, привязанная к виртуальному коммутатору, должна иметь только один предоставленный интерфейс группы
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 1074f086-1a2e-42e1-b58c-f55e657d5ce1
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 6baa9e4ae900c9b671003872b4eb4589efb2f085
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365398"
---
# <a name="a-team-bound-to-a-virtual-switch-should-only-have-one-exposed-team-interface"></a>Команда, привязанная к виртуальному коммутатору, должна иметь только один предоставленный интерфейс группы

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Warning|  
|**Категория**|Настройка|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*Один или несколько виртуальных коммутаторов привязаны к команде, имеющей несколько интерфейсов группы.*  
  
## <a name="impact"></a>**Благоприятн**  
*Следующие виртуальные коммутаторы могут не иметь доступа к виртуальным ЛС и пропускной способности, используемым другими интерфейсами команды:*  
  
\<список виртуальных коммутаторов >  
  
## <a name="resolution"></a>**Решение**  
*Используйте командлет Windows PowerShell Remove-Нетлбфотеамник для удаления всех интерфейсов команды, отличных от командного интерфейса по умолчанию.*  
  


