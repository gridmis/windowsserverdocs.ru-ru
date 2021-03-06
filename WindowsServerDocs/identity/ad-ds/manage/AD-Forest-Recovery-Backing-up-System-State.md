---
title: Восстановление леса Active Directory — резервное копирование всего сервера
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 9238cb27-0020-42f7-90d6-fcebf7e3c0bc
ms.technology: identity-adds
ms.openlocfilehash: 14aa7abc19573b76ebc144cb6dea5f510b45e269
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369351"
---
# <a name="ad-forest-recovery---backing-up-the-system-state-data"></a>Восстановление леса Active Directory. Резервное копирование данных состояния системы  

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Используйте следующую процедуру, чтобы выполнить резервное копирование состояния системы на контроллере домена с помощью cистема архивации данных Windows Server или Wbadmin. exe.  

## <a name="to-perform-a-system-state-backup-using-windows-server-backup"></a>Выполнение резервного копирования состояния системы с помощью cистема архивации данных Windows Server

1. Откройте **Диспетчер сервера**, выберите **Сервис**, а затем щелкните **Cистема архивации данных Windows Server**.
   - В Windows Server 2008 R2 и Windows Server 2008 нажмите кнопку **Пуск**, выберите пункт **Администрирование**, а затем щелкните **Cистема архивации данных Windows Server**. 

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup1.png)

2. При появлении запроса в диалоговом окне **контроль учетных записей** укажите учетные данные оператора архивации и нажмите кнопку **ОК**.
3. Щелкните **Локальная Архивация**.
4. В меню **Действие** выберите команду **Однократная архивация**.
5. В мастере однократной архивации на странице **Параметры резервного копирования** выберите **другие параметры**, а затем нажмите кнопку **Далее**.

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup3.png)

6. На странице **Выбор конфигурации резервного копирования** щелкните **Настраиваемый**, а затем нажмите кнопку **Далее**.
7. На экране **Выбор элементов для архивации** нажмите кнопку **Добавить элементы** и выберите **состояние системы** и нажмите кнопку **ОК**.
   - В Windows Server 2008 R2 и Windows Server 2008 выберите тома для включения в резервную копию. Если установить флажок **включить восстановление системы** , то будут выбраны все критические тома. 

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-System-State/systemstatebackup.png)  

8. На странице **Укажите тип назначения** выберите **локальные диски** или **Удаленная общая папка**, а затем нажмите кнопку **Далее**.  При резервном копировании в удаленную общую папку выполните следующие действия.  
   - Введите путь к общей папке.
   - В разделе **Управление доступом**выберите не **наследовать** или **наследовать** для определения доступа к резервной копии, а затем нажмите кнопку **Далее**.  
   - В диалоговом окне **укажите учетные данные пользователя для резервного копирования** укажите имя пользователя и пароль для пользователя, имеющего доступ на запись к общей папке, и нажмите кнопку **ОК**.

9. Для Windows Server 2008 R2 и Windows Server 2008 на странице **Указание дополнительных параметров** выберите **VSS копировать резервную копию** и нажмите кнопку **Далее**.
10. На странице **Выбор места расположения резервной копии** выберите расположение резервной копии.  Если выбран вариант Локальный диск выберите локальный диск или если выбран параметр Удаленная общая папка, выберите общую сетевую папку.
11. На экране подтверждения нажмите кнопку **резервное копирование**.
12. После завершения нажмите кнопку **Закрыть**.
13. Закройте cистема архивации данных Windows Server.

## <a name="to-perform-a-system-state-backup-using-wbadminexe"></a>Выполнение резервного копирования состояния системы с помощью WBADMIN. exe

Откройте командную строку с повышенными привилегиями, введите следующую команду и нажмите клавишу ВВОД:  
  
   ```
   wbadmin start systemstatebackup -backuptarget:<targetDrive>:
   ```

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-System-State/systemstatebackup2.png)  

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
