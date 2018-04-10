---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Oluşturma ve öğe yayımlama
ms.openlocfilehash: bbe9095b438e2ddb72a04055d1f05fbf20d4404a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-publishing-an-item"></a>Oluşturma ve öğe yayımlama
PowerShell Galerisi yayımlama ve daha geniş PowerShell kullanıcı topluluğuyla kararlı PowerShell modülleri, betikler ve DSC kaynakları paylaşmak için yerdir.

Bu makalede, bir komut dosyası veya modülü hazırlama ve PowerShell Galerisi yayımlama için önemli adımlar ve mekanizması kapsar.
Gözden geçirmenizi öneririz [yayımlama kılavuzları](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) yayımladığınız öğeleri daha geniş PowerShell Galerisi kullanıcılar tarafından kabul edilecek emin olmak nasıl anlamak için.

Bir öğe PowerShell galerisinde yayımlamak için en düşük gereksinimleri şunlardır:

* PowerShell Galerisi hesabınız varsa ve API anahtarını ilişkili
* Gerekli meta veriler, öğesinde olduğundan emin olun
* Öğenizi yayımlamak hazır olduğundan emin olmak için ön doğrulama araçlarını kullanın
* Öğesi Yayımla-Module ve yayımlama betik komutlarını kullanarak PowerShell Galerisi yayımlama
* Sorunuz veya endişeniz öğenizi için yanıt verme

PowerShell Galerisi PowerShell modülleri ve PowerShell betikleri kabul eder.
Biz betiklere başvurduğunuzda size bir tek dosya ve daha büyük bir modül parçası olmayan bir PowerShell Betiği anlamına gelir.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell Galerisi hesabı ve API anahtarı
Bkz: [PowerShell Galerisi hesabı oluşturma](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) nasıl PowerShell Galerisi hesabınızı kurmak.

Bir hesap oluşturduktan sonra öğeyi yayımlamak için gereken API anahtarını elde edebilirsiniz.
Hesabıyla oturum sonra kullanıcı adınızı kaydı yerine PowerShell Galerisi sayfaların üst görüntülenir.
Kullanıcı adınıza tıklayarak API anahtarını bulabileceğiniz hesabım sayfasına gideceksiniz.

Not: API anahtarını oturum açma ve parola olarak güvenli bir şekilde değerlendirilmesi gerekir.
Bu anahtarla, siz veya başkalarının, PowerShell galerisinde sahip herhangi bir öğeyi güncelleştirebilirsiniz.
Yapılabilir anahtarı düzenli olarak güncelleştirilmesi önerilir hesabım sayfanızda sıfırlama anahtarı kullanarak.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>PowerShell Galerisi yayımlanan öğeler için gerekli meta veriler

PowerShell Galerisi, komut dosyası veya modül bildiriminde dahil meta veri alanlarından çizilmiş galeri kullanıcılara bilgi sağlar.
Oluşturma veya PowerShell Galerisi yayına öğeleri değiştirme öğesi bildiriminde sağlanan bilgileri için gereksinimleri, küçük bir kümesini sahiptir.
Öğe meta verisi bölümünü gözden geçirmeniz önerilir [yayımlama kılavuzları](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) öğelerinizi ile kullanıcılara en iyi bilgi sağlamak hakkında bilgi edinmek için.

