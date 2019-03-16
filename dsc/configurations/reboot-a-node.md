---
ms.date: 1/17/2019
keywords: DSC, powershell, yapılandırma, Kurulum
title: Düğümü yeniden başlatma
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054739"
---
# <a name="reboot-a-node"></a>Düğümü yeniden başlatma

> [!NOTE]
> Bu konuda, bir düğümü yeniden başlatma hakkında konuşuyor. Başarılı olması için yeniden başlatma için sırayla **ActionAfterReboot** ve **RebootNodeIfNeeded** LCM ayarları doğru şekilde yapılandırılması gerekir.
> Yerel Configuration Manager ayarları hakkında bilgi için bkz [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md), veya [yerel Configuration Manager'ı (v4) yapılandırma](../managing-nodes/metaConfig4.md).

Düğümler yeniden başlatılması gelen bir kaynak içinde kullanarak `$global:DSCMachineStatus` bayrağı. Bu bayrak ayarlayarak `1` içinde `Set-TargetResource` işlevi zorlar düğümü doğrudan sonra yeniden başlatma için LCM'yi **ayarlayın** geçerli kaynak yöntemi. Bu bayrağı kullanarak **xPendingReboot** kaynak algılar bir yeniden başlatmanın bekletilip bekletilmediği DSC dışında.

[Yapılandırmaları](configurations.md) düğümü yeniden başlatmak gerekli adımları gerçekleştirebilir. Bu gibi şeyler içerebilir:

- Windows güncelleştirmeleri
- Yazılım yükleme
- Dosyayı yeniden adlandırır
- Bilgisayarı yeniden adlandırma

**XPendingReboot** kaynak bir yeniden başlatmanın bekletilip bekletilmediği belirlemek için belirli bir bilgisayar konumları denetler. Düğüm, DSC dışında yeniden başlatma gerektiriyorsa **xPendingReboot** kaynak kümeleri `$global:DSCMachineStatus` bayrak `1` bekleyen durumu çözümlemek ve bir yeniden başlatmaya zorlanıyor.

> [!NOTE]
> Bu bayrak ayarlayarak düğümü yeniden başlatma için LCM'yi herhangi bir DSC kaynağı bildirebilirsiniz `Set-TargetResource` işlevi. Daha fazla bilgi için [MOF ile özel bir DSC kaynağı yazma](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sözdizimi

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Özellikler

| Özellik | Açıklama |
| --- | --- |
| Adı| Kaynak yapılandırması içindeki örnek başına benzersiz olmalıdır, gerekli parametre.|
| SkipComponentBasedServicing | Skip yeniden başlatmalar bileşen tabanlı hizmet bileşeni tarafından tetiklendi. |
| SkipWindowsUpdate | Skip yeniden başlatmalar Windows Update tarafından tetiklendi.|
| SkipPendingFileRename | Bekleyen dosya yeniden adlandırma yeniden başlatmalar atlayın. |
| SkipCcmClientSDK | Skip yeniden başlatmalar ConfigMgr istemci tarafından tetiklendi. |
| SkipComputerRename | Bilgisayar tarafından tetiklenen Atla yeniden adlandırır. |
| PSDSCRunAsCredential | V5 desteklenir. Kaynak, belirtilen kullanıcı olarak yürütür. |
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`. Daha fazla bilgi için [DependsOn kullanma](resource-depends-on.md)|

## <a name="example"></a>Örnek

Aşağıdaki örnek, Microsoft Exchange kullanarak yükler [xExchange](https://github.com/PowerShell/xExchange) kaynak.
Yükleme boyunca **xPendingReboot** kaynak düğümü yeniden başlatma için kullanılır.

> [!NOTE]
> Bu örnek, bir Exchange sunucusunun ormana eklemek için haklarına sahip bir hesabın kimlik gerektirir. DSC kimlik bilgilerini kullanarak daha fazla bilgi için bkz: [DSC kimlik bilgilerini işleme](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Bu örnekte, yeniden başlatmalar izin vermek ve bir yeniden başlatma işleminden sonra yapılandırmasına devam etmek için yerel Configuration Manager yapılandırmış olduğunuz varsayılır.

## <a name="where-to-download"></a>Karşıdan yükleme konumu

Bu konuda aşağıdaki konumlarda ya da PowerShell Galerisi kullanılarak tarafından kullanılan kaynakları indirebilirsiniz.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
