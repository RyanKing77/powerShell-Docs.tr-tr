---
ms.date: 08/15/2019
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Windows için Istenen durum yapılandırması (DSC) ile çalışmaya başlama
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988931"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Windows için Istenen durum yapılandırması (DSC) ile çalışmaya başlama

Bu konuda, Windows için PowerShell Istenen durum yapılandırması (DSC) ile çalışmaya başlama açıklanmaktadır.
DSC hakkında genel bilgi için bkz. [Windows PowerShell Istenen durum yapılandırmasını kullanmaya başlama](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Desteklenen Windows işletim sistemi sürümleri

Aşağıdaki sürümler desteklenir:

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) tek başına Ürün SKU 'Su istenen durum yapılandırmasına sahip değil, bu nedenle PowerShell DSC veya Azure Otomasyonu durum yapılandırması tarafından yönetilemez.

## <a name="installing-dsc"></a>DSC yükleme

PowerShell Istenen durum Yapılandırması Windows 'a dahil edilmiştir ve Windows Management Framework aracılığıyla güncelleştirilir.
En son sürüm [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)' dir.

> [!NOTE]
> DSC kullanarak bir makineyi yönetmek için ' DSC-Service ' Windows Server özelliğini etkinleştirmeniz gerekmez.
> Bu özellik yalnızca bir Windows çekme sunucusu örneği oluşturulurken gereklidir.

## <a name="using-dsc-for-windows"></a>Windows için DSC kullanma

Aşağıdaki bölümlerde Windows bilgisayarlarda DSC yapılandırmalarının nasıl oluşturulacağı ve çalıştırılacağı açıklanmaktadır.

### <a name="creating-a-configuration-mof-document"></a>Yapılandırma MOF belgesi oluşturma

Windows PowerShell yapılandırma anahtar sözcüğü, bir yapılandırma oluşturmak için kullanılır.
Aşağıdaki adımlarda, Windows PowerShell kullanılarak bir yapılandırma belgesi oluşturma açıklanır.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Bir yapılandırma tanımlayın ve yapılandırma belgesini oluşturun:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>DSC kaynaklarını içeren bir modül yükler

Windows PowerShell Istenen durum yapılandırması, DSC kaynaklarını içeren yerleşik modüller içerir.
PowerShellGet cmdlet 'lerini kullanarak, PowerShell Galerisi gibi dış kaynaklardan modüller de yükleyebilirsiniz.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Yapılandırmayı makineye Uygula

Yapılandırma belgeleri (MOF dosyaları), [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet 'i kullanılarak makineye uygulanabilir.

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Yapılandırmanın geçerli durumunu al

[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet 'i makinenin geçerli durumunu sorgular ve yapılandırmanın geçerli değerlerini döndürür.

`Get-DscConfiguration`

[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet 'i, makineye uygulanan geçerli meta yapılandırmayı döndürür.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Geçerli yapılandırmayı bir makineden kaldır

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Yerel Configuration Manager Ayarları Yapılandır

[Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet 'ini kullanarak makineye meta yapılandırma MOF dosyası uygulayın.
Meta yapılandırma MOF 'nin yolunu gerektirir.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell Istenen durum yapılandırması günlük dosyaları

DSC günlükleri yoldaki `Microsoft-Windows-Dsc/Operational`Windows olay günlüğü 'ne yazılır.
Hata ayıklama amacıyla ek Günlükler, içinde [DSC olay günlüklerinin bulunduğu](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)adımlarda etkinleştirilebilir.
