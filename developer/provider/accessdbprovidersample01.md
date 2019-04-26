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
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Bu örnek, doğrudan öğesinden türetilen bir sağlayıcı sınıfı bildirmek gösterilmektedir [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı. Burada yalnızca bütünlük açısından dahil edilmiştir.

## <a name="demonstrates"></a>Gösteriler

> [!IMPORTANT]
> Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).

Bu örnek aşağıdaki gösterir:

- Bildirme `CmdletProvider` özniteliği.

- Doğrudan öğesinden türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı.

## <a name="example"></a>Örnek

Bu örnek sağlayıcısı sınıfın nasıl tanımlanacağını ve nasıl belirtileceğini göstermektedir `CmdletProvider` özniteliği.

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

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell sağlayıcınız tasarlama](./provider-types.md)