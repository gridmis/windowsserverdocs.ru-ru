---
title: 'Secedit: женератероллбакк'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 385a6799-51a7-4fe3-bd73-10c7998b6680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 797f93f010a903d6ec21f568d8d665cb2e42e692
ms.sourcegitcommit: 5ed817fff1262e390403a4f4f6c38fdc12300c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702745"
---
# <a name="seceditgeneraterollback"></a>Secedit: женератероллбакк



Позволяет создать шаблон отката для указанного шаблона конфигурации. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback template file name> [/log <log file name>] [/quiet]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|db|Обязательный.</br>Указывает путь и имя файла базы данных, содержащей сохраненную конфигурацию, для которой будет выполняться анализ.</br>Если имя файла указывает базу данных, для которой не был создан шаблон безопасности (представленный файлом конфигурации), необходимо также указать параметр командной строки `/cfg \<configuration file name>`.|
|CFG|Обязательный.</br>Указывает путь и имя файла для шаблона безопасности, который будет импортирован в базу данных для анализа.</br>Этот параметр/cfg допустим только при использовании с параметром `/db \<database file name>`. Если этот параметр не указан, анализ выполняется для любой конфигурации, уже хранящейся в базе данных.|
|рбк|Обязательный.</br>Указывает шаблон безопасности, в который записываются сведения об откате. Шаблоны безопасности создаются с помощью оснастки "Шаблоны безопасности". С помощью этой команды можно создать файлы отката.|
|log|Необязательно.</br>Указывает путь и имя файла журнала для процесса.|
|quiet|Необязательно.</br>Подавляет вывод на экран и журнал. Вы по-прежнему можете просматривать результаты анализа с помощью оснастки "Настройка и анализ безопасности" консоли управления (MMC).|

## <a name="remarks"></a>Примечания.

Если путь к файлу журнала не указан, используется файл журнала по умолчанию (*СистемныйКорневойКаталог*\Users \*UserAccount \<em>документс\секурити\логс\*DatabaseName</em>. log).

Начиная с Windows Server 2008 `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [gpupdate](gpupdate.md).

При успешном выполнении этой команды будет указано состояние «задача выполнена успешно». и записывает только несоответствия между указанным шаблоном безопасности и конфигурацией политики безопасности. В нем перечислены несоответствия в Scesrv. log.

Если указан существующий шаблон отката, эта команда перезапишет ее. С помощью этой команды можно создать новый шаблон отката. Никаких дополнительных параметров для какого либо либо условия не требуется.

## <a name="BKMK_Examples"></a>Примеры

После создания шаблона безопасности с помощью оснастки "Настройка и анализ безопасности" Сектмплконтосо. INF создайте файл конфигурации отката, чтобы сохранить исходные параметры. Запишите действие в файл журнала FY11.
```
Secedit /generaterollback /db C:\Security\FY11\SecDbContoso.sdb /cfg sectmplcontoso.inf /rbk sectmplcontosoRBK.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Программу Secedit](secedit.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)