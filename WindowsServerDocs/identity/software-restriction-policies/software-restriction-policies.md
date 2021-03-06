---
title: Политики ограниченного использования программ
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: security-software-restriction-policies
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c0befad-07c3-4262-b418-372d01850305
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: b06d038e919e2f4904d60b88ad223493c4f818eb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357675"
---
# <a name="software-restriction-policies"></a>Политики ограниченного использования программ

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этой статье для ИТ-специалистов описываются политики ограниченного использования программ (SRP) в Windows Server 2012 и Windows 8, а также приведены ссылки на технические сведения о наборе исправлений безопасности, начиная с Windows Server 2003.

Процедуры и советы по устранению неполадок см. в разделе [Администрирование политик ограниченного использования программ](administer-software-restriction-policies.md) и [Устранение неполадок политик ограниченного использования программ](troubleshoot-software-restriction-policies.md).

## <a name="BKMK_OVER"></a>Описание политик ограниченного использования программ
Политики ограниченного использования программ — это основанная на групповых политиках функция, которая выявляет программы, работающие на компьютерах в домене, и управляет возможностью выполнения этих программ. Политики ограниченного использования программ являются частью стратегии управления и безопасности Майкрософт, позволяющей предприятиям повышать надежность, целостность и управляемость их компьютеров.

Кроме того, данные политики помогают создать конфигурацию с расширенными ограничениями для компьютеров, на которых разрешается запуск только определенных приложений. Политики ограниченного использования программ интегрируются со службой Microsoft Active Directory и групповой политикой. Политики можно создавать на изолированных компьютерах. Они являются политиками доверия, то есть представляют собой правила, устанавливаемые администратором, чтобы ограничить выполнение сценариев и другого кода, не имеющего полного доверия.

Данные политики ограничения использования программ определяются как расширение редактора локальных групповых политик или оснастки Microsoft Management Console (MMC) "Локальные политики безопасности".

Подробные сведения о политиках ограниченного использования программ см. в разделе [Software Restriction Policies Technical Overview](software-restriction-policies-technical-overview.md).

## <a name="BKMK_APP"></a>Практические приложения
Администраторы могут использовать политики ограничения использования программ для решения следующих задач:

-   определить доверенный код;

-   разработать гибкую групповую политику для регулирования работы сценариев, исполняемых файлов и элементов ActiveX.

Политики ограниченного использования программ применяются операционной системой и приложениями (например, для создания сценариев), которые им соответствуют.

В частности, администраторы могут использовать политики ограниченного использования программ в следующих целях:

-   определить программное обеспечение (исполняемые файлы), которое может выполняться на клиентах;

-   запретить пользователям выполнять определенные программы на компьютерах с общим доступом;

-   определить, кто может добавлять доверенных издателей на клиентах;

-   установить область действия политик ограничения использования программ (указать, будут ли политики применяться для всех пользователей или только для группы пользователей на клиентах);

-   запретить работу исполняемых файлов на локальном компьютере, сайте, в подразделении или домене. Это уместно в тех случаях, когда политики ограниченного использования программ не применяются для решения потенциальных проблем со злоумышленниками.

## <a name="BKMK_NEW"></a>Новые и измененные функции
Функциональные изменения в политиках ограниченного использования программ отсутствуют.

## <a name="BKMK_DEP"></a>Удаленная или устаревшая функциональность
Удаленные или устаревшие функции в политиках ограниченного использования программ отсутствуют.

## <a name="BKMK_SOFT"></a>Требования к программному обеспечению
Расширение редактора локальных групповых политик для политик ограниченного использования программ доступно через консоль управления (MMC).

Для создания и поддержки политик ограничения использования программ на локальном компьютере требуются следующие компоненты:

-   Редактор локальных групповых политик

-   Установщик Windows

-   Authenticode и WinVerifyTrust

Если планируются вызовы для развертывания этих политик в домене, к вышеупомянутому списку потребуется добавить следующие компоненты:

-   Доменные службы Active Directory

-   Групповая политика

## <a name="BKMK_INSTALL"></a>Сведения о диспетчер сервера
Политики ограниченного использования программ представляют собой расширение редактора локальных групповых политик и не устанавливаются с помощью пункта "Добавить роли и компоненты" диспетчера серверов.

## <a name="BKMK_LINKS"></a>См. также
В следующей таблице содержатся ссылки на соответствующие ресурсы, необходимые для понимания и применения политик ограниченного использования программ.

|Тип содержимого|Ссылок|
|--------|-------|
|**Оценка продукта**|[Блокировка приложений с помощью политик ограниченного использования программ](https://technet.microsoft.com/magazine/2008.06.srp.aspx?pr=blog)|
|**Планирование**|[Технический обзор политик ограниченного использования программ](software-restriction-policies-technical-overview.md) (Windows Server 2012)<br /><br />[Технический справочник по политикам ограниченного использования программ](https://technet.microsoft.com/library/cc728085(v=WS.10).aspx) (Windows Server 2003)|
|**Развертывание**|Доступные ресурсы отсутствуют.|
|**Операции**|[Администрирование политик ограниченного использования программ](administer-software-restriction-policies.md) (Windows Server 2012)<br /><br />[Справка по политикам ограниченного использования программ](https://technet.microsoft.com/library/cc779607(v=WS.10).aspx) (Windows Server 2003)|
|**Устранение неполадок**|[Устранение неполадок политик ограниченного использования программ](troubleshoot-software-restriction-policies.md) (Windows Server 2012)<br /><br />[Диагностика политик ограниченного использования программ](https://technet.microsoft.com/library/cc737011(v=WS.10).aspx) (Windows Server 2003)|
|**безопасность**|[Угрозы и противодействия для политик ограниченного использования программ](https://technet.microsoft.com/library/dd349795(v=WS.10).aspx) (Windows Server 2008)<br /><br />[Угрозы и противодействия для политик ограниченного использования программ](https://technet.microsoft.com/library/hh125926(v=WS.10).aspx) (Windows Server 2008 R2)|
|**Средства и параметры**|[Средства и параметры политик ограниченного использования программ](https://technet.microsoft.com/library/cc782454(v=WS.10).aspx) (Windows Server 2003)|
|**Ресурсы сообщества**|[Блокировка приложений с помощью политик ограниченного использования программ](https://technet.microsoft.com/magazine/2008.06.srp.aspx?pr=blog)|



