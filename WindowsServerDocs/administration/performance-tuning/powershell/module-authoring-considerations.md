---
title: Вопросы создания модулей PowerShell
description: Вопросы создания модулей PowerShell
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: JasonSh
author: lzybkr
ms.date: 10/16/2017
ms.openlocfilehash: 8945339e7a7950d3cd722ab2af629b45e7f6dd5d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370358"
---
# <a name="powershell-module-authoring-considerations"></a>Вопросы создания модулей PowerShell

Этот документ содержит некоторые рекомендации, связанные с тем, как создается модуль для лучшей производительности.

## <a name="module-manifest-authoring"></a>Создание манифеста модуля

Манифест модуля, который не использует следующие рекомендации, может оказать заметное влияние на общую производительность PowerShell, даже если модуль не используется в сеансе.

Функция автоматического обнаружения команд анализирует каждый модуль, чтобы определить, какие команды экспортирует модуль, и этот анализ может быть дорогостоящим.
Результаты анализа модулей кэшируются для каждого пользователя, но кэш недоступен при первом запуске, что является типичным сценарием с контейнерами.
При анализе модуля, если экспортированные команды могут быть полностью определены из манифеста, можно избежать более дорогостоящего анализа модуля.

### <a name="guidelines"></a>Руководство

* В манифесте модуля не используйте подстановочные знаки в записях `AliasesToExport`, `CmdletsToExport` и `FunctionsToExport`.

* Если модуль не экспортирует команды определенного типа, явно укажите его в манифесте, указав `@()`.
Отсутствующая или `$null` запись эквивалентна указанию подстановочного знака `*`.

По возможности следует избегать следующих действий:

```PowerShell
@{
    FunctionsToExport = '*'

    # Also avoid omitting an entry, it is equivalent to using a wildcard
    # CmdletsToExport = '*'
    # AliasesToExport = '*'
}
```

Вместо этого используйте:

```PowerShell
@{
    FunctionsToExport = 'Format-Hex', 'Format-Octal'
    CmdletsToExport = @()  # Specify an empty array, not $null
    AliasesToExport = @()  # Also ensure all three entries are present
}
```

## <a name="avoid-cdxml"></a>Избегайте CDXML

При принятии решения о реализации модуля можно выбрать три основных варианта:

* Двоичный ( C#обычно)
* Script (PowerShell)
* CDXML (обтекание CIM XML-файла)

Если скорость загрузки вашего модуля важна, то процесс CDXML примерно медленнее, чем двоичный модуль.

Двоичный модуль загружает самую быструю загрузку, так как он компилируется заранее и может использовать NGen для JIT-компиляции на каждом компьютере.

Модуль скрипта обычно загружает немного медленнее, чем двоичный модуль, так как PowerShell должен проанализировать скрипт перед его компиляцией и выполнением.

Модуль CDXML обычно намного медленнее, чем модуль скрипта, поскольку сначала он должен анализировать XML-файл, который затем создает довольно небольшой сценарий PowerShell, который затем анализируется и компилируется.

