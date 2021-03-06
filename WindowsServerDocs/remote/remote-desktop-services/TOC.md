# [Службы удаленных рабочих столов](welcome-to-rds.md)
## [Начало работы](rds-get-started.md)
### [Что нового в RDS?](rds-whats-new.md)
### [Поддерживаемые конфигурации для RDS](rds-supported-config.md)
### [Конфигурации безопасности, поддерживаемые для инфраструктуры виртуальных рабочих столов (VDI) Windows 10](rds-vdi-supported-config.md)
### [Афиша по планированию для служб удаленных рабочих столов](rds-poster.md)
### [Партнеры по размещению служб удаленных рабочих столов](rds-hosting-partners.md)
## [Планирование и проектирование](rds-plan-and-design.md)
### [Сборка в любом расположении](rds-plan-build-anywhere.md)
### [Рабочие нагрузки Удаленного рабочего стола](remote-desktop-workloads.md)
### [Руководство по настройке сети](network-guidance.md)
### [Руководство по выбору размеров виртуальных машин](virtual-machine-recs.md)
### [Доступ из любого расположения](rds-plan-access-from-anywhere.md)
### [Высокая доступность](rds-plan-high-availability.md)
### [Многофакторная идентификация](rds-plan-mfa.md)
### [Безопасное хранилище данных](rds-plan-secure-data-storage.md)
### [Ускорение с помощью GPU](rds-graphics-virtualization.md)
### [Подключение с любого устройства](rds-plan-connect-from-any-device.md)
### [Выбор способа оплаты](rds-plan-choose-how-you-pay.md)
### [Office 2016 в развертываниях RDS и VDI](https://docs.microsoft.com/deployoffice/rds-office-vdi-rdsh)
#### [Использование поиска Outlook в средах без сохранения состояния](https://docs.microsoft.com/deployoffice/rds-outlook-search)
#### [OneDrive для бизнеса и среды VDI](https://docs.microsoft.com/deployoffice/rds-onedrive-business-vdi)
### [Эталонная архитектура размещения рабочих столов](Desktop-Hosting-Reference-Architecture.md)
#### [Архитектура служб удаленных рабочих столов](Desktop-hosting-logical-architecture.md)
#### [Служба размещения рабочих столов](Desktop-hosting-service.md)
#### [Роли служб удаленных рабочих столов](rds-roles.md)
#### [Службы и рекомендации Azure для размещения рабочих столов](Azure-services-and-considerations-for-desktop-hosting.md)
## [Сборка и развертывание](rds-build-and-deploy.md)
### [Развертывание экспериментальной среды RDS с помощью ARM и Azure Marketplace](rds-in-azure.md)
### [Перенос развертываний служб удаленных рабочих столов в Windows Server 2016](migrate-rds-role-services.md)
### [Перенос клиентских лицензий (CAL) служб удаленных рабочих столов (RDS)](migrate-rds-cals.md)
### [Обновление развертываний служб удаленных рабочих столов до Windows Server 2016](upgrade-to-rds.md)
#### [Обновление серверов узлов сеансов удаленных рабочих столов](upgrade-to-rdsh.md)
#### [Обновление серверов узлов виртуализации удаленных рабочих столов](upgrade-to-rdvh.md)
### [Развертывание инфраструктуры служб удаленных рабочих столов](rds-deploy-infrastructure.md)
### [Создание и развертывание коллекции служб удаленных рабочих столов](rds-create-collection.md)
### [Настройка веб-клиента удаленного рабочего стола для пользователей](clients/remote-desktop-web-client-admin.md)
### [Настройка обнаружения электронной почты для пользователей](rds-email-discovery.md)
### [Лицензия для развертывания удаленных рабочих столов](rds-client-access-license.md)
#### [Активация сервера лицензирования](rds-activate-license-server.md)
#### [Установка клиентских лицензий служб удаленных рабочих столов на сервере лицензирования](rds-install-cals.md)
#### [Отслеживание клиентских лицензий, используемых в развертывании](rds-track-cals.md)
### [Интеграция со службами Azure](rds-integrate-with-azure.md)
#### [Использование Многофакторной идентификации с RDS](/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway)
#### [Интеграция доменных служб Azure AD со средой RDS](rds-azure-adds.md)
#### [Публикация удаленного рабочего стола с помощью прокси-сервера приложений Azure AD](/azure/active-directory/application-proxy-publish-remote-desktop)
### Расширение среды RDS для обеспечения высокой доступности
#### [Масштабирование существующей коллекции RDS в ферме узлов сеансов удаленных рабочих столов](rds-scale-rdsh-farm.md)
#### [Реализация высокой доступности в инфраструктуре посредника подключений к удаленному рабочему столу](rds-connection-broker-cluster.md)
#### [Реализация высокой доступности в веб-интерфейсе удаленного рабочего стола и веб-интерфейсе шлюза удаленного рабочего стола](rds-rdweb-gateway-ha.md)
#### [Развертывание файловой системы Локальных дисковых пространств с двумя узлами для хранения UPD](rds-storage-spaces-direct-deployment.md)
#### [Развертывание среды рабочих столов на базе личных сеансов и управление ей](rds-personal-session-desktops.md)
#### [Создание виртуальных машин для RDS](rds-prepare-vms.md)
### [Настройка аварийного восстановления для среды RDS](rds-disaster-recovery.md)
#### [Создание географически избыточного развертывания RDS](rds-multi-datacenter-deployment.md)
#### [Настройка Azure Site Recovery для RDS](rds-disaster-recovery-with-azure.md)
##### [Включение аварийного восстановления для компонентов RDS](rds-enable-dr-with-asr.md)
##### [Создание плана аварийного восстановления](rds-disaster-recovery-plan.md)

