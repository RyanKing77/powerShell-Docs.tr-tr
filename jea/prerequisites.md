---
ms.date: 07/10/2019
keywords: jea, powershell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734285"
---
# <a name="prerequisites"></a><span data-ttu-id="225ff-103">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="225ff-103">Prerequisites</span></span>

<span data-ttu-id="225ff-104">Yeterli yönetim PowerShell 5.0 ve üzeri bulunan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="225ff-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="225ff-105">Bu makalede jea'yı kullanmaya başlamak için karşılanması gereken önkoşulları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="225ff-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="225ff-106">Yüklü PowerShell sürümünü denetleme</span><span class="sxs-lookup"><span data-stu-id="225ff-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="225ff-107">Hangi PowerShell sürümünü sisteminizde yüklü olmadığını denetlemek için kontrol `$PSVersionTable` bir Windows PowerShell isteminde değişken.</span><span class="sxs-lookup"><span data-stu-id="225ff-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="225ff-108">JEA kullanılabilir PowerShell 5.0 ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="225ff-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="225ff-109">Tam işlevsellik için sisteminiz için PowerShell kullanılabilir en son sürümünü yüklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="225ff-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="225ff-110">Aşağıdaki tabloda, Windows Server üzerinde JEA'ün kullanılabilirlik açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="225ff-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="225ff-111">Sunucu işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="225ff-111">Server Operating System</span></span> |                <span data-ttu-id="225ff-112">JEA kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="225ff-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="225ff-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="225ff-113">Windows Server 2016+</span></span>    | <span data-ttu-id="225ff-114">Önceden</span><span class="sxs-lookup"><span data-stu-id="225ff-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="225ff-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="225ff-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="225ff-116">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="225ff-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="225ff-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="225ff-117">Windows Server 2012</span></span>     | <span data-ttu-id="225ff-118">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="225ff-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="225ff-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="225ff-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="225ff-120">İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile</span><span class="sxs-lookup"><span data-stu-id="225ff-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="225ff-121">JEA, ev veya iş bilgisayarınızda de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="225ff-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="225ff-122">İstemci işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="225ff-122">Client Operating System</span></span> |                   <span data-ttu-id="225ff-123">JEA kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="225ff-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="225ff-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="225ff-124">Windows 10 1607+</span></span>        | <span data-ttu-id="225ff-125">Önceden</span><span class="sxs-lookup"><span data-stu-id="225ff-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="225ff-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="225ff-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="225ff-127">Önceden, ile işlevselliği azaltılmış<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="225ff-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="225ff-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="225ff-128">Windows 10 1507</span></span>         | <span data-ttu-id="225ff-129">Mevcut değil</span><span class="sxs-lookup"><span data-stu-id="225ff-129">Not available</span></span>                                        |
| <span data-ttu-id="225ff-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="225ff-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="225ff-131">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="225ff-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="225ff-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="225ff-132">Windows 7</span></span>               | <span data-ttu-id="225ff-133">İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile</span><span class="sxs-lookup"><span data-stu-id="225ff-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="225ff-134"><sup>1</sup> JEA, Windows Server 2008 R2 veya Windows 7 Grup yönetilen hizmet hesaplarını kullanmak için yapılandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="225ff-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="225ff-135">Sanal hesaplar ve diğer JEA özellikleri *olan* desteklenir.</span><span class="sxs-lookup"><span data-stu-id="225ff-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="225ff-136"><sup>2</sup> aşağıdaki JEA özellikleri, Windows 10 sürüm 1511 ve 1603 desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="225ff-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="225ff-137">Bir grup yönetilen hizmet hesabı olarak çalışıyor</span><span class="sxs-lookup"><span data-stu-id="225ff-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="225ff-138">Oturum yapılandırmaları koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="225ff-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="225ff-139">Kullanıcı sürücü</span><span class="sxs-lookup"><span data-stu-id="225ff-139">The user drive</span></span>
  - <span data-ttu-id="225ff-140">Yerel kullanıcı hesapları için erişim verme</span><span class="sxs-lookup"><span data-stu-id="225ff-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="225ff-141">Bu özellikler için destek almak için sürüm 1607 (Yıldönümü güncelleştirmesi) için Windows update veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="225ff-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="225ff-142">Windows Management Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="225ff-142">Install Windows Management Framework</span></span>

