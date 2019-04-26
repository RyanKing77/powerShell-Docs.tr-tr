---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084768"
---
# <a name="getting-started-with-the-powershell-gallery"></a>PowerShell Galerisi ile çalışmaya başlama

PowerShell Galerisi, betikleri ve modülleri indirin ve yararlanarak DSC kaynakları içeren bir paket depodur. Cmdlet'leri kullanmak [PowerShellGet](/powershell/module/powershellget) modülü PowerShell Galerisi'nden paketlerini yükleyin. PowerShell Galerisi'nden öğeleri indirmek oturum açmanız gerekmez.

> [!NOTE]
> Bir paket doğrudan PowerShell Galerisi'nden yüklemek mümkündür, ancak bu önerilen bir yaklaşım değildir.
> Daha fazla ayrıntı için [el ile indirme paketi](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Paketler PowerShell Galerisi'ndeki keşfetme

Kullanarak PowerShell Galerisi'nde paketleri bulabilirsiniz **arama** PowerShell galeri denetiminde [giriş sayfası](https://www.powershellgallery.com), betikleri ve modülleri gözatarak veya gelen [paketleri sayfası ](https://www.powershellgallery.com/packages). Çalıştırarak PowerShell Galerisi'ndeki paketleri bulabilirsiniz [Modül Bul][], [Bul-DscResource], ve [Bulma komut dosyası][] cmdlet'leri, paket türüne bağlı olarak ile `-Repository PSGallery`.

Aşağıdaki parametreleri kullanarak Galeriden sonuçlarını filtreleyebilirsiniz:

- Adı
- AllVersions
- MinimumVersion
- RequiredVersion
- Etiket
- İçerir
- DscResource
- RoleCapability
- Komut
- Filtre

Yalnızca galerideki belirli DSC kaynakları keşfetme içinde ilginizi çeken, çalıştırabileceğiniz [Bul-DscResource] cmdlet'i. Bul-DscResource galeride bulunan DSC kaynaklardaki verileri döndürür.
DSC kaynakları her zaman bir modülün bir parçası olarak teslim edildiğinden, çalıştırmanız yine [Install-Module][] bu DSC kaynakları yüklenecek.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>PowerShell Galerisi paketleri hakkında daha fazla bilgi

İlginizi çeken bir paket belirledikten sonra ilgili daha fazla bilgi edinmek isteyebilirsiniz. Galeri belirli sayfasında bu paketin inceleyerek bunu yapabilirsiniz. Bu sayfada, paket ile karşıya meta verileri görmek mümkün olacaktır. Bu meta veriler paketin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz. Paketinin sahibi kesin paket yayımlamak için kullanılan galeri hesabınıza bağlanır ve yazar alanı daha güvenilirdir.

Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.

Çalıştırıyorsanız [Modül Bul][] veya [Bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verileri görüntüleyebilirsiniz. Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Galerideki PSReadLine modül verileri döndürür.

## <a name="downloading-packages-from-the-powershell-gallery"></a>PowerShell Galerisi'nden paketleri yükleniyor

Aşağıdaki işlem PowerShell Galerisi'nden dosyalar indirilirken öneririz:

### <a name="inspect"></a>İnceleme

Galeri denetimi için bir paket indirmesine izin ya da çalıştırmak [Save-Module][] veya [Save-Script][] cmdlet'i, paket türüne bağlı olarak. Bu, paketi yüklemeden yerel olarak kaydetmek ve paket içeriğini İnceleme sağlar. Kaydedilen paket el ile silmeyi unutmayın.

Bu paketler bazıları Microsoft tarafından yazılmış ve başkaları PowerShell topluluğu tarafından yazılan.
Microsoft, içeriği ve paketleri yüklemeden önce bu galeri, kod gözden geçirme önerir.

Sizin de böyle bir paket iyi niyetle içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** sayfasında bu paketin.

### <a name="install"></a>Yükle

Galeri kullanmak için bir paket yüklemek için ya da çalıştırmak [Install-Module][] veya [Yükleme betiği][] cmdlet'i, paket türüne bağlı olarak.

[Install-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.
Bu, bir yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi modülünün yüklü için `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Yükleme betiği][] betiğe yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.
Bu, bir yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası yüklü olduğu için `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Varsayılan olarak, [Install-Module][] ve [Yükleme betiği][] bir paketin en son sürümünü yükler.
Paketin daha eski bir sürümünü yüklemek için ekleme `-RequiredVersion` parametresi.

### <a name="deploy"></a>Dağıt

Azure Otomasyonu PowerShell Galerisi'ndeki bir pakete dağıtmak için **Azure Otomasyonu**, ardından **Azure Otomasyonu Dağıt** Paket Ayrıntıları sayfasında. Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum açtığınızda Azure yönetim portalına yönlendirilirsiniz. Bağımlılıkları olan paketler dağıtılıyor tüm bağımlılıkları için Azure Otomasyonu dağıttığı unutmayın. 'Azure otomasyonu için Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** paket meta verileriniz için etiket.

Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.

## <a name="updating-packages-from-the-powershell-gallery"></a>PowerShell Galerisi'nden paketler güncelleştiriliyor

PowerShell Galerisi'nden yüklü paketleri güncelleştirmek için Update-Module [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın. Ek parametreler çalıştırdığınızda, güncelleştirme-Module [] çalıştırarak yüklü tüm modüllerin güncelleştirmek çalışır [Install-Module][]. Modüller seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi. 

Benzer şekilde, hiçbir ek parametre olmadan çalıştırdığınızda, [güncelleştirme betiğini] [] ayrıca tüm betikleri çalıştırarak yüklü güncelleştirme girişiminde [Yükleme betiği][]. Komut dosyaları seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell Galerisi'nden yüklediğiniz listeyi paketleri

Hangi modülleri PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledModule][] cmdlet'i. Bu komut, sisteminizde yüklü modülleri PowerShell Galerisi'nden doğrudan yüklenen tüm listeler.

Benzer şekilde, hangi betiklerin PowerShell Galerisi'nden yüklediğiniz öğrenmek için çalıştırma [Get-InstalledScript][] cmdlet'i. Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen, sisteminizde yüklü betikleriniz listeler.

[Bul-DscResource]: /powershell/module/powershellget/Find-DscResource
[Modül Bul]: /powershell/module/powershellget/Find-Module
[Bulma komut dosyası]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Yükleme betiği]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
