---
title: Управление Windows Server
description: Сведения о средствах, рекомендациях, а также инструкции по управлению Windows Server
ms.prod: windows-server
ms.technology: manage
ms.topic: article
author: lizap
ms.author: elizapo
ms.date: 03/16/2018
ms.localizationpriority: medium
ms.openlocfilehash: 880f8da5bfb872fba6fe4886198d932c91f4bf86
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370475"
---
# <a name="manage-windows-server"></a>Управление Windows Server

>Относится к: Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с другими нашими [библиотеками Windows Server](/previous-versions/windows/) на сайте docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

 <ul class="cardse panelContent cols cols3">
    <li>
        <a href="https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-feedback-hub">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img src="../media/i-manage.svg" alt="" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h2>Управление</h2>
                <p>После развертывания Windows Server в вашей среде, в том числе ролей для необходимых компонентов и функций, следующий шаг — управление этими серверами. Windows Server предоставляет несколько средств, которые помогут вам ознакомиться со средой Windows Server, методами управления определенными серверами, точной настройки производительности и автоматизации выполнения многих задач управления. </p>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li> 
</ul> 

## <a name="manage-windows-server-systems-and-environments"></a>Управление системами и средами Windows Server
Инструменты, используемые для управления экземплярами Windows Server, во многом зависят от типов развернутых систем (Windows Server с возможностями рабочего стола или основные серверные компоненты), типа компьютеров (физические или виртуальные) и расположения серверов. Воспользуйтесь следующими сведениями о выполнении базовых задач управления Windows Server.

Используйте следующую таблицу, чтобы определить, какие средства применять.

| Я   | Установка и запуск Windows Admin Center | Запуск диспетчера серверов в Windows Server | Запуск диспетчера серверов в RSAT в Windows 10 |
|--------|----------------------|--------------------------------------|------------------------------------------|
| использую ПК с Windows 10 | X  |                                      | X                                        |
| использую систему Windows Server с возможностями рабочего стола | X | X | X |
| использую систему Windows Server с основными серверными компонентами |X (установка в Windows 10, используется для управления основными серверными компонентами) | | X |
| нахожусь далеко от системы Windows Server |X | | X |
| нахожусь далеко от системы Windows Server, но мне доступны возможности рабочего стола |X | Используйте RDS для удаленного доступа к серверу, а затем используйте диспетчер серверов | X |

В дополнение к средствам, описанным ниже, вы также можете использовать [службы удаленных рабочих столов](../remote/remote-desktop-services/welcome-to-rds.md) для доступа к локальным, удаленным и виртуальным серверам. Затем вы можете использовать диспетчер серверов для выполнения задач управления.

### <a name="manage-on-premises-systems-remote-systems-and-systems-without-ui-with-windows-admin-center"></a>Управление локальными системами, удаленными системами и системами без пользовательского интерфейса с помощью Windows Admin Center
[Windows Admin Center](../manage/windows-admin-center/overview.md) — это браузерное приложение для управления системами с Windows Server независимо от Azure или облака в локальной среде. Windows Admin Center предоставляет полный контроль над всеми аспектами серверной инфраструктуры и особенно полезен для управления серверами в частных сетях, которые не подключены к Интернету. Windows Admin Center можно установить в Windows 10, на сервере шлюза или непосредственно в системе Windows Server, которой вы управляете.

>[!NOTE]
>Windows Admin Center — это официальное название для продукта, который раньше назывался "Project Honolulu".

### <a name="manage-on-premises-systems-with-server-manager"></a>Управление локальными системами с помощью диспетчера серверов
[Диспетчер серверов](server-manager/server-manager.md) — это консоль управления, включенная в полную установку Windows Server. (Она недоступна для установок, которые не имеют пользовательского интерфейса — основные компоненты сервера не включают диспетчер серверов.) С помощью диспетчера серверов вы можете устанавливать и удалять роли серверов, добавлять и отключать удаленные серверы, запускать и останавливать службы, а также просматривать собранные данные о среде.

### <a name="manage-remote-systems-and-systems-without-ui-with-remote-server-administration-tools-rsat"></a>Управление удаленными системами и системами без пользовательского интерфейса с помощью средств администрирования удаленного сервера (RSAT)
Если в среде есть установки основных серверных компонентов или удаленные серверы (локальные или виртуальные машины), для управления этими системами можно использовать [средства удаленного администрирования сервера (RSAT)](../remote/remote-server-administration-tools.md). В RSAT включен диспетчер серверов, поэтому вы сможете использовать его для управления всеми серверами.

> [!IMPORTANT]
> Средства RSAT работают в Windows 10. Средства RSAT невозможно установить в Windows Server Core.

Вы также можете управлять установками основных серверных компонентов из командной строки. См. раздел [Основные административные задачи в Server Core](server-core/server-core-administer.md).

### <a name="manage-updates-to-windows-server-systems"></a>Управление системами Windows Server
Вы можете использовать [сервер Windows Server Update Services (WSUS)](windows-server-update-services/get-started/windows-server-update-services-wsus.md) для развертывания обновлений в системах в среде Windows Server и управления ими.

