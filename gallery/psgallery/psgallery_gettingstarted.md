---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: d13c23cd6f9cce433cd3fe1ad5f2d00e3ef0527c
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="get-started-with-the-powershell-gallery"></a>PowerShell Galerisi ile çalışmaya başlama

## <a name="what-is-the-powershell-gallery"></a>PowerShell Galerisi nedir?

PowerShell Galerisi PowerShell içerik için merkezi depodur.
İçinde PowerShell komutlarını ve istenen durum Yapılandırması'nı (DSC) kaynakları içeren yararlı PowerShell modülleri bulabilirsiniz. PowerShell komut dosyaları, bazıları PowerShell iş akışları ve hangi bir dizi görevi anahat içeren ve bu görevler için sıralama sağlamak da bulabilirsiniz.
Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan.

## <a name="requirements"></a>Gereksinimler

Sisteminize PowerShell Galerisi'nden öğe indirme gerektirir [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modülü. Aşağıdakilerden birini PowerShellGet modülü bulabilirsiniz. PowerShell Galerisi'nden öğe indirme oturum açmak gerekmez.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [MSI Yükleyicisi (için PowerShell 3. ve 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet de gerektirir [NuGet sağlayıcı](http://go.microsoft.com/fwlink/?LinkId=722208) PowerShell Galerisi ile çalışmak için. NuGet sağlayıcısı aşağıdaki konumlardan birinde değilse NuGet sağlayıcısı PowerShellGet ilk kullanımında otomatik olarak üzerine yüklemeniz istenir:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Ya da çalıştırabilirsiniz `Install-PackageProvider -Name NuGet -Force` indirme ve yükleme NuGet sağlayıcısının otomatik hale getirmek için.

  
NuGet 2.8.5.201 eski bir sürüm varsa, yüklemek ve NuGet en son sürümüne geçiş için aşağıdaki PowerShell cmdlet'lerini aramak gerekir.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  NuGet eski sürümü yukarıdaki yüklü konumundan silin.

Daha fazla bilgi için bkz: <http://oneget.org/> .

  
Not: paketleme biçimlerde değişiklikler nedeniyle PowerShellGet ve PackageManagement en son güncelleştirilen öğeleri yüklemek için en son sürümüne güncelleştirme öneririz. PowerShellGet hakkında daha fazla bilgi edinebilirsiniz Windows 10 dahil [burada](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet karşıdan yükleyebileceğiniz parçası olarak Windows Management Framework (WMF) 5.0, ayrıca olduğu [burada](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğeleri bulma

PowerShell galerisinde öğelerini kullanarak bulabilirsiniz **arama** denetim bu Web sitesinde veya modüller ve komut dosyaları sayfalarıyla giderek. PowerShell Galerisi'nden öğe çalıştırarak bulabileceğiniz [bulma Modülü](https://go.microsoft.com/fwlink/?LinkId=821658) ve [bulma komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.

Galeri sonuçlarını filtreleme yapılabilir aşağıdaki parametreleri kullanarak [bulma Modülü](https://go.microsoft.com/fwlink/?LinkId=821658) ve [bulma komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822322)

- Ad
- AllVersions
- MinimumVersion
- RequiredVersion
- Tag
- İçerir
- DscResource
- RoleCapability
- Komut
- Filtre

Yalnızca galerisinde belirli DSC kaynakları bulmak isterseniz, çalıştırabilirsiniz [Bul DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet'i.
[Bul DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) DSC kaynakları galeride yer alan verileri döndürür. DSC kaynakları her zaman bir modül bir parçası olarak teslim edildiğinden, hala çalıştırmanız gereken [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663) bu DSC kaynakları yüklemek için.

## <a name="learning-about-items-in-the-powershell-gallery"></a>PowerShell galerisinde öğeleri hakkında bilgi

İlgilendiğiniz öğeyi tanımladıktan sonra hakkında daha fazla bilgi edinmek isteyebilirsiniz. Bu öğeye ait belirli galeri sayfasında inceleyerek bunu yapabilirsiniz. Bu sayfada tüm öğe ile karşıya meta verileri görmek mümkün olur. Bir öğe için bu meta veri öğesi'nin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz. Öğenin sahibi öğesini yayımlamak için kullanılan galeri hesabı kesinlikle bağlıdır ve yazar alanı daha güvenilirdir.

Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.

Çalıştırıyorsanız [bulma Modülü](https://go.microsoft.com/fwlink/?LinkId=821658) veya [bulma komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822322), döndürülen PSGetModuleInfo nesnesinde bu verilerini görüntüleyebilir.
Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` galerisinde PSReadLine modül verileri döndürür.

## <a name="downloading-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğe indirme

PowerShell Galerisi'nden öğe indirme sırasında şu işlem öneririz:

### <a name="inspect"></a>İnceleyin.

İnceleme için Galeriden bir öğe indirmek için ya da çalıştırın [Kaydet-Module](https://go.microsoft.com/fwlink/?LinkId=821669) veya [Kaydet-komut dosyası](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet öğesi türüne bağlı olarak. Bu, yüklemeden öğeyi yerel olarak kaydedin ve öğenin içeriğini incelemek sağlar. Kaydedilen öğeyi el ile silmek unutmayın.

Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan. Microsoft, yüklemeden önce bu galeri öğeleri kodunu ve içeriğini gözden önerir.

Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.

### <a name="install"></a>Yükle

Kullanmak için Galeriden bir öğe yüklemek için ya da çalıştırın [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663) veya [yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet öğesi türüne bağlı olarak.

[Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak. Bu yönetici hesabı gerektirir. Eklerseniz `-Scope
CurrentUser` parametresi modülü için yüklüdür `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327) komut dosyasına yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak. Bu yönetici hesabı gerektirir. Eklerseniz `-Scope
CurrentUser` parametresi, komut dosyası için yüklendiğini `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Varsayılan olarak, [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ve [yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327) öğeyi en güncel sürümünü yükler. Öğe daha eski bir sürümü yüklemek için add `-RequiredVersion` parametresi.

### <a name="deploy"></a>Dağıt

PowerShell Galerisi'nden bir öğe Azure Automation ile dağıtmak için **Azure Otomasyonu Dağıt** öğe Ayrıntıları sayfasında. Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirilir. Bağımlılıkları olan öğeleri dağıtmak için Azure Otomasyonu tüm bağımlılıkları dağıtması unutmayın. 'Azure Otomasyonu Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** öğe meta etiketi.

Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/en-us/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğeler güncelleştiriliyor

PowerShell Galerisi'nden yüklü öğeleri güncelleştirmek için ya da çalıştırın [güncelleştirme Modülü](https://go.microsoft.com/fwlink/?LinkID=398576) veya [güncelleştirme betiğini](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet'i. Herhangi bir ek parametre çalıştırdığınızda [güncelleştirme Modülü](https://go.microsoft.com/fwlink/?LinkID=398576) çalıştırarak yüklü modüllerin güncelleştirmeye [yükleme-Module](https://go.microsoft.com/fwlink/?LinkId=821663).
Modülleri seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.

Benzer şekilde, herhangi bir ek parametre çalıştırdığınızda [güncelleştirme betiğini](http://go.microsoft.com/fwlink/?LinkId=619787) de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [yükleme betiği](https://go.microsoft.com/fwlink/?LinkId=822327).
Komut dosyaları seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell Galerisi'nden yüklediğiniz liste öğeleri

PowerShell Galerisi'nden yüklü modüllerine öğrenmek için Çalıştır [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet'i. Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü modülleri listeler.

PowerShell Galerisi'nden yüklü hangi komut dosyaları bulmak için benzer şekilde, çalıştırmak [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet'i. Bu komut doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü komut dosyalarının tümü listeler.

