---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Tek örnekli DSC kaynağı yazma (en iyi uygulama)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="81cf3-103">Tek örnekli DSC kaynağı yazma (en iyi uygulama)</span><span class="sxs-lookup"><span data-stu-id="81cf3-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="81cf3-104">**Not:** bir yapılandırmada yalnızca tek bir örneğini izin veren bir DSC kaynağı tanımlamak için en iyi uygulama bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81cf3-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="81cf3-105">Şu anda, bunu yapmak için yerleşik bir DSC özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="81cf3-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="81cf3-106">Gelecekte değişebilir.</span><span class="sxs-lookup"><span data-stu-id="81cf3-106">That might change in the future.</span></span>

<span data-ttu-id="81cf3-107">Birden çok kez yapılandırmasında kullanılması için bir kaynak izin vermek için burada istemediğiniz durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="81cf3-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="81cf3-108">Örneğin, uygulamasında bir önceki [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak, bir yapılandırma çağrısına kaynak birden çok kez, her kaynak bloğundaki farklı bir ayar için saat dilimi ayarını:</span><span class="sxs-lookup"><span data-stu-id="81cf3-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="81cf3-109">Bu DSC kaynağı anahtarları çalışması nedeniyle yoludur.</span><span class="sxs-lookup"><span data-stu-id="81cf3-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="81cf3-110">Bir kaynak en az bir anahtarı özelliği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="81cf3-110">A resource must have at least one key property.</span></span> <span data-ttu-id="81cf3-111">Bir kaynak örneği tüm anahtar özelliklerini değerlerin birleşimi benzersiz ise benzersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="81cf3-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="81cf3-112">Kendi önceki uygulamasında [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak sahip yalnızca bir özellik--**saat dilimi**, bir anahtarı olması gereken.</span><span class="sxs-lookup"><span data-stu-id="81cf3-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="81cf3-113">Bu nedenle, bir yapılandırma yukarıdakine gibi derleyin ve uyarmadan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="81cf3-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="81cf3-114">Her biri **xTimeZone** kaynak blokları benzersiz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="81cf3-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="81cf3-115">Bu, saat dilimi İleri ve Geri Dönüşüm düğüme sürekli olarak uygulanması için yapılandırmayı neden olur.</span><span class="sxs-lookup"><span data-stu-id="81cf3-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="81cf3-116">Kaynak ikinci bir özellik eklemek için bir kez güncelleştirildi yalnızca bir yapılandırma bir hedef düğümü için saat dilimi ayarlayabilirsiniz emin olmak için **IsSingleInstance**, anahtar özelliği hale geldi.</span><span class="sxs-lookup"><span data-stu-id="81cf3-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="81cf3-117">**IsSingleInstance** tek bir değer için "Evet" kullanarak sınırlı bir **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="81cf3-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="81cf3-118">Kaynak için eski MOF şema oluştu:</span><span class="sxs-lookup"><span data-stu-id="81cf3-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="81cf3-119">Kaynak için güncelleştirilmiş MOF Şeması aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="81cf3-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="81cf3-120">Kaynak betik ayrıca yeni bir parametre kullanmak için güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="81cf3-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="81cf3-121">Eski bir kaynak betik şöyledir:</span><span class="sxs-lookup"><span data-stu-id="81cf3-121">Here is the old resource script:</span></span>

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

<span data-ttu-id="81cf3-122">Dikkat **saat dilimi** özelliktir artık bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="81cf3-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="81cf3-123">Şimdi, iki kez saat dilimini ayarlamak bir yapılandırma çalışırsa (iki farklı kullanarak **xTimeZone** farklı bloklarla **saat dilimi** değerleri), yapılandırma derleme çalışılırken bir hata neden olur:</span><span class="sxs-lookup"><span data-stu-id="81cf3-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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