---
title: Предварительные требования для развертывания DirectAccess
description: В этом разделе приводятся предварительные требования для развертывания DirectAccess в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57c7e039-42ef-4909-867a-b5f669c9e74e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 14da51a2617764f2ee11eedcbc7a4e10b3b0da15
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309317"
---
# <a name="prerequisites-for-deploying-directaccess"></a>Предварительные требования для развертывания DirectAccess

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В следующей таблице перечислены предварительные требования, необходимые для использования мастеров настройки для развертывания DirectAccess.  
  
|||  
|-|-|  
|Сценарий|Предварительные требования|  
|[Развертывание одного сервера DirectAccess с помощью мастера начало работы](../../remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)|— Брандмауэр Windows должен быть включен для всех профилей.<br /><br />— Поддерживается только для клиентов под управлением Windows 10&reg;, <br />              Windows&reg; 8 и Windows&reg; 8,1 Enterprise.<br /><br />— Инфраструктура открытых ключей не требуется.<br /><br />— Не поддерживается для развертывания двухфакторной проверки подлинности. Для проверки подлинности требуются учетные данные домена.<br /><br />— Автоматически развертывает DirectAccess на всех мобильных компьютерах в текущем домене.<br /><br />— Трафик к Интернету не проходит через DirectAccess. Конфигурация принудительного туннелирования не поддерживается.<br /><br />— Сервер DirectAccess — это сервер сетевых расположений.<br /><br />— Защита доступа к сети (NAP) не поддерживается.<br /><br />-Изменение политик с помощью компонента, отличного от консоли управления DirectAccess или командлетов Windows PowerShell, не поддерживается.<br /><br />— Для многосайтовой конфигурации, сейчас или в будущем, сначала следуйте указаниям в статье [развертывание одного сервера DirectAccess с дополнительными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md).|  
|[Развертывание одного сервера DirectAccess с расширенными параметрами](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)|— Инфраструктура открытых ключей должна быть развернута.<br />    Дополнительные сведения см. в разделе [тест лабораторного руководства мини-модуль: базовый PKI для Windows Server 2012](https://social.technet.microsoft.com/wiki/contents/articles/7862.test-lab-guide-mini-module-basic-pki-for-windows-server-2012.aspx).<br /><br />— Брандмауэр Windows должен быть включен для всех профилей.<br /><br />Следующие серверные операционные системы поддерживают DirectAccess.<br /><br />— Можно развернуть все версии Windows Server 2016 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2012 R2 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2012 в качестве клиента DirectAccess или сервера DirectAccess.<br />— Можно развернуть все версии Windows Server 2008 R2 в качестве клиента DirectAccess или сервера DirectAccess.<br /><br />Следующие клиентские операционные системы поддерживают DirectAccess.<br /><br />— Windows 10&reg; Enterprise<br />— Windows 10&reg; Enterprise 2015 Long Term Servicing Branch (LTSB)<br />— Windows&reg; 8 и 8,1 Enterprise<br />— Windows&reg; 7 Максимальная<br />— Windows&reg; 7 Корпоративная<br /><br />— Конфигурация принудительного туннелирования не поддерживается при проверке подлинности Кербпрокси.<br /><br />-Изменение политик с помощью компонента, отличного от консоли управления DirectAccess или командлетов Windows PowerShell, не поддерживается.<br /><br />-Разделение ролей NAT64, DNS64 и IPHTTPS сервера на другом сервере не поддерживается.|  
  


