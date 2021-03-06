---
ms.assetid: b8df1828-5ead-4c90-b0fe-95c675116b7c
title: Создание проекта подразделения
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: a699a30cce3b330c434fdb3784214de3a2daa403
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408955"
---
# <a name="creating-an-organizational-unit-design"></a>Создание проекта подразделения

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Владельцы леса несут ответственность за создание структур подразделения для своих доменов. Создание структур подразделения включает в себя проектирование структуры подразделений, назначение роли владельца подразделения и создание подразделений учетных записей и ресурсов.  
  
Сначала создайте структуру подразделений, чтобы включить делегирование администрирования. После завершения проектирования подразделений можно создать дополнительные структуры подразделений для применения групповая политика к пользователям и компьютерам и ограничить видимость объектов. Дополнительные сведения см. в разделе Разработка инфраструктуры групповая политика ([https://go.microsoft.com/fwlink/?LinkId=106655](https://go.microsoft.com/fwlink/?LinkId=106655)).  
  
## <a name="ou-owner-role"></a>Роль владельца подразделения  
Владелец леса определяет владельца подразделения для каждого подразделения, разрабатывается для домена. Владельцы подразделения — это диспетчеры данных, которые управляют поддеревом объектов в службах домен Active Directory Services (AD DS). Владельцы подразделения могут контролировать делегирование администрирования и применение политики к объектам в их подразделении. Они также могут создавать новые поддеревья и делегировать администрирование подразделений внутри этих поддеревьев.  
  
Поскольку владельцы подразделения не владеют и не управляют работой службы каталогов, можно отделить владельца и администрирование службы каталогов от владения и администрирования объектов, уменьшая число администраторов служб, имеющих высокий уровень. доступа.  
  
Подразделения обеспечивают административную автономность и средства для управления видимостью объектов в каталоге. Подразделения обеспечивают изоляцию от других администраторов данных, но не обеспечивают изоляцию от администраторов служб. Хотя владельцы подразделения имеют контроль над поддеревом объектов, владелец леса полностью контролирует все поддеревья. Это позволяет владельцу леса исправлять ошибки, такие как ошибка в списке управления доступом (ACL), и повторно запрашивать делегированные поддеревья при завершении работы администраторов данных.  
  
## <a name="account-ous-and-resource-ous"></a>Подразделения учетных записей и подразделения ресурсов  
Подразделения учетных записей содержат объекты пользователей, групп и компьютеров. Владельцы леса должны создать структуру подразделений для управления этими объектами, а затем делегировать управление структурой владельцу подразделения. При развертывании нового домена AD DS создайте подразделение учетной записи для домена, чтобы можно было делегировать управление учетными записями в домене.  
  
Подразделения ресурсов содержат ресурсы и учетные записи, ответственные за управление этими ресурсами. Владелец леса также отвечает за создание структуры подразделений для управления этими ресурсами и делегирования контроля над этой структурой владельцу подразделения. При необходимости создайте подразделения ресурсов на основе требований каждой группы в Организации для автономного управления данными и оборудованием.  
  
## <a name="documenting-the-ou-design-for-each-domain"></a>Документирование структуры подразделений для каждого домена  
Соберите команду для проектирования структуры подразделений, используемой для делегирования контроля над ресурсами в лесу. Владелец леса может участвовать в процессе разработки и должен утверждать структуру подразделения. Вы также можете использовать по крайней мере одного администратора служб, чтобы убедиться в том, что проект является допустимым. Другие участники группы проектирования могут включать администраторов данных, которые будут работать с подразделениями, и владельцы подразделений, которые будут отвечать за управление ими.  
  
Важно документировать структуру подразделений. Перечислите имена подразделений, которые планируется создать. И для каждого подразделения Задокументируйте тип подразделения, владельца подразделения, родительского подразделения (если применимо) и источника этого подразделения.  
  
Для листа, помогающего документировать структуру подразделений, скачайте Job_Aids_Designing_and_Deploying_Directory_and_Security_Services. zip из вспомогательных средств для пакета развертывания Windows Server 2003 ([https://go.microsoft.com/fwlink/?LinkID=102558](https://go.microsoft.com/fwlink/?LinkID=102558)) и откройте «определение подразделений для каждого домена». (DSSLOGI_9. doc).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Общие сведения о понятиях проекта подразделения](../../ad-ds/plan/Reviewing-OU-Design-Concepts.md)  
  
-   [Делегирование администрирования с помощью объектов подразделений](../../ad-ds/plan/Delegating-Administration-by-Using-OU-Objects.md)  
  


