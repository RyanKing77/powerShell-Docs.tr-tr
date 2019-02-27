---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849199"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="a3830-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="a3830-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="a3830-103">Bu örnek, üzerine yazma işlemi gösterilmektedir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Yöntem çağrıları desteklemek için `Get-Item` ve `Set-Item` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="a3830-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="a3830-104">Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3830-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a3830-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a3830-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3830-106">Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:</span><span class="sxs-lookup"><span data-stu-id="a3830-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="a3830-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3830-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="a3830-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3830-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a3830-109">Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="a3830-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="a3830-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3830-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="a3830-111">Bkz: [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="a3830-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="a3830-112">Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="a3830-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a3830-113">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="a3830-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a3830-114">Bildirme `CmdletProvider` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a3830-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a3830-115">Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3830-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="a3830-116">Üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) davranışını değiştirmek için yöntem `New-PSDrive` cmdlet'i, kullanıcının yeni sürücüler oluşturmaya izin.</span><span class="sxs-lookup"><span data-stu-id="a3830-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="a3830-117">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `New-PSDrive` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="a3830-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="a3830-118">Üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) mevcut sürücüleri kaldırma desteklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3830-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="a3830-119">Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) davranışını değiştirmek için yöntem `Get-Item` cmdlet'i, öğeleri veri deposundan alınacak kullanıcının izin verme.</span><span class="sxs-lookup"><span data-stu-id="a3830-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="a3830-120">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Item` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="a3830-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="a3830-121">Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) davranışını değiştirmek için yöntem `Set-Item` cmdlet'i, veri deposundaki öğeleri güncelleştirmek kullanıcının.</span><span class="sxs-lookup"><span data-stu-id="a3830-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="a3830-122">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Item` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="a3830-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="a3830-123">Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) davranışını değiştirmek için yöntem `Test-Path` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a3830-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="a3830-124">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Test-Path` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="a3830-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="a3830-125">Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) sağlanan yolun geçerli olup olmadığını belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3830-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="a3830-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3830-126">Example</span></span>

<span data-ttu-id="a3830-127">Bu örnek, üzerine almak ve bir Microsoft Access verileri temel öğeleri ayarlamak için gereken yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a3830-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="a3830-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a3830-128">See Also</span></span>

[<span data-ttu-id="a3830-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a3830-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a3830-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a3830-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a3830-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a3830-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a3830-132">Windows PowerShell sağlayıcınız tasarlama</span><span class="sxs-lookup"><span data-stu-id="a3830-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)