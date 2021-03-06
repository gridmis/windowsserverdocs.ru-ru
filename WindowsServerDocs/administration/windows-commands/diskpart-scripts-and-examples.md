---
title: Сценарии и примеры для DiskPart
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 319c0795-11df-47c8-b203-eadb0577ee0d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c40ce79664795297af4369e35cbda7422617e6e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377850"
---
# <a name="diskpart-scripts-and-examples"></a>Сценарии и примеры для DiskPart

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Используйте `/s` DiskPart для запуска скриптов, автоматизирующих\-связанные с дисками задачи, такие как создание томов или преобразование дисков в динамические диски. Написание сценариев этих задач полезно при развертывании Windows с помощью автоматической установки или средства Sysprep, которые не поддерживают создание томов, отличных от загрузочного тома.  
  
-   Чтобы создать сценарий DiskPart, создайте текстовый файл, содержащий команды DiskPart, которые необходимо выполнить, с одной командой в строке и без пустых строк. Чтобы сделать строку комментарием, можно начать строку с `rem`.  
  
    Например, Вот сценарий, который очищает диск, а затем создает раздел 300 МБ для среды восстановления Windows:  
  
    ```  
    select disk 0  
    clean  
    convert gpt  
    create partition primary size=300  
    format quick fs=ntfs label="Windows RE tools"  
    assign letter="T"  
    ```  
  
-   Чтобы запустить сценарий DiskPart, в командной строке введите следующую команду, где *имя_сценария* — это имя текстового файла, содержащего скрипт.  
  
    ```  
    diskpart /s scriptname.txt  
    ```  
  
-   Чтобы перенаправить выходные данные сценария DiskPart в файл, введите следующую команду, где *файл_журнала* — это имя текстового файла, где DiskPart записывает выходные данные.  
  
    ```  
    diskpart /s scriptname.txt > logfile.txt  
    ```  
  
> [!IMPORTANT]  
> При использовании команды **DiskPart** в составе скрипта рекомендуется выполнять все операции DiskPart вместе в рамках одного сценария DiskPart. Можно выполнять последовательные скрипты DiskPart, но по крайней мере 15 секунд между каждым сценарием необходимо выполнить полное завершение работы, прежде чем запускать команду **DiskPart** в последующих сценариях. В противном случае последующие сценарии могут завершиться ошибкой. Можно добавить паузу между последовательными сценариями DiskPart, добавив команду `timeout /t 15` в пакетный файл вместе с сценариями DiskPart.  
  
При запуске программы DiskPart в командной строке отобразится версия и имя сервера DiskPart. По умолчанию, если при попытке выполнения задачи, выполняемой в скрипте, DiskPart обнаруживает ошибку, DiskPart прекращает обработку скрипта и отображает код ошибки \(, если только не указан параметр **noerr**\). Однако при возникновении синтаксических ошибок программа DiskPart всегда возвращает ошибки, независимо от того, использовался ли параметр **noerr** . Параметр **noerr** позволяет выполнять такие полезные задачи, как использование одного сценария для удаления всех разделов на всех дисках, независимо от общего числа дисков.  
  
## <a name="see-also"></a>См. также  
[Пример: Настройка UEFI\/GPT\-разделов жесткого диска с помощью Windows PE и программы DiskPart](https://technet.microsoft.com/library/hh825686.aspx)  
[Пример: Настройка BIOS\/MBR\-разделов жесткого диска с помощью Windows PE и программы DiskPart](https://technet.microsoft.com/library/hh825677.aspx)  
[Командлеты хранилища в Windows PowerShell](https://technet.microsoft.com/library/hh848705.aspx)  
  