## <a name="gather-information-about-your-environment"></a>Сбор сведений о среде
Многие решения, которые вы принимаете в качестве администратора, зависят от данных о системах и пользователях в вашей среде. Используйте следующие сведения и средства для сбора этих данных.

В разделе [Настройка диагностических данных Windows в организации](/windows/configuration/configure-windows-diagnostic-data-in-your-organization) представлены сведения о диагностических данных, которые можно собирать в Windows 10 и Windows Server.

### <a name="setup-and-boot-event-collectionget-started-with-setup-and-boot-event-collectionmd"></a>[Сбор событий установки и загрузки](get-started-with-setup-and-boot-event-collection.md)
Функция сбора событий установки и загрузки позволяет назначить "компьютер-сборщик", который может собирать различные важные события, возникающие на других компьютерах в ходе загрузке или установки. Затем вы можете проанализировать собранные события с помощью компонента "Просмотр событий", анализатора сообщений, Wevtutil или командлетов Windows PowerShell. 

### <a name="software-inventory-logging-silsoftware-inventory-loggingget-started-with-software-inventory-loggingmd"></a>[Инвентаризация программного обеспечения (SIL)](software-inventory-logging/get-started-with-software-inventory-logging.md)

Журнал инвентаризации программного обеспечения в Windows Server — это компонент с простым набором командлетов PowerShell, который помогает администраторам получить список программ Майкрософт, установленных на их серверах. Он также предоставляет возможность периодически собирать и перенаправлять эти данные по сети с помощью протокола HTTPS для статистической обработки. Управление этим компонентом, главным образом для ежечасного сбора и перенаправления, также выполняется с помощью команд PowerShell.

### <a name="user-access-logging-ualuser-access-loggingget-started-with-user-access-loggingmd"></a>[Ведение журнала доступа пользователей](user-access-logging/get-started-with-user-access-logging.md)

Компонент ведения журнала доступа пользователей объединяет уникальные события клиентских устройств и запросов пользователей, которые регистрируются на компьютере с Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012 в локальной базе данных. Доступ к этим записям (с помощью запроса администратора сервера) позволяет получать сведения о количестве и экземплярах по роли сервера, пользователю, устройству, локальному серверу и дате. Кроме того, служба UAL предоставляет сторонним разработчикам программного обеспечения возможности реализовать в коде события UAL, которые должны собираться. 

## <a name="tune-your-windows-server-environment-for-performance"></a>Настройка среды Windows Server для обеспечения высокой производительности
Используйте следующие сведения, чтобы оптимизировать производительность среды.

### <a name="performance-tuning-guidelinesperformance-tuningindexmd"></a>[Руководство по обеспечению высокой производительности](performance-tuning/index.md)
Изучите набор рекомендаций, которые можно использовать для настройки параметров сервера в Windows Server 2016 и повышения производительности или экономии электроэнергии, особенно учитывая изменение характера рабочих нагрузки со временем.

### <a name="microsoft-server-performance-advisorserver-performance-advisormicrosoft-server-performance-advisormd"></a>[Microsoft Server Performance Advisor](server-performance-advisor/microsoft-server-performance-advisor.md)

С помощью Microsoft Server Performance Advisor (SPA) вы можете в фоновом режиме собирать показатели для диагностики проблем с производительностью на серверах Windows без добавления программных агентов или перенастройки производственных серверов. SPA создает подробные отчеты о производительности и ретроспективные диаграммы с рекомендациями.


## <a name="automate-windows-server-management"></a>Автоматизация управления Windows Server

Windows Server предоставляет набор команд и модулей Windows PowerShell, которые можно использовать для автоматизации задач управления.

### <a name="windows-powershellpowershellscriptingpowershell-scriptingviewpowershell-51"></a>[Windows PowerShell](/powershell/scripting/powershell-scripting?view=powershell-5.1)
Windows PowerShell — это оболочка командной строки и язык сценариев, созданный для быстрой автоматизации задач администрирования. 

### <a name="windows-commandswindows-commandswindows-commandsmd"></a>[Команды Windows](windows-commands/windows-commands.md)

Средства командной строки Windows используются для выполнения административных задач в Windows. Вы можете воспользоваться справочником по командам, чтобы ознакомиться со средствами командной строки, командной оболочкой и методами автоматизации задач командной строки с помощью пакетных файлов или средств написания сценариев.

## <a name="windows-server-insider-preview"></a>Сборка из программы предварительной оценки Windows Server
### <a name="system-insightsmanagesystem-insightsoverviewmd"></a>[Системная аналитика](../manage/system-insights/overview.md)
Системная аналитика — это новая возможность, которая представляет средства прогнозной аналитики, и изначально входит в состав Windows Server. Эти возможности прогнозирования локально анализируют системные данные Windows Server, такие как счетчики производительности или события трассировки событий Windows, помогая ИТ-администраторам упреждающим образом выявлять и устранять проблемы в их развертываниях. 
