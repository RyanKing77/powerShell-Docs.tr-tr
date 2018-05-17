---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Nano Server’da DSC Kullanma
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="using-dsc-on-nano-server"></a>Nano Server’da DSC Kullanma

> İçin geçerlidir: Windows PowerShell 5.0

**DSC Nano Server üzerinde** isteğe bağlı bir pakette `NanoServer\Packages` klasörü Windows Server 2016 medya. Belirterek Nano Server için bir VHD oluşturduğunuzda paket yüklenebilir **Microsoft NanoServer DSC paket** değeri olarak **paketleri** parametresinin **yeni NanoServerImage**  işlevi. Örneğin, bir sanal makineye ait bir VHD'ye oluşturuyorsanız, komut aşağıdaki gibi görünür:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Yükleme ve PowerShell uzaktan iletişimi Nano Server yönetme yanı sıra, Nano Server kullanma hakkında daha fazla bilgi için bkz: [Nano Server ile çalışmaya başlama](https://technet.microsoft.com/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>DSC özellikleri Nano Server üzerinde kullanılabilir

 Nano Server yalnızca sınırlı sayıda tam bir Windows Server sürümüne karşılaştırıldığında API'leri desteklediğinden, DSC Nano Server üzerinde tam işlevsel eşlik şimdilik tam SKU'ları üzerinde çalışan DSC ile yok. DSC Nano Server üzerinde etkin geliştirme ve henüz tam özelliği değil.

 Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir:


* Hem İtme hem de çekme modları

* Windows Server, aşağıdakiler dahil tam bir sürümünü mevcut tüm DSC cmdlet:
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [DscDebug devre dışı bırak](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Yayımlama DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Güncelleştirme DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Geri yükleme DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Çağırma DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Bul DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Derleme yapılandırmaları (bkz [DSC yapılandırmaları](configurations.md))

  **Sorun:** parola şifreleme (bkz [MOF dosyası güvenli hale getirme](securemof.md)) yapılandırması sırasında derleme çalışmıyor.

* Metaconfigurations derleme (bkz [yerel Configuration Manager Yapılandırma](metaConfig.md))

* Bir kaynak kullanıcı bağlamında çalışan (bkz [kullanıcı kimlik bilgileri (Farklı Çalıştır) ile çalışan DSC](runAsUser.md))

* Sınıf tabanlı kaynaklar (bkz [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](authoringResourceClass.md))

* DSC kaynakları, hata ayıklama (bkz [hata ayıklama DSC kaynakları](debugresource.md))

  **Sorun:** kaynak PsDscRunAsCredential kullanıyorsa, işe yaramazsa (bkz [çalıştıran DSC kullanıcı kimlik bilgileriyle](runAsUser.md))

* [Çapraz düğüm bağımlılıklarını belirtme](crossNodeDependencies.md)

* [Kaynak sürüm oluşturma](sxsResource.md)

* Çekme istemci (yapılandırmaları ve kaynakları) (bkz [yapılandırma adları kullanarak bir çekme istemcisi kurarken](pullClientConfigNames.md))

* [Kısmi yapılandırmaları (çekme ve itme)](partialConfigs.md)

* [Çekme sunucusuna raporlama](reportServer.md)

* MOF şifreleme

* Olay günlüğü

* Azure Otomasyonu DSC raporlama

* Tam olarak işlevsel kaynakları
  * [Arşiv](archiveResource.md)
  * [Ortamı](environmentResource.md)
  * [Dosya](fileResource.md)
  * [Günlük](logResource.md)
  * ProcessSet
  * [Kayıt defteri](registryResource.md)
  * [Komut dosyası](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))
  * WaitForAny (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))
  * WaitForSome (bkz [arası düğümlü bağımlılıkları belirtme](crossNodeDependencies.md))

* Kısmen işlev kaynakları
  * [Grup](groupResource.md)
  * GroupSet

  **Sorun:** kaynaklar başarısız belirli örneği iki kez çağrıldıysa (aynı yapılandırmayı iki kez çalışan)

  * [Hizmeti](serviceResource.md)
  * ServiceSet

  **Sorun:** yalnızca çalışır (durum) hizmeti başlatma/durdurma. Başarısız bir startuptype, kimlik bilgileri, açıklama vb. gibi diğer hizmeti öznitelikleri değiştirmeye çalışırsa.. Oluşturulan hata benzer:

  *Türü [management.managementobject] bulunamıyor: Bu türü içeren derlemenin yüklü olduğunu doğrulayın.*

* İşlev olmayan kaynaklar
  * [Kullanıcı](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>DSC özellikleri Nano sunucuda mevcut değil

Şu DSC özellikleri Nano Server üzerinde şu anda kullanılabilir değil:

* Şifrelenmiş parolası MOF belgeyle şifre çözme
* Çekme sunucusuna--şu anda Nano Server çekme sunucusunda ayarlayamazsınız
* Özellik works listede olmayan herhangi bir şey

## <a name="using-custom-dsc-resources-on-nano-server"></a>Nano sunucusunda özel DSC kaynakları kullanma

Windows API'ları ve CLR kitaplıkları Nano Server üzerinde kullanılabilir sınırlı bir kümelerini nedeniyle Windows tam CLR sürümü üzerinde çalışan DSC kaynakları, Nano Server üzerinde çalışmıyor.
DSC özel kaynakları üretim ortamına dağıtmadan önce uçtan uca test tamamlayın.

## <a name="see-also"></a>Ayrıca bkz:
- [Nano Server ile çalışmaya başlama](https://technet.microsoft.com/library/mt126167.aspx)