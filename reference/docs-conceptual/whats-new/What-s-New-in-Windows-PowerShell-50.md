---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 5.0 yenilikler
ms.openlocfilehash: b2cb729948d4b53c5ea9a536dbeda04c7cb50997
ms.sourcegitcommit: 9194e603ac242ae733839eb773e4af7360fdd044
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59363539"
---
# <a name="whats-new-in-windows-powershell-50"></a>Windows PowerShell 5.0 yenilikler

Windows PowerShell 5.0 kullanımını genişleten, kullanılabilirliğini iyileştiren ve şekilde denetlemenizi ve Windows tabanlı ortamları daha kolay ve kapsamlı bir şekilde yönetmenizi, önemli yeni özellikler içerir.

Windows PowerShell 5.0 geriye dönük olarak uyumludur. Cmdlet'leri, sağlayıcıları, modüller, ek bileşenler, betikleri, işlevleri ve Windows PowerShell 4.0, Windows PowerShell 3.0 ve Windows PowerShell 2.0 için genel olarak tasarlanmış profilleri Windows PowerShell 5. 0'değişikliğe gerek kalmadan çalışır.

## <a name="installing-windows-powershell"></a>Windows PowerShell Yükleme

Windows PowerShell 5.0, Windows Server 2016 Technical Preview ve Windows 10 üzerinde varsayılan olarak yüklenir.

Windows Server 2012 R2, Windows 8.1 Enterprise veya Windows 8.1 Pro Windows PowerShell 5.0 yüklemek için indirme ve yükleme [Windows Management Framework 5.0](https://aka.ms/wmf5download). İndirme ayrıntıları okuyun ve Windows Management Framework 5.0 yüklemeden önce tüm sistem gereksinimlerini karşılamak emin olun.

## <a name="in-this-topic"></a>Bu konuda,

- [BB 3000850 Windows PowerShell 4.0 DSC güncelleştirmeleri](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Windows PowerShell 5.0 yeni özellikler](#new-features-in-windows-powershell-50)
- [Windows PowerShell 4. 0'ı yeni özellikler](#new-features-in-windows-powershell-40)
- [Windows PowerShell 3. 0'ı yeni özellikler](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Windows PowerShell 4.0 güncelleştirmeleri Kasım 2014 güncelleştirme paketi (KB 3000850)

Birçok güncelleştirme ve geliştirmeleri için Windows PowerShell Desired State Configuration (DSC) Windows PowerShell 4. 0'ı kullanılabilir [Windows RT 8.1, Windows 8.1 ve Windows Server 2012 R2 için Kasım 2014 güncelleştirme paketi](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). BB 3000850 sisteminizde çalıştırarak yüklü olup olmadığını belirlemek `Get-Hotfix -Id KB3000850` Windows PowerShell'de.

- Mevcut cmdlet'ler için güncelleştirmeler [da PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) Modülü
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) (özellikle ISE) daha hızlıdır.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) - son uygulanan yapılandırma yeniden uygular, UseExisting, yeni bir parametresi vardır.
  - [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) -Force düzeltildi.
  - [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx) motoru durumu hakkında daha faydalı bilgiler görüntüler.
  - [Test-DscConfiguration](https://technet.microsoft.com/library/dn407382.aspx) artık doğru veya yanlış yanı sıra bilgisayar adını döndürür.
  - [Yeni DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) artık UNC yollarını desteklemektedir.

- Yeni cmdlet'ler [da PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) Modülü
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx):  Bir isteğe bağlı çekme sunucusu denetimi gerçekleştirir.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx):  Zaten çalışan bir yapılandırma durdurur.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx):  Yapılandırma belgelerini (Bekleyen, önceki veya geçerli) çeşitli aşamalarda kaldırmanıza olanak sağlar.

- Dil iyileştirmeleri
  - DependsOn bileşik kaynakları artık desteklemektedir.
  - DependsOn, artık sayıları kaynak örnek adlarını destekler.
  - Artık değerlendirmek için boş düğüm ifadeleri hataları atar.
  - Bir düğüm ifadesi boş olarak değerlendirilirse oluşan hata düzeltildi.
  - Windows PowerShell konsolunda yapılandırmalar artık çağırma yapılandırmaları çalışır.

- Çekme modu geliştirmeleri
  - Çekme modu, artık tüm ZIP dosyalarını destekler.
  - **AllowModuleOverwrite** artık düzgün şekilde çalışır.

- Dayanıklılık geliştirmeleri
  - Yeni **DebugMode** kaynak modülleri yeniden olanak sağlar.
  - Bir yapılandırma hatası meydana gelirse, pending.mof dosya silinmez.
  - Metaconfiguration ayarları bozulmuş, yerel Configuration Manager (LCM) artık daha esnektir.

- Tanılama geliştirmeleri
  - LCM belirtilenden farklı ayarlar Zamanlayıcıyı ayarlar bir uyarı görüntülenir.
  - Hata günlük dosyaları, artık Windows PowerShell kaynaklar için çağrı yığını içerir.

