---
ms.assetid: 696a29b2-d627-4c9a-a384-9c8aaf50bd23
title: Определение необходимого типа шаблона правил утверждений
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: eaf0e9fca9b24eb4e67caa4237efe044937d5831
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407402"
---
# <a name="determine-the-type-of-claim-rule-template-to-use"></a>Определение необходимого типа шаблона правил утверждений


Важной частью разработки службы федерации Active Directory (AD FS) \(AD FS\) инфраструктуры является определение полного набора правил утверждений, а также соответствующих шаблонов правил утверждений, которые следует использовать для их создания — для каждого партнера, который будет участвовать в Федерации с вашей организацией. Правила создаются с помощью шаблонов правил утверждений в оснастке управления AD FS\-в.  
  
Каждый набор правил для утверждений, который вы настраиваете, может быть связан только с одним федеративным отношением доверия. Это означает, что нельзя создать набор правил в одном отношении доверия и использовать его для других отношений доверия в службе федерации. Вместо этого можно легко создать правила из шаблонов правил для утверждений, помогающих быстро создать необходимый набор утверждений, согласованных между каждым участником федерации и вашей организацией.  
  
Дополнительные сведения правилах и шаблонах правил см. в разделе [The Role of Claim Rules](The-Role-of-Claim-Rules.md).  
  
Прежде чем приступить к определению типов шаблонов правил для утверждений, которые следует использовать, ответьте на следующие вопросы.  
  
-   Какие утверждения будут предоставляться вашими доверенными поставщиками утверждений?  
  
-   Каким утверждениям вы доверяете от каждого поставщика утверждений?  
  
-   Какие утверждения требуются проверяющими сторонами, доверяющими этой службе федерации?  
  
-   Какие утверждения вы готовы сообщать каждой проверяющей стороне?  
  
-   Какие пользователи должны иметь доступ к каждой проверяющей стороне?  
  
Ответы на эти вопросы помогут вам планировать надежную архитектуру правил для утверждений. Они также помогут создать гладкую стратегию авторизации и контроля доступа и повысить эффективность вашей рабочей группы развертывания во время выпуска.  
  
В следующем разделе вы можете узнать, какой тип шаблонов правил следует выбрать для вашей среды, исходя из ваших бизнес-требований.  
  
## <a name="claim-rule-template-types"></a>Типы шаблонов правил для утверждений  
В следующей таблице описаны все типы шаблонов правил утверждений, которые можно использовать для создания правил с помощью оснастки управления AD FS\-в, а также преимущества использования одного типа шаблона в другом.  
  
|Тип шаблона правила|Описание|Преимущества|Недостатки|  
|----------------------|---------------|--------------|-----------------|  
|Пропуск или фильтрация входящего утверждения|Используется для создания правила, которое будет пропускать все значения утверждений для выбранного типа утверждения или фильтровать утверждения на основе значений утверждений, чтобы пропускались только определенные значения утверждений для выбранного типа утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use a Pass Through or Filter Claim Rule](When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md).|— Может использоваться для выбора конкретных утверждений, которые должны приниматься или выдаваться без изменений|-Невозможно изменить тип и значение утверждения|  
|Преобразование входящего утверждения|Используется для создания правила, которое может выбрать входящее утверждение и сопоставить его с другим типом утверждения или сопоставить его значение с новым значением утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use a Transform Claim Rule](When-to-Use-a-Transform-Claim-Rule.md).|— Может использоваться для нормализации типов или значений утверждений.<br />— Может заменить суффикс электронной почты e\-входящего утверждения.|— Более сложные замены строк требует настраиваемого правила.|  
|Отправка атрибутов LDAP как утверждений|Используется для создания правила, которое будет выбрать атрибуты из хранилища атрибутов LDAP для отправки проверяющей стороне в виде утверждений.<br /><br />Дополнительные сведения см. в разделе [When to Use a Send LDAP Attributes as Claims Rule](When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md).|— Может быть источником утверждений из любого AD DS\/AD LDS хранилище атрибутов.<br />— Множественные утверждения могут быть выданы с помощью одного правила.|-Performance — медленный результат уточняющего запроса учетной записи<br />-Невозможно использовать настраиваемый фильтр LDAP для выполнения запросов|  
|Отправка членства в группах в качестве утверждения|Используется для создания правила, которое может отправлять указанный тип и значение утверждения, если пользователь является членом группы безопасности Active Directory. С помощью этого правила будет отправляться только одно утверждение на основе выбранной группы.<br /><br />Дополнительные сведения см. в разделе [When to Use a Send Group Membership as a Claim Rule](When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md).|-Высокая производительность при выдаче утверждений группы — без поиска учетной записи|-Пользователь должен быть членом локальной группы Active Directory|  
|Отправка утверждений с помощью настраиваемого правила|Используется для создания настраиваемого правила, которое предоставляет дополнительные варианты по сравнению со стандартным шаблоном правила. Вы пишете пользовательские правила с помощью языка правил для утверждений AD FS.<br /><br />Дополнительные сведения см. в разделе [When to Use a Custom Claim Rule](When-to-Use-a-Custom-Claim-Rule.md).|— Может использоваться для исходных утверждений из хранилища атрибутов SQL.<br />— Может использоваться для указания настраиваемого фильтра LDAP<br />— Может использоваться для выдача PPID<br />— Может использоваться с пользовательским хранилищем атрибутов;<br />— Может использоваться для добавления утверждений только к набору входящих утверждений.<br />— Может использоваться для отправки утверждений на основе более одного входящего утверждения|— Более сложная настройка \- может потребоваться некоторое время увеличения времени, чтобы получить знания о языке правил утверждений.|  
|Разрешать или запрещать пользователям на основании входящего утверждения|Используется для создания правила, которое будет разрешать или запрещать доступ пользователей к проверяющей стороне на основе типа и значения входящего утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md).|— Упрощает процесс авторизации.|— Требует указания только одного типа утверждения и одного значения утверждения.<br />— Не поддерживает сопоставление шаблонов для значений утверждений.|  
|Разрешить всем пользователям|Позволяет создать правило, которое разрешает всем пользователям доступ к проверяющей стороне.<br /><br />Дополнительные сведения см. в разделе [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md).|-Simple для настройки|Менее надежнее, чем использование разрешенных или запрещенных пользователей на основе шаблона входящего утверждения|  
  

