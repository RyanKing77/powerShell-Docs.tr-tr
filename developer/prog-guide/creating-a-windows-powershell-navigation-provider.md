---
title: Bir Windows PowerShell Gezinti sağlayıcı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: cbc8ce0600553f9e9ab973d6f92ea5eafde310e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430049"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a><span data-ttu-id="768be-102">Windows PowerShell Gezinti Sağlayıcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-102">Creating a Windows PowerShell Navigation Provider</span></span>

<span data-ttu-id="768be-103">Bu konuda, veri deposu gidebilirsiniz bir Windows PowerShell Gezinti sağlayıcısı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="768be-103">This topic describes how to create a Windows PowerShell navigation provider that can navigate the data store.</span></span> <span data-ttu-id="768be-104">Bu tür sağlayıcısı özyinelemeli komutları, iç içe geçmiş kapsayıcılar ve göreli yolları destekler.</span><span class="sxs-lookup"><span data-stu-id="768be-104">This type of provider supports recursive commands, nested containers, and relative paths.</span></span>

> [!NOTE]
> <span data-ttu-id="768be-105">İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider05.cs).</span><span class="sxs-lookup"><span data-stu-id="768be-105">You can download the C# source file (AccessDBSampleProvider05.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="768be-106">Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="768be-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="768be-107">İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.</span><span class="sxs-lookup"><span data-stu-id="768be-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="768be-108">Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="768be-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="768be-109">Kullanıcı veritabanında veri tablolarına gidebilmeniz burada açıklanan sağlayıcının kullanıcı tanıtıcı bir Access veritabanının bir sürücü olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="768be-109">The provider described here enables the user handle an Access database as a drive so that the user can navigate to the data tables in the database.</span></span> <span data-ttu-id="768be-110">Kendi gezinme sağlayıcısı oluşturulurken gezinme için gerekli sürücü nitelenmiş yollar yapmak, göreli yollar Normalleştir, öğeleri alt adları almak, bir öğenin üst yolu ve test yöntemleri yanı sıra veri depolama, taşıma yöntemleri uygulayabilirsiniz. bir öğeyi tanımlamak için bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="768be-110">When creating your own navigation provider, you can implement methods that can make drive-qualified paths required for navigation, normalize relative paths, move items of the data store, as well as methods that get child names, get the parent path of an item, and test to identify if an item is a container.</span></span>

> [!CAUTION]
> <span data-ttu-id="768be-111">Bu tasarım bir alan adı Kimliğine sahip olan bir veritabanının varsayar ve alan türünü LongInteger olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="768be-111">Be aware that this design assumes a database that has a field with the name ID, and that the type of the field is LongInteger.</span></span>

