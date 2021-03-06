---
title: Windows Admin Center — известные проблемы
description: Windows Admin Center (Project Honolulu) — известные проблемы
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 06/07/2019
ms.openlocfilehash: 4a91d09d6824795a21a9a7cdc7695c407aa70756
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79322926"
---
# <a name="windows-admin-center-known-issues"></a>Windows Admin Center — известные проблемы

> Область применения: центр администрирования Windows, предварительная версия Windows Admin Center

Если возникнет проблема, не описанная на этой странице, [свяжитесь с нами](https://aka.ms/WACfeedback).

## <a name="installer"></a>Установщик

- При установке Windows Admin Center с использованием собственного сертификата следует помнить, что если вы скопируете отпечаток из средства MMC для управления сертификатами, [он будет содержать недопустимый символ в начале.](https://support.microsoft.com/help/2023835/certificate-thumbprint-displayed-in-mmc-certificate-snap-in-has-extra) В качестве решения введите первый символ отпечатка и скопируйте/вставьте остальные символы.

- Использование порта, приведенного ниже 1024, не поддерживается. В режиме обслуживания при необходимости можно настроить порт 80 для перенаправления на указанный порт.

## <a name="general"></a>Общие

- Если центр администрирования Windows установлен в качестве шлюза на **Windows Server 2016** при интенсивном использовании, то служба может аварийно завершить работу из-за ошибки в журнале событий, содержащей ```Faulting application name: sme.exe``` и ```Faulting module name: WsmSvc.dll```. Это вызвано ошибкой, которая была исправлена в Windows Server 2019. Исправление для Windows Server 2016 включало накопительное обновление за Февраль 2019, [KB4480977](https://www.catalog.update.microsoft.com/Search.aspx?q=4480977).

- Если в качестве шлюза установлен центр администрирования Windows, а список подключений поврежден, выполните следующие действия.

   > [!WARNING]
   >Это приведет к удалению списка подключений и параметров для всех пользователей центра администрирования Windows на шлюзе.

  1. Удалите Windows Admin Center
  2. Удалите папку **Интерфейс управления сервером** в разделе **C:\Windows\ServiceProfiles\NetworkService\AppData\Roaming\Microsoft**
  3. Переустановите Windows Admin Center

- Если не закрыть средство и не пользоваться им в течение длительного периода времени, может возникнуть несколько ошибок **Ошибка: недопустимое состояние пространства выполнения этой операции**. В этом случае обновите окно браузера. Если вы столкнетесь с этим, [отправьте нам отзыв](https://aka.ms/WACfeedback).

- Между номерами версий ОС, работающих в модулях Windows Admin Center, может быть незначительная дисперсия, а также информация, которая содержится в указании стороннего программного обеспечения.

### <a name="extension-manager"></a>Диспетчер расширений

- При обновлении центра администрирования Windows необходимо переустановить расширения.
- Если добавить веб-канал расширения, который недоступен, предупреждение не будет. [14412861]

## <a name="browser-specific-issues"></a>Проблемы, связанные с браузером

### <a name="microsoft-edge"></a>Microsoft Edge

- Если вы развернули центр администрирования Windows в качестве службы и используете Microsoft ребро в качестве браузера, подключение шлюза к Azure может завершиться сбоем после создания нового окна браузера. Попробуйте обойти эту ошибку, добавив https://login.microsoftonline.com, https://login.live.comи URL-адрес шлюза в качестве доверенных сайтов и разрешенных сайтов для параметров блокирования всплывающих окон в браузере на стороне клиента. Дополнительные сведения об устранении этой проблемы см. в [руководстве по устранению неполадок](troubleshooting.md#azure-features-dont-work-properly-in-edge). [17990376]

### <a name="google-chrome"></a>Google Chrome

- До версии 70 (выпущена с опозданием октября, 2018) возникла [Ошибка](https://bugs.chromium.org/p/chromium/issues/detail?id=423609) , касающаяся протокола WebSockets и проверки подлинности NTLM. Она влияет на работу следующих средств: "События", PowerShell, "Удаленный рабочий стол".

- Chrome может отобразить несколько запросов на ввод учетных данных, в частности, во время добавления подключения в среде **рабочей группы** (не входящей в домен).

- Если у вас есть центр администрирования Windows, развернутый в качестве службы, для работы функций интеграции с Azure необходимо включить всплывающие окна из URL-адреса шлюза.

### <a name="mozilla-firefox"></a>Mozilla Firefox

Платформа Windows Admin Center не тестировалась с Mozilla Firefox, однако большинство функций должны работать.

- Установка Windows 10: Mozilla Firefox имеет собственное хранилище сертификатов, поэтому необходимо импортировать сертификат ```Windows Admin Center Client``` в Firefox, чтобы использовать центр администрирования Windows в Windows 10.

## <a name="websocket-compatibility-when-using-a-proxy-service"></a>Совместимость WebSocket при использовании прокси-службы

Модули "Удаленный рабочий стол", PowerShell и "События" в Windows Admin Center используют протокол WebSocket, который часто не поддерживается при использовании службы прокси-сервера. Поддержка WebSocket в прокси-сервере приложений Azure AD находится [на этапе тестирования](https://blogs.technet.microsoft.com/applicationproxyblog/2018/03/28/limited-websocket-support-now-in-public-preview/). В настоящий момент осуществляется сбор сведений об их совместимости.

## <a name="support-for-windows-server-versions-before-2016-2012-r2-2012-2008-r2"></a>Поддержка версий Windows Server до 2016 (2012 R2, 2012, 2008 R2)

> [!NOTE]
> Центру администрирования Windows требуются функции PowerShell, которые не включены в Windows Server 2012 R2, 2012 или 2008 R2. Если вы будете управлять Windows Server с помощью центра администрирования Windows, необходимо установить WMF версии 5,1 или выше на этих серверах.

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

## <a name="role-based-access-control-rbac"></a>Управление доступом на основе ролей (RBAC)

- Развертывание RBAC не будет выполнено на компьютерах, которые настроены на использование функции управления приложениями в Защитнике Windows (WDAC, ранее эта функция называлась "Целостность кода".)[16568455]

- Чтобы использовать RBAC в кластере, необходимо развернуть конфигурацию на каждом элементе узла по отдельности.

- При развертывании RBAC могут возникнуть неавторизованные ошибки, которые неправильно связаны с конфигурацией RBAC. [16369238]

## <a name="server-manager-solution"></a>Решение "Диспетчер серверов"

### <a name="certificates"></a>Сертификаты

- Невозможность импорта зашифрованного сертификата PFX в хранилище текущего пользователя. [11818622]

### <a name="events"></a>События

- На события оказывает влияние [совместимость с WebSocket при использовании службы прокси-сервера.](#websocket-compatibility-when-using-a-proxy-service)

- Возможна ошибка, ссылающаяся на "размер пакета" при экспорте больших файлов журнала.

  - Чтобы устранить эту проблему, используйте следующую команду в командной строке с повышенными привилегиями на компьютере шлюза: ```winrm set winrm/config @{MaxEnvelopeSizekb="8192"}```

### <a name="files"></a>Файлы

- Передача и скачивание больших файлов еще не поддерживаются. (ограничение\~100 МБ) [12524234]

### <a name="powershell"></a>PowerShell

- На PowerShell влияет [совместимость с WebSocket при использовании службы прокси-сервера](#websocket-compatibility-when-using-a-proxy-service)

- Вставка с помощью одного щелчка правой кнопкой мыши, как в консоли PowerShell рабочего стола, не работает. Вместо этого откроется контекстное меню браузера, в котором можно выбрать команду "Вставить". Сочетание клавиш CTRL + V также работает.

- Сочетание клавиш CTRL + C для копирования не работает. При его использовании отправляется команда BREAK на консоль. Команда "Копировать" из контекстного меню, вызываемого правой кнопкой мыши, работает.

- При уменьшении окна Windows Admin Center содержимое терминала переформатируется, однако при его обратном увеличении содержимое может не вернуться в прежнее состояние. При перемешивании элементов содержимого можно попробовать выполнить команду Clear-Host или отключиться и повторно подключиться, используя кнопку над терминалом.

### <a name="registry-editor"></a>Редактор реестра

- Возможность поиска не реализована. [13820009]

### <a name="remote-desktop"></a>Удаленный рабочий стол

- При развертывании центра администрирования Windows в качестве службы средство удаленный рабочий стол может не загрузиться после обновления службы центра администрирования Windows до новой версии. Чтобы обойти эту ошибку, очистите кэш браузера.   [23824194]

- При управлении Windows Server 2012 может произойти сбой подключения средства удаленный рабочий стол. [20258278]

- При использовании удаленный рабочий стол для подключения к компьютеру, который не присоединен к домену, необходимо ввести учетную запись в формате ```MACHINENAME\USERNAME```.

- Некоторые конфигурации могут блокировать клиент удаленного рабочего стола центра администрирования Windows с помощью групповой политики. Если вы столкнулись с этим, включите ```Allow users to connect remotely by using Remote Desktop Services``` в разделе ```Computer Configuration/Policies/Administrative Templates/Windows Components/Remote Desktop Services/Remote Desktop Session Host/Connections```

- Удаленный рабочий стол влияет на [Совместимость WebSocket.](#websocket-compatibility-when-using-a-proxy-service)

- Средство "Удаленный рабочий стол" в настоящий момент не поддерживает копирование/вставку любого текста, изображения или файла между локальным рабочим столом и удаленным сеансом.

- Чтобы выполнить операцию копирования/вставки в рамках удаленного сеанса, можно выполнить стандартную операцию копирования (правая кнопка мыши + "Копировать" или сочетание клавиш Ctrl + C), но чтобы вставить скопированный элемент, необходимо щелкнуть правой кнопкой мыши и выбрать "Вставить" (сочетание клавиш Ctrl + V НЕ РАБОТАЕТ).

- Следующие сочетания клавиш нельзя использовать в удаленном сеансе
  - ALT + Tab
  - Функциональные клавиши
  - Клавиша Windows
  - PRINT SCREEN

### <a name="roles-and-features"></a>Роли и компоненты

- При выборе ролей и компонентов с источниками, недоступным для установки, они пропускаются. [12946914]

- Если вы решаете не выполнять автоматическую перезагрузку после установки роли, новый запрос на это действие не отображается. [13098852]

- При выборе автоматической перезагрузки она произойдет до того, как состояние обновится до 100%. [13098852]

### <a name="storage"></a>Хранилище

- Нижний уровень: DVD-диски, компакт-диски или гибкие диски не отображаются в виде тома на нижнем уровне.

- Нижний уровень: некоторые свойства томов и дисков недоступны на нижнем уровне, поэтому они отображаются как неизвестные или пустые в области сведений.

- Нижний уровень: при создании нового тома файловая система ReFS поддерживает только размер кластера в 64 КБ на компьютерах с Windows 2012 и 2012 R2 При создании тома ReFS с меньшим размером кластера на целевых компьютерах нижнего уровня форматирование файловой системы заканчивается сбоем. Использовать новый том будет невозможно. Решение: удалите том и используйте кластер размером 64 КБ.

### <a name="updates"></a>Обновления

- После установки обновлений состояние установки может кэшироваться и требовать обновления браузера.

- При попытке настроить управление обновлениями Azure может возникнуть ошибка: "набор ключей не существует". В этом случае выполните следующие действия по исправлению на управляемом узле —
    1. Останавливает службу служб шифрования.
    2. Измените параметры папки, чтобы отображались скрытые файлы (если это необходимо).
    3. Имеет папку "%Аллусерспрофиле%\микрософт\крипто\рса\с-1-5-18" и удаляет все ее содержимое.
    4. Перезапустите службу служб шифрования.
    5. Повторная настройка Управление обновлениями с помощью центра администрирования Windows

### <a name="virtual-machines"></a>Виртуальные машины

- При управлении виртуальными машинами на узле Windows Server 2012 средство подключения виртуальной машины в браузере не сможет подключиться к виртуальной машине. Загрузка RDP-файла для подключения к виртуальной машине должна продолжать работать. [20258278]

- Azure Site Recovery — если ASR настроен на узле за пределами ВАК, вы не сможете защитить виртуальную машину в ВАК [18972276].

- Дополнительные функции, доступные в диспетчере Hyper-V, такие как "Диспетчер виртуальной SAN", "Перемещение виртуальных машин", "Экспорт виртуальных машин", "Репликация виртуальных машин", в настоящее время не поддерживаются.

### <a name="virtual-switches"></a>Виртуальные коммутаторы

- Объединение внедренных коммутаторов (SET): при добавлении сетевых адаптеров в группу они должны быть в одной подсети.

## <a name="computer-management-solution"></a>Решение "Управление компьютерами"

Решение "Управление компьютерами" содержит набор средств из решения "Диспетчер серверов", поэтому к нему относятся те же известные проблемы, а также следующие конкретные проблемы, характерные только для этого решения.

- Если вы используете учетную запись Майкрософт ([MSA](https://account.microsoft.com/account/)) или используете Azure Active Directory (AAD) для входа на компьютер с Windows 10, необходимо использовать команду "Управление как", чтобы предоставить учетные данные для учетной записи локального администратора [16568455].

- При попытке управления локальным узлом вам будет предложено повысить уровень процесса шлюза. Если в всплывающем окне управления учетными записями пользователей нажать кнопку **нет** , необходимо отменить попытки подключения и начать заново.

- В Windows 10 удаленное взаимодействие WinRM и PowerShell не включено по умолчанию.
  
  - Чтобы включить управление клиентом Windows 10, необходимо выполнить команду ```Enable-PSRemoting``` из командной строки PowerShell с повышенными привилегиями.

  - Также может потребоваться обновить межсетевой экран, чтобы разрешить подключения вне локальной подсети с помощью команды ```Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any```. Инструкции по реализации более жестких ограничительных сценариев см. в [этой документации](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1).

## <a name="failover-cluster-manager-solution"></a>Решение "Диспетчер отказоустойчивости кластеров"

- При управлении кластером (гиперконвергентным или традиционным) может возникнуть ошибка **Оболочка не найдена**. В этом случае перезагрузите браузер либо перейдите к другому инструменту и обратно. [13882442]

- Проблема может возникнуть при управлении кластером нижнего уровня (Windows Server 2012 или 2012 R2), который был настроен неполностью. Чтобы устранить эту проблему, убедитесь, что компонент Windows **RSAT-Clustering-PowerShell** установлен и для кластера задано значение **каждый элемент узла**. Чтобы сделать это с помощью PowerShell, введите команду `Install-WindowsFeature -Name RSAT-Clustering-PowerShell` на всех узлах кластера. [12524664]

- Может потребоваться добавить кластер с полным доменным именем, чтобы его можно было правильно обнаружить.

- При подключении к кластеру с помощью платформы Windows Admin Center, установленной в качестве шлюза, и предоставлении явных имени пользователя/пароля для проверки подлинности необходимо выбрать пункт **Использовать эти учетные данные для всех подключений**, чтобы учетные данные могли опрашивать элементы узлов.

## <a name="hyper-converged-cluster-manager-solution"></a>Решение "Диспетчер гиперконвергентных кластеров"

- Некоторые команды, например **Диски – Обновление встроенного ПО**, **Серверы – Удаление** и **Тома – Открыть** отключены и в настоящее время не поддерживаются.

## <a name="azure-services"></a>Службы Azure

### <a name="azure-file-sync-permissions"></a>Синхронизация файлов Azure разрешения

Для Синхронизация файлов Azure требуются разрешения в Azure, которые не были предоставлены центром администрирования Windows до версии 1910. Если вы зарегистрировали шлюз центра администрирования Windows в Azure с использованием более ранней версии, чем Windows Admin Center версии 1910, необходимо обновить приложение Azure Active Directory, чтобы получить правильные разрешения на использование Синхронизация файлов Azure в последней версии Центр администрирования Windows. Дополнительное разрешение позволяет Синхронизация файлов Azure выполнять автоматическую настройку доступа к учетной записи хранения, как описано в этой статье. [Убедитесь, что у синхронизация файлов Azure есть доступ к учетной записи хранения](https://docs.microsoft.com/azure/storage/files/storage-sync-files-troubleshoot?tabs=portal1%2Cazure-portal#tabpanel_CeZOj-G++Q-5_azure-portal).

Чтобы обновить приложение Azure Active Directory, можно выполнить одно из двух действий.
1. Перейдите в раздел **параметры** > **Azure** > **Отмена регистрации**, а затем снова Зарегистрируйте центр администрирования Windows в Azure, убедившись, что вы решили создать новое приложение Azure Active Directory. 
2. Перейдите в приложение Azure Active Directory и вручную добавьте разрешение, необходимое для существующего Azure Active Directory приложения, зарегистрированного в центре администрирования Windows. Для этого перейдите в раздел **параметры** > представление **Azure** > Azure **в Azure**. В колонке **Регистрация приложения** в Azure перейдите к разделу **разрешения API**и выберите **Добавить разрешение**. Прокрутите вниз, чтобы выбрать **диаграмму Azure Active Directory**, выберите **делегированные разрешения**, разверните **Каталог**и выберите **Directory. акцессасусер. ALL**. Нажмите кнопку **Добавить разрешения** , чтобы сохранить обновления в приложении.

### <a name="options-for-setting-up-azure-management-services"></a>Параметры для настройки служб управления Azure

Службы управления Azure, в том числе Azure Monitor, Управление обновлениями Azure и центр безопасности Azure, используют один и тот же агент для локального сервера: Microsoft Monitoring Agent. Управление обновлениями Azure имеет ограниченный набор поддерживаемых регионов, и для нее требуется связать Log Analytics рабочую область с учетной записью службы автоматизации Azure. Из-за этого ограничения, если вы хотите настроить несколько служб в центре администрирования Windows, сначала необходимо настроить Azure Управление обновлениями, а затем — центр безопасности Azure или Azure Monitor. Если вы настроили какие бы то ни было службы управления Azure, использующие Microsoft Monitoring Agent, а затем пытаетесь настроить Azure Управление обновлениями с помощью центра администрирования Windows, центр администрирования Windows позволит настроить Управление обновлениями Azure только в том случае, если существующие ресурсы, связанные с Microsoft Monitoring Agent, поддерживают Управление обновлениями Azure. Если это не так, вы можете использовать два варианта:

1. Перейдите на панель управления > Microsoft Monitoring Agent, чтобы [Отключить сервер от существующих решений управления Azure](https://docs.microsoft.com/azure/azure-monitor/platform/log-faq#q-how-do-i-stop-an-agent-from-communicating-with-log-analytics) (таких как Azure Monitor или центр безопасности Azure). Затем настройте Управление обновлениями Azure в центре администрирования Windows. После этого можно вернуться к настройке других решений по управлению Azure с помощью центра администрирования Windows без проблем.
2. Вы можете [вручную настроить ресурсы Azure, необходимые для управление обновлениями Azure](https://docs.microsoft.com/azure/automation/automation-update-management) , а затем [вручную обновить Microsoft Monitoring Agent](https://docs.microsoft.com/azure/azure-monitor/platform/agent-manage#adding-or-removing-a-workspace) (за пределами центра администрирования Windows), чтобы добавить новую рабочую область, соответствующую используемому решению Управление обновлениями.
