---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e4588e8c69efb965cd33c273ad09a8bef8e9bf16
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Yapılandırılmış Nesneleri Dizeden Çıkarma ve Ayıklama
Bu aynı zamanda ConvertFrom dize cmdlet'i için bazı ek işlevler sunar:

-   Uzantı metin özelliği varsayılan olarak kaldırır. -IncludeExtent parametresiyle ekleyebilirsiniz.

-   Çok sayıda algoritma hata düzeltmeleri MVP ve topluluk geri bildirim alanından öğrenme.

-   Şablon dosyası bir açıklama içine öğrenme algoritmasını sonuçlarını kaydetmek için yeni bir - UpdateTemplate parametresi. Bu bir kerelik maliyeti (yavaş aşama) işlem öğrenme hale getirir. Dönüştürme dizesi kodlanmış öğrenme algoritmasını içeren bir şablonla şimdi neredeyse anlık çalışıyor.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Ayıklamak ve dize içeriği dışında yapılandırılmış nesneleri ayrıştırılamadı
----------------------------------------------------------

İşbirliğiyle [Microsoft Research](http://research.microsoft.com/), yeni bir **ConvertFrom dize** cmdlet eklendi.

Bu cmdlet iki modlarını destekler: basic, ayrıştırma ve örnek temelli otomatik ayrıştırma ayrılmış.

Varsayılan olarak, ayrılmış ayrıştırma boşluk konumundaki giriş böler ve sonuçta elde edilen gruplarına özellik adları atar. Sınırlayıcı özelleştirebilirsiniz:

> 1 \[C:\\temp\] &gt; &gt; "Hello World" | ConvertFrom dize | Format-Table-otomatik

P1    P2
--    --

Cmdlet ayrıca otomatik olarak oluşturulan göre örnek temelli ayrıştırma destekler [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) araştırma iş [Microsoft Research](http://research.microsoft.com).

Başlamak için bir metin tabanlı adres defteri göz önünde bulundurun:

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

Birkaç örnek, şablon olarak kullanacağınız bir dosyaya kopyalayın:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



Ayıklamak istediğiniz verilerin etrafına süslü ayraçlar bunu gibi bir ad verip yerleştirin. Çünkü **adı** özelliği (ve diğer özellikleri ilişkili) birden çok kez görüntülenir, bir yıldız işareti kullanın (\*) bu birden çok kayıt (yerine tek bir demet özelliklerinin ayıklanıyor sonuçları göstermek için kayıt):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Bu örnekler, kümesinden **ConvertFrom dize** artık otomatik olarak nesne tabanlı çıkış benzer yapıya sahip girdi dosyalarındaki ayıklayabilirsiniz.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-içerik. \\addresses.output.txt | ConvertFrom dize - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-otomatik
>
> ExtentText adı Şehir durumu
> ----------                     ----               ----     -----
> Ana Trujillo...                Ana Trujillo Redmond Washington Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Çiğdem Berglund...          Çiğdem Berglund Redmond Washington Hanna Moos...                  Hanna Moos Puyallup WA

Ek veri işleme ayıklanan metni yapmak için **ExtentText** özelliği kendisinden kaydı çıkarılan ham metni yakalar. Bu özellik üzerinde geribildirim sağlamak veya örnekler yazma zorluk sahip içeriği paylaşmak için lütfen e-posta <psdmfb@microsoft.com>.
