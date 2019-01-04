---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Oluşturma ve bir öğe yayımlama
ms.openlocfilehash: 70696535a3bf540ff75a2dc43bca80cb1adf8f45
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012543"
---
# <a name="creating-and-publishing-an-item"></a>Oluşturma ve bir öğe yayımlama

PowerShell Galerisi yayımlama ve kararlı PowerShell modülleri, betikler ve DSC kaynakları daha geniş PowerShell kullanıcı toplulukla paylaşmak için yerdir.

Bu makalede mechanics ve bir betik veya modül hazırlamak ve PowerShell Galerisi'nde yayımlama için önemli adımlar anlatılmaktadır. Gözden geçirmenizi önemle öneririz [yayımlama kılavuzları](../../concepts/publishing-guidelines.md) yayımladığınız öğeleri daha yaygın olarak PowerShell Galerisi kullanıcılar tarafından kabul edilecek emin olmak nasıl yapılacağını görmek için.

Bir öğe PowerShell galerisinde yayımlamak için en düşük gereksinimleri şunlardır:

- PowerShell Galerisi hesabınız ve ilişkili API anahtarı
- Öğenizi içinde gerekli meta verileri olduğundan emin olun
- Öğenizi yayımlamaya hazır olduğundan emin olmak için ön doğrulama araçları kullanın
- Publish-Module ve Publish-Script komutlarını kullanarak PowerShell Galerisi'nde öğesi yayımlama
- Sorularınız veya endişeleriniz öğeniz hakkında yanıt

PowerShell Galerisi, PowerShell modülleri ve PowerShell betiklerini kabul eder. Betikleri diyoruz, tek dosyayı ve daha büyük bir modülün parçası olan bir PowerShell Betiği demek isteriz.

## <a name="powershell-gallery-account-and-api-key"></a>PowerShell Galerisi hesabı ve API anahtarı

Bkz: [PowerShell Galerisi hesabı oluşturma](/powershell/gallery/how-to/publishing-packages/creating-an-account) PowerShell Galerisi hesabınızı ayarlarken öğrenmek için.

Bir hesap oluşturduktan sonra öğeyi yayımlamak için gereken API anahtar alabilirsiniz. Hesabıyla oturum açın, sonra kullanıcı adınızı, YAZMAÇ yerine PowerShell Galerisi sayfaların üst kısmındaki görüntülenir. Kullanıcı adınıza tıklayarak API anahtarı nerede hesabım sayfasına gideceksiniz.

Not: API anahtarı kullanıcı adı ve parola olarak güvenli bir şekilde değerlendirilmesi gerekir.
Bu anahtar ile siz veya başka biri PowerShell Galerisi'nde olduğunuz herhangi bir öğeyi güncelleştirebilirsiniz.
Yapılabilir anahtarı düzenli olarak güncelleştirilmesi önerilir, Hesabım sayfasında sıfırlama anahtarını kullanarak.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>PowerShell Galerisi'nde yayımlanmış öğeler için gerekli meta veriler

PowerShell Galerisi, Galeri kullanıcılara komut veya modül bildiriminde bulunan meta verileri alanlarından alınan bilgi sağlar. PowerShell Galerisi yayına öğeleri oluşturmak veya küçük bir öğe bildiriminde sağlanan bilgi gereksinimleri vardır.
Öğe meta verileri bölümünü gözden geçirmeniz önemle öneririz [yayımlama kılavuzları](../../concepts/publishing-guidelines.md) öğelerinizle kullanıcıları için en iyi bilgileri sağlama hakkında bilgi edinmek için.

[Yeni ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) ve [yeni ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) cmdlet'leri oluşturacaktır bildirim şablonu, bildirim tüm öğeler için yer tutucu ile.

Her iki bildirimlerinin yayımlamak için birincil anahtar verileri ve PSData alanını PrivateData önemli olan iki bölümü vardır. Birincil anahtar PowerShell modül bildirimindeki PrivateData bölümün dışında her şey verilerdir. Birincil bir anahtar kümesini kullanmak PowerShell sürümünde bağlı ve tanımsız desteklenmez. PrivateData, PowerShell Galerisi'nde belirli öğeleri PSData böylece yeni anahtarları eklenmesini destekler.


Öğe PowerShell galerisinde yayımlamak için doldurmak en önemli olan bildirim öğeler şunlardır:

- Komut veya modül adı - bu adlarından çizilir. Bir komut dosyası PS1 veya. Bir modül için PSD1.
- Sürüm - bu gerekli bir birincil anahtar, biçim SemVer yönergeleri izlemelidir. Ayrıntılar için bkz.
- Yazar - bu gerekli bir birincil anahtar ve öğeyle ilişkilendirilecek adı içerir.
Yazarlar ve sahipleri aşağıya bakın.
- Açıklama - budur bu öğeyi yapar ve kullanım gereksinimlerini kısaca açıklamak için gereken birincil bir anahtar kullanılan
- ProjectURI - bu önerilir URI, Github deposuna bağlantı sağlayan PSData veya benzer konumunda geliştirmenizi öğesi üzerinde yaptığınız bir alandır
- Etiketler - paketinizi pseditions'ı ve Platform uyumluluğunu göre etiket güçlü önerilir. Ayrıntılar için bkz [yayımlama kılavuzları](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Yazarlar ve PowerShell sahipleri galeri öğeleri, ilgili kavramlardır, ancak her zaman eşleşmiyor. Öğe sahipleriyle öğesi korumak için izne sahip bir PowerShell Galerisi hesaplarıyla kullanıcılardır. Herhangi bir öğeyi güncelleştirebilirsiniz fazla sahip olabilir. Sahibi yalnızca PowerShell Galerisi'nden kullanılabilir ve öğe başka bir sistemden kopyalanırsa kaybolur. Yazar, her zaman bir öğenin bir parçası olacak şekilde bildirim verileri, yerleşik bir dizedir. Microsoft ürünleri öğelerinden önerilerdir:

