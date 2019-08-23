---
ms.date: 06/12/2017
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Tek örnekli DSC kaynağı yazma (en iyi uygulama)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986519"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Tek örnekli DSC kaynağı yazma (en iyi uygulama)

>**Not:** Bu konuda, bir yapılandırmada yalnızca tek bir örneğe izin veren bir DSC kaynağı tanımlamak için en iyi yöntem açıklanmaktadır. Şu anda bunu yapmak için yerleşik DSC özelliği yoktur. Bu, gelecekte değişebilir.

Bir yapılandırmada bir kaynağın birden çok kez kullanılmasına izin vermek istemediğiniz durumlar vardır. Örneğin, [Xtimezone](https://github.com/PowerShell/xTimeZone) kaynağının önceki bir uygulamasında, bir yapılandırma kaynağı birden çok kez çağırabilir ve saat dilimini her kaynak bloğunda farklı bir ayara ayarlar:

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

Bunun nedeni, DSC Kaynak anahtarlarının çalışma yoludur. Bir kaynağın en az bir anahtar özelliği olmalıdır. Tüm anahtar özellikleri değerlerinin birleşimi benzersiz ise kaynak örneği benzersiz olarak değerlendirilir. Önceki uygulamada, [Xtimezone](https://github.com/PowerShell/xTimeZone) kaynağında anahtar olması gereken yalnızca bir özellik--**saat dilimi**vardı. Bu nedenle, yukarıdaki gibi bir yapılandırma uyarı vermeden derleyip çalıştırılır. **Xtimezone** kaynak bloklarının her biri benzersiz olarak değerlendirilir. Bu, yapılandırmanın tekrar tekrar, zaman dilimini geriye ve geriye doğru bir şekilde uygulanmasına neden olur.

Bir yapılandırmanın bir hedef düğümün saat dilimini yalnızca bir kez ayarlayamasından emin olmak için, kaynak, anahtar özelliği olan **IsSingleInstance**ikinci bir özelliğini eklemek üzere güncelleştirildi.
**Isingleınstance** , **ValueMap**kullanılarak "Yes" tek bir değerle sınırlandı. Kaynak için eski MOF şeması:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Kaynağın güncelleştirilmiş MOF şeması:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Kaynak betiği de yeni parametreyi kullanacak şekilde güncelleştirildi. Kaynak betiğin nasıl değiştirildiği aşağıda verilmiştir:

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"
    
    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

**TimeZone** özelliğinin artık bir anahtar olmadığına dikkat edin. Artık, bir yapılandırma saat dilimini iki kez ayarlamaya çalışırsa (farklı **saat dilimi** değerleriyle Iki farklı **xtimezone** bloğu kullanarak), yapılandırmayı derlemeye çalışırken bir hata olur:

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
