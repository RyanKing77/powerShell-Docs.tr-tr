---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: Galeri, PowerShell, cmdlet, psgallery
description: Yayımcılar için yönergeler
title: PowerShell Galerisi yayımlama yönergeleri ve En Iyi uygulamalar
ms.openlocfilehash: b470dbd81e79d2a6a228b8c89f85e57c03803ede
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986507"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery yayımlama yönergeleri ve En Iyi uygulamalar

Bu konu, Microsoft ekipleri tarafından PowerShell Galerisi yayımlanan paketlerin yaygın olarak benimseneceği ve kullanıcılara yüksek bir değer sağlayarak PowerShell Galerisi bildirim verilerini nasıl işleyeceği ve büyük/veya geri bildirimlerle PowerShell Galerisi Kullanıcı sayısı.
Bu yönergeleri izleyerek yayınlanan paketlerin yüklenmesi, güvenilir olması ve daha fazla Kullanıcı çekilmesi daha yüksektir.

Aşağıda dahil olmak üzere iyi bir PowerShell Galerisi paketi oluşturan yönergeler, isteğe bağlı bildirim ayarlarının en önemli olduğu, kodunuzun ilk gözden geçirenler ve [PowerShell betiği Çözümleyicisi](https://aka.ms/psscriptanalyzer)'ndeki geri bildirimlerle geliştirilmesi, modülünüzün sürümü oluşturulmadan belgeler, neleri paylaşdıklarınızı kullanma hakkında örnekleri &.
Bu belgenin çoğu, [yüksek kalıtelı DSC kaynak modüllerini](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md)yayımlamaya yönelik yönergeleri izler.

PowerShell Galerisi bir paket yayımlamanın mekanizması için bkz. [paket oluşturma ve yayımlama](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Bu yönergelerle ilgili geri bildirimde bulunun. Geri bildiriminiz varsa, lütfen [GitHub belge deponuzdaki](https://github.com/powershell/powershell-docs/issues)sorunları açın.

## <a name="best-practices-for-publishing-packages"></a>Paketleri yayımlamak için en iyi uygulamalar

Aşağıdaki en iyi yöntemler, PowerShell Galerisi öğelerinin kullanıcılarının önemli olduğu ve nominal bir öncelik sırasıyla listelendikleridir.
Bu yönergeleri izleyen paketlerin başkaları tarafından indirilip benimseme olasılığı yüksektir.

- PSScriptAnalyzer kullanma
- Belgeleri ve örnekleri içer
- Geri bildirime yanıt verme
- Betikler yerine modüller sağlama
- Proje sitesine bağlantılar sağlama
- Paketinizi uyumlu savunma ve platformlarla etiketleyin
- Modüllerinizle testleri dahil etme
- Lisans koşullarını dahil et ve/veya bağla
- Kodunuzu imzala
- Sürüm oluşturma için [Semver](http://semver.org/) yönergelerini izleyin
- Ortak PowerShell Galerisi etiketlerinde belgelendiği gibi ortak etiketleri kullanın
- Yerel bir depo kullanarak yayınlamayı test etme
- Yayımlamak için PowerShellGet kullanın

Bunların her biri aşağıdaki bölümlerde kısaca ele alınmıştır.

## <a name="use-psscriptanalyzer"></a>PSScriptAnalyzer kullanma

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) , PowerShell kodunda çalıştırılan ücretsiz bir statik kod analizi aracıdır.
PSScriptAnalyzer, PowerShell kodunda görülen en yaygın sorunları ve genellikle sorunun nasıl düzeltileceği hakkında bir öneri belirler.
Aracın kullanımı kolaydır ve sorunları hata olarak kategorilere ayırır (ciddi, değinilmesi gerekir), uyarı (gözden geçirilmesi gereken & değinilmesi gerekir) ve bilgiler (en iyi uygulamalar için kullanıma alınıyor).
PowerShell Galerisi yayımlanan tüm paketler PSScriptAnalyzer kullanılarak taranır ve hatalar Sahibe geri bildirilir ve değinilmesi gerekir.

En iyi yöntem, ve `Invoke-ScriptAnalyzer` `-Severity` uyarı ile `-Recurse` çalıştırılır.

Sonuçları gözden geçirin ve aşağıdakileri doğrulayın:

- Tüm hatalar, belgelerinizde düzeltilir veya karşılanır
- Tüm uyarılar incelenir ve uygunsa

PowerShell Galerisi paket alan kullanıcıların, PSScriptAnalyzer çalıştırmaları ve tüm hataları ve uyarıları değerlendirmesi önemle önerilir.
PSScriptAnalyzer tarafından bildirilen bir hata olduğunu görürseniz, kullanıcılar paket sahiplerine başvurmaları çok olasıdır.
Paketinizin hata olarak işaretlenen kodu tutması için etkileyici bir neden varsa, aynı soruyu birçok kez yanıtlamak zorunda kalmamak için bu bilgileri belgelerinize ekleyin.

## <a name="include-documentation-and-examples"></a>Belgeleri ve örnekleri içer

Belgeler ve örnekler, kullanıcıların herhangi bir paylaşılan koddan yararlanabildiğinden emin olmanın en iyi yoludur.

Belgeler, PowerShell Galerisi yayımlanan paketlere dahil edilecek en yararlı şeydir.
Kullanıcılar, paketin ne olduğunu ve nasıl kullanılacağını anlamak üzere kodu okumanız durumunda, genellikle paketleri belgeler olmadan atlar.
PowerShell paketleriyle birlikte belgelerin nasıl sağlayadığının yanı sıra aşağıdakiler de dahil olmak üzere çeşitli makaleler mevcuttur:

- Yardım sağlamaya yönelik yönergeler [cmdlet yardımı yazma](https://go.microsoft.com/fwlink/?LinkID=123415)
- Herhangi bir PowerShell betiği, işlevi veya cmdlet 'i için en iyi yaklaşım olan cmdlet Yardımı oluşturma.
  Cmdlet Yardımı oluşturma hakkında daha fazla bilgi için [cmdlet yardımı yazma](https://go.microsoft.com/fwlink/?LinkID=123415)ile başlayın.
  Bir komut dosyası içinde yardım eklemek için bkz. [yorum tabanlı yardım hakkında](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Birçok modül, Markaşağı dosyaları gibi metin biçimindeki belgeleri de içerir.
  Bu özellikle GitHub 'da bir proje sitesi olduğunda yararlı olabilir; burada markın, yoğun olarak kullanılan bir biçimdir.
  En iyi uygulama, [GitHub-flavored Markaşağı](https://help.github.com/categories/writing-on-github/) kullanmaktır

Örnekler, kullanıcıların paketin nasıl kullanılacağına yönelik olduğunu gösterir.
Birçok geliştirici, bir şeyi nasıl kullanacağınızı anlamak için belgelerden önce örneklere bakmaları gerektiğini söyler.
Örneklerin en iyi türü, temel kullanımı ve sanal gerçekçi kullanım durumunu gösterir ve kodun iyi bir şekilde yorumlanma olur.
PowerShell Galerisi yayımlanan modüller için örnekler, modül kökünün altındaki bir örnekler klasöründe olmalıdır.

Örnekler S\registryresource klasörü altındaki [Psdscresource modülünde](https://www.powershellgallery.com/packages/PSDscResources) örneklere yönelik iyi bir model bulabilirsiniz.
Gösterilen her bir dosyanın en üstünde kısa bir açıklama içeren dört örnek kullanım örneği vardır.

## <a name="manage-dependencies"></a>Bağımlılıkları yönetme

Modülünüzün modül bildiriminde bağımlı olduğu modülleri belirtmek önemlidir.
Bu, son kullanıcının, bir bağımlılığı olan modüllerin doğru sürümlerini yükleme konusunda endişelenmesine gerek kalmaz.
Bağımlı modülleri belirtmek için modül bildiriminde gerekli modül alanını kullanmanız gerekir.
Bu, zaten yüklü olmadıkları müddetçe modülünüzü içeri aktarmadan önce listelenen tüm modülleri genel ortama yükler. (Örneğin, bazı modüller zaten farklı bir modül tarafından yüklenmiş olabilir.).
Ayrıca, ModuleVersion alanı yerine RequiredVersion alanı kullanılarak yüklenecek belirli bir sürüm belirtmek mümkündür. ModuleVersion kullanılırken, belirtilen en düşük sürümle birlikte en yeni sürümü yükler.
Belirli bir sürümü belirtmek için RequiredVersion alanı ne zaman kullanılmaz, gerekli modüldeki sürüm güncelleştirmelerini izlemek önemlidir.
Modülünüzün Kullanıcı deneyimini etkileyecek olan tüm önemli değişikliklerden haberdar olmak özellikle önemlidir.

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>Geri bildirime yanıt verme

Geri bildirime doğru şekilde yanıt veren paket sahipleri, topluluk tarafından yüksek bir şekilde değerlendirilir.
Yönetim geri bildirimi sağlayan kullanıcıların, bu paketin iyileştirilmesine yardımcı olmak için pakette yeterince ilgilendikleri için, yanıt vermek önemlidir.

PowerShell Galerisi için kullanılabilecek iki geri bildirim yöntemi vardır:

- Kişi sahibi: Bu, bir kullanıcının paket sahibine e-posta göndermesini sağlar. Bir paket sahibi olarak, PowerShell Galerisi paketleriyle kullanılan e-posta adresini izlemek ve oluşturulan sorunlara yanıt vermek önemlidir. Bu yöntemin dezavantajı, yalnızca kullanıcının ve sahibin iletişimi görmemesinin yanı sıra sahibi aynı soruyu birçok kez yanıtlamak zorunda kalabilir.
- Açıklamaları Paket sayfasının alt kısmında bir açıklama alanı bulunur.
  Bu sistemin avantajı, diğer kullanıcıların açıklamaları ve yanıtları görebileceği, tek bir sorunun cevaplanması gereken sürelerin sayısını azaltan bir avantajdır.
  Paket sahibi olarak, her paket için yapılan açıklamaları Izlemeniz önemle önerilir.
Bunun nasıl yapılacağını öğrenmek için [sosyal medya veya yorumlar aracılığıyla geri bildirim sağlama](../how-to/working-with-packages/social-media-feedback.md) konusuna bakın.

Geribildirime yanıt veren sahipler topluluk tarafından bir takdir edilir.
Gerekirse daha fazla bilgi istemek için raporda fırsatı kullanın, geçici bir çözüm sağlayın veya bir güncelleştirmenin bir sorunu düzeltiyi tespit edin.

Bu iletişim kanallarından birinin gözlemlediği uygunsuz davranış varsa, Galeri yöneticileri ile iletişim kurmak için PowerShell Galerisi uygunsuz kullanım özelliğini kullanın.

## <a name="modules-versus-scripts"></a>Modüller ve betiklere karşı

Bir betiğin diğer kullanıcılarla paylaşılması harika olur ve başkalarının sahip olabileceği sorunların nasıl çözüleceğini gösteren örnekler sağlar.
Sorun, PowerShell Galerisi betikler ayrı belgeler, örnekler ve testler olmadan tek dosyalardır.

PowerShell modülleri, pakete birden çok klasör ve dosya dahil edilmesini sağlayan bir klasör yapısına sahiptir.
Modül yapısı, en iyi uygulamalar olarak listediğimiz diğer paketleri de dahil etmenizi sağlayacak: cmdlet yardımı, belgeler, örnekler ve testler.
En büyük dezavantajı, bir modülün içindeki bir betiğin bir işlev olarak gösterilmesini ve kullanılmasını sağlamalıdır.
Modül oluşturma hakkında daha fazla bilgi için bkz. [Windows PowerShell modülü yazma](http://go.microsoft.com/fwlink/?LinkId=144916).

Bir Betiğin Kullanıcı için daha iyi bir deneyim sağladığını, özellikle de DSC yapılandırmalarına sahip olduğu durumlar vardır.
DSC yapılandırmaları için en iyi yöntem, yapılandırmayı belgeler, örnekler ve testleri içeren bir modül içeren bir komut dosyası olarak yayımlamaktır.
Betik RequiredModules = @ (modülün adı) kullanarak eşlik eden modülü listeler.
Bu yaklaşım herhangi bir komut dosyası ile kullanılabilir.

Diğer en iyi uygulamaları izleyen tek başına betikler, diğer kullanıcılara gerçek değer sağlar.
PowerShell Galerisi bir komut dosyası yayımlarken, açıklama tabanlı belgeler ve bir proje sitesinin bağlantısını sağlamak kesinlikle önerilir.

## <a name="provide-a-link-to-a-project-site"></a>Proje sitesi için bir bağlantı sağlayın

Proje sitesi, bir yayımcının PowerShell Galerisi paketlerinin kullanıcılarıyla doğrudan etkileşime girebildiği yerdir.
Kullanıcılar, paket hakkında daha kolay bilgi almasına izin verdiğinden, bunu sağlayan paketleri tercih eder.
PowerShell Galerisi birçok paket GitHub 'da geliştirilir, diğerleri özel bir Web varlığına sahip kuruluşlar tarafından sağlanırlar.
Bunların her biri bir proje sitesi olarak kabul edilebilir.

Bir bağlantı eklemek, bildirimin PSData bölümüne aşağıdaki gibi ProjectURI eklenerek yapılır:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

ProjectURI sağlandığında, PowerShell Galerisi paket sayfasının sol tarafındaki proje sitesinin bağlantısını içerecektir.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Paketinizi uyumlu savunma ve platformlarla etiketleyin

Hangi paketlerin ortamıyla düzgün çalışabileceğini kullanıcılara göstermek için aşağıdaki etiketleri kullanın:

- PSEdition_Desktop : Windows PowerShell ile uyumlu paketler
- PSEdition_Core : PowerShell Core ile uyumlu paketler
- Pencerelerin Windows Işletim sistemiyle uyumlu paketler
- 'Un Linux Işletim sistemleriyle uyumlu paketler
- MacOS Mac Işletim sistemiyle uyumlu paketler

Paketinizi uyumlu platformlarla etiketleyerek, arama sonuçlarının sol bölmesindeki Galeri arama filtrelerine dahil edilir. Paketinizi GitHub 'da barındırdığınızda, paketinizi etiketlediğinizde, [PowerShell Galerisi compyeteneğinin kalkan](https://img.shields.io/powershellgallery/p/:packageName.svg) 
![uyumluluk kalımızın](https://img.shields.io/powershellgallery/p/CosmosDB.svg)avantajlarından de yararlanabilirsiniz.  

## <a name="include-tests"></a>Testleri dahil et

Açık kaynak kodlu testlerin dahil edilmesi, kullanıcılar için önemlidir ve kodunuzun nasıl çalıştığı hakkında bilgi sağlar. Ayrıca, kodunuzun ortamınıza uyması için kodunuzu değiştirmeleri durumunda kullanıcıların özgün işlevselliklerinizi bozmayın olmasını sağlar.

Özellikle PowerShell için tasarlanmış olan pester test çerçevesinin avantajlarından yararlanmak için testlerin yazılması önemle tavsiye edilir.
Pester, [GitHub](https://github.com/Pester/Pester)'da, [PowerShell Galerisi](https://www.powershellgallery.com/packages/Pester/)ve Windows 10, WINDOWS Server 2016, wmf 5,0 ve WMF 5,1 ' de kullanıma sunulmuştur.

[GitHub 'Daki pester proje sitesi](https://github.com/Pester/Pester) , en iyi uygulamalara kadar olan pester testlerini yazmaya yönelik iyi belgeler içerir.

Test kapsamı için hedefler, [yüksek kaliteli kaynak modülü belgelerinde](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md),% 70 birim test kodu kapsamı önerilmesiyle çağrılır.

## <a name="include-andor-link-to-license-terms"></a>Lisans koşullarını dahil et ve/veya bağla

PowerShell Galerisi yayımlanan tüm paketlerin lisans koşullarını belirtmesi veya "sergiler" altında [kullanım koşullarına](https://www.powershellgallery.com/policies/Terms) dahil olan lisans tarafından bağlanması gerekir.
Farklı bir lisans belirtmenin en iyi yaklaşımı, PSData içinde LicenseURI kullanarak lisansın bağlantısını sağlamaktır.
Önerilen bildirim alanları konusunda bir örnek bulabilirsiniz.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Kodunuzu imzala

Kod imzalama, kullanıcılara paketi yayımlayan en yüksek düzeyde güvence sağlar ve elde ettikleri kodun kopyasının yayımcının serbest bırakıldığı şeydir.
Kod imzalama hakkında daha fazla bilgi için bkz. [kod Imzalamaya giriş](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell, iki birincil yaklaşımdan kod imzalama doğrulamasını destekler:

- Komut dosyalarını imzalama
- Katalog imzalama modül

PowerShell dosyalarını imzalama, yürütülen kodun güvenilir bir kaynak tarafından oluşturulduğundan ve değiştirilmediğinden emin olmanın iyi bir yaklaşımdır.
PowerShell betik dosyalarının imzalanmasının ayrıntıları [hakkında imzalama](/powershell/module/microsoft.powershell.core/about/about_signing) konusunda ele alınmıştır.
Genel bakışta, bir imza herhangi birine eklenebilir. Betik yüklendiğinde PowerShell 'in doğruladığı PS1 dosyası.
İmzalı betiklerin kullanımını sağlamak için [yürütme ilkesi](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlet 'Leri kullanılarak PowerShell kısıtlanabilir.

Katalog imzalama modülleri, sürüm 5,1 ' de PowerShell 'e eklenen bir özelliktir.
Modül imzalama, [Katalog cmdlet 'leri](/powershell/wmf/5.1/catalog-cmdlets) konusunda ele alınmıştır.
Genel Bakış ' da Katalog imzalama, modüldeki her dosya için bir karma değer içeren bir katalog dosyası oluşturularak ve sonra bu dosyayı imzalayarak yapılır.
PowerShellGet Publish-Module, Install-Module, Save-Module ve Update-Module cmdlet 'leri, geçerli olduğundan emin olmak için imzayı denetleyip, her bir paket için karma değerin katalogdaki ile eşleştiğinden emin olun.
Modülün önceki bir sürümü sistemde yüklüyse, Install-Module, yeni sürüm için imzalama yetkilisinin daha önce yüklenmiş olan ile eşleştiğini doğrulayacaktır.
Katalog imzalama ile birlikte çalışarak imza betiği dosyalarının yerini almaz. PowerShell, modül yükleme zamanında Katalog imzalarını doğrulamaz.

## <a name="follow-semver-guidelines-for-versioning"></a>Sürüm oluşturma için SemVer yönergelerini izleyin

[Semver](http://semver.org/) , değişikliklerin kolay bir şekilde yorumlanmasını sağlamak için bir sürümü nasıl yapılandırabileceğinizi ve değiştirileceğini açıklayan bir genel kuraldır.
Paketinizin sürümü bildirim verilerine dahil olmalıdır.

- Sürüm, 0.1.1 veya 4.11.192 ' de olduğu gibi, noktalarla ayrılmış 3 sayısal blok olarak yapılandırılmalıdır
- "0" ile başlayan sürümler, paketin henüz üretime hazırlanma olduğunu ve ilk numaranın yalnızca "0" ile başlaması gerektiğini belirtir. yalnızca bu sayı kullanılırsa
- İlk sayıdaki değişiklikler (1.9.9999 ile 2.0.0) sürümler arasındaki birincil ve son değişiklikleri belirtir
- İkinci sayıdaki değişiklikler (1,1-1,2), bir modüle yeni cmdlet 'ler ekleme gibi özellik düzeyi değişiklikleri gösterir
- Üçüncü sayı üzerinde yapılan değişiklikler, yeni parametreler, güncelleştirilmiş örnekler veya yeni testler gibi önemli olmayan değişiklikleri gösterir
- Sürümler listelenirken, PowerShell sürümleri dizeler olarak sıralar, bu nedenle 1.01.0 1.001.0 'den büyük olarak değerlendirilir

PowerShell, SemVer yayımlanmadan önce oluşturulmuştur, bu nedenle özel olarak tüm SemVer öğeleri için destek sağlar:

- Sürüm numaralarında yayın öncesi dizeleri desteklemez. Bu, bir yayımcı 1.0.0 sürümü sağladıktan sonra yeni ana sürümün önizleme sürümünü teslim etmesini istediğinde faydalıdır. Bu, PowerShell Galerisi ve PowerShellGet cmdlet 'lerinin gelecek bir sürümünde desteklenecektir.
- PowerShell ve PowerShell Galerisi, sürüm dizelerine 1, 2 ve 4 kesimle izin verir. Birçok erken modül yönergeleri izmedi ve Microsoft 'un ürün sürümleri, derleme bilgilerini 4. bir sayı bloğu olarak içerir (örneğin 5.1.14393.1066). Sürüm oluşturma açısından, bu farklılıklar yok sayılır.

## <a name="test-using-a-local-repository"></a>Yerel bir depo kullanarak test etme

PowerShell Galerisi, yayımlama işleminin test edilmesi için bir hedef olacak şekilde tasarlanmamıştır.
PowerShell Galerisi yayımlama işleminin uçtan uca bir şekilde test etmenin en iyi yolu, kendi yerel deponuzu kurmak ve kullanmaktır.
Bu, aşağıdakiler de dahil olmak üzere birkaç yolla yapılabilir:

- GitHub 'da [PS özel galeri projesini](https://github.com/PowerShell/PSPrivateGallery) kullanarak yerel bir PowerShell Galerisi örneği ayarlayın. Bu önizleme projesi, denetleyebilmeniz ve testleriniz için kullanabileceğiniz PowerShell Galerisi bir örneğini ayarlamanıza yardımcı olur.
- [Dahili bir NuGet deposu](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)ayarlayın. Bu, kurulum için daha fazla iş gerektirir, ancak daha fazla gereksinimi doğrulama, özellikle bir API anahtarı kullanımını doğrulama ve yayımlama sırasında bağımlılıkların hedefte mevcut olup olmadığı hakkında avantajına sahip olur.
- "Depo" testi olarak bir dosya paylaşma ayarlayın. Bu kolayca ayarlanabilir, ancak bir dosya paylaşımıdır, yukarıda belirtilen doğrulamalar gerçekleşmeyecektir. Bu örnekte olası bir avantaj, dosya paylaşımının (gerekli) API anahtarını denetmaması ve bu sayede PowerShell Galerisi yayımlamak için kullandığınız anahtarı kullanabilirsiniz.

Bu çözümlerden herhangi biriyle, Register-PSRepository ' yi kullanarak Publish-Module için-Repository özelliğinde kullandığınız yeni bir "depo" tanımlayın.

Test yayımlaması hakkında bir ek nokta: PowerShell Galerisi yayımladığınız herhangi bir paket, işlemler ekibinin yardımı olmadan silinemez, bu, yayımlamak istediğiniz pakete bağlı hiçbir şeyin olmadığını doğrulayacaktır.
Bu nedenle, PowerShell Galerisi test hedefi olarak desteklememiz ve bunu yapan herhangi bir yayımcıya başvuracağız.

## <a name="use-powershellget-to-publish"></a>Yayımlamak için PowerShellGet kullanın

Yayımcıların PowerShell Galerisi çalışırken Publish-Module ve Publish-SCRIPT cmdlet 'lerini kullanması önemle önerilir.
PowerShell Galerisi 'den yükleme ve yayımlama hakkında önemli ayrıntıları hatırlayıp anımsamaktan kaçınmanıza yardımcı olması için PowerShellGet oluşturulmuştur.
Bazen, yayımcılar PowerShellGet 'i atlamayı ve NuGet istemcisini ya da Publish-module yerine PackageManagement cmdlet 'lerini kullanmayı seçti.
Kolayca kaçırılmış ve çeşitli destek istekleri ile sonuçlanan birçok ayrıntı vardır.

Publish-Module veya Publish-SCRIPT ' ı kullanmanızın bir nedeni varsa lütfen bize bildirin.
PowerShellGet GitHub deposunda bir sorun yapın ve NuGet veya PackageManagement ' ı seçmenize yol açabilecek ayrıntıları sağlayın.

## <a name="recommended-workflow"></a>Önerilen iş akışı

PowerShell Galerisi yayımlanmış paketler için bulduğumuz en başarılı yaklaşım şunlardır:

- Açık kaynaklı bir proje sitesinde ilk geliştirmeyi yapın. PowerShell ekibi GitHub kullanır.
- Kodu kararlı duruma getirmek için gözden geçirenler ve [PowerShell betiği Çözümleyicisi](https://aka.ms/psscriptanalyzer) 'nden geri bildirim kullanın
- Belgelerinizi dahil edin, böylece diğerleri işinizi nasıl kullanacağınızı bilir
- Yerel bir depo kullanarak yayımlama eylemini test edin.
- PowerShell Galerisi için bir kararlı veya alfa sürümü yayımlayın, böylece belge ve bağlantı, proje sitenizin bağlantısını eklediğinizden emin olun
- Geri bildirim toplayın ve proje sitenizdeki kodu yineleyin, ardından PowerShell Galerisi kararlı güncelleştirmeler yayımlayın
- Projenize ve modülünüzü örnekler ve pester testleri ekleme
- Paketinize imza kodu eklemek istediğinize karar verin
- Projenin bir üretim ortamında kullanıma hazırlanmaya yönelik olduğunu hissettiğinizde, PowerShell Galerisi bir 1.0.0 sürümü yayımlayın
- Geri bildirim toplamaya ve kullanıcı girişine göre kodunuzda yineleme yapmaya devam edin
