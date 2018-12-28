---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynakları
ms.openlocfilehash: 542a210ab47c650eac625108a78e76bc2cd55572
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405726"
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

![Kaynak sekme tamamlama](/media/resource-tabcompletion.png)
