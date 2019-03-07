---
title: Genel kaynak şema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849297"
---
# <a name="public-resource-schema"></a><span data-ttu-id="26b96-102">Genel Kaynak Şema</span><span class="sxs-lookup"><span data-stu-id="26b96-102">Public Resource Schema</span></span>

<span data-ttu-id="26b96-103">Management OData MOF kaynakları ve bunların özelliklerini tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="26b96-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="26b96-104">Management OData entity öğesinin özellikleri doğrudan temel alınan cmdlet'i tarafından döndürülen yönetilen türünün özelliklerini karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="26b96-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="26b96-105">Bir kaynağı tanımlama</span><span class="sxs-lookup"><span data-stu-id="26b96-105">Defining a resource</span></span>

<span data-ttu-id="26b96-106">Her kaynak bir Windows PowerShell cmdlet'i tarafından döndürülen bir nesneye karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="26b96-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="26b96-107">Publc kaynak MOF dosyasında bir sınıf bildirme tarafından bir kaynağı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="26b96-107">In the publc resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="26b96-108">Sınıfı nesne özelliklerine karşılık gelen özelliklerle oluşur.</span><span class="sxs-lookup"><span data-stu-id="26b96-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="26b96-109">Örneğin, aşağıdaki örnekte, [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) sınıfı aşağıdaki MOF tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="26b96-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="26b96-110">Bir veri türüne göre her bir özellik adı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="26b96-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="26b96-111">Bu örnekte veri türleri, .NET Framework içindeki temel CLR veri türleri karşılık gelir ancak özellikler, ayrıca diğer kaynaklar ya da her ikisini de daha sonra açıklanan karmaşık türler için başvuru olabilir.</span><span class="sxs-lookup"><span data-stu-id="26b96-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="26b96-112">`Key` Niteleyicisi gösteren bir özelliği, bir kaynak örneğini benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26b96-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="26b96-113">Kaynak birden fazla anahtar sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b96-113">A resource can have more than one key.</span></span>

<span data-ttu-id="26b96-114">`Required` Niteleyici özelliği gerekli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="26b96-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="26b96-115">Bir özellik ile etiketlenmişse `Key` niteleyicisi kabul gerekli olmasını ve `Required` niteleyicisi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="26b96-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="26b96-116">Karmaşık veri türleri</span><span class="sxs-lookup"><span data-stu-id="26b96-116">Complex data types</span></span>

<span data-ttu-id="26b96-117">Varlıkların özelliklerini karmaşık veri türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="26b96-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="26b96-118">Karmaşık veri türleri C programlama dilinde yapılar benzer diğer tür yapılan türleridir.</span><span class="sxs-lookup"><span data-stu-id="26b96-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="26b96-119">Karmaşık bir tür ile bir sınıf olarak MOF dosyasında bildirilen `ComplexType` aşağıdaki örnekteki gibi bir niteleyici.</span><span class="sxs-lookup"><span data-stu-id="26b96-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="26b96-120">Olarak bildirdiğiniz bir varlık özelliği karmaşık bir tür olarak bildirmek için bir `string` tür `EmbeddedInstance` adını içeren bir karmaşık tür niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="26b96-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="26b96-121">Aşağıdaki örnek hshows özellik bildirimini, `PswsTest_ProcessModule` türü, önceki örnekte bildirilen.</span><span class="sxs-lookup"><span data-stu-id="26b96-121">The following example hshows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="26b96-122">Varlıkları ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="26b96-122">Associating entities</span></span>

<span data-ttu-id="26b96-123">İki varlık ilişkisi ve AssocationClass niteleyicileri kullanarak ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b96-123">You can associate two entities by using the Association and AssocationClass qualifiers.</span></span> <span data-ttu-id="26b96-124">Daha fazla bilgi için [Yönetimi OData varlıkları ilişkilendirme](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="26b96-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="26b96-125">Türetilmiş türler</span><span class="sxs-lookup"><span data-stu-id="26b96-125">Derived types</span></span>

<span data-ttu-id="26b96-126">Bir tür, başka türden türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b96-126">You can derive a type from another type.</span></span> <span data-ttu-id="26b96-127">Türetilmiş tür açıkça türetilmiş herhangi bir özelliği yanı sıra türetilen türün tüm özellikler devralır.</span><span class="sxs-lookup"><span data-stu-id="26b96-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="26b96-128">Aşağıdaki örnek, bir tür bildiriminde kullanıldığında ve o türden türetilmiş iki tür bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="26b96-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

[Key] String ProductName;

};

Class DairyProduct : Product {

Uint16 PercentFat;
};
Class POPProduct : Product {

Boolean IsCarbonated;
};

```