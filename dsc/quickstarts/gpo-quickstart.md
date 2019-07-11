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
> <span data-ttu-id="cea59-103">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cea59-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="cea59-104">Hızlı Başlangıç: Dönüştürme Grup İlkesi'nde DSC</span><span class="sxs-lookup"><span data-stu-id="cea59-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="cea59-105">Grup İlkesi veya Azure Güvenlik Merkezi taban çizgisinden bir DSC yapılandırması oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cea59-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="cea59-106">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) modülü, bu görev işlemi gerçekleştirmek için aşağıdaki komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="cea59-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="cea59-107">`ConvertFrom-GPO` -Dönüştürür grup ilkeleri, dosyaları olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="cea59-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="cea59-108">Bir dizin içeren bir yapılandırma ile birleştirilecek birden çok ilke de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cea59-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="cea59-109">Grup ilkeleri, ortamınızda vermek için kullanın [GPO yedekle](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet'ini veya yönergeleri [bir dosyaya bir GPO](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="cea59-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="cea59-110">`ConvertFrom-SCM` -Security Compliance Manager taban çizgisi olarak depolanan dönüştürür `.xml` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="cea59-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="cea59-111">`ConvertFrom-ASC` -Dönüştürür Azure Güvenlik Merkezi temelleri, depolanan `.json` dosyaları.</span><span class="sxs-lookup"><span data-stu-id="cea59-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="cea59-112">`Merge-GPOs` -Dönüştürür grup ilkeleri, bir hedef bilgisayara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cea59-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="cea59-113">Yukarıda listelenen cmdlet'ler temel bir DSC Dönüştür `.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="cea59-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="cea59-114">Bir yapılandırma betiği çıktısını almak de seçebilirsiniz (`.ps1`), Düzenle ve yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="cea59-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="cea59-115">Cmdlet'ler, eksik kaynakları veya yinelenen kaynak bloklar için derleme hataları algılayın.</span><span class="sxs-lookup"><span data-stu-id="cea59-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="cea59-116">Derleme hataları neden olan kaynak blok açıklama satırı yapılır.</span><span class="sxs-lookup"><span data-stu-id="cea59-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="cea59-117">Aşağıdaki örnek bir [Microsoft Güvenlik temeli](https://www.microsoft.com/en-us/download/details.aspx?id=55319) içine bir DSC yapılandırma betiği (`.ps1`) ve `.mof` dosya.</span><span class="sxs-lookup"><span data-stu-id="cea59-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="cea59-118">Bu komutları çalıştırdıktan sonra iki dosyada, geçerli yolun altındaki oluşturulan varsayılan "Çıkış" dizinine bakın.</span><span class="sxs-lookup"><span data-stu-id="cea59-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="cea59-119">Yönetilen her düğüm, aşağıdaki iki modül de gerekir:</span><span class="sxs-lookup"><span data-stu-id="cea59-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="cea59-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="cea59-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="cea59-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="cea59-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="cea59-122">**BaselineManagement** topluluk çözümleriyle proje maintainers ve değil Microsoft gelen için DSC desteği için daha bulunabilir hale getirmek için topluluk tarafından geliştirilen bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="cea59-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="cea59-123">İçin yeni bir sorun açabilirsiniz **BaselineManagement** üzerinde [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="cea59-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cea59-124">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cea59-124">Next steps</span></span>

- <span data-ttu-id="cea59-125">Azure Otomasyonu durum yapılandırması ile yapılandırma komut dosyanızı karşıya yüklemek için bkz [Başlarken](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="cea59-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="cea59-126">Ekleme **SecurityPolicyDSC** ve **AuditPolicyDSC** modüllerine, [Otomasyon hesabı](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="cea59-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="cea59-127">DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="cea59-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