- En az bir öğe oluşturan takım adı olan birden çok sahipleri
- Bir bilinen takım adı (örneğin, Azure SDK'sı ekibi) yazar veya Microsoft Corporation


## <a name="pre-validate-your-item"></a>Öğeniz önceden doğrulanamadı

PowerShell Galerisi'nde öğeniz yayımlamadan önce kodunuzu çalıştırmak için ihtiyacınız olan birkaç araç vardır:

- [PowerShell betik Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), PowerShell Galerisi'nde olduğu
- Modüller için PowerShell parçası olan Test ModuleManifest
- PowerShell Get ile sunulan Test ScriptFileInfo betikleri için

[PowerShell betik Çözümleyicisi](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) kodunuzu emin olmak için tarama yapmadan bir statik kod analizi aracı karşılayan kodlama yönergeleri temel PowerShell olduğu. Bu araç, kodunuzdaki yaygın ve kritik sorunları tanımlayacak ve öğeniz yayımlamaya hazır yardımcı olmak için düzenli olarak geliştirme sırasında çalıştırılmalıdır. PowerShell betik Çözümleyicisi, hatalar, uyarı ve bilgi tanımlanan sorunların listesini sağlar. PowerShell Galerisi'nde yayımlamadan önce tüm hataları ele alınması gerekir. Çoğu ilgilenilmesi gerekir ve Uyarıları gözden geçirilmesi gerekir. PowerShell betik Çözümleyicisi bir öğe yayımlanmış veya güncelleştirilmiş PowerShell Galerisi'nde her zaman çalışır. Galeri operasyon ekibinin bulunan hatalarını gidermek için öğe sahipleriyle iletişime geçeceğiz.

PowerShell Galerisi altyapısı tarafından öğeniz bildirim bilgileri okunamadığında yayımlamak mümkün olmayacaktır.
[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) Modülü yüklü olduğunda kullanılabilir olmaması neden olan yaygın sorunlar yakalar. Her modülü PowerShell Galerisi'nden yayımlamadan önce çalıştırılması gerekir.

Benzer şekilde, [Test ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) betikteki meta verileri doğrular ve Powershell galeride yayımlamadan önce her komut (yayımlanan ayrı bir modülden) çalıştırmanız gerekir.


## <a name="publishing-items"></a>Yayımlama öğeleri

Kullanmalısınız [Publish-Script](/powershell/module/PowerShellGet/publish-script) veya [Publish-Module](/powershell/module/PowerShellGet/publish-module) öğeleri PowerShell galerisinde yayımlamak için. Bu komutların her ikisi de gerektirir:

- Yayımlayacağınız öğenin yolu. Bir modül, modül için adlı klasörü kullanın. Birden çok sürümünü aynı modülde içeren bir klasör belirtirseniz RequiredVersion belirtmeniz gerekir.
- Bir Nuget API anahtarı. PowerShell Galerisi hesabım sayfasında bulunan API anahtarı budur.

Böylece bunları komutta belirtmeniz gerekmez komut satırında diğer seçeneklerin çoğu yayımlamakta olduğunuz öğesi için bildirim veri olması gerekir.

Hataları önlemek için - Whatif kullanarak komutları deneyin önerilir-Verbose, yayımlamadan önce. PowerShell galerisinde yayımlamak her zaman bu yana önemli ölçüde zaman kazandırır, öğe bildirimi bölümündeki sürüm numarasını güncelleştirmeniz gerekir.

Örnek şöyle olacaktır:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -Whatif -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose`

Çıkış dikkatle gözden geçirin ve bir hata veya uyarı görürseniz, - Whatif olmadan komutu yineleyin.

PowerShell Galerisi'nde yayımlanmış öğeler virüs taraması ve PowerShell betik Çözümleyicisi'ni kullanarak analiz edilir. O anda ortaya çıkan sorunları yayımcıya çözümlemesi için gönderilir.

Bir öğe için PowerShell Galerisi yayımladıktan sonra öğeniz hakkında geri bildirim izlemesi gerekir.

- Olun yayımlamak için kullanılan hesap ile ilişkili e-posta adresini izleyin. Kullanıcılar ve PowerShell Galerisi operasyon ekibinin sorunları PSSA veya virüsten koruma taraması dahil olmak üzere bu hesap aracılığıyla geri bildirim sağlar. E-posta hesabı geçersiz ya da hesap ve uzun bir süredir çözümlenmemiş sol bildirilen önemli sorunları, öğe bırakıldı ve PowerShell Galerisi'nden açıklandığı kaldırılacak kabul edilebilir bizim [kullanım](https://www.powershellgallery.com/policies/Terms).
- Yayımladığınız her PowerShell galeri öğesi için yorumlara abone ol öneririz. Bu, herkesin öğelerinizi PowerShell Galerisi hakkında yorumlar durumunda sağlar. LiveFyre ile bir hesabı oluşturuluyor gerektirdiği isteğe bağlıdır.
