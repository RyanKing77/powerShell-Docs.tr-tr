---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 59832ed8a4fad3b07a171946bff28fb3e1dbe442
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845874"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="7ab1f-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="7ab1f-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="7ab1f-103">Bu örnek nasıl çağrıları desteklemek için içerik yöntemleri üzerine gösterir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="7ab1f-104">Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="7ab1f-105">Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıf ve uyguladığı [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7ab1f-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="7ab1f-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ab1f-107">Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:</span><span class="sxs-lookup"><span data-stu-id="7ab1f-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="7ab1f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="7ab1f-109">Bkz: [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="7ab1f-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="7ab1f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="7ab1f-111">Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="7ab1f-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="7ab1f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="7ab1f-113">Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="7ab1f-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="7ab1f-114">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="7ab1f-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="7ab1f-115">Bildirme `CmdletProvider` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="7ab1f-116">Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı ve bu bildirir [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="7ab1f-117">Üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) davranışını değiştirmek için yöntem `Clear-Content` cmdlet'i, bir öğe içeriği kaldırmak için kullanıcıya izin verme.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="7ab1f-118">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Clear-Content` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="7ab1f-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="7ab1f-119">Üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) davranışını değiştirmek için yöntem `Get-Content` cmdlet'i, kullanıcının bir öğenin içeriğini almak izin verme.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="7ab1f-120">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Content` cmdlet'ini.).</span><span class="sxs-lookup"><span data-stu-id="7ab1f-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="7ab1f-121">Üzerine [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) davranışını değiştirmek için yöntem `Set-Content` cmdlet'i, bir öğenin içeriği güncelleştirmek kullanıcının.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-121">Overwriting the [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="7ab1f-122">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Set-Content` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="7ab1f-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="7ab1f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ab1f-123">Example</span></span>

<span data-ttu-id="7ab1f-124">Bu örnek, üzerine temizleyin, alma ve öğelerinin içeriğini bir Microsoft Access verileri temel ayarlamak için gereken yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ab1f-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="7ab1f-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7ab1f-125">See Also</span></span>

[<span data-ttu-id="7ab1f-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ab1f-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="7ab1f-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ab1f-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="7ab1f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ab1f-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="7ab1f-129">Windows PowerShell sağlayıcınız tasarlama</span><span class="sxs-lookup"><span data-stu-id="7ab1f-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)