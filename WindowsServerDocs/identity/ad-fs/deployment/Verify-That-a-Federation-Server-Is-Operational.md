---
ms.assetid: ad61c586-ba8a-4534-8824-b45994d60c6b
title: Проверка работоспособности сервера федерации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 6d27c8d69affe001630d8deaa2c21f334f8f86ad
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408310"
---
# <a name="verify-that-a-federation-server-is-operational"></a>Проверка работоспособности сервера федерации


Чтобы проверить работоспособность сервера федерации, выполните указанные ниже процедуры. Работоспособный сервер доступен всем клиентам, находящимся в одной с ним сети.  
  
Минимальным требованием для выполнения этой процедуры является членство в одной из следующих групп: **Пользователи**, **Операторы архива**, **Опытные пользователи**, **Администраторы**, — или эквивалентной группе на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="procedure-1-to-verify-that-a-federation-server-is-operational"></a>Процедура 1. Проверка работоспособности сервера федерации  
  
1.  Чтобы убедиться, что \(службы IIS\) IIS правильно настроен на сервере федерации, войдите на клиентский компьютер, расположенный в том же лесу, что и сервер федерации.  
  
2.  Откройте окно браузера, в адресной строке введите имя узла DNS сервера федерации, а затем добавьте в него/адфс/ФС/федератионсерверсервице.асмкс для нового сервера федерации, например:  
  
    **https://fs1.fabrikam.com/adfs/fs/federationserverservice.asmx**  
  
3.  Нажмите клавишу ВВОД и выполните указанную ниже процедуру на компьютере сервера федерации. Если появляется сообщение **о проблеме с сертификатом безопасности этого веб-сайта**, нажмите кнопку **"продолжить" для этого веб-сайта**.  
  
    В результате должна отобразиться XML-страница с описанием службы. Если она отображается, службы IIS на сервере федерации доступны и успешно обрабатывают страницы.  
  
Для выполнения этой процедуры минимальным требованием является членство в группе **Администраторы** или эквивалентные права на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="procedure-2-to-verify-that-a-federation-server-is-operational"></a>Процедура 2. Проверка работоспособности сервера федерации  
  
1.  Войдите на новый сервер федерации с правами администратора.  
  
2.  На **начальном** экране введите **Просмотр событий**и нажмите клавишу ВВОД.  
  
3.  В области сведений\-дважды щелкните **журналы приложений и служб**, дважды\-щелкните **AD FS события**, а затем щелкните **Администратор**.  
  
4.  В столбце **идентификатор события** найдите событие с идентификатором 100. Если сервер федерации настроен правильно, вы увидите новое событие — в журнале приложений Просмотр событий — с ИДЕНТИФИКАТОРом события 100. Это событие проверяет, удалось ли серверу федерации успешно взаимодействовать с служба федерации.  
  
## <a name="additional-references"></a>Дополнительная справка  
[Контрольный список. Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)  
  

