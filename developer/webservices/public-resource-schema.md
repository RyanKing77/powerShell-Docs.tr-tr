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
# <a name="public-resource-schema"></a>Genel Kaynak Şema

Management OData MOF kaynakları ve bunların özelliklerini tanımlamak için kullanır. Management OData entity öğesinin özellikleri doğrudan temel alınan cmdlet'i tarafından döndürülen yönetilen türünün özelliklerini karşılık gelir.

## <a name="defining-a-resource"></a>Bir kaynağı tanımlama

Her kaynak bir Windows PowerShell cmdlet'i tarafından döndürülen bir nesneye karşılık gelir. Publc kaynak MOF dosyasında bir sınıf bildirme tarafından bir kaynağı tanımlayın. Sınıfı nesne özelliklerine karşılık gelen özelliklerle oluşur. Örneğin, aşağıdaki örnekte, [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) sınıfı aşağıdaki MOF tarafından temsil edilir.

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

Bir veri türüne göre her bir özellik adı gelmelidir. Bu örnekte veri türleri, .NET Framework içindeki temel CLR veri türleri karşılık gelir ancak özellikler, ayrıca diğer kaynaklar ya da her ikisini de daha sonra açıklanan karmaşık türler için başvuru olabilir.

`Key` Niteleyicisi gösteren bir özelliği, bir kaynak örneğini benzersiz şekilde tanımlamak için kullanılır. Kaynak birden fazla anahtar sağlayabilirsiniz.

`Required` Niteleyici özelliği gerekli olduğunu gösterir. Bir özellik ile etiketlenmişse `Key` niteleyicisi kabul gerekli olmasını ve `Required` niteleyicisi gerekli değildir.

### <a name="complex-data-types"></a>Karmaşık veri türleri

Varlıkların özelliklerini karmaşık veri türleri içerebilir. Karmaşık veri türleri C programlama dilinde yapılar benzer diğer tür yapılan türleridir. Karmaşık bir tür ile bir sınıf olarak MOF dosyasında bildirilen `ComplexType` aşağıdaki örnekteki gibi bir niteleyici.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Olarak bildirdiğiniz bir varlık özelliği karmaşık bir tür olarak bildirmek için bir `string` tür `EmbeddedInstance` adını içeren bir karmaşık tür niteleyicisi. Aşağıdaki örnek hshows özellik bildirimini, `PswsTest_ProcessModule` türü, önceki örnekte bildirilen.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Varlıkları ilişkilendirme

İki varlık ilişkisi ve AssocationClass niteleyicileri kullanarak ilişkilendirebilirsiniz. Daha fazla bilgi için [Yönetimi OData varlıkları ilişkilendirme](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Türetilmiş türler

Bir tür, başka türden türetebilirsiniz. Türetilmiş tür açıkça türetilmiş herhangi bir özelliği yanı sıra türetilen türün tüm özellikler devralır. Aşağıdaki örnek, bir tür bildiriminde kullanıldığında ve o türden türetilmiş iki tür bildirimi gösterir.

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