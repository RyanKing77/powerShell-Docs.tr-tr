---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
description: Yayımcılar için yönergeler
title: PowerShell Galerisi kılavuzları ve en iyi uygulamaları yayımlama
ms.openlocfilehash: d2af1241cea69fb879da275cc024e270356e522d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery kılavuzları ve en iyi uygulamaları yayımlama

Bu konuda Microsoft ekipleri tarafından PowerShell Galerisi yayımlanan öğeleri geniş ölçüde benimsenmesi ve PowerShell Galerisi bildirim verileri nasıl işler ve çok sayıda görüşleri dayalı kullanıcılara yüksek bir değer sağlayın sağlamak için kullanılan önerilen adımları açıklanmaktadır PowerShell Galerisi kullanıcıları.
Bu yönergeleri izleyerek yayımlanan öğeler güvenilir, yüklenecek, büyük olasılıkla ve daha fazla kullanıcı çekebilir.

Aşağıda bulunan isteğe bağlı bildirim ayarları en önemli olan ilk gözden geçirenler görüşleri ile kodunuzu iyileştirme iyi bir PowerShell galeri öğesi kılan için yönergelerdir ve [Powershell komut dosyası Çözümleyicisi](https://aka.ms/psscriptanalyzer), sürüm oluşturma Modül, belgeleri, testleri ve örnekler için paylaşılan kullanma.
Bu belge çoğunu yayımlama yönelik yönergeleri izleyen [yüksek kaliteli DSC kaynakları modüllerinin](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Öğe için PowerShell Galerisi yayımlama mekanizması için bkz: [oluşturma ve öğe yayımlama](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item).

Bu yönergeleri geribildirim Hoş Geldiniz. Görüş bildirmek isterseniz, lütfen sorunları açın bizim [Github belgeleri deposu](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Öğelerini yayımlama için en iyi uygulamalar

Aşağıdaki en iyi yöntemleri ne önemlidir PowerShell galeri öğeleri kullanıcılarının söyleyin olan ve nominal öncelik sırasına göre listelenmiştir.
Bu yönergelere öğeleri indirilir ve başkaları tarafından benimsenen daha olasıdır.

- PSScriptAnalyzer kullanın
- Belgeler ve örnekler dahil
- Geri bildirim için yanıt
- Komut dosyaları yerine modülleri sağlar
- Proje sitesi için bağlantılar sağlar
- Modüllerinizi testleriyle içerir
- İçerir ve/veya lisans koşullarını bağlantı
- Kodunuzu oturum
- İzleyin [SemVer](http://semver.org/) sürüm oluşturma için yönergeler
- Ortak PowerShell Galerisi etiketlerinde belirtildiği gibi ortak etiketleri kullanma
- Yerel deposu kullanarak test yayımlama

Bunların her biri kısaca aşağıdaki bölümlerde ele alınmıştır.

## <a name="use-psscriptanalyzer"></a>PSScriptAnalyzer kullanın

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) PowerShell kodu üzerinde çalıştığı bir ücretsiz statik kod çözümleme aracıdır.
PSScriptAnalyzer PowerShell kodu ve genellikle sorun gidermeye yönelik bir öneri görülen en sık karşılaşılan sorunları tanımlar.
Aracın kullanımı kolaydır ve sorunları hata olarak kategorilere ayıran (önemli, ele alınması gereken), uyarı (gözden geçirilmesi gereken & ilgilenilmesi gerekir) ve bilgiler (değer için en iyi uygulamaları kullanıma).
PowerShell Galerisi yayımlanan tüm öğeleri öğesi PSScriptAnalyzer kullanarak taranacak ve hataları sahibine geri bildirilir ve ele alınması gereken.

Çalıştırmak için en iyi uygulamadır `Invoke-ScriptAnalyzer` ile `-Recurse` ve `-Severity` uyarı.

Sonuçları gözden geçirin ve emin olun:

- Tüm hatalar düzeltildi veya belgelerinizde ele
- Tüm Uyarıları gözden ve uygunsa ele

PowerShell Galerisi'nden öğe elde kullanıcılar PSScriptAnalyzer çalıştırın ve tüm hataları ve Uyarıları değerlendirmek için önemle önerilir.
Kullanıcılar, büyük olasılıkla PSScriptAnalyzer tarafından raporlanan bir hata olduğunu görürseniz öğesi sahiplerinin başvurun.
Hata olarak işaretlenmiş kod tutmak, öğe için ilgi çekici bir neden varsa, bu bilgileri birçok kez aynı soruyu yanıtlamak zorunda kalmamak için belgelerine ekleyin.

## <a name="include-documentation-and-examples"></a>Belgeler ve örnekler dahil

Belgeler ve örnekler kullanıcıların herhangi bir paylaşılan kod yararlanabilir emin olmak için en iyi yoludur.

Belgeleri, PowerShell Galerisi yayımlanan öğeleri dahil etmek için en yararlı bir şeydir.
Öğe nedir ve nasıl kullanılacağını anlamak için kodu okumak için alternatif olarak kullanıcıların belgeleri olmadan öğe genellikle atlayacaktır.
MSDN kullanılabilir belgeleri de dahil olmak üzere PowerShell öğelerle sağlamak nasıl çeşitli makaleler vardır:

- Yardım sağlama yönergeleri olan [nasıl Cmdlet Yardım yazma](https://go.microsoft.com/fwlink/?LinkID=123415)
- Cmdlet Yardım oluşturma, herhangi bir PowerShell komut dosyası, işlevini veya cmdlet'ini için en iyi yaklaşımı olduğu.
  Cmdlet Yardım oluşturma hakkında daha fazla bilgi için başlayın [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415) MSDN Kitaplığı'nda.
  Bir komut dosyası içinde Yardım eklemek için bkz: [hakkında açıklama tabanlı Yardım](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
- Birçok modül belgelerine MarkDown dosyaları gibi metin biçiminde de içerir.
  Markdown yoğun olarak kullanılan bir biçimde olduğu Github'da proje sitesi olduğunda bu özellikle yararlı olabilir.
  Kullanmak için en iyi uygulamadır [Github özellikli Markdown](https://help.github.com/categories/writing-on-github/)

Örnekler nasıl öğesi kullanılması amaçlanmıştır kullanıcıları göster.
Çoğu geliştirici belgeleri nasıl bir şey kullanılacağını anlamak için önce örnekler, Ara söyleyin.
En iyi örnekleri Göster temel kullanım, artı benzetimli gerçekçi kullanım örneği ve kod iyi açıklamalı türüdür.
Örnekler için PowerShell Galerisi yayımlanmış modül için modülü kökü altındaki bir örnekler klasöründe olması gerekir.

Örnekler için iyi bir desen bulunabilir [PSDscResource Modülü](https://www.powershellgallery.com/packages/PSDscResources) Examples\RegistryResource klasörü altında.
Ne gösterilen bu belgelerin her dosyanın üst kısa bir açıklama ile dört örnek kullanım durumları vardır.

## <a name="respond-to-feedback"></a>Geri bildirim için yanıt

Düzgün bir şekilde geri bildirime yanıt öğesi sahiplerine topluluk tarafından yüksek değerli.
Öğesi, geliştirmeye yardımcı olmak denemek için yeterince ilgi olarak yapıcı görüş kullanıcılar, yanıtlamak önemlidir.

PowerShell galerisinde iki geri bildirim yöntemleri vardır:

- Kişi sahibi: Bu sahibi öğesi görüntülemenize için bir e-posta göndermek bir kullanıcı sağlar. Bir öğe sahibi olarak PowerShell Galerisi öğeleriyle kullanılan e-posta adresi izlemek ve ortaya sorunları yanıt önemlidir. Bu yöntem bir dezavantajı sahibi birçok kez aynı soruyu yanıtlamak zorunda kalabilirsiniz şekilde yalnızca kullanıcı ve sahip herhangi bir zamanda iletişimi görecek olmasıdır.
- Açıklama: öğe sayfasının en altında bir yorum alanıdır.
  Bu sisteme avantajı, diğer kullanıcıların yorumlar ve yanıtları, tek bir soru yanıtlanması gereken sayısını azaltır görebileceği ' dir.
  Bir öğe sahibi olarak, her öğe için yorumların izleyin kesinlikle önerilir.
Bkz: [sosyal medya veya açıklamalar aracılığıyla geribildirim sağlama](../how-to/working-with-items/social-media-feedback.md) nasıl hakkında ayrıntılı bilgi için.

Geri bildirim için constructively yanıt sahiplerine topluluk tarafından takdir.
Bir güncelleştirme bir sorunu giderir belirlemek veya raporda fırsatı kullanın gerekirse daha fazla bilgi istemek için geçici bir çözüm sağlar.

Bu iletişim kanalları birinden gözlenen uygunsuz davranışı varsa, Galeri yöneticilerle iletişim için PowerShell Galerisi rapor kötüye özelliğini kullanın.

## <a name="modules-versus-scripts"></a>Komut dosyaları ve modüller

Bir komut dosyası diğer kullanıcılarla paylaşımını harikadır ve diğerleri sahip olabilir sorunları nasıl çözeceğinizi örnekleriyle sağlar.
PowerShell galerisinde komut ayrı bir belge, örnekler ve testleri olmadan tek dosyaları içeren konudur.

PowerShell modülleri birden çok paketiyle dahil edilecek dosya ve klasörleri izin veren bir klasör yapısına sahip.
Modül yapısı sağlar biz listesinde en iyi yöntemler diğer öğeler de dahil olmak üzere: cmdlet Yardım, belgeler, örnekler ve testleri.
En büyük dezavantajı, bir komut dosyası bir modül içinde kullanıma sunulan ve bir işlevi olarak kullanılması gerekir, ' dir.
Bir modül oluşturma hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](http://go.microsoft.com/fwlink/?LinkId=144916).

Bazı durumlarda, bir komut dosyası özellikle DSC yapılandırmaları olan bir kullanıcı için daha iyi bir deneyim sağlar.
DSC yapılandırmaları için en iyi uygulama olarak bir komut dosyası belgeleri, örnekler ve testleri içeren bir eşlik eden modülüyle yapılandırma yayımlamaktır.
Betik RequiredModules kullanarak eşlik eden modülü listeleri = @(modül adı).
Bu yaklaşım, komut dosyaları ile kullanılabilir.

Diğer en iyi uygulamaları izleyerek tek başına komut dosyaları, diğer kullanıcılara gerçek değer girin.
Açıklama tabanlı belge ve proje siteye bir bağlantı bir komut dosyası için PowerShell Galerisi yayımlarken kesinlikle önerilir sağlanması.

## <a name="provide-a-link-to-a-project-site"></a>Proje sitesi için bir bağlantı sağlayın

Burada bir yayımcı doğrudan kendi PowerShell galeri öğeleri kullanıcılarla etkileşim kurabilen bir proje sitesidir.
Bu öğe daha kolay hakkında bilgi almak izin verdiği ölçüde kullanıcı bunu sağlamak öğeleri tercih eder.
PowerShell galerisinde birçok öğeleri Github'da geliştirilir, diğerleri adanmış web varlığı olan kuruluşlar tarafından sağlanır.
Bunların her biri bir proje sitesi kabul edilebilir.

Bağlantı ekleme ProjectURI bildirim PSData bölümünde aşağıdaki gibi ekleyerek yapılır:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Bir ProjectURI sağlandığında, PowerShell Galerisi öğesi sayfanın sol tarafında projeye siteye bir bağlantı içerir.

## <a name="include-tests"></a>Sınamalar içerir

Açık kaynak kodu ile testleri de dahil olmak üzere, neleri doğrulamak ve kodunuzu nasıl çalıştığı hakkında bilgi sağlar hakkında güvence verir olarak kullanıcılar için önemlidir. Kodunuzu ortamlarına uyacak şekilde değiştirirseniz, bunlar, özgün işlevselliği bozmadığını emin olmak kullanıcılara izin verir.

Testleri PowerShell için özellikle tasarlanmış Pester test çerçevesinden yararlanamazsınız yazılması önerilir.
Pester kullanılabilir [GitHub](https://github.com/Pester/Pester), [PowerShell Galerisi](https://www.powershellgallery.com/packages/Pester/)ve Windows 10, Windows Server 2016, WMF 5.0 ve WMF 5.1 birlikte gelir.

[Pester proje sitesi github'da](https://github.com/Pester/Pester) Pester testleri için en iyi yöntemler Başlarken yazma iyi belgeleri içerir.

Test kapsamı hedefleri olarak çağrıldığı [yüksek kaliteli kaynak modülünün belgelerine](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), önerilen kod kapsamı ile % 70 birim testi.

## <a name="include-andor-link-to-license-terms"></a>İçerir ve/veya lisans koşullarını bağlantı

PowerShell Galerisi yayımlanan tüm öğeleri Lisans Koşulları'nı belirtmeniz gerekir ya da dahil lisans tarafından bağlanması [Kullanım Koşulları'nı](https://www.powershellgallery.com/policies/Terms) "Sergi A" altında.
Farklı lisans belirtmek için en iyi yaklaşımı LicenseURI içinde PSData kullanarak lisans bağlantı sağlamaktır.
Önerilen bildirim alanları konusunda bir örnek bulabilirsiniz.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Kodunuzu oturum

Kod kopyası bunlar elde tam ne yayımcı serbest olduğundan ve kod imzalama en üst düzeye kimin öğesi yayımlanan güvence kullanıcılarla sağlar.
Kod genellikle imzalama hakkında daha fazla bilgi için bkz: [kod imzalama giriş](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell iki birincil yaklaşım imzalama kod doğrulama destekler:

- Komut dosyalarını imzalama
- Bir modül imzalama Kataloğu

PowerShell dosyaları imzalama yürütülen kod güvenilir bir kaynak tarafından üretilen ve değiştirilmedi sağlayarak bir tanınmış yaklaşımdır.
PowerShell komut dosyalarını imzalama hakkında ayrıntıları ele [hakkında imzalama](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) konu.
Genel bakış, herhangi bir imza eklenebilir. PowerShell komut dosyası yüklendiğinde doğrulayan PS1 dosyası.
PowerShell kısıtlı kullanarak [yürütme İlkesi](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) kullanımını sağlamak için cmdlet'leri imzalanmış betikler.

Modülleri imzalama Kataloğu, PowerShell sürüm 5.1 eklenen bir özelliktir.
Bir modül imzalamak nasıl ele [katalog cmdlet'leri](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) konu.
Genel bakış, katalog imzalama modüldeki her dosya için bir karma değer içeren bir katalog dosyası oluşturma ve ardından bu dosya imzalama yapılır.
PowerShellGet yayımlama modülü, yükleme modülü, kaydetme modülü ve güncelleştirme modülü cmdlet'leri geçerli olduğundan emin olmak için imza denetleyin ve sonra her öğe için karma değer katalogda nedir eşleştiğini doğrulayın.
Sistemde modülünün önceki bir sürümünü yüklediyseniz, yükleme-module yeni sürümü için imzalama yetkilisi ne önceden yüklenmişse eşleştiğini onaylayın.
Katalog imzalama ile çalışır, ancak imzalama komut dosyalarının yerini almaz. PowerShell modülü yükleme zamanında katalog imzaları doğrulamaz.

## <a name="follow-semver-guidelines-for-versioning"></a>Sürüm oluşturma için SemVer yönergeleri izleyin

[SemVer](http://semver.org/) yapısı ve değişiklikleri kolay intepretation izin vermek için bir sürüm değiştirin açıklar ortak bir kuraldır.
Öğenizi sürümü bildirim verileri eklenmesi gerekir.

- Sürüm 3 sayısal blokları 0.1.1 veya 4.11.192 olduğu gibi dönemlere göre ayrılmış olarak yapılandırılmalıdır
- "0" ile başlayan sürümleri öğe henüz üretim hazır değil ve kullanılan tek sayı ise, ilk sayı yalnızca "0" ile başlaması gereken gösterir
- İlk sayı (1.9.9999 için 2.0.0) değişiklikleri sürümleri arasında önemli ve yeni değişiklik gösteren
- İkinci sayı (1.01 için 1.02) yapılan değişiklikler yeni cmdlet'leri modül ekleme gibi özellik düzeyinde değişiklikleri gösterir
- Yeni parametreler, güncelleştirilmiş örnekleri ya da yeni testleri gibi bölünemez değişiklikleri üçüncü sayıyı değişiklikleri gösterir
- 1.01.0 1.001.0'den büyük olarak kabul edilecek şekilde sürümleri listelerken PowerShell sürümleri dize olarak sıralayacağını

SemVer yayımlanmadan önce destek SemVer, çoğu ancak tüm öğeler için özellikle sağlar şekilde PowerShell oluşturuldu:

- Sürüm numaraları ön dizelerini desteklemez. Bir yayımcı sürümü 1.0.0 sağladıktan sonra yeni bir ana sürüm Önizleme sürümü teslim istediğinde kullanışlıdır. Bu PowerShell Galerisi ve PowerShellGet cmdlet'leri gelecekteki bir sürümde desteklenmez.
- PowerShell ve PowerShell Galerisi sürüm 1, 2 ve 4 kesimleri dizelerle izin verir. Pek çok erken modülleri yönergelerini izleyin değil ve Microsoft Ürün sürümlerden numaralarını (örneğin 5.1.14393.1066) bir 4 engelleme gibi yapı bilgileri içerir. Sürüm oluşturma açısından, bu farklılıklar göz ardı edilir.

## <a name="test-using-a-local-repository"></a>Yerel deposu kullanmadan test edin

PowerShell Galerisi yayımlama işlemini test etmek için bir hedef olacak şekilde tasarlanmamıştır.
PowerShell Galerisi yayımlama uçtan uca sürecinizin test etmek için en iyi yolu, yerel deponuza ayarlamak ve kullanmaktır.
Bu da dahil olmak üzere birkaç şekillerde yapılabilir:

- Yerel bir PowerShell Galerisi örneği kümesi kullanarak [PS Özel Galeri proje](https://github.com/PowerShell/PSPrivateGallery) github'da. Bu önizleme proje kontrol edebilirsiniz PowerShell Galerisi ve testleriniz için kullanım örneği ayarlamanıza yardımcı olur.
- Ayarlanmış bir [iç Nuget deposu](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Bu ayarlamak için daha fazla iş gerektirir, ancak özellikle bir API anahtarı ve yayımladığınızda, karşılamadığını bağımlılıkları hedef mevcut kullanımını doğrulama gereksinimlerinin birkaç daha fazla doğrulama avantajı vardır.
- Bir dosya paylaşımı test "repository" olarak ayarlayın. Bunu ayarlamak kolaydır, ancak bir dosya paylaşımı olduğuna göre yukarıda belirtilen doğrulama gerçekleşecek değil. Olası bir avantajı, dosya paylaşımı (gerekli) API anahtarı denetlemez, aynı kullanabilmeniz için anahtar PowerShell galerisinde yayımlamak için yaptığınız bu durumda olur.

Bu çözümlerden birini ile Register-PSRepository "Yayımla-Module depo özelliği kullanan yeni bir havuz", tanımlamak için kullanın.

Test yayımlama hakkında bir ek noktası: hiçbir şey yayımlamak istediğiniz öğenin bağımlı olduğunu onaylar takımın işlemleri Yardım olmadan PowerShell Galerisi yayımlama herhangi bir öğe silinemiyor.
Bu nedenle, sizi bir sınama hedefi olarak PowerShell Galerisi desteklemez ve bunu yapar herhangi bir yayımcıyı sizinle iletişim kuracaktır.

## <a name="recommended-workflow"></a>Önerilen iş akışı

PowerShell Galerisi yayımlanan öğeler için bulduk en başarılı yaklaşım şudur:

- Geliştirme ilk bir açık kaynaklı proje sitesi. Github PowerShell ekip kullanır.
- Gözden geçirenler görüşleri kullanın ve [Powershell komut dosyası Çözümleyicisi](https://aka.ms/psscriptanalyzer) kararlı durum kodu almak için
- Belgeler, diğerleri çalışmanızı kullanmayı bilmesi içerir
- Yerel deposu kullanarak yayımlama eyleme sınayın.
- Kararlı ya da alfa sürüm belgeleri ve proje sitenize bağlantı eklediğinizden emin olmak PowerShell Galerisi Yayımla
- Geri bildirimi toplama ve proje sitenizdeki kodu yinelemek sonra kararlı güncelleştirmeleri yayımlamak için PowerShell Galerisi
- Projenizi ve modülünüzün örnekler ve Pester testleri ekleme
- Kodu isteyip istemediğinize karar öğenizi oturum
- Proje bir üretim ortamında kullanıma hazır olduğunu hissettiğinizde, bir 1.0.0 yayımlama PowerShell Galerisi sürüme
- Geri bildirim toplamak ve kullanıcı girişini temel alarak kodunuzu yinelemek devam edin