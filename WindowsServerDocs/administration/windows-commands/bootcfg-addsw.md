---
title: bootcfg addsw
description: Раздел команд Windows для **bootcfg аддсв** — Добавление параметров загрузки операционной системы для указанной записи операционной системы.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8389293-ecd9-42f0-b84b-b9ead4cf52e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2dd727c839babe1ae4f7743285844f35cf5bf76e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380182"
---
# <a name="bootcfg-addsw"></a>bootcfg addsw

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет параметры загрузки операционной системы для указанной записи операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /addsw [/s <computer> [/u <Domain>\<User> /p <Password>]] [/mm <MaximumRAM>] [/bv] [/so] [/ng] /id <OSEntryLineNum>
```
## <a name="parameters"></a>Параметры

|         Термин         |                                                                                                            Определение                                                                                                            |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>     |                                                        Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                        |
| /u <Domain>\\<User>  |               Выполняет команду с разрешениями учетной записи пользователя, указанного в <User> или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.               |
|    /p <Password>     |                                                                      Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                                       |
|   /mm <MaximumRAM>   |                                          Указывает максимальный объем ОЗУ в мегабайтах, который может использоваться операционной системой. Значение должно быть больше или равно 32 МБ.                                          |
|         /bv          |                                    Добавляет параметр **/басевидео** к указанному <OSEntryLineNum>, направляя операционную систему для использования стандартного режима VGA для установленного видеодрайвера.                                     |
|         /So          |                                      Добавляет параметр **/SOS** в указанную *номер_строки_записи_в_разделе_ОС*, направляя операционную систему на отображение имен драйверов устройств во время их загрузки.                                      |
|         /NG          |                                         Добавляет параметр **/ногуибут** к заданному <OSEntryLineNum>, отключая индикатор выполнения, который отображается перед запросом Ctrl + Alt + Del для входа.                                          |
| /ID <OSEntryLineNum> | Указывает номер строки записи операционной системы в разделе [Operating Systems] файла Boot. ini, в который добавляются параметры загрузки операционной системы. Первая строка после заголовка раздела [Operating Systems] — 1. |
|          /?          |                                                                                               Отображение справки в командной строке.                                                                                               |

## <a name="BKMK_examples"></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/ADDSW** :
```
bootcfg /addsw /mm 64 /id 2 
bootcfg /addsw /so /id 3 
bootcfg /addsw /so /ng /s srvmain /u hiropln /id 2 
bootcfg /addsw /ng /id 2 
bootcfg /addsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
