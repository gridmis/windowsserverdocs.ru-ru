---
title: nslookup ls
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f15f06fe-67e7-41a9-93b5-192ab14ab380
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ecc419a72599b661865af6283821129a7021938a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373086"
---
# <a name="nslookup-ls"></a>nslookup ls

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Выводит сведения для домена службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
ls [<Option>] <DNSDomain> [{[>] <FileName>|[>>] <FileName>}]
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                                                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                                                                |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <Option>     | В следующей таблице перечислены допустимые параметры.<br /><br />--t: перечисляет все записи указанного типа. Описание <querytype>см. в разделе **сеткуеритипе** (дополнительные ссылки).<br />--a: перечисляет псевдонимы компьютеров в домене DNS. Этот параметр является синонимом для **-t CNAME**<br />--d: список всех записей для DNS-домена. Этот параметр является синонимом для **-t Any**<br />--h: выводит сведения о ЦП и операционной системе для домена DNS. Этот параметр является синонимом для **-t HINFO**<br />--s: выводит список хорошо известных служб компьютеров в домене DNS. Этот параметр является синонимом параметра **-t WKS**. |
|   <DNSDomain>   |                                                                                                                                                                                                                                                                                         Указывает домен DNS, сведения о котором требуется получить.                                                                                                                                                                                                                                                                                         |
|   <FileName>    |                                                                                                                                                                                                                                 Указывает имя файла, в котором следует сохранить выходные данные. Для перенаправления выходных данных в обычном режиме можно использовать символы "больше" (>) и "больше" (> >).                                                                                                                                                                                                                                  |
| {Help &#124; ?} |                                                                                                                                                                                                                                                                                          Отображает краткую сводку подкоманд **nslookup** .                                                                                                                                                                                                                                                                                           |

## <a name="remarks"></a>Замечания
- В выходных данных по умолчанию содержатся имена компьютеров и их IP-адреса. Когда выходные данные направляются в файл, для каждых 50 записей, полученных с сервера, выводятся хэш-знаки.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [nslookup set QueryType](nslookup-set-querytype.md)
