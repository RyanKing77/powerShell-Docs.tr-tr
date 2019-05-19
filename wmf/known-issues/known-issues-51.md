---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1'de bilinen sorunlar
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856367"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="cea35-103">WMF 5.1'de bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="cea35-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="cea35-104">Yönetici olarak PowerShell kısayolu başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="cea35-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="cea35-105">WMF yükleme sırasında kısayol yönetici olarak PowerShell başlatmaya çalışırsanız, bir "Bilinmeyen hata" iletisi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cea35-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="cea35-106">Yönetici olmayan kısaca yeniden açın ve kısayol artık yönetici olarak da çalışır.</span><span class="sxs-lookup"><span data-stu-id="cea35-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="cea35-107">Pester</span><span class="sxs-lookup"><span data-stu-id="cea35-107">Pester</span></span>

<span data-ttu-id="cea35-108">Bu sürümde, Pester Nano Sunucu'da kullanırken bilmeniz gereken iki sorun vardır:</span><span class="sxs-lookup"><span data-stu-id="cea35-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="cea35-109">Testleri Pester karşı çalışan bazı hataları tam CLR ve CORE CLR farklılıklardan dolayı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cea35-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="cea35-110">Özellikle, **doğrulama** yöntemi kullanılabilir değil **XmlDocument** türü.</span><span class="sxs-lookup"><span data-stu-id="cea35-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="cea35-111">NUnit çıktı günlüklerini şemasını onaylamaya altı testleri başarısız olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="cea35-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="cea35-112">Bir kod kapsamı test başarısız çünkü **WindowsFeature** Nano Server'da DSC kaynak mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="cea35-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="cea35-113">Ancak, bu hatalar genellikle zararsızdır ve güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="cea35-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="cea35-114">İşlem doğrulama</span><span class="sxs-lookup"><span data-stu-id="cea35-114">Operation Validation</span></span>

- <span data-ttu-id="cea35-115">`Update-Help` çalışmayan Yardım URI nedeniyle Microsoft.PowerShell.Operation.Validation modülü başarısız</span><span class="sxs-lookup"><span data-stu-id="cea35-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="cea35-116">DSC sonra WMF kaldırma</span><span class="sxs-lookup"><span data-stu-id="cea35-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="cea35-117">WMF kaldırma DSC MOF belgeleri yapılandırma klasörden silmez.</span><span class="sxs-lookup"><span data-stu-id="cea35-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="cea35-118">MOF belgeleri eski sistemlerde kullanılabilir olmayan yeni özellikler içeriyorsa DSC düzgün şekilde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cea35-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="cea35-119">Bu durumda, DSC durumları temizlemek için yükseltilmiş bir PowerShell konsolundan aşağıdaki betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cea35-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="cea35-120">JEA sanal hesaplar</span><span class="sxs-lookup"><span data-stu-id="cea35-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="cea35-121">JEA uç noktaları ve WMF 5.0 ile sanal hesaplar kullanacak şekilde yapılandırılmış oturum yapılandırmaları WMF 5.1 sürümüne yükselttikten sonra sanal bir hesabı kullanacak şekilde yapılandırılmaz.</span><span class="sxs-lookup"><span data-stu-id="cea35-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="cea35-122">Bu, JEA oturumlarında çalışan komutlar potansiyel olarak kullanıcı yükseltilmiş ayrıcalıklar gerektiren komutlar çalışmasını engelliyor. bir geçici yönetici hesabı yerine bağlanan kullanıcının kimliği altında çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cea35-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="cea35-123">Sanal hesaplar geri yüklemek için kaydını kaldırma ve sanal hesaplar kullanan herhangi bir oturum yapılandırmaları yeniden kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cea35-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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