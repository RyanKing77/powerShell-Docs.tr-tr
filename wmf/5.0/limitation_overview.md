---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892993"
---
# <a name="known-issues-and-limitations"></a>Bilinen Sorunlar ve Sınırlamalar

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>İlk kez kullanıldığında PowerShell kısayolları bozuk

**Çözüm:** aşağıdaki eylemlerden birini gerçekleştirin:

1. Sağ PowerShell kısayolunun tıklayın. Yükseltilmiş olmayan modunda başlatmak için "Windows PowerShell" seçin.
2. Sağ PowerShell kısayolunun tıklayın. "Windows PowerShell üzerinde" sağ tıklayıp "Yönetici olarak çalıştır bir yükseltilmiş modda başlatmak için" seçin.

Yukarıdaki işlemleri gerçekleştirdikten sonra PowerShell kısayolları çalışır. Bu Eylemler, yalnızca bir kez gerçekleştirilmesi gerekir.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell modülleri ve DSC kaynakları hataları hakkında ExecutionPolicy Windows 7'de raporlar.

Windows 7'de PowerShell modülleri ve DSC kaynakları ExecutionPolicy hakkında rapor edilen hata neden olabilir.

**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak ExecutionPolicy RemoteSigned olarak ayarlayın:

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Kilitlenmeye neden olan eski bir uzak Exchange uç noktasına bağlanma

Eski değişimi uç noktası, yeni bir uç noktasına yönlendirir. Bir hata olduğunu yeniden yönlendirme mantığının bu sonuçları içindeki bir kilitlenme.

**Çözüm:** yeni uç nokta doğrudan bağlanın.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Windows Server 2012 R2'de WMF 5.0 yüklemeden sonra yazılım envanter günlüğü özelliği deneyebileceğinizi durduruldu

WMF 5.0 bir Windows Server 2012 önceden SIL çalıştıran R2 üzerinde yükleme sırasında yazılım envanter günlüğü özelliği deneyebileceğinizi yüklemeden sonra durdurulur.

**Çözüm:** yükleme işlemi, yazılım envanter günlüğü özelliği errantly durduracak şekilde kez WMF yükleme işleminden sonra Start-SilLogging cmdlet'ini çalıştırın.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` -LiteralPath ve - Recurse birlikte kullanılması durumunda çalışmıyor

Bir dizin adı bir geçersiz joker karakter içeriyorsa `Get-ChildItem` - LiteralPath hem - Recurse birlikte kullanıldığında beklenen sonuçları oluşturmaz.

**Çözüm:** ideal değildir, ancak geçerli bir geçici çözüm etmektir özyineleme betikte uygulamak yerine cmdlet'ini kullanır.

## <a name="sysprep-fails-after-wmf-50-installation"></a>WMF 5.0 yüklemeden sonra Sysprep başarısız

Çalıştırmakta olduğunuz Windows Server sürümüne bağlı olarak bu sorunun iki geçici çözüm yoktur.

**Çözüm:**

- Çalışan sistemler için **Windows Server 2008 R2**
  1. Yönetici olarak PowerShell'i açın
  2. Aşağıdaki komutu çalıştırın

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. Komutunu çalıştırın ve bunlar beklendiği gibi hatayı yoksayın.

     ```powershell
     Publish-SilData
     ```

  4. \Windows\System32\Logfiles\SIL\ dizindeki dosyaları sil

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Tüm kullanılabilir önemli Windows güncelleştirmelerini yükleyin ve normalde Sysyprep işlemi başlar.

- Çalışan sistemler için **Windows Server 2012**
  1. WMF 5.0 olması için sunucuda yükledikten sonra Sysprep'd, yönetici olarak oturum açın.
  2. Generize.XML dizin \Windows\System32\Sysprep\ActionFiles\ C:\ Windows dizini dışındaki bir konuma örneğin kopyalayın.
  3. Generalize.xml kopyanızı notepad ile açın.
  4. Bulma ve aşağıdaki metni, silinmesi gerekiyor her bir örneğini kaldırma (belgenin sonuna olacaktır).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Düzenlenen Generalize.xml kopyasını kaydedin ve dosyayı kapatın.
  6. Yönetici olarak bir komut istemi açın
  7. System32 klasöründe Generalize.xml dosyanın sahipliğini almak için aşağıdaki komutu çalıştırın:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Dosyayı uygun izni ayarlamak için aşağıdaki komutu çalıştırın:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Evet, onay isteminde yanıtlayın.
     - Unutmayın `<AdministratorUserName>` makinede yönetici olan bir kullanıcı adı ile değiştirilmelidir. Örneğin, "Yönetici".

  9. Düzenlenebilir ve üzerinde aşağıdaki komutu kullanarak Sysprep'i dizine kaydedilen dosyayı kopyalayın:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - (Üzerine yazmak için herhangi bir istem ise çift girilen yol denetleyin unutmayın) üzerine yazmak için Evet olarak yanıtlayın.
     - Düzenlenen Generalize.xml kopyanızın C:\ için kopyalanan varsayar.

  10. Geçici çözüm ile generalize.XML güncellenir. Lütfen generalize seçeneği etkinken Sysprep'i çalıştırın.