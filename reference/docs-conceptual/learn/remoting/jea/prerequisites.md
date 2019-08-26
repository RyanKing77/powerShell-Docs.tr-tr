---
ms.date: 07/10/2019
keywords: Jea, PowerShell, güvenlik
title: JEA önkoşulları
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017940"
---
# <a name="prerequisites"></a><span data-ttu-id="c8919-103">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c8919-103">Prerequisites</span></span>

<span data-ttu-id="c8919-104">Yalnızca PowerShell 5,0 ve üzeri sürümlerde bulunan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="c8919-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="c8919-105">Bu makalede, JEA kullanmaya başlamak için karşılanması gereken önkoşullar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8919-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="c8919-106">Hangi PowerShell sürümünün yüklü olduğunu denetleyin</span><span class="sxs-lookup"><span data-stu-id="c8919-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="c8919-107">Sisteminizde hangi PowerShell sürümünün yüklü olduğunu denetlemek için bir Windows PowerShell komut isteminde `$PSVersionTable` değişkeni denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c8919-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="c8919-108">JEA, PowerShell 5,0 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8919-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="c8919-109">Tam işlevsellik için, sisteminizde kullanılabilir olan PowerShell 'in en son sürümünü yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="c8919-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="c8919-110">Aşağıdaki tabloda, JEA 'nın Windows Server 'da kullanılabilirliği açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="c8919-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="c8919-111">Sunucu Işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="c8919-111">Server Operating System</span></span> |                <span data-ttu-id="c8919-112">JEA kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="c8919-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="c8919-113">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="c8919-113">Windows Server 2016+</span></span>    | <span data-ttu-id="c8919-114">Önceden yüklenmiş</span><span class="sxs-lookup"><span data-stu-id="c8919-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="c8919-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c8919-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="c8919-116">WMF 5,1 ile tam işlevsellik</span><span class="sxs-lookup"><span data-stu-id="c8919-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="c8919-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c8919-117">Windows Server 2012</span></span>     | <span data-ttu-id="c8919-118">WMF 5,1 ile tam işlevsellik</span><span class="sxs-lookup"><span data-stu-id="c8919-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="c8919-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c8919-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="c8919-120">WMF 5,1 ile azaltılmış işlevsellik<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c8919-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="c8919-121">JEA 'yı evinizde veya iş bilgisayarınızda da kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8919-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="c8919-122">İstemci Işletim sistemi</span><span class="sxs-lookup"><span data-stu-id="c8919-122">Client Operating System</span></span> |                   <span data-ttu-id="c8919-123">JEA kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="c8919-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="c8919-124">Windows 10 1607 +</span><span class="sxs-lookup"><span data-stu-id="c8919-124">Windows 10 1607+</span></span>        | <span data-ttu-id="c8919-125">Önceden yüklenmiş</span><span class="sxs-lookup"><span data-stu-id="c8919-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="c8919-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="c8919-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="c8919-127">Önceden yüklenmiş, azaltılmış işlevsellik<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c8919-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="c8919-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="c8919-128">Windows 10 1507</span></span>         | <span data-ttu-id="c8919-129">Mevcut değil</span><span class="sxs-lookup"><span data-stu-id="c8919-129">Not available</span></span>                                        |
| <span data-ttu-id="c8919-130">Windows 8, 8,1</span><span class="sxs-lookup"><span data-stu-id="c8919-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="c8919-131">WMF 5,1 ile tam işlevsellik</span><span class="sxs-lookup"><span data-stu-id="c8919-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="c8919-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="c8919-132">Windows 7</span></span>               | <span data-ttu-id="c8919-133">WMF 5,1 ile azaltılmış işlevsellik<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c8919-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="c8919-134"><sup>1</sup> Jea, windows Server 2008 R2 veya Windows 7 ' de grup tarafından yönetilen hizmet hesaplarını kullanacak şekilde yapılandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8919-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="c8919-135">Sanal hesaplar ve diğer JEA özellikleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8919-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="c8919-136"><sup>2</sup> aşağıdaki Jea özellikleri 1511 ve 1603 Windows 10 sürümlerinde desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="c8919-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="c8919-137">Grup tarafından yönetilen hizmet hesabı olarak çalışıyor</span><span class="sxs-lookup"><span data-stu-id="c8919-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="c8919-138">Oturum yapılandırmalarında koşullu erişim kuralları</span><span class="sxs-lookup"><span data-stu-id="c8919-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="c8919-139">Kullanıcı sürücüsü</span><span class="sxs-lookup"><span data-stu-id="c8919-139">The user drive</span></span>
  - <span data-ttu-id="c8919-140">Yerel Kullanıcı hesaplarına erişim verme</span><span class="sxs-lookup"><span data-stu-id="c8919-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="c8919-141">Bu özelliklere yönelik destek almak için Windows 'u sürüm 1607 (yıldönümü güncelleştirmesi) veya sonraki bir sürüme güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c8919-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="c8919-142">Windows Management Framework 'Ü yükler</span><span class="sxs-lookup"><span data-stu-id="c8919-142">Install Windows Management Framework</span></span>

