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
# <a name="using-the-resource-designer-tool"></a>Kaynak Tasarımcısı aracını kullanma

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Kaynak Tasarımcısı araç tarafından kullanıma sunulan cmdlet'leri kümesidir **xDscResourceDesigner** Windows PowerShell Desired State Configuration (DSC) kaynak oluşturmaya kolaylaştırmak modülü. Bu kaynakta yer alan cmdlet'ler MOF şema ve betik modülündeki yeni kaynağınızın dizin yapısı oluşturma yardımcı olur. DSC kaynakları hakkında daha fazla bilgi için bkz. [yapı özel Windows PowerShell Desired State Configuration kaynaklarını](authoringResource.md).
Bu konuda, Active Directory Kullanıcıları yöneten bir DSC kaynağı oluşturacağız.
Kullanım [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet'ine **xDscResourceDesigner** modülü.

>**Not**: **Install-Module** dahil **PowerShellGet** modülü, PowerShell 5. 0'da dahildir. İndirebileceğiniz **PowerShellGet** modülü PowerShell 3.0 ve 4.0, [PackageManagement PowerShell modülleri Önizleme](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Kaynak özellikleri oluşturma
Yapmamız gereken ilk şey, kaynak açığa çıkarır özelliklerde karar ' dir. Bu örnekte, biz aşağıdaki özelliklere sahip bir Active Directory kullanıcı tanımlayın.

Parametre adı açıklaması
* **Kullanıcı adı**: Kullanıcının benzersiz olarak tanımlayan anahtar özelliği.
* **Olun**: Kullanıcı hesabının geçerli olup olmayacağını veya Absent belirtir. Bu parametre, yalnızca iki olası değerlere sahip olur.
* **DomainCredential**: Etki alanı kullanıcı parolası.
* **Parola**: Gerekirse, kullanıcı parolasını değiştirmek bir yapılandırma izin vermek kullanıcı için istenilen parola.

Özellikler oluşturmak için kullandığımız **yeni xDscResourceProperty** cmdlet'i. Aşağıdaki PowerShell komutlarını yukarıda açıklanan özellikler oluşturun.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Kaynak Oluştur

Kaynak özellikleri oluşturulan, biz çağırabilirsiniz **yeni xDscResource** kaynak oluşturmak için cmdlet'i. **Yeni xDscResource** cmdlet parametreleri olarak özelliklerinin listesini alır. Ayrıca, modül nerede oluşturulması gereken yolu, yeni kaynak adı ve yer modülün adını alır. Aşağıdaki PowerShell komutunu kaynak oluşturur.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

**Yeni xDscResource** cmdlet'i MOF şema, çatı kaynak betiği, yeni kaynak için gerekli bir dizin yapısı ve yeni kaynak sunan modülü için bir bildirim oluşturur.

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

Kaynak betiği altındadır **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Kendiniz eklemeniz gerekir kaynak uygulamak için fiili mantığı içermez. İskelet komut dosyasının içeriğini aşağıdaki gibidir.

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

Eklediğinizde veya değiştirdiğinizde kaynak parametre listesini gerekiyorsa çağırabilirsiniz **güncelleştirme xDscResource** cmdlet'i. Cmdlet'i yeni bir parametre listesiyle kaynak güncelleştirir. Kaynak kodunuzu zaten mantıksal eklediyseniz, olduğu gibi bırakılır.

Örneğin, son günlüğü bizim kaynak kullanıcı için zaman dahil etmek istediğinizi varsayalım. Kaynak tamamen yeniden yazmak yerine, çağırabilirsiniz **yeni xDscResourceProperty** yeni bir özellik oluşturmak ve ardından çağırmak için **güncelleştirme xDscResource** ve yeni özelliğinizi ekleyin özellikler listesi.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Bir kaynak şema test etme

Kaynak Tasarımcısı aracını el ile yazılmış bir MOF şema geçerliliğini sınamak için kullanılan bir daha fazla cmdlet kullanıma sunar. Çağrı **Test xDscSchema** cmdlet'i, bir parametre olarak bir MOF kaynak şema yolunu geçirerek. Şema hataları cmdlet çıktı olarak sunar.

### <a name="see-also"></a>Ayrıca bkz:

#### <a name="concepts"></a>Kavramlar
[Derleme özel Windows PowerShell Desired State Configuration kaynakları](authoringResource.md)

#### <a name="other-resources"></a>Diğer Kaynaklar
[xDscResourceDesigner Modülü](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
