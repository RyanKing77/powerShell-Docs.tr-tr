---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523068"
---
# <a name="get-started-with-the-powershell-gallery"></a>PowerShell Galerisi ile çalışmaya başlama

Öğeleri PowerShell Galerisi'nden yüklemek için en uygun yolu cmdlet'ler kullanmaktır [PowerShellGet](/powershell/module/powershellget) modülü. PowerShell Galerisi'nden öğeleri indirmek oturum açmanız gerekmez.

> [!NOTE]
> Bir paket doğrudan PowerShell Galerisi'nden yüklemek mümkündür, ancak bu önerilen bir yaklaşım değildir. Daha fazla ayrıntı için [el ile indirme paketi](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md).  


## <a name="discovering-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğeler bulunuyor

PowerShell galerisinde öğelerini kullanarak bulabilirsiniz **arama** bu Web sitesinde veya modülleri ve betikleri sayfalarıyla atarak denetimi. Çalıştırarak PowerShell Galerisi'ndeki öğeleri bulabilirsiniz [Modül Bul][] ve [Bulma komut dosyası][] cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.

Galeri sonuçlarını filtreleme, aşağıdaki parametreleri kullanarak gerçekleştirilebilir:

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

Yalnızca galerideki belirli DSC kaynakları keşfetme içinde ilginizi çeken, çalıştırabileceğiniz [Bul-DscResource] cmdlet'i. Bul-DscResource galeride bulunan DSC kaynaklardaki verileri döndürür.
DSC kaynakları her zaman bir modülün bir parçası olarak teslim edildiğinden, çalıştırmanız yine [Install-Module][] bu DSC kaynakları yüklenecek.

## <a name="learning-about-items-in-the-powershell-gallery"></a>PowerShell galeride bulunan öğeler hakkında daha fazla bilgi

İlgilendiğiniz öğeyi belirledikten sonra ilgili daha fazla bilgi edinmek isteyebilirsiniz. Bu öğenin özel galeri sayfasında inceleyerek bunu yapabilirsiniz. Bu sayfada tüm öğeyle karşıya meta verileri görmek mümkün olacaktır. Bu meta veriler için bir öğe öğenin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz. Öğenin sahibi kesin galeri öğesi yayımlamak için kullanılan hesaba bağlıdır ve yazar alanı daha güvenilirdir.

Sizin de böyle bir öğe inancıyla içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** bu öğeye ait sayfasında.

Çalıştırıyorsanız [Modül Bul][] veya [Bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verileri görüntüleyebilirsiniz. Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Galerideki PSReadLine modül verileri döndürür.

## <a name="downloading-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğe indirme

PowerShell Galerisi'nden öğe indirme işlemi gerçekleştirirken aşağıdaki işlem öneririz:

### <a name="inspect"></a>İnceleme

Galeri denetimi için bir öğe indirmesine izin ya da çalıştırmak [Save-Module][] veya [Save-Script][] cmdlet'i, öğe türüne bağlı olarak. Bu, yüklemeden öğe yerel olarak kaydedin ve öğe içeriği İnceleme sağlar. Kaydedilen öğeyi el ile silmeyi unutmayın.

Bu öğelerin bazıları, Microsoft tarafından yazılmış ve diğer PowerShell topluluğu tarafından yazıldı.
Microsoft, içeriği ve yüklemeden önce bu galeri öğeleri, kod gözden geçirme önerir.

Sizin de böyle bir öğe inancıyla içinde yayımlanmamışsa keşfederseniz tıklayın **uygunsuz** bu öğeye ait sayfasında.

### <a name="install"></a>Yükle

Galeri kullanmak için bir öğe yüklemek için ya da çalıştırmak [Install-Module][] veya [Yükleme betiği][] cmdlet'i, öğe türüne bağlı olarak.

[Install-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.
Bu, bir yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi modülünün yüklü için `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Yükleme betiği][] betiğe yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.
Bu, bir yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası yüklü olduğu için `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Varsayılan olarak, [Install-Module][] ve [Yükleme betiği][] öğenin en son sürümünü yükler.
Öğesi daha eski bir sürümünü yüklemek için ekleme `-RequiredVersion` parametresi.

### <a name="deploy"></a>Dağıt

Azure Otomasyonu PowerShell Galerisi'ndeki bir öğeye dağıtmak için **Azure Otomasyonu Dağıt** öğe Ayrıntıları sayfasında. Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum açtığınızda Azure yönetim portalına yönlendirilirsiniz. Bağımlılıkları olan öğeleri dağıtma tüm bağımlılıkları için Azure Otomasyonu dağıtacağınız olduğunu unutmayın. 'Azure otomasyonu için Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** öğesi meta verileriniz için etiket.

Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.

## <a name="updating-items-from-the-powershell-gallery"></a>Öğeleri PowerShell Galerisi'ndeki güncelleştiriliyor

Yüklü PowerShell Galerisi'nden öğeleri güncelleştirmek için Update-Module [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın. Update-Module [] herhangi ek bir parametre çalıştırdığınızda çalıştırarak yüklü her modülü güncelleştirme çalışır [Install-Module][]. Modüller seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.

Benzer şekilde, hiçbir ek parametre olmadan çalıştırdığınızda, [güncelleştirme betiğini] [] de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [Yükleme betiği][]. Komut dosyaları seçmeli olarak güncelleştirmek için ekleme `-Name` parametresi.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell Galerisi'nden yüklediğiniz liste öğeleri

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