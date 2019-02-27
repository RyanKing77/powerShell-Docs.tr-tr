---
title: PSModulePath yükleme yolunu değiştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846511"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="fd8f8-102">PSModulePath Yükleme Yolunu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fd8f8-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="fd8f8-103">`PSModulePath` Ortam değişkeni yollarınızı diske yüklü modülleri depolar.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="fd8f8-104">Windows PowerShell, bu değişken, kullanıcı bir modül tam yolunu belirtmediğinde modülleri bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="fd8f8-105">Bu değişken yollar göründükleri sırayla aranır.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="fd8f8-106">Windows PowerShell başladığında `PSModulePath` aşağıdaki varsayılan değerine sahip bir sistem ortam değişkeni olarak oluşturulur: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="fd8f8-107">PSModulePath değişkeni görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="fd8f8-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="fd8f8-108">Belirtilen yollarını görüntülemek için `PSModulePath` değişken, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="fd8f8-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="fd8f8-109">Konumları PSModulePath değişkeni eklemek için</span><span class="sxs-lookup"><span data-stu-id="fd8f8-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="fd8f8-110">Bu değişken için yol eklemek için aşağıdaki yöntemlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="fd8f8-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="fd8f8-111">Yalnızca geçerli oturum için kullanılabilir olan bir geçici değer eklemek için komut satırında aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd8f8-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="fd8f8-112">Her bir oturum açıldığında kullanılabilir kalıcı bir değer eklemek için bir Windows PowerShell profiliniz için aşağıdaki komutu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fd8f8-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="fd8f8-113">Profilleri hakkında daha fazla bilgi için bkz. [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="fd8f8-114">Kayıt defterinde kalıcı olarak değişken eklemek, adlı yeni bir kullanıcı ortam değişkeni oluşturma `PSModulePath` kullanarak ortam değişkenlerini Düzenleyicisi'nde **Sistem Özellikleri** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="fd8f8-115">Bir komut dosyası kullanarak kalıcı bir değişken eklemek için **SetEnvironmentVariable** ortam sınıfını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="fd8f8-116">Örneğin, aşağıdaki komut dosyasını "C:\Program Files\Fabrikam\Module yolu. bilgisayarın PSModulePath ortam değişkeninin değerine ekler</span><span class="sxs-lookup"><span data-stu-id="fd8f8-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="fd8f8-117">Yol kullanıcı PSModulePath ortam değişkeni eklemek için "Kullanıcı" hedef ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="fd8f8-118">Konumları PSModulePath kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="fd8f8-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="fd8f8-119">Benzer yöntemler kullanarak değişkeninden yolları kaldırabilirsiniz: Örneğin, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` kaldıracak **c:\ModulePath** geçerli oturumun yolu.</span><span class="sxs-lookup"><span data-stu-id="fd8f8-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd8f8-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="fd8f8-120">See Also</span></span>

[<span data-ttu-id="fd8f8-121">Bir Windows PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="fd8f8-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
