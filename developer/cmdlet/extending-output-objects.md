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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850963"
---
# <a name="extending-output-objects"></a>Çıkış Nesnelerini Genişletme

Türleri dosyalarını (.ps1xml) kullanarak cmdlet'ler, İşlevler ve betikleri tarafından döndürülen .NET Framework nesnelerini genişletebilirsiniz. Türler dosyaları varolan nesnelere özellikler ve yöntemler eklemenize olanak sağlayan XML tabanlı dosyalardır. Örneğin, Windows PowerShell öğeleri için birkaç mevcut .NET Framework nesneleri ekler Types.ps1xml dosyanın sağlar. Windows PowerShell yükleme dizininde bulunan Types.ps1xml dosyası (`$pshome`). Daha fazla nesneleri genişletmek veya diğer nesneleri genişletmek için kendi türleri dosyası oluşturabilirsiniz. Bir nesne türleri dosyası kullanarak genişlettiğinizde, herhangi bir nesne örneğini yeni öğelerle genişletilir.

## <a name="extending-the-systemarray-object"></a>System.Array nesne genişletme

Aşağıdaki örnek Windows PowerShell nasıl genişlettiğini gösterir [System.Array](/dotnet/api/System.Array) Types.ps1xml nesnesi. Varsayılan olarak, [System.Array](/dotnet/api/System.Array) nesneler sahip bir `Length` özelliği dizideki nesne sayısını listeler. Ancak, Windows PowerShell "uzunluğu" adı açıkça özellik tanımlamaz çünkü ekler `Count` aynı değere görüntüleyen diğer özellik `Length` özelliği. Aşağıdaki XML ekler `Count` özelliğini [System.Array](/dotnet/api/System.Array) türü.

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

Bu yeni diğer ad özelliği görmek için bir [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) aşağıdaki örnekte gösterildiği gibi bir dizi üzerinde komutu.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Komut aşağıdaki sonuçları döndürür.
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
Kullanabilirsiniz `Count` özelliği veya `Length` bir dizi içinde kaç nesneleri belirlemek için özellik. Örneğin:

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

## <a name="custom-types-files"></a>Özel türler dosyaları

Bir özel türler dosyası oluşturmak için varolan türleri dosyasını kopyalayarak başlatın. Yeni dosyayı herhangi bir ad olabilir, ancak .ps1xml dosya adı uzantısına sahip olmalıdır. Dosya kopyalama, Windows PowerShell için erişilebilir olan herhangi bir dizinini yeni bir dosya yerleştirebilirsiniz, ancak Windows PowerShell yükleme dizininde dosyaları yerleştirmek kullanışlıdır (`$pshome`) veya yükleme dizininin bir alt.

Dosyaya genişletilmiş türlerinizi eklemek, genişletmek istediğiniz her nesne için bir türler öğesi ekleyin. Aşağıdaki konular örnekleri sağlar.

- Özellikler ve özellik kümeleri ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş özellikler](./extending-properties-for-objects.md)

- Yöntem ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş yöntemleri](./defining-default-methods-for-objects.md).

- Üye kümesi ekleme hakkında daha fazla bilgi için bkz. [genişletilmiş üye ayarlar](./defining-default-member-sets-for-objects.md).

Genişletilmiş türlerinizi tanımladıktan sonra Genişletilmiş nesneler kullanılabilir hale getirmek için aşağıdaki yöntemlerden birini kullanın:

- Genişletilmiş türleri dosyanızın geçerli oturum için kullanılabilir hale getirmek için kullanın [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet'i yeni bir dosya ekleyin. Tanımlanan türleri öncelikli için türleri istiyorsanız diğer dosyaları (Types.ps1xml dosyası dahil) türleri, kullanın `PrependData` parametresinin [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet'i.
- Genişletilmiş türleri dosyanızı gelecekteki tüm oturumları için kullanılabilir hale getirmek için bir modüle türleri dosyası ekleyin, geçerli oturum dışarı aktarma veya ekleme [güncelleştirme TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) Windows PowerShell profiliniz komutu.

## <a name="signing-types-files"></a>Türleri dosyaları imzalama

XML komut dosyası blokları içerebildiklerinden kurcalanmaya karşı türleri dosyaları dijital olarak imzalanmış olması. Dijital imzalar ekleme hakkında daha fazla bilgi için bkz. [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Ayrıca bkz:

[Nesneler için varsayılan özellikleri tanımlama](./extending-properties-for-objects.md)

[Varsayılan yöntemler için nesneleri tanımlama](./defining-default-methods-for-objects.md)

[Nesneler için varsayılan üye kümesi tanımlama](./defining-default-member-sets-for-objects.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
