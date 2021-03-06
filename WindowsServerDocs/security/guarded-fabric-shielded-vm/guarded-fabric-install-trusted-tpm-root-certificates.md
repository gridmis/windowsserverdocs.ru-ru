---
title: Установка доверенных корневых сертификатов доверенного платформенного модуля
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 06/27/2019
ms.openlocfilehash: 15614ce1065170bc557fad10a168b3dda6a5b05a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386546"
---
# <a name="install-trusted-tpm-root-certificates"></a>Установка доверенных корневых сертификатов доверенного платформенного модуля

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

При настройке HGS для использования аттестации TPM необходимо также настроить HGS, чтобы доверять поставщикам доверенных платформенных модулей на серверах.
Этот дополнительный процесс проверки гарантирует, что только исдлинные доверенные платформенные модули смогут подтверждать работу с HGS.
При попытке зарегистрировать недоверенный доверенный платформенный модуль с `Add-HgsAttestationTpmHost` вы получите сообщение об ошибке, указывающее, что поставщик доверенного платформенного модуля не является доверенным.

Чтобы доверять доверенным платформенным модулям, необходимо установить корневой и промежуточный сертификаты подписи, используемые для подписывания ключа подтверждения в доверенных платформенных модулях серверов, в службе HGS.
Если в центре обработки данных используется более одной модели TPM, может потребоваться установить разные сертификаты для каждой модели.
HGS будет смотреть хранилища сертификатов "TrustedTPM_RootCA" и "TrustedTPM_IntermediateCA" для сертификатов поставщика.

> [!NOTE]
> Сертификаты поставщика TPM отличаются от сертификатов, установленных по умолчанию в Windows, и представляют конкретные корневые и промежуточные сертификаты, используемые поставщиками TPM.

Коллекция доверенных корневых и промежуточных сертификатов доверенного платформенного модуля публикуется корпорацией Майкрософт для вашего удобства.
Для установки этих сертификатов можно использовать следующие шаги.
Если Сертификаты доверенного платформенного модуля не включены в указанный ниже пакет, обратитесь к поставщику доверенного платформенного модуля или к ИЗГОТОВИТЕЛю сервера, чтобы получить корневые и промежуточные сертификаты для конкретной модели доверенного платформенного модуля.

Повторите следующие шаги на **каждом сервере HGS**.

1.  Скачайте последнюю версию пакета с [https://go.microsoft.com/fwlink/?linkid=2097925](https://go.microsoft.com/fwlink/?linkid=2097925).

2.  Проверьте подпись CAB-файла, чтобы убедиться в его подлинности. Не продолжайте, если подпись недействительна.

    ```powershell
    Get-AuthenticodeSignature .\TrustedTpm.cab
    ```
    
    Вот пример выходных данных:
    
    ```
    Directory: C:\Users\Administrator\Downloads
        
    SignerCertificate                         Status                                 Path
    -----------------                         ------                                 ----
    0DD6D4D4F46C0C7C2671962C4D361D607E370940  Valid                                  TrustedTpm.cab
    ```

2.  Разверните CAB-файл.

    ```
    mkdir .\TrustedTPM
    expand.exe -F:* <Path-To-TrustedTpm.cab> .\TrustedTPM
    ```

3.  По умолчанию скрипт конфигурации установит сертификаты для каждого поставщика TPM. Если требуется импортировать сертификаты только для конкретного поставщика доверенного платформенного модуля, удалите папки для поставщиков доверенного платформенного модуля, которые не являются доверенными для вашей организации.

4.  Установите пакет доверенных сертификатов, запустив сценарий установки в развернутой папке.

    ```
    cd .\TrustedTPM
    .\setup.cmd
    ```

Чтобы добавить новые сертификаты или объекты, которые преднамеренно пропущены во время предыдущей установки, просто повторите описанные выше действия на каждом узле в кластере HGS.
Существующие сертификаты останутся доверенными, но новые сертификаты, найденные в расширенном CAB-файле, будут добавлены в доверенные хранилища TPM.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Настройка DNS структуры](guarded-fabric-configuring-fabric-dns-tpm.md)



