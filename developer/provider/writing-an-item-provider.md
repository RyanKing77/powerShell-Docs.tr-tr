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
# <a name="writing-an-item-provider"></a><span data-ttu-id="4060a-102">Bir öğe sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="4060a-102">Writing an item provider</span></span>

<span data-ttu-id="4060a-103">Bu konuda, veri deposundaki öğelerini işlemek ve yöntemleri bir Windows PowerShell sağlayıcısının açıklar.</span><span class="sxs-lookup"><span data-stu-id="4060a-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="4060a-104">Öğeleri erişebilmesi için bir sağlayıcı öğesinden türetilmelidir [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4060a-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="4060a-105">Bu konudaki örneklerde sağlayıcı, bir Access veritabanının kendi veri deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="4060a-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="4060a-106">Çeşitli yardımcı yöntemler ve veritabanıyla etkileşime girmek için kullanılan sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="4060a-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="4060a-107">Yardımcı yöntemler içeren tam bir örnek için bkz. [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="4060a-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="4060a-108">Windows PowerShell sağlayıcıları hakkında daha fazla bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4060a-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="4060a-109">Uygulama öğesi yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4060a-109">Implementing item methods</span></span>

<span data-ttu-id="4060a-110">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı erişmek ve bir veri deposundaki öğeleri işlemek için kullanılan çeşitli yöntemler sunar.</span><span class="sxs-lookup"><span data-stu-id="4060a-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="4060a-111">Bu yöntemleri tam bir listesi için bkz. [ItemCmdletProvider yöntemleri](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="4060a-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="4060a-112">Bu örnekte Biz bu yöntemlerin dört uygular.</span><span class="sxs-lookup"><span data-stu-id="4060a-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="4060a-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) belirtilen yolda bir öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="4060a-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="4060a-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) belirtilen öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4060a-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="4060a-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) öğeyi belirtilen yolda mevcut olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4060a-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="4060a-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) veri deposundaki bir konuma eşler, görmek için bir yol denetler.</span><span class="sxs-lookup"><span data-stu-id="4060a-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="4060a-117">Bu konu başlığı altındaki bilgiler geliştirir [Windows PowerShell sağlayıcısı hızlı](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="4060a-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="4060a-118">Bu konuda bir sağlayıcı projeyi kurmak ilişkin temel bilgileri ele alınmamaktadır veya devralınan yöntemleri uygulamak nasıl [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı oluşturun ve sürücülerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4060a-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="4060a-119">Sağlayıcı Sınıf Bildirme</span><span class="sxs-lookup"><span data-stu-id="4060a-119">Declaring the provider class</span></span>

<span data-ttu-id="4060a-120">Türetmek için sağlayıcı bildirmek [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı ve onunla süslemek [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="4060a-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="4060a-121">GetItem uygulama</span><span class="sxs-lookup"><span data-stu-id="4060a-121">Implementing GetItem</span></span>

<span data-ttu-id="4060a-122">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) kullanıcı çağırdığında PowerShell altyapısı tarafından çağrılır [Microsoft.PowerShell.Commands.Get öğesi](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet'ini, Sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4060a-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="4060a-123">Yöntemi, belirtilen yolda öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4060a-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="4060a-124">Access veritabanı örnekte yöntemi öğesi sürücünün veritabanı veya bir satır veritabanındaki bir tablo olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4060a-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="4060a-125">Yöntemi çağrılarak öğesi PowerShell Altyapısı'na gönderir [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4060a-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="4060a-126">SetItem uygulama</span><span class="sxs-lookup"><span data-stu-id="4060a-126">Implementing SetItem</span></span>

<span data-ttu-id="4060a-127">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemi, PowerShell altyapısı çağrıları tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Set öğesi](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet'i .</span><span class="sxs-lookup"><span data-stu-id="4060a-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="4060a-128">Belirtilen yolda öğenin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4060a-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="4060a-129">Access veritabanı örnekte, yalnızca çağırılıyorsa yöntem için bu öğeyi bir satır olması durumunda bir öğenin değerini ayarlamak için mantıklı [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) öğesi olmadığında bir satır.</span><span class="sxs-lookup"><span data-stu-id="4060a-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="4060a-130">ItemExists uygulama</span><span class="sxs-lookup"><span data-stu-id="4060a-130">Implementing ItemExists</span></span>

<span data-ttu-id="4060a-131">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) yöntemi, PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Test yolu](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4060a-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="4060a-132">Yöntemi, belirtilen yolda bir öğe olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4060a-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="4060a-133">Öğe mevcut olursa, yöntem PowerShell altyapısına çağırarak aktarır [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="4060a-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="4060a-134">IsValidPath uygulama</span><span class="sxs-lookup"><span data-stu-id="4060a-134">Implementing IsValidPath</span></span>

<span data-ttu-id="4060a-135">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) yöntemi, belirtilen yol için geçerli sağlayıcıyı sözdizimsel olarak geçerli olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4060a-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="4060a-136">Bir öğe yolunda mevcut olup olmadığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="4060a-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="4060a-137">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4060a-137">Next steps</span></span>

<span data-ttu-id="4060a-138">Tipik bir gerçek sağlayıcısı diğer öğeleri içeren öğelerini destekleyen ve başka bir sürücü için bir yoldan öğeleri taşıma yeteneğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4060a-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="4060a-139">Kapsayıcıları destekleyen bir sağlayıcı örneği için bkz: [kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4060a-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="4060a-140">Taşıma öğelerini destekleyen bir sağlayıcı örneği için bkz: [Gezinti sağlayıcısı yazma](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4060a-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4060a-141">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4060a-141">See Also</span></span>

[<span data-ttu-id="4060a-142">Bir kapsayıcı sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="4060a-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="4060a-143">Bir gezinti sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="4060a-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="4060a-144">Windows PowerShell sağlayıcısındaki genel bakış</span><span class="sxs-lookup"><span data-stu-id="4060a-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)