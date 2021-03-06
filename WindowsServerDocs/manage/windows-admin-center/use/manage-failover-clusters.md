---
title: Управление отказоустойчивыми кластерами с помощью центра администрирования Windows
description: Управление отказоустойчивыми кластерами с помощью центра администрирования Windows (Project Хонолулу)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: b7f015ac4c9906447069501bf0922b36306a51d7
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950497"
---
# <a name="manage-failover-clusters-with-windows-admin-center"></a>Управление отказоустойчивыми кластерами с помощью центра администрирования Windows

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Скачайте или Узнайте больше о центре администрирования Windows](../overview.md).

## <a name="managing-failover-clusters"></a>Управление отказоустойчивыми кластерами
[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview) — это компонент Windows Server, позволяющий объединять несколько серверов в отказоустойчивый кластер для повышения доступности и масштабируемости приложений и служб, таких как масштабируемый файловый сервер, Hyper-V и Microsoft SQL Server.

Хотя можно управлять узлами отказоустойчивого кластера как отдельными серверами, добавляя их в качестве [подключений к серверу](manage-servers.md) в центре администрирования Windows, их также можно добавить в качестве отказоустойчивых кластеров для просмотра ресурсов кластера, хранилища, сети, узлов, ролей, виртуальных машин и виртуальных коммутаторов и управления ими.

![Экран обзора отказоустойчивого кластера](../media/manage-failover-clusters/fcm-overview.png)

## <a name="adding-a-failover-cluster-to-windows-admin-center"></a>Добавление отказоустойчивого кластера в центр администрирования Windows
Чтобы добавить кластер в центр администрирования Windows, выполните следующие действия.

1. Щелкните **+ Добавить** в разделе все подключения.
2. Выберите Добавление подключения для **отработки отказа**.
3. Введите имя кластера и при появлении запроса укажите учетные данные для использования.
4. Вы сможете добавить узлы кластера в качестве отдельных подключений к серверу в центре администрирования Windows.
5. Нажмите кнопку **Отправить** , чтобы завершить работу.

Кластер будет добавлен в список подключений на странице обзора. Щелкните его, чтобы подключиться к кластеру.

> [!NOTE]
> Можно также управлять кластером с поддержкой Hyper-in, добавив кластер в качестве [подключения к кластеру с технологией Hyper-](manage-hyper-converged.md) in в центре администрирования Windows.

## <a name="tools"></a>Средства

Для подключений к отказоустойчивому кластеру доступны следующие средства.

| Средство | Описание |
| ---- | ----------- |
| Обзор | Просмотр сведений о отказоустойчивом кластере и управление ресурсами кластера |
| Диски | Просмотр общих дисков и томов кластера |
| Сети | Просмотр сетей в кластере |
| Узлы | Просмотр узлов кластера и управление ими |
| Роли | Управление ролями кластера или создание пустой роли |
| Обновления | Управление обновлениями, поддерживающими кластер (требуется [CredSSP](../understand/faq.md#does-windows-admin-center-use-credssp)) |
| [Виртуальные машины](manage-virtual-machines.md) | Просмотр виртуальных машин и управление ими |
| Виртуальные коммутаторы | Просмотр виртуальных коммутаторов и управление ими |

## <a name="more-coming"></a>Ожидается

Управление отказоустойчивыми кластерами в центре администрирования Windows активно разрабатывается, а новые функции будут добавлены в ближайшем будущем. Вы можете просмотреть состояние и проголосовать за функции в UserVoice:

|Запрос функции|
|-------|
| [Отобразить дополнительные сведения о кластеризованном диске](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31740424--cluster-more-disk-info-in-failover-cluster-manag) |
| [Поддержка дополнительных действий кластера](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/33558076--fcm-full-csv-management-cycle-in-one-place) |
| [Поддержка Объединенных кластеров с Hyper-V и масштабируемый файловый сервер в разных кластерах](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31729741--cluster-support-for-converged-architecture) |
| [Просмотреть кэш блоков CSV](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31669477--cluster-csv-block-cache) |
| [Просмотреть все или предложить новую функцию](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5Bcluster%5D) |