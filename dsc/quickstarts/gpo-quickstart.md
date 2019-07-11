---
ms.date: 07/09/2019
keywords: DSC, gpo, powershell, yapılandırma ve Kurulum
title: Hızlı Başlangıç - DSC içine dönüştürme Grup İlkesi
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785141"
---
> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Hızlı Başlangıç: Dönüştürme Grup İlkesi'nde DSC

Grup İlkesi veya Azure Güvenlik Merkezi taban çizgisinden bir DSC yapılandırması oluşturabilirsiniz. [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) modülü, bu görev işlemi gerçekleştirmek için aşağıdaki komutları içerir.

- `ConvertFrom-GPO` -Dönüştürür grup ilkeleri, dosyaları olarak depolanır. Bir dizin içeren bir yapılandırma ile birleştirilecek birden çok ilke de belirtebilirsiniz.
  - Grup ilkeleri, ortamınızda vermek için kullanın [GPO yedekle](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet'ini veya yönergeleri [bir dosyaya bir GPO](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` -Security Compliance Manager taban çizgisi olarak depolanan dönüştürür `.xml` dosyaları.
- `ConvertFrom-ASC` -Dönüştürür Azure Güvenlik Merkezi temelleri, depolanan `.json` dosyaları.
- `Merge-GPOs` -Dönüştürür grup ilkeleri, bir hedef bilgisayara uygulanır.

Yukarıda listelenen cmdlet'ler temel bir DSC Dönüştür `.mof` dosya. Bir yapılandırma betiği çıktısını almak de seçebilirsiniz (`.ps1`), Düzenle ve yeniden derleyin. Cmdlet'ler, eksik kaynakları veya yinelenen kaynak bloklar için derleme hataları algılayın. Derleme hataları neden olan kaynak blok açıklama satırı yapılır.

Aşağıdaki örnek bir [Microsoft Güvenlik temeli](https://www.microsoft.com/en-us/download/details.aspx?id=55319) içine bir DSC yapılandırma betiği (`.ps1`) ve `.mof` dosya.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Bu komutları çalıştırdıktan sonra iki dosyada, geçerli yolun altındaki oluşturulan varsayılan "Çıkış" dizinine bakın.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Yönetilen her düğüm, aşağıdaki iki modül de gerekir:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** topluluk çözümleriyle proje maintainers ve değil Microsoft gelen için DSC desteği için daha bulunabilir hale getirmek için topluluk tarafından geliştirilen bir çözüm. İçin yeni bir sorun açabilirsiniz **BaselineManagement** üzerinde [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Sonraki adımlar

- Azure Otomasyonu durum yapılandırması ile yapılandırma komut dosyanızı karşıya yüklemek için bkz [Başlarken](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Ekleme **SecurityPolicyDSC** ve **AuditPolicyDSC** modüllerine, [Otomasyon hesabı](/azure/automation/shared-resources/modules).
- DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).
