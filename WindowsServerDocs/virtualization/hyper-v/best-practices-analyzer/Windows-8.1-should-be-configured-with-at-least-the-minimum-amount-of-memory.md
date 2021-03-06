---
title: Для Windows 8.1 следует настроить по крайней мере минимальный объем памяти.
description: Содержит инструкции по устранению проблемы, о которой сообщило это правило анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 84d7edab-610e-4265-87d0-9869f64b0039
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 0004432dc9fbfd0d294f3f7d96dcb1ea80334801
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393326"
---
# <a name="windows-81-should-be-configured-with-at-least-the-minimum-amount-of-memory"></a>Для Windows 8.1 следует настроить по крайней мере минимальный объем памяти.

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Ошибка|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.
  
## <a name="issue"></a>**Проблема**  
*Для виртуальной машины, на которой работает Windows 8.1, настраивается меньше минимального объема ОЗУ (512 МБ).*  
  
## <a name="impact"></a>**Благоприятн**  
*Гостевая операционная система на следующих виртуальных машинах может не запускаться или может работать ненадежно:*  
```  
<list of virtual machines>  
```  
## <a name="resolution"></a>**Решение**  
*Используйте диспетчер Hyper-V, чтобы увеличить объем памяти, выделенной для этой виртуальной машины, по крайней мере 512 МБ.*  
  
#### <a name="increase-the-memory-using-hyper-v-manager"></a>Увеличение объема памяти с помощью диспетчера Hyper-V  
  
1.  Откройте диспетчер Hyper-V. Нажмите кнопку **запустить**, пункты **Администрирование**, а затем нажмите кнопку **диспетчера Hyper-V**.  
  
2.  В области результатов в разделе **виртуальные машины**выберите виртуальную машину, которую требуется настроить. Состояние виртуальной машины должно быть указано в состоянии **Off**. Если это не так, щелкните правой кнопкой мыши виртуальную машину и выберите пункт **Завершение работы**.  
  
3.  На панели **Действия** откройте раздел **Параметры** рядом с именем виртуальной машины.  
  
4.  В области навигации щелкните **память**.  
  
5.  На странице **память** задайте для параметра **ОЗУ для запуска** значение не менее 512 МБ и нажмите кнопку **ОК**.  
  
### <a name="increase-the-memory-using-windows-powershell"></a>Увеличение объема памяти с помощью Windows PowerShell  
  
1.  Откройте Windows PowerShell. (На рабочем столе нажмите кнопку **Пуск** и начните вводить **Windows PowerShell**.)  
  
2.  Щелкните правой кнопкой мыши **Windows PowerShell** и выберите команду **Запуск от имени администратора**.  
  
3.  Выполните эту команду после замены \<MyVM > именем своей виртуальной машины:  
  
```  
Set-VMMemory <MyVM> -StartupBytes 512MB  
```  
  
## <a name="see-also"></a>См. также  
[Set-Вммемори](https://technet.microsoft.com/library/hh848572.aspx)  
  


