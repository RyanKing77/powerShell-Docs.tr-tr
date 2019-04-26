---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: Yerel PSRepositories ile çalışma
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084105"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="194bc-103">Yerel PowerShellGet depoları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="194bc-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="194bc-104">PowerShellGet modülü desteği, PowerShell Galerisi dışındaki depolar.</span><span class="sxs-lookup"><span data-stu-id="194bc-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="194bc-105">Bu cmdlet'ler aşağıdaki senaryolara olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="194bc-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="194bc-106">Ortamınızda PowerShell modülleri güvenilir, önceden doğrulanmış kümesi desteği</span><span class="sxs-lookup"><span data-stu-id="194bc-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="194bc-107">PowerShell modülleri veya betikleri bir CI/CD işlem hattı test etme</span><span class="sxs-lookup"><span data-stu-id="194bc-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="194bc-108">PowerShell betikleri ve modülleri Internet'e sistemlerine sunun</span><span class="sxs-lookup"><span data-stu-id="194bc-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="194bc-109">Bu makalede, yerel bir PowerShell deposu ayarlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="194bc-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="194bc-110">Makaleyi de kapsayan [OfflinePowerShellGetDeploy][] PowerShell Galerisi'nden modül.</span><span class="sxs-lookup"><span data-stu-id="194bc-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="194bc-111">Bu modül, yerel deponuzu PowerShellGet en son sürümünü yüklemek için cmdlet'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="194bc-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="194bc-112">Yerel depo türleri</span><span class="sxs-lookup"><span data-stu-id="194bc-112">Local repository types</span></span>

<span data-ttu-id="194bc-113">Yerel PSRepository oluşturmanın iki yolu vardır: NuGet sunucusu veya dosya paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="194bc-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="194bc-114">Her tür avantajları ve dezavantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="194bc-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="194bc-115">NuGet Server</span><span class="sxs-lookup"><span data-stu-id="194bc-115">NuGet Server</span></span>

| <span data-ttu-id="194bc-116">Olumlu yönleri</span><span class="sxs-lookup"><span data-stu-id="194bc-116">Advantages</span></span>| <span data-ttu-id="194bc-117">Olumsuz yönleri</span><span class="sxs-lookup"><span data-stu-id="194bc-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="194bc-118">PowerShellGallery işlevselliği yakından taklit eder</span><span class="sxs-lookup"><span data-stu-id="194bc-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="194bc-119">Çok katmanlı bir uygulama, operasyon ve Destek gerektirir</span><span class="sxs-lookup"><span data-stu-id="194bc-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="194bc-120">NuGet, Visual Studio, diğer araçlar ile tümleşir</span><span class="sxs-lookup"><span data-stu-id="194bc-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="194bc-121">Kimlik doğrulama modeli ve gerekli NuGet hesap yönetimi</span><span class="sxs-lookup"><span data-stu-id="194bc-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="194bc-122">NuGet destekleyen, meta verilerde `.Nupkg` paketleri</span><span class="sxs-lookup"><span data-stu-id="194bc-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="194bc-123">Yayınlama API anahtarı yönetim ve bakım gerektirir</span><span class="sxs-lookup"><span data-stu-id="194bc-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="194bc-124">Arama, paket yönetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="194bc-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="194bc-125">Dosya Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="194bc-125">File Share</span></span>

| <span data-ttu-id="194bc-126">Olumlu yönleri</span><span class="sxs-lookup"><span data-stu-id="194bc-126">Advantages</span></span>| <span data-ttu-id="194bc-127">Olumsuz yönleri</span><span class="sxs-lookup"><span data-stu-id="194bc-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="194bc-128">Kolay ayarlama, yedeklemek ve korumak</span><span class="sxs-lookup"><span data-stu-id="194bc-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="194bc-129">PowerShellGet tarafından kullanılan meta verileri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="194bc-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="194bc-130">Basit bir güvenlik modeli - paylaşım kullanıcı izinleri</span><span class="sxs-lookup"><span data-stu-id="194bc-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="194bc-131">Temel dosya paylaşımı ötesinde kullanıcı Arabirimi</span><span class="sxs-lookup"><span data-stu-id="194bc-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="194bc-132">Varolan öğelerini değiştirme gibi hiçbir kısıtlama</span><span class="sxs-lookup"><span data-stu-id="194bc-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="194bc-133">Sınırlı bir güvenlik ve kimin hangi güncelleştirmelerin, hiçbir kayıt</span><span class="sxs-lookup"><span data-stu-id="194bc-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="194bc-134">PowerShellGet, türü ve destekleyen sürümler ve bağımlılık yükleme bulma ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="194bc-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="194bc-135">Ancak, temel NuGet sunucularını veya dosya paylaşımları için PowerShell Galerisi için çalışan bazı özellikler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="194bc-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="194bc-136">Her şeyi bir - betikleri, modüller, DSC kaynakları veya rol işlevleri hiçbir ayrım paketidir.</span><span class="sxs-lookup"><span data-stu-id="194bc-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="194bc-137">Paket meta etiketleri dahil olmak üzere, dosya paylaşımı sunucuları göremez.</span><span class="sxs-lookup"><span data-stu-id="194bc-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="194bc-138">Yerel bir depo oluşturma</span><span class="sxs-lookup"><span data-stu-id="194bc-138">Creating a local repository</span></span>

