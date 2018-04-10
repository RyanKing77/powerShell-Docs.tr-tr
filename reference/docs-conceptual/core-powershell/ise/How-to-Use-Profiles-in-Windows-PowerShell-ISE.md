---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Profilleri Kullanma
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: 8789d6283457f790fdea27657abb2612304e10a1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="1f0fc-103">Windows PowerShell ISE’de Profilleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f0fc-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="1f0fc-104">Bu konu, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE içinde) profilleri kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="1f0fc-105">Bu bölümde görevleri gerçekleştirmeden önce gözden geçirmenizi öneririz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ya da konsol bölmesinde, türü, `Get-Help about_Profiles` ve basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="1f0fc-106">Yeni bir oturumu yeniden başlattığınızda, otomatik olarak çalışan bir Windows PowerShell ISE komut profilidir.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="1f0fc-107">Windows PowerShell ISE için bir veya daha fazla Windows PowerShell profilleri oluşturmak ve bunları Windows PowerShell veya Windows PowerShell ISE ortamı yapılandırma eklemek için değişkenleri, diğer adlar, İşlevler, renk ve yazı tipi kullanımınız için hazırlama kullanın kullanılabilir olmasını istediğiniz Tercihler.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="1f0fc-108">Bir profili başlattığınız her Windows PowerShell ISE oturumuna etkiler.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="1f0fc-109">Windows PowerShell yürütme ilkesini betik çalıştıran ve bir profil yük olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="1f0fc-110">Varsayılan yürütme İlkesi "Kısıtlı," tüm komut dosyalarının engeller profilleri de dahil olmak üzere çalışmasını.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="1f0fc-111">"Kısıtlı" ilkesi kullanırsanız, profil yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="1f0fc-112">Yürütme İlkesi hakkında daha fazla bilgi için bkz: [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="1f0fc-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="1f0fc-113">Windows PowerShell ISE kullanmak için bir profil seçme</span><span class="sxs-lookup"><span data-stu-id="1f0fc-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="1f0fc-114">Geçerli kullanıcı ve tüm kullanıcılar için Windows PowerShell ISE profillerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="1f0fc-115">Ayrıca, tüm ana bilgisayarlar için geçerli Windows PowerShell profillerini destekler.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="1f0fc-116">Kullandığınız profili, Windows PowerShell ve Windows PowerShell ISE kullanma tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="1f0fc-117">Windows PowerShell'i çalıştırmak için yalnızca Windows PowerShell ISE kullanırsanız, tüm öğelerinizi CurrentUserCurrentHost için Windows PowerShell ISE veya AllUsersCurrentHost profili için Windows PowerShell ISE gibi işe özgü profillerini birinde kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="1f0fc-118">Windows PowerShell'i çalıştırmak için birden çok ana bilgisayar programlar kullanıyorsanız, işlevleri, diğer adlar, değişkenler ve komutları CurrentUserAllHosts gibi tüm konak programlar etkileyen bir profil veya AllUsersAllHosts profilinde kaydedin ve işe özgü özellikler gibi kaydedin Windows PowerShell ISE için renk ve yazı tipi özelleştirme Windows PowerShell ISE veya AllUsersCurrentHost profili CurrentUserCurrentHost profilinde.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="1f0fc-119">Oluşturulan ve Windows PowerShell ISE kullanılan profilleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="1f0fc-120">Her profil kendi belirli yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="1f0fc-121">Profil türü</span><span class="sxs-lookup"><span data-stu-id="1f0fc-121">Profile Type</span></span> | <span data-ttu-id="1f0fc-122">Profil yolu</span><span class="sxs-lookup"><span data-stu-id="1f0fc-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="1f0fc-123">**Geçerli kullanıcı, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="1f0fc-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="1f0fc-124">`$PROFILE.CurrentUserCurrentHost`, veya `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="1f0fc-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="1f0fc-125">**Tüm kullanıcılar, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="1f0fc-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="1f0fc-126">**Geçerli kullanıcı, tüm ana bilgisayarlar**</span><span class="sxs-lookup"><span data-stu-id="1f0fc-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="1f0fc-127">**Tüm kullanıcılar, tüm ana bilgisayarlar**</span><span class="sxs-lookup"><span data-stu-id="1f0fc-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="1f0fc-128">Yeni bir profil oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1f0fc-128">To create a new profile</span></span>

<span data-ttu-id="1f0fc-129">Yeni "geçerli bir kullanıcı, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="1f0fc-130">Yeni bir "Tüm kullanıcılar, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="1f0fc-131">"Geçerli kullanıcının tüm barındıran" yeni bir profil oluşturmak için bu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="1f0fc-132">"Tüm kullanıcılar, tüm barındıran" yeni bir profil oluşturmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="1f0fc-133">Bir profili düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="1f0fc-133">To edit a profile</span></span>

1. <span data-ttu-id="1f0fc-134">Profil açmak için komut psedit düzenlemek istediğiniz profili belirten değişkeni ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="1f0fc-135">Örneğin, "Current user, Windows PowerShell ISE" açmak için profil, yazın: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="1f0fc-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="1f0fc-136">Bazı öğeler profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-136">Add some items to your profile.</span></span> <span data-ttu-id="1f0fc-137">Başlamanıza yardımcı olmak için birkaç örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="1f0fc-138">Konsol bölmesinde, profil dosya türü olarak mavi varsayılan arka plan rengini değiştirmek için: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="1f0fc-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="1f0fc-139">$PsISE değişken hakkında daha fazla bilgi için bkz: [Windows PowerShell ISE nesne modeli başvurusu](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="1f0fc-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="1f0fc-140">20, profil dosya türü için yazı tipi boyutunu değiştirmek için: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="1f0fc-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="1f0fc-141">Profil dosyanızı üzerinde kaydetmek için **dosya** menüsünde tıklatın **kaydetmek**.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="1f0fc-142">Windows PowerShell ISE sonraki açışınızda özelleştirmelerinizi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f0fc-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1f0fc-143">See Also</span></span>

- [<span data-ttu-id="1f0fc-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="1f0fc-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="1f0fc-145">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="1f0fc-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)