<span data-ttu-id="c8919-143">PowerShell 'in eski bir sürümünü çalıştırıyorsanız sisteminizi en son Windows Management Framework (WMF) güncelleştirmesiyle güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c8919-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="c8919-144">Daha fazla bilgi için bkz. [WMF belgeleri](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="c8919-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="c8919-145">Tüm sunucularınızı yükseltmeden önce iş yükünüzün WMF ile uyumluluğunu test etmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="c8919-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="c8919-146">Windows 10 kullanıcıları, geçerli Windows PowerShell sürümünü edinmek için en son özellik güncelleştirmelerini yüklemelidir.</span><span class="sxs-lookup"><span data-stu-id="c8919-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="c8919-147">PowerShell uzaktan iletişimini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="c8919-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="c8919-148">PowerShell Remoting, JEA 'nın oluşturulduğu temeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8919-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="c8919-149">JEA kullanabilmeniz için PowerShell Remoting 'in etkinleştirildiğinden ve düzgün şekilde güvende olduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8919-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="c8919-150">Daha fazla bilgi için bkz. [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="c8919-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="c8919-151">PowerShell uzaktan Iletişimi Windows Server 2012, 2012 R2 ve 2016 üzerinde varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c8919-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="c8919-152">Yükseltilmiş bir PowerShell penceresinde aşağıdaki komutu çalıştırarak PowerShell uzaktan iletişimini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8919-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="c8919-153">PowerShell modülünü ve betik bloğu günlüğünü etkinleştir (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c8919-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="c8919-154">Aşağıdaki adımlar, sisteminizdeki tüm PowerShell eylemleri için günlük kaydını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8919-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="c8919-155">PowerShell modülü günlüğü JEA için gerekli değildir, ancak kullanıcıların çalıştırdığı komutların merkezi bir konumda günlüğe kaydedilmesini sağlamak için günlüğe kaydetmeyi açmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c8919-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="c8919-156">Grup ilkesi kullanarak PowerShell modülü günlük ilkesini yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8919-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="c8919-157">Bir iş istasyonunda Yerel Grup İlkesi Düzenleyicisi veya bir Active Directory Etki Alanı Denetleyicisindeki Grup İlkesi Yönetim Konsolu bir grup ilkesi nesnesi açın</span><span class="sxs-lookup"><span data-stu-id="c8919-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="c8919-158">**Windows bileşenleri\\\\WindowsPowerShellYönetimŞablonlarıbilgisayaryapılandırması'nagidin.\\**</span><span class="sxs-lookup"><span data-stu-id="c8919-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="c8919-159">**Modül günlüğünü aç** ' a çift tıklayın</span><span class="sxs-lookup"><span data-stu-id="c8919-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="c8919-160">**Etkin** ' e tıklayın</span><span class="sxs-lookup"><span data-stu-id="c8919-160">Click **Enabled**</span></span>
5. <span data-ttu-id="c8919-161">Seçenekler bölümünde, modül adlarının yanındaki **göster** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c8919-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="c8919-162">Tüm `*` modüllerdeki komutları günlüğe kaydetmek için açılır pencereyi yazın.</span><span class="sxs-lookup"><span data-stu-id="c8919-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="c8919-163">İlkeyi ayarlamak için **Tamam** ' ı tıklatın</span><span class="sxs-lookup"><span data-stu-id="c8919-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="c8919-164">**PowerShell betik bloğu günlüğünü aç** ' a çift tıklayın</span><span class="sxs-lookup"><span data-stu-id="c8919-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="c8919-165">**Etkin** ' e tıklayın</span><span class="sxs-lookup"><span data-stu-id="c8919-165">Click **Enabled**</span></span>
10. <span data-ttu-id="c8919-166">İlkeyi ayarlamak için **Tamam** ' ı tıklatın</span><span class="sxs-lookup"><span data-stu-id="c8919-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="c8919-167">(Yalnızca etki alanına katılmış makinelerde) `gpupdate` Grup İlkesi güncelleştirilmiş ilkeyi işlemesini ve ayarları uygulamayı bekleyin</span><span class="sxs-lookup"><span data-stu-id="c8919-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="c8919-168">Ayrıca, grup ilkesi aracılığıyla sistem genelinde PowerShell dökümünü de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8919-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8919-169">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c8919-169">Next steps</span></span>

[<span data-ttu-id="c8919-170">Rol yetenek dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8919-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="c8919-171">Oturum yapılandırma dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8919-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="c8919-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8919-172">See also</span></span>

[<span data-ttu-id="c8919-173">WinRM güvenliği</span><span class="sxs-lookup"><span data-stu-id="c8919-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="c8919-174">Mavi ekibi ♥ PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8919-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