<span data-ttu-id="194bc-139">Aşağıdaki makalede kendi NuGet sunucusu kurma adımları listelenir.</span><span class="sxs-lookup"><span data-stu-id="194bc-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="194bc-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="194bc-140">[NuGet.Server][]</span></span>

<span data-ttu-id="194bc-141">Paketleri ekleme noktaya kadar adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="194bc-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="194bc-142">Adımları [bir paket yayımlama](#publishing-to-a-local-repository) bu makalenin sonraki bölümlerinde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="194bc-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="194bc-143">Bir dosya paylaşımı tabanlı deposu için kullanıcılarınızın dosya paylaşımına erişmek için izinlere sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="194bc-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="194bc-144">Yerel bir depoya kaydetme</span><span class="sxs-lookup"><span data-stu-id="194bc-144">Registering a local repository</span></span>

<span data-ttu-id="194bc-145">Bir depo kullanılabilmesi için önce onu kullanarak kaydedilmelidir `Register-PSRepository` komutu.</span><span class="sxs-lookup"><span data-stu-id="194bc-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="194bc-146">Aşağıdaki örneklerde **InstallationPolicy** ayarlanır *güvenilen*, kendi deponuzu güven varsayımına üzerinde.</span><span class="sxs-lookup"><span data-stu-id="194bc-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="194bc-147">İki komut nasıl işleneceğini arasındaki farkı Not **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="194bc-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="194bc-148">Dosya Paylaşımı tabanlı depoları **SourceLocation** ve **ScriptSourceLocation** eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="194bc-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="194bc-149">Web tabanlı bir depo için farklı olmalıdır bunu Bu örnekte bir sondaki "/" eklenir **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="194bc-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="194bc-150">Yeni oluşturulan PSRepository varsayılan depoyu olmasını istiyorsanız, diğer tüm PSRepositories kaydını silmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="194bc-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="194bc-151">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="194bc-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="194bc-152">Depo adı 'PSGallery' PowerShell Galerisi tarafından kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="194bc-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="194bc-153">PSGallery kaydını kaldırabilirsiniz, ancak farklı bir depoda PSGallery adı yeniden kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="194bc-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="194bc-154">PSGallery geri yüklemeniz gerekirse, aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="194bc-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="194bc-155">Yerel bir depo yayımlama</span><span class="sxs-lookup"><span data-stu-id="194bc-155">Publishing to a local repository</span></span>

<span data-ttu-id="194bc-156">Yerel PSRepository kaydettikten sonra yerel PSRepository için yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="194bc-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="194bc-157">Yayımlama iki ana senaryo vardır: kendi modül yayımlama ve PSGallery modülünden yayımlama.</span><span class="sxs-lookup"><span data-stu-id="194bc-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="194bc-158">Bir modül, yazılan yayımlama</span><span class="sxs-lookup"><span data-stu-id="194bc-158">Publishing a module you authored</span></span>

