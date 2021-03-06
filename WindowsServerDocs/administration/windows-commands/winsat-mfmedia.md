---
title: мфмедиа WinSAT
description: Команды Windows
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09a3b3dd-f746-4e6e-b684-76a9bde0c78d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3684d4b23ba6d34febe226f54b8b2ab2204f610c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361896"
---
# <a name="winsat-mfmedia"></a>мфмедиа WinSAT



Измеряет производительность декодирования видео (воспроизведения) с помощью платформы Media Foundation Framework.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
winsat mfmedia <parameters>
```

## <a name="parameters"></a>Параметры

|Параметры|Описание|
|----------|-----------|
|-input \<file имя >|Обязательно. Укажите файл, содержащий видеоклип для воспроизведения или кодирования. Файл может быть в любом формате, который может быть визуализирован с помощью Media Foundation.|
|-думпграф|Укажите, что граф фильтра следует сохранить в файл, совместимый с Графедит, перед началом оценки.|
|— NS|Укажите, что граф фильтра должен выполняться с нормальной скоростью воспроизведения входного файла. По умолчанию граф фильтра выполняется как можно быстрее, игнорируя время презентации.|
|-Play|Запустите оценку в режиме декодирования и воспроизводите любое переданное аудио содержимое в файле, указанном во **входных данных** , с помощью устройства DirectSound по умолчанию. По умолчанию воспроизведение звука отключено.|
|-нопмп|Не используйте процесс Media Foundation защищенного носителя (МФПМП) во время оценки.|
|-PMP|Всегда используйте процесс МФПМП во время оценки.</br>Примечание. Если значение **-PMP** или **-нопмп** не указано, МФПМП будет использоваться только при необходимости.|
|-v|Отправка подробных выходных данных в STDOUT, включая сведения о состоянии и ходе выполнения. Все ошибки также будут записываться в командное окно.|
|-XML \<имя файла >|Сохранить выходные данные оценки как указанный XML-файл. Если указанный файл существует, он будет перезаписан.|
|-идискинфо|Сохраните сведения о физических томах и логических дисках  **\<в разделе системконфиг >** в выходных данных XML.|
|-игуид|Создайте глобальный уникальный идентификатор (GUID) в выходном XML-файле.|
|-Примечание "текст примечания"|Добавьте текст  **\<** примечания в раздел Note > в выходном XML-файле.|
|-ИКН|Включите имя локального компьютера в выходной XML-файл.|
|-EEF|Перечислить дополнительные сведения о системе в выходном XML-файле.|

## <a name="BKMK_examples"></a>Примеров

- В следующем примере выполняется оценка с входным файлом, который используется во время оценки **формальной службы WinSAT** без применения Media Foundationного конвейера МФПМП, на компьютере, где c:\Windows — это расположение папки Windows.  
  ```
  winsat mfmedia -input c:\windows\performance\winsat\winsat.wmv -nopmp
  ```

## <a name="remarks"></a>Примечания

-   Членство в группе локальных администраторов или эквивалентной является минимальным требованием для использования **WinSAT**. Команда должна быть выполнена из окна командной строки с повышенными привилегиями.
-   Чтобы открыть окно командной строки с повышенными привилегиями, нажмите кнопку **Пуск**, выберите пункт **стандартные**, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.

#### <a name="additional-references"></a>Дополнительная справка

