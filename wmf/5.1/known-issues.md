---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: WMF 5.1 bilinen sorunlar
ms.openlocfilehash: 467a191f40d85bfca7c794915d6274a9a1b201e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="520e9-103">WMF 5.1 bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="520e9-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="520e9-104">Not: Bu bilgiler değiştirilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="520e9-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="520e9-105">Yönetici olarak PowerShell kısayol başlatma</span><span class="sxs-lookup"><span data-stu-id="520e9-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="520e9-106">WMF yükledikten sonra kısayol yönetici olarak PowerShell başlatmaya çalışırsanız, "Belirtilmeyen hata" iletisi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520e9-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="520e9-107">Yönetici olmayan kısaca yeniden açın ve kısayol şimdi bile yönetici olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="520e9-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="520e9-108">Pester</span><span class="sxs-lookup"><span data-stu-id="520e9-108">Pester</span></span>
<span data-ttu-id="520e9-109">Bu sürümde Pester Nano Server kullanırken bilmeniz gereken iki sorunlar vardır:</span><span class="sxs-lookup"><span data-stu-id="520e9-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="520e9-110">Testleri Pester karşı çalışan bazı hatalar tam CLR ve çekirdek CLR arasındaki farklar nedeniyle neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="520e9-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="520e9-111">Özellikle, doğrula yöntemini XmlDocument türünde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="520e9-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="520e9-112">NUnit Çıktı günlükleri şeması doğrulamaya altı testleri başarısız olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="520e9-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
* <span data-ttu-id="520e9-113">Kod kapsamı test başarısız şu anda çünkü *WindowsFeature* DSC kaynağı Nano Server yok.</span><span class="sxs-lookup"><span data-stu-id="520e9-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="520e9-114">Ancak, bu hatalar genellikle zararsız olan ve güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="520e9-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="520e9-115">İşlemi doğrulama</span><span class="sxs-lookup"><span data-stu-id="520e9-115">Operation Validation</span></span>

* <span data-ttu-id="520e9-116">Çalışma dışı Yardım URI nedeniyle Microsoft.PowerShell.Operation.Validation modülü için Update-Help başarısız</span><span class="sxs-lookup"><span data-stu-id="520e9-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="520e9-117">DSC sonra WMF kaldırma</span><span class="sxs-lookup"><span data-stu-id="520e9-117">DSC after uninstall WMF</span></span>
* <span data-ttu-id="520e9-118">WMF kaldırma DSC MOF belgeleri yapılandırma klasöründen silinmez.</span><span class="sxs-lookup"><span data-stu-id="520e9-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="520e9-119">MOF belgeleri eski sistemlerinde kullanılabilir olmayan daha yeni özellikler içeriyorsa DSC düzgün çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="520e9-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="520e9-120">Bu durumda, aşağıdaki komut dosyasını yükseltilmiş PowerShell konsolundan DSC durumları temizlemek için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="520e9-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="520e9-121">JEA sanal hesaplar</span><span class="sxs-lookup"><span data-stu-id="520e9-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="520e9-122">JEA uç noktaları ve sanal hesaplar WMF 5.0 ile kullanmak üzere yapılandırılmış oturum yapılandırmaları WMF 5.1 sürümüne yükselttikten sonra sanal hesap kullanmak için yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="520e9-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="520e9-123">Bu, JEA oturumlarında çalışan komutlar olası kullanıcı yükseltilmiş ayrıcalıklar gerektiren komutlar çalışmasını engelleyen bir geçici yönetici hesabı yerine bağlanan kullanıcının kimliği altında çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="520e9-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="520e9-124">Sanal hesaplar geri yüklemek için kaydı ve sanal hesapları kullanan tüm oturum yapılandırmaları yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="520e9-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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