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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081079"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Bu örnek, üzerine yazma işlemi gösterilmektedir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) Yöntem çağrıları desteklemek için `Get-Item` ve `Set-Item` cmdlet'leri. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.

## <a name="demonstrates"></a>Gösteriler

> [!IMPORTANT]
> Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).

Bu örnek aşağıdaki gösterir:

- Bildirme `CmdletProvider` özniteliği.

- Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.

- Üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) davranışını değiştirmek için yöntem `New-PSDrive` cmdlet'i, kullanıcının yeni sürücüler oluşturmaya izin. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `New-PSDrive` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) mevcut sürücüleri kaldırma desteklemek için yöntemi.

- Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) davranışını değiştirmek için yöntem `Get-Item` cmdlet'i, öğeleri veri deposundan alınacak kullanıcının izin verme. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Item` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) davranışını değiştirmek için yöntem `Set-Item` cmdlet'i, veri deposundaki öğeleri güncelleştirmek kullanıcının. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Item` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) davranışını değiştirmek için yöntem `Test-Path` cmdlet'i. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Test-Path` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) sağlanan yolun geçerli olup olmadığını belirlemek için yöntemi.

## <a name="example"></a>Örnek

Bu örnek, üzerine almak ve bir Microsoft Access verileri temel öğeleri ayarlamak için gereken yöntemleri gösterilmektedir.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell sağlayıcınız tasarlama](./provider-types.md)