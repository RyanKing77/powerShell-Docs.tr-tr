---
ms.date: 06/12/2017
keywords: jea, powershell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084853"
---
# <a name="prerequisites"></a><span data-ttu-id="4da4d-103">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4da4d-103">Prerequisites</span></span>

> <span data-ttu-id="4da4d-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4da4d-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4da4d-105">Yeterli yönetim, Windows PowerShell 5.0 ve üzeri bulunan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="4da4d-106">Bu konuda jea'yı kullanmaya başlamak için karşılanması gereken önkoşulları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4da4d-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="4da4d-107">Jea'yı yükleme</span><span class="sxs-lookup"><span data-stu-id="4da4d-107">Install JEA</span></span>

<span data-ttu-id="4da4d-108">JEA kullanılabilir Windows PowerShell 5.0 ve üzeri, ancak tam işlevsellik için sisteminiz için PowerShell kullanılabilir en son sürümünü yüklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="4da4d-109">Aşağıdaki tabloda, Windows Server üzerinde JEA'ün kullanılabilirlik açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="4da4d-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="4da4d-110">Sunucu işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="4da4d-110">Server Operating System</span></span>   | <span data-ttu-id="4da4d-111">JEA kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="4da4d-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="4da4d-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4da4d-112">Windows Server 2016</span></span>       | <span data-ttu-id="4da4d-113">Önceden</span><span class="sxs-lookup"><span data-stu-id="4da4d-113">Preinstalled</span></span>
<span data-ttu-id="4da4d-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4da4d-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="4da4d-115">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="4da4d-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="4da4d-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4da4d-116">Windows Server 2012</span></span>       | <span data-ttu-id="4da4d-117">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="4da4d-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="4da4d-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4da4d-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="4da4d-119">İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile</span><span class="sxs-lookup"><span data-stu-id="4da4d-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="4da4d-120">JEA, ev veya iş bilgisayarınızda de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4da4d-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="4da4d-121">İstemci işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="4da4d-121">Client Operating System</span></span>   | <span data-ttu-id="4da4d-122">JEA kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="4da4d-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="4da4d-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="4da4d-123">Windows 10 1607+</span></span>          | <span data-ttu-id="4da4d-124">Önceden</span><span class="sxs-lookup"><span data-stu-id="4da4d-124">Preinstalled</span></span>
<span data-ttu-id="4da4d-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="4da4d-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="4da4d-126">Önceden, ile işlevselliği azaltılmış<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4da4d-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="4da4d-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="4da4d-127">Windows 10 1507</span></span>           | <span data-ttu-id="4da4d-128">Mevcut değil</span><span class="sxs-lookup"><span data-stu-id="4da4d-128">Not available</span></span>
<span data-ttu-id="4da4d-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="4da4d-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="4da4d-130">WMF 5.1 tam işlevselliğiyle</span><span class="sxs-lookup"><span data-stu-id="4da4d-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="4da4d-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="4da4d-131">Windows 7</span></span>                 | <span data-ttu-id="4da4d-132">İşlevselliği azaltılmış<sup>1</sup> WMF 5.1 ile</span><span class="sxs-lookup"><span data-stu-id="4da4d-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="4da4d-133"><sup>1</sup> JEA, Grup yönetilen hizmet hesapları, Windows Server 2008 R2 veya Windows 7'yi kullanmak için yapılandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="4da4d-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="4da4d-134">Sanal hesaplar ve diğer JEA özellikleri *olan* desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="4da4d-135"><sup>2</sup> Windows 10 sürüm 1511 ve 1603 aşağıdaki JEA özellikleri desteklemez: Grup yönetilen hizmet hesabı, oturum yapılandırmaları koşullu erişim kuralları, kullanıcı sürücüsünde ve erişebilmesi için yerel kullanıcı hesapları olarak çalıştırmak.</span><span class="sxs-lookup"><span data-stu-id="4da4d-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="4da4d-136">Bu özellikler için destek almak için sürüm 1607 (Yıldönümü güncelleştirmesi) için Windows update veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="4da4d-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="4da4d-137">Yüklü PowerShell sürümünü denetleme</span><span class="sxs-lookup"><span data-stu-id="4da4d-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="4da4d-138">Hangi PowerShell sürümünü sisteminizde yüklü olmadığını denetlemek için kontrol `$PSVersionTable` bir Windows PowerShell isteminde değişken.</span><span class="sxs-lookup"><span data-stu-id="4da4d-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="4da4d-139">JEA, kullanıma hazır *ana* sürümüdür eşit veya ondan **5**.</span><span class="sxs-lookup"><span data-stu-id="4da4d-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="4da4d-140">En iyi deneyimi ve tüm yeni özelliklere erişimi için PowerShell sürümüne yükseltmeniz kesinlikle önerilir **5.1** mümkün olduğunda.</span><span class="sxs-lookup"><span data-stu-id="4da4d-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="4da4d-141">Windows Management Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="4da4d-141">Install Windows Management Framework</span></span>

