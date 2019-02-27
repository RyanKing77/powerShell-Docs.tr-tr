---
title: Management OData varlıklarına ilişkilendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850193"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="34da0-102">Yönetim OData Varlıklarını İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="34da0-102">Associating Management OData Entities</span></span>

<span data-ttu-id="34da0-103">Genellikle, iki farklı yönetim OData varlıklar arasında ilişkilendirme oluşturma kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="34da0-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="34da0-104">Örneğin, bir yönetim OData hizmeti kategorilerde organize edilmiştir ürünlerinin bir katalog yönetme varlıkların ve varlıklar tanımlayan `Product` ve `Category`.</span><span class="sxs-lookup"><span data-stu-id="34da0-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="34da0-105">Bu iki varlık ilişkilendirerek, bir istemci, tek bir istek web hizmeti ile bir kategorideki tüm ürünleri hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34da0-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="34da0-106">Varlıklar arasında ilişkiler oluşturmak nasıl gösteren bir örnek, indirilebilir [ilişkilendirme örnek](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="34da0-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="34da0-107">İlişki kaynak şema dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="34da0-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="34da0-108">Aşağıdaki MOF iki varlık tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34da0-108">The following MOF defines two entities.</span></span> <span data-ttu-id="34da0-109">Bunlar arasında bir ilişkilendirme oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="34da0-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="34da0-110">`Category` Sınıfı, bu kategoriye ait ürün adlarının dizisini bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34da0-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="34da0-111">İki varlık ilişkilendirmek için bir sınıf tanımlama `Association` hizmeti için kaynak şema MOF dosyasındaki özniteliği.</span><span class="sxs-lookup"><span data-stu-id="34da0-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="34da0-112">İlişkili, adlı iki varlık sınıfı tanımlamanız gerekir `ends` ilişkilendirmenin.</span><span class="sxs-lookup"><span data-stu-id="34da0-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="34da0-113">Aşağıdaki örnek kategori ve ürün varlıkları arasındaki ilişkiyi tanımlayan bir sınıf tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="34da0-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="34da0-114">Ayrıca kategori sınıfında ürünleri özellik bildirimini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="34da0-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="34da0-115">Kullandığınız `AssociationClass` özelliğini ilişkinin bir ucu olduğunu belirtmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="34da0-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="34da0-116">Özelliği, başvuru dizelerden oluşan bir dizi yerine ayrı bir varlık olarak da tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34da0-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="34da0-117">Kullanarak bunu `ref` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="34da0-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="34da0-118">Aşağıdaki örnek, ilişkilendirme için özellik tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="34da0-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="34da0-119">Son olarak, bir özellik tanımına ekleyerek bir ilişki sonu bildirmeniz gerekir `Product` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34da0-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="34da0-120">Ya da bir dizi veya tek bir varlık için bir başvuru budur.</span><span class="sxs-lookup"><span data-stu-id="34da0-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="34da0-121">Her ürün için yalnızca bir kategoriye ait olduğu varsayılarak, tanımı şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="34da0-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="34da0-122">Gezinti özellikleri ilişkilendirme iki ucunu gösterir özellikler çağrılır.</span><span class="sxs-lookup"><span data-stu-id="34da0-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="34da0-123">Kaynak şema dosyası varlıkları ilişkilendirme adımları</span><span class="sxs-lookup"><span data-stu-id="34da0-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="34da0-124">Kullanarak bir sınıf olarak ilişki tanımlamak `Association` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="34da0-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="34da0-125">İlişki sonu, ilişkili varlıkları özelliklerini nitelemek için ilişki sınıfı anahtar sözcüğü kullanarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="34da0-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="34da0-126">Kaynak eşleme XML dosyasında ilişki oluşturma</span><span class="sxs-lookup"><span data-stu-id="34da0-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="34da0-127">Kaynak eşleme XML dosyasında bir ilişkilendirme eşlerken göz önüne almanız gereken üç farklı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="34da0-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="34da0-128">Kaynak eşleme dosyasında varlıkları ilişkilendirme belirleme</span><span class="sxs-lookup"><span data-stu-id="34da0-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="34da0-129">Gezinme özelliğini temel varsa.</span><span class="sxs-lookup"><span data-stu-id="34da0-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="34da0-130">.NET framework türü ve özellik açık hiçbir eşleme gereklidir yabancı anahtarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="34da0-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="34da0-131">Gezinti özelliği temel alınan .NET Framework türünde mevcut değilse, anahtarları ilişkilendirilmiş örneklerinin listesini alır bir cmdlet belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="34da0-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="34da0-132">Ekleyerek bunu bir `Association` öğesi altında iç içe `CmdletImplementation` tanımlayan öğeleri aşağıdaki öğe, `cmdlets` diğer CRUD komutlar için.</span><span class="sxs-lookup"><span data-stu-id="34da0-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="34da0-133">Gezinme özelliğini temel .NET Framework türü içinde yok ancak yabancı anahtarları yerine nesne örneklerini içerir ve ardından bir cmdlet (bir Windows PowerShell işlevi veya komut dosyasını yazmayarak) oluşturmanız gerekir, yabancı anahtarlar alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="34da0-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="34da0-134">Ardından bu cmdlet'i kaynak eşleme dosyası belirtin.</span><span class="sxs-lookup"><span data-stu-id="34da0-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="34da0-135">Örneğin, anahtarları almak için betiği aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="34da0-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="34da0-136">Ve XML kaynak eşleme dosyasında aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="34da0-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="34da0-137">İlişkili varlıkları almak için bir cmdlet belirtmeye ek olarak, ekleme ve koleksiyondan başvuruları kaldırmak için cmdlet'leri de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34da0-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="34da0-138">Aşağıdaki örnek ProductToCategory Ekle ve Kaldır-ProductFromCategory cmdlet'lerin mevcut olduğunu varsayar (bunlar da betik veya işlevdeki önceki örnekte olduğu gibi tanımlanabilir).</span><span class="sxs-lookup"><span data-stu-id="34da0-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="34da0-139">İlişkili varlıkları sorgulama</span><span class="sxs-lookup"><span data-stu-id="34da0-139">Querying associated entities</span></span>

<span data-ttu-id="34da0-140">İstemci, belirli bir sorgu oluşturarak bir varlıkla ilişkilendirilmiş örneklerinin bir listesini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34da0-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="34da0-141">İlişkili varlıklar için sorgular oluşturma</span><span class="sxs-lookup"><span data-stu-id="34da0-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="34da0-142">Bir istemci, ilişkili ürünlerinden almadan ayrıntılarını bir kategori isteğinde bulunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34da0-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="34da0-143">Örneğin, aşağıdaki istek ayrıntılarını alır `food` kategorisi.</span><span class="sxs-lookup"><span data-stu-id="34da0-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="34da0-144">Kategorisi ilişkili ürünleri almak için (ancak kendisi kategori, istemci ayrıntılarını istekte gezinme özelliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="34da0-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="34da0-145">Yalnızca ürünleri URL'lerini almaya `$links` istekteki niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="34da0-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="34da0-146">İstemci kategori ayrıntıları hem kendi ilişkili ürünleri kullanarak alabilirsiniz `$expand` niteleyicisi.</span><span class="sxs-lookup"><span data-stu-id="34da0-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="34da0-147">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="34da0-147">See Also</span></span>

[<span data-ttu-id="34da0-148">Management OData IIS uzantısı Web hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="34da0-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)