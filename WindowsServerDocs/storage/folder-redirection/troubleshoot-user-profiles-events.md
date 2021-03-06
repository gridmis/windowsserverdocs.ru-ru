---
title: Устранение проблем с профилями пользователей с помощью событий
description: Устранение проблем с загрузкой и выгрузкой профилей пользователей с использованием журналов событий и трассировки.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 04/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 9e927a77627e786015a928d798aafee13a2cc34b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394380"
---
# <a name="troubleshoot-user-profiles-with-events"></a>Устранение проблем с профилями пользователей с помощью событий

>Применяется к: Windows 10, Windows 8, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 и Windows Server (Semi-annual Channel).

В этой статье рассматривается устранение проблем с загрузкой и выгрузкой профилей пользователей с использованием журналов событий и трассировки. В следующих разделах описано, как использовать три журнала событий, в которые записываются сведения о профиле пользователя.

## <a name="step-1-checking-events-in-the-application-log"></a>Шаг 1. Проверка событий в журнале приложений

Первый шаг в устранении проблем, связанных с загрузкой и выгрузкой профилей пользователей (в том числе перемещаемых профилей пользователей), заключается в использовании компонента "Просмотр событий" для проверки всех событий предупреждений и ошибок, которые записываются службой профилей пользователей в журнал приложений.

Вот как можно просмотреть события служб профилей пользователей в журнале приложений.

1. Запустите компонент "Просмотр событий". Для этого откройте **Панель управления**, выберите раздел **Система и безопасность**, а затем в разделе **Администрирование** щелкните ссылку **Просмотр журналов событий**. Откроется окно компонента "Просмотр событий".
2. В дереве консоли сначала перейдите к узлу **Журналы Windows**, а затем выберите ветку **Приложение**.
3. В области действий выберите действие **Фильтровать текущий журнал**. Откроется диалоговое окно "Фильтровать текущий журнал".
4. В поле **Источники событий** установите флажок **User Profiles Service** (Служба профилей пользователей), а затем нажмите кнопку **ОК**.
5. Ознакомьтесь с перечнем событий, обращая особое внимание на события ошибок.
6. При обнаружении значимых событий выберите ссылку "Справка в Интернете для журнала событий", чтобы просмотреть дополнительные сведения и узнать о процедурах устранения проблем.
7. Прежде чем выполнить дальнейшие действия по устранению проблем, обратите внимание на дату и время значимых событий, а затем изучите операционный журнал (как описано в шаге 2), чтобы узнать сведения о том, что делала служба профилей пользователей во время происшествия событий ошибок или предупреждений.

>[!NOTE]
>Можно спокойно проигнорировать событие службы профилей пользователей 1530 "Windows detected your registry file is still in use by other applications or services." (Система Windows обнаружила, что файл реестра все еще используют другие приложения или службы).

## <a name="step-2-view-the-operational-log-for-the-user-profile-service"></a>Шаг 2. Просмотр операционного журнала для службы профилей пользователей

Если проблему нельзя устранить только с помощью журнала приложений, используйте следующую процедуру для просмотра событий службы профилей пользователей в операционном журнале. В этом журнале отображаются некоторые внутренние действия службы, по которых могут помочь точно определить, где в процессе загрузки или выгрузки профиля возникает проблема.

Журнал приложений и операционный журнал службы профилей пользователей Windows включены по умолчанию во всех установках Windows.

Вот как просмотреть операционный журнал для службы профилей пользователей:

1. В дереве консоли "Просмотр событий" перейдите к разделу **Журналы приложений и служб**, затем выберите **Microsoft**, **Windows**, **Служба профилей пользователей**, **Операционный**.
2. Изучите события, произошедшие во время происшествия событий ошибок или предупреждений, записанных в журнале приложений.

## <a name="step-3-enable-and-view-analytic-and-debug-logs"></a>Шаг 3. Включение и просмотр журналов аналитики и отладки

