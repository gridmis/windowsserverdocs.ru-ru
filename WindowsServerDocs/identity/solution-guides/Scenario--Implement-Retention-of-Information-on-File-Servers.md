---
ms.assetid: 81c55015-82e5-4ba1-b15e-cc7b49af28fc
title: Сценарий, реализующий хранение информации на файловых серверах
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: b6df28987e9e6d2fa1382b00e9403f2d112fc226
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406984"
---
# <a name="scenario-implement-retention-of-information-on-file-servers"></a>Сценарий: реализация хранения информации на файловых серверах

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Период хранения — это время, в течение которого следует хранить документ, прежде чем он будет просрочен. В зависимости от организации период хранения может быть разным. Файлы в папке можно классифицировать как подлежащие кратко-, средне- и долгосрочному хранению, а затем назначить для каждого периода свои временные рамки. Возможно, какой-либо файл вам понадобится хранить неограниченно долго, поместив его на удержание по юридическим причинам.  
  
## <a name="BKMK_OVER"></a>Описание сценария  
Инфраструктура классификации файлов и диспетчер ресурсов файлового сервера используют задачи управления файлами и классификацию файлов для применения периодов хранения к набору файлов. Вы можете назначить период хранения для папки, а затем с помощью задачи управления файлами настроить, сколько должен длиться назначенный период. Когда срок хранения файлов в папке подходит к концу, их владелец получает уведомление по электронной почте. Также файл можно классифицировать как находящийся на удержании по юридическим причинам, благодаря чему задача управления файлами не завершит срок хранения этого файла.  
  
Сведения о планировании настройки хранения см. в разделе [Plan for Retention of Information on File Servers](assetId:///edf13190-7077-455a-ac01-f534064a9e0c).  
  
Вы можете узнать, как классифицировать файлы для юридических удержаний и настроить период хранения в разделе [развертывание реализация хранения сведений на файловых серверах &#40;&#41;](Deploy-Implementing-Retention-of-Information-on-File-Servers--Demonstration-Steps-.md).  
  
> [!NOTE]  
> В этом сценарии описывается, только как вручную классифицировать документ для удержания по юридическим причинам. Однако в Windows Server 2012 можно автоматически классифицировать документы для юридического хранения. Один из способов — создать классификатор Windows PowerShell, который сравнивает владельца файла со списком учетных записей пользователей, находящихся на удержании по юридическим причинам. Если владелец файла входит в этот список, файл классифицируется для удержания по юридическим причинам.  
  
## <a name="in-this-scenario"></a>Содержание сценария  
Этот сценарий является частью сценария динамического контроля доступа. Дополнительные сведения о динамическом контроле доступа см. в следующих разделах:  
  
-   [Динамический контроль доступа. Обзор сценария](Dynamic-Access-Control--Scenario-Overview.md)  
  
## <a name="BKMK_NEW"></a>Функции, входящие в этот сценарий  
В следующей таблице перечислены компоненты, являющиеся частью данного сценария, и описано, как они поддерживают его.  
  
|Компонент|Способ поддержки сценария|  
|-----------|---------------------------------|  
|[Обзор диспетчер ресурсов файлового сервера](https://technet.microsoft.com/library/hh831701.aspx)|Инфраструктура классификации файлов — это компонент диспетчера ресурсов файлового сервера.|  
|[Обзор служб файлов и хранилищ](https://technet.microsoft.com/library/hh831487.aspx)|Диспетчер ресурсов файлового сервера — это компонент, включенный в роль сервера файловых служб.|  
  
  


