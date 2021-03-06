---
title: netcfg
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2daaab7-12db-4e36-b70c-db8906d084f7 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bfbe8cd757f78bfa3e808a9126af7d1698579885
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79320008"
---
# <a name="netcfg"></a>netcfg

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Устанавливает среда предустановки Windows (WinPE), облегченную версию Windows, используемую для развертывания рабочих станций.
## <a name="syntax"></a>Синтаксис
```
netcfg [/v] [/e] [/winpe] [/l ] /c /i
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/v|Выполнение в **подробном** режиме (подробный)|
|/e|Использование переменных **среды** обслуживания во время установки и удаления|
|/винпе|Устанавливает среду предустановки TCP/IP, NetBIOS и Microsoft Client для Windows (WinPE)|
|/l|Предоставляет **Расположение** INF-файла|
|/c|Предоставляет **класс** устанавливаемого компонента. Протокол, служба или клиент|
|/i|Предоставляет **идентификатор** компонента|
|/s|Предоставляет тип **отображаемых**компонентов.<br /><br />\та = адаптеры, n = компоненты сети|
|/b|Отображает **пути привязки**, за которым следует строка, содержащая имя пути.|
|/?|Отображает **справку** в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

Чтобы установить *Пример* протокола с помощью к:\оемдир\ексампле.инф, выполните следующие действия.
```
netcfg /l c:\oemdir\example.inf /c p /i example
```
Чтобы установить службу *MS_Server* , выполните следующие действия.
```
netcfg /c s /i MS_Server
```
Установка протокола TCP/IP, NetBIOS и Microsoft Client для среды предустановки Windows
```
netcfg /v /winpe
```
Чтобы отобразить, если компонент *MS_IPX* установлен:
```
netcfg /q MS_IPX
```
Чтобы удалить *MS_IPX*компонента, выполните следующие действия.
```
netcfg /u MS_IPX
```
Чтобы отобразить все установленные сетевые компоненты, выполните следующие действия.
```
netcfg /s n
```
Отображение путей привязки, содержащих *MS_TCPIP*:
```
netcfg /b ms_tcpip
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
