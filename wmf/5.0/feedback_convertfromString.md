---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085363"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Yapılandırılmış Nesneleri Dizeden Çıkarma ve Ayıklama

Bu da bazı ilave işlevler için tanıtılmaktadır `ConvertFrom-String` cmdlet:

- Uzantı metin özelliği varsayılan olarak kaldırır. -IncludeExtent parametresiyle ekleyebilirsiniz.

- Birçok algoritma hata düzeltmelerine MVP ve topluluk geri bildirimine ilişkin öğrenme.

- Şablon dosyası bir açıklama içine öğrenme algoritmasını sonuçlarını kaydetmek için yeni bir - UpdateTemplate parametre. Bu tek seferlik bir ücret (yavaş aşaması) işlem öğrenme sağlar. Dize dönüştürme kodlanmış öğrenme algoritmasını içeren bir şablon ile artık neredeyse anında çalışıyor.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Yapılandırılmış nesneleri dize içerik dışına çıkarma ve

İşbirliği ile [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), yeni bir `ConvertFrom-String` cmdlet'i eklendi.

Bu cmdlet iki modu destekler: basic ayrıştırma ve otomatik örnek temelli ayrıştırma ayrılmış.

Varsayılan olarak, sınırlandırılmış ayrıştırma boşluk konumundaki giriş böler ve elde edilen gruplara özellik adlarını atar. Sınırlayıcı özelleştirebilirsiniz:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

Cmdlet, ayrıca otomatik olarak oluşturulan göre örnek temelli ayrıştırma destekler [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) araştırma çalışması [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Başlamak için bir metin tabanlı adres defteri göz önünde bulundurun:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

Bazı örnekler, şablon olarak kullanacağınız bir dosyaya kopyalayın:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Bunu gibi bir ad verip ayıklamak istediğiniz verileriyle küme ayracı yerleştirin. Çünkü **adı** özelliği (ve ilgili diğer özellikleri) birden çok kez görünür, bir yıldız işareti kullanın (\*) bu birden çok kayıt (yerine tek bir sürü özellikleri ayıklama sonuçları göstermek için kayıt için):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

Bu örnekler, kümesinden `ConvertFrom-String` artık otomatik olarak nesne tabanlı çıkış benzer yapıya sahip giriş dosyalarından ayıklayabilir.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Ayıklanan metin üzerinde ek veri işleme yapmak için **ExtentText** özelliği kendisinden kaydı çıkarılan ham metni yakalar. Bu özellik hakkında geri bildirim sağlamak veya zorluk örnekler yazmak zorunda içeriği paylaşmak için lütfen e-posta <psdmfb@microsoft.com>.