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
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847302"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Bu örnek nasıl çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri. Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır. Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.

## <a name="demonstrates"></a>Gösteriler

> [!IMPORTANT]
> Sağlayıcı sınıfınıza büyük olasılıkla türetilmesi [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

Bu örnek aşağıdaki gösterir:

- Bildirme `CmdletProvider` özniteliği.

- Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı.

- Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) davranışını değiştirmek için yöntem `Copy-Item` öğeleri tek bir konumdan diğerine kopyalamak kullanıcı izin veren cmdlet. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Copy-Item` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) kullanıcının üst öğenin alt öğeleri almak Get-ChildItems cmdlet davranışını değiştirmek için yöntemi . (Bu örnekte Get-ChildItems cmdlet'e dinamik parametreler ekleme göstermez.)

- Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) Get-ChildItems cmdlet davranışını değiştirmek için yöntem olduğunda `Name` cmdlet parametresi belirtildi.

- Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) davranışını değiştirmek için yöntem `New-Item` öğeleri veri deposuna eklemek kullanıcının veren cmdlet. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `New-Item` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) davranışını değiştirmek için yöntem `Remove-Item` cmdlet'i. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Remove-Item` cmdlet'ini.)

## <a name="example"></a>Örnek

Bu örnek, üzerine kopyalayın, oluşturmak ve alt öğeleri bir üst öğenin almak için yöntemler yanı sıra, öğeleri kaldırmak için gereken yöntemleri gösterilmektedir.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell sağlayıcınız tasarlama](./provider-types.md)