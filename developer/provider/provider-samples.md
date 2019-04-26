---
title: Sağlayıcı örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080943"
---
# <a name="provider-samples"></a>Sağlayıcı Örnekleri

Bu bölüm, bir Microsoft Access veritabanına erişim sağlayıcıları örnekleri içerir. Bu örnekler, tüm temel sağlayıcısı sınıflarından sağlayıcısı sınıfları içerir.

## <a name="in-this-section"></a>Bu Bölümde

Bu bölüm şu konuları içerir:

[AccessDBProviderSample01 örnek](./accessdbprovidersample01.md) nasıl doğrudan türetilen sağlayıcı sınıfı bildirmek Bu örnek gösterir [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı. Burada yalnızca bütünlük açısından dahil edilmiştir.

[AccessDBProviderSample02](./accessdbprovidersample02.md) nasıl üzerine yazmak bu örnek gösterir [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) çağrıları desteklemek için yöntemler `New-PSDrive` ve `Remove-PSDrive` cmdlet'leri. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı.

[AccessDBProviderSample03](./accessdbprovidersample03.md) nasıl üzerine yazmak bu örnek gösterir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) çağrıları desteklemek için yöntemler `Get-Item` ve `Set-Item` cmdlet'leri. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.

[AccessDBProviderSample04](./accessdbprovidersample04.md) nasıl çağrıları desteklemek için kapsayıcı yöntemleri üzerine yazmak bu örnek gösterir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri. Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır. Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.

[AccessDBProviderSample05](./accessdbprovidersample05.md) nasıl çağrıları desteklemek için kapsayıcı yöntemleri üzerine yazmak bu örnek gösterir `Move-Item` ve `Join-Path` cmdlet'leri. Bu yöntemler, bir kapsayıcı içindeki öğeleri taşımak gerektiğinde ve veri depolama alanı iç içe geçmiş kapsayıcılar varsa uygulanmalıdır. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.

[AccessDBProviderSample06](./accessdbprovidersample06.md) nasıl çağrıları desteklemek için içerik yöntemleri üzerine yazmak bu örnek gösterir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri. Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıf ve uyguladığı [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)