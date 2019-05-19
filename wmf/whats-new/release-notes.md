---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.x sürüm notları
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856402"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x sürüm notları

## <a name="wmf-50-changes"></a>WMF 5.0 değiştirir

- PowerShell 5.0 ekler yeni yapılandırılmış **bilgi** akış
- Dört yeni DSC kaynakları dahil olmak üzere DSC geliştirmeleri:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Eklenen yeterli rol tabanlı yönetim üzerinden PowerShell uzaktan iletişimini etkinleştirmek için Yönetim
- PowerShell 5.0 kullanıcı tanımlı sınıflar ve numaralandırmalar içerecek şekilde dili genişletir.
- Gelişmiş hata ayıklama PowerShell ISE ve eklenen uzaktan hata ayıklama özellikleri
- PowerShellGet ve PackageManagement modülleri eklendi
- PowerShell betiğini Gelişmiş günlüğe kaydetme ve dökümleri
- Şifreli ileti söz dizimi cmdlet'leri eklendi
- WMF 5.0 NetworkSwitchManager modülü için Windows içerir.
- Microsoft.PowerShell.ODataUtils modülü eklendi
- Yazılım envanteri günlüğü (SIL) için destek eklendi
- Yeni Sunucu veya kullanıcı talebi ve sorununa yanıt cmdlet'leri güncelleştir

## <a name="wmf-51-changes"></a>WMF 5.1 değiştirir

WMF 5.1, Windows Server 2016 ile yayımlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenleri içerir. WMF 5.1 yüklenebilmesi için Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2 ve WMF 5.0 şu gibi çeşitli iyileştirmeler sağlar:

- Yeni cmdlet'ler
- PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur
- PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi
- DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri
- PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri
- Birkaç kullanıcı talebi ve sorununa yanıt

## <a name="powershell-editions"></a>PowerShell Sürümleri

5.1 sürümünden itibaren PowerShell çeşitli özellik kümelerini ve platform uyumluluğunu belirten farklı sürümlerinde kullanıma sunulmuştur.

- **Masaüstü sürümü:** .NET Framework üzerine inşa edilmiş ve Windows Masaüstü ve Windows Server Core gibi tam boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek sürümü:** .NET Core üzerine yapılandırılan ve Nano Server gibi Windows ve Windows IOT azaltılmış boyutlu sürümlerinde çalışan PowerShell sürümlerinin hedeflendiği betikler ve modüllerle uyumluluk sağlar.

### <a name="learn-more-about-using-powershell-editions"></a>PowerShell sürümleri kullanma hakkında daha fazla bilgi edinin

- [$PSVersionTable kullanarak PowerShell'in çalışan sürümü belirleme](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Get-Module sonuçları PSEdition parametresini kullanarak CompatiblePSEditions göre filtrele](/powershell/module/microsoft.powershell.core/get-module)
- [Betik yürütme uyumlu bir PowerShell sürümünde çalıştırmadıkça engelle](/powershell/gallery/concepts/script-psedition-support)
- [Belirli PowerShell sürümleri için bir modülün uyumluluk bildirme](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Modül çözümleme önbellek

WMF 5.1 ile başlayarak, PowerShell, bunu aktarır komutlar gibi bir modülle ilgili verileri önbelleğe almak için kullanılan dosya üzerinde denetim sağlar.

Varsayılan olarak, bu önbelleğin dosyasında depolanan `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Önbellek başlatma sırasında bir komut için aranırken genellikle okuma ve bir modülü içeri aktardıktan sonra bir arka plan iş parçacığında süre yazılır.

Önbelleğinin varsayılan konumu değiştirmek için Ayarla `$env:PSModuleAnalysisCachePath` PowerShell başlatmadan önce ortam değişkeni. Bu ortam değişkeni yapılan değişiklikler, yalnızca alt işlemlerin etkiler. Değeri, PowerShell oluşturun ve dosyalarını yazma iznine sahip bir tam yol (dosya adı dahil) adlandırmanız gerekir. Dosya önbelleği devre dışı bırakmak için geçersiz bir konum için bu değeri örneğin ayarlayın:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Bu, geçersiz bir cihaza yolunu ayarlar. PowerShell yolu yazılamıyor, hata döndürülür, ancak hata raporlama bir izleyici kullanarak görebilirsiniz:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Önbelleği dışına yazılırken, PowerShell modülleri için artık gereksiz derecede büyük bir önbellek önlemek için mevcut kontrol eder. Bazen bu denetimler, bu durumda, bunları ayarlayarak kapatabilirsiniz, istenmez:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Bu ortam değişkenini ayarlayarak hemen geçerli işlemde etkili olur.

## <a name="specifying-module-version"></a>Modül sürümü belirtme

WMF 5.1 içinde `using module` PowerShell modülü ile ilgili diğer yapılarını aynı şekilde davranır.
Daha önce belirli bir modül sürümü belirtmek için imkanı yoktu; var olan birden çok sürüm varsa, bu hatayla sonuçlandı.

WMF 5.1:

- Kullanabileceğiniz [ModuleSpecification Oluşturucusu (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
  Bu karma tablosu olarak aynı biçimde `Get-Module -FullyQualifiedName`.

  **Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Birden çok modül sürümü varsa, PowerShell kullanan **aynı çözüm mantığı** olarak `Import-Module` ve bir hata--aynı davranışı döndürmüyor `Import-Module` ve `Import-DscResource`.

## <a name="improvements-to-pester"></a>Pester geliştirmeleri

WMF 5.1 Pester PowerShell ile birlikte gelen sürümünü 3.4.0 için 3.3.5 güncelleştirildi.
Bu güncelleştirme, Nano Sunucu'da Pester için daha iyi davranışını etkinleştirir.

İnceleyerek Pest değişiklikleri gözden geçirebilirsiniz [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) GitHub deposunda.
