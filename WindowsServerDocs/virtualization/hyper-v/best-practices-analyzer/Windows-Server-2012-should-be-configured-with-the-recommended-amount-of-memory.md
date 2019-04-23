---
title: Windows Server 2012 должны быть настроены Рекомендуемый объем памяти
description: Инструкции для устранения проблемы, о которых сообщает это правило анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 12d0b473-cf6a-4746-b03d-2ceeb701c5d0
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 601682917e242b747d6ed8b9922372aca234cfd9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825805"
---
# <a name="windows-server-2012-should-be-configured-with-the-recommended-amount-of-memory"></a>Windows Server 2012 должны быть настроены Рекомендуемый объем памяти

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|   
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*Виртуальную машину под управлением Windows Server 2012 оснащен меньше, чем Рекомендуемый объем ОЗУ, который составляет 2 ГБ.*  
  
## <a name="impact"></a>**Влияние**  
*Гостевой операционной системы и приложений может работать неправильно. Не может быть недостаточно памяти для одновременного выполнения нескольких приложений. Это влияет на следующие виртуальные машины:*  
  
\<Список виртуальных машин >  
  
## <a name="resolution"></a>**Решение**  
*Используйте диспетчер Hyper-V, чтобы увеличить объем памяти, выделенной для этой виртуальной машины по крайней мере 2 ГБ.*  
  
### <a name="increase-the-memory-using-hyper-v-manager"></a>Увеличьте объем памяти, с помощью диспетчера Hyper-V  
  
1.  Откройте диспетчер Hyper-V. Нажмите кнопку **запустить**, пункты **Администрирование**, а затем нажмите кнопку **диспетчера Hyper-V**.  
  
2.  В области результатов в разделе **виртуальных машин**, выберите виртуальную машину, которую требуется настроить. Состояние виртуальной машины должен быть указан в качестве **Off**. Если это не так, щелкните правой кнопкой мыши виртуальную машину и нажмите кнопку **завершение работы**.  
  
3.  На панели **Действия** откройте раздел **Параметры** рядом с именем виртуальной машины.  
  
4.  В области навигации щелкните **памяти**.  
  
5.  На **памяти** странице **ОЗУ для запуска** по крайней мере 2 ГБ и выберите команду **ОК**.  
  
### <a name="increase-the-memory-using-windows-powershell"></a>Увеличьте объем памяти, с помощью Windows PowerShell  
  
1.  Откройте Windows PowerShell. (На рабочем столе щелкните **запустить** и начните вводить **Windows PowerShell**.)  
  
2.  Щелкните правой кнопкой мыши **Windows PowerShell** и нажмите кнопку **Запуск от имени администратора**.  
  
3.  Выполните эту команду после замены \<MyVM > с именем виртуальной машины:  
  
```  
Set-VMMemory <MyVM> -StartupBytes 2GB  
```  
  
## <a name="see-also"></a>См. также  
[SET-VMMemory](https://technet.microsoft.com/library/hh848572.aspx)  
  

