---
title: Управление пользователями в коллекции служб удаленных рабочих столов
description: Узнайте, как управление пользователями в службах удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2727e1ab-69b8-46f3-9f6d-2540324fe596
author: christianmontoya
ms.author: chrimo
ms.date: 03/27/2018
manager: scottman
ms.openlocfilehash: 4b45061697926a3003712a88610cb17ef3c00c45
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859645"
---
# <a name="manage-users-in-your-rds-collection"></a>Управление пользователями в коллекции служб удаленных рабочих столов

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Как администратор вы сможете напрямую управлять какие пользователи имеют доступ к определенным коллекциям. Таким образом, можно создать одну коллекцию с помощью стандартных приложений для информационных работников, но затем создать отдельную коллекцию с насыщенной графикой моделирования приложений для инженеров. Существует два основных шага, для управления доступом пользователей в развертывании служб удаленных рабочих столов (RDS).

1.  [Создание пользователей и групп в Active Directory](#create-your-users-and-groups-in-active-directory)
2.  [Назначение пользователей и групп в коллекции](#assign-users-and-groups-to-collections)


## <a name="create-your-users-and-groups-in-active-directory"></a>Создание пользователей и групп в Active Directory

В развертывании служб удаленных рабочих СТОЛОВ доменных служб Active Directory (AD DS) является источником всех пользователей, групп и других объектов в домене. Вы можете управлять Active Directory непосредственно с помощью PowerShell, или можно использовать встроенные средства пользовательского интерфейса, которые добавляют обеспечить простоту и гибкость. Следующие шаги укажут, как устанавливать эти средства, если у вас нет их уже установлен и затем использовать эти инструменты для управления пользователями и группами.

### <a name="install-ad-ds-tools"></a>Установить средства AD DS

Ниже приведены инструкции для установки средства AD DS на сервере уже под управлением AD DS. После установки можно создавать пользователей или создание групп.

1. Подключиться к серверу под управлением доменных служб Active Directory. Для развертываний Azure:
   1. На портале Azure щелкните **Обзор > группы ресурсов**, а затем щелкните группу ресурсов для развертывания
   2. Выберите виртуальную машину AD.
   3. Нажмите кнопку **Connect > Открыть** открыт клиент удаленного рабочего стола. Если **Connect** отображается серым цветом, виртуальной машины не может иметь общедоступный IP-адрес. Ему один выполните следующие действия, затем повторите этот шаг.
      1. Нажмите кнопку **параметры > Сетевые интерфейсы**и выберите соответствующий сетевой интерфейс.
      2. Нажмите кнопку **параметры > IP-адрес**.
      3. Для **общедоступный IP-адрес**выберите **включено**, а затем нажмите кнопку **IP-адрес**.
      4. Если у вас есть существующий общедоступный IP-адрес, вы хотите использовать, выберите его из списка. В противном случае нажмите **создать**, введите имя и нажмите кнопку **ОК** и **Сохранить**.
   4. В окне клиента, выберите **Connect**, а затем нажмите кнопку **использовать другую учетную запись**. Введите имя пользователя и пароль для учетной записи администратора домена.
   5. Нажмите кнопку **Да** в ответ на запрос о сертификате.
2. Установите средства AD DS.
   1. В диспетчере серверов выберите **Управление > Добавить роли и компоненты**.
   2. Нажмите кнопку **Установка ролей или компонентов**, а затем щелкните текущий сервер AD. Выполните действия, пока не дойдете до **функции** вкладки.
   3. Разверните **средства удаленного администрирования сервера > средства администрирования ролей > средства AD LDS AD DS и**, а затем выберите **средства AD DS**.
   4. Выберите **автоматический перезапуск конечного сервера, если требуется**, а затем нажмите кнопку **установить**.

### <a name="create-a-group"></a>Создание группы

Группы AD DS можно использовать для предоставления доступа к набору пользователей, которым необходимо использовать те же ресурсы удаленного.

1. В диспетчере серверов на сервере, на котором выполняются AD DS, нажмите кнопку **средства > Active Directory — пользователи и компьютеры**.
2. Разверните домен, на панели слева, чтобы просмотреть ее вложенных папках.
3. Щелкните правой кнопкой мыши папку, где вы хотите создать группу и нажмите кнопку **New > группы**.
4. Введите имя соответствующей группы, а затем выберите **Global** и **безопасности**.

### <a name="create-a-user-and-add-to-a-group"></a>Создайте пользователя и добавить в группу
1. В диспетчере серверов на сервере, на котором выполняются AD DS, нажмите кнопку **средства > Active Directory — пользователи и компьютеры**.
2. Разверните домен, на панели слева, чтобы просмотреть ее вложенных папках.
3. Щелкните правой кнопкой мыши **пользователей**, а затем нажмите кнопку **New > пользователя**.
4. Введите минимальное, имя и имя пользователя.
5. Введите и подтвердите пароль для пользователя. Настраиваемые параметры соответствующего пользователя, как **пользователь должен сменить пароль при следующем входе в систему**.
6. Добавление нового пользователя в группу:
   1. В **пользователей** папку, щелкните правой кнопкой мыши нового пользователя.
   2. Нажмите кнопку **добавить в группу**.
   3. Введите имя группы, к которому вы хотите добавить пользователя.

## <a name="assign-users-and-groups-to-collections"></a>Назначение пользователей и групп в коллекции
Теперь, после создания пользователей и групп в Active Directory, можно добавить некоторые гранулярности относительно кто имеет доступ к удаленному рабочему столу коллекций в развертывании.

1. Соединиться с сервером под управлением роли посредника подключений удаленных рабочих столов (RD Connection Broker), выполнив действия, описанные ранее.
2. Добавьте другие серверы удаленного рабочего стола, пул управляемых серверов посредника подключений к удаленному рабочему Столу:
   1. В диспетчере серверов выберите **Управление > Добавление серверов**.
   2. Щелкните **Find Now**(Найти).
   3. Щелкните каждый сервер развертывания, на котором выполняется роль служб удаленных рабочих столов и нажмите кнопку **ОК**.
3. Изменение коллекции для предоставления доступа к конкретным пользователям или группам:
   1. В диспетчере серверов выберите **служб удаленных рабочих столов > Обзор**, а затем нажмите кнопку определенной коллекции.
   2. В разделе **свойства**, нажмите кнопку **задачи > изменить свойства**.
   3. Нажмите кнопку **групп пользователей**.
   4. Нажмите кнопку **добавить** и введите пользователя или группы, вы должны иметь доступ к коллекции. Можно также удалить пользователей и групп из этого окна, выберите пользователя или группы, которые требуется удалить и нажмите кнопку **удалить**. 
   
   >[!NOTE] 
   > Окно группы пользователя никогда не может быть пустым. Чтобы ограничить круг пользователей, имеющих доступ к коллекции, необходимо сначала добавить конкретным пользователям или группам перед удалением более широких групп.