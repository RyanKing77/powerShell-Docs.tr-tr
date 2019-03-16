---
title: Sağlayıcı cmdlet parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057051"
---
# <a name="provider-cmdlet-parameters"></a>Sağlayıcı cmdlet parametreleri

Bir dizi cmdlet destekleyen tüm sağlayıcılar için kullanılabilir olan statik parametreler, belirli bir değer sağlayıcı cmdlet'inin statik parametreler için kullanıcının belirttiği alındığında, eklenen de dinamik parametreleri sağlayıcısı cmdlet'leri gelir.

## <a name="provider-cmdlet-static-parameters"></a>Sağlayıcı cmdlet'i statik Parametreler

Statik parametreler, Windows PowerShell tarafından tanımlanır. Çok sayıda bu parametreleri, tüm sağlayıcılar arasında tutarlılık sağlamak ve daha basit bir geliştirme deneyimi sunmak için Windows PowerShell tarafından uygulanır. Bu parametre örnekler `literalPath`, `exclude`, ve `include` parametrelerinin `Get-Item` cmdlet'i. Sağlayıcınıza özgü olan eylemler sağlamak için daha küçük bir dizi bu parametrenin üzerine yazılabilir. Bu parametre örnekler `Path` ve `Value` parametresinin `Set-Item` cmdlet'i. Sağlayıcı cmdlet'ler için geçersiz kılınabilir Parametreler aşağıda verilmiştir.

`Clear-Content` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Clear-Content` cmdlet'i uygulayarak [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)yöntemi.

`Clear-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Clear-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) yöntem.

`Clear-ItemProperty` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `Name` parametrelerinin `Clear-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) yöntemi.

`Copy-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path`, `Destination`, ve `Recurse` parametrelerinin `Copy-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) yöntemi.

Get-ChildItems cmdlet'i sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz `Path` ve `Recurse` parametrelerinin `Get-ChildItem` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ve [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) yöntemleri.

`Get-Content` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Get-Content` cmdlet'i uygulayarak [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) yöntemi.

`Get-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Get-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) yöntemi.

`Get-ItemProperty` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `Name` parametrelerinin `Get-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) yöntemi.

`Invoke-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Invoke-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)yöntemi.

`Move-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `Destination` parametrelerinin `Move-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi.

`New-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path`, `ItemType`, ve `Value` parametrelerinin `New-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemi.

`New-ItemProperty` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path`, `Name`, `PropertyType`, ve `Value` parametrelerinin `New-ItemProperty` cmdlet'i uygulayarak [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) yöntemi.

`Remove-Item` Sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz `Path` ve `Recurse` parametrelerinin `Remove-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) yöntemi.

`Remove-ItemProperty` Sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz `Path` ve `Name` parametrelerinin `Remove-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) yöntemi.

`Rename-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `NewName` parametrelerinin `Rename-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) yöntemi.

`Rename-ItemProperty` Sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz `Path`, `NewName`, ve `Name` parametrelerinin `Rename-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) yöntemi.

`Set-Content` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Set-Content` cmdlet'i uygulayarak [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) yöntemi.

`Set-Item` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `Value` parametrelerinin `Set-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemi.

`Set-ItemProperty` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` ve `Value` parametrelerinin `Set-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) yöntemi.

`Test-Path` sağlayıcınız geçirilen değerlerin nasıl kullanacağını tanımlayabilirsiniz cmdlet'i `Path` parametresinin `Test-Path` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)yöntemi.

Ayrıca, bu parametre isteğe bağlı veya gerekli olup olmadıkları gibi özellikleri belirtemezsiniz veya, bu parametreleri bir diğer ad verin veya doğrulama öznitelikleri belirtin. Tek başına cmdlet'ler gibi öznitelikleri kullanarak parametre özellikleri buna karşılık, belirtebilirsiniz `Parameters` özniteliği.

## <a name="provider-cmdlet-dynamic-parameters"></a>Sağlayıcı cmdlet'i dinamik parametreleri

Cmdlet sağlayıcıları için dinamik parametreler, tek başına cmdlet'leri için dinamik sağlayıcıları benzerdir. Kullanıcı varsayılan parametrelerden biri için belirli bir değer gibi belirttiğinde her iki durumda da, cmdlet'e parametre eklenen `path` parametresi. Ancak, statik parametrelerin tümü dinamik parametreleri eklenmesini tetiklemek için kullanılabilir. Dinamik parametreler hakkında daha fazla bilgi için bkz. [sağlayıcısı Cmdlet dinamik parametreleri](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Ayrıca bkz:

[Sağlayıcı cmdlet'i dinamik parametreleri](./provider-cmdlet-dynamic-parameters.md)

[Bir Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)