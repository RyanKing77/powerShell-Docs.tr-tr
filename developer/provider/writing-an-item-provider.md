---
title: Bir öğe sağlayıcısı yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058207"
---
# <a name="writing-an-item-provider"></a>Bir öğe sağlayıcısı yazma

Bu konuda, veri deposundaki öğelerini işlemek ve yöntemleri bir Windows PowerShell sağlayıcısının açıklar. Öğeleri erişebilmesi için bir sağlayıcı öğesinden türetilmelidir [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.

Bu konudaki örneklerde sağlayıcı, bir Access veritabanının kendi veri deposu olarak kullanır. Çeşitli yardımcı yöntemler ve veritabanıyla etkileşime girmek için kullanılan sınıfları vardır. Yardımcı yöntemler içeren tam bir örnek için bkz. [AccessDBProviderSample03](./accessdbprovidersample03.md)

Windows PowerShell sağlayıcıları hakkında daha fazla bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Uygulama öğesi yöntemleri

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı erişmek ve bir veri deposundaki öğeleri işlemek için kullanılan çeşitli yöntemler sunar. Bu yöntemleri tam bir listesi için bkz. [ItemCmdletProvider yöntemleri](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). Bu örnekte Biz bu yöntemlerin dört uygular. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) belirtilen yolda bir öğeyi alır. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) belirtilen öğenin değerini ayarlar. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) öğeyi belirtilen yolda mevcut olup olmadığını denetler. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) veri deposundaki bir konuma eşler, görmek için bir yol denetler.

> [!NOTE]
> Bu konu başlığı altındaki bilgiler geliştirir [Windows PowerShell sağlayıcısı hızlı](./windows-powershell-provider-quickstart.md). Bu konuda bir sağlayıcı projeyi kurmak ilişkin temel bilgileri ele alınmamaktadır veya devralınan yöntemleri uygulamak nasıl [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı oluşturun ve sürücülerini kaldırın.

### <a name="declaring-the-provider-class"></a>Sağlayıcı Sınıf Bildirme

Türetmek için sağlayıcı bildirmek [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı ve onunla süslemek [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem uygulama

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) kullanıcı çağırdığında PowerShell altyapısı tarafından çağrılır [Microsoft.PowerShell.Commands.Get öğesi](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet'ini, Sağlayıcı. Yöntemi, belirtilen yolda öğeyi döndürür. Access veritabanı örnekte yöntemi öğesi sürücünün veritabanı veya bir satır veritabanındaki bir tablo olup olmadığını denetler. Yöntemi çağrılarak öğesi PowerShell Altyapısı'na gönderir [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) yöntemi.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>SetItem uygulama

[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemi, PowerShell altyapısı çağrıları tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Set öğesi](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet'i . Belirtilen yolda öğenin değerini ayarlar.

Access veritabanı örnekte, yalnızca çağırılıyorsa yöntem için bu öğeyi bir satır olması durumunda bir öğenin değerini ayarlamak için mantıklı [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) öğesi olmadığında bir satır.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>ItemExists uygulama

[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) yöntemi, PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Test yolu](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet'i. Yöntemi, belirtilen yolda bir öğe olup olmadığını belirler. Öğe mevcut olursa, yöntem PowerShell altyapısına çağırarak aktarır [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>IsValidPath uygulama

[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) yöntemi, belirtilen yol için geçerli sağlayıcıyı sözdizimsel olarak geçerli olup olmadığını denetler. Bir öğe yolunda mevcut olup olmadığını denetlemez.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Sonraki adımlar

Tipik bir gerçek sağlayıcısı diğer öğeleri içeren öğelerini destekleyen ve başka bir sürücü için bir yoldan öğeleri taşıma yeteneğine sahiptir. Kapsayıcıları destekleyen bir sağlayıcı örneği için bkz: [kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md). Taşıma öğelerini destekleyen bir sağlayıcı örneği için bkz: [Gezinti sağlayıcısı yazma](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md)

[Bir gezinti sağlayıcısı yazma](./writing-a-navigation-provider.md)

[Windows PowerShell sağlayıcısındaki genel bakış](./windows-powershell-provider-overview.md)