<span data-ttu-id="768be-112">Aşağıdaki listede, bu konudaki bölümler içerir.</span><span class="sxs-lookup"><span data-stu-id="768be-112">The following list includes sections in this topic.</span></span> <span data-ttu-id="768be-113">Bir Windows PowerShell Gezinti sağlayıcısı yazma ile alışkın değilseniz, bu bilgileri göründüğü sırayla okuyun.</span><span class="sxs-lookup"><span data-stu-id="768be-113">If you are unfamiliar with writing a Windows PowerShell navigation provider, read this information in the order that it appears.</span></span> <span data-ttu-id="768be-114">Ancak, bir Windows PowerShell Gezinti sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.</span><span class="sxs-lookup"><span data-stu-id="768be-114">However, if you are familiar with writing a Windows PowerShell navigation provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="768be-115">PS Gezinti sağlayıcı sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="768be-115">Defining a PS Navigation Provider Class</span></span>](#Define-the-Windows-PowerShell-provider)

- [<span data-ttu-id="768be-116">Temel işlevlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="768be-116">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="768be-117">PS yol oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-117">Creating a PS Path</span></span>](#Creating-a-Windows-PowerShell-Path)

- [<span data-ttu-id="768be-118">Üst yolu alınıyor</span><span class="sxs-lookup"><span data-stu-id="768be-118">Retrieving the Parent Path</span></span>](#Retrieving-the-Parent-Path)

- [<span data-ttu-id="768be-119">Alt yol adı alınıyor</span><span class="sxs-lookup"><span data-stu-id="768be-119">Retrieving the Child Path Name</span></span>](#Retrieve-the-Child-Path-Name)

- [<span data-ttu-id="768be-120">Bir öğenin bir kapsayıcı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="768be-120">Determining if an Item is a Container</span></span>](#Determining-if-an-Item-is-a-Container)

- [<span data-ttu-id="768be-121">Bir öğe taşıma</span><span class="sxs-lookup"><span data-stu-id="768be-121">Moving an Item</span></span>](#Moving-an-Item)

- [<span data-ttu-id="768be-122">Dinamik parametreleri ekleme `Move-Item` cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="768be-122">Attaching Dynamic Parameters to the `Move-Item` Cmdlet</span></span>](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [<span data-ttu-id="768be-123">Göreli bir yol Normalleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="768be-123">Normalizing a Relative Path</span></span>](#Normalizing-a-Relative-Path)

- [<span data-ttu-id="768be-124">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="768be-124">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="768be-125">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="768be-125">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="768be-126">Windows PowerShell sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-126">Building the Windows PowerShell Provider</span></span>](#Building-the-Windows-PowerShell-provider)

- [<span data-ttu-id="768be-127">Windows PowerShell sağlayıcıyı test etme</span><span class="sxs-lookup"><span data-stu-id="768be-127">Testing the Windows PowerShell Provider</span></span>](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a><span data-ttu-id="768be-128">Windows PowerShell sağlayıcısını tanımlayın</span><span class="sxs-lookup"><span data-stu-id="768be-128">Define the Windows PowerShell provider</span></span>

<span data-ttu-id="768be-129">Bir Windows PowerShell Gezinti sağlayıcısı, türetilen bir .NET sınıfı oluşturmalısınız [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="768be-129">A Windows PowerShell navigation provider must create a .NET class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class.</span></span> <span data-ttu-id="768be-130">Bu bölümde açıklanan Gezinti sağlayıcısı için sınıf tanımı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="768be-130">Here is the class definition for the navigation provider described in this section.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

<span data-ttu-id="768be-131">Bu sağlayıcıda unutmayın [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) iki parametre özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="768be-131">Note that in this provider, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute includes two parameters.</span></span> <span data-ttu-id="768be-132">İlk parametre, kullanıcı dostu bir Windows PowerShell uygulamaları tarafından kullanılan sağlayıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="768be-132">The first parameter specifies a user-friendly name for the provider that is used by Windows PowerShell.</span></span> <span data-ttu-id="768be-133">İkinci parametre, sağlayıcı için Windows PowerShell çalışma zamanı komut işleme sırasında ortaya koyan Windows PowerShell belirli özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="768be-133">The second parameter specifies the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="768be-134">Bu sağlayıcı için eklenen hiçbir Windows PowerShell belirli özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="768be-134">For this provider, there are no Windows PowerShell specific capabilities that are added.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="768be-135">Temel işlevlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="768be-135">Defining Base Functionality</span></span>

<span data-ttu-id="768be-136">Bölümünde anlatıldığı gibi [tasarım sağlayıcınız PS](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıf farklı bir sağlayıcı sağlanan çeşitli diğer sınıflarından türetilen işlevselliği.</span><span class="sxs-lookup"><span data-stu-id="768be-136">As described in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) base class derives from several other classes that provided different provider functionality.</span></span> <span data-ttu-id="768be-137">Bir Windows PowerShell Gezinti sağlayıcısı, bu nedenle, tüm bu sınıfları tarafından sağlanan işlevselliği tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="768be-137">A Windows PowerShell navigation provider, therefore, must define all of the functionality provided by those classes.</span></span>

<span data-ttu-id="768be-138">Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak için işlevselliği uygulamak için bkz: [temel bir PS sağlayıcı oluşturma](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="768be-138">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic PS Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="768be-139">Ancak, çoğu sağlayıcıları (burada açıklanan sağlayıcısı dahil), Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="768be-139">However, most providers (including the provider described here) can use the default implementation of this functionality provided by Windows PowerShell.</span></span>

<span data-ttu-id="768be-140">Bir Windows PowerShell sürücüsü veri deposuna erişmek için yöntemlerini uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="768be-140">To get access to the data store through a Windows PowerShell drive, you must implement the methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="768be-141">Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="768be-141">For more information about implementing these methods, see [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

<span data-ttu-id="768be-142">Bir veri deposu, alma, ayarlama ve temizleme öğeleri gibi öğeleri işlemek için sağlayıcı tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="768be-142">To manipulate the items of a data store, such as getting, setting, and clearing items, the provider must implement the methods provided by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) base class.</span></span> <span data-ttu-id="768be-143">Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="768be-143">For more information about implementing these methods, see [Creating an Windows PowerShell Item Provider](./creating-a-windows-powershell-item-provider.md).</span></span>

<span data-ttu-id="768be-144">Alt öğeler veya oluşturma, kopyalama, yeniden adlandırmak ve öğeleri kaldırmak yöntemleri yanı sıra veri deposu, adlarını almak için tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="768be-144">To get to the child items, or their names, of the data store, as well as methods that create, copy, rename, and remove items, you must implement the methods provided by the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) base class.</span></span> <span data-ttu-id="768be-145">Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="768be-145">For more information about implementing these methods, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

## <a name="creating-a-windows-powershell-path"></a><span data-ttu-id="768be-146">Bir Windows PowerShell yol oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-146">Creating a Windows PowerShell Path</span></span>

<span data-ttu-id="768be-147">Windows PowerShell Gezinti sağlayıcısı veri deposunun öğeleri gitmek için bir sağlayıcı iç Windows PowerShell yol kullanın.</span><span class="sxs-lookup"><span data-stu-id="768be-147">Windows PowerShell navigation provider use a provider-internal Windows PowerShell path to navigate the items of the data store.</span></span> <span data-ttu-id="768be-148">Sağlayıcı bir sağlayıcı iç yolu oluşturmak için uygulaması [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) destekleyen bir yönteme birleştirme yolu cmdlet'inden çağırır.</span><span class="sxs-lookup"><span data-stu-id="768be-148">To create a provider-internal path the provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to supports calls from the Combine-Path cmdlet.</span></span> <span data-ttu-id="768be-149">Bu yöntem bir sağlayıcıya özgü yol ayırıcı arasındaki üst ve alt yolları kullanarak sağlayıcısı iç yolu, üst ve alt yolu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="768be-149">This method combines a parent and child path into a provider-internal path, using a provider-specific path separator between the parent and child paths.</span></span>

<span data-ttu-id="768be-150">Varsayılan uygulama alan yolları ile "/" veya "\\"yol ayırıcı olarak yolu ayırıcısı normalleştirir"\\", üst ve alt yol bölümleri arasındaki ayırıcı ile birleştirir ve ardından içeren bir dize döndürür. Birleşik yolları.</span><span class="sxs-lookup"><span data-stu-id="768be-150">The default implementation takes paths with "/" or "\\" as the path separator, normalizes the path separator to "\\", combines the parent and child path parts with the separator between them, and then returns a string that contains the combined paths.</span></span>

<span data-ttu-id="768be-151">Bu gezinti sağlayıcı, bu yöntem uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="768be-151">This navigation provider does not implement this method.</span></span> <span data-ttu-id="768be-152">Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="768be-152">However, the following code is the default implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a><span data-ttu-id="768be-153">MakePath'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-153">Things to Remember About Implementing MakePath</span></span>

<span data-ttu-id="768be-154">Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span><span class="sxs-lookup"><span data-stu-id="768be-154">The following conditions may apply to your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):</span></span>

- <span data-ttu-id="768be-155">Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi doğrulamamanız yolu yasal tam yol sağlayıcı ad alanı olarak.</span><span class="sxs-lookup"><span data-stu-id="768be-155">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method should not validate the path as a legal fully-qualified path in the provider namespace.</span></span> <span data-ttu-id="768be-156">Her parametre yalnızca yolun bir bölümünü temsil edebilir ve birleştirilmiş parçaları bir tam yol oluşturabilen değil unutmayın.</span><span class="sxs-lookup"><span data-stu-id="768be-156">Be aware that each parameter can only represent a part of a path, and the combined parts might not generate a fully-qualified path.</span></span> <span data-ttu-id="768be-157">Örneğin, [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) dosya sistemi sağlayıcısı yöntemi alma "windows\system32" `parent` parametresi ve "abc.dll"`child` parametresi.</span><span class="sxs-lookup"><span data-stu-id="768be-157">For example, the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method for the filesystem provider might receive "windows\system32" in the `parent` parameter and "abc.dll" in the `child` parameter.</span></span> <span data-ttu-id="768be-158">Yöntemi bu değerleri ile birleştiren "\\" ayırıcı ve "bir tam dosya sistemi yolu olmayan döndürür windows\system32\abc.dll",.</span><span class="sxs-lookup"><span data-stu-id="768be-158">The method joins these values with the "\\" separator and returns "windows\system32\abc.dll", which is not a fully-qualified file system path.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="768be-159">Çağrısında sağlanan yol bölümleri [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) sağlayıcı ad alanı içinde izin verilmeyen karakterleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="768be-159">The path parts provided in the call to [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) might contain characters not allowed in the provider namespace.</span></span> <span data-ttu-id="768be-160">Bu karakterler için joker karakter genişletmesi büyük olasılıkla kullanılır ve bu yöntemin uygulanmasını bunları kaldırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="768be-160">These characters are most likely used for wildcard expansion and the implementation of this method should not remove them.</span></span>

## <a name="retrieving-the-parent-path"></a><span data-ttu-id="768be-161">Üst yolu alınıyor</span><span class="sxs-lookup"><span data-stu-id="768be-161">Retrieving the Parent Path</span></span>

<span data-ttu-id="768be-162">Windows PowerShell Gezinti sağlayıcıları uygulamak [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) üst kısmını belirtilen tam veya kısmi alınacak yöntemi sağlayıcıya özgü yolu.</span><span class="sxs-lookup"><span data-stu-id="768be-162">Windows PowerShell navigation providers implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method to retrieve the parent part of the indicated full or partial provider-specific path.</span></span> <span data-ttu-id="768be-163">Yöntem yolunun alt parçası kaldırır ve üst yol bölümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-163">The method removes the child part of the path and returns the parent path part.</span></span> <span data-ttu-id="768be-164">`root` Parametresi bir sürücünün kökünü tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="768be-164">The `root` parameter specifies the fully-qualified path to the root of a drive.</span></span> <span data-ttu-id="768be-165">Bu parametre null ya da bir sürücünün alma işlemi için kullanımda değilse boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="768be-165">This parameter can be null or empty if a mounted drive is not in use for the retrieval operation.</span></span> <span data-ttu-id="768be-166">Bir kök belirtilmezse, kök olarak aynı ağacında bir kapsayıcıya yöntemi bir yol döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="768be-166">If a root is specified, the method must return a path to a container in the same tree as the root.</span></span>

<span data-ttu-id="768be-167">Örnek gezinme sağlayıcısı bu yöntemi yok sayın değil, ancak varsayılan uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="768be-167">The sample navigation provider does not override this method, but uses the default implementation.</span></span> <span data-ttu-id="768be-168">İkisi de yolları kabul ettiği "/" ve "\\" yol ayırıcıları olarak.</span><span class="sxs-lookup"><span data-stu-id="768be-168">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="768be-169">Önce yalnızca yolu normalleştirir "\\" Ayırıcılar, ardından üst yolu kapalı son böler "\\" ve üst yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-169">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the parent path.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a><span data-ttu-id="768be-170">GetParentPath'ı uygulama hakkında unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-170">To Remember About Implementing GetParentPath</span></span>

<span data-ttu-id="768be-171">Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi sağlayıcı ad alanı için yol ayırıcı yolunda sözcüksel olarak Böl.</span><span class="sxs-lookup"><span data-stu-id="768be-171">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method should split the path lexically on the path separator for the provider namespace.</span></span> <span data-ttu-id="768be-172">Örneğin, dosya sistemi sağlayıcısı için son aramak için bu yöntemi kullanır "\\" ve her şeyi ayırıcının solunda döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-172">For example, the filesystem provider uses this method to look for the last "\\" and returns everything to the left of the separator.</span></span>

## <a name="retrieve-the-child-path-name"></a><span data-ttu-id="768be-173">Alt yol adını alma</span><span class="sxs-lookup"><span data-stu-id="768be-173">Retrieve the Child Path Name</span></span>

<span data-ttu-id="768be-174">Gezinti sağlayıcı uygular, [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yönteminin öğesinin alt (yaprak öğe) adını almak için belirtilen tam bulunan veya Kısmi sağlayıcıya özgü yolu.</span><span class="sxs-lookup"><span data-stu-id="768be-174">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method to retrieve the name (leaf element) of the child of the item located at the indicated full or partial provider-specific path.</span></span>

<span data-ttu-id="768be-175">Örnek gezinme sağlayıcının bu yöntemi geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="768be-175">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="768be-176">Varsayılan uygulama, aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="768be-176">The default implementation is shown below.</span></span> <span data-ttu-id="768be-177">İkisi de yolları kabul ettiği "/" ve "\\" yol ayırıcıları olarak.</span><span class="sxs-lookup"><span data-stu-id="768be-177">It accepts paths that use both "/" and "\\" as path separators.</span></span> <span data-ttu-id="768be-178">Önce yalnızca yolu normalleştirir "\\" Ayırıcılar, ardından üst yolu kapalı son böler "\\" ve yol bölümü alt adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-178">It first normalizes the path to have only "\\" separators, then splits the parent path off at the last "\\" and returns the name of the child path part.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a><span data-ttu-id="768be-179">GetChildName'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-179">Things to Remember About Implementing GetChildName</span></span>

<span data-ttu-id="768be-180">Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi yol ayırıcısı yolunda sözcüksel olarak Böl.</span><span class="sxs-lookup"><span data-stu-id="768be-180">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method should split the path lexically on the path separator.</span></span> <span data-ttu-id="768be-181">Sağlanan yol hiçbir yol ayırıcıları içeriyorsa, yöntem üzerinde değişiklik yapılmadan yolu döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="768be-181">If the supplied path contains no path separators, the method should return the path unmodified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="768be-182">Bu yöntem çağrısında sağlanan yol sağlayıcı ad alanı içinde geçersiz karakterler içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="768be-182">The path provided in the call to this method might contain characters that are illegal in the provider namespace.</span></span> <span data-ttu-id="768be-183">Joker karakter genişletmesi veya normal ifadenin eşleştirilmesi için kullanılan bu karakterler büyük olasılıkla ve bu yöntemin uygulanmasını bunları kaldırmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="768be-183">These characters are most likely used for wildcard expansion or regular expression matching, and the implementation of this method should not remove them.</span></span>

## <a name="determining-if-an-item-is-a-container"></a><span data-ttu-id="768be-184">Bir öğenin bir kapsayıcı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="768be-184">Determining if an Item is a Container</span></span>

<span data-ttu-id="768be-185">Gezinti sağlayıcılarınızı uygulayabilirsiniz [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi belirtilen yol bir kapsayıcı sağlayacağını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="768be-185">The navigation provider can implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method to determine if the specified path indicates a container.</span></span> <span data-ttu-id="768be-186">Aksi takdirde bir kapsayıcı ve yanlış yolu temsil ediyorsa true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-186">It returns true if the path represents a container, and false otherwise.</span></span> <span data-ttu-id="768be-187">Kullanabilmek için bu yöntemi kullanıcının erişmesi `Test-Path` cmdlet için sağlanan yol.</span><span class="sxs-lookup"><span data-stu-id="768be-187">The user needs this method to be able to use the `Test-Path` cmdlet for the supplied path.</span></span>

<span data-ttu-id="768be-188">Aşağıdaki kodda gösterildiği [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) bizim örnek Gezinti sağlayıcısı uygulaması.</span><span class="sxs-lookup"><span data-stu-id="768be-188">The following code shows the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementation in our sample navigation provider.</span></span> <span data-ttu-id="768be-189">Yöntemi, belirtilen yolun doğru olduğundan ve tablosunun var olduğunu ve bir kapsayıcı yolunu belirtir, true değerini döndürür, doğrular.</span><span class="sxs-lookup"><span data-stu-id="768be-189">The method verifies that  the specified path is correct and if the table exists, and returns true if the path indicates a container.</span></span>

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a><span data-ttu-id="768be-190">IsItemContainer'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-190">Things to Remember About Implementing IsItemContainer</span></span>

<span data-ttu-id="768be-191">Öğesinden gezinme sağlayıcınız .NET sınıf sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="768be-191">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="768be-192">Bu durumda, uygulanması [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) geçirilen yolu gereksinimlerini karşıladığından emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="768be-192">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) needs to ensure that the path passed meets requirements.</span></span> <span data-ttu-id="768be-193">Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) özelliği.</span><span class="sxs-lookup"><span data-stu-id="768be-193">To do this, the method should access the appropriate property, for example, the [System.Management.Automation.Provider.Cmdletprovider.Exclude\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) property.</span></span>

## <a name="moving-an-item"></a><span data-ttu-id="768be-194">Bir öğe taşıma</span><span class="sxs-lookup"><span data-stu-id="768be-194">Moving an Item</span></span>

<span data-ttu-id="768be-195">Support, `Move-Item` Gezinti sağlayıcınız cmdlet'ini uygulayan [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="768be-195">In support of the `Move-Item` cmdlet, your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="768be-196">Bu yöntem tarafından belirtilen öğe taşır `path` parametresi sağlanan yolda kapsayıcıya `destination` parametresi.</span><span class="sxs-lookup"><span data-stu-id="768be-196">This method moves the item specified by the `path` parameter to the container at the path supplied in the `destination` parameter.</span></span>

<span data-ttu-id="768be-197">Örnek gezinme sağlayıcı geçersiz [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="768be-197">The sample navigation provider does not override the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method.</span></span> <span data-ttu-id="768be-198">Aşağıdaki varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="768be-198">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a><span data-ttu-id="768be-199">MoveItem'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-199">Things to Remember About Implementing MoveItem</span></span>

<span data-ttu-id="768be-200">Öğesinden gezinme sağlayıcınız .NET sınıf sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="768be-200">Your navigation provider .NET class might declare provider capabilities of ExpandWildcards, Filter, Include, or Exclude, from the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="768be-201">Bu durumda, uygulanması [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) geçirilen yolu gereksinimleri karşıladığından emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="768be-201">In this case, the implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) must ensure that the path passed meets requirements.</span></span> <span data-ttu-id="768be-202">Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, **CmdletProvider.Exclude** özelliği.</span><span class="sxs-lookup"><span data-stu-id="768be-202">To do this, the method should access the appropriate property, for example, the **CmdletProvider.Exclude** property.</span></span>

<span data-ttu-id="768be-203">Varsayılan olarak, bu yöntem geçersiz kılmalarına nesneleri var olan nesnelerin üzerine sürece taşımamalısınız [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="768be-203">By default, overrides of this method should not move objects over existing objects unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="768be-204">Örneğin, dosya sistemi sağlayıcısı c:\temp\abc.txt varolan c:\bar.txt dosyasını sürece kopyalamaz [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="768be-204">For example, the filesystem provider will not copy c:\temp\abc.txt over an existing c:\bar.txt file unless the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is set to `true`.</span></span> <span data-ttu-id="768be-205">Yolunu belirtilmişse `destination` parametresi var ve bir kapsayıcı [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="768be-205">If the path specified in the `destination` parameter exists and is a container, the [System.Management.Automation.Provider.Cmdletprovider.Force\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) property is not required.</span></span> <span data-ttu-id="768be-206">Bu durumda, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) tarafından belirtilen öğe taşımalısınız `path` kapsayıcıya parametresi tarafından belirtilen `destination` parametre olarak bir alt.</span><span class="sxs-lookup"><span data-stu-id="768be-206">In this case, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) should move the item indicated by the `path` parameter to the container indicated by the `destination` parameter as a child.</span></span>

<span data-ttu-id="768be-207">Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="768be-207">Your implementation of the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) and check its return value before making any changes to the data store.</span></span> <span data-ttu-id="768be-208">Bu yöntem, bir sistem durumu, örneğin, dosyaları silme değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="768be-208">This method is used to confirm execution of an operation when a change is made to system state, for example, deleting files.</span></span> <span data-ttu-id="768be-209">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak, çalışma zamanı Windows PowerShell ile değiştirilmesi kaynağın adını gönderir kullanıcıya görüntülenen belirleme.</span><span class="sxs-lookup"><span data-stu-id="768be-209">[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="768be-210">Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="768be-210">After the call to [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returns `true`, the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method should call the [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) method.</span></span> <span data-ttu-id="768be-211">Bu yöntem, geri bildirim işlemi devam söylemek izin vermek için kullanıcıya bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="768be-211">This method sends a message to the user to allow feedback to say if the operation should be continued.</span></span> <span data-ttu-id="768be-212">Sağlayıcınız çağırmalıdır [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) olarak tehlikeli olabilecek bir sistem değişiklikleri için ek bir denetim.</span><span class="sxs-lookup"><span data-stu-id="768be-212">Your provider should call [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) as an additional check for potentially dangerous system modifications.</span></span>

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a><span data-ttu-id="768be-213">Öğe taşıma cmdlet'e dinamik parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="768be-213">Attaching Dynamic Parameters to the Move-Item Cmdlet</span></span>

<span data-ttu-id="768be-214">Bazen `Move-Item` cmdlet, çalışma zamanında dinamik olarak sağlanan ek parametreler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="768be-214">Sometimes the `Move-Item` cmdlet requires additional parameters that are provided dynamically at runtime.</span></span> <span data-ttu-id="768be-215">Bu dinamik parametreleri sağlamak için Gezinti sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) gerekli parametre değerlerini almak için yöntemi Belirtilen yol ve dönüş öğesi özelliklerini ve alanları ayrıştırma ile sahip bir nesne cmdlet'i sınıfla benzer öznitelikleri veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne.</span><span class="sxs-lookup"><span data-stu-id="768be-215">To provide these dynamic parameters, the navigation provider must implement the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method to get the required parameter values from the item at the indicated path, and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="768be-216">Bu gezinti sağlayıcı, bu yöntem uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="768be-216">This navigation provider does not implement this method.</span></span> <span data-ttu-id="768be-217">Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="768be-217">However, the following code is the default implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a><span data-ttu-id="768be-218">Göreli bir yol Normalleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="768be-218">Normalizing a Relative Path</span></span>

<span data-ttu-id="768be-219">Gezinti sağlayıcı uygular, [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) tam yol'leri normalleştirmek için yöntemi gösterilir `path` parametresi tarafından belirtilen göreli olarak `basePath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="768be-219">Your navigation provider implements the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method to normalize the fully-qualified path indicated in the `path` parameter as being relative to the path specified by the `basePath` parameter.</span></span> <span data-ttu-id="768be-220">Yöntemi, normalleştirilmiş yol dize gösterimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="768be-220">The method returns a string representation of the normalized path.</span></span> <span data-ttu-id="768be-221">Bu bir hata ortaya çıkarsa Yazar `path` parametresi, varolmayan bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="768be-221">It writes an error if the `path` parameter specifies a nonexistent path.</span></span>

<span data-ttu-id="768be-222">Örnek gezinme sağlayıcının bu yöntemi geçersiz kılmaz.</span><span class="sxs-lookup"><span data-stu-id="768be-222">The sample navigation provider does not override this method.</span></span> <span data-ttu-id="768be-223">Aşağıdaki varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="768be-223">The following is the default implementation.</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a><span data-ttu-id="768be-224">NormalizeRelativePath'ı uygulama hakkında bunları unutmayın</span><span class="sxs-lookup"><span data-stu-id="768be-224">Things to Remember About Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="768be-225">Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) çözümlenmelidir `path` parametresi, ancak sahip değil söz dizimi tamamen Ayrıştırmada kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="768be-225">Your implementation of [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) should parse the `path` parameter, but it does not have to use purely syntactical parsing.</span></span> <span data-ttu-id="768be-226">Büyük/küçük harf veri deposundaki yol bilgileri aramak ve oluşturan bir yol yolu kullanmak için bu yöntem eşleşen tasarım için önerilir ve yolu sözdizimi standart.</span><span class="sxs-lookup"><span data-stu-id="768be-226">You are encouraged to design this method to use the path to look up the path information in the data store and create a path that matches the casing and standardized path syntax.</span></span>

## <a name="code-sample"></a><span data-ttu-id="768be-227">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="768be-227">Code Sample</span></span>

<span data-ttu-id="768be-228">Tam örnek kod için bkz: [AccessDbProviderSample05 kod örneği](./accessdbprovidersample05-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="768be-228">For complete sample code, see [AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="768be-229">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="768be-229">Defining Object Types and Formatting</span></span>

<span data-ttu-id="768be-230">Varolan nesnelere üyelerini ekleyebilir veya yeni nesneleri tanımlamak için bir sağlayıcı için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="768be-230">It is possible for a provider to add members to existing objects or define new objects.</span></span> <span data-ttu-id="768be-231">Daha fazla bilgi için[genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="768be-231">For more information, see[Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-windows-powershell-provider"></a><span data-ttu-id="768be-232">Windows PowerShell sağlayıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-232">Building the Windows PowerShell provider</span></span>

<span data-ttu-id="768be-233">Daha fazla bilgi için [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="768be-233">For more information, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="768be-234">Windows PowerShell sağlayıcıyı test etme</span><span class="sxs-lookup"><span data-stu-id="768be-234">Testing the Windows PowerShell provider</span></span>

<span data-ttu-id="768be-235">Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı olduğunda göre türetme kullanıma cmdlet de dahil olmak üzere komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="768be-235">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including cmdlets made available by derivation.</span></span> <span data-ttu-id="768be-236">Bu örnekte, örnek Gezinti sağlayıcısı test eder.</span><span class="sxs-lookup"><span data-stu-id="768be-236">This example will test the sample navigation provider.</span></span>

1. <span data-ttu-id="768be-237">Yeni kabuğunuz çalıştırın ve `Set-Location` erişim veritabanını belirtmek için bir yol ayarlamak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-237">Run your new shell and use the `Set-Location` cmdlet to set the path to indicate the Access database.</span></span>

   ```powershell
   Set-Location mydb:
   ```

2. <span data-ttu-id="768be-238">Şimdi Çalıştır `Get-Childitem` kullanılabilir veritabanı tablolar veritabanı öğelerinin bir listesini almak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-238">Now run the `Get-Childitem` cmdlet to retrieve a list of the database items, which are the available database tables.</span></span> <span data-ttu-id="768be-239">Her tablo için bu cmdlet ayrıca tablo satır sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="768be-239">For each table, this cmdlet also retrieves the number of table rows.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. <span data-ttu-id="768be-240">Kullanım `Set-Location` cmdlet'ini yeniden çalışanlar veri tablosunun konumunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="768be-240">Use the `Set-Location` cmdlet again to set the location of the Employees data table.</span></span>

   ```powershell
   Set-Location Employees
   ```

4. <span data-ttu-id="768be-241">Şimdi kullanalım `Get-Location` Employees tablosunu yolunu almak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-241">Let's now use the `Get-Location` cmdlet to retrieve the path to the Employees table.</span></span>

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. <span data-ttu-id="768be-242">Artık `Get-Childitem` cmdlet'i yöneltilen için `Format-Table` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-242">Now use the `Get-Childitem` cmdlet piped to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="768be-243">Bu cmdlet kümesini, çalışanların veri tablosu için tablo satırları olan öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="768be-243">This set of cmdlets retrieves the items for the Employees data table, which are the table rows.</span></span> <span data-ttu-id="768be-244">Biçimlendirilmiş belirtildiği gibi `Format-Table` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-244">They are formatted as specified by the `Format-Table` cmdlet.</span></span>

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. <span data-ttu-id="768be-245">Şimdi Çalıştır `Get-Item` çalışanlar veri tablonun satırında 0 olan öğeleri almak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-245">You can now run the `Get-Item` cmdlet to retrieve the items for row 0 of the Employees data table.</span></span>

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. <span data-ttu-id="768be-246">Kullanım `Get-Item` yeniden satır 0 öğeler için çalışan verilerini almak için cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="768be-246">Use the `Get-Item` cmdlet again to retrieve the employee data for the items in row 0.</span></span>

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a><span data-ttu-id="768be-247">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="768be-247">See Also</span></span>

[<span data-ttu-id="768be-248">Windows PowerShell sağlayıcılar oluşturma</span><span class="sxs-lookup"><span data-stu-id="768be-248">Creating Windows PowerShell providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="768be-249">Tasarım bilgisayarınızı Windows PowerShell sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="768be-249">Design Your Windows PowerShell provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="768be-250">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="768be-250">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="768be-251">Kapsayıcı Windows PowerShell sağlayıcıyı uygulama</span><span class="sxs-lookup"><span data-stu-id="768be-251">Implement a Container Windows PowerShell provider</span></span>](./creating-a-windows-powershell-container-provider.md)

[<span data-ttu-id="768be-252">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="768be-252">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="768be-253">Windows PowerShell Programcı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="768be-253">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="768be-254">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="768be-254">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)