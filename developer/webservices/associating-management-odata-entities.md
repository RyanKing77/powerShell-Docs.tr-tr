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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080756"
---
# <a name="associating-management-odata-entities"></a>Yönetim OData Varlıklarını İlişkilendirme

Genellikle, iki farklı yönetim OData varlıklar arasında ilişkilendirme oluşturma kullanışlıdır. Örneğin, bir yönetim OData hizmeti kategorilerde organize edilmiştir ürünlerinin bir katalog yönetme varlıkların ve varlıklar tanımlayan `Product` ve `Category`. Bu iki varlık ilişkilendirerek, bir istemci, tek bir istek web hizmeti ile bir kategorideki tüm ürünleri hakkında bilgi edinebilirsiniz.

Varlıklar arasında ilişkiler oluşturmak nasıl gösteren bir örnek, indirilebilir [ilişkilendirme örnek](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>İlişki kaynak şema dosyası oluşturma

Aşağıdaki MOF iki varlık tanımlar. Bunlar arasında bir ilişkilendirme oluşturacağız.

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

`Category` Sınıfı, bu kategoriye ait ürün adlarının dizisini bir özelliği tanımlar.

İki varlık ilişkilendirmek için bir sınıf tanımlama `Association` hizmeti için kaynak şema MOF dosyasındaki özniteliği. İlişkili, adlı iki varlık sınıfı tanımlamanız gerekir `ends` ilişkilendirmenin. Aşağıdaki örnek kategori ve ürün varlıkları arasındaki ilişkiyi tanımlayan bir sınıf tanımını gösterir.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Ayrıca kategori sınıfında ürünleri özellik bildirimini değiştirmeniz gerekir. Kullandığınız `AssociationClass` özelliğini ilişkinin bir ucu olduğunu belirtmek için anahtar sözcüğü. Özelliği, başvuru dizelerden oluşan bir dizi yerine ayrı bir varlık olarak da tanımlanmalıdır. Kullanarak bunu `ref` anahtar sözcüğü. Aşağıdaki örnek, ilişkilendirme için özellik tanımı gösterilmektedir.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Son olarak, bir özellik tanımına ekleyerek bir ilişki sonu bildirmeniz gerekir `Product` sınıfı. Ya da bir dizi veya tek bir varlık için bir başvuru budur. Her ürün için yalnızca bir kategoriye ait olduğu varsayılarak, tanımı şu şekilde olacaktır.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Gezinti özellikleri ilişkilendirme iki ucunu gösterir özellikler çağrılır.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Kaynak şema dosyası varlıkları ilişkilendirme adımları

- Kullanarak bir sınıf olarak ilişki tanımlamak `Association` anahtar sözcüğü.

- İlişki sonu, ilişkili varlıkları özelliklerini nitelemek için ilişki sınıfı anahtar sözcüğü kullanarak tanımlayın.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Kaynak eşleme XML dosyasında ilişki oluşturma

Kaynak eşleme XML dosyasında bir ilişkilendirme eşlerken göz önüne almanız gereken üç farklı durumlar vardır.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Kaynak eşleme dosyasında varlıkları ilişkilendirme belirleme

- Gezinme özelliğini temel varsa. .NET framework türü ve özellik açık hiçbir eşleme gereklidir yabancı anahtarlar içerir.

- Gezinti özelliği temel alınan .NET Framework türünde mevcut değilse, anahtarları ilişkilendirilmiş örneklerinin listesini alır bir cmdlet belirtmeniz gerekir. Ekleyerek bunu bir `Association` öğesi altında iç içe `CmdletImplementation` tanımlayan öğeleri aşağıdaki öğe, `cmdlets` diğer CRUD komutlar için.

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

- Gezinme özelliğini temel .NET Framework türü içinde yok ancak yabancı anahtarları yerine nesne örneklerini içerir ve ardından bir cmdlet (bir Windows PowerShell işlevi veya komut dosyasını yazmayarak) oluşturmanız gerekir, yabancı anahtarlar alınamıyor. Ardından bu cmdlet'i kaynak eşleme dosyası belirtin. Örneğin, anahtarları almak için betiği aşağıdaki gibi görünür.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Ve XML kaynak eşleme dosyasında aşağıdaki gibi görünür.

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

- İlişkili varlıkları almak için bir cmdlet belirtmeye ek olarak, ekleme ve koleksiyondan başvuruları kaldırmak için cmdlet'leri de belirtebilirsiniz. Aşağıdaki örnek ProductToCategory Ekle ve Kaldır-ProductFromCategory cmdlet'lerin mevcut olduğunu varsayar (bunlar da betik veya işlevdeki önceki örnekte olduğu gibi tanımlanabilir).

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

## <a name="querying-associated-entities"></a>İlişkili varlıkları sorgulama

İstemci, belirli bir sorgu oluşturarak bir varlıkla ilişkilendirilmiş örneklerinin bir listesini alabilirsiniz.

#### <a name="constructing-queries-for-associated-entities"></a>İlişkili varlıklar için sorgular oluşturma

- Bir istemci, ilişkili ürünlerinden almadan ayrıntılarını bir kategori isteğinde bulunabilirsiniz. Örneğin, aşağıdaki istek ayrıntılarını alır `food` kategorisi.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Kategorisi ilişkili ürünleri almak için (ancak kendisi kategori, istemci ayrıntılarını istekte gezinme özelliğini belirtir.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Yalnızca ürünleri URL'lerini almaya `$links` istekteki niteleyicisi.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- İstemci kategori ayrıntıları hem kendi ilişkili ürünleri kullanarak alabilirsiniz `$expand` niteleyicisi.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Ayrıca bkz:

[Management OData IIS uzantısı Web hizmeti oluşturma](./creating-a-management-odata-web-service.md)