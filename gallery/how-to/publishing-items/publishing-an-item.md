---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Oluşturma ve bir öğe yayımlama
ms.openlocfilehash: c5027c5fb357bb187611880ba75610a8f33074e0
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522982"
---
# <a name="creating-and-publishing-an-item"></a>Oluşturma ve bir öğe yayımlama

PowerShell Galerisi yayımlama ve kararlı PowerShell modülleri, betikler ve DSC kaynakları daha geniş PowerShell kullanıcı toplulukla paylaşmak için yerdir.

Bu makalede mechanics ve bir betik veya modül hazırlamak ve PowerShell Galerisi'nde yayımlama için önemli adımlar anlatılmaktadır.
Gözden geçirmenizi önemle öneririz [yayımlama kılavuzları](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery-PublishingGuidelines) yayımladığınız öğeleri daha yaygın olarak PowerShell Galerisi kullanıcılar tarafından kabul edilecek emin olmak nasıl yapılacağını görmek için.

Bir öğe PowerShell galerisinde yayımlamak için en düşük gereksinimleri şunlardır:

- PowerShell Galerisi hesabınız ve ilişkili API anahtarı
- Öğenizi içinde gerekli meta verileri olduğundan emin olun
- Öğenizi yayımlamaya hazır olduğundan emin olmak için ön doğrulama araçları kullanın
- Publish-Module ve Publish-Script komutlarını kullanarak PowerShell Galerisi'nde öğesi yayımlama
- Sorularınız veya endişeleriniz öğeniz hakkında için yanıt verme

PowerShell Galerisi, PowerShell modülleri ve PowerShell betiklerini kabul eder.
Betikleri diyoruz, tek dosyayı ve daha büyük bir modülün parçası olan bir PowerShell Betiği demek isteriz.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell Galerisi hesabı ve API anahtarı

Bkz: [PowerShell Galerisi hesabı oluşturma](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery_creating_an_account) PowerShell Galerisi hesabınızı ayarlarken öğrenmek için.

Bir hesap oluşturduktan sonra öğeyi yayımlamak için gereken API anahtar alabilirsiniz.
Hesabıyla oturum açın, sonra kullanıcı adınızı, YAZMAÇ yerine PowerShell Galerisi sayfaların üst kısmındaki görüntülenir.
Kullanıcı adınıza tıklayarak API anahtarı nerede hesabım sayfasına gideceksiniz.

Not: API anahtarı kullanıcı adı ve parola olarak güvenli bir şekilde değerlendirilmesi gerekir.
Bu anahtar ile siz veya başka biri PowerShell Galerisi'nde olduğunuz herhangi bir öğeyi güncelleştirebilirsiniz.
Yapılabilir anahtarı düzenli olarak güncelleştirilmesi önerilir, Hesabım sayfasında sıfırlama anahtarını kullanarak.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>PowerShell Galerisi'nde yayımlanmış öğeler için gerekli meta veriler

