---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynakları
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046700"
---
# <a name="dsc-resources"></a>DSC kaynakları

>Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired State Configuration ' nı (DSC) kaynakları bir DSC yapılandırması için yapı taşlarını sağlar. Bir kaynak (şema) yapılandırılmış olabilir ve yerel Configuration Manager (LCM) ", bunu yapmak için" çağıran PowerShell Betiği işlevlerini içeren özellikleri sunar.

Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucusu ayarı olarak belirli bir şey modelleyebilirsiniz.  Grupları kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve kaynakları nasıl kullanılması amaçlanır tanımlamak için meta veriler içeren bir yapıya düzenleyen bir DSC modülünü, birleştirilir.

Her kaynağın bir * kaynakta kullanmak için gerekli sözdizimi belirleyen şema bir [yapılandırma](../configurations/configurations.md). Bir kaynağın şema, aşağıdaki yollarla tanımlanabilir:

- **'Schema.Mof'** dosyası: Çoğu kaynakları tanımlayan kendi *şema* 'schema.mof' nda kullanarak dosya [Yönetilen Nesne biçimi](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Kaynak adı\>. schema.psm1'** dosyası: [Bileşik kaynaklar](../configurations/compositeConfigs.md) tanımlayın, *şema* içinde bir '<ResourceName>. schema.psm1' kullanarak dosya bir [parametre bloğu](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Kaynak adı\>.psm1'** dosyası: Temel DSC kaynakları tanımlayan bir sınıf kendi *şema* sınıf tanımında. Söz dizimi öğeleri sınıfı özellik olarak belirtilir. Daha fazla bilgi için [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

DSC kaynak sözdizimi almak için kullanın [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'iyle `-Syntax` parametresi. Bu kullanım kullanmaya benzer [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ile `-Syntax` cmdlet sözdizimi almak için parametre. Bir kaynak bloğu için belirttiğiniz kaynak için kullanılan şablon, çıktıyı gösterir.

```powershell
Get-DscResource -Syntax Service
```

Bu kaynağın sözdizimi gelecekte değişebilir olsa, çıktıyı aşağıdaki çıktıya benzer olmalıdır. Cmdlet sözdizimi gibi *anahtarları* köşeli ayraçlar içinde görülen, isteğe bağlıdır. Her anahtar bekliyor veri türüne türlerini belirtin.

> [!NOTE]
> **Olun** "Var" için varsayılanları nedeniyle anahtar isteğe bağlıdır.

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

İçinde bir yapılandırma bir **hizmet** kaynak bloğu için şöyle görünebilir **olun** Biriktirici hizmetini çalıştıran.

> [!NOTE]
> Bir kaynak bir yapılandırmada kullanmadan önce kullanarak aktarmalısınız [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Yapılandırmalar, aynı kaynak türünün birden fazla örneğini içerebilir. Her örneğini benzersiz olarak adlandırılmalıdır. Aşağıdaki örnekte, ikinci bir **hizmet** kaynak blok "DHCP" hizmetini yapılandırma eklenir.

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> PowerShell 5. 0'den itibaren IntelliSense için DSC eklendi. Bu yeni özellik kullanmanıza olanak sağlar. \<sekmesini\> ve \<Ctrl + boşluk\> anahtar adları otomatik olarak tamamlamak için.

![Kaynak sekme tamamlama](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Yerleşik kaynaklar

Topluluk kaynakları yanı sıra Windows, Linux için kaynaklar ve çapraz düğüm bağımlılığı kaynakları için yerleşik kaynaklar vardır. Sözdizimi, bu kaynakları ve bunların nasıl kullanılacağını belirlemek için yukarıdaki adımları kullanabilirsiniz. Bu kaynaklar hizmet sayfaları altında arşivlenmiştir **başvuru**.

Windows yerleşik kaynaklar

* [Archive Kaynağı](../reference/resources/windows/archiveResource.md)
* [Environment Kaynağı](../reference/resources/windows/environmentResource.md)
* [File Kaynağı](../reference/resources/windows/fileResource.md)
* [Group Kaynağı](../reference/resources/windows/groupResource.md)
* [GroupSet Kaynağı](../reference/resources/windows/groupSetResource.md)
* [Log Kaynağı](../reference/resources/windows/logResource.md)
* [Package Kaynağı](../reference/resources/windows/packageResource.md)
* [ProcessSet Kaynağı](../reference/resources/windows/ProcessSetResource.md)
* [Registry Kaynağı](../reference/resources/windows/registryResource.md)
* [Script Kaynağı](../reference/resources/windows/scriptResource.md)
* [Service Kaynağı](../reference/resources/windows/serviceResource.md)
* [ServiceSet Kaynağı](../reference/resources/windows/serviceSetResource.md)
* [User Kaynağı](../reference/resources/windows/userResource.md)
* [WindowsFeature Kaynağı](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet Kaynağı](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature Kaynağı](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet Kaynağı](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource kaynak](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess Kaynağı](../reference/resources/windows/windowsProcessResource.md)

[Çapraz düğüm bağımlılık](../configurations/crossNodeDependencies.md) kaynakları

* [WaitForAll kaynak](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome kaynak](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny kaynak](../reference/resources/windows/waitForAnyResource.md)

Paket Yönetimi kaynakları

* [PackageManagement kaynak](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource kaynak](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux kaynakları

* [Linux Archive kaynağı](../reference/resources/linux/lnxArchiveResource.md)
* [Linux Environment kaynağı](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine kaynak](../reference/resources/linux/lnxFileLineResource.md)
* [Linux dosya kaynağı](../reference/resources/linux/lnxFileResource.md)
* [Linux Group kaynağı](../reference/resources/linux/lnxGroupResource.md)
* [Linux paket kaynağı](../reference/resources/linux/lnxPackageResource.md)
* [Linux Script kaynağı](../reference/resources/linux/lnxScriptResource.md)
* [Linux Service kaynağı](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys kaynak](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux kullanıcı kaynağı](../reference/resources/linux/lnxUserResource.md)
