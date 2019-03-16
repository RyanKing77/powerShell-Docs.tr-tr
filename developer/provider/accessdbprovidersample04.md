---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057629"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="84dff-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="84dff-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="84dff-103">Bu örnek nasıl çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="84dff-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="84dff-104">Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84dff-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="84dff-105">Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="84dff-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="84dff-106">Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="84dff-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="84dff-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="84dff-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84dff-108">Sağlayıcı sınıfınıza büyük olasılıkla türetilmesi [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="84dff-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="84dff-109">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="84dff-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="84dff-110">Bildirme `CmdletProvider` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="84dff-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="84dff-111">Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="84dff-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="84dff-112">Üzerine [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) davranışını değiştirmek için yöntem `Copy-Item` öğeleri tek bir konumdan diğerine kopyalamak kullanıcı izin veren cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84dff-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="84dff-113">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Copy-Item` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="84dff-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="84dff-114">Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) kullanıcının üst öğenin alt öğeleri almak Get-ChildItems cmdlet davranışını değiştirmek için yöntemi .</span><span class="sxs-lookup"><span data-stu-id="84dff-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="84dff-115">(Bu örnekte Get-ChildItems cmdlet'e dinamik parametreler ekleme göstermez.)</span><span class="sxs-lookup"><span data-stu-id="84dff-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="84dff-116">Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Get-ChildItems cmdlet davranışını değiştirmek için yöntem olduğunda `Name` cmdlet parametresi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="84dff-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="84dff-117">Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) davranışını değiştirmek için yöntem `New-Item` öğeleri veri deposuna eklemek kullanıcının veren cmdlet.</span><span class="sxs-lookup"><span data-stu-id="84dff-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="84dff-118">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `New-Item` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="84dff-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="84dff-119">Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) davranışını değiştirmek için yöntem `Remove-Item` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="84dff-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="84dff-120">(Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Remove-Item` cmdlet'ini.)</span><span class="sxs-lookup"><span data-stu-id="84dff-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="84dff-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="84dff-121">Example</span></span>

<span data-ttu-id="84dff-122">Bu örnek, üzerine kopyalayın, oluşturmak ve alt öğeleri bir üst öğenin almak için yöntemler yanı sıra, öğeleri kaldırmak için gereken yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="84dff-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="84dff-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="84dff-123">See Also</span></span>

[<span data-ttu-id="84dff-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="84dff-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="84dff-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="84dff-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="84dff-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="84dff-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="84dff-127">Windows PowerShell sağlayıcınız tasarlama</span><span class="sxs-lookup"><span data-stu-id="84dff-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)