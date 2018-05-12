---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_faqs
ms.openlocfilehash: 83954908acdab716cb938881b3ee80badaa1c6e1
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

## <a name="what-is-a-powershell-module"></a>PowerShell Modülü nedir?

PowerShell modülü, PowerShell işlevselliğinin içeren yeniden kullanılabilir bir pakettir. Her şeyi (İşlevler, değişkenleri, DSC kaynakları, vb.) PowerShell modülleri paketlenebilir. Genellikle, belirli türde belirli yola depolanan dosyaları içeren klasörleri modüllerdir. PowerShell modülleri ölçeklendiriyor birkaç farklı türde vardır.

## <a name="what-is-a-powershell-script"></a>Bir PowerShell komut dosyası nedir?

Bir PowerShell Betiği yeniden kullanma ve paylaşma etkinleştirmek için bir .ps1 dosyasına depolanan komutları dizisidir. PowerShell Ayrıca, bir dizi görevi anahat ve bu görevler için sıralama belirtin, PowerShell komut dosyası iş akışlarıdır. Daha fazla bilgi için lütfen ziyaret [PowerShell iş akışı ile çalışmaya başlama](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>PowerShell betiklerinin PowerShell modülleri fark nedir?

Modülleri paylaşmak için genellikle daha iyi, ancak iş akışları ve betikler topluluğa katkıda kolaylaştırmak komut dosyası paylaşımı biz etkinleştirme. Daha fazla bilgi için aşağıdaki Bloglara bakın:

- [Komut dosyaları, yazma PowerShell modülleri yazma yok](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [PowerShell modülleri anlama](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>PowerShell Galerisi nasıl yayımlayabilmeniz için?

Galeri öğeleri yayımlayabilmeniz için önce bir hesap PowerShell galerisinde kaydetmeniz gerekir. Öğelerini yayımlama kayıt sırasında sağlanan bir NuGetApiKey gerektirdiğinden budur. Kaydetmek için kişisel, iş veya Okul hesabı için PowerShell Galerisi oturum açmak için. Tek seferlik kayıt işlemini ilk kez oturum açtığınızda gereklidir. Daha sonra NuGetApiKey profil sayfanızda kullanılabilir.

Galeride kaydettikten sonra kullanmak [Yayımla-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) veya [Yayımla-komut dosyası](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) öğenizi galerisinde yayımlamak için cmdlet'leri. Bu cmdlet'lerinin nasıl çalıştırılacağı hakkında daha fazla ayrıntı için Yayımla sekmesini adresini ziyaret edin veya okuma [Yayımla-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ve [Yayımla-komut dosyası](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) belgeleri.

**Kaydetme veya Galeri'ye yükleyin veya öğeleri kaydetmek için oturum açma gerekmez.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>"İstek işlenemedi. aldım 'Belirtilen API anahtarı geçersiz veya belirtilen paket erişim izni yok.'. Uzak sunucu bir hata döndürdü: (403) Yasak. " bir öğe PowerShell galerisinde yayımlamak çalışırken hata oluştu. Bu ne demek?

Bu hata aşağıdaki nedenlerle oluşabilir:

- **Belirtilen API anahtarı geçersiz.**
     Hesabınızdan geçerli API anahtarı belirttiğinizden emin olun. API anahtarınızı almak için profili sayfasını görüntüleyin.
- **Belirtilen öğe adı size ait değil.**
     Doğruladıysanız API anahtarınıza doğru olduğundan ve ayrıca kullanmaya çalıştığınız biri aynı ada sahip bir öğe zaten bulunabilir. Öğe sahibi tarafından listelenmemiş olabilir, bu durumda herhangi arama sonuçlarında görünmez. Aynı ada sahip bir öğe zaten olup olmadığını belirlemek için bir tarayıcı açın ve öğenin ayrıntıları sayfasına gidin: `https://www.powershellgallery.com/packages/<itemName>`. Örneğin, doğrudan gezinme `https://www.powershellgallery.com/packages/pester` onu olsun veya olmasın listelenmemiş Pester modülünün ayrıntıları sayfasına gideceksiniz. Çakışan bir ada sahip bir öğe zaten var ve listede yoksa, şunları yapabilirsiniz:
    - Öğenizi için başka bir ad seçin.
    - Varolan öğeyi sahipleri başvurun.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>My kişisel hesabıyla oturum açamazsınız ancak dün oturum neden?

Galeri hesabınızın birincil e-posta diğer adınız değişiklikler hale getirmez unutmayın. Daha fazla bilgi için bkz: [Microsoft e-posta diğer adlar](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Öğeleri sekmesinde tüm kategori onay kutularını seçtiğinizde tüm galeri öğelerini neden göremiyorum?

Bir kategori onay kutusunu seçerek, "Bu kategorideki tüm öğeleri görmek istiyorum." belirten Yalnızca seçili kategorilerdeki öğeleri görüntülenir. Bu nedenle benzer şekilde, tüm kategori onay kutularını işaretleyerek, "Herhangi bir kategorideki tüm öğeleri görmek istiyorum." belirten Ancak, yani sonuçlarında görünmez galerideki bazı öğeler listelenen, kategorilerden birine ait değil. Galerideki tüm öğeleri görmek için tüm kategorileri seçeneğinin işaretini kaldırın veya yeniden öğeleri sekmesini seçin.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Bir modül PowerShell galerisinde yayımlamak için gereksinimleri nelerdir?

PowerShell Modülü (betik modüllerini, ikili modülleri veya bildirim modülleri) her türlü Galerisi'ne yayımlanabilir. Bir modül yayımlamak için PowerShellGet birkaç IT - sürüm hakkında bilmek ister açıklama, yazar ve nasıl lisanslanır. Yayımlama işleminin bir parçası olarak bu bilgileri okuyun *modül bildirimi* (.psd1) dosyası ya da değerinden [ **Yayımla-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet **LicenseUri** parametresi. Galeriye yayımlanan tüm modülleri, modül bildirimleri olması gerekir. Kendi bildiriminde aşağıdaki bilgileri içeren herhangi bir modül Galerisi'ne yayımlanabilir:

- Sürüm
- Açıklama
- Yazar
- Bir URI modülünün bir parçası olarak ya da Lisans Koşulları'nı **PrivateData** bölüm bildiriminin ya da içinde **LicenseUri** parametresinin [ **Yayımla-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Doğru biçimlendirilmiş modül bildirimi nasıl oluşturulur?

Bir modül bildirimi oluşturmak için en kolay yolu çalıştırmaktır [ **yeni ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i. PowerShell 5.0 veya daha yeni, doğru biçimlendirilmiş modül bildirimi gibi yararlı meta veriler için boş alanları ile yeni ModuleManifest oluşturur **ProjectUri**, **LicenseUri**, ve **etiketleri**. Yalnızca boşlukları doldurursunuz veya üretilen bildirim doğru biçimlendirme örneği olarak kullanın.

Gerekli tüm meta veri alanlarını düzgün doldurulmuş doğrulamak için kullanılan [ **Test ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

Modül bildirim dosyası alanlarını güncelleştirmek için kullanmak [ **güncelleştirme ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Bir komut dosyası galerisinde yayımlamak için gereksinimleri nelerdir?

PowerShell Betiği (komut dosyaları veya iş akışları) her türlü Galerisi'ne yayımlanabilir. Bir komut dosyası yayımlamak için PowerShellGet birkaç IT - sürüm hakkında bilmek ister açıklama, yazar ve nasıl lisanslanır. İçin yayımlama işlemini komut dosyasının bir parçası olarak bu bilgileri okuyun *PSScriptInfo* bölümünde veya değerinden [ **Yayımla-komut dosyası** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet  **LicenseUri** parametresi. Galeriye yayımlanan tüm betikler meta veri bilgilerine sahip olması gerekir. Kendi PSScriptInfo bölümünde aşağıdaki bilgileri içeren herhangi bir komut dosyası Galerisi'ne yayımlanabilir:

- Sürüm
- Açıklama
- Yazar
- Betiğin bir parçası olarak ya da Lisans Koşulları'nı bir URI **PSScriptInfo** bölüm betiğin veya içinde **LicenseUri** parametresinin [ **Yayımla-komut dosyası** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

## <a name="how-do-i-search"></a>Nasıl arama yapabilirim?

Ne metin kutusuna aradığınız yazın. Örneğin, Azure SQL ilgili modülleri bulmak istiyorsanız, yalnızca "azure sql" yazın. Bizim arama motoru başlıkları, açıklamaları da dahil olmak üzere tüm yayımlanan öğeleri ve meta verileri üzerinden bu anahtar sözcükleri arar. Ardından, bir ağırlıklı kalite puan bağlı olarak, bu en yakın eşleşmeleri görüntüler. Alanını kullanarak belirli alana göre arama yapabilirsiniz: "değeri" aşağıdaki alanlar için arama sorgusu söz dizimi:

- Etiketler
- İşlevler
- Cmdlet’ler
- DscResources
- PowerShellVersion

Böylece, örneğin PowerShellVersion için arama yaparken: PowerShellVersion (kendi modülü/komut dosyası bildiriminde göre) 2.0 ile uyumlu olan "2.0" yalnızca sonuçları görüntülenir.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Doğru biçimlendirilmiş bir betiğin nasıl oluşturulur?

Doğru biçimlendirilmiş komut dosyası oluşturmak için en kolay yolu çalıştırmaktır [ **yeni ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i. PowerShell 5. 0'da, yeni ScriptFileInfo gibi yararlı meta veriler için boş alanı olan bir komut dosyası doğru biçimlendirilmiş dosyası oluşturur. **ProjectUri**, **LicenseUri**, ve **etiketleri** . Yalnızca boşlukları doldurursunuz ya da oluşturulan komut dosyası doğru biçimlendirilmiş bir örnek kullanın.

Gerekli tüm meta veri alanlarını düzgün doldurulmuş doğrulamak için kullanılan [ **Test ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

Komut dosyası meta veri alanlarını güncelleştirmek için kullanmak [ **güncelleştirme ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

## <a name="what-other-types-of-powershell-modules-exist"></a>Ne PowerShell modülleri diğer türleri var?

Terim PowerShell modülü de gerçek işlevselliğini uygulayan dosyalara başvurur. Betik Modülü dosyaları (.psm1) PowerShell kodu içerir. İkili Modülü dosyaları (.dll) derlenmiş kod içerir.

İşte hakkında düşünmek için bir yol: modül yalıtan modülü klasör klasörüdür. Modül klasörü klasörünün içeriğini açıklayan bir modül bildirimi (.psd1) içerebilir. Aslında işini yapması komut Modülü dosyaları (.psm1) ve ikili Modülü dosyaları (.dll) dosyalarıdır. DSC kaynakları belirli bir alt klasöründe bulunur ve komut dosyası modülü veya ikili Modülü dosyaları uygulanır.

Tüm modülleri galerisinde modül bildirimleri içerir ve bu modüllerin çoğu betik modülü veya ikili Modülü dosyaları içerir. Terim modülü nedeniyle bu farklı anlamları kafa karışıklığına neden olabilir. Açıkça aksi belirtilmedikçe, tüm kullanır, bu sayfada word modülün bu dosyaları içeren modülü klasörüne bakın.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>PackageManagement PowerShellGet için nasıl ilişkilidir? (Yüksek düzey yanıt)

PackageManagement, hiçbir Paket Yöneticisi ile çalışmak için ortak bir arabirimdir. Sonuç olarak, PowerShell modülleri, MSI'lerini, Söyleniş gems, NuGet paketlerini veya Perl modülleri ile ilgilenen olup olmadığını PackageManagement'ın komutları (Bul-paket ve Install-Package) bulun ve bunları yüklemek için kullanmak mümkün olmalıdır. PackageManagement bu PackageManagement takılan her Paket Yöneticisi için bir paket sağlayıcı sağlayarak gerçekleştirir. Sağlayıcıları asıl işi tümünü; Bunlar havuzların içeriği getirebilir ve içeriği yerel olarak yükleyin. Genellikle, paket sağlayıcıları yalnızca verilen paket türü için varolan Paket Yöneticisi Araçları sarma.

PowerShellGet PowerShell öğeleri için paket yöneticisidir. PackageManagement aracılığıyla PowerShellGet işlevselliği kullanıma sunan bir PSModule paket sağlayıcısı yok. Bu nedenle, her iki çalışma için [yükleme-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) veya Install-Package-PSModule PowerShell Galerisi'nden modül yüklemek için sağlayıcı. Bazı PowerShellGet işlevselliği de dahil olmak üzere [güncelleştirme Modülü](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ve [Yayımla-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), PackageManagement komutları erişilemiyor.

Özet olarak, PowerShell içerik için bir premium paket yönetim deneyimi sahip PowerShellGet yalnızca odaklanmıştır. PackageManagement bir genel birtakım Araçlar tüm paket yönetim deneyimleriyle gösterme üzerinde odaklanmıştır. Bu yanıt unsatisfying bulursanız, olduğundan bu belgenin sonundaki uzun yanıt **nasıl PackageManagement gerçekten ilişkilendirmek için PowerShellGet?** bölümü.

Daha fazla bilgi için lütfen ziyaret [PackageManagement proje sayfası](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>NuGet PowerShellGet için nasıl ilişkilidir?

PowerShell Galerisi değiştirilmiş bir sürümüdür [NuGet galerisinde](https://www.nuget.org/). PowerShellGet PowerShell Galerisi gibi temel NuGet depoları çalışmak için NuGet sağlayıcısını kullanır.

Tüm geçerli NuGet deposu veya dosya paylaşımı karşı PowerShellGet kullanabilirsiniz. Çalıştırarak depo eklemeniz yeterlidir [ **Register-PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet'i.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Bu, NuGet.exe Galerisi ile çalışmak için kullanabilir miyim anlama geliyor?

Evet.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Nasıl PackageManagement PowerShellGet için gerçekten ilişkilidir? (Teknik ayrıntıları)

Başlık altında PowerShellGet yoğun PackageManagement altyapı yararlanır.

PowerShell cmdlet katmanında [yükleme-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Install-Package çevresinde gerçekte ince bir sarmalayıcı olduğu-sağlayıcısı PSModule.

PackageManagement paket sağlayıcısı katmanında PSModule paket sağlayıcısı aslında diğer PackageManagement paket sağlayıcıları çağırır. Örneğin, NuGet tabanlı galerileri (örneğin, PowerShell Galerisi) ile çalışırken, PSModule paket sağlayıcısı deposuyla çalışmak için NuGet paketi sağlayıcısı kullanır.

![PowerShellGet mimarisi](Images/powershellgetArchitecture.png)

Şekil 1: PowerShellGet mimarisi

## <a name="what-is-required-to-run-powershellget"></a>PowerShellGet çalıştırmak için gereken nedir?

Genel PowerShellGet Modülü (.NET 4.5 gerektirdiğini unutmayın) en son sürümünü çekme öneririz.

**PowerShellGet** modülü gerektirir **PowerShell 3.0 veya daha yeni**.

Bu nedenle, **PowerShellGet** aşağıdaki işletim sistemlerinden birini gerektirir:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** de .NET Framework 4.5 gerektirir veya üstü. .NET Framework 4.5 yükleyebilirsiniz ya da yukarıdaki gelen [burada](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>Gelecekte yayımlanacak öğe adları ayırmak mümkün mü?

Alaturka öğe adları için mümkün değildir. Varolan öğeyi daha deneyin öğenizi uygun adına gerçekleştirdiği düşünüyorsanız [öğenin sahibi iletişim kurmasını](./how-to/working-with-items/contacting-item-owners.md). Birkaç hafta içinde yanıt almadı, destek ile iletişime geçin ve PowerShell Galerisi takım için bakacağı.

## <a name="how-do-i-claim-ownership-for-items-"></a>Öğeleri için sahipliğini talep nasıl?

Kullanıma [yönetme öğesi sahiplerinin PowerShellGallery.com üzerinde](./how-to/publishing-items/managing-item-owners.md) Ayrıntılar için.

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>My öğesi lisans ihlal eden bir öğe sahibi ile nasıl ilgilenir?

Öğe sahipleri ve diğer öğeleri sahipleri arasında kaynaklanabilecek itirazları çözümlemek için birlikte çalışmak üzere PowerShell topluluğu öneririz.  Biz hazırlanmış bir [itiraz çözümleme işlemi](./how-to/getting-support/dispute-resolution.md) , biz PowerShellGallery.com Yöneticiler intercede önce izleyin istenir.