## [Запуск и настройка](rds-run-and-tune.md)
### [Управление коллекциями сеансов личных рабочих столов](rds-manage-personal-collection.md)
### [Рекомендуемая конфигурация для рабочих столов VDI](rds-vdi-recommendations.md)
### [Оптимизация Windows 10 версии 1909 для роли инфраструктуры виртуальных рабочих столов (VDI)](rds_vdi-recommendations-1909.md)
### [Оптимизация Windows 10 версии 1803 для роли инфраструктуры виртуальных рабочих столов (VDI)](rds-vdi-recommendations-1803.md)
### [Управление пользователями в коллекции RDS](rds-user-management.md)
### [Настройка заголовка "Рабочие ресурсы" для RDS с помощью PowerShell в Windows Server](rds-work-resources.md)
### [Диагностика проблем с производительностью в приложениях с помощью счетчиков производительности](rds-rdsh-performance-counters.md)

## Доступ к материалам по Удаленному рабочему столу
### [Доступные клиенты Удаленного рабочего стола](clients/remote-desktop-clients.md)
### Клиент Удаленного рабочего стола
#### [Приступая к работе с клиентом Удаленного рабочего стола](clients/windowsdesktop.md)
#### [Клиент Удаленного рабочего стола для администраторов](clients/windowsdesktop-admin.md)
#### [Что нового в клиенте Удаленного рабочего стола](clients/windowsdesktop-whatsnew.md)
### Клиент Microsoft Store
#### [Приступая к работе с клиентом Microsoft Store](clients/windows.md)
#### [Что нового в клиенте Microsoft Store?](clients/windows-whatsnew.md)
### Клиент Android
#### [Приступая к работе с клиентом Android](clients/remote-desktop-android.md)
#### [Что нового в клиенте Android?](clients/android-whatsnew.md)
### Клиент iOS
#### [Приступая к работе с клиентом iOS](clients/remote-desktop-ios.md)
#### [Что нового в клиенте iOS?](clients/ios-whatsnew.md)
### Клиент macOS
#### [Приступая к работе с клиентом macOS](clients/remote-desktop-mac.md)
#### [Что нового в клиенте macOS?](clients/mac-whatsnew.md)
### Веб-клиент
#### [Приступая к работе с веб-клиентом](clients/remote-desktop-web-client.md)
#### [Что нового в веб-клиенте?](clients/web-client-whatsnew.md)
### Настройка удаленного рабочего стола на компьютере
#### [Поддерживаемые компьютеры](clients/remote-desktop-supported-config.md)
#### [Предоставление доступа к компьютеру через удаленный рабочий стол](clients/remote-desktop-allow-access.md)
#### [Предоставление доступа к компьютеру за пределами сети](clients/remote-desktop-allow-outside-access.md)
#### [Изменение прослушивающего порта удаленного рабочего стола на вашем компьютере](clients/change-listening-port.md)
### Дополнительные сведения
#### [Сравнение клиентов](clients/remote-desktop-app-compare.md)
#### [Поддерживаемые параметры RDP-файла удаленного рабочего стола](clients/rdp-files.md)
#### [Схема URI удаленного рабочего стола](clients/remote-desktop-uri.md)
#### [Вопросы и ответы по клиенту удаленного рабочего стола](clients/remote-desktop-client-faq.md)
#### [Параметры конфиденциальности для управляемых приложений и настольных компьютеров](clients/remote-privacy-settings.md)
### Известные проблемы
#### [Устранение неполадок с подключениями к удаленному рабочему столу](troubleshoot/rdp-error-general-troubleshooting.md)
#### [Клиенты не могут подключиться и получают сообщение об ошибке "Класс не зарегистрирован"](troubleshoot/rdp-error-class-not-registered.md)
#### [Клиенты не могут подключиться и получают ошибку "Нет доступных лицензий"](troubleshoot/rdp-error-no-licenses-available.md)
#### [Пользователь не может пройти проверку подлинности или проходит ее дважды](troubleshoot/cannot-authenticate-or-must-authenticate-twice.md)
#### [При подключении возникает ошибка "Служба удаленных рабочих столов сейчас занята"](troubleshoot/remote-desktop-service-currently-busy.md)
#### [Клиент удаленного рабочего стола отключается и не может повторно подключиться к тому же сеансу](troubleshoot/rdp-client-disconnects-cannot-reconnect-same-session.md)
#### [Удаленный ноутбук отключается от беспроводной сети](troubleshoot/remote-laptop-disconnects-wireless-network.md)
#### [Низкая производительность или проблемы с приложениями во время подключения к удаленному рабочему столу](troubleshoot/poor-performance-or-application-problems.md)

## [Дополнительные ресурсы](rds-get-support.md)
