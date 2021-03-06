---
ms.assetid: 692bd2af-deee-44cf-9af9-f364677e267f
title: Планирование размещения контроллеров доменов
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: ff0cba67454080db7cca4b012ae0a2d5cb40e412
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408757"
---
# <a name="planning-domain-controller-placement"></a>Планирование размещения контроллеров доменов

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

После сбора всех сведений о сети, которые будут использоваться для проектирования топологии сайтов, следует спланировать, где нужно разместить контроллеры домена, в том числе контроллеры корневого домена леса, региональные контроллеры домена, владельцы ролей хозяина операций и серверы глобального каталога.  
  
В Windows Server 2008 также можно воспользоваться контроллерами домена только для чтения (RODC). RODC — это новый тип контроллера домена, который содержит разделы базы данных Active Directory, предназначенные только для чтения. За исключением паролей учетных записей, RODC содержит все объекты и атрибуты Active Directory, которые содержатся в контроллере домена с возможностью записи. Однако нельзя вносить изменения в базу данных, которая хранится на RODC. Изменения необходимо вносить на контроллер домена с возможностью записи, а затем реплицировать обратно в RODC.  
  
Контроллеры домена только для чтения предназначены для развертывания в удаленных средах или филиалах, в которых обычно есть относительно мало пользователей, низкая физическая безопасность, относительно слабая пропускная способность сети на центральном сайте и персонал с ограниченным набором сведений. Технология (ИТ). Развертывание RODC приводит к повышению безопасности и повышению эффективности доступа к сетевым ресурсам. Дополнительные сведения о функциях RODC см. в разделе AD DS: Контроллеры домена только для чтения ([https://go.microsoft.com/fwlink/?LinkID=106616](https://go.microsoft.com/fwlink/?LinkID=106616)). Сведения о развертывании RODC см. в разделе Пошаговое руководство по контроллерам домена только для чтения ([https://go.microsoft.com/fwlink/?LinkID=92728](https://go.microsoft.com/fwlink/?LinkID=92728)).  
  
> [!NOTE]  
> В этом руководство не объясняется, как определить правильное количество контроллеров домена и требования к оборудованию контроллера домена для каждого домена, представленного на каждом сайте.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Планирование размещения корневого контроллера домена в лесу](../../ad-ds/plan/Planning-Forest-Root-Domain-Controller-Placement.md)  
  
-   [Планирование размещения регионального контроллера домена](../../ad-ds/plan/Planning-Regional-Domain-Controller-Placement.md)  
  
-   [Планирование размещения сервера глобального каталога](../../ad-ds/plan/Planning-Global-Catalog-Server-Placement.md)  
  
-   [Планирование размещения роли хозяина операций](../../ad-ds/plan/Planning-Operations-Master-Role-Placement.md)  
  


