---
title: Включение всех служб Integration Services на виртуальных машинах
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 16e202ad-3795-40c9-8176-7ca319e56d26
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 1984c3d1d6261756bf83f899985b457681537046
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364888"
---
# <a name="enable-all-integration-services-in-virtual-machines"></a>Включение всех служб Integration Services на виртуальных машинах

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Warning|  
|**Категория**|Настройка|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблема  
  
*Одна или несколько служб Integration Services отключены или не работают на виртуальной машине.*  
  
## <a name="impact"></a>Влияние  
  
*Служба или функция интеграции может работать неправильно для следующих виртуальных машин:*  
  
\<список имен виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
  
*Используйте оснастку "службы" или программу командной строки SC config, чтобы убедиться, что служба настроена для автоматического запуска и не остановлена.*  
  
#### <a name="to-configure-how-a-service-is-started-using-the-services-snap-in"></a>Настройка запуска службы с помощью оснастки «службы»  
  
1.  Используйте службы удаленных рабочих столов или подключение виртуальной машины для подключения к виртуальной машине и входа в операционную систему на виртуальной машине.  
  
2.  Откройте компонент "Службы". (Нажмите кнопку **Пуск**, щелкните в поле **начать поиск** , введите **Services. msc**и нажмите клавишу ВВОД.)  
  
3.  В области сведений щелкните правой кнопкой мыши службу, которую требуется настроить, и выберите пункт **Свойства**.  
  
4.  На вкладке **Общие** в поле Тип **запуска** выберите пункт **автоматически**.  
  
#### <a name="to-configure-how-a-service-is-started-using-sc-config"></a>Настройка запуска службы с помощью SC config  
  
1.  Откройте Windows PowerShell. (На рабочем столе нажмите кнопку **Пуск** и начните вводить **Windows PowerShell**.)  
  
2.  Щелкните правой кнопкой мыши **Windows PowerShell** и выберите команду **Запуск от имени администратора**.  
  
3.  Замените < service-name > именем службы, а затем введите:  
  
    ```  
    sc config <service-name> start=auto  
    ```  
  


