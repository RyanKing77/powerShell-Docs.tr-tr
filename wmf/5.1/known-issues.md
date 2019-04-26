---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1'de bilinen sorunlar
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084972"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="ab4f2-103">WMF 5.1'de bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="ab4f2-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="ab4f2-104">Bu bilgiler değiştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="ab4f2-105">Yönetici olarak PowerShell kısayolu başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="ab4f2-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="ab4f2-106">WMF yükleme sırasında kısayol yönetici olarak PowerShell başlatmaya çalışırsanız, bir "Bilinmeyen hata" iletisi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="ab4f2-107">Yönetici olmayan kısaca yeniden açın ve kısayol artık yönetici olarak da çalışır.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="ab4f2-108">Pester</span><span class="sxs-lookup"><span data-stu-id="ab4f2-108">Pester</span></span>

<span data-ttu-id="ab4f2-109">Bu sürümde, Pester Nano Sunucu'da kullanırken bilmeniz gereken iki sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="ab4f2-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="ab4f2-110">Testleri Pester karşı çalışan bazı hataları tam CLR ve CORE CLR farklılıklardan dolayı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="ab4f2-111">Özellikle, doğrula yöntemini XmlDocument türü üzerinde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="ab4f2-112">NUnit çıktı günlüklerini şemasını onaylamaya altı testleri başarısız olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="ab4f2-113">Bir kod kapsamı test başarısız olursa şu anda çünkü *WindowsFeature* Nano Server'da DSC kaynak mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="ab4f2-114">Ancak, bu hatalar genellikle zararsızdır ve güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="ab4f2-115">İşlem doğrulama</span><span class="sxs-lookup"><span data-stu-id="ab4f2-115">Operation Validation</span></span>

- <span data-ttu-id="ab4f2-116">`Update-Help` çalışmayan Yardım URI nedeniyle Microsoft.PowerShell.Operation.Validation modülü başarısız</span><span class="sxs-lookup"><span data-stu-id="ab4f2-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="ab4f2-117">DSC sonra WMF kaldırma</span><span class="sxs-lookup"><span data-stu-id="ab4f2-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="ab4f2-118">WMF kaldırma DSC MOF belgeleri yapılandırma klasörden silmez.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="ab4f2-119">MOF belgeleri eski sistemlerde kullanılabilir olmayan yeni özellikler içeriyorsa DSC düzgün şekilde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="ab4f2-120">Bu durumda, DSC durumları temizlemek için yükseltilmiş bir PowerShell konsolundan aşağıdaki betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-120">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="ab4f2-121">JEA sanal hesaplar</span><span class="sxs-lookup"><span data-stu-id="ab4f2-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="ab4f2-122">JEA uç noktaları ve WMF 5.0 ile sanal hesaplar kullanacak şekilde yapılandırılmış oturum yapılandırmaları WMF 5.1 sürümüne yükselttikten sonra sanal bir hesabı kullanacak şekilde yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="ab4f2-123">Bu, JEA oturumlarında çalışan komutlar potansiyel olarak kullanıcı yükseltilmiş ayrıcalıklar gerektiren komutlar çalışmasını engelliyor. bir geçici yönetici hesabı yerine bağlanan kullanıcının kimliği altında çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="ab4f2-124">Sanal hesaplar geri yüklemek için kaydını kaldırma ve sanal hesaplar kullanan herhangi bir oturum yapılandırmaları yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab4f2-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```