---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Kaynak Tasarımcısı aracını kullanma
ms.openlocfilehash: 3dc03adefa71eadc5e80532fdeaaa0e0388e6dce
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="24010-103">Kaynak Tasarımcısı aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="24010-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="24010-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24010-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="24010-105">Kaynak Tasarımcısı aracı tarafından sunulan cmdlet'leri kümesidir **xDscResourceDesigner** oluşturma Windows PowerShell istenen durum yapılandırması (DSC) kaynakları kolaylaştırmak modülü.</span><span class="sxs-lookup"><span data-stu-id="24010-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="24010-106">Bu kaynak Cmdlet'lerde MOF şema, betik modülündeki ve yeni kaynak dizin yapısı oluşturmaya yardımcı olmak.</span><span class="sxs-lookup"><span data-stu-id="24010-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="24010-107">DSC kaynakları hakkında daha fazla bilgi için bkz: [yapı özel Windows PowerShell istenen durum yapılandırması kaynaklarını](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="24010-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="24010-108">Bu konuda, Active Directory Kullanıcıları yönetir DSC kaynağı oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="24010-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="24010-109">Kullanım [yükleme-Module](https://technet.microsoft.com/library/dn807162.aspx) yüklemek için cmdlet'i **xDscResourceDesigner** modülü.</span><span class="sxs-lookup"><span data-stu-id="24010-109">Use the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="24010-110">**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü.</span><span class="sxs-lookup"><span data-stu-id="24010-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="24010-111">İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="24010-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="24010-112">Kaynak özellikleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="24010-112">Creating resource properties</span></span>
<span data-ttu-id="24010-113">Yapmamız gereken ilk şey, kaynak açığa çıkarır özelliklerinde karar ' dir.</span><span class="sxs-lookup"><span data-stu-id="24010-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="24010-114">Bu örnekte, biz aşağıdaki özelliklere sahip bir Active Directory kullanıcı tanımlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="24010-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="24010-115">Parametre adı açıklaması</span><span class="sxs-lookup"><span data-stu-id="24010-115">Parameter name  Description</span></span>
* <span data-ttu-id="24010-116">**Kullanıcı adı**: anahtarı bir kullanıcı olarak tanıtan özelliği.</span><span class="sxs-lookup"><span data-stu-id="24010-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="24010-117">**Olun**: kullanıcı hesabı yoksa mi olacağını Absent belirtir.</span><span class="sxs-lookup"><span data-stu-id="24010-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="24010-118">Bu parametre yalnızca iki olası değerlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="24010-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="24010-119">**DomainCredential**: kullanıcı için etki alanı parolası.</span><span class="sxs-lookup"><span data-stu-id="24010-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="24010-120">**Parola**: gerekirse, kullanıcı parolasını değiştirmek bir yapılandırma izin vermek kullanıcı için istenen parola.</span><span class="sxs-lookup"><span data-stu-id="24010-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="24010-121">Özellikleri oluşturmak için kullanırız **yeni xDscResourceProperty** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="24010-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="24010-122">Aşağıdaki PowerShell komutları yukarıda açıklanan özellikleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24010-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="24010-123">Kaynak oluşturma</span><span class="sxs-lookup"><span data-stu-id="24010-123">Create the resource</span></span>

<span data-ttu-id="24010-124">Kaynak özelliklerini oluşturulan, biz çağırabilirsiniz **yeni xDscResource** kaynağı oluşturmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="24010-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="24010-125">**Yeni xDscResource** cmdlet'i parametre olarak özelliklerinin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="24010-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="24010-126">Ayrıca modülü nerede oluşturulacağını yolu, yeni kaynak adının ve yer modülünün adını alır.</span><span class="sxs-lookup"><span data-stu-id="24010-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="24010-127">Aşağıdaki PowerShell komutunu kaynağı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24010-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="24010-128">**Yeni xDscResource** cmdlet'i, MOF şeması, bir iskelet kaynak komut dosyası, yeni kaynak için gerekli dizin yapısını ve yeni kaynak sunan modülü bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24010-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="24010-129">MOF şema dosyası altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, ve içeriğini aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="24010-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="24010-130">Kaynak betik altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="24010-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="24010-131">Kendiniz eklemeniz gerekir kaynak uygulamak için gerçek mantığı içermez.</span><span class="sxs-lookup"><span data-stu-id="24010-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="24010-132">İskelet komut dosyasının içeriğini aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="24010-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="24010-133">Kaynak güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="24010-133">Updating the resource</span></span>

<span data-ttu-id="24010-134">Eklemek veya kaynak parametre listesini değiştirmek gerekiyorsa, çağırabilirsiniz **güncelleştirme xDscResource** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="24010-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="24010-135">Cmdlet kaynak ile yeni bir parametre listesini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="24010-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="24010-136">Kaynak kodunuzu mantığı zaten eklediyseniz, olduğu gibi bırakılır.</span><span class="sxs-lookup"><span data-stu-id="24010-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="24010-137">Örneğin, son günlüğü bizim kaynak kullanıcı için zaman dahil etmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="24010-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="24010-138">Kaynak tamamen yeniden yazmak yerine çağırabilirsiniz **yeni xDscResourceProperty** yeni özellik oluşturmak ve ardından arama **güncelleştirme xDscResource** ve yeni özelliğinizi ekleyin özellikler listesi.</span><span class="sxs-lookup"><span data-stu-id="24010-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="24010-139">Bir kaynak şema test etme</span><span class="sxs-lookup"><span data-stu-id="24010-139">Testing a resource schema</span></span>

<span data-ttu-id="24010-140">Kaynak Tasarımcısı aracını el ile yazılmış bir MOF şema geçerliliğini sınamak için kullanılan bir daha fazla cmdlet kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="24010-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="24010-141">Çağrı **Test xDscSchema** cmdlet, bir MOF kaynak şema yolunu parametre olarak geçirme.</span><span class="sxs-lookup"><span data-stu-id="24010-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="24010-142">Cmdlet'i şemayı hatalarını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="24010-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="24010-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="24010-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="24010-144">Kavramlar</span><span class="sxs-lookup"><span data-stu-id="24010-144">Concepts</span></span>
[<span data-ttu-id="24010-145">Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma</span><span class="sxs-lookup"><span data-stu-id="24010-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="24010-146">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="24010-146">Other Resources</span></span>
[<span data-ttu-id="24010-147">xDscResourceDesigner Modülü</span><span class="sxs-lookup"><span data-stu-id="24010-147">xDscResourceDesigner Module</span></span>](https://powershellgallery.com/packages/xDscResourceDesigner)