<span data-ttu-id="4da4d-142">PowerShell daha eski bir sürümünü çalıştırıyorsanız, sisteminizi en son Windows Management Framework (WMF) güncelleştirmesi ile güncelleştirmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="4da4d-143">Güncelleştirme paketlerini ve en son WMF sürüm notlarını bağlantı kullanılabilir [İndirme Merkezi](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span><span class="sxs-lookup"><span data-stu-id="4da4d-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="4da4d-144">Tüm sunucularınızı yükseltmeden önce WMF İş yükünüzün uyumluluğu test önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="4da4d-145">Windows 10 kullanıcıları, Windows PowerShell'ın geçerli sürümü almak için en son özellik güncelleştirmeleri yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="4da4d-146">PowerShell uzaktan iletişimini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4da4d-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="4da4d-147">PowerShell uzaktan iletişimini JEA yerleşik bir temel sunar.</span><span class="sxs-lookup"><span data-stu-id="4da4d-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="4da4d-148">Bu nedenle PowerShell uzaktan iletişimini etkin emin olmak gerekli olan ve [düzgün güvenli](/powershell/scripting/setup/winrmsecurity) sisteminize JEA kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="4da4d-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="4da4d-149">PowerShell uzaktan iletişimini, Windows Server 2012, 2012 R2 ve 2016 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="4da4d-150">PowerShell uzaktan iletişimini yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4da4d-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="4da4d-151">PowerShell modülü ve komut dosyası bloğu günlüğünü (isteğe bağlı) etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4da4d-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="4da4d-152">Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="4da4d-153">PowerShell modülü günlüğü JEA için gerekli değildir, ancak bu komutları kullanıcıların çalışmasını sağlamak için açmanız önerilir merkezi bir konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="4da4d-154">Grup İlkesi kullanarak PowerShell modülü oturum ilkesi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4da4d-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="4da4d-155">Bir iş istasyonundaki yerel Grup İlkesi Düzenleyicisi'ni veya bir Grup İlkesi nesnesi bir Active Directory etki alanı denetleyicisinde Grup İlkesi Yönetim Konsolu'nu açma</span><span class="sxs-lookup"><span data-stu-id="4da4d-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="4da4d-156">Gidin **Bilgisayar Yapılandırması\\Yönetim Şablonları\\Windows bileşenleri\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="4da4d-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="4da4d-157">Çift tıklayın **modülü oturum açın**</span><span class="sxs-lookup"><span data-stu-id="4da4d-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="4da4d-158">Tıklayın **etkin**</span><span class="sxs-lookup"><span data-stu-id="4da4d-158">Click **Enabled**</span></span>
5. <span data-ttu-id="4da4d-159">Seçenekler bölümünde tıklayarak **Göster** modül adlarını yanındaki</span><span class="sxs-lookup"><span data-stu-id="4da4d-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="4da4d-160">Tür `\*` açılır pencerede içinde.</span><span class="sxs-lookup"><span data-stu-id="4da4d-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="4da4d-161">Bu PowerShell komutları tüm modüllerden oturum bildirir.</span><span class="sxs-lookup"><span data-stu-id="4da4d-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="4da4d-162">Tıklayın **Tamam** ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4da4d-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="4da4d-163">Çift tıklayın **PowerShell komut dosyası bloğu oturum açın**</span><span class="sxs-lookup"><span data-stu-id="4da4d-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="4da4d-164">Tıklayın **etkin**</span><span class="sxs-lookup"><span data-stu-id="4da4d-164">Click **Enabled**</span></span>
10. <span data-ttu-id="4da4d-165">Tıklayın **Tamam** ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4da4d-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="4da4d-166">(Etki alanına katılmış makinelerde yalnızca) Çalıştırma `gpupdate` veya güncelleştirilmiş ilke işlemek ve ayarları uygulamak Grup İlkesi için bekleyin</span><span class="sxs-lookup"><span data-stu-id="4da4d-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="4da4d-167">Sistem genelinde PowerShell transkripsiyonu Grup İlkesi aracılığıyla da etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4da4d-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4da4d-168">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4da4d-168">Next steps</span></span>

[<span data-ttu-id="4da4d-169">Bir rol özelliği dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="4da4d-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="4da4d-170">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="4da4d-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="4da4d-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4da4d-171">See also</span></span>

[<span data-ttu-id="4da4d-172">PowerShell uzaktan iletişimini ve WinRM güvenliği hakkında ek bilgi</span><span class="sxs-lookup"><span data-stu-id="4da4d-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="4da4d-173">*PowerShell mavi takımın ♥* güvenlik blog gönderisi</span><span class="sxs-lookup"><span data-stu-id="4da4d-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)