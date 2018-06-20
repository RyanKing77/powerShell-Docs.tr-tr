---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Kaynak Tasarımcısı aracını kullanma
ms.openlocfilehash: 3dc03adefa71eadc5e80532fdeaaa0e0388e6dce
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186952"
---
# <a name="using-the-resource-designer-tool"></a>Kaynak Tasarımcısı aracını kullanma

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Kaynak Tasarımcısı aracı tarafından sunulan cmdlet'leri kümesidir **xDscResourceDesigner** oluşturma Windows PowerShell istenen durum yapılandırması (DSC) kaynakları kolaylaştırmak modülü. Bu kaynak Cmdlet'lerde MOF şema, betik modülündeki ve yeni kaynak dizin yapısı oluşturmaya yardımcı olmak. DSC kaynakları hakkında daha fazla bilgi için bkz: [yapı özel Windows PowerShell istenen durum yapılandırması kaynaklarını](authoringResource.md).
Bu konuda, Active Directory Kullanıcıları yönetir DSC kaynağı oluşturacağız.
Kullanım [yükleme-Module](https://technet.microsoft.com/library/dn807162.aspx) yüklemek için cmdlet'i **xDscResourceDesigner** modülü.

>**Not**: **yükleme-Module** dahil **PowerShellGet** PowerShell 5. 0 ' dahil modülü. İndirebilirsiniz **PowerShellGet** için modülü PowerShell 3.0 ve 4.0 en [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Kaynak özellikleri oluşturma
Yapmamız gereken ilk şey, kaynak açığa çıkarır özelliklerinde karar ' dir. Bu örnekte, biz aşağıdaki özelliklere sahip bir Active Directory kullanıcı tanımlayacaksınız.

Parametre adı açıklaması
* **Kullanıcı adı**: anahtarı bir kullanıcı olarak tanıtan özelliği.
* **Olun**: kullanıcı hesabı yoksa mi olacağını Absent belirtir. Bu parametre yalnızca iki olası değerlere sahip olur.
* **DomainCredential**: kullanıcı için etki alanı parolası.
* **Parola**: gerekirse, kullanıcı parolasını değiştirmek bir yapılandırma izin vermek kullanıcı için istenen parola.

Özellikleri oluşturmak için kullanırız **yeni xDscResourceProperty** cmdlet'i. Aşağıdaki PowerShell komutları yukarıda açıklanan özellikleri oluşturur.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Kaynak oluşturma

Kaynak özelliklerini oluşturulan, biz çağırabilirsiniz **yeni xDscResource** kaynağı oluşturmak için cmdlet'i. **Yeni xDscResource** cmdlet'i parametre olarak özelliklerinin listesini alır. Ayrıca modülü nerede oluşturulacağını yolu, yeni kaynak adının ve yer modülünün adını alır. Aşağıdaki PowerShell komutunu kaynağı oluşturur.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

**Yeni xDscResource** cmdlet'i, MOF şeması, bir iskelet kaynak komut dosyası, yeni kaynak için gerekli dizin yapısını ve yeni kaynak sunan modülü bir bildirim oluşturur.

MOF şema dosyası altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, ve içeriğini aşağıdaki gibidir.

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

Kaynak betik altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Kendiniz eklemeniz gerekir kaynak uygulamak için gerçek mantığı içermez. İskelet komut dosyasının içeriğini aşağıdaki gibidir.

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

## <a name="updating-the-resource"></a>Kaynak güncelleştirme

Eklemek veya kaynak parametre listesini değiştirmek gerekiyorsa, çağırabilirsiniz **güncelleştirme xDscResource** cmdlet'i. Cmdlet kaynak ile yeni bir parametre listesini güncelleştirir. Kaynak kodunuzu mantığı zaten eklediyseniz, olduğu gibi bırakılır.

Örneğin, son günlüğü bizim kaynak kullanıcı için zaman dahil etmek istediğinizi varsayalım. Kaynak tamamen yeniden yazmak yerine çağırabilirsiniz **yeni xDscResourceProperty** yeni özellik oluşturmak ve ardından arama **güncelleştirme xDscResource** ve yeni özelliğinizi ekleyin özellikler listesi.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Bir kaynak şema test etme

Kaynak Tasarımcısı aracını el ile yazılmış bir MOF şema geçerliliğini sınamak için kullanılan bir daha fazla cmdlet kullanıma sunar. Çağrı **Test xDscSchema** cmdlet, bir MOF kaynak şema yolunu parametre olarak geçirme. Cmdlet'i şemayı hatalarını çıkarır.

### <a name="see-also"></a>Ayrıca bkz:

#### <a name="concepts"></a>Kavramlar
[Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma](authoringResource.md)

#### <a name="other-resources"></a>Diğer Kaynaklar
[xDscResourceDesigner Modülü](https://powershellgallery.com/packages/xDscResourceDesigner)