[Yeni ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) ve [yeni ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlet'leri oluşturacak bildirim şablonu, tüm bildirim öğeleri yer tutucular ile.

Hem bildirimlerinin yayımlama için önemli olan iki bölümü vardır, birincil anahtar veri ve PSData PrivateData birincil anahtar verilerini bir PowerShell modülü bildiriminde PrivateData bölüm dışında her şeyi alanıdır.
Birincil anahtarlar PowerShell sürüm kullanımda bağlıdır ve tanımsız desteklenmez.
PowerShell Galerisi belirli öğeleri PSData böylece yeni anahtarlar ekleme PrivateData destekler.


PowerShell galerisinde yayımlamak öğesi için doldurmak en önemli bildirim öğeleri şunlardır:

* Komut dosyası veya modül adı - bu adlarından çizilir. Bir komut dosyası için PS1 veya. Bir modül için PSD1.
* Sürüm - bu gerekli bir birincil anahtar, biçimi (en iyi uygulamalar için ayrıntılara bakın) SemVer yönergeleri izlemelidir
* Yazar - bu gerekli bir birincil anahtar ve öğeyle ilişkilendirilecek adı içerir (aşağıda yazarlar ve sahipleri, bakın)
* -Bu açıklamasıdır gerekli bir birincil anahtar kullanılan bu öğe ne yaptığını ve kullanım herhangi bir koşul kısaca açıklayan
* ProjectURI - bu özellikle önerilir URI Github deposuna bağlantı sağlar PSData veya öğenin geliştirmenizi yaptığınız benzer konumunda bir alandır

Yazarlar ve PowerShell Galerisi sahipleri öğeler ilgili kavramlar, ancak her zaman eşleşmiyor.
Öğesi sahiplerinin öğesi korumak için izne sahip PowerShell Galerisi hesaplarıyla kullanıcılardır. Herhangi bir öğeyi güncelleştirebilirsiniz birçok sahipleri olabilir.
Sahibi yalnızca PowerShell Galerisi'nden kullanılabilir ve öğe bir sistemden diğerine kopyalansa kaybolur.
Yazar her zaman öğesinin bir parçası olacak şekilde, bildirim verisine yerleşik olarak bulunan bir dizedir.
Microsoft ürünleri öğelerinden önerileri:

* Birden çok sahipleri, en az bir öğe üreten takım adı olması gerekir;
* İyi bilinen takım adı (örneğin, Azure SDK ekibi) yazar ya da Microsoft Corporation'ın sahip.


## <a name="pre-validate-your-item"></a>Öğenizi önceden doğrula

Öğenizi PowerShell Galerisi yayımlamadan önce kodunuzu karşı çalıştırmak için gereken birkaç araç vardır:

* [PowerShell komut dosyası Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), PowerShell galerisinde olduğu
* Modüller, PowerShell parçası olan Test ModuleManifest
* Komut dosyaları için PowerShell Get ile birlikte gelen Test ScriptFileInfo

[PowerShell komut dosyası Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) emin olmak için kodunuzu tarayarak statik kod çözümleme aracı karşılayan kodlama yönergeleri temel PowerShell olduğu. Bu araç yaygın ve kritik sorunları kodunuzda tanımlayacak ve öğenizi yayımlamak hazırlanmanıza yardımcı olmak için düzenli olarak geliştirme sırasında çalıştırmanız gerekir.
PowerShell komut dosyası Çözümleyicisi hatalar, uyarı ve bilgi tanımlanan sorunların listesini sağlar.
PowerShell Galerisi yayımlamadan önce tüm hataları ele alınması gerekir. Uyarıları gözden geçirilmesi gerekir ve çoğu ilgilenilmesi gerekir.
PowerShell komut dosyası Çözümleyicisi öğeyi yayımlanan veya PowerShell galerisinde güncelleştirilmiş her zaman çalıştırılır.
Galeri işlemler ekibinin öğesi sahiplerinin bulunan adres hataları için sizinle iletişim kuracaktır.

Öğenizi bildirim bilgileri PowerShell Galerisi altyapısı tarafından okunamadığında yayımlama mümkün olmaz.
[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) modülün yüklü olduğunda kullanılabilir olmaması için neden olacağından yaygın sorunlar yakalar. PowerShell Galerisi yayımlamadan önce her modül için çalıştırılması gerekir.

Benzer şekilde, [Test ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) bir komut dosyası meta verilerde doğrular ve Powershell Galerisi yayımlamadan önce her komut (yayımlanan ayrı bir modülden) çalıştırmanız gerekir.


## <a name="publishing-items"></a>Yayımlama öğeleri

Kullanmalısınız [Yayımla-komut dosyası](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) veya [Yayımla-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) öğeleri PowerShell galerisinde yayımlamak için.
Bu komutlar gerektirir

* Yayımlayacak öğe yolu. Bir modül için modülü için adlı klasörü kullanın. Aynı modülü birden fazla sürümünü içeren bir klasör belirtirseniz, RequiredVersion belirtmeniz gerekir.
* Bir Nuget API anahtarı. Bu, PowerShell Galerisi hesabım sayfasında bulunan API anahtarıdır.

Komutta belirtmeniz gerekmez böylece komut satırında diğer seçeneklerin çoğu yayımlama, öğesi için bildirim verilerdeki olmalıdır.

Hatalarını önlemek için - whatIf kullanarak komutları deneyin önerilir-Verbose, yayımlamadan önce.
PowerShell galerisinde yayımlamak her zaman bu yana önemli ölçüde zaman kazandırır, öğenin bildirim bölümünde sürüm numarasını güncelleştirmeniz gerekir.

Örnekler olacaktır: ' Yayımla-Module-yolu ". \MyModule" - RequiredVersion "0.0.1" - NugetAPIKey "GUID" - Whatif-ayrıntılı ' ' Yayımla-komut dosyası-yolu ".\MyScriptFile.PS1" - NugetAPIKey "GUID" - Whatif-Verbose'

Çıktı dikkatle gözden geçirin ve hiçbir hata veya uyarı görürseniz, - whatIf olmadan komutu yineleyin.

PowerShell Galerisi yayımlanan tüm öğeleri virüs taraması ve PowerShell komut dosyası Çözümleyicisi kullanarak Analiz.
O zaman ortaya çıkan sorunları geri Publisher'a çözümlemesi için gönderilir.

Bir öğe için PowerShell Galerisi yayımladıktan sonra öğenizi geribildirim izlemesi gerekir.

* Olun yayımlamak için kullanılan hesapla ilişkili e-posta adresi izleyin.
Kullanıcılar ve PowerShell Galerisi işlemler ekibinin PSSA veya virüsten koruma taraması sorunları da dahil olmak üzere bu hesap aracılığıyla geri bildirim sağlar.
E-posta hesabı geçersiz ya da hesap ve uzun bir süredir çözümlenmemiş sol ciddi sorunlar bildirildiğinde, öğeleri terk ve PowerShell Galerisi'nden açıklandığı gibi kaldırılacak kabul edilebilir bizim [Kullanım Koşulları'nı](https://www.powershellgallery.com/policies/Terms).
* Yorumlara yayımladığınız her PowerShell galeri öğesi için abone öneririz.
Bu, herkesin PowerShell Galerisi, öğelerde yorumları olursa bildirilir olanak sağlar.
Bir hesap ile LiveFyre oluşturma gerektirdiğinden bu isteğe bağlı, budur.