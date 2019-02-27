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
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Bu örnek nasıl çağrıları desteklemek için içerik yöntemleri üzerine gösterir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri. Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır. Bu örnekteki sağlayıcı sınıfın türetildiği [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıf ve uyguladığı [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.

## <a name="demonstrates"></a>Gösteriler

> [!IMPORTANT]
> Sağlayıcı sınıfınız, büyük olasılıkla bir aşağıdaki sınıflar noktasından türettikten ve büyük olasılıkla diğer sağlayıcısı arabirimleri de uygulamak:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı. Bkz: [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.
>
> Sağlayıcı özelliklerini temel alarak türetilen öğrenmek için hangi sağlayıcı sınıfı seçme hakkında daha fazla bilgi için [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./provider-types.md).

Bu örnek aşağıdaki gösterir:

- Bildirme `CmdletProvider` özniteliği.

- Türetilen bir sağlayıcı sınıfı tanımlayarak [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı ve bu bildirir [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.

- Üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) davranışını değiştirmek için yöntem `Clear-Content` cmdlet'i, bir öğe içeriği kaldırmak için kullanıcıya izin verme. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Clear-Content` cmdlet'ini.)

- Üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) davranışını değiştirmek için yöntem `Get-Content` cmdlet'i, kullanıcının bir öğenin içeriğini almak izin verme. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Get-Content` cmdlet'ini.).

- Üzerine [Microsoft.Powershell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) davranışını değiştirmek için yöntem `Set-Content` cmdlet'i, bir öğenin içeriği güncelleştirmek kullanıcının. (Bu örnekte dinamik parametreleri eklemek nasıl algılanacağını göstermez `Set-Content` cmdlet'ini.)

## <a name="example"></a>Örnek

Bu örnek, üzerine temizleyin, alma ve öğelerinin içeriğini bir Microsoft Access verileri temel ayarlamak için gereken yöntemleri gösterilmektedir.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell sağlayıcınız tasarlama](./provider-types.md)