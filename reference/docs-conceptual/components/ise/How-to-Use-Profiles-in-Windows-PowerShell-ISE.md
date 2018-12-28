---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Profilleri Kullanma
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405844"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="774fa-103">Windows PowerShell ISE’de Profilleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="774fa-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="774fa-104">Bu konu, Windows PowerShell® Tümleşik komut dosyası ortamı (ISE içinde) profilleri kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="774fa-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="774fa-105">Bu bölümde görevleri gerçekleştirmeden önce gözden geçirmenizi öneririz [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ya da konsol bölmesinde, türü, `Get-Help about_Profiles` basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="774fa-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="774fa-106">Yeni bir oturum başlattığınızda otomatik olarak çalışan bir Windows PowerShell ISE betik profilidir.</span><span class="sxs-lookup"><span data-stu-id="774fa-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="774fa-107">Windows PowerShell ISE için bir veya daha fazla Windows PowerShell profilleri oluşturmak ve bunları yapılandırma Windows PowerShell veya Windows PowerShell ISE ortamı eklemek için değişkenleri, diğer adlar, İşlevler, renk ve yazı tipi, kullanımınız için hazırlama kullanın kullanılabilir olmasını istediğiniz tercihleri.</span><span class="sxs-lookup"><span data-stu-id="774fa-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="774fa-108">Bir profili başlattığınız her Windows PowerShell ISE oturumuna etkiler.</span><span class="sxs-lookup"><span data-stu-id="774fa-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="774fa-109">Windows PowerShell yürütme İlkesi betikleri çalıştırabilir ve profil yükleme olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="774fa-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="774fa-110">Varsayılan yürütme ilkesini "Yasak" engelleyen tüm betikleri profilleri de dahil olmak üzere çalışmasını.</span><span class="sxs-lookup"><span data-stu-id="774fa-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="774fa-111">"Restricted" ilkesini kullanırsanız, profil yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="774fa-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="774fa-112">Yürütme İlkesi hakkında daha fazla bilgi için bkz. [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="774fa-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="774fa-113">Windows PowerShell ISE'de kullanmak için bir profil seçme</span><span class="sxs-lookup"><span data-stu-id="774fa-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="774fa-114">Geçerli kullanıcı ve tüm kullanıcılar için Windows PowerShell ISE profillerini destekler.</span><span class="sxs-lookup"><span data-stu-id="774fa-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="774fa-115">Ayrıca, tüm Konaklara uygulamak Windows PowerShell profillerini destekler.</span><span class="sxs-lookup"><span data-stu-id="774fa-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="774fa-116">Kullandığınız profili, Windows PowerShell ve Windows PowerShell ISE'yi kullanma tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="774fa-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="774fa-117">Windows PowerShell'i çalıştırmak için yalnızca Windows PowerShell ISE kullanırsanız, tüm öğeleri bir Windows PowerShell ISE CurrentUserCurrentHost profilini veya Windows PowerShell ISE AllUsersCurrentHost profilini gibi işe özgü profilini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="774fa-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="774fa-118">Windows PowerShell'i çalıştırmak için birden çok konak programlar kullanıyorsanız işlevleri, diğer adlar, değişkenler ve komutları CurrentUserAllHosts gibi tüm konak programlar etkileyen bir profilinde AllUsersAllHosts kaydedin ve işe özgü özellikler gibi Windows PowerShell ISE için renk ve yazı tipi özelleştirme için Windows PowerShell ISE profilini veya AllUsersCurrentHost profilini CurrentUserCurrentHost profilinde.</span><span class="sxs-lookup"><span data-stu-id="774fa-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="774fa-119">Oluşturulan ve kullanılan Windows PowerShell ISE'de profilleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="774fa-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="774fa-120">Her profil belirli kendi yoluna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="774fa-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="774fa-121">Profil türü</span><span class="sxs-lookup"><span data-stu-id="774fa-121">Profile Type</span></span> | <span data-ttu-id="774fa-122">Profil yolu</span><span class="sxs-lookup"><span data-stu-id="774fa-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="774fa-123">**Geçerli kullanıcı, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="774fa-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="774fa-124">`$PROFILE.CurrentUserCurrentHost`, veya `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="774fa-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="774fa-125">**Tüm kullanıcılar, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="774fa-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="774fa-126">**Geçerli kullanıcı, tüm konaklar**</span><span class="sxs-lookup"><span data-stu-id="774fa-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="774fa-127">**Tüm kullanıcılar, tüm konaklar**</span><span class="sxs-lookup"><span data-stu-id="774fa-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="774fa-128">Yeni bir profil oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="774fa-128">To create a new profile</span></span>

<span data-ttu-id="774fa-129">Yeni "geçerli bir kullanıcı, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="774fa-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="774fa-130">Yeni bir "Tüm kullanıcılar, Windows PowerShell ISE" oluşturmak için profili, bu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="774fa-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="774fa-131">"Geçerli kullanıcının tüm barındıran" yeni bir profil oluşturmak için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="774fa-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="774fa-132">"Tüm kullanıcılar, tüm barındıran" yeni bir profil oluşturmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="774fa-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="774fa-133">Bir profili düzenlemek için</span><span class="sxs-lookup"><span data-stu-id="774fa-133">To edit a profile</span></span>

1. <span data-ttu-id="774fa-134">Profil açmak için komut psedit düzenlemek istediğiniz profili belirten değişkeni ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="774fa-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="774fa-135">Örneğin, "geçerli kullanıcının, Windows PowerShell ISE" açmak için profil, yazın: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="774fa-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="774fa-136">Bazı öğeler profilinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="774fa-136">Add some items to your profile.</span></span> <span data-ttu-id="774fa-137">Başlamanıza yardımcı olmak için bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="774fa-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="774fa-138">Konsol bölmesinde, profili dosya türünü mavi varsayılan arka plan rengini değiştirmek için: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="774fa-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="774fa-139">$PsISE değişken hakkında daha fazla bilgi için bkz. [Windows PowerShell ISE nesne modeli başvurusu](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="774fa-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="774fa-140">Profil dosya türü 20 yazı tipi boyutunu değiştirmek için: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="774fa-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="774fa-141">Profil dosyanızı ile tasarruf için **dosya** menüsünde tıklatın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="774fa-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="774fa-142">Özelleştirmelerinizi Windows PowerShell ISE, sonraki açışınızda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="774fa-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="774fa-143">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="774fa-143">See Also</span></span>

- [<span data-ttu-id="774fa-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="774fa-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="774fa-145">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="774fa-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)