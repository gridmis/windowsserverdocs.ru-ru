---
title: cmstp
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34aad544-11c3-4e85-8bbf-5bc5a971da93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd2e8dbb08b41875335b35dd802007a0bd1fbd41
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379267"
---
# <a name="cmstp"></a>cmstp

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Устанавливает или удаляет профиль службы диспетчера подключений. При использовании без дополнительных параметров **cmstp** устанавливает профиль службы с параметрами по умолчанию, соответствующими операционной системе и разрешениям пользователя. 
## <a name="syntax"></a>Синтаксис
Синтаксис 1:
```
ServiceProfileFileName .exe /q:a /c:"cmstp.exe ServiceProfileFileName .inf [/nf] [/ni] [/ns] [/s] [/su] [/u]"
```
Синтаксис 2:
```
cmstp.exe [/nf] [/ni] [/ns] [/s] [/su] [/u]  [Drive:][path]ServiceProfileFileName.inf"
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|< ИмяФайлаПрофиляСлужбы >. exe|Указывает имя пакета установки, содержащего профиль, который требуется установить.<br /><br />Требуется для синтаксиса 1, но недопустим для синтаксиса 2.|
|/q:a|Указывает, что профиль должен быть установлен без запроса пользователя. Сообщение об успешном выполнении установки будет по-прежнему отображаться.<br /><br />Требуется для синтаксиса 1, но недопустим для синтаксиса 2.|
|[Диск:] [путь] <ServiceProfileFileName>. INF|Обязательный. Указывает имя файла конфигурации, определяющего способ установки профиля.<br /><br />Параметр [Drive:] [path] недопустим для синтаксиса 1.|
|/нф|Указывает, что файлы поддержки устанавливать не следует.|
|/ни|Указывает, что не следует создавать значок рабочего стола. Этот параметр допустим только для компьютеров под управлением Windows 95, Windows 98, Windows NT 4,0 или Windows Millennium Edition.|
|/нс|Указывает, что не следует создавать ярлыки на рабочем столе. Этот параметр допустим только для компьютеров, работающих под управлением семейства Windows Server 2003, Windows 2000 или Windows XP.|
|/s|Указывает, что профиль службы должен быть установлен или удален автоматически (без запроса ответа пользователя или при отображении проверочного сообщения).|
|/SU|Указывает, что профиль службы должен быть установлен для одного пользователя, а не для всех пользователей. Этот параметр допустим только для компьютеров под управлением Windows Server 2003, Windows 2000 или Windows XP.|
|/ау|Указывает, что профиль службы должен быть установлен для всех пользователей. Этот параметр допустим только для компьютеров под управлением Windows Server 2003, Windows 2000 или Windows XP.|
|/u|Указывает, что профиль службы должен быть удален.|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Замечания
**/s** — единственный параметр, который можно использовать в сочетании с **/u**.
Синтаксис 1 — типичный синтаксис, используемый в пользовательском приложении установки. Чтобы использовать этот синтаксис, необходимо запустить **cmstp** из каталога, содержащего файл <ServiceProfileFileName>. exe.
## <a name="BKMK_Examples"></a>Примеров
Чтобы установить вымышленный профиль службы без файлов поддержки, введите:
```
fiction.exe /c:"cmstp.exe fiction.inf /nf"
```
Чтобы автоматически установить вымышленный профиль службы для одного пользователя, введите:
```
fiction.exe /c:"cmstp.exe fiction.inf /s /su"
```
Чтобы автоматически удалить вымышленный профиль службы, введите:
```
fiction.exe /c:"cmstp.exe fiction.inf /s /u"
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
