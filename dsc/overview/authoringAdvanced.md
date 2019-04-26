---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: CI/CD işlem hattında DSC'ın rolünü anlama
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079854"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>CI/CD işlem hattında DSC'ın rolünü anlama

Bu makalede, yapılandırmaları ve kaynakları birleştirmek için kullanılabilen yaklaşımlardan türleri açıklanmaktadır.
Her senaryo için hedef, birden fazla yapılandırması, bir sunucu dağıtımı bitiş durumuna ulaşmak için tercih edilen zaman karmaşıklığını azaltmak için aynıdır.
Buna örnek olarak bir uygulama sahibi uygulama durumunu ve güvenlik temellerini değişiklikleri serbest merkezi bir ekip bakımını yapma gibi bir sunucu dağıtımı sonucunu merkezine katkı sağlayan birden çok takımı olacaktır.
Her yaklaşımın avantajları ve risklerinin dahil olmak üzere küçük farklar aşağıda açıklanmıştır.

![İşlem hattı](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>İşbirliğine dayalı geliştirme teknikleri türleri

Bu kavramı etkinleştirmek için yerel Configuration Manager için yerleşik iki çözümü vardır:

| Kavram | Ayrıntılı bilgi
|-|-
| Kısmi Yapılandırmalar | [Belgeleri](../pull-server/partialConfigs.md)
| Bileşik kaynaklar | [Belgeleri](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Her bir yaklaşıma etkisini anlama

Bu çözümlerden birini, bir sunucu dağıtımı sonucunu yönetmek için kullanılabilir.
Ancak, her bir yaklaşım kullanarak etkisini önemli fark yoktur.

## <a name="partial-configurations"></a>Kısmi Yapılandırmalar

Kısmi yapılandırmalar kullanırken, yerel Configuration Manager birden fazla yapılandırması bağımsız olarak yönetmek üzere yapılandırılmış.
Yapılandırmaları bağımsız olarak derlenir ve ardından düğüme atanır.
Bu, her bir yapılandırma adı ile önceden yapılandırılmış olması için LCM'yi gerektirir.

![PartialConfiguration](../images/PartialConfiguration.jpg)

İki kısmi yapılandırmaları sağlamak ya da daha, takımlar üzerinde sık iletişim veya işbirliği avantajı olmadan bir sunucunun yapılandırmasını tam denetim.

Müşteriler bu kaynak çakışmaları, yanlışlıkla geçersiz kılmalar ve varlığın true yapılandırma denetim kaybı sonuçta açabilir geri bildirim sağlanmıştır.

Ayrıca, müşteriler bu model kullanılırken, her denetimi takımlar yapılandırma değişikliklerini tam olarak bir yayın ardışık düzeni test olasılığının düşük olduğu bir geri bildirim üretimde beklenmeyen sonuçlar için önde gelen sağlanmıştır.

**Tek bir işlem hattını sunucularına tüm değişiklikleri yayın değerlendirmek için kullanılması önemlidir.**

Aşağıdaki çizimde, B takımı takım A. takım bir kısmi yapılandırmalarını serbest bırakır ardından kendi çalıştırdığında uygulanan hem yapılandırmaları olan bir sunucuda yürütülemez.
Bu modelde, yalnızca bir yetkili üretim ortamında değişiklik yapma iznine sahiptir.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Değişiklikleri Team B'den gerekli olduğunda, bir çekme isteği takım A'ın kaynak denetimi ortamı karşı gönderin.
Bir takım test otomasyonu kullanarak değişiklikleri gözden geçirin ve değişiklikler uygulamaların veya sunucu tarafından barındırılan hizmetleri hataları açmayacağını güvenle olduğunda üretime sürüm.

## <a name="composite-resources"></a>Bileşik kaynaklar

Yalnızca bir kaynak olarak paketlenmiş DSC yapılandırma bir bileşik kaynaktır.
Bileşik kaynakları kabul edecek şekilde LCM yapılandırma için özel gereksinimler yoktur.
Kaynaklar içinde yeni bir yapılandırma kullanılır ve tek bir derleme bir MOF dosyasında sonuçlanır.

![CompositeResource](../images/CompositeResource.jpg)

Bileşik kaynaklar için iki yaygın senaryo vardır.
İlk karmaşıklığı ve soyut benzersiz kavramları azaltmaktır.
İkincisi, paketlenmiş bir uygulama ekipleri tüm testleri geçtikten sonra güvenli bir şekilde üretime, yayın ardışık düzeni üzerinden dağıtmak taban çizgileri izin vermektir.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Bileşik kaynaklar hem oluşturma hem de işletimsel olgunluk oluşturulurken bir işlem hattı kullanarak işbirliği Yükselt

Zaten bileşik kaynakları fark etmeden kullanıyor olabilir.
Bir örnek **ServiceSet**.
Bu kaynak ayrı ayrı listelemek olmadan birden çok Windows hizmetlerinin durumunu yönetir.
Name özelliği, her hizmetin adını sağlamak için bir dize dizisi kabul eder.
Yapılandırma derlendiğinde MOF ServiceSet için geçirilen adlarının her biri için benzersiz bir hizmet bölümü içerecektir.

Kuruluşların "Aracısı" veya "her sunucuya yüklenmesi ara yazılımı" olabilir.
Bağımlılıklar, Kurulum ve bu araçlar ve yardımcı programlar yapılandırmasını yönetmek için en iyi cevabı buna bileşik bir kaynaktır.

Kişi veya birden çok sunucu uzanan çözümler için sorumlu ekip gereksinimlerine içeren bir yapılandırma yazar.
Ardından, yapılandırmayı bileşik kaynak belgelerde sağlanan yönergeleri kullanarak bir bileşik kaynak paketlenmesi.
Son olarak, bir dosya paylaşımı gibi bir konuma yeni bileşik kaynak yayımlanan veya burada uygulama ekipleri akışı NuGet yapılandırmalarında kullanabilir.

Yeni bir sürüm takım sürümleri her zaman kendi bileşik kaynak için modül bildirimindeki sürüm numarasını artırmanız.
Uygulama ekipleri, uygulama bağımlılıkları yönetmek için yazar yapılandırmasında bileşik kaynak içerir.
İşlem/güvenlik takımlar yeni bir sürümü, kaynak serbest bıraktığınızda, bunlar yeni bir değişiklik uygulama ekipleri bildirin.

Uygulama ekipleri, burada taban çizgisine göre tek değişiklik, üretim sürümü tetikleyebilir.
Ancak, bu uygulamaları bir hizmet kesintisi riskini önce etkisini değerlendirmek için bir fırsat sağlar.

Not - bileşik kaynaklar kullanımına ilişkin geri bildirim, değişiklik yapmadan derleme ve yeni bir MOF serbest gerektirdiğini eleştirilere eklemiştir.
Bu tasarım gereğidir.
Her yeni yapılandırma sürüm, her bir kaynağın belirli bir sürümünü statik bir başvuru içermelidir ve üretim sunucusu düğümleri ulaşmadan önce testler tarafından doğrulanmalıdır.
Test ve kaynak denetiminden değişiklikleri serbest bırakma işlemi, değişiklik küçük ancak sık toplu serbest bırakmak için güvenli bir ortam oluşturur.

Teknik incelemeyi yayın işlem hatları, çekirdek altyapıyı yönetmek için kullanma hakkında daha fazla bilgi için bkz: [Yayın işlem hattı modelini](../further-reading/whitepapers.md).
