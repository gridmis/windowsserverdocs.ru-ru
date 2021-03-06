---
title: Расширения публикации для центра администрирования Windows
description: Расширения публикации для центра администрирования Windows (проект Хонолулу)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 0182c4097ec3bc4432e2ba408d701a72d82a7c8d
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950085"
---
# <a name="publishing-extensions"></a>Публикация расширений

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

После разработки расширения необходимо опубликовать его и сделать доступным для тестирования или использования другими пользователями. В зависимости от аудитории и целей публикации существует несколько вариантов, которые будут представлены ниже вместе с действиями и требованиями для публикации.

## <a name="publishing-options"></a>Параметры публикации

Существует три основных варианта для настраиваемых источников пакетов, поддерживаемых центром администрирования Windows.
* Общедоступный веб-канал NuGet центра администрирования Windows для Microsoft
* Собственный частный веб-канал NuGet
* Локальный или сетевой файловый ресурс

### <a name="publishing-to-the-windows-admin-center-extension-feed"></a>Публикация в веб-канале расширения центра администрирования Windows

По умолчанию центр администрирования Windows подключен к веб-каналу NuGet, поддерживаемому группой разработчиков центра администрирования Windows корпорации Майкрософт. Предварительные версии новых расширений, разработанных корпорацией Майкрософт, могут быть опубликованы в этом веб-канале и доступны пользователям центра администрирования Windows. Разработчики, планирующие создание и выпуск расширений для внешних разработчиков, могут также [Отправить запрос](#publishing-your-extension-to-the-windows-admin-center-feed) на публикацию в этом веб-канале.

### <a name="publishing-to-a-different-nuget-feed"></a>Публикация в другом веб-канале NuGet

Вы также можете создать собственный веб-канал NuGet для публикации расширений, используя один из множества [различных вариантов настройки частного источника или службы размещения NuGet](https://docs.microsoft.com/nuget/hosting-packages/overview). Канал NuGet должен поддерживать API-интерфейс NuGet v2. Так как центр администрирования Windows в настоящее время не поддерживает проверку подлинности веб-канала, веб-канал должен быть настроен так, чтобы иметь доступ на чтение для всех пользователей.

### <a name="publishing-to-a-file-share"></a>Публикация в общую папку

Чтобы ограничить доступ вашего расширения к Организации или группе людей с ограниченными правами, можно использовать файловый ресурс SMB в качестве веб-канала расширения. В этом случае разрешения общей папки и папок будут применяться для предоставления доступа к веб-каналу.

## <a name="preparing-your-extension-for-release"></a>Подготовка расширения к выпуску

Убедитесь, что прочитали и рассмотрите следующие темы по разработке:

- [Управление отображением вашего инструмента](guides/dynamic-tool-display.md)
- [Строки и локализация](guides/strings-localization.md)

### <a name="consider-releasing-as-a-preview-release"></a>Рассмотрите возможность выпуска в качестве предварительной версии

Если вы выпустили предварительную версию расширения для целей оценки, рекомендуется выполнить следующие действия.

- Добавьте "(Предварительная версия)" в конец заголовка расширения в nuspec-файле.
- Объясните ограничения в описании расширения в файле nuspec

## <a name="creating-an-extension-package"></a>Создание пакета расширения

Центр администрирования Windows использует пакеты NuGet и каналы для распространения и скачивания расширений.  Для отправки пакета необходимо создать пакет NuGet, содержащий подключаемые модули и расширения.  Один пакет может содержать как расширение пользовательского интерфейса, так и подключаемый модуль шлюза, и в следующем разделе будет рассмотрен процесс.

### <a name="1-build-your-extension"></a>1. Создание расширения

Как только вы будете готовы начать упаковку расширения, создайте новый каталог в файловой системе, откройте консоль и перейдете в нее компакт-диск.  Это будет корневой каталог, который будет использоваться для хранения всех каталогов nuspec и содержимого, которые будут представлять наш пакет.  Мы будем ссылаться на эту папку как на "пакет NuGet" в течение этого документа.

#### <a name="ui-extensions"></a>Расширения пользовательского интерфейса

Чтобы начать процесс сбора всего содержимого, необходимого для расширения пользовательского интерфейса, выполните в средстве "gulp Build" и убедитесь, что сборка выполнена успешно.  Этот процесс упаковывает все компоненты вместе в папку с именем "пакет", расположенную в корневом каталоге расширения (на том же уровне каталога src).  Скопируйте этот каталог и все его содержимое в папку "пакет NuGet".

#### <a name="gateway-plugins"></a>Подключаемые модули шлюза

С помощью инфраструктуры сборки (это может быть так же просто, как открытие Visual Studio и нажатие кнопки "построить"), скомпилируйте и создайте подключаемый модуль.  Откройте выходной каталог сборки и скопируйте библиотеки DLL, представляющие подключаемый модуль, и вставьте их в новую папку в каталоге "пакет NuGet" с именем "Package".  Вам не нужно копировать библиотеку DLL Феатуреинтерфаце, а только библиотеки DLL, представляющие код.

### <a name="2-create-the-nuspec-file"></a>2. Создание файла nuspec

Чтобы создать пакет NuGet, сначала необходимо создать nuspec-файл. Файл. nuspec — это XML-манифест, содержащий метаданные пакета NuGet. Этот манифест используется при построении пакета и содержит дополнительные сведения для его потребителей.  Поместите этот файл в корень папки "пакет NuGet".

Ниже приведен пример файла. nuspec и список обязательных или рекомендуемых свойств. Полную схему см. в [справочнике по nuspec](https://docs.microsoft.com/nuget/reference/nuspec). Сохраните nuspec-файл в корневую папку проекта с именем выбранного файла.

> [!IMPORTANT]
> Значение ```<id>``` в файле nuspec должно совпадать со значением ```"name"``` в ```manifest.json``` файле проекта, иначе опубликованное расширение не будет успешно загружено в центре администрирования Windows.

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="https://schemas.microsoft.com/packaging/2011/08/nuspec.xsd">
  <metadata>
    <packageTypes>
      <packageType name="WindowsAdminCenterExtension" />
    </packageTypes>  
    <id>contoso.project.extension</id>
    <version>1.0.0</version>
    <title>Contoso Hello Extension</title>
    <authors>Contoso</authors>
    <owners>Contoso</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <projectUrl>https://msft-sme.myget.org/feed/windows-admin-center-feed/package/nuget/contoso.sme.hello-extension</projectUrl>
    <licenseUrl>http://YourLicenseLink</licenseUrl>
    <iconUrl>http://YourLogoLink</iconUrl>
    <description>Hello World extension by Contoso</description>
    <copyright>(c) Contoso. All rights reserved.</copyright> 
    <tags></tags>
  </metadata>
  <files>
    <file src="bundle\**\*.*" target="ux" />
    <file src="package\**\*.*" target="gateway" />
  </files>
</package>
```

#### <a name="required-or-recommended-properties"></a>Обязательные или Рекомендуемые свойства

| Имя свойства | Обязательно/рекомендуется | Описание |
| ---- | ---- | ---- |
| packageType | Обязательный | Используйте "Виндовсадминцентерекстенсион", который является типом пакета NuGet, определенным для расширений центра администрирования Windows. |
| id | Обязательный | Уникальный идентификатор пакета в веб-канале. Это значение должно соответствовать значению "Name" в файле manifest. JSON вашего проекта.  Инструкции см. в разделе [Выбор уникального идентификатора пакета](https://docs.microsoft.com/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number). |
| title | Требуется для публикации в веб-канале центра администрирования Windows | Понятное имя пакета, отображаемое в диспетчере расширений центра администрирования Windows. |
| Версия | Обязательный | Версия расширения. Рекомендуется использовать [семантическое управление версиями (соглашение SemVer)](http://semver.org/spec/v1.0.0.html) , но не является обязательным. |
| authors | Обязательный | При публикации от имени компании используйте название вашей компании. |
| Описание | Обязательный | Введите описание функциональных возможностей расширения. |
| iconUrl | Рекомендуется при публикации в веб-канале центра администрирования Windows | URL-адрес для значка, отображаемого в диспетчере расширений. |
| projectUrl | Требуется для публикации в веб-канале центра администрирования Windows | URL-адрес веб-сайта расширения. Если у вас нет отдельного веб-сайта, используйте URL-адрес веб-страницы пакета в канале NuGet. |
| licenseUrl | Требуется для публикации в веб-канале центра администрирования Windows | URL-адрес лицензионного соглашения для вашего расширения. |
| файлы | Обязательный | Эти два параметра задают структуру папок, которую Центр администрирования Windows ожидает для расширений пользовательского интерфейса и подключаемых модулей шлюза. |

### <a name="3-build-the-extension-nuget-package"></a>3. Создание пакета NuGet для расширения

Используя созданный ранее файл. nuspec, вы создадите файл NuGet Package. nupkg, который можно передать и опубликовать в веб-канале NuGet.

1. Скачайте средство NuGet. exe CLI с [веб-сайта средств клиента NuGet](https://docs.microsoft.com/nuget/install-nuget-client-tools).
2. Выполните команду "NuGet. exe Pack [. nuspec File name]", чтобы создать файл nupkg.

### <a name="4-signing-your-extension-nuget-package"></a>4. Подписывание пакета NuGet для расширения

Все DLL-файлы, входящие в расширение, должны быть подписаны сертификатом из доверенного центра сертификации (ЦС). По умолчанию неподписанные DLL-файлы будут заблокированы, когда центр администрирования Windows работает в рабочем режиме.

Также настоятельно рекомендуется подписать пакет NuGet для расширения, чтобы обеспечить целостность пакета, но это не обязательное действие.

### <a name="5-test-your-extension-nuget-package"></a>5. Тестирование пакета NuGet для расширения

Теперь пакет расширения готов к тестированию. Отправьте файл. nupkg в веб-канал NuGet или скопируйте его в общую папку. Чтобы просмотреть и скачать пакеты из другого канала или общей папки, необходимо [изменить конфигурацию веб-канала](../configure/using-extensions.md#installing-extensions-from-a-different-feed) , чтобы она указывала на ваш канал NuGet или общую папку. При тестировании убедитесь, что свойства правильно отображаются в диспетчере расширений, и вы можете успешно установить и удалить расширение.

## <a name="publishing-your-extension-to-the-windows-admin-center-feed"></a>Публикация расширения в веб-канале центра администрирования Windows

Публикация в веб-канале центра администрирования Windows позволяет сделать расширение доступным любому пользователю центра администрирования Windows. Так как пакет SDK для Windows Admin Center по-прежнему находится на этапе предварительной версии, мы хотели бы тесно работать с вами, чтобы помочь в устранении проблем разработки и убедиться, что вы можете предоставить пользователям качественный продукт и опыт работы с ним.

Прежде чем выпустить первоначальную версию расширения, рекомендуется отправить запрос на проверку расширения в корпорацию Майкрософт по крайней мере до 2-3 недель перед выпуском, чтобы убедиться, что у нас достаточно времени для проверки, и при необходимости внести изменения в расширение. Когда ваше расширение будет готово к публикации, его необходимо отправить нам для проверки, а если он утвержден, мы будем публиковать его в веб-канале.

Затем, если вы хотите освободить обновление для расширения, необходимо отправить другой запрос на проверку. В зависимости от области изменения время обработки для проверок обновлений должно быть короче.

### <a name="submit-an-extension-review-request-to-microsoft"></a>Отправка запроса на проверку расширения в корпорацию Майкрософт

Чтобы отправить запрос на проверку расширения, введите следующие сведения и отправьте сообщение электронной почты по адресу [wacextensionrequest@microsoft.com](mailto:wacextensionrequest@microsoft.com?subject=Windows%20Admin%20Center%20Extension%20Review%20Request). Мы ответим на ваш адрес электронной почты в течение недели.

```
Windows Admin Center Extension Review Request
1. Name and email address of extension owner/developer (up to 3 users). If you will be releasing an extension on behalf of your company, provide your company email address.
2. Company name (Only required if you are releasing an extension on behalf of your company):
3. Extension name:
4. Release target date (estimate):
5. For new extension submission - Extension description (early design wire frames, screen mockups or product screenshots are highly recommended):
6. For extension update review – Description of changes (include product screenshots if UI has been significantly changed):
```

### <a name="submit-your-extension-package-for-review-and-publishing"></a>Отправка пакета расширения для проверки и публикации

Убедитесь, что вы выполняйте приведенные выше инструкции по [созданию пакета расширения](#creating-an-extension-package) , и файл nuspec определен правильно, и файлы подписаны. Также рекомендуется наличие веб-сайта проекта, включая следующие:

- Подробное описание расширения, включая снимки экрана или видео
- Адрес электронной почты или компонент веб-сайта для получения отзывов или вопросов

Когда вы будете готовы опубликовать расширение, отправьте сообщение электронной почты по адресу [wacextensionrequest@microsoft.com](mailto:wacextensionrequest@microsoft.com?subject=Windows%20Admin%20Center%20Extension%20Package%20Review) и получите инструкции по отправке вашего пакета расширения. После получения пакета мы рассмотрим и, если он утвержден, опубликуйте его в веб-канале центра администрирования Windows.