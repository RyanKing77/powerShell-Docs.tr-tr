---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.x Sürüm Notları
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848146"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5. x sürüm notları

## <a name="wmf-50-changes"></a>WMF 5,0 değişiklikleri

- PowerShell 5,0 yeni bir yapılandırılmış **bilgi** akışı ekler
- Dört yeni DSC kaynağı da dahil olmak üzere DSC geliştirmeleri:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- PowerShell uzaktan iletişim yoluyla rol tabanlı yönetimi etkinleştirmek için yeterli yönetim eklendi
- PowerShell 5,0, dili Kullanıcı tanımlı sınıfları ve numaralandırmaları içerecek şekilde genişletir
- PowerShell ıSE 'de geliştirilmiş hata ayıklama özellikleri ve uzaktan hata ayıklama eklendi
- PowerShellGet ve PackageManagement modülleri eklendi
- Gelişmiş PowerShell betiği günlüğü ve dökümü
- Şifreleme Iletisi sözdizimi cmdlet 'leri Ekle
- WMF 5,0, Windows için NetworkSwitchManager modülünü içerir
- Microsoft. PowerShell. ODataUtils modülü eklendi
- Yazılım envanter günlüğü (SIL) için destek eklendi
- Kullanıcı isteklerine ve sorunlarına yanıt olarak yeni veya güncelleştirme cmdlet 'lerini sunucu

## <a name="wmf-51-changes"></a>WMF 5,1 değişiklikleri

WMF 5,1, Windows Server 2016 ile yayınlanan PowerShell, WMI, WinRM ve yazılım envanteri günlüğü (SIL) bileşenlerini içerir. WMF 5,1, Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 ve 2012 R2 'ye yüklenebilir ve aşağıdakiler de dahil olmak üzere WMF 5,0 üzerinde çeşitli geliştirmeler sağlar:

- Yeni cmdlet 'ler
- PowerShellGet iyileştirmeleri arasında imzalı modülleri zorlama ve JEA modülleri yükleme bulunur
- PackageManagement; Kapsayıcılar, CBS Kurulumu, EXE temelli kurulum ve CAD paketleri için destek ekledi
- DSC ve PowerShell sınıfları için hata ayıklama iyileştirmeleri
- PowerShellGet cmdlet’leri kullanırken Çekme Sunucusundan gelen katalog imzalı modülleri zorlamayı da içeren güvenlik iyileştirmeleri
- Birkaç kullanıcı talebi ve sorununa yanıt

> [!IMPORTANT]
> Windows Server 2008 veya Windows 7 ' de WMF 5,1 ' ü yüklemeden önce, WMF 3,0 ' nin yüklenmediğini doğrulayın. Daha fazla bilgi için bkz. [Windows Server 2008 R2 SP1 ve Windows 7 SP1 Için WMF 5,1 önkoşulları](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>PowerShell Sürümleri

Sürüm 5,1 ' den başlayarak, PowerShell, değişen özellik kümelerini ve platform uyumluluğunu gösteren farklı sürümlerde kullanılabilir.

- **Masaüstü sürümü:** .NET Framework oluşturulmuştur ve, Windows 'un sunucu çekirdeği ve Windows Masaüstü gibi tam parmak izi sürümlerinde çalışan PowerShell sürümlerini hedefleyen betikler ve modüllerle uyumluluk sağlar.
- **Çekirdek sürüm:** .NET Core üzerine kurulmuştur ve nano sunucu ve Windows IoT gibi Windows 'un azaltılmış ayak sürümleri üzerinde çalışan PowerShell sürümlerini hedefleyen betikler ve modüllerle uyumluluk sağlar.

### <a name="learn-more-about-using-powershell-editions"></a>PowerShell sürümlerini kullanma hakkında daha fazla bilgi edinin

- [$PSVersionTable kullanarak PowerShell 'in çalışan sürümünü belirleme](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [PSEdition parametresini kullanarak, Get-Module sonuçlarını CompatiblePSEditions ile filtreleyin](/powershell/module/microsoft.powershell.core/get-module)
- [PowerShell 'in uyumlu bir sürümünde çalıştırılmadığı takdirde betik yürütmeyi engelleyin](/powershell/gallery/concepts/script-psedition-support)
- [Belirli PowerShell sürümlerine bir modülün uyumluluğunu bildirin](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Modül Analizi önbelleği

WMF 5,1 ' den itibaren PowerShell, dışarı aktardığı komutlar gibi bir modülle ilgili verileri önbelleğe almak için kullanılan dosya üzerinde denetim sağlar.

Bu önbellek, varsayılan olarak dosyada `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`depolanır. Önbellek genellikle bir komut aranırken ve bir modül içeri aktarıldıktan sonra bir arka plan iş parçacığında yazıldığında başlangıçta okunurdur.

Önbelleğin varsayılan konumunu değiştirmek için, PowerShell 'i başlatmadan önce `$env:PSModuleAnalysisCachePath` ortam değişkenini ayarlayın. Bu ortam değişkeninde yapılan değişiklikler yalnızca alt süreçlerini etkiler. Bu değer, PowerShell 'in dosya oluşturma ve yazma iznine sahip olduğu bir tam yolu (filename dahil) olarak adı olmalıdır. Dosya önbelleğini devre dışı bırakmak için bu değeri geçersiz bir konuma ayarlayın, örneğin:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Bu, yolu geçersiz bir cihaza ayarlar. PowerShell yola yazamaz, hata döndürülmez, ancak izleyici kullanarak hata raporlamayı görebilirsiniz:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Önbellek yazılırken, PowerShell gereksiz bir büyük önbelleğinizi önlemek için artık mevcut olmayan modülleri denetlecektir. Bazen bu denetimler istenmez, bu durumda şunları yaparak devre dışı bırakabilirsiniz:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Bu ortam değişkeninin ayarlanması, geçerli işlemde hemen etkili olur.

## <a name="specifying-module-version"></a>Modül sürümünü belirtme

WMF 5,1 ' de `using module` , diğer modülle ilgili kurulumlarını PowerShell ile aynı şekilde davranır.
Daha önce, belirli bir modül sürümünü belirtmenin bir yolu yoktu; birden çok sürüm varsa, bu hata ile sonuçlanır.

WMF 5,1:

- [Modulespecification oluşturucusunu (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)kullanabilirsiniz.

  Bu karma tablo, ile `Get-Module -FullyQualifiedName`aynı biçimde.

  **Örnek:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Modülün birden çok sürümü varsa, PowerShell **aynı çözünürlükte mantığı** `Import-Module` kullanır ve bir hata döndürmez; `Import-Module` ve ile `Import-DscResource`aynı davranış.

## <a name="improvements-to-pester"></a>Pester geliştirmeleri

WMF 5,1 ' de, PowerShell ile birlikte gelen pester sürümü 3.3.5 ' den 3.4.0 ' ye güncelleştirilmiştir.
Bu güncelleştirme, nano sunucu 'da pester için daha iyi davranışı sunar.

GitHub deposundaki [changelog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) 'u Inceleyerek, Pest 'deki değişiklikleri inceleyebilirsiniz.