PowerShell Galerisi, Galeri kullanıcılara komut veya modül bildiriminde bulunan meta verileri alanlarından alınan bilgi sağlar.
PowerShell Galerisi yayına öğeleri oluşturmak veya küçük bir öğe bildiriminde sağlanan bilgi gereksinimleri vardır.
Öğe meta verileri bölümünü gözden geçirmeniz önemle öneririz [yayımlama kılavuzları](https://msdn.microsoft.com/powershell/gallery/psgallery/psgallery-PublishingGuidelines) öğelerinizle kullanıcıları için en iyi bilgileri sağlama hakkında bilgi edinmek için.

[Yeni ModuleManifest](https://msdn.microsoft.com/powershell/gallery/psget/module/ModuleManifest-Reference) ve [yeni ScriptFileInfo](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlet'leri oluşturacaktır bildirim şablonu, bildirim tüm öğeler için yer tutucu ile.

Hem bildirimlerinin yayımlama için önemli olan iki bölümü vardır, birincil anahtar verileri ve PSData PrivateData PowerShell modül bildirimindeki birincil anahtar veri PrivateData bölümün dışında her şeyi alanıdır.
Birincil bir anahtar kümesini kullanmak PowerShell sürümünde bağlı ve tanımsız desteklenmez.
PrivateData, PowerShell Galerisi'nde belirli öğeleri PSData böylece yeni anahtarları eklenmesini destekler.


Öğe PowerShell galerisinde yayımlamak için doldurmak en önemli olan bildirim öğeler şunlardır:

- Komut veya modül adı - bu adlarından çizilir. Bir komut dosyası PS1 veya. Bir modül için PSD1.
- Sürüm - bu gerekli bir birincil anahtar, biçimi (en iyi yöntemler için ayrıntılara bakın) SemVer yönergeleri izlemelidir
- Yazar - bu gerekli bir birincil anahtar ve öğeyle ilişkilendirilecek adı içeriyor (aşağıda yazarlar ve sahipleri, bakın)
- Açıklama - budur bu öğeyi yapar ve kullanım gereksinimlerini kısaca açıklamak için gereken birincil bir anahtar kullanılan
- ProjectURI - bu önerilir URI, Github deposuna bağlantı sağlayan PSData veya benzer konumunda geliştirmenizi öğesi üzerinde yaptığınız bir alandır

Yazarlar ve PowerShell sahipleri galeri öğeleri, ilgili kavramlardır, ancak her zaman eşleşmiyor.
Öğe sahipleriyle öğesi korumak için izne sahip bir PowerShell Galerisi hesaplarıyla kullanıcılardır. Herhangi bir öğeyi güncelleştirebilirsiniz fazla sahip olabilir.
Sahibi yalnızca PowerShell Galerisi'nden kullanılabilir ve öğe başka bir sistemden kopyalanırsa kaybolur.
Yazar, her zaman bir öğenin bir parçası olacak şekilde bildirim verileri, yerleşik bir dizedir.
Microsoft ürünleri öğelerinden önerilerdir:

- En az bir öğe oluşturan takım adı olan birden fazla sahibe sahip;
- Bir bilinen takım adı (örneğin, Azure SDK'sı ekibi) yazar veya Microsoft Corporation'ın sahip.


## <a name="pre-validate-your-item"></a>Öğeniz önceden doğrulanamadı

PowerShell Galerisi'nde öğeniz yayımlamadan önce kodunuzu çalıştırmak için ihtiyacınız olan birkaç araç vardır:

- [PowerShell betik Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), PowerShell Galerisi'nde olduğu
- Modüller için PowerShell parçası olan Test ModuleManifest
- PowerShell Get ile sunulan Test ScriptFileInfo betikleri için

[PowerShell betik Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) kodunuzu emin olmak için tarama yapmadan bir statik kod analizi aracı karşılayan kodlama yönergeleri temel PowerShell olduğu. Bu araç, kodunuzdaki yaygın ve kritik sorunları tanımlayacak ve öğeniz yayımlamaya hazır yardımcı olmak için düzenli olarak geliştirme sırasında çalıştırılmalıdır.
PowerShell betik Çözümleyicisi, hatalar, uyarı ve bilgi tanımlanan sorunların listesini sağlar.
PowerShell Galerisi'nde yayımlamadan önce tüm hataları ele alınması gerekir. Çoğu ilgilenilmesi gerekir ve Uyarıları gözden geçirilmesi gerekir.
PowerShell betik Çözümleyicisi bir öğe yayımlanmış veya güncelleştirilmiş PowerShell Galerisi'nde her zaman çalışır.
Galeri operasyon ekibinin bulunan hatalarını gidermek için öğe sahipleriyle iletişime geçeceğiz.

PowerShell Galerisi altyapısı tarafından öğeniz bildirim bilgileri okunamadığında yayımlamak mümkün olmayacaktır.
[Test-ModuleManifest](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) Modülü yüklü olduğunda kullanılabilir olmaması neden olan yaygın sorunlar yakalar. Her modülü PowerShell Galerisi'nden yayımlamadan önce çalıştırılması gerekir.

Benzer şekilde, [Test ScriptFileInfo](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_test-scriptfileinfo) betikteki meta verileri doğrular ve Powershell galeride yayımlamadan önce her komut (yayımlanan ayrı bir modülden) çalıştırmanız gerekir.


## <a name="publishing-items"></a>Yayımlama öğeleri

Kullanmalısınız [Publish-Script](https://msdn.microsoft.com/powershell/gallery/psget/script/psget_publish-script) veya [Publish-Module](https://msdn.microsoft.com/powershell/gallery/psget/module/psget_publish-module) öğeleri PowerShell galerisinde yayımlamak için.
Bu komutlar gerektirir

- Yayımlayacağınız öğenin yolu. Bir modül, modül için adlı klasörü kullanın. Birden çok sürümünü aynı modülde içeren bir klasör belirtirseniz RequiredVersion belirtmeniz gerekir.
- Bir Nuget API anahtarı. PowerShell Galerisi hesabım sayfasında bulunan API anahtarı budur.

Böylece bunları komutta belirtmeniz gerekmez komut satırında diğer seçeneklerin çoğu yayımlamakta olduğunuz öğesi için bildirim veri olması gerekir.

Hataları önlemek için - Whatif kullanarak komutları deneyin önerilir-Verbose, yayımlamadan önce.
PowerShell galerisinde yayımlamak her zaman bu yana önemli ölçüde zaman kazandırır, öğe bildirimi bölümündeki sürüm numarasını güncelleştirmeniz gerekir.

Örnekler olacaktır: ' Publish-Module-yolu ". \MyModule" - RequiredVersion "0.0.1'e" - NugetAPIKey "GUID" - Whatif-Verbose' ' Publish-Script-yolu ".\MyScriptFile.PS1" - NugetAPIKey "GUID" - Whatif-ayrıntılı '

Çıkış dikkatle gözden geçirin ve bir hata veya uyarı görürseniz, - Whatif olmadan komutu yineleyin.

PowerShell Galerisi'nde yayımlanmış öğeler virüs taraması ve PowerShell betik Çözümleyicisi'ni kullanarak analiz edilir.
O anda ortaya çıkan sorunları yayımcıya çözümlemesi için gönderilir.

Bir öğe için PowerShell Galerisi yayımladıktan sonra öğeniz hakkında geri bildirim izlemesi gerekir.

- Olun yayımlamak için kullanılan hesap ile ilişkili e-posta adresini izleyin.
Kullanıcılar ve PowerShell Galerisi operasyon ekibinin sorunları PSSA veya virüsten koruma taraması dahil olmak üzere bu hesap aracılığıyla geri bildirim sağlar.
E-posta hesabı geçersiz ya da hesap ve uzun bir süredir çözümlenmemiş sol bildirilen önemli sorunları, öğe bırakıldı ve PowerShell Galerisi'nden açıklandığı kaldırılacak kabul edilebilir bizim [kullanım](https://www.powershellgallery.com/policies/Terms).
- Yayımladığınız her PowerShell galeri öğesi için yorumlara abone ol öneririz.
Bu, herkesin öğelerinizi PowerShell Galerisi hakkında yorumlar durumunda sağlar.
LiveFyre ile bir hesabı oluşturuluyor gerektirdiği isteğe bağlıdır.