---
ms.assetid: 2a2f493a-9796-454a-9721-e223b799dfa7
title: Планирование размещения корневого контроллера домена в лесу
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: e619d5f5e9cc317f9ba1548d5ed3a32e7bd12c2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402543"
---
# <a name="planning-forest-root-domain-controller-placement"></a>Планирование размещения корневого контроллера домена в лесу

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Контроллеры домена корня леса необходимы для создания путей доверия для клиентов, которым требуется доступ к ресурсам в доменах, отличных от их собственных. Размещение контроллеров корневого домена леса в расположениях концентратора и в расположениях, где размещены центры обработки данных. Если пользователям в данном расположении требуется доступ к ресурсам из других доменов в том же расположении, а доступность сети между центром обработки данных и расположением пользователя ненадежна, можно добавить контроллер корневого домена леса в расположение или создать сочетание доверия между двумя доменами. Более экономично создавать сокращенное доверие между доменами, если у вас нет других причин для размещения контроллера корневого домена леса в этом расположении.  
  
Сокращенные доверия помогают оптимизировать запросы проверки подлинности, выполненные от пользователей, расположенных в любом домене. Дополнительные сведения о доверии между доменами см. в статье Общие сведения о создании междоменного [доверия](https://go.microsoft.com/fwlink/?LinkId=107061).  
  
Сведения о том, как задокументировать размещение контроллера корневого домена леса, см. в разделе [вспомогательные материалы для Windows Server 2003 Deployment Kit](https://go.microsoft.com/fwlink/?LinkID=102558), скачайте Job_Aids_Designing_and_Deploying_Directory_and_Security_Services. zip и откройте "домен Размещение контроллера (DSSTOPO_4. doc).  
  
При создании корневого домена леса необходимо будет обращаться к этим сведениям. Дополнительные сведения о развертывании корневого домена леса см. в разделе [Развертывание корневого домена леса Windows Server 2008](https://technet.microsoft.com/library/cc731174.aspx).  