- Esneklik geliştirmeleri
  - Yeni bir özellik LocalConfigurationManager kaynakta yok **ActionAfterReboot**.
    - ContinueConfiguration (varsayılan değer): Bir hedef düğümü yeniden başlatıldıktan sonra yapılandırma otomatik olarak sürdürür.
    - StopConfiguration: Otomatik olarak bir yapılandırma, bir düğümü yeniden başlatıldıktan sonra devam.
  - Tutarlılık çalıştırma artık bir ÇEKME işlemi ya da tam tersi çok sık gerçekleşebilir.
  - Sürüm oluşturma desteği:  DSC daha yeni bir istemci üzerinde oluşturulmuş bir belge artık algılayabilir (birlikte [WMF 5.0](https://aka.ms/wmf5download)).

- Hata önleme geliştirmeleri
  - Bir yapılandırma uygulanmadan önce Modül sürümü artık uygulanmaz.
  - **DebugPreference** artık doğru şekilde Get-, Set- veya Test TargetResource aramalar için ayarlanır.

- Kimlik bilgisi işleme geliştirmeleri
  - Sertifika artık, her iki kullanıldığında **sertifika** ve **PSDscAllowPlainTextPassword** belirtilir.
  - Kimlik bilgileri, bile Get-TargetResource için şifresi çözülür.
  - Metaconfiguration kimlik bilgileri şifrelenir ve şifresi çözülür.
  - Katıştırılmış nesne olduklarında PSCredentials artık şifresi çözülür.

- Yerleşik kaynak geliştirmeleri
  - Package kaynağı
    - Artık yanlış paketi yükler (yerel uygulamasından veya web kaynaklarını).
    - Artık HTTPS destekler.
  - HTTPS için artık destek [paket kaynak](https://technet.microsoft.com/library/dn282132.aspx).
  - [Kaynak arşiv](https://technet.microsoft.com/library/dn249917.aspx) artık kimlik bilgilerini destekler.

## <a name="new-features-in-windows-powershell-50"></a>Windows PowerShell 5.0 yeni özellikler

- [Windows PowerShell'de yeni özellikler](#new-features-in-windows-powershell)
- [Windows PowerShell Desired State Configuration ' deki yeni özellikler](#new-features-in-windows-powershell-desired-state-configuration)
- [Windows PowerShell ıse'de yeni özellikler](#new-features-in-windows-powershell-ise)
- [Windows PowerShell Web Hizmetleri yenilikleri](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Windows PowerShell 5.0 önemli hata düzeltmeleri](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Windows PowerShell'de yeni özellikler

- Windows PowerShell 5.0 ile başlayarak, sınıflar, biçimsel sözdizimi ve diğer nesne yönelimli programlama dillerinde benzer semantiği kullanarak geliştirebilirsiniz. **Sınıf**, **Enum**, ve diğer anahtar sözcükleri yeni özelliği desteklemek için Windows PowerShell dil sürümüne eklenmiştir. About_Classes sınıfları ile çalışma hakkında daha fazla bilgi için bkz.

- Windows PowerShell 5.0, bir komut dosyası ve çağıranlar (veya barındırma ortamı) arasındaki yapılandırılmış veri aktarmak için kullanabileceğiniz bir yeni, yapılandırılmış bilgi akışı sunar. Write-Host artık bilgi akışına çıkış yaymak için de kullanabilirsiniz. Bilgi akışları da PowerShell.Streams, işler, zamanlanmış işler ve iş akışları için çalışır. Bilgi akışı aşağıdaki özellikleri destekler.
  - Windows PowerShell komutu için akış veri bilgileri nasıl işlediğini belirtmenize olanak sağlar. yeni bir yazma bilgi cmdlet. Write-Host yazma bilgi bir sarmalayıcıdır. Yazma-ayrıca desteklenen bir iş akışı etkinlik bilgilerdir.
  - İki yeni ortak parametreleri Informationvariable ve Informationaction, bir komut bilgileri akışlardan nasıl görüntüleneceğini belirlemenize olanak tanır. SilentlyContinue, durdurma, devam et, Inquire, Yoksay veya askıya alma, varsayılan olan SilentlyContinue ile Informationaction için geçerli değerlerdir. Informationvariable bir dize olarak kaydedilmiş bir komut Write-Host verilerinden istediğiniz değişken adını belirtir.
  - Yeni tercih değişkeni, InformationPreference, varsayılan tercihinizi bilgi veri akışı için bir Windows PowerShell oturumunda belirtir. SilentlyContinue varsayılan değerdir.
  - İki yeni iş akışı ortak parametreleri PSInformation ve Informationaction, sürümüne eklenmiştir.
  - Format-Table komutunu kullandığınızda, tablo sütunları artık otomatik olarak akış geçen veri ilk 300ms değerlendirerek biçimlendirilir.

- İşbirliği ile [Microsoft Research](https://research.microsoft.com/), ConvertFrom-dize, yeni bir cmdlet eklendi. ConvertFrom-dize çıkarma ve metin dizelerini içeriğini yapılandırılmış nesnelerden sağlar. Daha fazla bilgi için bkz: ConvertFrom-dize.
- Yeni dize dönüştürme cmdlet örnek parametresi sağladığınız örneği temel metin otomatik olarak biçimlendirir.
- Dosyaları sıkıştır sağlayan cmdlet'ler Microsoft.PowerShell.Archive, yeni bir modül içerir ve klasörler halinde (ZIP olarak da bilinir) arşiv dosyaları ZIP dosyaları var olan dosyaları ayıklayın ve bunları sıkıştırılmış dosya daha yeni sürümleriyle ZIP dosyalarını güncelleştirme.
- PackageManagement, yeni bir modül, bulma ve Internet'te yazılım paketlerini yükleme sağlar. PackageManagement (önceki adıyla OneGet da bilinir) Yöneticisi'ni veya var olan paket yöneticileri (paket sağlayıcıları olarak da bilinir) çoğaltıcı tek bir Windows PowerShell arabirimine sahip Windows paket Yönetimi buluşturulan modülüdür.
- PowerShellGet, yeni bir modülü bulma, yükleme, yayımlama ve güncelleştirme modülleri ve DSC kaynakları üzerinde sağlar [PowerShell Galerisi](https://www.powershellgallery.com/), veya bir iç modül deposunda, Register-PSRepository cmdlet çalıştırılarak ayarlayabilirsiniz.
- Yeni bir dil anahtar kelimesi **gizli**, bir üye (bir özellik veya yöntem), Get-Member sonuçlarında varsayılan olarak gösterilmez belirtmek için eklendi (eklediğiniz sürece - Force parametresi). Üye görünür olması gereken yerde bağlamında olmadığı sürece özellikleri veya gizli olarak işaretlenmiş bir yöntem aynı zamanda IntelliSense sonuçlarında gösterilmez; Örneğin, otomatik değişken $bu sınıf yöntemi, gizli üyeleri göstermelidir.
- Yeni öğe, öğe kaldırma ve Get-Childıtem oluşturma ve yönetme desteklemek için Gelişmiş [simgesel bağlantılar](https://en.wikipedia.org/wiki/Symbolic_link). **- Itemtype** yeni öğe için parametre kabul eder, yeni bir değer **SymbolicLink**. Artık yeni öğe cmdlet'ini çalıştırarak tek bir satırda simgesel bağlantılar oluşturabilirsiniz.
- Get-Childıtem de sahip yeni - Depth parametresi özyineleme sınırlamak için ile Recurse parametresini kullanın. Örneğin, Get-Childıtem-Recurse - derinliği 2 sonuçları klasörlerin geçerli klasörde geçerli klasördeki tüm alt klasörlerde ve tüm alt klasörlerde döndürür.
- Artık, dosyaları veya klasörleri bir Windows PowerShell oturumundan diğerine kopyalama, uzak bir bilgisayara bağlı oturuma dosyalarını kopyalayabilirsiniz anlamı sağlar Copy-Item (çalıştıran bilgisayarlar da dahil olmak üzere [Nano sunucu](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), ve Bu nedenle herhangi bir arabirim sahip). Dosyaları kopyalamak için PSSession kimlikleri yeni - FromSession ve - ToSession parametrelerinin değeri belirtin ve - Path ve - kaynak yolu belirtmek için hedef ve hedef, sırasıyla ekleyin. Örneğin, Copy-Item-c: yol\\myFile.txt - ToSession $s-hedef d:\\destinationFolder.
- Konsol konağı yanı sıra tüm barındırma uygulamalarının (örneğin, Windows PowerShell ISE) uygulamak için Windows PowerShell transkripsiyonu geliştirildi (**powershell.exe**). (Bir sistem genelinde döküm etkinleştirme dahil) transkripsiyon seçenekleri sağlayarak yapılandırılabilir **PowerShell Transkripsiyonu kapatma** Grup İlkesi ayarı, Yönetim Şablonları/Windows bileşenleri/Windows içinde bulunamadı PowerShell.
- Yeni bir betik ayrıntılı izleme özelliği, ayrıntılı izleme ve çözümleme sisteminde Windows PowerShell komut dosyası kullanımı etkinleştirmenize olanak tanır. Ayrıntılı betik izlemeyi etkinleştirdikten sonra Windows PowerShell tüm betik bloklarını olay izleme için Windows (ETW) olayı günlüğe kaydeder. **Microsoft-Windows-PowerShell/Operational**.
- Windows PowerShell 5.0 ile başlayarak, yeni şifreli ileti söz dizimi cmdlet'leri şifreleme ve şifre çözme içeriğin şifreli olarak iletileri tarafından belirtildiği gibi korumak için IETF standart biçimi kullanarak desteklemek [RFC5652](https://tools.ietf.org/html/rfc5652). Get-CmsMessage ve Koru-CmsMessage Unprotect-CmsMessage cmdlet'leri eklenmiş [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx) modülü.
- Yeni cmdlet'ler [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modülü, Get-çalışma, hata ayıklama çalışma, Get-RunspaceDebug, RunspaceDebug etkinleştirme ve devre dışı bırak-RunspaceDebug, bir çalışma alanı ve başlatılması ve durdurulması hata ayıklama seçeneklerini ayarlamanızı sağlar bir çalışma alanı üzerinde hata ayıklama. İsteğe bağlı çalışma alanları (bir Windows PowerShell konsolu veya Windows PowerShell ISE oturumu için varsayılan çalışma olmayan diğer bir deyişle, çalışma alanları) hata ayıklama için Windows PowerShell bir betikte kesme noktaları ayarlayın ve kesme noktaları durdurun betikten eklediğiniz olanak sağlar Çalışma alanı hataları ayıklamak için bir debugger iliştirebilmek için kadar çalışıyor. Çalışma alanları için Windows PowerShell komut dosyası hata ayıklayıcı rastgele çalışma alanları için iç içe geçmiş hata ayıklama desteği eklendi.
- Yeni biçimi onaltılık cmdlet eklendi [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modülü. Onaltılık biçiminde metin veya ikili veri onaltılık biçimde görüntülemenize olanak tanır.
- Pano get ve Set-Pano cmdlet'leri eklenmiştir [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modülü; bunlar için ve bir Windows PowerShell oturumundan içerik aktarımını kolaylaştırır. Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listeler ve metin destekler.
- Clear-geridönüşüm kutusu, yeni bir cmdlet eklendi [Microsoft.PowerShell.Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx) modülü; Geri Dönüşüm Kutusu'nu dış sürücüleri içeren bir sabit sürücü için bu boşaltır cmdlet'i. Cmdlet Confirmımpact özelliği için ConfirmImpact.High olarak ayarlandığından varsayılan olarak, bir düz geridönüşüm kutusu komutu onaylamanız istenir.
- Yeni cmdlet, New-TemporaryFile, betik oluşturma işleminin parçası olarak geçici bir dosya oluşturmanıza olanak sağlar. Varsayılan olarak, yeni bir geçici dosya içinde oluşturulan ```C:\Users\<user name>\AppData\Local\Temp```.
- Çıktıdan sonra yeni bir satır atlar yeni - NoNewline parametresi Out-File, içerik ekleyin ve Set-Content cmdlet'leri artık var.
- Yeni GUID cmdlet betikleri veya DSC kaynakları yazarken yararlı bir GUID oluşturmak için .NET Framework GUID sınıfı yararlanır.
- Özellikle dosya uygulandıktan sonra dosya sürümü bilgilerini yanıltıcı olabilir bu nedenle, yeni FileVersionRaw ve ProductVersionRaw betik özellikleri FileInfo nesneler için kullanılabilir. Örneğin, burada $pid çalışan bir Windows PowerShell oturumu için işlem Kimliğini içeren için powershell.exe, bu özelliklerin değerlerini görüntülemek için aşağıdaki komutu çalıştırabilirsiniz:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- Yeni cmdlet'ler Enter PSHostProcess ve çıkış PSHostProcess Windows PowerShell betikleri Windows PowerShell konsolunu çalıştıran geçerli işleminden ayrı işlemlerde hata ayıklamanıza olanak tanır. Girin veya bir özel işlem kimliği için eklemek için ENTER-PSHostProcess çalıştırın ve sonra etkin çalışma alanları işlemde döndürülecek Get-çalışma çalıştırın. İşiniz bittiğinde işlemdeki betik hata ayıklama işlemden ayırmak için çıkış-PSHostProcess çalıştırın.
- Yeni bir bekleme hata ayıklayıcı cmdlet'i eklendi [Microsoft.PowerShell.Utility](https://technet.microsoft.com/library/hh849958.aspx) modülü. Sonraki deyim komut dosyasını çalıştırmadan önce bir betikte hata ayıklayıcıyı durdurmak için bekleme-hata ayıklayıcı çalıştırabilirsiniz.
- Windows PowerShell iş akışı hata ayıklayıcısını artık komutu veya sekme tamamlama destekler ve iç içe geçmiş iş akışı işlevleri ayıklayabilirsiniz. Artık basabilirsiniz **Ctrl + Break** hata ayıklayıcı, çalışan bir komut dosyası, hem yerel hem de uzak oturumlar ve bir iş akışı betiği girmek için.
- Hata ayıklama işi cmdlet'i eklendi [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx) Windows PowerShell iş akışı, arka plan ve uzak oturumlarında çalışan işler çalışan iş betikleri hata ayıklamak için modülü.
- Yeni bir durum AtBreakpoint, Windows PowerShell işleri için eklendi. Kesme noktaları belirleyin içeren bir betiği bir iş çalışırken AtBreakpoint durumu uygular ve betik, bir kesme noktası isabet. Bir işi hata ayıklama kesme noktasında durdurulduğu zaman hata ayıklama işi cmdlet'ini çalıştırarak bu işin hatalarını gerekir.
- Windows PowerShell 5.0 $PSModulePath aynı klasörde birden çok sürümünü tek bir Windows PowerShell modülü için destek uygular. Bir RequiredVersion özelliği bir modülün istenen sürümünü almak amacıyla ModuleSpecification sınıfı eklenmiştir; Bu özellik ModuleVersion özelliği ile birbirini dışlayan. Get-Module, karşılık gelen fullyqualifiedname öğesi parametresinin değeri bir parçası olarak RequiredVersion desteklenen artık Import-Module ve Remove-Module cmdlet'leri.
- Artık Test ModuleManifest cmdlet'ini çalıştırarak modülü sürüm doğrulama gerçekleştirebilirsiniz.
- Get-Command cmdlet'inin sonuçlarını, sürüm sütununda artık görüntüler; Yeni bir sürüm özelliği CommandInfo sınıfı eklendi. Get-Command birden çok sürümünü aynı modülde komutları gösterir. Version özelliği ayrıca CmdletInfo türetilmiş sınıfları parçasıdır: CmdletInfo ve ApplicationInfo.
- Get-Command - PSObjects ShowCommand bilgileri döndürür ShowCommandInfo, yeni bir parametre vardır. Bu Windows PowerShell uzaktan iletişimi kullanarak, Show komutunu Windows PowerShell ISE'de çalıştırdığınızda için kullanışlı bir işlevdir. -ShowCommandInfo parametre Microsoft.PowerShell.Utility modülünde mevcut Get-SerializedCommand işlevi değiştirir ancak Get-SerializedCommand betik alt düzey komut dosyasını destekleyen hala kullanılabilir.
- Yeni cmdlet Get-ItemPropertyValue noktalı gösterim kullanmadan bir özelliğin değerini almanıza olanak tanır. Örneğin, Windows PowerShell daha eski sürümleri, uygulama tabanı özelliği PowerShellEngine kayıt defteri anahtarının değerini almak için aşağıdaki komutu çalıştırabilirsiniz: **(Get-Itemproperty-yolu HKLM:\\yazılım\\Microsoft\\PowerShell\\3\\PowerShellEngine-ad ApplicationBase). ApplicationBase**. Çalıştırabileceğiniz Windows PowerShell 5.0 ile başlayarak, **ItemPropertyValue Get-yolu HKLM:\\yazılım\\Microsoft\\PowerShell\\3\\PowerShellEngine-adı ApplicationBase öğesi** .
- Windows PowerShell konsolu, artık söz dizimi renklendirme, yalnızca Windows PowerShell ISE olduğu gibi kullanır.
- Yeni bir NetworkSwitch modülü, Windows Server 2012 R2 logo sertifikalı ağ anahtarları için anahtar ve sanal LAN (VLAN) temel Katman 2 ağ anahtarı bağlantı noktası yapılandırması uygulamanıza imkan sağlayan cmdlet'ler içerir.
- Karşılık gelen fullyqualifiedname öğesi parametresi, tek bir modülün birden çok sürümünü saklama desteklemek için Import-Module ve Remove-Module cmdlet'leri eklendi.
- Save-Help, Update-Help, Import-PSSession, Export-PSSession ve Get-Command FullyQualifiedModule, ModuleSpecification türünde yeni bir parametre vardır. Bir modül tarafından tam olarak nitelenmiş adını belirtmek için bu parametreyi ekleyin.
- Değerini **$PSVersionTable.PSVersion** 5.0 güncelleştirildi.
- WMF 5.0 (PowerShell 5.0) içeren **Pester** modülü.  Pester olan bir birim testi çerçevesi için PowerShell. Bu komut dosyalarınız için testler oluşturmanıza olanak tanıyan birkaç basit kullanımı anahtar sözcükleri sağlar.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration ' deki yeni özellikler

- Windows PowerShell dil iyileştirmeleri sınıflarını kullanarak Windows PowerShell Desired State Configuration (DSC) kaynakları tanımlamanıza olanak sağlar. Import-DscResource true dinamik bir anahtar sözcüğü sunulmuştur; Windows PowerShell DscResource özniteliği içeren sınıflar için arama belirtilen modülün kök modül ayrıştırır. Artık, hangi ne bir MOF dosyası ya da modül klasöründe bir DSCResource alt gerekli değil, DSC kaynakları tanımlamak için sınıflar da kullanabilirsiniz. Bir Windows PowerShell modülü dosyası birden çok DSC kaynak sınıfları içerebilir.
- Şu cmdlet'lere da PSDesiredStateConfiguration modülünde ThrottleLimit, yeni bir parametre eklendi. Hedef bilgisayarları veya cihazları komutu aynı anda çalışmak istediğiniz sayısını belirtmek için ThrottleLimit parametresini ekleyin.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Geri yükleme-DscConfiguration
  - Test-DscConfiguration
  - COMPARE-DscConfiguration
  - Yayımlama-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Olay günlüğü, ancak daha sonra analiz için merkezi bir konuma gönderilebilir merkezi DSC hata raporlama ile zengin hata bilgileri yalnızca günlüğe kaydedilmez. DSC yapılandırması ortamlarında herhangi bir sunucu için oluşan bir hata depolamak için bu merkezi bir konum kullanabilirsiniz. Rapor sunucusu meta yapılandırmasında tanımlandıktan sonra tüm hataları rapor sunucusuna gönderilen ve ardından bir veritabanında saklanır. Bir çekme sunucusu yapılandırmaları çekmek için hedef düğümü yapılandırılmış olup olmadığına bakılmaksızın bu işlevselliği ayarlayabilirsiniz.
- Windows PowerShell ISE kolayca DSC kaynağı yazma geliştirmeleri. Şimdi aşağıdakileri yapabilirsiniz.
  - İçindeki tüm DSC kaynakları listesinden bir **yapılandırma** veya **düğüm** girerek blok **Ctrl + boşluk** bloğu içinde boş bir satıra.
  - Kaynak özellikleri otomatik tamamlama **numaralandırma** türü.
  - Otomatik Tamamlama üzerinde **DependsOn** DSC kaynakları, diğer kaynak örnekleri yapılandırma temel özelliğidir.
  - Geliştirilmiş sekme tamamlama kaynak özellik değerleri.
- Kullanıcı artık belirtilen kimlik bilgileri kümesi altında bir kaynak ekleyerek çalıştırabilirsiniz **PSDscRunAsCredential** özniteliği için bir düğüm bloğu. Örneğin, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Bu işlevsellik, Windows Installer ve yürütülebilir yükleyicileri çalıştırmak, kullanıcı başına kayıt defteri kovanı erişmek veya geçerli kullanıcı bağlamı dışında diğer görevleri gerçekleştirmek yapılandırmaları oluşturmak için kullanışlıdır.
- 32-bit (x86 tabanlı) desteği için eklenmiştir **yapılandırma** anahtar sözcüğü.
- Windows PowerShell artık ekleyerek tanımlanan DSC yapılandırmaları için özel bir Yardım için destek içerir \[CmdletBinding()] oluşturulan yapılandırmayı işlevi.
- Yeni bir **DscLocalConfigurationManager** özniteliği bir meta-DSC Local Configuration Manager'ı yapılandırmak için kullanılan yapılandırma, bir yapılandırma bloğu belirler. Bu öznitelik, DSC Local Configuration Manager yapılandırma öğelerini içeren bir yapılandırma kısıtlar. İşlem sırasında yapılandırmanın oluşturduğu bir \*. uygun hedef düğümler için Set-DscLocalConfigurationManager cmdlet'i çalıştırarak gönderilir oluşturduğunuzdan dosya.
- Kısmi yapılandırmalar artık Windows PowerShell 5. 0 ' izin verilir. Yapılandırma belgelerini parçaları bir düğüme sunabilir. Bir düğüm yapılandırmasını belgenin birden çok parçaya almak düğümün yerel Configuration Manager beklenen parçaları belirtmek için önce ayarlanmalıdır
- Bilgisayarlar arası eşitleme, Windows PowerShell 5.0 DSC yenidir. Yerleşik WAITFOR kullanarak\* kaynakları (**WaitForAll**, **WaitForAny**, ve **WaitForSome**), bilgisayarlar arasında bağımlılıklar artık belirtebilirsiniz yapılandırma işlemleri sırasında dış düzenlemeler olmadan. Bu kaynaklar, WS-Man protokolü üzerinden CIM bağlantıları kullanarak düğümden düğüme eşitleme sağlar. Bir yapılandırma için başka bir bilgisayarın belirli kaynak durumunu değiştirmek bekleyebilirsiniz.
- Yalnızca yeterli yönetim (JEA), yeni bir temsilci güvenlik özelliği, DSC yararlanır ve Windows PowerShell kısıtlı çalışma alanları kasıtlı veya yanlışlıkla veri kaybı veya güvenlik ihlali çalışanlar tarafından güvenli kullanmasına yardımcı olacak. JEA xJEA DSC kaynak indirebileceğiniz dahil olmak üzere hakkında daha fazla bilgi için bkz. [yeterli yönetim, adım adım](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).
- Da PSDesiredStateConfiguration Modülü aşağıdaki yeni cmdlet eklendi.
  - Yeni cmdlet Get-DscConfigurationStatus hedef düğüm yapılandırma durumu hakkında üst düzey bilgileri alır. Durum edinebilirsiniz son veya tüm yapılandırmalar.
  - Yeni bir karşılaştırma-DscConfiguration cmdlet'i belirtilen bir yapılandırma bir veya daha fazla hedef düğümleri gerçek durumuyla karşılaştırır.
  - Yeni bir Yayımla-DscConfiguration cmdlet'i bir yapılandırma MOF dosyasının hedef düğüme kopyalar, ancak yapılandırma geçerli değildir. Yapılandırma, sonraki tutarlılık geçişi sırasında veya Update-DscConfiguration cmdlet'i çalıştırdığınızda uygulanır.
  - Yeni bir Test-DscConfiguration cmdlet'i, sonuçta elde edilen yapılandırma gerçek yapılandırmasını istenen eşleşmiyorsa istenen yapılandırma veya yanlış yapılandırma eşleşmesi durumunda ya da True döndüren bir istenen yapılandırma eşleştiğini doğrulayın olanak tanır yapılandırma.
  - Yeni bir güncelleştirme-DscConfiguration cmdlet'i işlenmek üzere bir yapılandırma zorlar. Yerel Configuration Manager çekme modunda ise, cmdlet uygulamadan önce çekme sunucusundan yapılandırmasını alır.

### <a name="new-features-in-windows-powershell-ise"></a>Windows PowerShell ıse'de yeni özellikler

- Artık uzak Windows PowerShell betikleri ve dosyaları bu Windows PowerShell ISE'yi yerel bir kopyasını düzenlemek istediğiniz dosyaları depolamak bilgisayarda Uzak oturumu başlatmak için Enter-PSSession çalıştıran ve ardından çalıştırarak düzenleyebilirsiniz **PSEdit \<uzak bilgisayardaki yolunu ve dosya adı\>**. Bu özellik, Windows PowerShell ISE çalıştırdığı olamaz, Windows Server'ın Sunucu Çekirdeği yükleme seçeneğini üzerinde depolanan düzenleme Windows PowerShell dosyaları kolaylaştırır.
- Başlangıç döküm cmdlet, Windows PowerShell ISE'de artık desteklenmektedir.
- Şimdi uzak Windows PowerShell ISE'de betiklerde hata ayıklaması yapabilirsiniz.
- Yeni bir menü komutu **tümünü Kes** hem yerel hem de uzaktan çalışan betikler için hata ayıklayıcısına (Ctrl + B) keser.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Yeni özellikler Windows PowerShell Web Hizmetleri (Management OData IIS uzantısı)

- Windows PowerShell 5.0 ile başlayarak, Windows PowerShell cmdlet'leri yeni bulunan dışarı aktarma ODataEndpointProxy cmdlet'ini çalıştırarak belirli bir OData uç tarafından sunulan işlevselliği göre bir dizi oluşturabilirsiniz [ Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modülü.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Windows PowerShell 5.0 önemli hata düzeltmeleri

- Windows PowerShell 5.0 COM nesneleriyle çalışırken önemli performans geliştirmeleri sunan yeni bir COM uygulamasını içerir. Etkisi video gösterimi için bkz. [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Sekme tamamlama süresi yaklaşık 500 ms tarafından kısaltmayı ilk sekme tamamlama bir Windows PowerShell oturumunda önemli performans geliştirmeleri yapılmıştır.

## <a name="new-features-in-windows-powershell-40"></a>Windows PowerShell 4. 0'ı yeni özellikler

Windows PowerShell 4.0 geriye dönük olarak uyumludur. Cmdlet'leri, sağlayıcıları, modüller, ek bileşenler, betikleri, işlevleri ve Windows PowerShell 3.0 ve Windows PowerShell 2.0 için tasarlanmış olan profilleri Windows PowerShell 4. 0'değişikliğe gerek kalmadan çalışır.

Windows PowerShell 4.0, Windows 8.1 ve Windows Server 2012 R2 üzerinde varsayılan olarak yüklenir. Windows 7 SP1 veya Windows Server 2008 R2 ile Windows PowerShell 4.0 sürümünü yüklemek için indirme ve yükleme [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). İndirme ayrıntıları okuyun ve Windows Management Framework 4.0 yüklemeden önce tüm sistem gereksinimlerini karşılamak emin olun.

- [Windows PowerShell'de yeni özellikler](#new-features-in-windows-powershell-1)
- [Yeni özellikler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Yeni Windows PowerShell iş akışı özellikleri](#new-features-in-windows-powershell-workflow)
- [Windows PowerShell Web Hizmetleri yenilikleri](#new-features-in-windows-powershell-web-services)
- [Windows PowerShell Web Erişimi'nde yeni özellikler](#new-features-in-windows-powershell-web-access)
- [Windows PowerShell 4. 0'ı önemli hata düzeltmeleri](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0, aşağıdaki yeni özellikler içerir.

### <a name="a-namenew-features-in-windows-powershell-1-new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Windows PowerShell'de yeni özellikler

- **Windows PowerShell Desired State Configuration** (DSC), dağıtımını ve yazılım hizmetleri ve bu hizmetlerin çalıştırıldığı ortam için yapılandırma verilerini yönetimini sağlayan Windows PowerShell 4.0 yeni bir yönetim sistemidir. DSC hakkında daha fazla bilgi için bkz: [Windows PowerShell Desired State Configuration ile'çalışmaya başlama](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- **Save-Help** şimdi uzak bilgisayarlara yüklü modüller için Yardım tasarruf sağlar. Save-Help modül Yardım (üzerinde tüm Yardım istediğiniz modüllerini mutlaka yüklenir) bir İnternet'e bağlı istemcisinden yükleyin ve ardından uzak, paylaşılan bir klasöre veya İnternet'e sahip olmayan bir uzak bilgisayar kaydedilmiş Yardım kopyalamak için kullanabilirsiniz erişim.
- Windows PowerShell hata ayıklayıcı, Windows PowerShell iş akışlarının yanı sıra uzak bilgisayarlarda çalıştırılan betikler, hata ayıklamaya izin verecek şekilde geliştirilmiştir. Windows PowerShell iş akışları artık Windows PowerShell komut satırından veya Windows PowerShell ISE betik düzeyinde ayıklanabilir. Windows PowerShell komut dosyaları, komut dosyası iş akışları dahil olmak üzere artık Uzak Oturumlar ayıklanabilir. Uzaktan hata ayıklama oturumlarında, bağlantısı kesilmiş ve sonraki kesilince Windows PowerShell uzak oturum korunur.
- A **RunNow** parametresi için **Register-ScheduledJob** ve **Set-ScheduledJob** kullanarakbirhemenbaşlangıçtarihivesaatiişleriiçinayarlanacakihtiyacınıortadankaldıran**Tetikleyici** parametresi.
- **Invoke-RestMethod** ve **Invoke-WebRequest** şimdi üstbilgiler parametresini kullanarak tüm üst bilgilerini ayarlayacak sağlar. Bu parametre her zaman mevcut olsa da, özel durumlar veya hata ile sonuçlandı web cmdlet'leri için birkaç parametrelerinden biri oldu.
- **Get-Module** yeni bir parametreye sahip **karşılık gelen fullyqualifiedname öğesi**, türün **ModuleSpecification\[]**. **Karşılık gelen fullyqualifiedname öğesi** parametresi Get-Module artık bir modül modülün adı, sürüm ve isteğe bağlı olarak, bunun GUID'sini kullanarak belirtmenizi sağlar.
- Windows Server 2012 R2'de varsayılan yürütme İlkesi ayarı **RemoteSigned**. Windows 8.1 üzerinde varsayılan ayarı değişiklik yoktur.
- Windows PowerShell 4.0 başlayarak, dinamik yöntem adlarını kullanarak yöntem çağırma desteklenmiyor. Bir yöntem adı depolamak için bir değişken kullanın ve değişkeni çağrılarak yöntemi dinamik olarak çağırır.
- Zaman aşımı süresi, tarafından belirtildiğinde, zaman uyumsuz iş akışı işleri silinmiş artık **PSElapsedTimeoutSec** iş akışı ortak parametresi geçti.
- Yeni bir parametre **RepeatIndefinitely**, eklenmiş **New-JobTrigger** ve **Set-JobTrigger** cmdlet'leri. Bu belirtme ihtiyacını ortadan kaldıran bir **TimeSpan.MaxValue** değerini **RepetitionDuration** zamanlanmış bir iş belirsiz bir süre için tekrar tekrar çalıştırmak için parametre.
- A **Passthru** parametresi eklendi **Enable-JobTrigger** ve **devre dışı bırak-JobTrigger** cmdlet'leri. Passthru parametresini oluşturulan veya değiştirilen komutunuz tarafından tüm nesneleri görüntüler.
- Bir çalışma grubu belirtmek için parametre adları **Add-Computer** ve **Remove-Computer** cmdlet'leri tutarlı şimdi. Her iki cmdlet de artık ilgili parametreyi kullanın **ÇalışmaGrubuAdı**.
- Yeni bir ortak parametre **PipelineVariable**, eklendi. İşlem hattı geri kalanı ile geçirilebilir bir değişken olarak PipelineVariable, yöneltilen komutu (veya piped komutun bir parçası) sonuçlarını kaydetmek sağlar.
- Bir yöntem sözdizimi kullanarak filtreleme koleksiyonu artık desteklenmez. Bu, artık nesnelerinin bir koleksiyonunu Basitleştirilmiş söz dizimi, benzer Where() veya Where-Object, bir yöntem çağrısının biçimlendirilmiş kullanarak filtreleyebilirsiniz, anlamına gelir. Bir örnek verilmiştir: (Get-işlem) .where ({$_. Adı - eşleşen 'powershell'})
- **Get-Process** cmdlet'i yeni bir anahtar parametresi olan **IncludeUserName**.
- Yeni bir cmdlet **Get-FileHash**, dosyayı belirtilen dosya için çeşitli biçimlerden birinde döndürür, eklendi.
- Windows PowerShell 4.0 modülü kullanıyorsa, **DefaultCommandPrefix** kendi bildirimindeki anahtar veya kullanıcı ile bir modülü içeri aktarırsa **önek** parametresi **ExportedCommands**modülünün özelliği önekiyle modüldeki komutlar gösterir. Modül adı Modül tam sözdizimini kullanarak komutlar çalıştırıldığında\\CommandName, komut adlarını ön ekini içermelidir.
- Değerini **$PSVersionTable.PSVersion** 4.0 için güncelleştirilmiştir.
- **Birlikte WHERE()** işleci davranışı değişti. `Collection.Where('property -match name')` Biçim string ifadesinde kabul `"Property -CompareOperator Value"` artık desteklenmiyor. Ancak, **Where()** işleci bir scriptblock biçimde dize ifadeleri kabul eder; Bu hala desteklenmektedir.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Yeni özellikler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE)

- Windows PowerShell ISE hem Windows PowerShell iş akışı hata ayıklama hem de uzaktan hata ayıklamayı destekler.
- Windows PowerShell Desired State Configuration sağlayıcıları ve yapılandırmalar için IntelliSense desteği eklendi.

### <a name="new-features-in-windows-powershell-workflow"></a>Yeni Windows PowerShell iş akışı özellikleri

- Destek eklendi. yeni bir **PipelineVariable** olanlar gibi yinelemeli işlem hatları bağlamında ortak parametresi System Center Orchestrator tarafından kullanılan; diğer bir deyişle, yalnızca soldan sağa, başlangıcı yerine sonundan komutları çalıştıran işlem hatları Akış'ı kullanarak çalışan karışık olarak kullanıldı.
- Parametre bağlaması, geçerli çalışma alanında var olmayan komutları gibi sekme tamamlama senaryoları dışında çalışacak şekilde önemli ölçüde geliştirilmiştir.
- Windows PowerShell iş akışına özel kapsayıcı etkinlikleri için destek eklendi. Bir etkinlik parametre türleri ise **etkinlik**, **etkinlik\[]** (veya genel bir etkinlikler koleksiyonudur) ve kullanıcı bağımsız değişken olarak, ardından Windows PowerShell komut dosyası bloğu yayımlamış İş akışı komut dosyası bloğu normal olarak Windows PowerShell komut dosyası iş akışı derleme ile XAML için dönüştürür.
- Kilitlenme sonrasında, Windows PowerShell iş akışı yönetilen düğümlere otomatik olarak yeniden bağlanır.
- Artık kısıtlama **Foreach-paralel** kullanarak etkinlik deyimleri **ThrottleLimit** özelliği.
- **ErrorAction** ortak parametrenin yeni geçerli bir değer **askıya alma**, yani yalnızca iş akışları için.
- Hiçbir etkin oturumları, devam eden işlerden ve bekleyen iş varsa bir iş akışı uç noktası artık otomatik olarak kapanır. Bu özellik otomatik kapatma koşullar karşılandığında iş akışı sunucusu olarak hareket eden bilgisayardaki kaynak kullanımını azaltır.

### <a name="new-features-in-windows-powershell-web-services"></a>Windows PowerShell Web Hizmetleri yenilikleri

- Windows PowerShell Web Hizmetleri (PSWS, ayrıca çağrılan Management OData IIS uzantısı), bir hata oluştuğunda bir cmdlet çalışıyor, ayrıntılı hata iletilerini çağırana döndürülür. Ayrıca, hata kodlarını izleyin [Windows Azure REST API'si hata kodu yönergeleri](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- Bir uç nokta artık API sürümü tanımlamak yanı belirli bir API sürümü kullanımı zorla. İstemci ile sunucu arasında sürüm uyuşmazlığı meydana geldiğinde, hatalar için istemci ve sunucu görüntülenir.
- Yönetim gönderme şemasının şemada tüm eksik alanlar için değerleri otomatik olarak oluşturarak basitleştirilmiştir. Gönderme şema mevcut olsa bile oluşturma, faydalı bir başlangıç noktası olarak gerçekleşir.
- Türü içinde PSWS işleme benzer şekilde davrandığından tarafından varsayılan oluşturucu değerinden farklı bir oluşturucu kullanan türlerini destekleyecek şekilde geliştirildi **pstypeconverter'ı** Windows PowerShell'de. Bu karmaşık türler ile PSWS kullanmanıza olanak sağlar.
- Sorgu çalıştırılırken ilişkili bir örnek genişletme PSWS artık sağlar. Büyük ikili içeriği (örneğin, görüntüleri, ses veya video) aktarımı maliyeti önemli olduğu ve kodlamadan ikili veri aktarımı daha iyidir. PSWS kodlamadan aktarmak için adlandırılmış kaynağı akışları kullanır. Adlandırılmış bir kaynak akışı, bir varlığın özelliğidir **Edm.Stream** türü. Her adlandırılmış bir kaynak akışı, GET veya güncelleştirme işlemleri için ayrı bir URI'ya sahip.
- OData eylemleri, artık kaynakta olmayan CRUD (oluşturma, okuma, güncelleştirme ve silme) yöntemlerini çağırma için bir mekanizma sağlar. Bir eylem için eylem tanımlanan URI HTTP POST isteği göndererek çağırabilirsiniz. Eylem parametrelerini POST isteğinin gövdesi içinde tanımlanır.
- Windows Azure yönergeleri ile tutarlı olması için tüm URL'leri Basitleştirilmiş. Bir değişikliğin dahil **anahtarı olarak Segment** parçaları olarak gösterilemeyecek kadar tek anahtarlarına izin verir. Birden çok anahtar değerlerinde başvurular parantez gösterimde, virgülle ayrılmış değerler önceki gibi gerektirdiğine dikkat edin.
- PSWS, bu sürümünden önce yolu oluşturma, güncelleştirme veya silme gerçekleştirme işlemleri yalnızca Post çağırmak için Put veya üzerinde üst düzey bir kaynakla silin. Yeni PSWS bu sürümünde, kullanıcılar aynı kaynak bu kaynakları yer alacağı yaklaşan daha az doğrudan ulaşmasını sırasında aynı sonuçları elde etmek yer alan kaynak işlemleri sağlar.

### <a name="new-features-in-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi'nde yeni özellikler

- Bağlantısını kesmek ve Windows PowerShell Web erişimi web tabanlı konsolunda mevcut oturumlar için yeniden bağlayın. A **Kaydet** web tabanlı konsolunda düğmesi sayesinde silmeden bir oturumun bağlantısını kesmek ve başka bir oturuma yeniden zaman.
- Oturum açma sayfasında varsayılan parametreleri görüntülenebilir. Varsayılan parametreleri görüntülemek için görüntülenen tüm ayarları için değerleri yapılandırma **isteğe bağlı bağlantı ayarları** alanını adlı bir dosya içinde oturum açma sayfasının **web.config**. Kullanabileceğiniz **web.config** ikinci veya alternatif kimlik bilgileri kümesi dışında tüm isteğe bağlı bağlantı ayarlarını yapılandırmak için bir dosya.
- Windows Server 2012 R2'de Windows PowerShell Web erişimi için yetkilendirme kuralları uzaktan yönetebilirsiniz. **Add-PswaAuthorizationRule** ve **Test-PswaAuthorizationRule** cmdlet'ler artık uzak bir bilgisayardan veya yetkilendirme kurallarını yönetme olanağı sağlayan bir kimlik bilgisi parametresi içeren bir Windows PowerShell Web erişimi oturumu.
- Ayrıca, her oturum için yeni bir tarayıcı sekmesi kullanarak tek tarayıcı oturumunda birden çok Windows PowerShell Web erişimi oturumu artık sahip olabilir. Artık web tabanlı Windows PowerShell konsolunda yeni bir oturum bağlanmak için yeni bir tarayıcı oturumu açmanız gerekir.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Windows PowerShell 4. 0'ı önemli hata düzeltmeleri

- **Get-Counter** Fransızca Windows sürümleri bir kesme işareti karakteri sayaçları artık döndürebilir.
- Artık görüntüleyebilirsiniz **GetType** seri durumdan çıkarılmış nesne yöntemi.
- **#Requires** deyimleri gerekirse yönetici erişim hakları gerektiren kullanıcılar artık sağlar.
- **Alma Csv** cmdlet artık boş satırlar yok sayar.
- Burada Windows PowerShell ISE kullanan çok fazla bellek çalıştırırken bir sorun bir **Invoke-WebRequest** komutu düzeltildi.
- **Get-Module** modülü sürümlerde artık görüntüler bir **sürüm** sütun.
- Remove-öğesi - Recurse şimdi beklendiği gibi bu öğeleri alt klasörlerdeki kaldırır.
- A **kullanıcıadı** özelliği eklendi **Get-Process** çıkış nesneleri.
- **Invoke-RestMethod** cmdlet artık tüm kullanılabilir sonuçları döndürür.
- **Üye Ekle** artık alıyor olmalarına rağmen etkisi hashtable'da değil henüz erişilmiş bile.
- **Select-Object - genişletin** artık başarısız olursa veya özelliğinin değeri null veya boş ise bir özel durum oluşturur.
- **Get-Process** alma diğer komutlarla işlem hattında artık kullanılabilir **ComputerName** nesnelerden özelliği.
- **ConvertTo-Json** ve **ConvertFrom-Json** çift tırnak içindeki terimler artık kabul edebilir ve hata iletilerini yerelleştirilebilir sunulmuştur.
- **Get-Job** artık herhangi bir tamamlanmış zamanlanmış işler, hatta yeni bir oturum döndürür.
- Bağlama ve VHD çıkarma kullanarak sorunları **dosya sistemi** Windows PowerShell 4. 0'ı sağlayıcısı düzeltilmiştir. Windows PowerShell artık aynı oturumda bağlı oldukları zaman yeni sürücüler algılayabilir.
- Artık açıkça yüklemek gerekmez **ScheduledJob** veya **iş akışı** kendi işlem türleriyle çalışmak için modüller.
- İç içe geçmiş iş akışları tanımlamak iş akışlarını içeri aktarma işlemi için performans geliştirmeleri yapılmıştır; Bu işlem artık daha hızlıdır.

## <a name="new-features-in-windows-powershell-30"></a>Windows PowerShell 3. 0'ı yeni özellikler

Windows PowerShell 3.0, aşağıdaki yeni özellikler içerir.

- [Windows PowerShell iş akışı](#windows-powershell-workflow)
- [Windows PowerShell Web Erişimi](#windows-powershell-web-access)
- [Yeni Windows PowerShell ISE Özellikleri](#new-windows-powershell-ise-features)
- [Microsoft .NET Framework 4.0 desteği](#support-for-microsoft-net-framework-4)
- [Windows önyükleme ortamı için destek](#support-for-windows-preinstallation-environment)
- [Oturumlara](#disconnected-sessions)
- [Güçlü oturum bağlantısı](#robust-session-connectivity)
- [Güncelleştirilebilir Yardımı](#updatable-help-system)
- [Gelişmiş çevrimiçi Yardım](#enhanced-online-help)
- [CIM tümleştirme](#cim-integration)
- [Oturum yapılandırma dosyaları](#session-configuration-files)
- [Zamanlanmış işleri ve Görev Zamanlayıcı'yı tümleştirme](#scheduled-jobs-and-task-scheduler-integration)
- [Windows PowerShell dil iyileştirmeleri](#windows-powershell-language-enhancements)
- [Yeni çekirdek cmdlet'leri](#new-core-cmdlets)
- [Var olan çekirdek cmdlet'leri ve sağlayıcıları geliştirmeleri](#improvements-to-existing-core-cmdlets-and-providers)
- [Uzak modül içeri aktarma ve bulma](#remote-module-import-and-discovery)
- [Gelişmiş sekme tamamlama](#enhanced-tab-completion)
- [Modül otomatik yükleme](#module-auto-loading)
- [Modül deneyimi geliştirmeleri](#module-experience-improvements)
- [Basitleştirilmiş komut bulma](#simplified-command-discovery)
- [Gelişmiş günlük kaydı, tanılama ve Grup İlkesi desteği](#improved-logging-diagnostics-and-group-policy-support)
- [Biçimlendirme ve çıkış geliştirmeleri](#formatting-and-output-improvements)
- [Gelişmiş konsol konak deneyimi](#enhanced-console-host-experience)
- [Yeni Cmdlet ve API'ler barındırma](#new-cmdlet-and-hosting-apis)
- [Performans iyileştirmeleri](#performance-improvements)
- [Farklı Çalıştır ve paylaşılan konak desteği](#runas-and-shared-host-support)
- [Özel karakter işleme geliştirmeleri](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell iş akışı

Windows PowerShell iş akışı Windows Workflow Foundation'ın gücünü, Windows PowerShell'e getirir. İş akışları XAML veya Windows PowerShell dilde yazabilir ve bir cmdlet çalıştırırken çalıştırabilirsiniz. [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i iş akışı komutlar alır ve [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet'i iş akışları için Yardım alır.

Uzun süre çalışan, yinelenebilir, sık sık, paralelleştirilebilir, kesilebilir, suspendable ve yeniden başlatılabilir multicomputer Yönetimi etkinlik iş akışlarıdır. İş akışları, ağ kesintisi, Windows yeniden başlatma veya güç kesintisi gibi bir kasıtlı olarak veya yanlışlıkla kesinti gelen sürdürülebilir.

İş akışları da taşınabilir; Bunlar olarak dışarı veya içeri aktarılan XAML dosyaları. Temsilci veya bağımlı kullanıcılar tarafından çalıştırılacak bir iş akışındaki iş akışı ve etkinlikleri sağlayan özel oturum yapılandırmaları yazabilirsiniz.

Windows PowerShell iş akışı avantajları şunlardır:

- Sıralı, uzun süre çalışan görevleri otomatikleştirme.
- **Uzaktan izleme uzun soluklu görevlerin**. Herhangi bir zamanda, durum ve ilerlemesini etkinlikleri görülebilir.
- **Multicomputer yönetimi.** Aynı anda görevlerini yüzlerce yönetilen düğüme iş akışları olarak çalıştırın. Windows PowerShell iş akışı içeren yerleşik bir kitaplık ortak yönetim parametrelerinin gibi **PSComputerName**, çoklu bilgisayar yönetimi senaryoları etkinleştirin.
- **Karmaşık işlemleri tek bir görev yürütme.** Tek bir iş akışı tüm uçtan uca senaryo uygulayan ilgili betikleri birleştirebilirsiniz.
- **Kalıcılık.** : bir iş akışı kaydedildi (onay işaret iş akışını baştan yeniden başlatmak yerine son kalıcı görevden (veya Denetim) akışından devam edebilmek için yazar tarafından tanımlanan belirli noktalarda veya).
- **Robustness.** Otomatik hatadan kurtarma. İş akışları, planlı ve plansız başlatmalarda. İş akışı yürütmeyi askıya almak ve sonra iş akışı son Kalıcılık noktadan devam. İş akışı yazarları, hata durumunda bir veya daha fazla yönetilen düğümde yeniden çalıştırılması için belirli etkinlikleri belirleyebilirsiniz.
- **Bağlantıyı kesmek için özelliği yeniden bağlayın ve bağlantısı kesilmiş oturumlarında çalışan.** Kullanıcılar bağlanır ve iş akışı sunucu bağlantısını kesin, ancak iş akışı sürekli olarak çalışır. İstemci bilgisayar oturumunu veya istemci bilgisayarı yeniden başlatın ve iş akışını kesintiye uğratmadan iş akışı yürütme başka bir bilgisayardan izleyin.
- **Zamanlama.** Herhangi bir Windows PowerShell cmdlet veya betik gibi iş akışı görevleri zamanlanabilir.
- **İş akışı ve bağlantı daraltma.** İş akışı yürütme ve bağlantıları düğümlere böylece ölçeklenebilirlik ve yüksek kullanılabilirlik senaryolarını etkinleştirme kısıtlanabilir.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Erişimi

Windows PowerShell Web erişimi kullanıcıların bir web tabanlı konsolunda Windows PowerShell komutları ve betikleri çalıştırmasına olanak sağlayan bir Windows Server 2012 özelliğidir. Web tabanlı konsolda kullanan cihazları, Windows PowerShell, uzaktan yönetim yazılımı veya tarayıcı eklentisi yükleme gerektirmez. Gerekli olan tek şey düzgün yapılandırılmış Windows PowerShell Web erişimi ağ geçidi ve JavaScript destekleyen ve tanımlama bilgilerini kabul eden bir istemci cihaz tarayıcısı.

Daha fazla bilgi için [Windows PowerShell Web erişimi dağıtma](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Yeni Windows PowerShell ISE Özellikleri

Windows PowerShell 3.0, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) için IntelliSense, Göster komut penceresinde de dahil olmak üzere birçok yeni özellik bir birleşik Konsol bölmesinde, kod parçacıkları, ayraç eşleştirme Genişlet-Daralt bölümler, otomatik kaydetme, son öğeler Liste, zengin kopyalama, blok kopyalama ve Windows PowerShell komut dosyası iş akışları yazmak için tam destek. Daha fazla bilgi için [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Microsoft .NET Framework 4 için destek

Windows PowerShell ortak dil çalışma zamanı 4.0 karşı yerleşik olarak bulunur. Cmdlet'i, betik ve iş akışı yazarları yeni Microsoft .NET Framework 4 sınıfları içeren uygulama uyumluluğu ve dağıtımı, Managed Extensibility Framework, paralel, ağ, hesaplama, özellikleri ile Windows Windows PowerShell'de kullanabilirsiniz Communication Foundation ve Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Windows önyükleme ortamı için destek

Windows PowerShell 3.0, Windows Önyükleme Ortamı (Windows PE) 4.0 Windows 8 için isteğe bağlı bir bileşenidir. Windows PE, hiçbir işletim sistemi ve Windows yüklemesi için hazırlayan bir bilgisayar başlatıldığında en az bir işletim sistemi ' dir. Windows PE bölümü için kullanılabilir ve sabit sürücüler biçimlendirmek, disk görüntüleri bir bilgisayara kopyalayın ve bir ağ paylaşımındaki Windows Kurulumu başlatın. Windows PowerShell 3.0, Windows PE'de dağıtım, tanılama ve kurtarma senaryolarını yönetmek için kullanılabilir.

### <a name="disconnected-sessions"></a>Oturumlara

New-PSSession cmdlet'i kullanarak oluşturduğunuz kalıcı kullanıcı tarafından yönetilen oturumları ("Pssessions'dan"), Windows PowerShell 3. 0'den itibaren uzak bilgisayarda kaydedilir. Artık oluşturulmuş olan oturum bağımlı değildir.

Şimdi, oturumda çalışan komutlar kesintiye uğratmadan oturum bağlantısını kesebilirsiniz. Oturumu kapatın ve bilgisayarınızı kapatın. Daha sonra aynı veya farklı bir bilgisayara farklı bir oturumdan oturuma bağlanabilirsiniz.

**ComputerName** parametresinin [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet'i artık alır bilgisayara bağlanan kullanıcının oturumların farklı bir bilgisayara farklı bir oturumda başlatıldıkları bile. Oturumlara bağlamak, komutlarının sonuçlarını Al, yeni komutları başlatın ve ardından oturum bağlantısını kesebilir.

Bağlantısı kesilen oturumlara özelliğini desteklemek için yeni cmdlet'ler eklenmiştir dahil olmak üzere [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), ve için alma-PSSession ve yeni parametreler eklendi Pssessions'dan, gibi yönetme cmdlet'leri **InDisconnectedSession** parametresinin [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet'i.

Bağlantısı kesilen oturumlara özelliği, yalnızca bilgisayarları hem kaynak ("istemci") ve ("Sunucu") sona erer bağlantının sonlandırılması Windows PowerShell 3.0 çalışırken desteklenir.

### <a name="robust-session-connectivity"></a>Güçlü oturum bağlantısı

Windows PowerShell 3.0, istemci ve sunucu arasındaki bağlantı beklenmeyen kayıpları algılar ve bağlantınızın yeniden kurulması ve sürdürebilir otomatik olarak çalışır. İstemci-sunucu bağlantısı ayrılan sürede yeniden kurulamıyor, kullanıcı bilgilendirilir ve oturum bağlantısı kesilir. Yeniden bağlanma girişimi sırasında Windows PowerShell, kullanıcıya sürekli geri bildirim sağlar.

Bağlantısı kesilen bir oturuma Invokecommand kullanarak başlatılmışsa, Windows PowerShell bağlantısı kesilen bir oturuma bağlanın ve sürdürebilir daha kolay hale getirmek bir iş oluşturur.

Bu özellikler daha güvenli ve kurtarılabilir bir uzak deneyimi sağlamak ve iş akışları gibi güçlü oturumları gerektiren uzun süre çalışan görevleri gerçekleştirmek kullanıcıların.

### <a name="updatable-help-system"></a>Güncelleştirilebilir Yardımı

Cmdlet'leri için güncelleştirilmiş Yardım dosyaları, modülleri indirebilirsiniz. [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet'i en yeni Yardım dosyaları tanımlar, bunları Internetten indirir, bunları ayıklar, bunları doğrular ve modülü için doğru dile özgü dizinde yükler.

Güncelleştirilmiş Yardım dosyalarını kullanmak için yazmanız yeterlidir `Get-Help`. Windows veya Windows PowerShell yeniden başlatmanız gerekmez. $Pshome dizinde modüller için Yardım'ı güncelleştirmek için Windows PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatın.

Internet erişimi ve güvenlik duvarı arkasına kullanıcılar, yeni dağıtılmayan kullanıcılar desteklemek için [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet'i, bir dosya paylaşımı gibi bir dosya sistemi dizine Yardım dosyalarını indirir. Kullanıcılar daha sonra kullanabileceğiniz [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) güncelleştirilmiş Yardım dosyaları dosya paylaşımından almak için cmdlet.

Kullanabileceğiniz [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) Yardım güncelleştirmek için cmdlet tüm dosyaları veya belirli modüller tüm desteklenen UI kültür. Hatta koyabilirsiniz bir [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) Windows PowerShell profilinizde komutu. Varsayılan olarak, Windows PowerShell modülü için Yardım dosyaları en fazla günde bir kez yükler.

Windows 8 ve Windows Server 2012 modülleri Yardım dosyaları eklemeyin. En son Yardım dosyalarını indirmek için şunu yazın `Update-Help`. Daha fazla bilgi için `Get-Help` (parametresiz) veya [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Bir cmdlet için Yardım dosyaları bilgisayarda yüklü olmadığında [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet artık otomatik olarak oluşturulmuş Yardım görüntüler. Otomatik olarak oluşturulmuş Yardım komut sözdizimi ve kullanımına ilişkin yönergeler içerir [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) Yardım dosyalarını indirmek için cmdlet'i.

Hiçbir modül yazarına güncelleştirilebilir Yardımı için kendi modülü destekler. Modülde Yardım dosyaları içerir ve bunları güncelleştirin veya Yardım dosyalarını atlamak ve bunları yüklemek için güncelleştirilebilir Yardımı'nı kullanmak için güncelleştirilebilir Yardımı'ı kullanın. Güncelleştirilebilir Yardımı destekleme hakkında daha fazla bilgi için bkz. [güncelleştirilebilir Yardımı destekleme](https://go.microsoft.com/FWLink/?LinkID=242129) MSDN'de.

### <a name="enhanced-online-help"></a>Gelişmiş çevrimiçi Yardım

Windows PowerShell çevrimiçi Yardım tüm kullanıcılar için değerli bir kaynaktır, ancak olmayan veya güncelleştirilmiş Yardım dosyaları yükleyemezsiniz kullanıcıları için özellikle önemlidir.

Herhangi bir Windows PowerShell cmdlet'i için çevrimiçi Yardım almak için şunu yazın:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell Yardım konusunun çevrimiçi sürümünü, varsayılan Internet tarayıcısında açar.

**Get-Help-Online** özelliği Windows PowerShell 3.0, artık çok daha güçlü bile, cmdlet için Yardım dosyaları bilgisayarda yüklü değil çalıştığından. **Get-Help-Online** özelliği cmdlet'ler ve gelişmiş işlevleri HelpUri özelliğinden Yardım konusunun URI'sini alır.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Windows PowerShell 3.0 yazarları başlayarak C# cmdlet'leri doldurma **HelpUri** oluşturarak özelliği bir **HelpUri** cmdlet'i Sınıf özniteliği. Gelişmiş işlevleri yazarları tanımlayabilirsiniz bir **HelpUri** özelliği **CmdletBinding** özniteliği. Değerini **HelpUri** özelliği "http" veya "https" ile başlamalıdır.

De içerebilir bir **HelpUri** değeri bir XML temelli cmdlet Yardım dosyasının ilk ilgili bağlantı veya. Bir işlev açıklama tabanlı Yardım bağlantısı yönergesi.

Çevrimiçi Yardımı destekleme hakkında daha fazla bilgi için bkz. [çevrimiçi Yardımı destekleme](/powershell/developer/module/supporting-online-help) Microsoft Docs içinde.

### <a name="cim-integration"></a>CIM tümleştirme

Ortak Bilgi Modeli (CIM için destek sistemler, ağlar, uygulamalar ve hizmetler için yönetim bilgilerin ortak tanımlara sağlayan arasında yönetim bilgi alışverişi olanak), Windows PowerShell 3.0 içerir heterojen sistemler. Windows PowerShell cmdlet'leri yeni veya mevcut CIM sınıflarını, komutları temel yazma özelliği dahil olmak üzere Windows PowerShell 3.0 CIM desteği CIM .NET Framework desteği, XML dosyalarını cmdlet'i tanımını temel. API, CIM Yönetimi cmdlet'leri ve sağlayıcıları WMI 2.0.

### <a name="session-configuration-files"></a>Oturum yapılandırma dosyaları

Windows PowerShell 3. 0'den itibaren bir dosyayı kullanarak özel bir oturum yapılandırması tasarlayabilirsiniz. Yeni bir oturum yapılandırma dosyası betikleri, hangi modüllerin de dahil olmak üzere, bir oturum yapılandırması kullanan oturumları ortamının belirlemenize olanak tanır ve biçimi dosyaları modüllerine hangi cmdlet'leri ve dil öğeleri kullanıcıların kullanabileceği oturumlara yüklenir ve betikleri çalıştırdığı ve hangi değişkenleri görürler.

Bir oturumu, kullanıcılar yalnızca cmdlet'ler belirli bir modülden çalıştırabilir ya da kullanıcıların tam dil ve tüm modüllere erişim için Gelişmiş görevler betikler erişimi olan bir oturum tasarlayabilirsiniz.

Windows PowerShell önceki sürümlerinde, bu düzeyde denetimi yalnızca yazabilirsiniz olan olanlar için kullanılabilir bir C# program veya karmaşık başlatma komut dosyası. Artık, herhangi bir bilgisayarda Administrators grubunun üyesi, bir yapılandırma dosyası kullanarak bir oturum yapılandırması özelleştirebilirsiniz.

Bir oturum yapılandırma dosyası oluşturmak için kullanın [yeni PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet'i. Oturum yapılandırma dosyası için bir oturum yapılandırması uygulamak için [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) veya [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlet'leri.

Daha fazla bilgi için [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) ve [yeni PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Zamanlanmış işleri ve Görev Zamanlayıcı'yı tümleştirme

Şimdi, Windows PowerShell arka plan işleri zamanlama ve Windows PowerShell'de ve Görev Zamanlayıcısı'nı yönetme.

Zamanlanmış Windows PowerShell, Windows PowerShell arka plan işleri Görev Zamanlayıcı görevlerini ve kullanışlı bir karma işlerdir.

Zamanlanmış işleri, Windows PowerShell arka plan işleri gibi arka planda zaman uyumsuz olarak çalışır. Tamamlanan zamanlanmış işleri örneklerini gibi iş cmdlet'lerini kullanarak yönetilebilir [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) ve [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Görev Zamanlayıcı görevlerini gibi tek seferlik veya yinelenen bir zamanlamaya göre veya bir eylem veya olay yanıt zamanlanmış işleri çalıştırabilirsiniz. Görüntüleyebilir ve görev scheduler'da zamanlanmış işler yönetmek, etkinleştirmek ve bunları çalıştırın veya bunları şablon olarak kullanarak ve koşullar altında işleri başlatmak, gerektiği gibi devre dışı.

Ayrıca, bunları yönetmek için cmdlet'ler özelleştirilmiş bir zamanlanmış işleri gelir. Cmdlet'ler, oluşturma, düzenleme, yönetme, devre dışı ve zamanlanmış işleri yeniden etkinleştirmek, zamanlanmış işi Tetikleyicileri oluşturma ve zamanlanmış işi seçenekleri sağlar.

Zamanlanmış işler hakkında daha fazla bilgi için bkz. [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Windows PowerShell dil iyileştirmeleri

Windows PowerShell 3.0, daha basit ve kolay kullanın ve sık karşılaşılan hataları önlemek için dili sağlamak üzere tasarlanmış birçok özellik içerir. Özellik sabit listesi, sayısı ve uzunluğu özelliklerinin skaler nesneleri yeni yönlendirme işleçlerini, $Using kapsam değiştiricisi, otomatik bir değişken, esnek betik PSItem biçimlendirme, değişkenlerin Basitleştirilmiş özniteliği öznitelikleri geliştirmeleri bağımsız değişkenler, sayısal komut adlarını, Dur ayrıştırma işleci, geliştirilmiş dizi sıçratmaya, yeni bit işleçleri, sıralanmış sözlük, PSCustomObject atama ve geliştirilmiş açıklama tabanlı Yardım.

### <a name="new-core-cmdlets"></a>Yeni çekirdek cmdlet'leri

Zamanlanmış işler, oturumlara, CIM tümleştirme ve güncelleştirilebilir Yardım sistemi yönetmek için cmdlet'leri dahil olmak üzere Windows PowerShell Core yükleme için yeni cmdlet'ler eklendi.

|||
|-|-|
|Ekle-JobTrigger|Yeni-JobTrigger|
|Connect-PSSession|Yeni PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|Yeni-PSWorkflowExecutionOption|
|Disable-JobTrigger|Yeni-PSWorkflowSession|
|Disable-ScheduledJob|Yeni ScheduledJobOption|
|Bağlantıyı Kes-PSSession|Yeni-WinEvent|
|Etkinleştir-JobTrigger|Al-PSSession|
|Etkinleştir-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-Cimınstance|
|Get-Cimınstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Bilgisayarı yeniden adlandırma|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-Cimınstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|İçeri aktarma IseSnippet|Set-ScheduledJobOption|
|Çağırma AsWorkflow|Göster komutu|
|Invoke-CimMethod|ControlPanelItem Göster|
|Çağırma RestMethod|İşi askıya alma|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|Yeni-Cimınstance|Dosya engelini kaldırma|
|Yeni-CimSession|Unregister-ScheduledJob|
|Yeni CimSessionOption|Update-Help|
|Yeni IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Var olan çekirdek cmdlet'leri ve sağlayıcıları geliştirmeleri

Windows PowerShell 3.0 Basitleştirilmiş bir sözdizimi ve aşağıdaki cmdlet'leri için yeni parametreler dahil olmak üzere mevcut cmdlet'ler için yeni özellikler içerir: Bilgisayar cmdlet'leri, CSV cmdlet'leri, Get-Childıtem, Get-Command, Get-içerik alma geçmişi, ölçü nesnesi, güvenliği cmdlet'leri, Select-Object, String seçin, bölünmüş yolu, işlemini başlat Tee nesne, Test-Connection Üye Ekle ve WMI cmdlet'leri.

Windows PowerShell sağlayıcıları Ayrıca önemli ölçüde, web barındırma için Güvenli Yuva Katmanı (SSL) sertifikalarını yönetmek için sertifika sağlayıcı desteği dahil olmak üzere geliştirildi, kimlik bilgisi, kalıcı bir ağ sürücülerini ve alternatif veri akışlarını desteği dosya sistemi sürücü.

### <a name="remote-module-import-and-discovery"></a>Uzak modül içeri aktarma ve bulma

Windows PowerShell 3.0 modülü bulma, alma ve uzak bilgisayarlarda örtük uzak iletişim yeteneklerini genişletir. Modülü cmdlet'lerini uzak bilgisayarlarda modüllerini alın ve Windows PowerShell uzaktan iletişimini kullanarak uzak veya yerel bilgisayarda modülleri içeri aktarın. Yeni CIM oturumu desteği örtük olarak uzak bilgisayarda çalışan yerel bilgisayarda komutları içeri aktararak Windows olmayan bilgisayarları yönetmek için CIM ve WMI kullanmanıza olanak tanır.

Daha fazla bilgi için Yardım konularını görmek [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) ve [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet'leri.

### <a name="enhanced-tab-completion"></a>Gelişmiş sekme tamamlama

Windows PowerShell Konsolu sekme tamamlamayı artık cmdlet'leri, parametreleri, parametre değerleri, numaralandırma, .NET Framework türleri, COM nesneleri, gizli dizinler ve diğer adlarını tamamlar. Sekme tamamlama özelliği tamamen yeni Ayrıştırıcı ve bellek içi ayrıştırma ağaçlarını ve Orta çizgi sekme tamamlama dahil olmak üzere daha fazla senaryoları desteklemek için soyut sözdizimi ağacını göre yeniden.

### <a name="module-auto-loading"></a>Modül otomatik yükleme

[Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i artık alır tüm cmdlet'ler ve İşlevler bilgisayarda yüklü tüm modüllerdeki bile modülü geçerli oturuma içe aktarılmaz.

İhtiyacınız olan bir cmdlet'i aldığınızda, bunu hemen modüllerin içeri aktarmadan kullanabilirsiniz. Sürümünde modüldeki herhangi bir cmdlet'i kullandığınızda Windows PowerShell modülleri artık otomatik olarak içeri aktarılır. Artık bu modül araması gerçekleştirin ve cmdlet'lerini kullanmak için içeri aktarılması gerekmez.

Otomatik modüllerini içeri aktarma tetiklenir cmdlet'ini çalışan bir komut kullanarak **Get-Command** joker karakterler veya çalışan olmadan bir cmdlet için [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) joker karakter içermeyen bir cmdlet için.

Etkinleştirme, devre dışı bırakın ve otomatik modüllerini kullanarak içe aktarma yapılandırma **$PSModuleAutoLoadingPreference** tercih değişkeni.

Daha fazla bilgi için [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [tercih değişkenleri hakkında [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b)ve için Yardım konularını [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) ve [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet'leri.

### <a name="module-experience-improvements"></a>Modül deneyimi geliştirmeleri

Windows PowerShell 3.0 modüllerine aşağıdaki yeni özellikler dahil olmak üzere, gelişmiş özellik desteği sunar.

1. Tek tek modüller (LogPipelineExecutionDetails) için modülü günlüğe kaydetmeyi ve yeni "Kapatma modülü oturum" Grup İlkesi ayarı
2. Genişletilmiş modül bildirimindeki değerlerini göstermesi modülü nesneleri
3. Yeni **ExportedCommands** özelliği dahil olmak üzere modüllerinin, her türden komutlar birleştirir modüller, iç içe geçmiş
4. Geliştirilmiş izin verme dahil olmak üzere, kullanılabilir (içe aktarılan beklemediğiniz) modülleri bulunmasını **yolu** ve **ListAvailable** aynı komutu parametreleri
5. Yeni **DefaultCommandPrefix** modülü kodunu değiştirmeden ad çakışmaları önler, modül bildirimlerinde anahtar.
6. Gerekli modülleri tam sürümü ve GUID ve otomatik gerekli modülleri içeri aktarma da dahil olmak üzere, modül gereksinimleri geliştirildi
7. Sessiz, kolaylaştırılmış işleyişini [yeni ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet'i.
8. Yeni **Modülü** parametresi için #Requires
9. Geliştirilmiş [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet'i hem **MinimumVersion** ve **RequiredVersion** parametreleri.

### <a name="simplified-command-discovery"></a>Basitleştirilmiş komut bulma

Artık oturumunuza kullanılabilir komutları bulmak için tüm modülleri içeri aktarmak gerekir. Windows PowerShell 3. 0'da, [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i tüm komutlar yüklü tüm modüllerden alır. Ve oturumunuza bir komutunu kullanırsanız, bir komut verir modülü otomatik olarak aktarılır.

Yeni [Show komutunu](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet'i, özellikle de yeni başlayanlar için tasarlanmıştır. Bir penceresindeki komutları için arama yapabilirsiniz. Tüm komutlar görüntülemek veya modülü tarafından filtrelemek için bir düğmeye tıklayarak bir modülü içeri aktarmak, geçerli bir komut oluşturun ve ardından kopyalayın veya pencerenin çıkmadan komutu çalıştırın, metin kutusu ve aşağı açılan listeleri kullanın.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Gelişmiş günlük kaydı, tanılama ve Grup İlkesi desteği

Windows PowerShell 3.0, günlüğe kaydetme ve izleme komutları ve modüller için destek Windows (ETW) günlükleri, düzenlenebilir bir olay izleme desteği ile artırır **LogPipelineExecutionDetails** modülleri ve "kapatma üzerinde modülü özelliği Günlüğe kaydetme"Grup İlkesi ayarı. Artık, parametre değerlerini günlük özelliklerini görüntüleyerek günlük ayrıntılarını alabilirsiniz.

### <a name="formatting-and-output-improvements"></a>Biçimlendirme ve çıkış geliştirmeleri

Yeni biçimlendirme ve çıkış geliştirmeleri tüm Windows PowerShell kullanıcıları verimliliğini artırın. Tüm akışlar, türleri Format.ps1xml dosyaları çıkışında, sözcük kaydırma olmadan dinamik olarak varsayılan özel nesnelerin biçimlendirme özellikleri ekleyen bir Gelişmiş güncelleştirme türü cmdlet çıktı yeniden yönlendirme geliştirmeleri **PSCustomObject** WMI nesnelerini heterojen nesne ve yöntem aşırı yüklemeleri bulmaya yönelik destek için biçimlendirme, geliştirilmiş türü.

### <a name="enhanced-console-host-experience"></a>Gelişmiş konsol konak deneyimi

Windows PowerShell Konsolu ana bilgisayar programı varsayılan olarak tek iş parçacıklı dahil olmak üzere Windows PowerShell 3.0 yeni özelliklere sahiptir. Dosya Gezgini yeni "PowerShell ile Çalıştır" seçeneğini yalnızca sağ tıklayarak sınırsız bir oturumda betikleri çalıştırmanıza olanak tanır. Yeni konsol konak başlatma mantıksal Windows PowerShell daha hızlı başlatılan ve tanıdık bir konsol penceresi deneyimini kişiselleştirmek yeni yazı tipleri izin verir.

Daha fazla bilgi için [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Yeni Cmdlet ve API'ler barındırma

Yeni Cmdlet API'si ve barındırma API'si genel Gelişmiş söz dizimi ağacı (AST) API'ları ve API'ler için işlem hattı disk belleği, iç içe işlem hatları, çalışma havuzları sekme tamamlama, Windows RT, eski cmdlet özniteliği ve fiil ve isim FunctionInfo nesnesinin özelliklerini içerir.

### <a name="performance-improvements"></a>Performans iyileştirmeleri

Windows PowerShell önemli performans geliştirmeleri, üzerinde dinamik çalışma zamanı dil (DLR) .NET Framework 4'te oluşturulan yeni dil ayrıştırıcı geldiğini., çalışma zamanı betik derlemesi, altyapı güvenilirlik geliştirmeleri ve değişiklikleri birlikte algoritması, [Get-Childıtem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) , iyileştirmek, performansı, özellikle ağ arama paylaştığında.

### <a name="runas-and-shared-host-support"></a>Farklı Çalıştır ve paylaşılan konak desteği

Windows PowerShell 3.0, farklı çalıştır ve paylaşılan konak özellikleri için destek içerir.

*RunAs* özelliği, Windows PowerShell iş akışı için tasarlanmış bir oturum yapılandırması kullanıcıları paylaşılan bir kullanıcı hesabını izinleriyle çalıştırın oturumları oluşturmasına olanak tanır. Bu belirli komutları ve komut dosyalarını yönetici izinleriyle çalıştırmak daha az ayrıcalıklı kullanıcıların sağlar ve daha üst düzey kullanıcı Administrators grubuna ekleme gereksinimini azaltır.

**SharedHost** özelliği aynı anda bir iş akışı oturumu bağlanıp bir iş akışı ilerlemesini izlemek için birden çok bilgisayar üzerinde birden fazla kullanıcı sağlar. Kullanıcılar tek bir bilgisayarda bir iş akışı başlatın ve ardından başka bir bilgisayardaki iş akışı oturumu özgün bilgisayardan oturumun bağlantısını kesmeden bağlanın. Kullanıcılar aynı izinlere sahip olmalıdır ve aynı oturum yapılandırmasına kullanıyor. Daha fazla bilgi için bkz: "Çalıştıran bir Windows PowerShell iş akışı" içinde Windows PowerShell iş akışı ile çalışmaya başlama.

### <a name="special-character-handling-improvements"></a>Özel karakter işleme geliştirmeleri

Yorumlar ve özel karakterleri doğru bir şekilde işlemek için Windows PowerShell 3.0 yeteneğini artırmak için **LiteralPath** olan neredeyse tüm Cmdlet'lerde yolları bulunan özel karakterleri işleyen parametresi geçerli bir  **Yol** yeni dahil olmak üzere parametre [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) ve [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet'leri. Ayrıştırıcının da işleme vurgulamasını belirtir karakterin geliştirmek için özel mantığı içerir (\`) ve köşeli parantez içindeki dosya adlarını ve yollarını.

## <a name="see-also"></a>Ayrıca bkz:

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
