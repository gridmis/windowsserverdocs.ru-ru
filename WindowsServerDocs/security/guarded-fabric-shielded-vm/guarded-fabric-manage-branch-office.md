---
title: Рекомендации для филиалов
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.openlocfilehash: 5a07553e6662fd79230d566ba2049c5e8997f4d6
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79322506"
---
# <a name="branch-office-considerations"></a>Рекомендации для филиалов

> Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), 

В этой статье описываются рекомендации по запуску экранированных виртуальных машин в филиалах и других удаленных сценариях, где узлы Hyper-V могут иметь периоды времени с ограниченным подключением к HGS.

## <a name="fallback-configuration"></a>Конфигурация отката

Начиная с Windows Server версии 1709, можно настроить дополнительный набор URL-адресов службы защиты узлов на узлах Hyper-V для использования в случае, если основная служба HGS не отвечает.
Это позволяет запускать локальный кластер HGS, используемый в качестве сервера-источника, для повышения производительности с возможностью возврата к HGS в вашем корпоративном центре обработки данных, если локальные серверы не работают.

Чтобы использовать резервный вариант, необходимо настроить два сервера HGS. Они могут работать под управлением Windows Server 2019 или Windows Server 2016, либо входить в состав одних и тех же или разных кластеров. Если это разные кластеры, необходимо будет установить операционные методы, чтобы обеспечить синхронизацию политик аттестации между двумя серверами. Они должны иметь возможность правильно авторизовать узел Hyper-V для запуска экранированных виртуальных машин и получить ключевой материал для запуска экранированных виртуальных машин. Вы можете использовать пару общих сертификатов шифрования и подписи между двумя кластерами или воспользоваться отдельными сертификатами и настроить экранированную виртуальную машину HGS, чтобы авторизовать обе защиты (пары сертификатов шифрования и подписи) в файле данных экранирования.

Затем обновите узлы Hyper-V до Windows Server версии 1709 или Windows Server 2019 и выполните следующую команду:
```powershell
# Replace https://hgs.primary.com and https://hgs.backup.com with your own domain names and protocols
Set-HgsClientConfiguration -KeyProtectionServerUrl 'https://hgs.primary.com/KeyProtection' -AttestationServerUrl 'https://hgs.primary.com/Attestation' -FallbackKeyProtectionServerUrl 'https://hgs.backup.com/KeyProtection' -FallbackAttestationServerUrl 'https://hgs.backup.com/Attestation'
```

Чтобы отменить настройку резервного сервера, просто опустите оба параметра:
```powershell
Set-HgsClientConfiguration -KeyProtectionServerUrl 'https://hgs.primary.com/KeyProtection' -AttestationServerUrl 'https://hgs.primary.com/Attestation'
```

Чтобы узел Hyper-V мог передать аттестацию как на основном, так и на резервном сервере, необходимо убедиться, что данные аттестации актуальны для обеих кластеров HGS.
Кроме того, сертификаты, используемые для расшифровки доверенного платформенного модуля виртуальной машины, должны быть доступны в обеих кластерах HGS.
Вы можете настроить каждый HGS с разными сертификатами и настроить виртуальную машину для доверия в обоих случаях или добавить общий набор сертификатов в оба кластера HGS.

Дополнительные сведения о настройке HGS в филиале с помощью URL-адресов резервных узлов см. в записи блога [улучшена поддержка филиалов для экранированных виртуальных машин в Windows Server версии 1709](https://blogs.technet.microsoft.com/datacentersecurity/2017/11/15/improved-branch-office-support-for-shielded-vms-in-windows-server-version-1709/).


## <a name="offline-mode"></a>Автономный режим

Автономный режим позволяет экранированной виртуальной машине включать в случае недоступности HGS, если конфигурация безопасности узла Hyper-V не изменилась.
Автономный режим работает путем кэширования специальной версии предохранителя ключа TPM виртуальной машины на узле Hyper-V.
Предохранитель ключа шифруется в соответствии с текущей конфигурацией безопасности узла (с помощью ключа удостоверения безопасности на основе виртуализации).
Если узлу не удается связаться с HGS, а его конфигурация безопасности не изменилась, она сможет использовать для запуска экранированной виртуальной машины предохранитель ключа с кэшированием.
При изменении параметров безопасности в системе, например при применении новой политики целостности кода или отключенной безопасной загрузки, предохранители кэшированных ключей станут недействительными, и узел должен будет подтвердить свою работу с HGS, прежде чем все экранированные виртуальные машины можно будет снова запустить в автономном режиме.

Для автономного режима требуется Windows Server Insider Preview Build 17609 или более поздней версии для кластера службы защиты узла и узла Hyper-V.
Он управляется политикой HGS, которая по умолчанию отключена.
Чтобы включить поддержку автономного режима, выполните следующую команду в узле HGS:

```powershell
Set-HgsKeyProtectionConfiguration -AllowKeyMaterialCaching:$true
```

Так как предохранители ключей, поддерживающие кэширование, уникальны для каждой экранированной виртуальной машины, необходимо полностью завершить работу (не перезапускать) и запустить экранированные виртуальные машины, чтобы получить предохранитель ключа с возможностью кэширования после включения этого параметра в HGS.
Если экранированная виртуальная машина переносится на узел Hyper-V под управлением более старой версии Windows Server или получает новый предохранитель ключа из более старой версии HGS, он не сможет запуститься в автономном режиме, но может продолжать работать в режиме «в сети», когда доступ к службе HGS имеющ.