<span data-ttu-id="225ff-143">PowerShell daha eski bir sürümünü çalıştırıyorsanız, en son Windows Management Framework (WMF) güncelleştirmesiyle sisteminizi güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="225ff-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="225ff-144">Daha fazla bilgi için [WMF belgeleri](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="225ff-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="225ff-145">Tüm sunucularınızı yükseltmeden önce WMF İş yükünüzün uyumluluğu test önerilir.</span><span class="sxs-lookup"><span data-stu-id="225ff-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="225ff-146">Windows 10 kullanıcıları, Windows PowerShell'ın geçerli sürümü almak için en son özellik güncelleştirmeleri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="225ff-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="225ff-147">PowerShell uzaktan iletişimini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="225ff-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="225ff-148">PowerShell uzaktan iletişimini JEA yerleşik bir temel sunar.</span><span class="sxs-lookup"><span data-stu-id="225ff-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="225ff-149">PowerShell uzaktan iletişimini etkin ve JEA kullanmadan önce düzgün şekilde güvenliğinin emin olmak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="225ff-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="225ff-150">Daha fazla bilgi için [WinRM güvenlik](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="225ff-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="225ff-151">PowerShell uzaktan iletişimini, Windows Server 2012, 2012 R2 ve 2016 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="225ff-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="225ff-152">PowerShell uzaktan iletişimini yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="225ff-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="225ff-153">PowerShell modülü ve komut dosyası bloğu günlüğünü (isteğe bağlı) etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="225ff-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="225ff-154">Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="225ff-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="225ff-155">PowerShell modülü günlüğü JEA için gerekli değildir, ancak komutları kullanıcıların çalışmasını sağlamak için günlüğe kaydetmeyi önerilir merkezi bir konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="225ff-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="225ff-156">Grup İlkesi kullanarak PowerShell modülü oturum ilkesi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="225ff-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="225ff-157">Bir iş istasyonundaki yerel Grup İlkesi Düzenleyicisi'ni veya bir Grup İlkesi nesnesi bir Active Directory etki alanı denetleyicisinde Grup İlkesi Yönetim Konsolu'nu açma</span><span class="sxs-lookup"><span data-stu-id="225ff-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="225ff-158">Gidin **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows bileşenleri\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="225ff-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="225ff-159">Çift **modülü günlüğünü etkinleştirme**</span><span class="sxs-lookup"><span data-stu-id="225ff-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="225ff-160">Tıklayın **etkin**</span><span class="sxs-lookup"><span data-stu-id="225ff-160">Click **Enabled**</span></span>
5. <span data-ttu-id="225ff-161">Seçenekler bölümünde tıklayarak **Göster** modül adlarını yanındaki</span><span class="sxs-lookup"><span data-stu-id="225ff-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="225ff-162">Tür `*` komutları tüm modüllerden oturum açılan penceresinde.</span><span class="sxs-lookup"><span data-stu-id="225ff-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="225ff-163">Tıklayın **Tamam** ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="225ff-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="225ff-164">Çift **günlük PowerShell komut dosyası bloğu üzerinde Aç**</span><span class="sxs-lookup"><span data-stu-id="225ff-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="225ff-165">Tıklayın **etkin**</span><span class="sxs-lookup"><span data-stu-id="225ff-165">Click **Enabled**</span></span>
10. <span data-ttu-id="225ff-166">Tıklayın **Tamam** ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="225ff-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="225ff-167">(Etki alanına katılmış makinelerde yalnızca) Çalıştırma `gpupdate` veya güncelleştirilmiş ilke işlemek ve ayarları uygulamak Grup İlkesi için bekleyin</span><span class="sxs-lookup"><span data-stu-id="225ff-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="225ff-168">Sistem genelinde PowerShell transkripsiyonu Grup İlkesi aracılığıyla da etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="225ff-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="225ff-169">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="225ff-169">Next steps</span></span>

[<span data-ttu-id="225ff-170">Bir rol özelliği dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="225ff-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="225ff-171">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="225ff-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="225ff-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="225ff-172">See also</span></span>

[<span data-ttu-id="225ff-173">WinRM güvenlik</span><span class="sxs-lookup"><span data-stu-id="225ff-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="225ff-174">PowerShell ♥ mavi takım</span><span class="sxs-lookup"><span data-stu-id="225ff-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
