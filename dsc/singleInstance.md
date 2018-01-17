---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Tek Örnekli DSC kaynağı (en iyi yöntem) yazma"
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Tek Örnekli DSC kaynağı (en iyi yöntem) yazma

>**Not:** bir yapılandırmada yalnızca tek bir örneğini izin veren bir DSC kaynağı tanımlamak için en iyi uygulama bu konuda açıklanmaktadır. Şu anda, bunu yapmak için yerleşik bir DSC özelliği yoktur. Gelecekte değişebilir.

Birden çok kez yapılandırmasında kullanılması için bir kaynak izin vermek için burada istemediğiniz durumlar vardır. Örneğin, uygulamasında bir önceki [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak, bir yapılandırma çağrısına kaynak birden çok kez, her kaynak bloğundaki farklı bir ayar için saat dilimi ayarını:

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

Bu DSC kaynağı anahtarları çalışması nedeniyle yoludur. Bir kaynak en az bir anahtarı özelliği olması gerekir. Bir kaynak örneği tüm anahtar özelliklerini değerlerin birleşimi benzersiz ise benzersiz olarak kabul edilir. Kendi önceki uygulamasında [xTimeZone](https://github.com/PowerShell/xTimeZone) kaynak sahip yalnızca bir özellik--**saat dilimi**, bir anahtarı olması gereken. Bu nedenle, bir yapılandırma yukarıdakine gibi derleyin ve uyarmadan çalıştırın. Her biri **xTimeZone** kaynak blokları benzersiz olarak değerlendirilir. Bu, saat dilimi İleri ve Geri Dönüşüm düğüme sürekli olarak uygulanması için yapılandırmayı neden olur.

Kaynak ikinci bir özellik eklemek için bir kez güncelleştirildi yalnızca bir yapılandırma bir hedef düğümü için saat dilimi ayarlayabilirsiniz emin olmak için **IsSingleInstance**, anahtar özelliği hale geldi. **IsSingleInstance** tek bir değer için "Evet" kullanarak sınırlı bir **ValueMap**. Kaynak için eski MOF şema oluştu:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Kaynak için güncelleştirilmiş MOF Şeması aşağıdaki gibidir:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Kaynak betik ayrıca yeni bir parametre kullanmak için güncelleştirilmiştir. Eski bir kaynak betik şöyledir:

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

Dikkat **saat dilimi** özelliktir artık bir anahtar. Şimdi, iki kez saat dilimini ayarlamak bir yapılandırma çalışırsa (iki farklı kullanarak **xTimeZone** farklı bloklarla **saat dilimi** değerleri), yapılandırma derleme çalışılırken bir hata neden olur:

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
   
