---
ms.date: 12/12/2018
keywords: DSC, powershell, kaynak, Galeri, Kurulum
title: Ek DSC kaynakları yükleme
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686386"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="50c38-103">Ek DSC kaynakları yükleme</span><span class="sxs-lookup"><span data-stu-id="50c38-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="50c38-104">PowerShell Desired State Configuration (DSC) için çeşitli kullanıma hazır kaynaklar içerir.</span><span class="sxs-lookup"><span data-stu-id="50c38-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="50c38-105">**Da PSDesiredStateConfiguration** modülü PowerShell belirli örneğinde kullanılabilir tüm OOB DSC kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="50c38-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="50c38-106">Bu kaynağın özellikleri açıklaması ve PowerShell 4.0 sürümünü de dahil OOB kaynakların listesidir.</span><span class="sxs-lookup"><span data-stu-id="50c38-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="50c38-107">OOB kaynak sayısı her PowerShell sürümüyle büyümüştür gibi eksik bir listesini budur.</span><span class="sxs-lookup"><span data-stu-id="50c38-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="50c38-108">Kaynak</span><span class="sxs-lookup"><span data-stu-id="50c38-108">Resource</span></span>  |<span data-ttu-id="50c38-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50c38-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="50c38-110">**Dosya**</span><span class="sxs-lookup"><span data-stu-id="50c38-110">**File**</span></span>|<span data-ttu-id="50c38-111">Dosyalar ve dizinler durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="50c38-111">Controls the state of files and directories.</span></span> <span data-ttu-id="50c38-112">Dosyaları kopyalayan bir **kaynak** için bir **hedef** ve bunları güncelleştiren olduğunda **kaynak** tarihler, sağlama ve karma değerlerini karşılaştırarak değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="50c38-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="50c38-113">**Arşiv**</span><span class="sxs-lookup"><span data-stu-id="50c38-113">**Archive**</span></span>|<span data-ttu-id="50c38-114">Arşivler ve belirli bir konuma ayıklar.</span><span class="sxs-lookup"><span data-stu-id="50c38-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="50c38-115">Belirtilen bir arşivlerle doğrular **sağlama toplamı**.</span><span class="sxs-lookup"><span data-stu-id="50c38-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="50c38-116">**Ortam**</span><span class="sxs-lookup"><span data-stu-id="50c38-116">**Environment**</span></span>|<span data-ttu-id="50c38-117">Ortam değişkenlerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="50c38-117">Manages environment variables.</span></span>|
|<span data-ttu-id="50c38-118">**Grup**</span><span class="sxs-lookup"><span data-stu-id="50c38-118">**Group**</span></span>|<span data-ttu-id="50c38-119">Yerel gruplar yönetir ve grup üyeliği denetler.</span><span class="sxs-lookup"><span data-stu-id="50c38-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="50c38-120">**Günlük**</span><span class="sxs-lookup"><span data-stu-id="50c38-120">**Log**</span></span>|<span data-ttu-id="50c38-121">İleti yazar `Microsoft-Windows-Desired State Configuration/Analytic` olay günlüğü.</span><span class="sxs-lookup"><span data-stu-id="50c38-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="50c38-122">**Paket**</span><span class="sxs-lookup"><span data-stu-id="50c38-122">**Package**</span></span>|<span data-ttu-id="50c38-123">Yükler veya kaldırır kullanarak paketleri **bağımsız değişkenleri**, **LogPath**, **ReturnCode**, diğer ayarları.</span><span class="sxs-lookup"><span data-stu-id="50c38-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="50c38-124">**kayıt defteri**</span><span class="sxs-lookup"><span data-stu-id="50c38-124">**Registry**</span></span>|<span data-ttu-id="50c38-125">Kayıt defteri anahtarları ve değerleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="50c38-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="50c38-126">**Komut dosyası**</span><span class="sxs-lookup"><span data-stu-id="50c38-126">**Script**</span></span>|<span data-ttu-id="50c38-127">Tasarlamak, kendi sağlar [get sınama kümesi](../resources/get-test-set.md) betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="50c38-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="50c38-128">**Hizmet**</span><span class="sxs-lookup"><span data-stu-id="50c38-128">**Service**</span></span>|<span data-ttu-id="50c38-129">Windows Hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="50c38-129">Configures Windows services.</span></span>|
|<span data-ttu-id="50c38-130">**Kullanıcı**</span><span class="sxs-lookup"><span data-stu-id="50c38-130">**User**</span></span> |<span data-ttu-id="50c38-131">Yerel Kullanıcılar ve öznitelikleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="50c38-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="50c38-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="50c38-132">**WindowsFeature**</span></span>|<span data-ttu-id="50c38-133">Rol ve özellik yönetir.</span><span class="sxs-lookup"><span data-stu-id="50c38-133">Manages roles and features.</span></span>|
|<span data-ttu-id="50c38-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="50c38-134">**WindowsProcess**</span></span>|<span data-ttu-id="50c38-135">Windows işlemleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="50c38-135">Configures Windows processes.</span></span>|

