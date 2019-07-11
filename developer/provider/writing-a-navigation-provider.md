---
title: Bir gezinti sağlayıcısı yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734734"
---
# <a name="writing-a-navigation-provider"></a>Bir gezinti sağlayıcısı yazma

Bu konu, iç içe geçmiş kapsayıcılar öğeleri ve göreli yolları taşıma (çok düzeyli veri depoları) destekleyen bir Windows PowerShell sağlayıcısı yöntemlerini uygulamak açıklar. Bir gezinti sağlayıcısı öğesinden türetilmelidir [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.

Bu konudaki örneklerde sağlayıcı, bir Access veritabanının kendi veri deposu olarak kullanır. Çeşitli yardımcı yöntemler ve veritabanıyla etkileşime girmek için kullanılan sınıfları vardır. Yardımcı yöntemler içeren tam bir örnek için bkz. [AccessDBProviderSample05](./accessdbprovidersample05.md).

Windows PowerShell sağlayıcıları hakkında daha fazla bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Gezinme yöntemlerinden uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı, iç içe geçmiş kapsayıcılar, göreli yolları ve taşıma öğelerini destekleyen yöntemler uygular. Bu yöntemleri tam bir listesi için bkz. [NavigationCmdletProvider yöntemleri](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).

> [!NOTE]
> Bu konu başlığı altındaki bilgiler geliştirir [Windows PowerShell sağlayıcısı hızlı](./windows-powershell-provider-quickstart.md). Bu konuda bir sağlayıcı projeyi kurmak ilişkin temel bilgileri ele alınmamaktadır veya devralınan yöntemleri uygulamak nasıl [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı oluşturun ve sürücülerini kaldırın. Bu konuda ayrıca yöntemleri tarafından kullanıma sunulan uygulama konularını kapsamaz [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) veya [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfları. Öğe cmdlet'leri uygulamak nasıl gösteren bir örnek için bkz: [öğe sağlayıcısı yazma](./writing-an-item-provider.md). Nasıl kapsayıcı cmdlet'leri uygulayacağınızı gösteren bir örnek için bkz: [kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Sağlayıcı Sınıf Bildirme

Türetmek için sağlayıcı bildirmek [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı ve onunla süslemek [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>IsItemContainer uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi öğesini belirtilen yolda bir kapsayıcı olup olmadığını denetler.

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a>GetChildName uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi, belirtilen yolda alt öğesinin adı özelliği alır. Bir kapsayıcının alt öğesini belirtilen yolda değilse, bu yöntem yolu döndürmesi gerekir.

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a>GetParentPath uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi, belirtilen yolda üst öğenin yolunu alır. (Üst öğe sahip olması) veri deposunun kök öğesini belirtilen yolda ise bu yöntem kök yolu döndürmesi gerekir.

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a>MakePath uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi birleştiren bir belirtilen üst ile (yolu hakkında bilgi türleri için bir sağlayıcı iç yolu oluşturmak için belirtilen alt yolu Sağlayıcı desteği, bkz: [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md). Bir kullanıcı çağırdığında PowerShell altyapısı bu yöntemi çağırır [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet'i.

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a>NormalizeRelativePath uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) yöntemi `path` ve `basepath` parametreleri ve içineşdeğernormalleştirilmişbiryoldöndürür`path`parametresi ve göreceli olarak `basepath` parametresi.

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a>MoveItem uygulama

[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi belirtilen yolu bir öğe için belirtilen hedef yolu taşır. Bir kullanıcı çağırdığında PowerShell altyapısı bu yöntemi çağırır [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet'i.

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md)

[Windows PowerShell sağlayıcısındaki genel bakış](./windows-powershell-provider-overview.md)