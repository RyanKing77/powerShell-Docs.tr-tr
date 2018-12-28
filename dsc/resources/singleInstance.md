---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Tek örnekli DSC kaynağı yazma (en iyi uygulama)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405898"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="4e578-103">Tek örnekli DSC kaynağı yazma (en iyi uygulama)</span><span class="sxs-lookup"><span data-stu-id="4e578-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="4e578-104">**Not:** Bu konu, yalnızca tek bir örnek bir yapılandırma sağlayan bir DSC kaynağı tanımlamak için en iyi uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e578-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="4e578-105">Şu anda, bunu yapmak için yerleşik bir DSC özelliğini yoktur.</span><span class="sxs-lookup"><span data-stu-id="4e578-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="4e578-106">Bu gelecekte değişebilir.</span><span class="sxs-lookup"><span data-stu-id="4e578-106">That might change in the future.</span></span>

<span data-ttu-id="4e578-107">Burada bir yapılandırmada birden çok kez kullanılacak bir kaynağa izin vermenin istemediğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="4e578-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="4e578-108">Örneğin, bir önceki uygulaması içinde [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak, bir yapılandırma çağrı kaynak birden çok kez, her kaynak blok içinde farklı bir ayar için saat dilimini ayarlamak:</span><span class="sxs-lookup"><span data-stu-id="4e578-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="4e578-109">DSC kaynak anahtarlarını çalışma şekli nedeniyle budur.</span><span class="sxs-lookup"><span data-stu-id="4e578-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="4e578-110">Bir kaynak en az bir anahtarı özelliği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e578-110">A resource must have at least one key property.</span></span> <span data-ttu-id="4e578-111">Bir kaynak örneği tüm anahtar özelliklerinin değerlerinin bileşimi benzersiz olması durumunda benzersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="4e578-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="4e578-112">Kendi önceki uygulamasında [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak olduğu tek özelliği--**saat dilimi**, bir anahtar olması için gerekli.</span><span class="sxs-lookup"><span data-stu-id="4e578-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="4e578-113">Bu nedenle, yukarıdaki gibi bir yapılandırma derleyin ve uyarı olmadan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e578-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="4e578-114">Her biri **xTimeZone** kaynak bloklar benzersiz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4e578-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="4e578-115">Bu, saat dilimi İleri ve Geri Dönüşüm düğüme sürekli olarak uygulanacak yapılandırma neden olur.</span><span class="sxs-lookup"><span data-stu-id="4e578-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="4e578-116">Kaynak ikinci bir özellik eklemek için bir kez güncelleştirildi yalnızca bir yapılandırma bir hedef düğüm için saat dilimini ayarlayabilirsiniz emin olmak için **IsSingleInstance**, anahtar özelliği hale geldi.</span><span class="sxs-lookup"><span data-stu-id="4e578-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="4e578-117">**IsSingleInstance** tek bir değer için "Evet" kullanarak sınırlı bir **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="4e578-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="4e578-118">Kaynak için eski MOF şema şöyleydi:</span><span class="sxs-lookup"><span data-stu-id="4e578-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="4e578-119">Kaynak için güncelleştirilmiş MOF Şeması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4e578-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="4e578-120">Kaynak betiği ayrıca yeni bir parametre kullanmak için güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="4e578-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="4e578-121">Eski kaynak betiği şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="4e578-121">Here is the old resource script:</span></span>

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
    [CmdletBinding(SupportsShouldProcess=$true)]
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

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
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

<span data-ttu-id="4e578-122">Dikkat **saat dilimi** özellik olup artık bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="4e578-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="4e578-123">Şimdi, iki kez saat dilimini ayarlamak bir yapılandırma çalışırsa (iki farklı kullanarak **xTimeZone** farklı bloklar **saat dilimi** değerler), yapılandırmayı derlemek çalışılırken bir hata neden olur:</span><span class="sxs-lookup"><span data-stu-id="4e578-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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