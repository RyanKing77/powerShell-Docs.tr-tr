---
title: Sağlayıcı cmdlet dinamik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058241"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Sağlayıcı cmdlet dinamik parametreleri

Sağlayıcıları cmdlet'inin statik parametrelerden biri için belirli bir değer kullanıcının belirttiği alındığında, bir sağlayıcı cmdlet'e eklenen dinamik parametreleri tanımlayabilirsiniz. Örneğin, bir sağlayıcı tabanlı farklı dinamik parametreler ekleyebilirsiniz hangi yola çağırdığınızda, kullanıcının belirttiği `Get-Item` veya `Set-Item` sağlayıcısı cmdlet'leri.

## <a name="dynamic-parameter-methods"></a>Dinamik parametre yöntemleri

Dinamik parametreler, dinamik parametre yöntemlerden birini gibi uygulama tarafından tanımlanan [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) ve [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s yöntemleri. Bu yöntemler, tek başına cmdlet'leri için benzer öznitelikleri ile donatılmış ortak özelliklere sahip bir nesne döndürür. İşte bir örnek uygulaması [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) Sertifika Sağlayıcısı'ndan alınan yöntemi:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Farklı olarak statik parametreler sağlayıcısı cmdlet'lerin parametre tek başına cmdlet'leri tanımlanan aynı şekilde bu parametreleri özelliklerini belirtebilirsiniz. Sertifika Sağlayıcısı'ndan gerçekleştirilen bir dinamik parametre sınıfı örneği aşağıda verilmiştir:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Dinamik parametreler

Dinamik parametreleri eklemek için kullanılabilir statik parametreler listesi aşağıda verilmiştir.

`Clear-Content` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` uygulayarak Clear-Clear cmdlet parametresi [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) yöntemi.

`Clear-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Clear-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) yöntemi.

`Clear-ItemProperty` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Clear-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) yöntemi.

`Copy-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path`, `Destination`, ve `Recurse` parametrelerinin `Copy-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) yöntemi.

Get-ChildItems cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Recurse` parametrelerinin `Get-ChildItem` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) ve [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) yöntemleri.

`Get-Content` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Get-Content` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) yöntemi.

`Get-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Get-Item` cmdlet'i uygulayarak [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) yöntemi.

`Get-ItemProperty` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Name` parametrelerinin `Get-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) yöntemi.

`Invoke-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Invoke-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) yöntemi.

`Move-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Destination` parametrelerinin `Move-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) yöntemi.

`New-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path`, `ItemType`, ve `Value` parametrelerinin `New-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) yöntemi.

`New-ItemProperty` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path`, `Name`, `PropertyType`, ve `Value` parametrelerinin `New-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) yöntemi.

`New-PSDrive` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) tarafından döndürülen nesne `New-PSDrive` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemi.

`Remove-Item` Tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Recurse` parametrelerinin `Remove-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) yöntemi.

`Remove-ItemProperty` Tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Name` parametrelerinin `Remove-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) yöntemi.

`Rename-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `NewName` parametrelerinin `Rename-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) yöntemi.

`Rename-ItemProperty` Tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path`, `Name`, ve `NewName` parametrelerinin `Rename-ItemProperty` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) yöntemi.

`Set-Content` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Set-Content` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) yöntemi.

`Set-Item` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Value` parametrelerinin `Set-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) yöntemi.

`Set-ItemProperty` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` ve `Value` parametrelerinin `Set-Item` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) yöntemi.

`Test-Path` cmdlet'i tarafından tetiklenen dinamik parametreleri tanımlayabilirsiniz `Path` parametresinin `Test-Path` cmdlet'i uygulayarak [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) yöntemi.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)