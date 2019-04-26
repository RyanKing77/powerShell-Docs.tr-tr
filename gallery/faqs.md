---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi hakkında SSS
ms.openlocfilehash: bcbb36a9ec60d88d1ef56fd270f0ae1862d5ca6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084631"
---
# <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

## <a name="what-is-a-powershell-module"></a>Bir PowerShell Modülü nedir?

Bir PowerShell modülü, bazı PowerShell işlevler içeren yeniden kullanılabilir bir pakettir. Her şeyi (İşlevler, değişkenler, DSC kaynakları, vb.) PowerShell modülleri paketlenebilir. Genellikle, belirli bir yolda depolanmış dosyaları belirli türlerini içeren klasörleri modüllerdir. PowerShell modülleri burada birkaç farklı türde vardır.

## <a name="what-is-a-powershell-script"></a>Bir PowerShell Betiği nedir?

Bir PowerShell Betiği yeniden kullanımı ve paylaşımı için bir .ps1 dosyası depolanan komutları dizisidir. PowerShell iş akışları, ayrıca, bir dizi görevi anahat ve bu görevlerin sıralamasını sağlayan PowerShell betikleri olur. Daha fazla bilgi için lütfen [PowerShell iş akışı ile çalışmaya başlama](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>PowerShell betiklerinin PowerShell modüllerini farklı misiniz?

Modüller paylaşmak için genellikle daha iyi, ancak komut dosyası iş akışları ve betikler topluluğa katkıda kolaylaştırmak paylaşımı etkinleştirdik. Daha fazla bilgi için aşağıdaki Bloglara bakın:

- [Betikler, yazma PowerShell modülleri yazma yok](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [PowerShell modüllerini anlama](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>PowerShell Galerisi'nde nasıl yayımlayabilirim?

Paketleri galeride yayımlamadan önce bir hesap PowerShell Galerisi'nde kaydetmeniz gerekir. Paketleri yayımlama kayıt sırasında sağlanan bir NuGetApiKey gerektirdiğinden budur. Kaydetmek için kişisel, iş veya Okul hesabınızda oturum açmak için PowerShell Galerisi için. İlk kez oturum açtığınızda, tek seferlik kayıt işlemi gereklidir. Daha sonra NuGetApiKey profil sayfanızdan kullanılabilir.

Galeride kaydedildikten sonra kullanın [Yayımlama Modülü][] veya [Yayımlama-komut dosyası][] paketinizi galerisinde yayımlamak için cmdlet'ler.
Bu cmdlet'lerinin nasıl çalıştırılacağı hakkında daha fazla ayrıntı için yayımlama sekmesindeki adresini ziyaret edin veya okuma [Yayımlama Modülü][] ve [Yayımlama-komut dosyası][] belgeleri.

**Galeri'ye yükleyin veya paketleri kaydetmek için oturum açın veya kaydolun gerekmez.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>"İsteği işleyemedi. aldım 'Belirtilen API anahtarı geçersiz veya belirtilen paket erişim iznine sahip değil.'. Uzak sunucu bir hata döndürdü: (403) Yasak." PowerShell Galerisi'nde bir paketi yayımlamaya çalışırken hata oluştu. Bu ne demek?

Bu hata aşağıdaki nedenlerle oluşabilir:

- **Belirtilen API anahtarı geçersiz.**
     Hesabınızdan geçerli API anahtarını belirttiğinizden emin olun. API anahtarınızı almak için profil sayfanızı görüntüleyin.
- **Belirtilen paket adı sizin tarafınızdan ait değil.**
     Doğruladıysanız API anahtarınızı doğru olduğundan ve ayrıca kullanmayı denemekte olduğunuz bir aynı ada sahip bir paket zaten bulunabilir. Paket sahibi tarafından listelenmemiş olabilir, bu durumda herhangi bir arama sonuçlarında görünmez. Aynı ada sahip bir paket zaten mevcut olup olmadığını belirlemek için bir tarayıcı açın ve Paket Ayrıntıları sayfasına gidin: `https://www.powershellgallery.com/packages/<packageName>`. Örneğin, doğrudan gezinme `https://www.powershellgallery.com/packages/pester` , listelenmemiş olup olmadığını Pester modülün Ayrıntılar sayfasına gideceksiniz. Çakışan bir ada sahip bir paket zaten var ve listelenmemiş ise, şunları yapabilirsiniz:
    - Paketiniz için başka bir ad seçin.
    - Var olan paketi sahipleri başvurun.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>My kişisel hesabıyla oturum açamazsınız ancak dün oturum neden?

Galeri hesabınız için birincil e-posta diğer adınızı değişiklikleri hale getirmez unutmayın. Daha fazla bilgi için [Microsoft e-posta diğer adlar](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Paketleri sekmesinde tüm kategori onay kutularını seçtiğimde tüm galeri paketleri neden göremiyorum?

Bir kategori onay kutusunu seçerek, "Bu kategorideki tüm paketleri görmek istiyorum." ifadesi Yalnızca seçilen kategorilerdeki paketler görüntülenir. Bu nedenle benzer şekilde, tüm kategori onay kutularını seçerek, "Herhangi bir kategorideki tüm paketleri görmek istiyorum." belirten Ancak sonuçlarda görünmeyecek galerideki bazı paketler listelenen, kategorilerden birine ait değil. Tüm paketleri galerisinde görmek için tüm kategorileri işaretini kaldırın veya yeniden paketleri sekmesini seçin.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Bir modülü PowerShell galerisinde yayımlamak için gereksinimler nelerdir?

PowerShell Modülü (betik modülleri, ikili modülleri veya bildirim modüllerini) herhangi bir türden Galerisi'ne yayımlanabilir.
Bir modül yayımlamak için PowerShellGet birkaç IT - sürüm hakkında bilmesi gereken açıklama, yazar ve nasıl lisanslanır.
Yayımlama işleminden bir parçası olarak bu bilgileri okuyun *modül bildirimini* (.psd1) dosya veya değerini [Yayımlama Modülü][] cmdlet'in **LicenseUri** parametre.
Galeride yayımlanmış olan tüm modülleri, modül bildirimleri olması gerekir.
Kendi bildiriminde aşağıdaki bilgileri içeren herhangi bir modülü Galerisi'ne yayımlanabilir:

- Sürüm
- Açıklama
- Yazar
- Bir URI modülünün bir parçası olarak ya da lisans koşullarını **PrivateData** bildiriminin ya da bölüm **LicenseUri** parametresinin [Yayımlama Modülü][] cmdlet'i.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Doğru biçimlendirilmiş modül bildirimi nasıl oluşturulur?

Bir modül bildirimi oluşturmak için en kolay yolu çalıştırmaktır [yeni ModuleManifest][] cmdlet'i. PowerShell 5.0 veya daha yeni bir hatalı biçimlendirilmiş modül bildirimi gibi kullanışlı meta veriler için boş alanları ile yeni ModuleManifest oluşturur **ProjectUri**, **LicenseUri**, ve **etiketleri**. Yalnızca boşlukları doldurmak veya oluşturulan bildirim doğru biçimlendirilmiş bir örnek olarak kullanın.

Gerekli tüm meta veri alanları düzgün doldurulur doğrulamak için [Test-ModuleManifest][] cmdlet'i.

Modül bildirim dosyası alanları güncelleştirmek için [güncelleştirme ModuleManifest][] cmdlet'i.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Bir betik galerisinde yayımlamak için gereksinimler nelerdir?

PowerShell Betiği (betikleri veya iş akışları) herhangi bir türden Galerisi'ne yayımlanabilir.
Bir betik yayımlamak için PowerShellGet birkaç IT - sürüm hakkında bilmesi gereken açıklama, yazar ve nasıl lisanslanır.
Betik dosyasının yayımlama işleminden bir parçası olarak bu bilgileri okuyun *PSScriptInfo* bölümünde veya değerini [Yayımlama-komut dosyası][] cmdlet'in **LicenseUri**parametresi.
Galeride yayımlanmış tüm betikler, meta veri bilgilerini olması gerekir.
Kendi PSScriptInfo bölümünde aşağıdaki bilgileri içeren bir betik Galerisi'ne yayımlanabilir:

- Sürüm
- Açıklama
- Yazar
- Bir URI betiğinin bir parçası olarak ya da lisans koşullarını **PSScriptInfo** bölüm veya betiğin **LicenseUri** parametresinin [Yayımlama-komut dosyası][] cmdlet'i.

## <a name="how-do-i-search"></a>Nasıl arayabilirim?

Metin kutusuna aradıklarınızı yazın. Örneğin, Azure SQL'e ilgili modülleri bulmak istiyorsanız, yalnızca "azure sql" yazın. Arama altyapımız başlıklarını, açıklamaları da dahil olmak üzere tüm yayımlanmış paketleri ve meta verileri üzerinden bu anahtar sözcükleri arar. Ardından, ağırlıklı kalite puanına göre bağlı olarak, en yakın eşleşme görüntüler. Aynı zamanda alanını kullanarak belirli alana göre arayabilirsiniz: "değer" söz dizimi arama sorgusuna şu alanlar için:

- Etiketler
- İşlevler
- Cmdlet’ler
- DscResources
- PowerShellVersion

Böylece, örneğin PowerShellVersion için arama yaparken: PowerShellVersion (kendi modül/komut dosyası bildiriminde göre) 2.0 ile uyumlu olan "2.0" yalnızca sonuçları görüntülenir.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Doğru biçimlendirilmiş bir betiğin nasıl oluşturulur?

Doğru biçimlendirilmiş komut dosyası oluşturmak için en kolay yolu çalıştırmaktır [yeni ScriptFileInfo][] cmdlet'i. PowerShell 5. 0'da, yeni ScriptFileInfo gibi kullanışlı meta veriler için boş alanları ile doğru biçimlendirilmiş bir betik dosyası oluşturur. **ProjectUri**, **LicenseUri**, ve **etiketleri** . Yalnızca boşlukları doldurmak veya doğru biçimlendirilmiş bir örnek olarak oluşturulan komut dosyasını kullanın.

Gerekli tüm meta veri alanları düzgün doldurulur doğrulamak için [Test-ScriptFileInfo][] cmdlet'i.

Komut dosyası meta veri alanları güncelleştirmek için [Update-ScriptFileInfo][] cmdlet'i.

## <a name="what-other-types-of-powershell-modules-exist"></a>Ne diğer PowerShell modüllerini türleri var?

Terim PowerShell modülü de gerçek işlevselliğini uygulayan dosyaları gösterir. Betik Modülü dosyaları (.psm1) PowerShell kodunu içerir. İkili modül dosyaları (.dll) derlenmiş kodunu içerir.

Hakkında düşünmek yöntemlerinden biri aşağıda verilmiştir: modül kapsülleyen klasörü modülü klasörüdür. Modül klasörü klasörünün içeriğini açıklayan bir modül bildirimi (.psd1) içerebilir. İşi yapan komut Modülü dosyaları (.psm1) ve ikili modül dosyaları (.dll) dosyalarıdır. DSC kaynakları belirli bir alt klasörde yer alır ve komut modülü dosyalarını veya ikili modül dosyaları olarak uygulanır.

Tüm Galerisi modülleri, modül bildirimleri içeren ve bu modüllerin çoğu betik modülü veya ikili modül dosyaları içerir. Terim modülü nedeniyle bu farklı anlamları kafa karıştırıcı olabilir. Açıkça aksi belirtilmediği sürece, bu dosyaları içeren modül klasöre word modülü bu sayfadaki tüm kullanımları bakın.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Paket yönetimi için PowerShellGet nasıl ilişkilidir? (Yüksek düzey yanıt)

PackageManagement, herhangi bir paket Yöneticisi ile çalışmak için bir ortak arabirimdir. Sonuç olarak, PowerShell modülleri, Msı'ler, Ruby toprağa değerli taşlar, NuGet paketlerini veya Perl modülleri ile ilgilenen olsun, PackageManagement'ın komutları (Bul-Package ve Install-Package) bulmak ve onları yüklemek için kullanabilmek için olmalıdır. PackageManagement PackageManagement takılan her Paket Yöneticisi için bir paket sağlayıcı sağlayarak bunu yapar. Sağlayıcıları tüm asıl işi gerçekleştirmek; Bunlar depolarından içeriği getirmek ve içeriği yerel olarak yükleyin. Genellikle, paket sağlayıcıları yalnızca belirli bir paket türü için var olan paketi Yöneticisi Araçları sarma.

PowerShellGet, PowerShell paketler için paket yöneticisidir.
PackageManagement ile PowerShellGet işlevsellik sunduğu bir PSModule paket sağlayıcısı yok.
Bu nedenle, her iki çalışma yapabilecekleriniz [Install-Module][] veya Install-Package-modülü PowerShell Galerisi'nden yüklemek için sağlayıcı PSModule.
Bazı PowerShellGet işlevleri dahil olmak üzere [Güncelleştirme Modülü][] ve [Yayımlama Modülü][], PackageManagement komutları erişilemez.

Özet olarak, PowerShellGet yalnızca PowerShell içeriği için bir premium paket yönetimi deneyimi olan odaklanır. PackageManagement genel bir araç seti tüm paket yönetim deneyimleriyle gösterme üzerinde odaklanır. Bu yanıt unsatisfying fark ederseniz, bu belgenin sonundaki bir uzun yanıt alanında var. **nasıl PackageManagement gerçekten ilişkilendirmek için PowerShellGet?** bölümü.

Daha fazla bilgi için lütfen [PackageManagement proje sayfası](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>NuGet için PowerShellGet nasıl ilişkilidir?

PowerShell Galerisi değiştirilmiş bir sürümüdür [NuGet galerisinde](https://www.nuget.org/). PowerShellGet, PowerShell Galerisi gibi temel NuGet depoları ile çalışmak için NuGet sağlayıcısı kullanır.

PowerShellGet geçerli NuGet depo veya dosya paylaşım karşı kullanabilirsiniz. Çalıştırarak depoya eklemeniz yeterlidir [Register-PSRepository][] cmdlet'i.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>NuGet.exe Galerisi ile çalışmak için kullanabileceğim anlama geliyor?

Evet.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>PackageManagement nasıl gerçekten için PowerShellGet ilişkilidir? (Teknik ayrıntıları)

PowerShellGet, altyapı öğeleri, PackageManagement altyapı yoğun bir şekilde yararlanır.

PowerShell cmdlet katmanında [Install-Module][] Install-Package çevresinde aslında basit bir sarmalayıcı olan-sağlayıcısı PSModule.

PackageManagement paket sağlayıcısı katmanında PSModule paket sağlayıcısı gerçekten diğer PackageManagement paket sağlayıcıları çağırır. Örneğin, NuGet tabanlı galeriler (örneğin, PowerShell Galerisi) ile çalışırken, PSModule paket sağlayıcısı deposu ile çalışacak şekilde NuGet paketi sağlayıcısı kullanır.

![PowerShellGet mimarisi](Images/powershellgetArchitecture.png)

Şekil 1: PowerShellGet mimarisi

## <a name="what-is-required-to-run-powershellget"></a>PowerShellGet çalıştırmak için gereken nedir?

Genel olarak PowerShellGet Modülü (.NET 4.5 gerektirir. Not) en son sürümünü çekme öneririz.

**PowerShellGet** modülü gerektirir **PowerShell 3.0 veya daha yeni**.

Bu nedenle, **PowerShellGet** aşağıdaki işletim sistemlerinden birini gerektirir:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** ayrıca .NET Framework 4.5 gerektirir veya üzeri. .NET Framework 4.5 yüklemek ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Bu ad gelecekte yayımlanacak paketleri için ayrılacak mümkün mü?

Alaturka paket adları için mümkün değildir. Var olan bir paket daha deneyin paketinizi uygun ad sürdü düşünüyorsanız [paketinin sahibinden](./how-to/working-with-packages/contacting-package-owners.md). Birkaç hafta içinde yanıt almadıysanız, desteğe başvurabilirsiniz ve bunun için görünür PowerShell Galerisi takım.

## <a name="how-do-i-claim-ownership-for-packages"></a>Paketler için mülkiyeti üzerine hak iddia nasıl?

Kullanıma [PowerShellGallery.com üzerinde paket sahiplerini yönetme](./how-to/publishing-packages/managing-package-owners.md) Ayrıntılar için.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Paket Lisansımı ihlal bir paket sahibi ile nasıl dağıtılsın mı?

Paket sahipleri ve diğer paketleri sahipleri arasında kaynaklanabilecek herhangi Anlaşmazlıkların çözüm yeri birlikte çalışmak üzere PowerShell topluluğu öneririz.  Biz hazırlanmış bir [itiraz çözümleme işlemi](./how-to/getting-support/dispute-resolution.md) , PowerShellGallery.com Yöneticiler intercede önce izleyin isteriz.

[Yeni ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Güncelleştirme ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Update-ModuleManifest

[Install-Module]: /powershell/module/PowershellGet/Install-Module
[Yeni ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Yayımlama Modülü]: /powershell/module/PowershellGet/Publish-Module
[Yayımlama-komut dosyası]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Güncelleştirme Modülü]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
