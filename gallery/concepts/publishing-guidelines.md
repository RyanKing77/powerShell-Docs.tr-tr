---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
description: Yayımcılar için yönergeler
title: PowerShell Galerisi kılavuzları ve en iyi uygulamaları yayımlama
ms.openlocfilehash: 1cd0140cc208949e13d23331b23a58ffc374430b
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623917"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery kılavuzları ve en iyi uygulamaları yayımlama

Bu konuda PowerShell Galerisi'nde yayımlanmış paketleri yaygın olarak benimsenen ve kullanıcılara, PowerShell Galerisi bildirim verileri nasıl işlediğini ve büyük görüşlerine dayalı yüksek değerli sağlamak emin olmak için Microsoft ekipleri tarafından kullanılan önerilen adımlar açıklanır. PowerShell Galerisi kullanıcılara sayılar.
Bu yönergeleri izleyerek yayımlanan paketleri yüklenecek, daha büyük olasılıkla güvenilir ve daha fazla kullanıcıların ilgisini çekin.

Aşağıdaki ilk gözden geçirenler geri bildirimi ile kodunuzu geliştirme isteğe bağlı bildirim ayarları en önemli olan bir iyi PowerShell Galerisi paket kılan yönergeleri içerir ve [Powershell betik Çözümleyicisi](https://aka.ms/psscriptanalyzer), sürüm oluşturma modülü, belgeler, testleri ve örnekler için paylaşılan sahip kullanma.
Bu belge çoğunu yayımlama yönergelerine uyduğundan [yüksek kalite DSC kaynak modülleri](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Mekanizması bir paket için PowerShell Galerisi yayımlama bkz [oluşturma ve bir paket yayımlama](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Bu yönergelere geri Hoş Geldiniz. Geri bildiriminiz varsa, lütfen sorunları Aç bizim [Github belge deposuna](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Paketleri yayımlama için en iyi yöntemler

Aşağıdaki en iyi ne önemlidir PowerShell galeri öğelerini kullanıcıları söyleyin misiniz ve çok düşük öncelik sırasına göre listelenir.
Aşağıdaki yönergeleri izleyin paketlerin yüklenmesini ve başkaları tarafından benimsenen çok daha yüksektir.

- PSScriptAnalyzer kullanın
- Belgeler ve örnekler dahil
- Geri bildirime yanıt
- Betikler yerine modülleri belirtin
- Proje sitesi bağlantılar sağlar
- Paketiniz uyumlu PSEdition(s) ve platformlarla etiketi
- Sınamalar, modülleri
- Dahil ve/veya lisans koşullarını bağlantı
- Kod imzalama
- İzleyin [SemVer](http://semver.org/) sürüm oluşturma için yönergeler
- Ortak PowerShell Galerisi etiketleri belgelendiği gibi ortak etiketleri kullanma
- Yerel depo kullanmaya test yayımlama
- Yayımlamak için PowerShellGet kullanma

Her birini aşağıdaki bölümlerde kısaca ele alınmaktadır.

## <a name="use-psscriptanalyzer"></a>PSScriptAnalyzer kullanın

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) PowerShell kod üzerinde çalışan bir ücretsiz statik kod analizi aracıdır.
PowerShell kodu ve genellikle bir öneri için sorunu düzeltmek için görülen yaygın sorunların çoğunu PSScriptAnalyzer tanımlar.
Araç kullanımı kolaydır ve sorunları hata olarak kategorilere ayıran (önemli, ele alınması gerekir), uyarı (gözden geçirilmesi gereken ve ilgilenilmesi gerekir) ve bilgi (değer için en iyi kullanıma).
PowerShell Galerisi'nde yayımlanmış tüm paketleri PSScriptAnalyzer kullanarak taranır ve hataları sahibine geri raporlanacak ve ele alınması gerekir.

Çalıştırmak için en iyi uygulamadır `Invoke-ScriptAnalyzer` ile `-Recurse` ve `-Severity` uyarı.

Sonuçları gözden geçirin ve emin olun:

- Tüm hatalar düzeltildi ve, belgelerinde ele
- Tüm Uyarıları gözden geçirdi ve uygunsa ele

Paketler PowerShell Galerisi'ndeki alma kullanıcılar PSScriptAnalyzer çalıştırın ve tüm hataları ve Uyarıları değerlendirmek için önerilir.
Büyük olasılıkla PSScriptAnalyzer tarafından raporlanan bir hata olduğunu görürseniz, paket sahipleriyle temas kullanıcılardır.
Paketiniz hata olarak işaretlenmiş kod tutmak için yeterli bir neden varsa, bu bilgileri birden çok kez aynı soruyu yanıtlamak zorunda kalmamak için belgelerine ekleyin.

## <a name="include-documentation-and-examples"></a>Belgeler ve örnekler dahil

Belgeler ve örnekler kullanıcıların herhangi bir paylaşılan kod yararlanabilirsiniz emin olmak için en iyi yoludur.

Belgeleri, PowerShell Galerisi'nde yayımlanmış paketleri dahil etmek için en faydalı bir şeydir.
Paket nedir ve nasıl kullanılacağını anlamak için kodu okumak için alternatif olarak kullanıcıların belgeleri olmadan paketleri genellikle atlama.
Kullanılabilir belgeler de dahil olmak üzere PowerShell paketleriyle sağlama hakkında birkaç makale vardır:

- Yardım sağlama yönergeleri alanlarındadır [cmdlet'i Yardımı yazma hakkında](https://go.microsoft.com/fwlink/?LinkID=123415)
- Cmdlet yardımına oluşturmadan, en iyi yaklaşım herhangi bir PowerShell Betiği, işlev veya cmdlet'i için olan.
  Cmdlet yardımına oluşturma hakkında daha fazla bilgi için başlayan [yazma Cmdlet Yardım nasıl](https://go.microsoft.com/fwlink/?LinkID=123415).
  Bir betik içinde Yardım eklemek için bkz [hakkında açıklama tabanlı Yardım](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Birçok modülleri belgeleri MarkDown dosyaları gibi metin biçiminde de içerir.
  Github Markdown yoğun olarak kullanılan bir biçim olduğu, proje sitesi olduğunda bu özellikle yararlı olabilir.
  Kullanmak için en iyi uygulamadır [Github özellikli Markdown](https://help.github.com/categories/writing-on-github/)

Örnekler için paketin nasıl kullanılmak kullanıcıları göster.
Birçok geliştirici belgeleri nasıl bir şey kullanılacağını anlamak için önce örnekler, Ara yazar.
En iyi örnekler show temel kullanım yanı sıra sanal gerçekçi kullanım örneği ve kod iyi açıklamalı türüdür.
PowerShell Galerisi'nde yayımlanmış olan modüller için örnekler modülü kökü altındaki örnekler klasöründe olmalıdır.

Örnekler için iyi bir düzen bulunabilir [PSDscResource Modülü](https://www.powershellgallery.com/packages/PSDscResources) Examples\RegistryResource klasörü altında.
Ne gösterilen bu belgeleri dört örnek kullanım örneklerini kısaca her dosya üst kısmındaki vardır.

## <a name="respond-to-feedback"></a>Geri bildirime yanıt

Düzgün bir şekilde geri bildirime yanıt paketi sahiplerine topluluk tarafından yüksek değerli.
Paketi, geliştirmeye yardımcı olmak denemek için yeterince ilgilenen oldukları gibi yanıt kullanıcılar, yapıcı geri bildirim sağlamak önemlidir.

PowerShell galerisinde kullanılabilir geri bildirim iki yöntem vardır:

- Sahibiyle iletişime geçin: Bu, bir kullanıcı için paket sahip bir e-posta göndermek sağlar. Bir paket sahibi olarak, PowerShell Galerisi paketlerle kullanılan e-posta adresi izleyebilir ve oluşan sorunlara yanıt önemlidir. Bu yöntem bir dezavantajı sahip birden çok kez aynı soruyu yanıtlamak zorunda yalnızca kullanıcı ve sahibi şimdiye kadar iletişim görecek olmasıdır.
- Açıklama: Paket alt kısmında bir yorum alanı sayfasıdır.
  Bu sisteme avantajı diğer kullanıcıların açıklamalar ve yanıtları herhangi tek soru yanıtlanması gereken sayısını azaltan görebilmenizdir.
  Paket sahibi olarak, her paket için açıklamalar izleyin önemle tavsiye edilir.
Bkz: [sosyal medya veya yorumlar aracılığıyla geri bildirim sağlayarak](../how-to/working-with-packages/social-media-feedback.md) bunu nasıl yapacağınız hakkında ayrıntılı bilgi için.

Topluluk tarafından constructively geri bildirime yanıt sahipleri geri bildirimlerinize.
Bir güncelleştirme bir problemi çözdüyse tanımlamak veya raporda fırsatı kullanın gerekirse daha fazla bilgi istemek için geçici bir çözüm sağlar.

Bu iletişim kanallarını birinden gözlemlenen uygunsuz davranışı varsa, Galeri yöneticilerle iletişim için PowerShell Galerisi Uygunsuz kullanım bildir özelliğini kullanın.

## <a name="modules-versus-scripts"></a>Betikleri ve modülleri

Bir betik diğer kullanıcılarla paylaşma idealdir ve diğerleri olabilir sorunları nasıl çözeceğinizi örnekleriyle sağlar.
PowerShell Galerisi betiklerde ayrı bir belge, örnekler ve testler olmadan tek dosyaların olduğunu sorunudur.

PowerShell modülleri, birden çok dosya ve klasörleri paketine dahil olmasını sağlayan bir klasör yapısına sahiptir.
Modül yapısı sağlar ki listesinde en iyi yöntemler diğer paketleri de dahil olmak üzere: cmdlet, belgeler, örnekler ve testleri yardımcı olur.
En büyük dezavantajı, bir komut dosyası bir modül içinde kullanıma sunulan ve bir işlev olarak kullanılması gerekir, ' dir.
Bir modül oluşturma hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](http://go.microsoft.com/fwlink/?LinkId=144916).

Bazı durumlarda burada bir betik özellikle DSC yapılandırmaları olan bir kullanıcı için daha iyi bir deneyim sağlar.
DSC yapılandırmaları için en iyi uygulama olarak bir komut dosyası belgeleri, örnekler ve testleri içeren bir eşlik eden modülü ile yapılandırma yayımlamaktır.
Betik RequiredModules kullanarak eşlik eden modülü listeler = @(modülünün adı).
Bu yaklaşım, tüm betiklerde olduğu kullanılabilir.

Diğer en iyi uygulamaları izleyin tek başına komut diğer kullanıcılara gerçek değeri belirtin.
Yürütmeyi açıklama tabanlı belge ve bir proje siteye bir bağlantı PowerShell Galerisi'nden bir betik yayımlarken kesinlikle önerilir.

## <a name="provide-a-link-to-a-project-site"></a>Proje sitesi için bir bağlantı sağlayın

Burada, bir yayımcı doğrudan PowerShell Galerisi paketlerini kullanıcılarla etkileşim kurabilir bir proje sitedir.
Kullanıcılar daha kolay paketi hakkında bilgi almak bunları verdiğinden bu sağlayan paketleri tercih eder.
Github'da PowerShell galerisinde birçok paketi geliştirilir, diğer bir adanmış bir web varlığı bir kuruluşlarıyla tarafından sağlanır.
Bunların her biri proje sitesi kabul edilebilir.

Bir bağlantının eklenmesi ProjectURI gibi bildirim PSData bölümünü ekleyerek gerçekleştirilir:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Bir ProjectURI sağlandığında, PowerShell Galerisi paket sayfanın sol tarafındaki proje siteye bir bağlantı bulunur.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Paketiniz uyumlu PSEdition(s) ve platformlarla etiketi

Paketleri de ortamıyla çalışır kullanıcılara göstermek için aşağıdaki etiketlerin kullanın:

- PSEdition_Desktop: Windows PowerShell ile uyumlu olan paketler
- PSEdition_Core: PowerShell Core ile uyumlu olan paketler
- Windows: Windows işletim sistemiyle uyumlu olan paketler
- Linux : Linux işletim sistemleri ile uyumlu olan paketler
- MacOS : Mac işletim sistemiyle uyumlu olan paketler

Paketiniz uyumlu platformları ile etiketleme tarafından galeri arama filtreleri sol bölmedeki arama sonuçları dahil edilir. Paketiniz etiketlediğinizde, github'da paketinizi barındırıyorsanız, ayrıca avantajlarından yararlanabilirsiniz bizim [PowerShell Galerisi uyumluluk shields](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![uyumluluk kalkan](https://img.shields.io/powershellgallery/p/CosmosDB.svg).  

## <a name="include-tests"></a>Sınamalar

Açık kaynak kod ile testler de dahil olmak üzere, neleri doğrulamak ve kodunuzun nasıl çalıştığı hakkında bilgi sağlar hakkında güvence verir olarak kullanıcılar için önemlidir. Ayrıca, kendi ortamlarında uyacak şekilde kodunuzu değiştirirseniz, bunlar, özgün işlevi bozulmaz emin olmak kullanıcıların sağlar.

PowerShell için özellikle tasarlanmış Pester test çerçevesi yararlanmak için testleri yazılması önemle tavsiye edilir.
Pester kullanılabilir [GitHub](https://github.com/Pester/Pester), [PowerShell Galerisi](https://www.powershellgallery.com/packages/Pester/)ve Windows 10, Windows Server 2016, WMF 5.0 ve WMF 5.1 birlikte gelir.

[Pester proje sitesi github'da](https://github.com/Pester/Pester) Pester testleri için en iyi Başlarken yazma iyi belgeleri içerir.

Test kapsamı hedeflerini anılmaktadır [yüksek kalite Resource modülü belgeleri](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), önerilen kod kapsamı ile % 70'in birim test.

## <a name="include-andor-link-to-license-terms"></a>Dahil ve/veya lisans koşullarını bağlantı

PowerShell Galerisi'nde yayımlanmış tüm paketler Lisans Koşulları'nı belirtmeniz gerekir veya dahil lisans bağlayıcılığını [kullanım](https://www.powershellgallery.com/policies/Terms) altında "Ek A".
Farklı bir lisans belirtmek için en iyi yaklaşım bir bağlantı içinde PSData LicenseURI kullanma lisansına sağlamaktır.
Önerilen bildirim alanları konusunda bir örnek bulabilirsiniz.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Kod imzalama

Kod imzalama güvencesi kimin yayımlanan paket için en yüksek düzeyde kullanıcılarla sağlar ve kod kopyası bunlar alma tam olarak ne yayımcı yayımlanan.
Kod genellikle imzalama hakkında daha fazla bilgi için bkz: [kod imzalama giriş](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell kod imzalama iki birincil yaklaşım doğrulama destekler:

- Komut dosyalarını imzalama
- Bir modül imzalama Kataloğu

PowerShell dosyaları imzalama yürütülen kod güvenilir bir kaynak tarafından üretilen ve değiştirilmemiş sağlamak için bir tanınmış bir yaklaşımdır.
PowerShell komut dosyalarını imzalama hakkında ayrıntılı bilgi alınmıştır [hakkında imzalama](/powershell/module/microsoft.powershell.core/about/about_signing) konu.
Genel bakış sayfasında herhangi bir imza eklenebilir. PowerShell betik yüklendiğinde doğrulayan PS1 dosyası.
PowerShell kısıtlı kullanarak [yürütme İlkesi](/powershell/module/microsoft.powershell.core/about/about_execution_policies) kullanımını sağlamak için cmdlet'leri imzalanmış betikler.

Katalog modülleri imzalama için PowerShell sürüm 5.1 eklenen bir özelliktir.
Bir modül oturum açma ele alınmıştır [katalog cmdlet'leri](/powershell/wmf/5.1/catalog-cmdlets) konu.
Genel bakış sayfasında Kataloğu imzalama modüldeki her dosya için bir karma değer içeren bir katalog dosyası oluşturma ve ardından bu dosya imzalama gerçekleştirilir.
PowerShellGet yayımlama modülü, Install-module, save-module ve güncelleştirme modülü cmdlet'lerini geçerli olduğundan emin olmak için imza denetleyin, sonra her paket için karma değer katalogda nedir eşleştiğini onaylayın.
Sistemde bir modülün önceki bir sürümünü yüklediyseniz, Install-module yeni sürüm için imzalama yetkisini ne daha önce yüklü olduğu eşleştiğini doğrulayın.
Katalog imzalama ile çalışır, ancak imzalama komut dosyalarının yerini almaz. PowerShell modülü yükleme zamanında Kataloğu imzaları doğrulamaz.

## <a name="follow-semver-guidelines-for-versioning"></a>Sürüm oluşturma için SemVer yönergeleri izleyin

[SemVer](http://semver.org/) nasıl yapılandırılacağı ve değişiklikleri kolay yorumlanması izin vermek için bir sürüm değiştirin açıklayan genel bir kuraldır.
Bildirim verileri, Paket sürümü yeniden eklenmesi gerekir.

- Sürüm 3 sayısal blokları 0.1.1 veya 4.11.192 noktayla ayrılmış olarak yapılandırılmalıdır
- "0" ile başlayan sürümleri paket henüz üretime hazır değildir ve ilk sayı yalnızca "0" ile başlamalıdır, kullanılan tek sayı olup olmadığını gösterir
- Değişiklikler, ilk sayısı (için 1.9.9999 2.0.0) sürümleri arasında önemli ve derleyicideki en güncel değişiklikler gösteriyor
- Değişiklikler, ikinci sayı (1.1 için 1.2) için yeni cmdlet'ler modül ekleme gibi özellik düzeyinde değişiklikleri gösteriyor
- Üçüncü sayıyı değişiklikleri yeni parametreler, güncelleştirilmiş örnekleri ve yeni testler gibi hataya neden olmayan değişiklikleri gösterir.
- 1.01.0 1.001.0 daha büyük olarak kabul edilecek şekilde sürümlerin listelenmesi zaman PowerShell sürümleri dize olarak sıralanır

SemVer yayımlanmadan önce PowerShell desteği SemVer, çoğu ancak tüm öğeler için özellikle sağladığı için oluşturulmuştur:

- Dizeleri yayın öncesi sürüm numaraları desteklemez. Bir yayımcı, sürüm 1.0.0 girdikten sonra yeni bir ana sürüm'in bir önizleme sürümünü sunmak istediğinde, bu yararlıdır. Bu PowerShell Galerisi ve PowerShellGet cmdlet'leri gelecekteki bir sürümde desteklenecek.
- PowerShell ve PowerShell Galerisi sürümüne dizeleriyle 1, 2 ve 4 Kesimden izin verir. Pek çok erken modülleri yönergeleri izleyin değil ve Microsoft Ürün sürümlerinden (örneğin 5.1.14393.1066) sayıda bir 4 engelleme gibi yapı bilgilerini içerir. Sürüm oluşturma açısından, bu farklılıkları göz ardı edilir.

## <a name="test-using-a-local-repository"></a>Yerel bir depoyu kullanarak test edin

PowerShell Galerisi yayımlama işlemini test etmek için bir hedef olarak tasarlanmamıştır.
PowerShell Galerisi yayımlama, uçtan uca sürecinizin test etmek için en iyi yolu, ayarlamak ve yerel deponuzu kullanmaktır.
Bu, birkaç yolla yapılabilir:

- Yerel bir PowerShell Galerisi örneği oluşturan kümesi kullanarak [PS Özel Galeri proje](https://github.com/PowerShell/PSPrivateGallery) github'da. Bu önizleme proje denetleyebileceğiniz PowerShell Galerisi ve testleriniz için kullanım örneği ayarlamanıza yardımcı olur.
- Ayarlanmış bir [iç Nuget depo](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Bunu ayarlamak için daha fazla iş gerektirir, ancak özellikle bir API anahtarı ve yayımladığınızda, alınıp alınmayacağını bağımlılıkları hedefte mevcut olduğundan doğrulama gereksinimleri birkaç daha fazla doğrulama avantajı gerekir.
- Bir dosya paylaşım test "depo" olarak ayarlayın. Bunu ayarlamak kolaydır, ancak bir dosya paylaşımı olduğundan, yukarıda belirtilen doğrulamaları yerde olmaz. Olası bir avantajı, dosya paylaşımı (gerekli) API anahtarını denetlemez, aynı kullanabilmeniz için anahtar PowerShell galerisinde yayımlamak için yaptığınız bu durumda olur.

Bu çözümlerden birini ile Register-PSRepository "Publish-Module depo özelliği kullanan yeni bir havuz", tanımlamak için kullanın.

Test yayımlama hakkında bir ek noktası: hiçbir şey yayımlamak istediğiniz paket bağımlı olduğunu onaylar operasyon ekibinin Yardım olmadan PowerShell Galerisi'nden yayımladığınız herhangi bir paket silinemez.
Bu nedenle şu PowerShell Galerisi test hedefi olarak desteklemez ve yazılabilmesine herhangi bir yayımcı bağlantı kurar.

## <a name="use-powershellget-to-publish"></a>Yayımlamak için PowerShellGet kullanma

Yayımcılar PowerShell Galerisi ile çalışırken Publish-Module ve Publish-Script cmdlet'leri kullanmanız önerilir.
PowerShellGet yükleme ve yayımlama için PowerShell Galerisi hakkında önemli ayrıntıları hatırlamak önlemek için oluşturuldu.
Bazen, yayımcılar PowerShellGet atlayın ve Publish-Module yerine NuGet istemcisi veya PackageManagement cmdlet'leri seçtiniz.
Destek isteklerini çeşitli sonuçları bir kolayca eksik ayrıntıları sayısı vardır.

Publish-Module veya Publish-Script kullanamazsınız bir neden varsa, lütfen bize bildirin.
PowerShellGet GitHub deposunda sorun kaydedebilir ve NuGet ya da PackageManagement seçmek neden ayrıntılarını sağlayın.

## <a name="recommended-workflow"></a>Önerilen iş akışı

PowerShell Galerisi'nde yayımlanmış paketleri için bulduk en başarılı yaklaşım budur:

- Geliştirme ilk bir açık kaynak proje site. PowerShell ekibi, Github kullanır.
- Gözden geçirenler geri bildirimi kullanın ve [Powershell betik Çözümleyicisi](https://aka.ms/psscriptanalyzer) kararlı durumda kodu almak için
- Belgeler, böylece başkaları çalışmanıza nasıl kullanılacağını dahil
- Yerel depo kullanmaya yayımlama eyleme test edin.
- Bir kararlı veya alfa sürümü belgeleri ve bağlantı proje sitenize eklediğinizden emin olmak PowerShell Galerisi yayımlama
- Geri bildirim toplayın ve proje sitenizde kod üzerinde yinelemek ve ardından PowerShell Galerisi'nde kararlı güncelleştirmeleri yayımlama
- Projenizi ve modülünüzde örnekler ve Pester testleri Ekle
- Kod için istediğinize karar paketinizi oturum
- Proje bir üretim ortamında kullanıma hazır olduğunu hissettiğinizde, bir 1.0.0 yayımlama sürüme PowerShell Galerisi
- Geri bildirim toplamak ve kullanıcı girişini temel alarak kodunuz üzerinde yinelemek devam edin
