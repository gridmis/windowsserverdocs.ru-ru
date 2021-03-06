---
title: driverquery
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92ca4b84-e4e2-405b-9f31-bf6db9f66839
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5d44a1be300b7178bc2271187344c2fc4ab8815e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377655"
---
# <a name="driverquery"></a>driverquery



Позволяет администратору отображать список установленных драйверов устройств и их свойств. Если используется без параметров, на локальном компьютере выполняется **driverquery** .

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
driverquery [/s <System> [/u [<Domain>\]<Username> [/p <Password>]]] [/fo {table | list | csv}] [/nh] [/v | /si]
```

## <a name="parameters"></a>Параметры

|         Параметр         |                                                                                                                                         Описание                                                                                                                                          |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       /s \<> системы        |                                                                                      Указывает имя или IP-адрес удаленного компьютера. Не используйте обратные косые черты. По умолчанию используется локальный компьютер.                                                                                       |
| /u [\<> домена\]<Username> | Выполняет команду с учетными данными учетной записи пользователя, *указанной пользователем\** *домена* <em>. По умолчанию \*\*/s</em>\* использует учетные данные пользователя, который в данный момент вошел в систему компьютера, выполняющего команду. **/u** не может использоваться, если не указан параметр **/s** . |
|      /p \<пароль >       |                                                                           Указывает пароль учетной записи пользователя, указанной в параметре **/u** . параметр **/p** нельзя использовать, если не указан параметр **/u** .                                                                            |
|        /FO {таблица         |                                                                                                                                             list                                                                                                                                             |
|            использован            |                                                                                      Исключает строку заголовка из отображаемых сведений о драйвере. Недопустим, если для параметра **/FO** задано значение **List**.                                                                                      |
|            /v             |                                                                                                               Отображает подробные выходные данные. параметр **/v** недопустим для подписанных драйверов.                                                                                                               |
|            /Si            |                                                                                                                          Предоставляет сведения о подписанных драйверах.                                                                                                                          |
|            /?             |                                                                                                                             Отображение справки в командной строке.                                                                                                                             |

## <a name="BKMK_examples"></a>Примеров

Чтобы отобразить список установленных драйверов устройств на локальном компьютере, введите:
```
driverquery 
```
Чтобы отобразить выходные данные в формате значений с разделителями-запятыми (CSV), введите:
```
driverquery /fo csv 
```
Чтобы скрыть строку заголовка в выходных данных, введите:
```
driverquery /nh 
```
Чтобы использовать команду **driverquery** на удаленном сервере с именем **Server1** , используя текущие учетные данные на локальном компьютере, введите:
```
driverquery /s server1
```
Чтобы использовать команду **driverquery** на удаленном сервере с именем **Server1** , используя учетные данные для пользователя **User1** в домене **маиндом**, введите:
```
driverquery /s server1 /u maindom\user1 /p p@ssw3d
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)