Если требуется больше сведений, чем в операционном журнале, можно включить журналы аналитики и отладки на затронутом компьютере. Эти журналы предоставляют более подробные сведения. Они должны быть отключены, за исключением случаев, когда вы пытаетесь устранить проблему.

Вот как включить и просмотреть журналы аналитики и отладки:

1. В компоненте "Просмотр событий" в области **Действия** выберите **Вид**, а затем выберите **Отобразить аналитический и отладочный журналы**.
2. Перейдите к узлу **Журналы приложений и служб**, затем выберите **Microsoft**, **Windows**, **Служба профилей пользователей**, **Диагностика**.
3. Щелкните **Включить журнал**, а затем нажмите кнопку **Да**. Это включит журнал диагностики, который начнет запись.
4. Если требуется более подробная информация, см. [Шаг 4. Создание и декодирование трассировки](#step-4-creating-and-decoding-a-trace) для получения дополнительных сведений о создании журнала трассировки.
5. Завершив устранение проблемы, перейдите к журналу **Диагностика**, щелкните **Отключить журнал**, выберите **Вид**, а затем снимите флажок **Отобразить аналитический и отладочный журналы**, чтобы отменить ведение журнала аналитики и отладки.

## <a name="step-4-creating-and-decoding-a-trace"></a>Шаг 4. Создание и декодирование трассировки

Если не удается устранить проблему с помощью событий, можно создать журнал трассировки (ETL-файл) при воспроизведении проблемы, а затем декодировать его с помощью общедоступных символов с сервера символов (Майкрософт). Журналы трассировки предоставляют конкретные сведения о том, что делает служба профилей пользователей, и могут помочь выявить место возникновения сбоя.

Оптимальная стратегия использования трассировки ETL — сначала записывать наименьшие возможные журналы. После декодирования журнала выполните поиск ошибок в нем.

Вот как создать и декодировать трассировку для службы профилей пользователей:

1. Войдите на компьютер, на котором пользователь столкнулся с проблемами, используя учетную запись члена локальной группы администраторов.
2. В командной строке с повышенными привилегиями введите следующие команды, где *\<Путь\>*  — это путь к локальной папке, созданной ранее, например, C:\\logs:
        
    ```PowerShell
    logman create trace -n RUP -o <Path>\RUP.etl -ets
    logman update RUP -p {eb7428f5-ab1f-4322-a4cc-1f1a9b2c5e98} 0x7FFFFFFF 0x7 -ets
    ```
3. На начальном экране выберите имя пользователя, а затем выберите команду **Переключить учетную запись**, будьте внимательны и не выходите из учетной записи администратора. Если вы используете удаленный рабочий стол, закройте сеанс администратора, чтобы установить сеанс пользователя.
4. Воспроизведите проблему. Эта процедура обычно заключается в том, чтобы войти в систему в качестве пользователя, испытывающего проблему, выйти из системы, или и то, и другое.
5. После воссоздания проблемы войдите в систему опять с правами локального администратора.
6. В командной строке с повышенными привилегиями выполните следующую команду, чтобы сохранить журнал в ETL-файле:
  
    ```PowerShell
    logman stop -n RUP -ets
    ```
7. Введите следующую команду, чтобы экспортировать ETL-файл в файл, доступный для чтения, в текущем каталоге (возможно, в домашней папке или папке %WINDIR%\\System32):
    
    ```PowerShell
    Tracerpt <path>\RUP.etl
    ```
8. Откройте файл **Summary.txt** и файл **Dumpfile.xml** (их можно открыть в Microsoft Excel, чтобы упростить просмотр подробных сведений журнала). Найдите события, которые включают **отказ** или **сбой**. Можно спокойно пропускать строки, содержащие имя события **Unknown** (Неизвестно).

## <a name="more-information"></a>Дополнительные сведения

* [Развертывание перемещаемых профилей пользователя](deploy-roaming-user-profiles.md)