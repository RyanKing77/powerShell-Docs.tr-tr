---
title: Sağlayıcı türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057969"
---
# <a name="provider-types"></a>Sağlayıcı türleri

Sağlayıcıları nasıl (Windows PowerShell tarafından sağlanan) sağlayıcı cmdlet eylemlerini gerçekleştirmek değiştirerek temel işlevleri tanımlayın. Örneğin, sağlayıcıları varsayılan işlevlerini kullanabilirsiniz `Get-Item` cmdlet veya değiştirebilir Bu cmdlet öğeleri veri deposundan alınırken nasıl çalışır. Özel sağlayıcı sınıflar ve arabirimler yöntemlerinden üzerine yazarak tanımlanan işlevleri bu konuda açıklanan sağlayıcı işlevselliğini içerir.

> [!NOTE]
> Windows PowerShell tarafından önceden tanımlanan sağlayıcısı özellikler için bkz. [sağlayıcısı yeteneklerini](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Etkin sürücü sağlayıcıları

Etkin sürücü sağlayıcıları, kullanıcı varsayılan sürücüleri belirtin ve sürücüleri ekleyip izin verin. Bunlar veri deposuna erişmek için bazı varsayılan sürücü gerektirdiğinden çoğu durumda, etkin sürücü sağlayıcıları sağlayıcılarıdır. Ancak, kendi sağlayıcınızı yazarken olabilir veya oluşturmak ve sürücüleri kaldırmak izin vermek istemeyebilirsiniz.

Sürücü özellikli bir sağlayıcı oluşturmak için sağlayıcı sınıfı öğesinden türetilmelidir [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı veya bu sınıftan türetilen başka bir sınıf. [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı tanımlar varsayılan sürücü sağlayıcısı uygulama ve destek için aşağıdaki yöntemlerden `New-PSDrive` ve `Remove-PSDrive` cmdlet'leri. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `NewDrive` yöntemi `New-PSDrive` cmdlet'i ve isteğe bağlı olarak gibiikincibiryöntemüzerineyazabilirsiniz`NewDriveDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

- [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) sağlayıcı kullanıldığında kullanıcı tarafından kullanılabilen varsayılan sürücüleri yöntemi tanımlar.

- [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemleri sağlayıcınız nasıl desteklediğine tanımlar `New-PSDrive` sağlayıcısı cmdlet'i. Bu cmdlet veri deposuna erişmek için sürücüleri oluşturmasına olanak tanır.

- [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi tanımlar sağlayıcınız nasıl desteklediğini `Remove-PSDrive` sağlayıcısı cmdlet'i. Bu cmdlet'i, veri deposundan sürücüleri kaldırmak için kullanıcı sağlar.

## <a name="item-enabled-providers"></a>Öğe etkin sağlayıcılar

Öğe etkin sağlayıcıları Al, Ayarla veya veri deposundaki öğeleri temizleyin izin verin. "Öğe", kullanıcı erişebileceğini veya yönetebileceğini bağımsız olarak veri deposunun bir öğedir. Bir öğe etkin sağlayıcısı oluşturmak için sağlayıcı sınıfı öğesinden türetilmelidir [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı veya bu sınıftan türetilen başka bir sınıf.

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `ClearItem` yöntemi `Clear-Item` cmdlet'i ve isteğe bağlı olarak gibiikincibiryöntemüzerineyazabilirsiniz`ClearItemDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

- [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) yöntemleri sağlayıcınız nasıl desteklediğini tanımlamak `Clear-Item` sağlayıcısı cmdlet'i. Bu cmdlet'i, veri deposundaki bir öğe değerinin kaldırmasını sağlar.

- [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) definovat metody nasıl Sağlayıcı desteklediği `Get-Item` sağlayıcısı cmdlet'i. Bu cmdlet, verileri veri deposundan alınacak kullanıcının sağlar.

- [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ve [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) definovat metody nasıl Sağlayıcı desteklediği `Set-Item` sağlayıcısı cmdlet'i. Bu cmdlet öğelerini veri deposundaki değerleri güncelleştirmek kullanıcının sağlar.

- [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) ve [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) yöntemleri sağlayıcınız nasıl desteklediğini tanımlamak `Invoke-Item` sağlayıcısı cmdlet'i. Bu cmdlet öğesi tarafından belirtilen varsayılan eylem gerçekleştirmesine izin verir.

- [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) ve [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) yöntemleri sağlayıcınız nasıl desteklediğini tanımlamak `Test-Path` sağlayıcısı cmdlet'i. Bu cmdlet'i bir yolu, tüm öğeleri mevcut olup olmadığını belirlemek kullanıcı sağlar.

  Sağlayıcısı cmdlet'leri uygulamak için kullanılan yöntemleri yanı sıra [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıf aşağıdaki yöntemleri de tanımlar:

- [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) sağlayıcı yolu belirtmek için joker karakterler kullanmak kullanıcının yöntemi sağlar.

- [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) yol sağlayıcı için sözdizimi ve anlamsal olarak geçerli olup olmadığını belirlemek için kullanılır.

## <a name="container-enabled-providers"></a>Kapsayıcı etkin sağlayıcılar

Kapsayıcı etkin sağlayıcılar kapsayıcılardır öğelerini yönetmek verin. Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır. Kapsayıcı etkin bir sağlayıcı oluşturmak için sağlayıcı sınıfı öğesinden türetilmelidir [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı veya bu sınıftan türetilen başka bir sınıf.

> [!IMPORTANT]
> Kapsayıcı etkin sağlayıcılar, iç içe geçmiş kapsayıcılar içeren veri depoları erişemez. Bir alt öğe kapsayıcı başka bir kapsayıcı ise, sağlayıcısı Gezinti etkin uygulamalıdır.

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `CopyItem` yöntemi `Copy-Item` cmdlet'i ve isteğe bağlı olarak gibiikincibiryöntemüzerineyazabilirsiniz`CopyItemDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

- [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ve [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Copy-Item` sağlayıcısı cmdlet'i. Bu cmdlet, öğeyi bir konumdan diğerine kopyalamak kullanıcının sağlar.

- [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ve [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Get-ChildItem` sağlayıcısı cmdlet'i. Bu cmdlet, üst öğenin alt öğeleri almak kullanıcının sağlar.

- [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ve [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Get-ChildItem` sağlayıcısı cmdlet'i, kendi `Name` parametre belirtildi.

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) ve [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `New-Item` sağlayıcısı cmdlet'i. Bu cmdlet veri deposunda yeni öğeleri oluşturmasına olanak tanır.

- [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ve [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Remove-Item` sağlayıcısı cmdlet'i. Bu cmdlet öğeleri veri deposundan kaldırmak izin verir.

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) ve [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Rename-Item` sağlayıcısı cmdlet'i. Bu cmdlet'i, veri deposundaki öğeleri yeniden adlandırmak kullanıcı sağlar.

  Sağlayıcısı cmdlet'leri uygulamak için kullanılan yöntemleri yanı sıra [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıf aşağıdaki yöntemleri de tanımlar:

- [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) yöntemi öğenin alt öğeleri olup olmadığını belirlemek için sağlayıcı sınıfı tarafından kullanılabilir.

- [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) yöntemi belirtilen yoldan yeni bir sağlayıcıya özgü yolu oluşturmak için sağlayıcı sınıfı tarafından kullanılabilir.

## <a name="navigation-enabled-providers"></a>Gezinme özelliğinin etkin sağlayıcılar

Gezinme özelliğinin etkin sağlayıcıları veri deposunda öğeleri Taşı izin verin. Gezinme özelliğinin etkin bir sağlayıcı oluşturmak için sağlayıcı sınıfı öğesinden türetilmelidir [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `MoveItem` yöntemi `Move-Item` cmdlet'i ve isteğe bağlı olarak gibiikincibiryöntemüzerineyazabilirsiniz`MoveItemDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ve [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Move-Item` sağlayıcısı cmdlet'i. Bu cmdlet'i bir öğeyi deposundaki bir konumdan başka bir konuma taşımak kullanıcı sağlar.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi tanımlar sağlayıcınız nasıl desteklediğini `Join-Path` sağlayıcısı cmdlet'i. Bu cmdlet bir sağlayıcı iç yolu oluşturmak için bir üst ve alt yol kesimi birleştirme izin verir.

  Sağlayıcısı cmdlet'leri uygulamak için kullanılan yöntemleri yanı sıra [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıf aşağıdaki yöntemleri de tanımlar:

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi yolunun alt düğümün adını ayıklar.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi üst yolun bir bölümünü ayıklar.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi öğe kapsayıcı öğe olup olmadığını belirler. Bu bağlamda, bir ortak bir üst öğe altında bir alt öğe grubunu kapsayıcıdır.

- [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) yöntemi, belirtilen bir taban yolu göreli bir öğe için bir yol döndürür.

## <a name="content-enabled-providers"></a>İçerik özellikli sağlayıcıları

İçerik özellikli sağlayıcıları temizleyin, alma veya bir veri deposunda öğelerinin içeriğini kümesi izin verin. Örneğin, dosya sistemi sağlayıcısı temizleyin, alma ve dosya sistemindeki dosyaların içeriğini ayarlamak sağlar. İçerik etkin sağlayıcısı oluşturmak için sağlayıcı sınıfı yöntemleri uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi.

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `ClearContent` yöntemi `Clear-Content` cmdlet'i ve isteğe bağlı olarak gibiikincibiryöntemüzerineyazabilirsiniz`ClearContentDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ve [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)definovat metody sağlayıcınız nasıl desteklediğini `Clear-Content` sağlayıcısı cmdlet'i. Bu cmdlet, kullanıcının bir öğenin içeriğini öğeyi silmeniz izin verir.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) ve [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Get-Content` sağlayıcısı cmdlet'i. Bu cmdlet, bir öğenin içeriğini almak kullanıcının sağlar. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) yöntemi döndürür bir [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) tanımlayan arabirimi içeriği okumak için kullanılan yöntemleri.

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ve [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Set-Content` sağlayıcısı cmdlet'i. Bu cmdlet, bir öğenin içeriği güncelleştirmek kullanıcının sağlar. [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) yöntemi döndürür bir [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) tanımlayan arabirimi içerik yazmak için kullanılan yöntemleri.

## <a name="property-enabled-providers"></a>Enabled özelliği sağlayıcıları

Özelliği etkinleştirilmiş sağlayıcıları veri deposundaki öğelerin özelliklerini yönetmesine olanak sağlar. Özelliği etkin bir sağlayıcı oluşturmak için sağlayıcı sınıfı yöntemleri uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) arabirimleri. Çoğu durumda, bir sağlayıcı cmdlet desteklemek için cmdlet'i gibi çağırmak için Windows PowerShell altyapısı çağıran yöntemin üzerine gerekir `ClearProperty` yöntemi Clear-özellik cmdlet ve isteğe bağlı olarak, gibiikincibiryöntemüzerineyaz`ClearPropertyDynamicParameters`, cmdlet'e dinamik parametreler ekleme.

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) arabirimi belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar:

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) ve [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Clear-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet kullanıcının bir özelliğin değerini silmesine izin verir.

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) ve [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)definovat metody sağlayıcınız nasıl desteklediğini `Get-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet'i, bir öğenin özellik alınacak kullanıcının sağlar.

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ve [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)definovat metody sağlayıcınız nasıl desteklediğini `Set-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet, bir öğenin özelliklerini güncelleştirmek kullanıcının sağlar.

  [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) arabirimi belirli sağlayıcısı cmdlet'leri uygulamak için aşağıdaki yöntemleri tanımlar:

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Copy-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet bir özelliği ve değerini bir konumdan diğerine kopyalama izin verir.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Move-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet, kullanıcının bir özelliği ve değerini bir konumdan diğerine taşımanıza olanak sağlar.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `New-ItemProperty` sağlayıcısı cmdlet'i. Bu cmdlet, kullanıcının yeni bir özellik oluşturmak ve değerini ayarlama izin verir.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Remove-ItemProperty` cmdlet'i. Bu cmdlet, kullanıcının bir özelliği ve değerini silmesine izin verir.

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) ve [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) definovat metody sağlayıcınız nasıl desteklediğini `Rename-ItemProperty` cmdlet'i. Bu cmdlet bir özelliğin adını değiştirmesine izin verir.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)