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
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="8166d-103">Tek örnekli DSC kaynağı yazma (en iyi uygulama)</span><span class="sxs-lookup"><span data-stu-id="8166d-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="8166d-104">**Not:** Bu konuda, bir yapılandırmada yalnızca tek bir örneğe izin veren bir DSC kaynağı tanımlamak için en iyi yöntem açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8166d-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="8166d-105">Şu anda bunu yapmak için yerleşik DSC özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="8166d-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="8166d-106">Bu, gelecekte değişebilir.</span><span class="sxs-lookup"><span data-stu-id="8166d-106">That might change in the future.</span></span>

<span data-ttu-id="8166d-107">Bir yapılandırmada bir kaynağın birden çok kez kullanılmasına izin vermek istemediğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="8166d-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="8166d-108">Örneğin, [Xtimezone](https://github.com/PowerShell/xTimeZone) kaynağının önceki bir uygulamasında, bir yapılandırma kaynağı birden çok kez çağırabilir ve saat dilimini her kaynak bloğunda farklı bir ayara ayarlar:</span><span class="sxs-lookup"><span data-stu-id="8166d-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="8166d-109">Bunun nedeni, DSC Kaynak anahtarlarının çalışma yoludur.</span><span class="sxs-lookup"><span data-stu-id="8166d-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="8166d-110">Bir kaynağın en az bir anahtar özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8166d-110">A resource must have at least one key property.</span></span> <span data-ttu-id="8166d-111">Tüm anahtar özellikleri değerlerinin birleşimi benzersiz ise kaynak örneği benzersiz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8166d-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="8166d-112">Önceki uygulamada, [Xtimezone](https://github.com/PowerShell/xTimeZone) kaynağında anahtar olması gereken yalnızca bir özellik--**saat dilimi**vardı.</span><span class="sxs-lookup"><span data-stu-id="8166d-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="8166d-113">Bu nedenle, yukarıdaki gibi bir yapılandırma uyarı vermeden derleyip çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8166d-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="8166d-114">**Xtimezone** kaynak bloklarının her biri benzersiz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8166d-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="8166d-115">Bu, yapılandırmanın tekrar tekrar, zaman dilimini geriye ve geriye doğru bir şekilde uygulanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8166d-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="8166d-116">Bir yapılandırmanın bir hedef düğümün saat dilimini yalnızca bir kez ayarlayamasından emin olmak için, kaynak, anahtar özelliği olan **IsSingleInstance**ikinci bir özelliğini eklemek üzere güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="8166d-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="8166d-117">**Isingleınstance** , **ValueMap**kullanılarak "Yes" tek bir değerle sınırlandı.</span><span class="sxs-lookup"><span data-stu-id="8166d-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="8166d-118">Kaynak için eski MOF şeması:</span><span class="sxs-lookup"><span data-stu-id="8166d-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="8166d-119">Kaynağın güncelleştirilmiş MOF şeması:</span><span class="sxs-lookup"><span data-stu-id="8166d-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="8166d-120">Kaynak betiği de yeni parametreyi kullanacak şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="8166d-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="8166d-121">Kaynak betiğin nasıl değiştirildiği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8166d-121">Here how the resource script was changed:</span></span>

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

<span data-ttu-id="8166d-122">**TimeZone** özelliğinin artık bir anahtar olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8166d-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="8166d-123">Artık, bir yapılandırma saat dilimini iki kez ayarlamaya çalışırsa (farklı **saat dilimi** değerleriyle Iki farklı **xtimezone** bloğu kullanarak), yapılandırmayı derlemeye çalışırken bir hata olur:</span><span class="sxs-lookup"><span data-stu-id="8166d-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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
