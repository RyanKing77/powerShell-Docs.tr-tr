---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 306241bc5ec854c0e2ed835009a79b21fc249f14
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-and-limitations"></a>Bilinen Sorunlar ve Sınırlamalar

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>İlk defa kullanıldığında PowerShell kısayolları bozuk
------------------------------------------------------------

**Çözüm:** aşağıdaki eylemlerden birini gerçekleştirin:

1.  PowerShell kısayolu sağ tıklatın. Yükseltilmiş olmayan modunda başlatmak için "Windows PowerShell" seçin.
2.  PowerShell kısayolu sağ tıklatın. "Windows PowerShell üzerinde" sağ tıklatın ve "Yönetici olarak çalıştır yükseltilmiş modda başlatmak için" seçin.

Yukarıdaki eylemlerden birini gerçekleştirdikten sonra PowerShell kısayolları çalışır. Bu eylem yalnızca bir kez gerçekleştirilmesi gerekir.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell modülleri ve DSC kaynakları hakkında hata ExecutionPolicy Windows 7
-------------------------------------------------------------------------------------
Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.

**Çözüm:** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak ExecutionPolicy RemoteSigned olarak ayarlayın:

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Eski bir uzak Exchange uç noktasına bağlanan bir kilitlenme neden olur.
------------------------------------------------------------

Eski Exchange uç noktası için yeni bir uç noktası yönlendirir. Bir hata varsa yeniden yönlendirme mantığında sonucu bir kilitlenme.

**Çözüm:** yeni uç noktası doğrudan bağlanın.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Windows Server 2012 R2 WMF 5.0 yüklemeden sonra yazılım envanter günlüğü özelliği yanlışlıkla durduruldu
-------------------------------------------------------------------------------------------------------------

Bir Windows Server 2012 SIL zaten çalışmakta olan R2 üzerinde WMF 5.0 yükleme sırasında yazılım envanter günlüğü özelliği yanlışlıkla yüklendikten sonra durduruldu.

**Çözüm:** yükleme işlemini errantly yazılım envanter günlüğü özelliği durduracak şekilde kez WMF yüklendikten sonra Start-SilLogging cmdlet'ini çalıştırın.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-Childıtem - LiteralPath ve - Recurse birlikte kullanılan çalışmaz
--------------------------------------------------------------------------

Ardından bir dizin adı geçersiz joker karakter içeriyorsa, - LiteralPath hem - Recurse birlikte kullanıldığında Get-Childıtem beklenen sonuçları oluşturmaz.

**Çözüm:** değil ideal, ancak geçerli geçici bir çözüm değildir yerine özyineleme komut dosyasında uygulamak için cmdlet'ini kullanır.


<a name="sysprep-fails-after-wmf-50-installation"></a>WMF 5.0 yüklendikten sonra Sysprep başarısız
----------------------------------------

Çalıştırdığınız Windows Server sürümüne bağlı olarak bu sorunun iki geçici çözüm yoktur.

**Çözüm:**
- Çalışan sistemler için **Windows Server 2008 R2**
  1. Yönetici olarak PowerShell'i açın
  2. Aşağıdaki komutu çalıştırın

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Komutunu çalıştırın ve bunlar beklendiği gibi hatayı yok sayıp.

  ```powershell
    Publish-SilData
   ```
  4. \Windows\System32\Logfiles\SIL\ dizindeki dosyaları sil

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Kullanılabilir tüm önemli Windows güncelleştirmeleri yüklemek ve Sysyprep işlemi normalde başlayın.

- Çalışan sistemler için **Windows Server 2012**
  1.    WMF 5.0 olabilir sunucuya yükledikten sonra Sysprep'd, yönetici olarak oturum açın.
  2.    Generize.XML dizin \Windows\System32\Sysprep\ActionFiles\ C:\ Windows dizini dışındaki bir konuma örneğin kopyalayın.
  3.    Generalize.xml kopyanızı not defteri ile açın.
  4.    Bulma ve aşağıdaki metni, silinmesi gerekiyor her bir örneğini kaldırma (belgenin sonuna olacaktır).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Generalize.xml düzenlenen kopyasını dosyasını kaydedin ve kapatın.
  6.    Yönetici olarak bir komut istemi açın
  7.    System32 klasöründe Generalize.xml dosya sahipliğini almak için aşağıdaki komutu çalıştırın:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Dosyayı uygun izni ayarlamak için aşağıdaki komutu çalıştırın:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Evet komut isteminde onay yanıtı.
      * Unutmayın `<AdministratorUserName>` makinedeki yöneticisi olan kullanıcı adı ile değiştirilmelidir. Örneğin, "Yönetici".

  9.    Düzenlenen ve üzerinde aşağıdaki komutu kullanarak Sysprep'i dizinine kaydedilir dosyasını kopyalayın:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * (Üzerine yazmak için hiçbir istemi ise girilen yolunu kontrol edin unutmayın) üzerine yazmak için Evet'i yanıtlayın.
      * Düzenlenen Generalize.xml kopyanızı C:\ için kopyalanan varsayar.

  10.   Generalize.xml geçici çözüm ile güncelleştirilmiştir. Lütfen Sysprep etkin generalize seçeneği ile çalıştırın.