---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: PowerShell Galerisi ile çalışmaya başlama
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>PowerShell Galerisi ile çalışmaya başlama

Sisteminize PowerShell Galerisi'nden öğe indirme gerektirir [PowerShellGet](/powershell/module/powershellget) modülü. Aşağıdakilerden birini PowerShellGet modülü bulabilirsiniz. PowerShell Galerisi'nden öğe indirme oturum açmak gerekmez.

## <a name="discovering-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğeleri bulma

PowerShell galerisinde öğelerini kullanarak bulabilirsiniz **arama** denetim bu Web sitesinde veya modüller ve komut dosyaları sayfalarıyla giderek. PowerShell Galerisi'nden öğe çalıştırarak bulabileceğiniz [bulma Modülü][] ve [bulma komut dosyası][] cmdlet'leri ile öğe türüne bağlı olarak, `-Repository PSGallery`.

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

Yalnızca galerisinde belirli DSC kaynakları bulmak isterseniz, çalıştırabilirsiniz [Bul DscResource] cmdlet'i. Bul DscResource DSC kaynakları galeride yer alan verileri döndürür.
DSC kaynakları her zaman bir modül bir parçası olarak teslim edildiğinden, hala çalıştırmanız gereken [yükleme-Module][] bu DSC kaynakları yüklemek için.

## <a name="learning-about-items-in-the-powershell-gallery"></a>PowerShell galerisinde öğeleri hakkında bilgi

İlgilendiğiniz öğeyi tanımladıktan sonra hakkında daha fazla bilgi edinmek isteyebilirsiniz. Bu öğeye ait belirli galeri sayfasında inceleyerek bunu yapabilirsiniz. Bu sayfada tüm öğe ile karşıya meta verileri görmek mümkün olur. Bir öğe için bu meta veri öğesi'nin yazarı tarafından sağlanan ve Microsoft tarafından doğrulanmaz. Öğenin sahibi öğesini yayımlamak için kullanılan galeri hesabı kesinlikle bağlıdır ve yazar alanı daha güvenilirdir.

Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.

Çalıştırıyorsanız [bulma Modülü][] veya [bulma komut dosyası][], döndürülen PSGetModuleInfo nesnesinde bu verilerini görüntüleyebilir. Örneğin, çalışan `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` galerisinde PSReadLine modül verileri döndürür.

## <a name="downloading-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğe indirme

PowerShell Galerisi'nden öğe indirme sırasında şu işlem öneririz:

### <a name="inspect"></a>İnceleyin.

İnceleme için Galeriden bir öğe indirmek için ya da çalıştırın [Kaydet-Module][] veya [Kaydet-komut dosyası][] cmdlet öğesi türüne bağlı olarak. Bu, yüklemeden öğeyi yerel olarak kaydedin ve öğenin içeriğini incelemek sağlar. Kaydedilen öğeyi el ile silmek unutmayın.

Bu öğelerin bazıları, Microsoft tarafından yazılan ve diğerleri PowerShell topluluğu tarafından yazılan.
Microsoft, yüklemeden önce bu galeri öğeleri kodunu ve içeriğini gözden önerir.

Düşündüğünüz bir öğe iyi niyetli içinde yayımlanmamışsa bulursanız tıklatın **rapor kötüye** bu öğeye ait sayfasında.

### <a name="install"></a>Yükle

Kullanmak için Galeriden bir öğe yüklemek için ya da çalıştırın [yükleme-Module][] veya [yükleme betiği][] cmdlet öğesi türüne bağlı olarak.

[yükleme-Module][] modülünü yükler `$env:ProgramFiles\WindowsPowerShell\Modules` varsayılan olarak.
Bu yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi modülü için yüklüdür `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[yükleme betiği][] komut dosyasına yükler `$env:ProgramFiles\WindowsPowerShell\Scripts` varsayılan olarak.
Bu yönetici hesabı gerektirir. Eklerseniz `-Scope CurrentUser` parametresi, komut dosyası için yüklendiğini `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Varsayılan olarak, [yükleme-Module][] ve [yükleme betiği][] öğeyi en güncel sürümünü yükler.
Öğe daha eski bir sürümü yüklemek için add `-RequiredVersion` parametresi.

### <a name="deploy"></a>Dağıt

PowerShell Galerisi'nden bir öğe Azure Automation ile dağıtmak için **Azure Otomasyonu Dağıt** öğe Ayrıntıları sayfasında. Burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirilir. Bağımlılıkları olan öğeleri dağıtmak için Azure Otomasyonu tüm bağımlılıkları dağıtması unutmayın. 'Azure Otomasyonu Dağıt' düğmesini ekleyerek devre dışı bırakılabilir **AzureAutomationNotSupported** öğe meta etiketi.

Azure Otomasyonu hakkında daha fazla bilgi için bkz: [Azure Otomasyonu](/azure/automation) belgeleri.

## <a name="updating-items-from-the-powershell-gallery"></a>PowerShell Galerisi'nden öğeler güncelleştiriliyor

PowerShell Galerisi'nden yüklü öğeleri güncelleştirmek için [güncelleştirme-Module] [] veya [güncelleştirme betiğini] [] cmdlet'ini çalıştırın. Ek parametreler çalıştırdığınızda [güncelleştirme-Module] [] çalıştırarak yüklü her modülü güncelleştirme girişiminde [yükleme-Module][]. Modülleri seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.

Benzer şekilde, ek parametreler çalıştırdığınızda, [güncelleştirme betiğini] [] de her komut dosyası çalıştırarak yüklü güncelleştirme girişiminde [yükleme betiği][]. Komut dosyaları seçmeli olarak güncelleştirmek için ekleyin `-Name` parametresi.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>PowerShell Galerisi'nden yüklediğiniz liste öğeleri

PowerShell Galerisi'nden yüklü modüllerine öğrenmek için Çalıştır [Get-InstalledModule][] cmdlet'i. Bu komut tüm doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü modülleri listeler.

PowerShell Galerisi'nden yüklü hangi komut dosyaları bulmak için benzer şekilde, çalıştırmak [Get-InstalledScript][] cmdlet'i. Bu komut doğrudan PowerShell Galerisi'nden yüklenen sisteminizde yüklü komut dosyalarının tümü listeler.

[Bul DscResource]: /powershell/module/powershellget/Find-DscResource
[bulma Modülü]: /powershell/module/powershellget/Find-Module
[bulma komut dosyası]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[yükleme-Module]: /powershell/module/powershellget/Install-Module
[yükleme betiği]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Kaydet-Module]: /powershell/module/powershellget/Save-Module
[Kaydet-komut dosyası]: /powershell/module/powershellget/Save-Script