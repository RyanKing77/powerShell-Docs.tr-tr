---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081130"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="f4d46-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="f4d46-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="f4d46-103">Bu örnek, doğrudan öğesinden türetilen bir sağlayıcı sınıfı bildirmek gösterilmektedir [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4d46-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="f4d46-104">Burada yalnızca bütünlük açısından dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f4d46-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f4d46-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="f4d46-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4d46-106">Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:</span><span class="sxs-lookup"><span data-stu-id="f4d46-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="f4d46-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4d46-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="f4d46-108">Bkz: [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="f4d46-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="f4d46-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4d46-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="f4d46-110">Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="f4d46-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="f4d46-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4d46-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="f4d46-112">Bkz: [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="f4d46-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="f4d46-113">Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4d46-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="f4d46-114">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="f4d46-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f4d46-115">Bildirme `CmdletProvider` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f4d46-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="f4d46-116">Doğrudan öğesinden türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4d46-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="f4d46-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4d46-117">Example</span></span>

<span data-ttu-id="f4d46-118">Bu örnek sağlayıcısı sınıfın nasıl tanımlanacağını ve nasıl belirtileceğini göstermektedir `CmdletProvider` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f4d46-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="f4d46-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f4d46-119">See Also</span></span>

[<span data-ttu-id="f4d46-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f4d46-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="f4d46-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f4d46-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="f4d46-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="f4d46-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="f4d46-123">Windows PowerShell sağlayıcınız tasarlama</span><span class="sxs-lookup"><span data-stu-id="f4d46-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)