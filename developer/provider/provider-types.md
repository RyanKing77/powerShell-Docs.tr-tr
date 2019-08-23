---
title: Sağlayıcı türleri | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986665"
---
# <a name="provider-types"></a>Sağlayıcı türleri

Sağlayıcılar, PowerShell tarafından sunulan sağlayıcı cmdlet 'lerinin eylemlerini yerine getirmek için temel işlevlerini tanımlar. Örneğin, sağlayıcılar `Get-Item` cmdlet 'in varsayılan işlevselliğini kullanabilir veya veri deposundan öğeleri alırken bu cmdlet 'in nasıl çalıştığını değiştirebilirler. Bu belgede açıklanan sağlayıcı işlevselliği, belirli sağlayıcı temel sınıflarından ve Arayüzlerdeki yöntemlerin üzerine yazarak tanımlanan işlevleri içerir.

> [!NOTE]
> PowerShell tarafından önceden tanımlanan sağlayıcı özellikleri için bkz. [sağlayıcı özellikleri](/previous-versions//ee126189(v=vs.85)).

## <a name="drive-enabled-providers"></a>Sürücü etkinleştirilmiş sağlayıcılar

Sürücü etkinleştirilmiş sağlayıcılar, kullanıcının kullanabileceği varsayılan sürücüleri belirtir ve kullanıcının sürücü eklemesine veya kaldırmasına izin verir. Çoğu durumda, sağlayıcılar, veri deposuna erişmek için bazı varsayılan sürücülere ihtiyaç duydukları için sürücü özellikli sağlayıcılardır. Bununla birlikte, kendi sağlayıcınızı yazarken, kullanıcının sürücü oluşturmasına ve kaldırmasına izin vermek isteyebilirsiniz veya istemeyebilirsiniz.

Sürücü etkin bir sağlayıcı oluşturmak için, sağlayıcı sınıfınız [System. Management. Automation. Provider. Drvecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfından veya bu sınıftan türetilen başka bir sınıftan türetilmelidir. **System. Management. Automation. Provider. drivecmdletprovider** sınıfı, sağlayıcının varsayılan sürücülerinin uygulanması ve `New-PSDrive` ve `Remove-PSDrive` cmdlet 'lerini desteklemek için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'i çağırmak `NewDrive` için çağırdığı yöntemin üzerine yazmanız gerekir (örneğin, `New-PSDrive` cmdlet 'in yöntemi gibi) ve isteğe bağlı olarak `NewDriveDynamicParameters` bir ikinci yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

- [System. Management. Automation. Provider. Drvecmdletprovider. ınitializedefaultdrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) yöntemi, sağlayıcı her kullanıldığında kullanıcı için kullanılabilir olan varsayılan sürücüleri tanımlar.

- [System. Management. Automation. Provider. Drvecmdletprovider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [System. Management. Automation. Provider. Drvecmdletprovider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemleri, `New-PSDrive`sağlayıcınızınşunlarınasıldesteklediğinitanımlarsağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposuna erişmek için sürücü oluşturmasına izin verir.

- [System. Management. Automation. Provider. drvecmdletprovider. removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi, sağlayıcınızın `Remove-PSDrive` sağlayıcı cmdlet 'ini nasıl desteklediğini tanımlar. Bu cmdlet, kullanıcının veri deposundan sürücü kaldırmasına izin verir.

## <a name="item-enabled-providers"></a>Öğe etkin sağlayıcılar

Öğe etkin sağlayıcılar, kullanıcının veri deposundaki öğeleri almasını, ayarlamanızı veya temizlemesini sağlar. "Öğe", kullanıcının bağımsız olarak erişebileceği veya yönetebileceği veri deposunun bir öğesidir. Öğe etkin bir sağlayıcı oluşturmak için, sağlayıcı sınıfınız [System. Management. Automation. Provider. ıtemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfından veya bu sınıftan türetilen başka bir sınıftan türetilmelidir.

**System. Management. Automation. Provider. ıtemcmdletprovider** sınıfı, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'i çağırmak `ClearItem` için çağırdığı yöntemin üzerine yazmanız gerekir (örneğin, `Clear-Item` cmdlet 'in yöntemi gibi) ve isteğe bağlı olarak `ClearItemDynamicParameters` bir ikinci yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

- [System. Management. Automation. Provider. ıtemcmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) ve [System. Management. Automation. Provider. ItemCmdletProvider. Clearıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) yöntemleri, `Clear-Item`sağlayıcınızınşunlarınasıldesteklediğinitanımlarsağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposundaki bir öğenin değerini kaldırmasına izin verir.

- [System. Management. Automation. Provider. ıtemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ve [System. Management. Automation. Provider. ItemCmdletProvider. Getıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) yöntemleri, `Get-Item` sağlayıcınızın şunları nasıl desteklediğini tanımlar sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposundan veri almasına izin verir.

- [System. Management. Automation. Provider. ıtemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ve [System. Management. Automation. Provider. ItemCmdletProvider. Setıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) yöntemleri, `Set-Item` sağlayıcınızın şunları nasıl desteklediğini tanımlar sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposundaki öğelerin değerlerini güncelleştirmesine izin verir.

- [System. Management. Automation. Provider. ıtemcmdletprovider. ınvokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) ve [System. Management. Automation. Provider. ıtemcmdletprovider. ınvokedefaultactiondynamicparameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Invoke-Item` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının öğe tarafından belirtilen varsayılan eylemi gerçekleştirmesini sağlar.

- [System. Management. Automation. Provider. ıtemcmdletprovider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) ve [System. Management. Automation. Provider. ItemCmdletProvider. ıtemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) yöntemleri sağlayıcınızın şunları nasıl desteklediğini tanımlar `Test-Path`sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının bir yolun tüm öğelerinin mevcut olup olmadığını belirlemesine izin verir.

**System. Management. Automation. Provider. ItemCmdletProvider** sınıfı, sağlayıcı cmdlet 'lerini uygulamak için kullanılan yöntemlere ek olarak aşağıdaki yöntemleri de tanımlar:

- [System. Management. Automation. Provider. ıtemcmdletprovider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) yöntemi, kullanıcının sağlayıcı yolunu belirtirken joker karakter kullanmasına izin verir.

- [System. Management. Automation. Provider. ıtemcmdletprovider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) , bir yolun sözdizimsel olup olmadığını ve sağlayıcı için anlam açısından geçerli olduğunu belirlemede kullanılır.

## <a name="container-enabled-providers"></a>Kapsayıcı özellikli sağlayıcılar

Kapsayıcı özellikli sağlayıcılar, kullanıcının kapsayıcı olan öğeleri yönetmesine izin verir. Kapsayıcı, ortak bir üst öğe altındaki alt öğeler grubudur. Kapsayıcı özellikli bir sağlayıcı oluşturmak için, sağlayıcı sınıfınızın [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfından veya bu sınıftan türeyen başka bir sınıftan türetilmesi gerekir.

> [!IMPORTANT]
> Kapsayıcı özellikli sağlayıcılar, iç içe geçmiş kapsayıcılar içeren veri depolarına erişemez. Bir kapsayıcının alt öğesi başka bir kapsayıcı ise, bir gezinti etkin sağlayıcı uygulamanız gerekir.

**System. Management. Automation. Provider. ContainerCmdletProvider** sınıfı, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'i çağırmak `CopyItem` için çağırdığı yöntemin üzerine yazmanız gerekir (örneğin, `Copy-Item` cmdlet 'in yöntemi gibi) ve isteğe bağlı olarak `CopyItemDynamicParameters` bir ikinci yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

- [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ve [System. Management. Automation. Provider. containercmdletprovider. Copyıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) yöntemleri sağlayıcınızın şunları nasıl desteklediğini tanımlar `Copy-Item` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının bir öğeyi bir konumdan diğerine kopyalamasını sağlar.

- [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ve [System. Management. Automation. Provider. Containercmdletprovider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Get-ChildItem` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının üst öğenin alt öğelerini almasına izin verir.

- [System. Management. Automation. Provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ve [System. Management. Automation. Provider. Containercmdletprovider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Name` parametresi belirtilmişse `Get-ChildItem` sağlayıcı cmdlet 'ini destekler.

- [System. Management. Automation. Provider. ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) ve [System. Management. Automation. Provider. Containercmdletprovider. Newwitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) yöntemleri, sağlayıcınızınşunlarınasıldesteklediğinitanımlar`New-Item` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposunda yeni öğeler oluşturmasına izin verir.

- [System. Management. Automation. Provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ve [System. Management. Automation. Provider. containercmdletprovider. Removeıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) yöntemleri sağlayıcınızın şunları nasıl desteklediğini tanımlar `Remove-Item` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposundan öğe kaldırmasına izin verir.

- [System. Management. Automation. Provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) ve [System. Management. Automation. Provider. Containercmdletprovider. Renameıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) yöntemleri sağlayıcınızın şunları nasıl desteklediğini tanımlar `Rename-Item` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının veri deposundaki öğeleri yeniden adlandırmasına izin verir.

**System. Management. Automation. Provider. ContainerCmdletProvider** sınıfı, sağlayıcı cmdlet 'lerini uygulamak için kullanılan yöntemlere ek olarak aşağıdaki yöntemleri de tanımlar:

- [System. Management. Automation. Provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) yöntemi, bir öğenin alt öğeler içerip içermediğini anlamak için sağlayıcı sınıfı tarafından kullanılabilir.

- [System. Management. Automation. Provider. ContainerCmdletProvider. convertpath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) yöntemi sağlayıcı sınıfı tarafından belirtilen bir yoldan sağlayıcıya özgü yeni bir yol oluşturmak için kullanılabilir.

## <a name="navigation-enabled-providers"></a>Gezinti özellikli sağlayıcılar

Gezinti özellikli sağlayıcılar, kullanıcının veri deposundaki öğeleri taşımasına izin verir. Gezinti etkin bir sağlayıcı oluşturmak için, sağlayıcı sınıfınızın [System. Management. Automation. Provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfından türetilmesi gerekir.

**System. Management. Automation. Provider. NavigationCmdletProvider** sınıfı, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'i çağırmak `MoveItem` için çağırdığı yöntemin üzerine yazmanız gerekir (örneğin, `Move-Item` cmdlet 'in yöntemi gibi) ve isteğe bağlı olarak `MoveItemDynamicParameters` bir ikinci yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

- [System. Management. Automation. Provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ve [System. Management. Automation. Provider. navigationcmdletprovider. Moveıtemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) yöntemleri sağlayıcınızın şunları nasıl desteklediğini tanımlar `Move-Item` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının depodaki bir konumdan başka bir konuma taşınmasını sağlar.

- [System. Management. Automation. Provider. navigationcmdletprovider. makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi, sağlayıcınızın `Join-Path` sağlayıcı cmdlet 'ini nasıl desteklediğini tanımlar. Bu cmdlet, bir sağlayıcının iç yolunu oluşturmak için kullanıcının bir üst ve alt yol kesimini birleştirmesine olanak tanır.

Sağlayıcı cmdlet 'leri uygulamak için kullanılan yöntemlere ek olarak **System. Management. Automation. Provider. NavigationCmdletProvider** sınıfı da aşağıdaki yöntemleri tanımlar:

- [System. Management. Automation. Provider. NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi bir yolun alt düğümünün adını ayıklar.

- [System. Management. Automation. Provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi bir yolun üst kısmını ayıklar.

- [System. Management. Automation. Provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi öğenin bir kapsayıcı öğe olup olmadığını belirler. Bu bağlamda, bir kapsayıcı ortak bir üst öğe altındaki alt öğeler grubudur.

- [System. Management. Automation. Provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) yöntemi, belirtilen temel yola göre bir öğenin yolunu döndürür.

## <a name="content-enabled-providers"></a>İçerik etkinleştirilmiş sağlayıcılar

İçerik etkinleştirilmiş sağlayıcılar, kullanıcının bir veri deposundaki öğelerin içeriğini temizlemesini, almasını veya değiştirmesine izin verir.
Örneğin, dosya sistemi sağlayıcısı dosya sistemindeki dosyaların içeriğini temizlemenizi, almanızı ve ayarlamanıza olanak sağlar. İçerik etkinleştirilmiş bir sağlayıcı oluşturmak için, sağlayıcı sınıfınızın [System. Management. Automation. Provider. ıtentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabiriminin yöntemlerini uygulaması gerekir.

**System. Management. Automation. Provider. ıtentcmdletprovider** arabirimi, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'i çağırmak `ClearContent` için çağırdığı yöntemin üzerine yazmanız gerekir (örneğin, `Clear-Content` cmdlet 'in yöntemi gibi) ve isteğe bağlı olarak `ClearContentDynamicParameters` bir ikinci yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

- [System. Management. Automation. Provider. ıtentcmdletprovider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ve [System. Management. Automation. Provider. ıtentcmdletprovider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) yöntemleri sağlayıcınızın nasıl desteklediğini tanımlar `Clear-Content` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının öğeyi silmeksizin öğenin içeriğini silmesine izin verir.

- [System. Management. Automation. Provider. ıtentcmdletprovider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) ve [System. Management. Automation. Provider. ıditentcmdletprovider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Get-Content` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının bir öğenin içeriğini almasına izin verir. Yöntemi, içeriği okumak için kullanılan yöntemleri tanımlayan bir [System. Management. Automation. Provider. ıtentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) arabirimi döndürür. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`

- [System. Management. Automation. Provider. ıtentcmdletprovider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ve [System. Management. Automation. Provider. ıtentcmdletprovider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Set-Content` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının bir öğenin içeriğini güncelleştirmesine izin verir. Yöntemi, içeriği yazmak için kullanılan yöntemleri tanımlayan bir [System. Management. Automation. Provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) arabirimi döndürür. `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`

## <a name="property-enabled-providers"></a>Özellik etkinleştirilmiş sağlayıcılar

Özellik etkinleştirilmiş sağlayıcılar, kullanıcının veri deposundaki öğelerin özelliklerini yönetmesine olanak tanır.
Özellik etkin bir sağlayıcı oluşturmak için, sağlayıcı sınıfınızın [System. Management. Automation. Provider. ıpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider yöntemlerini uygulaması gerekir ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)arabirimler. Çoğu durumda, bir sağlayıcı cmdlet 'ini desteklemek için PowerShell altyapısının cmdlet 'ini `ClearProperty` çağırmak için çağırdığı yöntemin (Clear-Property cmdlet 'i için yöntemi gibi) üzerine yazmanız gerekir ve isteğe bağlı olarak `ClearPropertyDynamicParameters` ikinci bir yöntemin üzerine yazabilirsiniz, örneğin , cmdlet 'e dinamik parametreler eklemek için.

**System. Management. Automation. Provider. ıpropertycmdletprovider** arabirimi, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar:

- [System. Management. Automation. Provider. ıpropertycmdletprovider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) ve [System. Management. Automation. Provider. ıpropertycmdletprovider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) yöntemleri sağlayıcınızın nasıl olduğunu tanımlar `Clear-ItemProperty` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının bir özelliğin değerini silmesine izin verir.

- [System. Management. Automation. Provider. ıpropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) ve [System. Management. Automation. Provider. ıpropertycmdletprovider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) yöntemleri sağlayıcınızın nasıl desteklediğini tanımlar `Get-ItemProperty` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının bir öğenin özelliğini almasına izin verir.

- [System. Management. Automation. Provider. ıpropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ve [System. Management. Automation. Provider. ıpropertycmdletprovider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) yöntemleri sağlayıcınızın nasıl desteklediğini tanımlar `Set-ItemProperty` sağlayıcı cmdlet 'i. Bu cmdlet, kullanıcının bir öğenin özelliklerini güncelleştirmesine izin verir.

  **System. Management. Automation. Provider. ıdynamicpropertycmdletprovider** arabirimi, belirli sağlayıcı cmdlet 'lerini uygulamak için aşağıdaki yöntemleri tanımlar:

- [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) yöntemleri sağlayıcı, `Copy-ItemProperty` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının bir özelliği ve değerini bir konumdan diğerine kopyalamasını sağlar.

- [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) yöntemleri sağlayıcı, `Move-ItemProperty` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının bir özelliği ve değerini bir konumdan diğerine taşımasını sağlar.

- [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) yöntemleri, sağlayıcı, `New-ItemProperty` sağlayıcı cmdlet 'ini destekler. Bu cmdlet, kullanıcının yeni bir özellik oluşturmasına ve değerini ayarlamasına olanak tanır.

- [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) yöntemleri nasıl yapılacağını tanımlar sağlayıcınız `Remove-ItemProperty` cmdlet 'ini destekliyor. Bu cmdlet, kullanıcının bir özelliği ve değerini silmesine izin verir.

- [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) ve [System. Management. Automation. Provider. ıdynamicpropertycmdletprovider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) yöntemleri nasıl yapılacağını tanımlar sağlayıcınız `Rename-ItemProperty` cmdlet 'ini destekliyor. Bu cmdlet, kullanıcının bir özelliğin adını değiştirmesine izin verir.

## <a name="see-also"></a>Ayrıca bkz.

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)
