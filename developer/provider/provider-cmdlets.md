---
title: Sağlayıcısı cmdlet'leri | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080960"
---
# <a name="provider-cmdlets"></a>Sağlayıcı cmdlet’leri

Kullanıcı bir veri deposu yönetmek için çalıştırabileceğiniz cmdlet'leri sağlayıcısı cmdlet'leri adlandırılır. Bu cmdlet'ler desteklemek için bazı temel sağlayıcısı sınıfları ve arabirimleri tarafından tanımlanan yöntemlere üzerine yazmak gerekir.

## <a name="provider-cmdlets"></a>Sağlayıcısı cmdlet'leri

Kullanıcı tarafından çalıştırılabilir sağlayıcısı cmdlet'leri şunlardır:

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet'leri

- `Get-PSDrive`: Bu cmdlet, geçerli oturumda Windows PowerShell sürücülerini döndürür. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.

- `New-PSDrive`: Bu cmdlet veri deposuna erişmek için Windows PowerShell sürücülerini oluşturmasına olanak tanır. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemleri.

- `Remove-PSDrive`: Bu cmdlet'i, veri deposuna erişim Windows PowerShell sürücülerini kaldırmasını sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi.

### <a name="item-cmdlets"></a>Öğe cmdlet'leri

- `Clear-Item`: Bu cmdlet'i, veri deposunda bir öğenin değerini kaldırmasını sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) ve [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) yöntemleri.

- `Copy-Item`: Bu cmdlet, öğeyi bir konumdan diğerine kopyalamak kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ve [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) yöntemleri.

- `Get-Item`: Bu cmdlet, verileri veri deposundan alınacak kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) yöntemleri.

- `Get-ChildItem`: Bu cmdlet, üst öğenin alt öğeleri almak kullanıcının sağlar. Bu cmdlet desteklemek için aşağıdaki yöntemlerden üzerine yaz:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Bu cmdlet öğesi tarafından belirtilen varsayılan eylem gerçekleştirmesine izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) ve [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) yöntemleri.

- `Move-Item`: Bu cmdlet'i bir öğeyi bir konumdan başka bir konuma taşımak kullanıcı sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ve [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s yöntemleri.

- `New-ItemProperty`: Bu cmdlet kullanıcının veri deposunda yeni bir öğe oluşturmanıza izin verir.

- `Remove-Item`: Bu cmdlet öğeleri veri deposundan kaldırmak izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ve [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) yöntemleri.

- `Rename-Item`: Bu cmdlet'i, veri deposundaki öğeleri yeniden adlandırmak kullanıcı sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) ve [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) yöntemleri.

- `Set-Item`: Bu cmdlet öğelerini veri deposundaki değerleri güncelleştirmek kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) yöntemleri.

### <a name="item-content-cmdlets"></a>Öğe içerik cmdlet'leri

- `Add-Content`: Bu cmdlet, kullanıcının bir öğe için içerik ekleme izin verir.

- `Clear-Content`: Bu cmdlet öğesi silmeden bir öğe içeriği silmek kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ve [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) yöntemleri.

- `Get-Content`: Bu cmdlet, bir öğenin içeriğini almak kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) ve [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) yöntemleri. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) yöntemi döndürür bir [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) tanımlayan arabirimi içeriği okumak için kullanılan yöntemleri.

- `Set-Content`: Bu cmdlet, bir öğenin içeriği güncelleştirmek kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ve [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) yöntemleri. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) yöntemi döndürür bir [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) tanımlayan arabirimi içerik yazmak için kullanılan yöntemleri.

### <a name="item-property-cmdlets"></a>Öğe özelliği cmdlet'leri

- `Clear-ItemProperty`: Bu cmdlet kullanıcının bir özelliğin değerini silmesine izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) ve [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) yöntemleri.

- `Copy-ItemProperty`: Bu cmdlet bir özelliği ve değerini bir konumdan diğerine kopyalama izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) yöntemleri.

- `Get-ItemProperty`: Bu cmdlet, bir öğenin özelliklerini alır. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) ve [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) yöntemleri.

- `Move-ItemProperty`: Bu cmdlet, kullanıcının bir özelliği ve değerini bir konumdan diğerine taşımanıza olanak sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) yöntemleri.

- `New-ItemProperty`: Bu cmdlet, kullanıcının yeni bir özellik oluşturmak ve değerini ayarlama izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) yöntemleri.

- `Remove-ItemProperty`: Bu cmdlet, kullanıcının bir özelliği ve değerini silmesine izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) yöntemleri.

- `Rename-ItemProperty`: Bu cmdlet bir özelliğin adını değiştirmesine izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) yöntemleri.

- `Set-ItemProperty`: Bu cmdlet, bir öğenin özelliklerini güncelleştirmek kullanıcının sağlar. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ve [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) yöntemleri.

### <a name="location-cmdlets"></a>Konum cmdlet'leri

- `Get-Location`: Geçerli çalışma konumu hakkındaki bilgileri alır. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.

- `Pop-Location`: Bu cmdlet'i, yığın üstüne en son gönderilen konumuna geçerli konumunu değiştirir. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.

- `Push-Location`: Bu cmdlet, geçerli konumu ("yığın") konumların bir listesini üstüne ekler. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.

- `Set-Location`: Bu cmdlet, geçerli çalışma konumu belirtilen konuma ayarlar. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.

### <a name="path-cmdlets"></a>Yol cmdlet'leri

- `Join-Path`: Bu cmdlet bir sağlayıcı iç yolu oluşturmak için bir üst ve alt yol kesimi birleştirme izin verir. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi.

- `Convert-Path`: Bu cmdlet bir yolu, bir Windows PowerShell yolundan bir Windows PowerShell sağlayıcısı yoluna dönüştürür.

- `Split-Path`: Belirtilen yolun bir bölümünü döndürür.

- `Resolve-Path`: Joker karakterler bir yolda giderir ve yol içerikleri görüntüler.

- `Test-Path`: Bu cmdlet, tüm öğeleri bir yolu var olup olmadığını belirler. Bu cmdlet desteklemek için üzerine [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) ve [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) yöntemleri.

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet'leri

- `Get-PSProvider`: Bu cmdlet, oturum yok sağlayıcıları hakkında bilgi döndürür. Bu cmdlet desteklemek için herhangi bir yöntemin üzerine yazmak gerekmez.