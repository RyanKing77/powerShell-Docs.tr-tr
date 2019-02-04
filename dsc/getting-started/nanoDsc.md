---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Nano Server’da DSC Kullanma
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686589"
---
# <a name="using-dsc-on-nano-server"></a>Nano Server’da DSC Kullanma

> Şunun için geçerlidir: Windows PowerShell 5.0

**Nano Sunucu'da DSC** isteğe bağlı bir pakette `NanoServer\Packages` Windows Server 2016 medya klasörü. Belirterek bir Nano sunucu için bir VHD oluşturduğunuzda, paketin yüklenebilir **Microsoft-NanoServer-DSC-Package** değeri olarak **paketleri** parametresinin **New-Nanoserverımage**  işlevi. Örneğin, bir VHD için bir sanal makine oluşturuyorsanız, komut aşağıdaki gibi görünür:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Yükleme ve PowerShell uzaktan iletişimi ile Nano sunucuyu yönetmek nasıl yanı sıra, Nano Server'ı kullanma hakkında daha fazla bilgi için bkz: [Nano Server ile çalışmaya başlama](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>Nano Sunucu'da DSC Özellikler

Nano sunucu Windows Server'ın tam sürümüne kıyasla API'leri yalnızca sınırlı sayıda desteklediğinden, Nano Sunucu'da DSC tam işlevsel eşlik şimdilik tam SKU'ları üzerinde çalışan DSC ile yok. Nano Sunucu'da DSC active geliştirme aşamasındadır ve henüz tam bir özellik değil.

Şu DSC özellikler şu anda Nano Sunucu'da kullanılabilir:

Hem İtme hem de çekme modu

- Aşağıdakiler dahil olmak üzere Windows Server'ın tam sürümünde mevcut tüm DSC cmdlet'leri:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [DscDebug etkinleştir](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [DscDebug devre dışı bırak](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Yayımlama DscConfiguraiton](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Geri yükleme-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Bul-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Yapılandırmaları derleme (bkz [DSC yapılandırmaları](../configurations/configurations.md))

  **Sorun:** Parola şifrelemesini (bkz [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md)) derleme yapılandırması sırasında çalışmaz.

- Metaconfigurations derleme (bkz [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md))

- Kullanıcı bağlamı altında bir kaynak çalıştıran (bkz [kullanıcı kimlik bilgilerini (Farklı Çalıştır) ile çalışan DSC](../configurations/runAsUser.md))

- Sınıf tabanlı kaynaklar (bkz [PowerShell sınıfları ile özel bir DSC kaynağı yazma](../resources/authoringResourceClass.md))

- DSC kaynakları hata ayıklama (bkz [hata ayıklama DSC kaynakları](../troubleshooting/debugResource.md))

  **Sorun:** Bir kaynak PsDscRunAsCredential kullanıyorsa, işe yaramazsa (bkz [DSC çalıştıran kullanıcı kimlik bilgileriyle](../configurations/runAsUser.md))

- [Çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md)

- [Kaynak sürümü oluşturma](../configurations/sxsResource.md)

- Çekme istemcisi (yapılandırmaları ve kaynakları) (bkz [yapılandırma adlarını kullanarak çekme istemcisi ayarlama](../pull-server/pullClientConfigNames.md))

- [Kısmi yapılandırmalar (çekme ve itme)](../pull-server/partialConfigs.md)

- [Çekme sunucusuna raporlama](../pull-server/reportServer.md)

- MOF şifreleme

- Olay günlüğü

- Azure Automation DSC raporlama

- Tamamen işlevseldir, kaynakları

- **Arşiv**
- **Ortam**
- **Dosya**
- **Günlük**
- **ProcessSet**
- **kayıt defteri**
- **Komut dosyası**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))
- **WaitForAny** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))
- **WaitForSome** (bkz [çapraz düğüm bağımlılıklarını belirtme](../configurations/crossNodeDependencies.md))

- Kısmen işlevsel olan kaynaklar
- **Grup**
- **GroupSet**

  **Sorun:** Belirli bir örneği iki kez çağrılırsa üzerinde kaynak başarısız (aynı yapılandırmanın iki kez çalıştıran)

- **Hizmet**
- **ServiceSet**

  **Sorun:** Yalnızca çalışır (durum) hizmeti başlatma/durdurma. Bir başlangıç türü, kimlik bilgileri, açıklama vb. gibi diğer hizmet öznitelikleri değiştirmeye çalışırsa başarısız.. Söz konusu hata benzer:

  *[Management.managementobject] türü bulunamıyor: Bu tür içeren derlemenin yüklü olduğundan emin olun.*

- İşlevsel olmayan kaynaklar
- **Kullanıcı**

## <a name="dsc-features-not-available-on-nano-server"></a>DSC özelliklerini Nano Sunucu'da kullanılabilir değil

Şu DSC özellikler şu anda Nano Sunucu'da kullanılamaz:

- MOF belgesi şifrelenmiş parolası ile şifre çözme
- Çekme sunucusu--şu anda Nano Sunucu'da bir çekme sunucusu ayarlayamazsınız
- Özellik works listesinde değil herhangi bir şey

## <a name="using-custom-dsc-resources-on-nano-server"></a>Nano Sunucu'da özel DSC kaynakları kullanma

Windows API'ları ve kitaplıkları CLR Nano Sunucu'da kullanılabilir sınırlı kümesi nedeniyle Windows tam CLR sürümü üzerinde çalışan DSC kaynakları, Nano Sunucu'da çalışmaz.
Uçtan uca DSC özel kaynaklar herhangi bir üretim ortamına dağıtmadan önce test tamamlayın.

## <a name="see-also"></a>Ayrıca bkz:

- [Nano Server ile çalışmaya başlama](/windows-server/get-started/getting-started-with-nano-server)
