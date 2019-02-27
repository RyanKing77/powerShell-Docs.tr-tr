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
ms.openlocfilehash: a789b392bddd344ad583c93a1a55302329df9917
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852090"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="1dfc5-102">Bir gezinti sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="1dfc5-102">Writing a navigation provider</span></span>

<span data-ttu-id="1dfc5-103">Bu konu, iç içe geçmiş kapsayıcılar öğeleri ve göreli yolları taşıma (çok düzeyli veri depoları) destekleyen bir Windows PowerShell sağlayıcısı yöntemlerini uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="1dfc5-104">Bir gezinti sağlayıcısı öğesinden türetilmelidir [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="1dfc5-105">Bu konudaki örneklerde sağlayıcı, bir Access veritabanının kendi veri deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="1dfc5-106">Çeşitli yardımcı yöntemler ve veritabanıyla etkileşime girmek için kullanılan sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="1dfc5-107">Yardımcı yöntemler içeren tam bir örnek için bkz. [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="1dfc5-108">Windows PowerShell sağlayıcıları hakkında daha fazla bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="1dfc5-109">Gezinme yöntemlerinden uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-109">Implementing navigation methods</span></span>

<span data-ttu-id="1dfc5-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı, iç içe geçmiş kapsayıcılar, göreli yolları ve taşıma öğelerini destekleyen yöntemler uygular.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="1dfc5-111">Bu yöntemleri tam bir listesi için bkz. [NavigationCmdletProvider yöntemleri](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="1dfc5-112">Bu konu başlığı altındaki bilgiler geliştirir [Windows PowerShell sağlayıcısı hızlı](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="1dfc5-113">Bu konuda bir sağlayıcı projeyi kurmak ilişkin temel bilgileri ele alınmamaktadır veya devralınan yöntemleri uygulamak nasıl [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı oluşturun ve sürücülerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="1dfc5-114">Bu konuda ayrıca yöntemleri tarafından kullanıma sunulan uygulama konularını kapsamaz [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) veya [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="1dfc5-115">Öğe cmdlet'leri uygulamak nasıl gösteren bir örnek için bkz: [öğe sağlayıcısı yazma](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="1dfc5-116">Nasıl kapsayıcı cmdlet'leri uygulayacağınızı gösteren bir örnek için bkz: [kapsayıcı sağlayıcısı yazma](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="1dfc5-117">Sağlayıcı Sınıf Bildirme</span><span class="sxs-lookup"><span data-stu-id="1dfc5-117">Declaring the provider class</span></span>

<span data-ttu-id="1dfc5-118">Türetmek için sağlayıcı bildirmek [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı ve onunla süslemek [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="1dfc5-119">IsItemContainer uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="1dfc5-120">[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi öğesini belirtilen yolda bir kapsayıcı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="1dfc5-121">GetChildName uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-121">Implementing GetChildName</span></span>

<span data-ttu-id="1dfc5-122">[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi, belirtilen yolda alt öğesinin adı özelliği alır.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="1dfc5-123">Bir kapsayıcının alt öğesini belirtilen yolda değilse, bu yöntem yolu döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="1dfc5-124">GetParentPath uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-124">Implementing GetParentPath</span></span>

<span data-ttu-id="1dfc5-125">[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi, belirtilen yolda üst öğenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="1dfc5-126">(Üst öğe sahip olması) veri deposunun kök öğesini belirtilen yolda ise bu yöntem kök yolu döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="1dfc5-127">MakePath uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-127">Implementing MakePath</span></span>

<span data-ttu-id="1dfc5-128">[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi birleştiren bir belirtilen üst ile (yolu hakkında bilgi türleri için bir sağlayıcı iç yolu oluşturmak için belirtilen alt yolu Sağlayıcı desteği, bkz: [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1dfc5-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="1dfc5-129">Bir kullanıcı çağırdığında PowerShell altyapısı bu yöntemi çağırır [Microsoft.Powershell.Commands.Join yolu](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-129">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="1dfc5-130">NormalizeRelativePath uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="1dfc5-131">[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) yöntemi `path` ve `basepath` parametreleri ve içineşdeğernormalleştirilmişbiryoldöndürür`path`parametresi ve göreceli olarak `basepath` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="1dfc5-132">MoveItem uygulama</span><span class="sxs-lookup"><span data-stu-id="1dfc5-132">Implementing MoveItem</span></span>

<span data-ttu-id="1dfc5-133">[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi belirtilen yolu bir öğe için belirtilen hedef yolu taşır.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="1dfc5-134">Bir kullanıcı çağırdığında PowerShell altyapısı bu yöntemi çağırır [Microsoft.Powershell.Commands.Move öğesi](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1dfc5-134">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1dfc5-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1dfc5-135">See Also</span></span>

[<span data-ttu-id="1dfc5-136">Bir kapsayıcı sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="1dfc5-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="1dfc5-137">Windows PowerShell sağlayıcısındaki genel bakış</span><span class="sxs-lookup"><span data-stu-id="1dfc5-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)