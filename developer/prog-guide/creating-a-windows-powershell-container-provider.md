---
title: Bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: e0d83a742eae2bcde2e691860a5f2b3e5862d2de
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430052"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Windows PowerShell Kapsayıcı Sağlayıcısı Oluşturma

Bu konuda, çok katmanlı veri depolarına üzerinde çalışabilen bir Windows PowerShell sağlayıcısı oluşturmayı açıklar. Bu tür veri deposunun en üst düzey deposunun kök öğe içeriyor ve sonraki her düzeyi bir alt öğeleri düğüm olarak adlandırılır. Bu alt düğümleri üzerinde çalışmak kullanıcı izin vererek, bir kullanıcı hiyerarşik veri deposu etkileşim kurabilir.

Çok düzeyli veri depolarını çalışabilir sağlayıcıları, Windows PowerShell kapsayıcı sağlayıcıları olarak adlandırılır. Ancak, yalnızca bir kapsayıcı (iç içe geçmiş kapsayıcılar yok) içindeki öğeler olduğunda bir Windows PowerShell kapsayıcısı sağlayıcısı kullanılabileceğini unutmayın. İç içe geçmiş kapsayıcılar varsa, Windows PowerShell Gezinti sağlayıcıyı uygulama gerekir. Windows PowerShell Gezinti sağlayıcıyı uygulama hakkında daha fazla bilgi için bkz. [bir Windows PowerShell Gezinti sağlayıcı oluşturma](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider04.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

Burada açıklanan Windows PowerShell kapsayıcısı sağlayıcısı veritabanı tabloları ve satırları kapsayıcının öğeleri olarak tanımlanan veritabanı ile tek kapsayıcısı olarak tanımlar.

> [!CAUTION]
> Bu tasarım bir alan adı Kimliğine sahip olan bir veritabanının varsayar ve alan türünü LongInteger olduğunu unutmayın.

Bu konudaki bölümler listesi aşağıda verilmiştir. Bir Windows PowerShell kapsayıcı sağlayıcısı yazma ile bilginiz yoksa Lütfen göründüğü sırayı bu bilgileri okuyun. Ancak, bir Windows PowerShell kapsayıcı sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.

- [Bir Windows PowerShell kapsayıcı sağlayıcı sınıfı tanımlama](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Temel işlevlerini tanımlama]()

- [Alt öğeleri alınıyor](#Retrieving-Child-Items)

- [Dinamik parametreleri ekleme `Get-ChildItem` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Alt öğe adları alınıyor](#Retrieving-Child-Item-Names)

- [Dinamik parametreleri ekleme `Get-ChildItem` Cmdlet (Name)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Öğeleri yeniden adlandırma](#Renaming-Items)

- [Dinamik parametreleri ekleme `Rename-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Yeni öğeler oluşturma](#Creating-New-Items)

- [Dinamik parametreleri ekleme `New-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Bir öğe kaldırma](#Removing-Items)

- [Dinamik parametreleri ekleme `Remove-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Alt öğeleri için sorgulama](#Querying-for-Child-Items)

- [Karşılanan öğeleri](#Copying-Items)

- [Dinamik parametreleri ekleme `Copy-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme]()

- [Windows PowerShell sağlayıcısı oluşturma](#Building-the-Windows-PowerShell-Provider)

- [Windows PowerShell sağlayıcıyı test etme](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Bir Windows PowerShell kapsayıcı sağlayıcı sınıfı tanımlama

Bir Windows PowerShell kapsayıcısı sağlayıcısı, türetilen bir .NET sınıfı tanımlamanız gerekir [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) temel sınıfı. Bu bölümde açıklanan Windows PowerShell kapsayıcısı sağlayıcısı için sınıf tanımı aşağıda verilmiştir.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Bu tanım, sınıf bildirimi [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) iki parametre özniteliği içerir. İlk parametre, kullanıcı dostu bir Windows PowerShell uygulamaları tarafından kullanılan sağlayıcı adını belirtir. İkinci parametre, sağlayıcı için Windows PowerShell çalışma zamanı komut işleme sırasında ortaya koyan Windows PowerShell belirli özelliklerini belirtir. Bu sağlayıcı için eklenen hiçbir Windows PowerShell belirli özellikleri vardır.

## <a name="defining-base-functionality"></a>Temel işlevlerini tanımlama

Bölümünde anlatıldığı gibi [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı sağlanan çeşitli diğer sınıflarından türetilen farklı bir sağlayıcı işlevselliği. Bu nedenle, bir Windows PowerShell kapsayıcısı sağlayıcısı bu sınıfları tarafından sağlanan işlevselliği tümünün tanımlanması gerekir.

Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak için işlevselliği uygulamak için bkz: [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md). Ancak, çoğu sağlayıcıları (burada açıklanan sağlayıcısı dahil), Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.

Veri deposuna erişim elde etmek için sağlayıcıyı yöntemlerini uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).

Bir veri deposu, alma, ayarlama ve temizleme öğeleri gibi öğeleri işlemek için sağlayıcı tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Alt öğeleri alınıyor

Bir alt öğesini almak için Windows PowerShell kapsayıcısı sağlayıcısı kılmalı [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) çağrılarından desteklemek için gereken yöntemini `Get-ChildItem` cmdlet'i. Bu yöntem, alt öğelerini veri deposundan alır ve işlem hattına nesneler olarak yazar. Varsa `recurse` cmdlet parametresi belirtildiğinde, yöntem olduklarından, hangi düzeyde bağımsız olarak tüm alt öğeleri alır. Varsa `recurse` parametresi belirtilmezse, yöntemi yalnızca tek bir düzey alt öğeyi alır.

Uygulamasını işte [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) bu sağlayıcı için yöntemi. Bu yöntem yolu Access veritabanı gösterir ve bir veri tablosu yolunu gösterir o tablodaki satırların alt öğelerini alır veritabanı tablolarındaki tüm alt öğelerini alır dikkat edin.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>GetChildItems'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell kapsayıcısı sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Bu yöntemin uygulanmasını öğesi kullanıcıya görünür duruma sokan öğesine erişim herhangi bir biçimde dikkate almalıdır. Örneğin, bir kullanıcı (Windows PowerShell tarafından sağlanan) dosya sistemi sağlayıcısından ancak okuma erişimi aracılığıyla bir dosyaya yazma erişimi varsa, dosyanın hala var ve [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) döndürür `true`. Uygulamanızı bir üst öğenin alt listesinin oluşturulmasını görmek için denetimi gerektirebilir.

- Birden çok öğe yazarken [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi biraz zaman alabilir. Kullanarak öğeleri yazmak için sağlayıcınıza tasarlayabilirsiniz [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) birer birer yöntemi. Bu tekniği kullanarak öğeleri kullanıcı bir akışa sunacaktır.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) döngüsel bağlantıları ve benzeri olduğunda sonsuz özyineleme durumuna yol önlemek için sorumludur. Bir koşul yansıtmak için uygun bir sonlandırma özel durumun oluşturulması gerekir.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Get-Childıtem cmdlet'e dinamik parametreleri ekleme

Bazen `Get-ChildItem` çağıran cmdlet'i [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için Windows PowerShell kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Get-ChildItem` cmdlet'i.

Bu Windows PowerShell kapsayıcısı sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Alt öğe adları alınıyor

Alt öğelerin adlarını almak için Windows PowerShell kapsayıcısı sağlayıcısı kılmalı [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) çağrılarındandesteklemekiçingerekenyöntemini`Get-ChildItem`cmdlet'i, kendi `Name` parametre belirtildi. Bu yöntem, tüm kapsayıcılar için belirtilen yol veya alt öğe adları alt öğelerinin adlarını alır `returnAllContainers` cmdlet parametresi belirtildi. Bir alt ad yolunun yaprak bölümüdür. Örneğin, alt yolu c:\windows\system32\abc.dll "abc.dll" dir. Alt dizin c:\windows\system32 "system32" dir.

Uygulamasını işte [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) bu sağlayıcı için yöntemi. Belirtilen yol bir tablo yolunu gösterir, Access veritabanı (sürücü) ve satır numaralarını belirtir, tablo adları yöntemi alır dikkat edin.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>GetChildNames'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell kapsayıcısı sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

  > [!NOTE]
  > Bu kuralın özel bir durum oluştuğunda, `returnAllContainers` cmdlet parametresi belirtildi. Bu durumda, değerleri eşleşmiyor olsa bile bir kapsayıcı için herhangi bir alt ad yöntemi almalıdır [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), veya [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına kullanıcıdan sürece genellikle gizlenen nesnelerin adları almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği belirtildi. Belirtilen yol bir kapsayıcı gösteriyorsa [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) döngüsel bağlantıları ve benzeri olduğunda sonsuz özyineleme durumuna yol önlemek için sorumludur. Bir koşul yansıtmak için uygun bir sonlandırma özel durumun oluşturulması gerekir.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Get-Childıtem Cmdlet (Name) için dinamik parametreler ekleme

Bazen `Get-ChildItem` cmdlet (ile `Name` parametresi) çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için Windows PowerShell kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Get-ChildItem` cmdlet'i.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Öğeleri yeniden adlandırma

Bir öğeyi yeniden adlandırmak için Windows PowerShell kapsayıcısı sağlayıcısı kılmalı [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) çağrılarından desteklemek için gereken yöntemini `Rename-Item` cmdlet'i. Bu yöntem, sağlanan yeni bir adla belirtilen yolda öğesinin adını değiştirir. Yeni adı her zaman üst öğesi (kapsayıcı) göreli olmalıdır.

Bu sağlayıcı geçersiz [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) yöntemi. Ancak, aşağıdaki varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>RenameItem'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell kapsayıcısı sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) yöntemi yalnızca bir öğe adı değişikliği ve taşıma işlemleri için tasarlanmıştır. Uygulamanıza yöntemi bir hata varsa yazmalısınız `newName` parametresi, yol ayırıcıları içerir veya aksi halde üst konumunu değiştirmek için öğeyi neden olabilir.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına nesneleri sürece değiştirmemeniz gerekir [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği belirtildi. Belirtilen yol bir kapsayıcı gösteriyorsa [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin. Bu yöntem, bir sistem durumu, örneğin, dosyaları yeniden adlandırma değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak, çalışma zamanı Windows PowerShell ile değiştirilmesi kaynağın adını gönderir nelerin görüntüleneceğini belirleyin.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem bir ileti işlemi devam söylemek ek geri bildirim izin vermek için kullanıcıya bir onay iletisi gönderir. Bir sağlayıcı çağırmalıdır [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) olarak tehlikeli olabilecek bir sistem değişiklikleri için ek bir denetim.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Öğeyi yeniden adlandır cmdlet'e dinamik parametreleri ekleme

Bazen `Rename-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için Windows PowerShell kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) yöntemi. Bu yöntem, öğeyi belirtilen yolda parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Rename-Item` cmdlet'i.

Bu kapsayıcı sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Yeni öğeler oluşturma

Yeni öğeleri oluşturmak için bir kapsayıcı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) çağrılarından desteklemek için gereken yöntemini `New-Item` cmdlet'i. Bu yöntem, belirtilen yolda bulunan bir veri öğesi oluşturur. `type` Cmdlet parametresi yeni öğe sağlayıcısı tarafından tanımlanan türü içerir. Örneğin, dosya sistemi sağlayıcısı kullanan bir `type` parametresi "dosya" veya "dizin" değerine sahip. `newItemValue` Cmdlet parametresi yeni öğe için sağlayıcıya özgü bir değer belirtir.

Uygulamasını işte [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) bu sağlayıcı için yöntemi.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>NewItem'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemi geçirilen dize büyük küçük harf duyarsız bir karşılaştırmasını gerçekleştirmesi gereken `type` parametresi. Ayrıca az belirsiz eşleşmeleri için izin vermelidir. Örneğin, türleri "file" ve "dizin" için yalnızca ilk harfini ayırt etmek için gereklidir. Varsa `type` sağlayıcınız oluşturamıyor, bir tür parametresi gösterir [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemi ArgumentException bir iletiyle yazma türlerini belirten bir sağlayıcı oluşturabilirsiniz.

- İçin `newItemValue` parametre, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemi en az dizeleri kabul etmek için önerilir. Ayrıca tarafından alınan nesnenin türünü kabul etmelidir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) aynı yol için yöntemi. [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemi kullanabilir [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) yöntemini türleri için İstenen türü.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin. Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) true döndürür [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim olarak yöntemi.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Yeni öğe cmdlet'e dinamik parametreleri ekleme

Bazen `New-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) yöntemi. Bu yöntem, öğeyi belirtilen yolda parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `New-Item` cmdlet'i.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Öğeleri kaldırma

Öğeleri kaldırmak için Windows PowerShell sağlayıcısını kılmalı [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) çağrılarından desteklemek için gereken yöntemini `Remove-Item` cmdlet'i. Bu yöntem, belirtilen yolda veri deposundan bir öğeyi siler. Varsa `recurse` parametresinin `Remove-Item` cmdlet'i ayarlandığında `true`, yöntemi düzeylerini bağımsız olarak tüm alt öğeleri kaldırır. Parametre ayarlanırsa `false`, yöntemi yalnızca tek bir öğe belirtilen yolda kaldırır.

Bu sağlayıcı öğeyi kaldırmayı desteklemez. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>RemoveItem'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell kapsayıcısı sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, nesneleri bu yöntemi geçersiz kılmalarına sürece kaldırmamalısınız [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği ayarlanmışsa true. Belirtilen yol bir kapsayıcı gösteriyorsa [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) döngüsel bağlantıları ve benzeri olduğunda sonsuz özyineleme durumuna yol önlemek için sorumludur. Bir koşul yansıtmak için uygun bir sonlandırma özel durumun oluşturulması gerekir.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin. Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim olarak yöntemi.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Remove öğesi cmdlet'e dinamik parametreleri ekleme

Bazen `Remove-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) bu parametreleri işlemek için yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Remove-Item` cmdlet'i.

Bu kapsayıcı sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Alt öğeleri için sorgulama

Alt öğeleri belirtilen yolda mevcut olup olmadığını kontrol etmek için Windows PowerShell kapsayıcısı sağlayıcısı kılmalı [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) yöntemi. Bu yöntem döndürür `true` öğenin alt öğeleri, yoksa ve `false` Aksi takdirde. Null veya boş bir yol yöntemi tüm öğeler alt öğeleri olarak veri deposu olarak değerlendirir ve döndürür `true`.

İşte geçersiz kılma için [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) yöntemi. Olup olmadığını ChunkPath yardımcı yöntemi tarafından oluşturulan ikiden fazla yol bölümleri, yöntem döndürür `false`, yalnızca bir veritabanı kapsayıcısı ve bir tablo kapsayıcısı tanımlamış. Bu yardımcı yöntem hakkında daha fazla bilgi için bkz: ChunkPath yöntemi ele alınmıştır [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>HasChildItems'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Kapsayıcısı sağlayıcısı yürütmesinin ilginç bağlama noktaları içeren bir kök sunarsa [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) yöntemi döndürmelidir`true`ne zaman bir null veya boş bir dize geçirilir yolu.

## <a name="copying-items"></a>Öğeleri kopyalama

Öğeleri kopyalamak için kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) çağrılarından desteklemek için gereken yöntemini `Copy-Item` cmdlet'i. Bu yöntem bir veri öğesi tarafından belirtilen bir konuma kopyalar `path` parametresi tarafından belirtilen konuma cmdlet'inin `copyPath` parametresi. Varsa `recurse` parametresi belirtildiğinde, tüm alt kapsayıcıları yöntemi kopyalar. Parametre belirtilmezse, yöntemi yalnızca tek düzeyli öğeleri kopyalar.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>CopyItem'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell kapsayıcısı sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına nesneleri var olan nesnelerin üzerine sürece kopyalamamanız gerekir [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Örneğin, dosya sistemi sağlayıcısı c:\temp\abc.txt varolan c:\abc.txt dosyasını sürece kopyalamaz [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Yolunu belirtilmişse `copyPath` parametresi var ve bir kapsayıcı gösterir [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir. Bu durumda, [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) tarafından belirtilen öğe kopyalamalısınız `path` kapsayıcıya parametresi tarafından belirtilen `copyPath` parametre olarak bir alt.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) döngüsel bağlantıları ve benzeri olduğunda sonsuz özyineleme durumuna yol önlemek için sorumludur. Bir koşul yansıtmak için uygun bir sonlandırma özel durumun oluşturulması gerekir.

- Uygulamanıza [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin. Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) true döndürür [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim olarak yöntemi. Bu yöntemleri çağırma hakkında daha fazla bilgi için bkz. [öğeleri yeniden adlandırmak](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Copy-Item cmdlet'e dinamik parametreleri ekleme

Bazen `Copy-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için Windows PowerShell kapsayıcısı sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) bu işlemeye yöntemi Parametreler. Bu yöntem, öğeyi belirtilen yolda parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Copy-Item` cmdlet'i.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample04 kod örneği](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısı oluşturma

Bkz: [cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcıyı test etme

Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı, komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz. Aşağıdaki örnek çıktıda, kurgusal bir Access veritabanı kullandığını unutmayın.

1. Çalıştırma `Get-ChildItem` bir erişim veritabanındaki Müşteriler tablosunu alt öğelerin listesini almak için cmdlet'i.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Aşağıdaki çıktı görünür.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Çalıştırma `Get-ChildItem` yeniden bir tablonun verileri almak için cmdlet'i.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Aşağıdaki çıktı görünür.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Artık `Get-Item` veri tablosundaki Satır 0 olan öğeleri almak için cmdlet'i.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Aşağıdaki çıktı görünür.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Yeniden `Get-Item` satır 0 öğeler için verileri almak için.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Aşağıdaki çıktı görünür.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Artık `New-Item` var olan bir tabloya satır eklemek için cmdlet'i. `Path` Parametre satırı tam yolunu belirtir ve satır numarası belirtmelisiniz tablosundaki satırları mevcut sayısından büyük. `Type` Parametre eklemek için öğe türü belirtmek için "satır" gösterir. Son olarak, `Value` parametre satır için sütun değerlerini virgülle ayrılmış bir listesini belirtir.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Aşağıda gösterildiği gibi yeni öğe işlemi doğruluğunu doğrulayın.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Aşağıdaki çıktı görünür.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell sağlayıcınız tasarlama](./designing-your-windows-powershell-provider.md)

[Bir öğe Windows PowerShell sağlayıcısı uygulama](./creating-a-windows-powershell-item-provider.md)

[Bir gezinti Windows PowerShell sağlayıcısı uygulama](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)