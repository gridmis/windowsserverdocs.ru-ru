---
title: Контрольный список действий, выполняемых перед развертыванием
description: Содержит контрольный список, который можно использовать для планирования развертывания служб MultiPoint
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87ea20e4-46cf-49e9-86bf-70be9098c8db
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 38ff3832551024e3d6d89fe6d0f5eb3e136abca6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405015"
---
# <a name="predeployment-checklist"></a>Контрольный список действий, выполняемых перед развертыванием
Используйте следующий контрольный список, чтобы спланировать развертывание служб MultiPoint.  
  
|Шаг|Проблемы|Раздел справки|  
|--------|---------|--------------|  
|1.|Убедитесь, что приложения совместимы со службами MultiPoint.|[Рекомендации по приложениям](Application-Considerations.md)|  
|2.|Определите количество пользователей, которые, скорее всего, обращаются одновременно, на каждом компьютере, на котором выполняются службы MultiPoint, чтобы оценить количество необходимых компьютеров, на которых должны выполняться службы MultiPoint.|[Пользователи, станции и компьютеры](MultiPoint-services-Site-Planning.md#users-stations-and-computers)|  
|3.|Изучите программные приложения и веб-содержимое, к которому, скорее всего, будут обращаться пользователи, и влияние на производительность системы.|[Требования к оборудованию и рекомендации по производительности](hardware-and-performance-recommendations.md)|  
|4.|Определите число и тип станций, которые будут подключены к системе.|[Станции MultiPoint](MultiPoint-services-Stations.md)|  
|5.|Определите необходимое оборудование.|[Выбор оборудования для системы служб MultiPoint](Selecting-Hardware-for-Your-MultiPoint-services-System.md) и [требований к оборудованию и рекомендаций по производительности](hardware-and-performance-recommendations.md)|  
|6.|Определите, где будет располагаться система служб MultiPoint. Будет ли оно настроено в одной комнате или будет настроено таким образом, чтобы его можно было переместить из одного места в другое?|[Планирование сайтов MultiPoint Server](MultiPoint-services-Site-Planning.md)|  
|7.|Определите, как будут упорядочиваться станции.|[Планирование сайта служб MultiPoint](MultiPoint-services-Site-Planning.md)|  
|8.|Проверьте правильность инфраструктуры питания и сети.|[Планирование сайта служб MultiPoint](MultiPoint-services-Site-Planning.md)|  
|9.|Определите, как будут реализовываться и управляться учетными записями пользователей.|[Требования к сети и учетные записи пользователей](Network-Considerations-and-User-Accounts.md)|  
|10.|Определите, как файлы пользователей будут совместно использоваться и храниться.|[Хранение файлов с помощью служб MultiPoint](Storing-Files-with-MultiPoint-services.md)|