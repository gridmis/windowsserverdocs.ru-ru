---
ms.assetid: c50ecc6a-9504-4b4a-816f-e762dcf3a95e
title: Установка службы роли прокси-агента службы федерации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 1f66e863c28aea7c9214c8363328a103b0a92f06
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359569"
---
# <a name="install-the-federation-service-proxy-role-service"></a>Установка службы роли прокси-агента службы федерации

После настройки компьютера с необходимыми приложениями и сертификатами можно приступать к установке службы роли прокси-агент службы федерации службы федерации Active Directory (AD FS) \(AD FS\). Для установки службы роли прокси-агент службы федерации можно использовать следующую процедуру. При установке службы роли прокси-агент службы федерации на компьютере этот компьютер станет прокси-сервером федерации.  
  
Для выполнения этой процедуры минимальным требованием является членство в группе **Администраторы** или эквивалентные права на локальном компьютере.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="to-install-the-federation-service-proxy-role-service-using-the-server-manager"></a>Установка службы роли прокси-агент службы федерации с помощью диспетчер сервера
  
1.  На **начальном** экране введите**Диспетчер сервера**и нажмите клавишу ВВОД.  
  
2.  Щелкните **Управление**, а затем щелкните **Добавить роли и компоненты** , чтобы запустить мастер добавления ролей и компонентов.  
  
3.  На странице **Перед работой** нажмите кнопку **Далее**.  
  
4.  На странице **Выбор типа установки** щелкните **роль\-на основе ролей или компонентов\-установки**и нажмите кнопку **Далее**.  
  
5.  На странице **Выбор целевого сервера** щелкните **выбрать сервер в пуле серверов**, убедитесь, что целевой компьютер выделен, а затем нажмите кнопку **Далее**.  
  
6.  На странице **Выбор ролей сервера** щелкните **Удаленный доступ**, а затем нажмите кнопку Далее.  
  
    > [!NOTE]  
    > Если будет предложено установить дополнительные компоненты .NET Framework или службы активации Windows, щелкните **Добавить компоненты** , чтобы установить их.  
  
7. На странице **Выбор служб ролей** установите флажок **прокси-агент службы федерации** и нажмите кнопку **Далее**.  

8. После проверки информации на странице **Подтверждение выбранных элементов для установки** установите флажок **Автоматический перезапуск конечного сервера, если требуется** , а затем щелкните **Установить**.  
  
13. На странице **Ход установки** убедитесь, что все установлено верно, а затем нажмите кнопку **Закрыть**.  

### <a name="to-install-the-federation-service-proxy-role-service-using-powershell"></a>Установка службы роли прокси-агент службы федерации с помощью PowerShell

1. Откройте Windows PowerShell (Запуск от имени администратора).

2. Введите следующую команду и нажмите клавишу **Ввод**:

        Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools



  
## <a name="additional-references"></a>Дополнительная справка  
[Контрольный список: Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)  
  
[Контрольный список: Настройка прокси-сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  