<span data-ttu-id="194bc-159">Kullanım `Publish-Module` ve `Publish-Script` modülünüzde, yerel PSRepository için PowerShell Galerisi için bunu aynı şekilde yayımlamak için.</span><span class="sxs-lookup"><span data-stu-id="194bc-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="194bc-160">Kodunuz için konumu belirtin</span><span class="sxs-lookup"><span data-stu-id="194bc-160">Specify the location for your code</span></span>
- <span data-ttu-id="194bc-161">Bir API anahtarı sağlayın</span><span class="sxs-lookup"><span data-stu-id="194bc-161">Supply an API key</span></span>
- <span data-ttu-id="194bc-162">Depo adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="194bc-162">Specify the repository name.</span></span> <span data-ttu-id="194bc-163">Örneğin, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="194bc-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="194bc-164">NuGet sunucusu bir hesap oluşturma ardından oluşturmak ve API anahtarını kaydetmek oturum açın.</span><span class="sxs-lookup"><span data-stu-id="194bc-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="194bc-165">Bir dosya paylaşımı için herhangi bir boş olmayan dize NuGetApiKey değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="194bc-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="194bc-166">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="194bc-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="194bc-167">Güvenliğini sağlamak için API anahtarları betiklerde sabit kodlanmış olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="194bc-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="194bc-168">Güvenli anahtar yönetimi sistemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="194bc-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="194bc-169">Bir modülden PSGallery yayımlama</span><span class="sxs-lookup"><span data-stu-id="194bc-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="194bc-170">Bir modülden PSGallery için yerel PSRepository yayımlamak için 'Kaydet-Package' cmdlet'ini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="194bc-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="194bc-171">Paket adını belirtin</span><span class="sxs-lookup"><span data-stu-id="194bc-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="194bc-172">'NuGet' sağlayıcısı olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="194bc-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="194bc-173">Kaynak (PSGallery konumu belirtin https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="194bc-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="194bc-174">Yerel deponuzu yolunu belirtin</span><span class="sxs-lookup"><span data-stu-id="194bc-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="194bc-175">Örnek:</span><span class="sxs-lookup"><span data-stu-id="194bc-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="194bc-176">Web tabanlı, yerel PSRepository ise nuget.exe yayımlamak için kullandığı ek bir adım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="194bc-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="194bc-177">Kullanmaya yönelik belgeler bkz [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="194bc-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="194bc-178">Bağlantısı kesilmiş bir sisteme PowerShellGet yükleme</span><span class="sxs-lookup"><span data-stu-id="194bc-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="194bc-179">PowerShellGet dağıtma, internet'ten kesilecek sistemleri gerektiren ortamlarda zordur.</span><span class="sxs-lookup"><span data-stu-id="194bc-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="194bc-180">PowerShellGet ilk kez kullanıldığı en son sürümü yükleyen bir önyükleme işlemi var.</span><span class="sxs-lookup"><span data-stu-id="194bc-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="194bc-181">PowerShell Galerisi OfflinePowerShellGetDeploy modülünde bu önyükleme işlemini destekleyecek cmdlet'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="194bc-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="194bc-182">Çevrimdışı bir dağıtım bootstrap için için gerekir:</span><span class="sxs-lookup"><span data-stu-id="194bc-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="194bc-183">OfflinePowerShellGetDeploy, İnternet'e bağlı sistem ve bağlantısı kesilmiş sistemlerinizi indirip yükleyin</span><span class="sxs-lookup"><span data-stu-id="194bc-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="194bc-184">PowerShellGet ve kullanarak İnternet'e bağlı sistem bağımlılıklarını karşıdan `Save-PowerShellGetForOffline` cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="194bc-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="194bc-185">PowerShellGet ve bağımlılıklarını İnternet'e bağlı sistemden, bağlantısı kesilmiş sunucuya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="194bc-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="194bc-186">Kullanım `Install-PowerShellGetOffline` PowerShellGet ve bağımlılıklarının doğru klasörler halinde yerleştirmek için bağlantısı kesik sistemdeki</span><span class="sxs-lookup"><span data-stu-id="194bc-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="194bc-187">Aşağıdaki komutları kullanın `Save-PowerShellGetForOffline` tüm bileşenlerin bir klasöre koymak için `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="194bc-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="194bc-188">Bu noktada, içeriğini yapmalısınız `F:\OfflinePowerShellGet` bağlantısı kesilmiş sistemleriniz için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="194bc-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="194bc-189">Çalıştırma `Install-PowerShellGetOffline` cmdlet'ini PowerShellGet bağlantısı kesilmiş sisteme yükleyin.</span><span class="sxs-lookup"><span data-stu-id="194bc-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="194bc-190">Bir PowerShell oturumunda aşağıdaki komutları çalıştırmadan önce PowerShellGet çalıştırmayın önemlidir.</span><span class="sxs-lookup"><span data-stu-id="194bc-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="194bc-191">PowerShellGet oturuma yüklendikten sonra bileşenlerin güncelleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="194bc-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="194bc-192">PowerShellGet yanlışlıkla başlatırsanız, çıkmak ve PowerShell yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="194bc-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="194bc-193">Bu komutları çalıştırdıktan sonra yerel deponuzu PowerShellGet yayımlamak hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="194bc-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="194bc-194">Güvenliğini sağlamak için API anahtarları betiklerde sabit kodlanmış olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="194bc-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="194bc-195">Güvenli anahtar yönetimi sistemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="194bc-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
