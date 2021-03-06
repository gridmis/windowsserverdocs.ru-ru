---
author: shortpatti
ms.author: pashort
ms.date: 10/02/2018
ms.prod: windows-server-threshold
ms:topic: include
ms.openlocfilehash: 4e8e3234b89630bf16148eef644f0c6607ad38bd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852345"
---
## <a name="importance-of-time-protocols"></a>Важность время протоколов
Время протоколы обмена данными между двумя компьютерами для обмена сведения о времени и затем использовать эту информацию, чтобы синхронизировать свои часы. С помощью протокола NTP службы времени Windows клиент запрашивает сведения о времени с сервера и синхронизирует ее часы на основе информации, которая принимается.
  
Служба времени Windows использует NTP для синхронизации времени в сети. NTP является время Интернет-протокол, включает в себя алгоритмов Дисциплина, необходимые для синхронизации часов. NTP является более точные протоколом времени, чем простой сети времени протокол SNTP, используемого в некоторых версиях Windows; Тем не менее W32Time продолжает поддерживать SNTP для обеспечения обратной совместимости с компьютерами под управлением службы времени на основе SNTP, такие как Windows 2000.

Существует много разных причин, что может потребоваться точное время.  Типичный случай для Windows — Kerberos, который требует 5 минут точности между клиентом и сервером.  Тем не менее существует много других областей, могут быть затронуты, включив точность времени:


- Государственные нормы, такие как:
    - точность превышает 50 мс для FINRA в США.
    - ESMA мс (MiFID II), 1 — в ЕС.
- Алгоритмы шифрования
- Распределенные системы, такие как кластера/SQL/Exchange и документа БД
- Блокчейн framework для добывание транзакций
- Распределенных журналов и анализ угроз 
- Репликация Active Directory
- Стандарт PCI (платежных карт), в настоящее время 1 второй точности