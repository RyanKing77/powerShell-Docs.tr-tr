---
title: Bir Windows PowerShell sürücüsünü sağlayıcı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055659"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="b04d9-102">Windows PowerShell Sürücü Sağlayıcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b04d9-103">Bu konuda, bir Windows PowerShell sürücüsü bir veri deposuna erişmek için bir yol sağlayan bir Windows PowerShell sürücüsü sağlayıcısı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="b04d9-104">Bu tür sağlayıcısı, aynı zamanda Windows PowerShell sürücüsü sağlayıcıları olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b04d9-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="b04d9-105">Sağlayıcı tarafından kullanılan Windows PowerShell sürücülerini veri deposuna bağlanmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="b04d9-106">Burada açıklanan Windows PowerShell sürücüsü sağlayıcısı, bir Microsoft Access veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="b04d9-107">Bu sağlayıcı için Windows PowerShell sürücüsünü (mümkündür bir sürücü sağlayıcısı için herhangi bir sayıda sürücüler ekleme), veritabanı temsil eder. sürücünün en üst düzey kapsayıcıları veritabanındaki tabloları temsil eder ve satırlarda kapsayıcıları öğelerini temsil eder tablolar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="b04d9-108">Bu konudaki bölümler listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="b04d9-109">Bir Windows PowerShell sürücüsü sağlayıcısı yazma ile alışkın değilseniz, göründükleri sırayla bu bölümleri okuyun.</span><span class="sxs-lookup"><span data-stu-id="b04d9-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="b04d9-110">Ancak, bir sürücü sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.</span><span class="sxs-lookup"><span data-stu-id="b04d9-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="b04d9-111">Windows PowerShell sağlayıcısındaki sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="b04d9-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="b04d9-112">Temel işlevlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="b04d9-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="b04d9-113">Sürücü durumu bilgilerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="b04d9-114">Bir sürücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="b04d9-115">Dinamik parametreler için NewDrive ekleme</span><span class="sxs-lookup"><span data-stu-id="b04d9-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="b04d9-116">Bir sürücü kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="b04d9-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="b04d9-117">Varsayılan başlatma sürücüleri</span><span class="sxs-lookup"><span data-stu-id="b04d9-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="b04d9-118">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="b04d9-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="b04d9-119">Windows PowerShell sürücüsünü sağlayıcıyı test etme</span><span class="sxs-lookup"><span data-stu-id="b04d9-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="b04d9-120">Windows PowerShell sağlayıcısındaki sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="b04d9-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="b04d9-121">Sürücü sağlayıcınız, türetilen bir .NET sınıfı tanımlamanız gerekir [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b04d9-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="b04d9-122">Bu sürücü sağlayıcısı için sınıf tanımı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b04d9-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b04d9-123">Bu örnekte, dikkat [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) sağlayıcı ve Windows PowerShell belirli bir özellik için bir kolay ad özniteliğini belirtir, sağlayıcı Windows PowerShell çalışma zamanına komut işleme sırasında ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="b04d9-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="b04d9-124">Sağlayıcı özellikleri için olası değerler tarafından tanımlanan [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="b04d9-125">Bu sürücü sağlayıcısı bu özellikleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b04d9-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="b04d9-126">Temel işlevlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="b04d9-126">Defining Base Functionality</span></span>

<span data-ttu-id="b04d9-127">Bölümünde anlatıldığı gibi [tasarım bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıf türetilir [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) temel sınıf başlatma ve başlatmayı kaldırma sağlayıcı için gereken yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="b04d9-128">Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak için işlevselliği uygulamak için bkz: [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b04d9-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="b04d9-129">Ancak, çoğu sağlayıcıları (burada açıklanan sağlayıcısı dahil), Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b04d9-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="b04d9-130">Sürücü durumu bilgilerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-130">Creating Drive State Information</span></span>

<span data-ttu-id="b04d9-131">Tüm Windows PowerShell sağlayıcıları sürücü sağlayıcınız sağlayıcınız çağırdığında, Windows PowerShell çalışma zamanı tarafından gereken herhangi bir durum bilgisini oluşturmak için gerek duyduğu anlamına gelir durum bilgisi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="b04d9-132">Bu sürücü sağlayıcısı için kitaplığın sürücü bilgilerinin bir parçası olarak tutulur veritabanına bağlantı durumu bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="b04d9-133">Bu bilgileri nasıl depolandığını gösteren kod işte [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) sürücü açıklayan nesnesi:</span><span class="sxs-lookup"><span data-stu-id="b04d9-133">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="b04d9-134">Bir sürücü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-134">Creating a Drive</span></span>

<span data-ttu-id="b04d9-135">Bir sürücü oluşturmak Windows PowerShell çalışma zamanı izin vermek için sürücü sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="b04d9-136">Aşağıdaki kod uygulamasını gösterir [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi bu sürücü sağlayıcısı için:</span><span class="sxs-lookup"><span data-stu-id="b04d9-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b04d9-137">Bu yöntemi geçersiz kılma aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="b04d9-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="b04d9-138">Doğrulayın [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) üyesi var ve veri deposuna bağlantı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-138">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="b04d9-139">Bir sürücü oluşturmak ve support, bağlantı üye doldurmak `New-PSDrive` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b04d9-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="b04d9-140">Doğrulama [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) önerilen sürücü için nesne.</span><span class="sxs-lookup"><span data-stu-id="b04d9-140">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="b04d9-141">Değiştirme [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) sürücü gerekli performans veya güvenilirlik bilgileri açıklayan nesne ya da bu sürücüyü kullanıp arayanlar için ek verileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b04d9-141">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="b04d9-142">Kullanarak hatalarını [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) yöntemi ve ardından return `null`.</span><span class="sxs-lookup"><span data-stu-id="b04d9-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="b04d9-143">Bu yöntem, yöntem veya bir sağlayıcıya özgü sürümü geçilen ya da sürücü bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b04d9-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="b04d9-144">Dinamik parametreler için NewDrive ekleme</span><span class="sxs-lookup"><span data-stu-id="b04d9-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="b04d9-145">`New-PSDrive` Cmdlet'i sürücü sağlayıcınız tarafından desteklenen ek parametreler gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="b04d9-146">Bu dinamik parametreler cmdlet'e iliştirmek için sağlayıcı uygulayan [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="b04d9-147">Bu yöntem, özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne.</span><span class="sxs-lookup"><span data-stu-id="b04d9-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="b04d9-148">Bu sürücü sağlayıcısı bu yöntemi geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="b04d9-148">This drive provider does not override this method.</span></span> <span data-ttu-id="b04d9-149">Ancak, aşağıdaki kod, bu yöntem varsayılan uygulanışı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b04d9-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="b04d9-150">Bir sürücü kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="b04d9-150">Removing a Drive</span></span>

<span data-ttu-id="b04d9-151">Veritabanı bağlantısını kapatmak için sürücü sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="b04d9-152">Bu yöntem, bir sağlayıcıya özgü bilgileri temizleniyor sonra sürücü bağlantıyı kapatır.</span><span class="sxs-lookup"><span data-stu-id="b04d9-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="b04d9-153">Aşağıdaki kod uygulamasını gösterir [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi bu sürücü sağlayıcısı için:</span><span class="sxs-lookup"><span data-stu-id="b04d9-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b04d9-154">Sürücü kaldırılabilir, yöntem yöntemine geçirilen bilgileri döndürmelidir `drive` parametresi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="b04d9-155">Sürücü kaldırılamazsa yöntemi bir özel durum yazma ve ardından dönün `null`.</span><span class="sxs-lookup"><span data-stu-id="b04d9-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="b04d9-156">Sağlayıcınız bu yöntemi yok sayın değil, bu yöntem varsayılan uygulaması yalnızca giriş olarak geçirilen sürücü bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b04d9-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="b04d9-157">Varsayılan başlatma sürücüleri</span><span class="sxs-lookup"><span data-stu-id="b04d9-157">Initializing Default Drives</span></span>

<span data-ttu-id="b04d9-158">Sürücü sağlayıcısı uygular [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) sürücüleri bağlamak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="b04d9-159">Örneğin, Active Directory Sağlayıcısı varsayılan olarak bilgisayarın bir etki alanına katılmışsa adlandırma bağlamı için bir sürücü bağlama.</span><span class="sxs-lookup"><span data-stu-id="b04d9-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="b04d9-160">Bu yöntem, başlatılmış sürücüleriyle ilgili sürücü bilgileri koleksiyonunu ya da boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="b04d9-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="b04d9-161">Windows PowerShell çalışma zamanı çağrıları sonra bu yönteme bir çağrı yapılır [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Sağlayıcısı'nı başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="b04d9-162">Bu sürücü sağlayıcısı geçersiz [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b04d9-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="b04d9-163">Ancak, aşağıdaki kod, bir sürücü boş koleksiyonu döndürür. varsayılan uygulama gösterir:</span><span class="sxs-lookup"><span data-stu-id="b04d9-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="b04d9-164">InitializeDefaultDrives'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="b04d9-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="b04d9-165">Tüm sürücü sağlayıcıları kullanıcının bulunabilirliği yardımcı olmak için bir kök sürücü bağlamak.</span><span class="sxs-lookup"><span data-stu-id="b04d9-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="b04d9-166">Kök sürücü bağlı diğer sürücülerin kökleri görevi gören konumları listeleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b04d9-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="b04d9-167">Örneğin, Active Directory sağlayıcısı bulunan adlandırma bağlamlarının listeleyen bir sürücü oluşturabilirsiniz `namingContext` Dağıtılmış Sistem ortamı (DSE) kök öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b04d9-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="b04d9-168">Bu, bağlama noktaları diğer sürücüleri için keşfetmek kullanıcılara yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b04d9-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b04d9-169">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="b04d9-169">Code Sample</span></span>

<span data-ttu-id="b04d9-170">Tam örnek kod için bkz: [AccessDbProviderSample02 kod örneği](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b04d9-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="b04d9-171">Windows PowerShell sürücüsünü sağlayıcıyı test etme</span><span class="sxs-lookup"><span data-stu-id="b04d9-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b04d9-172">Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı olduğunda türetme tarafından kullanıma sunulan tüm cmdlet'leri dahil olmak üzere komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b04d9-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="b04d9-173">Şimdi örnek sürücü sağlayıcısı test edin.</span><span class="sxs-lookup"><span data-stu-id="b04d9-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="b04d9-174">Çalıştırma `Get-PSProvider` AccessDB sürücü sağlayıcısı mevcut olduğundan emin olmak için sağlayıcıları listesini almak için cmdlet:</span><span class="sxs-lookup"><span data-stu-id="b04d9-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="b04d9-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="b04d9-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="b04d9-176">Şu çıktı görünür:</span><span class="sxs-lookup"><span data-stu-id="b04d9-176">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="b04d9-177">Bir veritabanı sunucu adı (DSN) erişerek veritabanı için mevcut olduğundan emin olun **veri kaynakları** kısmı **Yönetimsel Araçlar** işletim sistemi için.</span><span class="sxs-lookup"><span data-stu-id="b04d9-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="b04d9-178">İçinde **Kullanıcı DSN** tablo, çift **MS Access veritabanı** C:\ps\northwind.mdb sürücü yolu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b04d9-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="b04d9-179">Örnek sürücü Sağlayıcısı'nı kullanarak yeni bir sürücüye oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b04d9-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="b04d9-180">**PS > psdrive yeni-adı mydb-c:\ps\northwind.mdb - psprovider AccessDb kök**</span><span class="sxs-lookup"><span data-stu-id="b04d9-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="b04d9-181">Şu çıktı görünür:</span><span class="sxs-lookup"><span data-stu-id="b04d9-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="b04d9-182">Bağlantıyı doğrulama.</span><span class="sxs-lookup"><span data-stu-id="b04d9-182">Validate the connection.</span></span> <span data-ttu-id="b04d9-183">Bağlantı sürücü üyesi olarak tanımlı olduğundan, Get-PDDrive cmdlet'ini kullanarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b04d9-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b04d9-184">Sağlayıcı, bu etkileşim için kapsayıcı işlevi gereksinimleriniz değiştikçe kullanıcı henüz bir sürücü olarak sağlayıcısı ile etkileşime giremezler.</span><span class="sxs-lookup"><span data-stu-id="b04d9-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="b04d9-185">Daha fazla bilgi için [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b04d9-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="b04d9-186">**PS > (get-psdrive mydb) .connection**</span><span class="sxs-lookup"><span data-stu-id="b04d9-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="b04d9-187">Şu çıktı görünür:</span><span class="sxs-lookup"><span data-stu-id="b04d9-187">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="b04d9-188">Sürücü kaldırın ve kabuktan çıkış yapma:</span><span class="sxs-lookup"><span data-stu-id="b04d9-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="b04d9-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="b04d9-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="b04d9-190">**PS > Çık**</span><span class="sxs-lookup"><span data-stu-id="b04d9-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="b04d9-191">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b04d9-191">See Also</span></span>

[<span data-ttu-id="b04d9-192">Windows PowerShell sağlayıcılar oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="b04d9-193">Windows PowerShell sağlayıcınız tasarlama</span><span class="sxs-lookup"><span data-stu-id="b04d9-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="b04d9-194">Temel Windows PowerShell sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b04d9-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)