<span data-ttu-id="50c38-136">OOB kaynakları sık kullanılan işlemler için iyi bir başlangıç noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="50c38-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="50c38-137">OOB kaynakları gereksinimlerinizi karşılamıyorsa, kendi yazabileceğiniz [özel kaynak](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="50c38-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="50c38-138">Sorununuzu çözmek için özel bir kaynak yazmadan önce hem Microsoft hem de PowerShell topluluğu tarafından zaten oluşturulmuş DSC kaynakları geniş sayısı üzerinden görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="50c38-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="50c38-139">DSC kaynakları hem de bulabilirsiniz [PowerShell Galerisi](https://www.powershellgallery.com/) ve [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="50c38-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="50c38-140">PowerShell Konsolu kullanarak doğrudan gelen DSC kaynakları da yükleyebilirsiniz [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="50c38-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="50c38-141">PowerShellGet yükleme</span><span class="sxs-lookup"><span data-stu-id="50c38-141">Installing PowerShellGet</span></span>

<span data-ttu-id="50c38-142">Zaten varsa belirlemek için **PowerShell** alın veya yükleme Yardım almak için aşağıdaki Kılavuzu'na bakın: [PowerShellGet yükleme](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="50c38-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="50c38-143">PowerShellGet kullanarak DSC kaynakları bulma</span><span class="sxs-lookup"><span data-stu-id="50c38-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="50c38-144">Bir kez **PowerShellGet** yüklenir, sisteminizde bulmak ve barındırılan DSC kaynaklarını yüklemek [PowerShell Galerisi](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="50c38-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="50c38-145">İlk olarak, [Bul-DSCResource](/powershell/module/powershellget/find-dscresource) DSC kaynakları bulmak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="50c38-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="50c38-146">Çalıştırdığınızda `Find-DSCResource` ilk kez, "NuGet sağlayıcısı" yüklemek için aşağıdaki iletiyi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="50c38-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="50c38-147">Tuşlarına basarak 'y', sonra "NuGet" sağlayıcının yüklü olduğundan, PowerShell Galerisi'nden yüklemek için kullanabileceğiniz DSC kaynakların bir listesini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="50c38-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="50c38-148">Çok büyük olduğundan listesinde gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="50c38-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="50c38-149">Belirtebilirsiniz `-Name` parametresi joker karakterler kullanarak veya `-Filter` aramanızı daraltmak için joker karakter içermeyen bir parametre.</span><span class="sxs-lookup"><span data-stu-id="50c38-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="50c38-150">Bu örnekte, joker karakterlerini kullanarak bir "Saat dilimi" DSC kaynağı bulmayı dener.</span><span class="sxs-lookup"><span data-stu-id="50c38-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50c38-151">Şu anda bir hata var. `Find-DSCResource` hem de joker karakter kullanılması engelleyen cmdlet'i `-Name` ve `-Filter` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="50c38-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="50c38-152">Kullanarak bir geçici çözüm aşağıdaki ikinci örnekte gösterilir `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="50c38-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="50c38-153">Ayrıca `Where-Object` daha ayrıntılı filtrelemeyle DSC kaynakları bulmak için.</span><span class="sxs-lookup"><span data-stu-id="50c38-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="50c38-154">Bu yaklaşım, parametreleri filtreleme içinde yerleşik kullanmaktan daha yavaş olur.</span><span class="sxs-lookup"><span data-stu-id="50c38-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="50c38-155">Filtreleme hakkında daha fazla bilgi için bkz: [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="50c38-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="50c38-156">DSC kaynakları PowerShellGet kullanarak yükleme</span><span class="sxs-lookup"><span data-stu-id="50c38-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="50c38-157">DSC kaynak yüklemek için kullanın [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet modülünün altında gösterilen adı belirterek, **Modülü** arama sonuçlarındaki adı.</span><span class="sxs-lookup"><span data-stu-id="50c38-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="50c38-158">"Saat dilimi" kaynak "ComputerManagementDSC" modülünde, bu nedenle diğer bir deyişle bu örnek modülünü yükler var.</span><span class="sxs-lookup"><span data-stu-id="50c38-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="50c38-159">PowerShell Galerisi güvenilir değil, aşağıda onaylanmasını isteyen bir uyarı görürsünüz ve sonraki komut istemlerini önlemek nasıl söyleyen yükler.</span><span class="sxs-lookup"><span data-stu-id="50c38-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="50c38-160">Modülünü yüklemeye devam etmek için ' y' tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="50c38-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="50c38-161">Yüklemeyi tamamladıktan sonra yeni kaynak kullanarak yüklü olduğunu doğrulayabilirsiniz [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="50c38-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="50c38-162">Belirterek, yeni yüklenen modülde diğer kaynakları görüntüleyebilir `-ModuleName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="50c38-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="50c38-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c38-163">See also</span></span>

- [<span data-ttu-id="50c38-164">Kaynaklar nelerdir?</span><span class="sxs-lookup"><span data-stu-id="50c38-164">What are Resources?</span></span>](../resources/resources.md)
