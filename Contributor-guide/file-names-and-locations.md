<properties title="" pageTitle="Имена файлов и расположения для технических статей Windows Server 2016" description="Описание структуры файлов для статей, а также соглашения об именовании, которые необходимо выполнить при создании новой статьи." metaKeywords="" services="" solutions="" documentationCenter="" authors="Kathy-Davies" videoId="" scriptId="" manager="required" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="03/14/2016" ms.author="jimpark; tysonn" />

# <a name="file-names-and-locations-for-windows-server-technical-articles"></a>Имена файлов и расположения для технических статей Windows Server

Зная и следуя правилам помогает получить ваш запрос на Вытягивание, принят быстрее.

+ [правила]
+ [Шаблон]
+ [Утверждение имен файлов]

## <a name="rules"></a>Правила

- Все файлы должны быть в формате markdown и использовать расширение файла. md.
- По возможности сохранять имена файлов слова 3-5 - 10 слов на самом деле слишком долго для удобства чтения и оптимизацией поисковых СИСТЕМ.
- Используйте строчные и только буквы, цифры и дефисы.
- Без пробелов и знаков препинания. Для разделения слов и чисел в имя файла, используйте дефис.
- Не используйте в краткой форме команды действия, "-ing" формы: `deploy-nano-server` не `Deploying-Nano-Server`
- Указывайте служебные слова, такие как и, in, или.
- Орфографии слов Старайтесь не употреблять неутвержденные или ненужные в именах файлов
- Имена файлов должны быть уникальными - вместо `overview.md` использовать `storage-spaces-overview.md`

Акронимов и сокращений, в именах файлов - конкретные рекомендации:

- Существующие рекомендации Microsoft, для сокращения допустимого имени
- Стандартные для отрасли сокращения допустимы при необходимости в именах файлов.

## <a name="pattern"></a>Шаблон

Просмотрите список статей в репозитории, чтобы получить представление о существующих именах. Ниже приведен общий шаблон.

 **компонент разделе title.md**
 
Например `storage-spaces-direct-overview.md` 

## <a name="file-name-approval"></a>Утверждение имен файлов

При отправке нового файла, рецензенты запросов на Вытягивание просмотрите имя и отправить отзыв через поток комментариев запроса на включение внесенных изменений, если необходимо внести изменения. Имя файла должно быть исправлено до принятия запроса на включение внесенных изменений. Участники могут легко отправить запрос на Вытягивание ожидающие обновления.

## <a name="folders-in-the-repo"></a>Папки в репозитории

Используйте существующую структуру каталогов. Не создавайте папки без получения утверждения от администратора репозитория. Обратитесь к ним, если вы считаете, что новая папка.

Репозиторий GitHub должны иметь простой и относительно плоскую структуру папки — \<области >\\\<технологии > — для примера storage\data дедупликации. Это дает следующие преимущества:
 - Это очень просто.
 - Она будет ближе к работе Azure.com
 - Он упрощает для модулей записи/PMs, быстро находить их темы — не нужно туда-сюда через другие папки, ищете где вложен определенной технологии.
 - Она хранит URL-адрес short, которые хорошо подходят для оптимизации поисковой системы и взаимодействие с пользователем, время от времени клиенты взгляните на URL-адрес для подсказки.

## <a name="changing-case-in-file-names"></a>Смена регистра в именах файлов

Операционные системы Windows зависят от регистра символов. Если вам нужно изменить имя файла, чтобы исправить регистр, лучше внести изменения в содержимое файла, если только вы не в Linux или Mac. Пример:

  biztalk-administration-and-Development-Task-List-in-BizTalk-Services--> biztalk-services-administration-and-development-task-list

Используйте `git mv` команду, чтобы переименовать файл:
```
  git mv <WindowsServerDocs/tech-area/subarea/current-file-name.md> <WindowsServerDocs/tech-area/subarea/new-file-name.md>
```

### <a name="contributors-guide-links"></a>Ссылки руководство для участников

- [Указатель руководств](./contributor-guide-index.md)


<!--Anchors-->
[правила]: #rules
[Шаблон]: #pattern
[Утверждение имен файлов]: #file-name-approval