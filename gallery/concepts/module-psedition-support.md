---
ms.date: 03/28/2019
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Modülleri ile uyumlu PowerShell sürümleri
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623849"
---
# <a name="modules-with-compatible-powershell-editions"></a>Modülleri ile uyumlu PowerShell sürümleri

Sürüm 5.1’den başlayarak, PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümler halinde sağlanır.

- **Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş, hem Windows Masaüstü, Windows Server, Windows Sunucu Çekirdeği ve çoğu Windows sürümleri üzerinde Windows PowerShell 5.1, Windows PowerShell v4.0 ve aşağıda geçerlidir.
- **Çekirdek sürümü:** .NET Core üzerine yapılandırılan, PowerShell Core 6.0 ve üzeri, Windows PowerShell 5.1 yanı sıra kapladığı alanın azaltılmış olması Windows IOT ve Windows Nanoserver gibi Windows sürümleri üzerinde geçerlidir.

PowerShell sürümleri hakkında daha fazla bilgi için bkz. [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Uyumlu sürümleri bildirme

Modül yazarları CompatiblePSEditions modül bildirim anahtarını kullanarak kendi modüllerinin bir veya birden çok PowerShell sürümüyle uyumlu olduğunu bildirebilir. Bu anahtar yalnızca PowerShell 5.1 veya üstünde desteklenir.

> [!NOTE]
> Bir modül bildirimi CompatiblePSEditions anahtarla belirlendikten sonra PowerShell sürüm 4 ve aşağıdaki içeri aktarılamıyor.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Kullanılabilir modüllerin listesini alırken, listeyi PowerShell sürümüne göre filtreleyebilirsiniz.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Birden çok sürümü hedefleme

Modül yazarları, tek bir modül hedefleme veya her ikisi de PowerShell sürümleri için (Masaüstü ve çekirdek) yayımlayabilirsiniz.

Tek bir modül, hem Masaüstü hem de çekirdek sürümleri üzerinde çalışabilir, ya da RootModule veya $PSEdition değişkenini kullanarak modül bildirimindeki gerekli mantığı eklemek, yazarın Bu modülde olur. Modüller, CoreCLR hem FullCLR hedefleyen derlenen DLL'leri iki kümesi olabilir. Birkaç seçeneğiniz modülünüzde uygun DLL'leri yükleme için mantığı paketlemek için aşağıda verilmiştir.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Seçenek 1: Bir modülün birden çok sürümü ve birden çok PowerShell sürümü hedeflemek için paketleme

Modül klasör içeriği

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

PSScriptAnalyzer.psd1 dosyasının içeriği

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Mantıksal geçerli sürümü veya bağlı olarak gerekli bütünleştirilmiş kodları yükler.

PSScriptAnalyzer.psm1 dosyasının içeriği:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>2. Seçenek: $PSEdition değişkeni PSD1 dosyası içinde uygun DLL'ler ve iç içe geçmiş ve gerekli modülleri yüklemek için kullanın.

PS 5.1 veya yeni, $PSEdition genel değişkeni modül bildirim dosyasında izin verilir. Bu değişkeni kullanarak, modül yazarına modül bildirim dosyasında koşullu değerleri belirtebilirsiniz. Kısıtlı dil modu veya veri bölümündeki $PSEdition değişkeni başvurulabilir.

> [!NOTE]
> Bir modül bildirimi CompatiblePSEditions anahtarı ile belirtilen ya da kullanıyorsa sonra `$PSEdition` değişken, daha düşük PowerShell sürümlerinde içeri aktarılamıyor.

Örnek modülü bildirim dosyası CompatiblePSEditions anahtarı

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a>Modül içeriği

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

PowerShell Galerisi kullanıcılar etiketleri PSEdition_Desktop ve PSEdition_Core kullanarak belirli bir PowerShell sürümünde desteklenen modüllerin listesini bulabilirsiniz.

PSEdition_Desktop ve PSEdition_Core etiketleri olmadan modülleri PowerShell Masaüstü sürümleri için üzerinde sorunsuz çalışacak şekilde değerlendirilir.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Daha fazla ayrıntı

[PSEditions’ı olan Betikler](script-psedition-support.md)

[PowerShellGallery pseditions'ı desteği](../how-to/finding-packages/searching-by-compatibility.md)

[Modül bildirimini güncelleştir](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
