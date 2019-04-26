---
title: Çıkış nesnelerini genişleterek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068173"
---
# <a name="extending-output-objects"></a><span data-ttu-id="2324b-102">Çıkış Nesnelerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="2324b-102">Extending Output Objects</span></span>

<span data-ttu-id="2324b-103">Türleri dosyalarını (.ps1xml) kullanarak cmdlet'ler, İşlevler ve betikleri tarafından döndürülen .NET Framework nesnelerini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2324b-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="2324b-104">Türler dosyaları varolan nesnelere özellikler ve yöntemler eklemenize olanak sağlayan XML tabanlı dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="2324b-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="2324b-105">Örneğin, Windows PowerShell öğeleri için birkaç mevcut .NET Framework nesneleri ekler Types.ps1xml dosyanın sağlar.</span><span class="sxs-lookup"><span data-stu-id="2324b-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="2324b-106">Windows PowerShell yükleme dizininde bulunan Types.ps1xml dosyası (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="2324b-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="2324b-107">Daha fazla nesneleri genişletmek veya diğer nesneleri genişletmek için kendi türleri dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2324b-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="2324b-108">Bir nesne türleri dosyası kullanarak genişlettiğinizde, herhangi bir nesne örneğini yeni öğelerle genişletilir.</span><span class="sxs-lookup"><span data-stu-id="2324b-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="2324b-109">System.Array nesne genişletme</span><span class="sxs-lookup"><span data-stu-id="2324b-109">Extending the System.Array Object</span></span>

<span data-ttu-id="2324b-110">Aşağıdaki örnek Windows PowerShell nasıl genişlettiğini gösterir [System.Array](/dotnet/api/System.Array) Types.ps1xml nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2324b-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="2324b-111">Varsayılan olarak, [System.Array](/dotnet/api/System.Array) nesneler sahip bir `Length` özelliği dizideki nesne sayısını listeler.</span><span class="sxs-lookup"><span data-stu-id="2324b-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="2324b-112">Ancak, Windows PowerShell "uzunluğu" adı açıkça özellik tanımlamaz çünkü ekler `Count` aynı değere görüntüleyen diğer özellik `Length` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2324b-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="2324b-113">Aşağıdaki XML ekler `Count` özelliğini [System.Array](/dotnet/api/System.Array) türü.</span><span class="sxs-lookup"><span data-stu-id="2324b-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

<span data-ttu-id="2324b-114">Bu yeni diğer ad özelliği görmek için bir [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) aşağıdaki örnekte gösterildiği gibi bir dizi üzerinde komutu.</span><span class="sxs-lookup"><span data-stu-id="2324b-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="2324b-115">Komut aşağıdaki sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2324b-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="2324b-116">Kullanabilirsiniz `Count` özelliği veya `Length` bir dizi içinde kaç nesneleri belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="2324b-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="2324b-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2324b-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="2324b-118">Özel türler dosyaları</span><span class="sxs-lookup"><span data-stu-id="2324b-118">Custom Types Files</span></span>

<span data-ttu-id="2324b-119">Bir özel türler dosyası oluşturmak için varolan türleri dosyasını kopyalayarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="2324b-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="2324b-120">Yeni dosyayı herhangi bir ad olabilir, ancak .ps1xml dosya adı uzantısına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2324b-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="2324b-121">Dosya kopyalama, Windows PowerShell için erişilebilir olan herhangi bir dizinini yeni bir dosya yerleştirebilirsiniz, ancak Windows PowerShell yükleme dizininde dosyaları yerleştirmek kullanışlıdır (`$pshome`) veya yükleme dizininin bir alt.</span><span class="sxs-lookup"><span data-stu-id="2324b-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="2324b-122">Dosyaya genişletilmiş türlerinizi eklemek, genişletmek istediğiniz her nesne için bir türler öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2324b-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="2324b-123">Aşağıdaki konular örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2324b-123">The following topics provide examples.</span></span>

- <span data-ttu-id="2324b-124">Özellikler ve özellik kümeleri ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş özellikler](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="2324b-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="2324b-125">Yöntem ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş yöntemleri](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="2324b-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="2324b-126">Üye kümesi ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş üye ayarlar](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="2324b-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="2324b-127">Genişletilmiş türlerinizi tanımladıktan sonra Genişletilmiş nesneler kullanılabilir hale getirmek için aşağıdaki yöntemlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2324b-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="2324b-128">Genişletilmiş türleri dosyanızın geçerli oturum için kullanılabilir hale getirmek için kullanın [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet'i yeni bir dosya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2324b-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="2324b-129">Tanımlanan türleri öncelikli için türleri istiyorsanız diğer dosyaları (Types.ps1xml dosyası dahil) türleri, kullanın `PrependData` parametresinin [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="2324b-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="2324b-130">Genişletilmiş türleri dosyanızı gelecekteki tüm oturumları için kullanılabilir hale getirmek için bir modüle türleri dosyası ekleyin, geçerli oturum dışarı aktarma veya ekleme [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Windows PowerShell profiliniz komutu.</span><span class="sxs-lookup"><span data-stu-id="2324b-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="2324b-131">Türleri dosyaları imzalama</span><span class="sxs-lookup"><span data-stu-id="2324b-131">Signing Types Files</span></span>

<span data-ttu-id="2324b-132">XML komut dosyası blokları içerebildiklerinden kurcalanmaya karşı türleri dosyaları dijital olarak imzalanmış olması.</span><span class="sxs-lookup"><span data-stu-id="2324b-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="2324b-133">Dijital imzalar ekleme hakkında daha fazla bilgi için bkz. [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="2324b-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="2324b-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2324b-134">See Also</span></span>

[<span data-ttu-id="2324b-135">Nesneler için varsayılan özellikleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2324b-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="2324b-136">Varsayılan yöntemler için nesneleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2324b-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="2324b-137">Nesneler için varsayılan üye kümesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="2324b-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="2324b-138">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="2324b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
