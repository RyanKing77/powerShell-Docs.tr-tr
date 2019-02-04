---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Kaynak Tasarımcısı aracını kullanma
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686659"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="260df-103">Kaynak Tasarımcısı aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="260df-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="260df-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="260df-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="260df-105">Kaynak Tasarımcısı araç tarafından kullanıma sunulan cmdlet'leri kümesidir **xDscResourceDesigner** Windows PowerShell Desired State Configuration (DSC) kaynak oluşturmaya kolaylaştırmak modülü.</span><span class="sxs-lookup"><span data-stu-id="260df-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="260df-106">Bu kaynakta yer alan cmdlet'ler MOF şema ve betik modülündeki yeni kaynağınızın dizin yapısı oluşturma yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="260df-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="260df-107">DSC kaynakları hakkında daha fazla bilgi için bkz. [yapı özel Windows PowerShell Desired State Configuration kaynaklarını](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="260df-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="260df-108">Bu konuda, Active Directory Kullanıcıları yöneten bir DSC kaynağı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="260df-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="260df-109">Kullanım [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xDscResourceDesigner** modülü.</span><span class="sxs-lookup"><span data-stu-id="260df-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="260df-110">**Not**: **Install-Module** dahil **PowerShellGet** modülü, PowerShell 5. 0'da dahildir.</span><span class="sxs-lookup"><span data-stu-id="260df-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="260df-111">İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="260df-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="260df-112">Kaynak özellikleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="260df-112">Creating resource properties</span></span>
<span data-ttu-id="260df-113">Yapmamız gereken ilk şey, kaynak açığa çıkarır özelliklerde karar ' dir.</span><span class="sxs-lookup"><span data-stu-id="260df-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="260df-114">Bu örnekte, biz aşağıdaki özelliklere sahip bir Active Directory kullanıcı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="260df-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="260df-115">Parametre adı açıklaması</span><span class="sxs-lookup"><span data-stu-id="260df-115">Parameter name  Description</span></span>
* <span data-ttu-id="260df-116">**Kullanıcı adı**: Kullanıcının benzersiz olarak tanımlayan anahtar özelliği.</span><span class="sxs-lookup"><span data-stu-id="260df-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="260df-117">**Olun**: Kullanıcı hesabının geçerli olup olmayacağını veya Absent belirtir.</span><span class="sxs-lookup"><span data-stu-id="260df-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="260df-118">Bu parametre, yalnızca iki olası değerlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="260df-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="260df-119">**DomainCredential**: Etki alanı kullanıcı parolası.</span><span class="sxs-lookup"><span data-stu-id="260df-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="260df-120">**Parola**: Gerekirse, kullanıcı parolasını değiştirmek bir yapılandırma izin vermek kullanıcı için istenilen parola.</span><span class="sxs-lookup"><span data-stu-id="260df-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="260df-121">Özellikler oluşturmak için kullandığımız **yeni xDscResourceProperty** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="260df-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="260df-122">Aşağıdaki PowerShell komutlarını yukarıda açıklanan özellikler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="260df-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="260df-123">Kaynak Oluştur</span><span class="sxs-lookup"><span data-stu-id="260df-123">Create the resource</span></span>

<span data-ttu-id="260df-124">Kaynak özellikleri oluşturulan, biz çağırabilirsiniz **yeni xDscResource** kaynak oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="260df-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="260df-125">**Yeni xDscResource** cmdlet parametreleri olarak özelliklerinin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="260df-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="260df-126">Ayrıca, modül nerede oluşturulması gereken yolu, yeni kaynak adı ve yer modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="260df-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="260df-127">Aşağıdaki PowerShell komutunu kaynak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="260df-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="260df-128">**Yeni xDscResource** cmdlet'i MOF şema, çatı kaynak betiği, yeni kaynak için gerekli bir dizin yapısı ve yeni kaynak sunan modülü için bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="260df-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="260df-129">MOF şema dosyası altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, ve içeriğini aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="260df-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="260df-130">Kaynak betiği altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="260df-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="260df-131">Kendiniz eklemeniz gerekir kaynak uygulamak için fiili mantığı içermez.</span><span class="sxs-lookup"><span data-stu-id="260df-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="260df-132">İskelet komut dosyasının içeriğini aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="260df-132">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="260df-133">Kaynak güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="260df-133">Updating the resource</span></span>

<span data-ttu-id="260df-134">Eklediğinizde veya değiştirdiğinizde kaynak parametre listesini gerekiyorsa çağırabilirsiniz **güncelleştirme xDscResource** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="260df-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="260df-135">Cmdlet'i yeni bir parametre listesiyle kaynak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="260df-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="260df-136">Kaynak kodunuzu zaten mantıksal eklediyseniz, olduğu gibi bırakılır.</span><span class="sxs-lookup"><span data-stu-id="260df-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="260df-137">Örneğin, son günlüğü bizim kaynak kullanıcı için zaman dahil etmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="260df-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="260df-138">Kaynak tamamen yeniden yazmak yerine, çağırabilirsiniz **yeni xDscResourceProperty** yeni bir özellik oluşturmak ve ardından çağırmak için **güncelleştirme xDscResource** ve yeni özelliğinizi ekleyin özellikler listesi.</span><span class="sxs-lookup"><span data-stu-id="260df-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="260df-139">Bir kaynak şema test etme</span><span class="sxs-lookup"><span data-stu-id="260df-139">Testing a resource schema</span></span>

<span data-ttu-id="260df-140">Kaynak Tasarımcısı aracını el ile yazılmış bir MOF şema geçerliliğini sınamak için kullanılan bir daha fazla cmdlet kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="260df-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="260df-141">Çağrı **Test xDscSchema** cmdlet'i, bir parametre olarak bir MOF kaynak şema yolunu geçirerek.</span><span class="sxs-lookup"><span data-stu-id="260df-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="260df-142">Şema hataları cmdlet çıktı olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="260df-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="260df-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="260df-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="260df-144">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="260df-144">Concepts</span></span>
[<span data-ttu-id="260df-145">Derleme özel Windows PowerShell Desired State Configuration kaynakları</span><span class="sxs-lookup"><span data-stu-id="260df-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="260df-146">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="260df-146">Other Resources</span></span>
[<span data-ttu-id="260df-147">xDscResourceDesigner Modülü</span><span class="sxs-lookup"><span data-stu-id="260df-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
