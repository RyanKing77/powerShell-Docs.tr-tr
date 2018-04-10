---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell 5.0 yenilikler nelerdir?
ms.openlocfilehash: f1134a37e7027b00c948ce1db186a21dc5a311c6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="whats-new-in-windows-powershell-50"></a>Windows PowerShell 5.0 yenilikler nelerdir?
Windows PowerShell 5.0 kullanımını genişleten, kullanılabilirliğini artıran ve denetime izin ver ve Windows tabanlı ortamları daha kolay ve kapsamlı bir şekilde yönetmek, önemli yeni özellikler içerir.

Windows PowerShell 5.0 geriye dönük olarak uyumludur. Cmdlet'leri, sağlayıcıları, modüller, ek bileşenler, komut dosyaları, İşlevler ve Windows PowerShell 4.0, Windows PowerShell 3.0 ve Windows PowerShell 2.0 için genellikle tasarlanmış profilleri Windows PowerShell 5. 0 ' değişiklik yapılmadan çalışır.

# <a name="installing-windows-powershell"></a>Windows PowerShell Yükleme
Windows PowerShell 5.0, Windows Server 2016 Technical Preview ve Windows 10 varsayılan olarak yüklenir.

Windows Server 2012 R2, Windows 8.1 Enterprise veya Windows 8.1 Pro üzerinde Windows PowerShell 5. 0'ı yüklemek için karşıdan yükleyip [Windows Management Framework 5.0](http://aka.ms/wmf5download). Yükleme ayrıntılarını okuduğunuzdan ve Windows Management Framework 5.0 yüklemeden önce tüm sistem gereksinimlerini karşıladığından emin olun.

## <a name="in-this-topic"></a>Bu konuda,

- [BB 3000850 Windows PowerShell 4.0 DSC güncelleştirmeleri](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Windows PowerShell 5. 0'teki yeni özellikler](#new-features-in-windows-powershell-50)
- [Windows PowerShell 4. 0'ı yeni özellikler](#new-features-in-windows-powershell-40)
- [Windows PowerShell 3. 0'ı yeni özellikler](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Windows PowerShell 4.0 güncelleştirmeleri Kasım 2014 güncelleştirme paketi (KB 3000850)
Birçok güncelleştirme ve geliştirmeleri için Windows PowerShell istenen durum yapılandırması (DSC) Windows PowerShell 4. 0'ı kullanılabilir olan [Windows RT 8.1, Windows 8.1 ve Windows Server 2012 R2 için Kasım 2014 güncelleştirme paketi](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). BB 3000850 sisteminizde çalıştırarak yüklü olup olmadığını belirlemek `Get-Hotfix -Id KB3000850` Windows PowerShell'de.

- Mevcut cmdlet'leri güncelleştirmeleri [da PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) Modülü

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) (özellikle ISE) daha hızlıdır.

    -   [Başlangıç DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) - hangi son uygulanan yapılandırma yeniden uygular UseExisting, yeni bir parametre içeriyor.

    -   [Başlangıç DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force sabit.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) displays more useful information about the engine state.

    -   [Test-DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) artık doğru veya yanlış yanı sıra bilgisayar adını döndürür.

    -   [DscChecksum yeni](http://technet.microsoft.com/library/dn521622.aspx) artık UNC yollarını destekler.

- Yeni cmdlet'leri [da PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) Modülü

    -   [Güncelleştirme DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): bir isteğe bağlı çekme sunucu denetimi gerçekleştirir.

    -   [Stop-DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): zaten çalışmakta olan bir yapılandırma durdurur.

    -   [Remove-DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): çeşitli aşamalarda (Beklemede, önceki veya geçerli) yapılandırma belgelerini kaldırmanıza olanak sağlar.

- Dil geliştirmeleri

    -   DependsOn artık bileşik kaynakları destekler.

    -   DependsOn numaraları artık kaynak örnek adlarını destekler.

    -   Artık değerlendirmek için boş bir düğüm ifade hataları atar.

    -   Bir düğüm ifadesi için boş değerlendirilirse oluşan bir hata düzeltildi.

    -   Yapılandırmalar artık çağırma yapılandırmaları Windows PowerShell konsolunda da çalışır.

- Çekme modu geliştirmeleri

    -   Çekme mod şimdi tüm ZIP dosyaları destekler.

    -   **AllowModuleOverwrite** şimdi düzgün çalışır.

- Dayanıklılık geliştirmeleri

    -   Yeni **DebugMode** kaynak modülleri yeniden olanak tanır.

    -   Bir yapılandırma hatası oluşursa, pending.mof dosya silinmez.

    -   Meta yapılandırmasını ayarları bozulmuş olduğunda yerel Configuration Manager (LCM'yi) artık daha esnektir.

- Tanılama geliştirmeleri

    -   LCM'yi belirtilenden farklı ayarlar Zamanlayıcı ayarlar bir uyarı görüntülenir.

    -   Hata günlük dosyalarını artık Windows PowerShell kaynaklar için çağrı yığını içerir.

- Esneklik geliştirmeleri

    -   Yeni bir özellik LocalConfigurationManager kaynak sahip **ActionAfterReboot**.

        -   ContinueConfiguration (varsayılan değer): hedef düğüm yeniden başlatıldıktan sonra yapılandırma otomatik olarak devam ettirir.

        -   StopConfiguration: bir düğümü yeniden başlatıldıktan sonra otomatik olarak bir yapılandırma devam.

    -   Bir tutarlılık çalıştırma artık ÇEKME işlemi ya da tam tersini kıyasla daha sık oluşabilir.

    -   Sürüm oluşturma desteği: DSC daha yeni bir istemci üzerinde oluşturulan bir belgeyi artık algılayabilir (ile birlikte gelen [WMF 5.0](http://aka.ms/wmf5download)).

- Hata Engellemesi geliştirmeleri

    -   Bir yapılandırma uygulanmadan önce Modül sürümü artık zorlanır.

    -   **DebugPreference** artık doğru Get-, Set- veya Test TargetResource aramalar için ayarlanır.

- Kimlik bilgisi geliştirmeleri işleme

    -   Bir sertifika, her iki kullanılan **sertifika** ve **PSDscAllowPlainTextPassword** belirtilir.

    -   Kimlik bilgileri, hatta Get-TargetResource için şifresi çözülür.

    -   Meta yapılandırmasını kimlik bilgileri şifrelenir ve şifreleri çözülür.

    -   Katıştırılmış nesne olduklarında PSCredentials artık şifresi çözülür.

- Yerleşik kaynak geliştirmeleri

    -   Paket kaynağı

        -   Artık yanlış paketi yükler (yerel uygulamasından veya web kaynakları).

        -   Artık HTTPS destekler.

    -   HTTPS için şimdi destek [paket kaynak](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Arşiv kaynak](http://technet.microsoft.com/library/dn249917.aspx) artık kimlik bilgilerini destekler.

## <a name="new-features-in-windows-powershell-50"></a>Windows PowerShell 5. 0'teki yeni özellikler

- [Windows PowerShell'de yeni özellikler](#new-features-in-windows-powershell)
- [Windows PowerShell istenen durum Yapılandırması'deki yeni özellikler](#new-features-in-windows-powershell-desired-state-configuration)
- [Windows PowerShell ISE yeni özellikler](#new-features-in-windows-powershell-ise)
- [Windows PowerShell Web Hizmetleri'ndeki yeni özellikler](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Windows PowerShell 5. 0 ' önemli hata düzeltmeleri](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Windows PowerShell'de yeni özellikler

- Windows PowerShell 5. 0'dan başlayarak, sınıflar, resmi sözdizimi ve diğer nesne odaklı programlama dili için benzer semantiği kullanarak geliştirebilirsiniz. **Sınıf**, **Enum**, ve diğer anahtar sözcükler yeni özellik desteklemek için Windows PowerShell dil eklenmiştir. About_Classes sınıfları ile çalışma hakkında daha fazla bilgi için bkz.

- Windows PowerShell 5.0, bir komut dosyası ve arayanlar (veya barındırma ortamı) arasındaki yapılandırılmış veri iletmek için kullanabileceğiniz bir yeni, yapılandırılmış bilgi akış tanıtır. Write-Host artık bilgi akış çıkışı yaymak üzere de kullanabilirsiniz. Bilgi akışlarını PowerShell.Streams, işler, zamanlanmış işler ve iş akışları için de çalışır. Aşağıdaki özellikleri bilgi akışını destekler.

    -   Windows PowerShell komutu için bilgi akışını veri işleme biçimini belirtmenize olanak sağlar. yeni bir yazma bilgi cmdlet'i. Write-Host yazma bilgisi için sarmalayıcı ' dir. Yazma bilgileri de bir desteklenen iş akışı etkinliğidir.

    -   İki yeni ortak parametreleri, Informationvariable ve Informationaction, bir komut bilgi akışlardan nasıl görüntüleneceğini belirlemenize olanak tanır. SilentlyContinue, Durdur, devam et, Inquire, Yoksay veya varsayılan değer olan SilentlyContinue ile askıya alma Informationaction için geçerli değerler. Informationvariable bir dize olarak kaydedilmiş bir komut Write-Host verilerden istediğiniz bir değişkeni adını belirtir.

    -   Yeni tercih değişkeni, InformationPreference, varsayılan tercihinizi bilgi veri akışı için bir Windows PowerShell oturumunda belirtir. SilentlyContinue varsayılan değerdir.

    -   İki yeni iş akışı ortak parametreleri, PSInformation ve Informationaction, eklenmiştir.

    -   Tablo Biçimlendir komutunu kullandığınızda, tablo sütunları artık otomatik olarak akışını geçirir verilerin ilk 300ms değerlendirerek biçimlendirilir.

- İşbirliğiyle [Microsoft Research](http://research.microsoft.com/), ConvertFrom dizesi, yeni bir cmdlet eklendi. ConvertFrom dize ayıklayın ve metin dizelerini içeriğini yapılandırılmış nesnelerden ayrıştırma olanak sağlar. Daha fazla bilgi için bkz: ConvertFrom dize.

- Yeni bir dönüştürme dizesi cmdlet'i bir - örnek parametresinde sağlayan örnek göre metin otomatik olarak biçimlendirir.

- Arşiv (ZIP da bilinir) dosyaları, klasörlere var olan posta dosyalarından dosyaları ayıklayın ve bunların içinde sıkıştırılmış dosyaların daha yeni sürümlerle ZIP dosyaları güncelleştirmek ve Microsoft.PowerShell.Archive, yeni bir modül dosyaları sıkıştırın olanak tanıyan cmdlet'leri içerir.

- PackageManagement, yeni bir modülü bulmak ve Internet'te yazılım paketleri yüklemek olanak sağlar. PackageManagement (önceki adıyla OneGet da bilinir) Yöneticisi'ni veya var olan paketi yöneticileri (paket sağlayıcıları olarak da bilinir) çoğaltıcı tek bir Windows PowerShell arabirimi ile Windows paket Yönetimi birleştirmek için modülüdür.

- PowerShellGet, yeni bir modülü bulmak, yükleme, yayımlama ve güncelleştirme modülleri ve DSC kaynakları üzerinde sağlar [PowerShell Galerisi](http://www.powershellgallery.com/), veya Register-PSRepository cmdlet'ini çalıştırarak ayarlayabileceğiniz bir iç modül deposu.

- Yeni bir dil anahtar sözcüğü **gizli**, bir üye (bir özellik veya yöntem) varsayılan Get-üye sonuçlarında gösterilmez belirtmek için eklenene (eklediğiniz sürece - Force parametresini). Burada üye görünmesi gereken bir bağlamda olmadıkça özellikleri veya gizli olarak işaretlenmiş yöntemler de IntelliSense sonuçlarında görünmüyor; Örneğin, otomatik değişken $bu sınıf yöntemi, gizli üyeleri göstermelidir.

- Yeni öğe, Kaldır öğesini ve Get-Childıtem oluşturma ve yönetme desteği veren geliştirilmiş [sembolik bağlantılar](http://en.wikipedia.org/wiki/Symbolic_link). **- ItemType** yeni öğesi için parametre kabul eden yeni bir değer **SymbolicLink**. Artık yeni öğe cmdlet'ini çalıştırarak tek bir satırda sembolik bağlantılar oluşturabilirsiniz.

- Get-Childıtem de sahip yeni - derinliği özyineleme sınırlamak için Recurse parametresiyle kullanmak parametresi. Örneğin, Get-Childıtem-Recurse - derinliği 2 sonuçları klasörleri geçerli klasörden, geçerli klasördeki tüm alt klasörleri ve tüm alt klasörlerde döndürür.

- Öğeyi Kopyala şimdi kopyaladığınız dosya veya klasör bir Windows PowerShell oturumundan diğerine, uzak bir bilgisayara bağlı oturuma dosyalarını kopyalayabilirsiniz anlamı sağlar (çalıştıran bilgisayarlar da dahil olmak üzere [Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), ve Bu nedenle başka bir arabirim vardır). Dosyaları kopyalamak için yeni - FromSession ve - ToSession parametre değeri olarak PSSession kimlikleri belirlemek ve - Path ve - kaynak yolunu belirtmek için hedef ve hedef, sırasıyla ekleyin. Örneğin, Copy-Item-yol c:\\dosyam.txt - ToSession $s-hedef d:\\destinationFolder.

- Konsolu konak yanı sıra tüm barındırma uygulamaları (örneğin, Windows PowerShell ISE) uygulamak için Windows PowerShell transcription geliştirilmiştir (**powershell.exe**). (Sistem genelindeki dökümü etkinleştirme dahil) transcription seçenekleri sağlayarak yapılandırılabilir **PowerShell Transcription üzerinde kapatma** Yönetim Şablonları/Windows bileşenleri/Windows'ta bulunan, Grup İlkesi ayarı PowerShell.

- Yeni bir ayrıntılı betik izleme özelliği, ayrıntılı izleme ve çözümleme sisteminde Windows PowerShell komut dosyası kullanımı olanak tanır. Ayrıntılı betik izleme etkinleştirdikten sonra Windows PowerShell tüm komut dosyası blokları olay izleme için Windows (ETW) olayı günlüğe kaydeder. **Microsoft-Windows-PowerShell/Operational**.

- Windows PowerShell 5. 0'dan başlayarak, yeni şifreleme iletisi söz dizimi cmdlet'leri şifreleme ve şifre çözme içeriğin şifreli olarak iletileri tarafından belgelenen şekilde korumak için IETF standart biçimi kullanarak destek [RFC5652](http://tools.ietf.org/html/rfc5652). Get-CmsMessage, koruma CmsMessage ve Unprotect-CmsMessage cmdlet'leri için eklenene [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) modülü.

- Yeni cmdlet'leri [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modülü, Get-çalışma alanı, hata ayıklama çalışma, Get-RunspaceDebug, etkinleştirme RunspaceDebug ve devre dışı bırak-RunspaceDebug, izin, bir çalışma alanı ve başlatma ve durdurma hata ayıklama seçeneklerini ayarlama bir çalışma alanı üzerinde hata ayıklama. Rastgele çalışma alanlarını hata ayıklama için "başka bir deyişle, bir Windows PowerShell konsolu veya Windows PowerShell ISE oturumu için varsayılan çalışma olmayan çalışma alanlarını '"Windows PowerShell sağlar kesme bir komut dosyası ve kesme noktaları Durdur betikten eklediyseniz Çalışma alanı komut dosyası hata ayıklamak için bir hata ayıklayıcı ekleyebileceğini kadar çalışıyor. Çalışma alanları için Windows PowerShell komut dosyası hata ayıklayıcı için rasgele çalışma alanlarını iç içe geçmiş hata ayıklama desteği eklendi.

- Yeni bir biçim onaltılık cmdlet eklendi [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modülü. Biçim onaltılık metin veya ikili veri onaltılık biçimde görüntülemenize olanak tanır.

- Get-Pano ve Set-Pano cmdlet'leri eklenmiştir [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modülü; içerik için ve bir Windows PowerShell oturumundan aktarımını kolaylaştırır. Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listelerinin ve metin destekler.

- Clear-geridönüşüm kutusu, yeni bir cmdlet için eklenen [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) modülü; dönüşüm dış sürücüleri içeren bir sabit sürücü için bu cmdlet'i kutusunu boşaltır. Varsayılan olarak, cmdlet'in Confirmımpact özelliği için ConfirmImpact.High ayarlandığından Temizle geridönüşüm kutusu komutu onaylamanız istenir.

- Yeni bir cmdlet, New-TemporaryFile, komut dosyası bir parçası olarak geçici bir dosya oluşturmanıza olanak sağlar. Varsayılan olarak, yeni geçici dosya oluşturulan ```C:\Users\<user name>\AppData\Local\Temp```.

- Şimdi Out-File, Add-Content ve Set-Content cmdlet'leri çıktıdan sonra yeni bir satır atlar bir yeni - NoNewline parametreye sahip.

- Yeni GUID cmdlet komut dosyaları veya DSC kaynakları yazarken yararlı bir GUID oluşturmak için .NET Framework GUID sınıfı yararlanır.

- Bir dosya özellikle uygulandıktan sonra dosya sürümü bilgilerini yanıltıcı, olabileceğinden, yeni FileVersionRaw ve ProductVersionRaw komut dosyası özellikleri FileInfo nesneler için kullanılamaz. Örneğin, burada $pid çalışan bir Windows PowerShell oturumu için işlem kimliği içerir, powershell.exe için bu özelliklerin değerlerini görüntülemek için aşağıdaki komutu çalıştırabilirsiniz:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Yeni cmdlet'leri Enter PSHostProcess ve çıkış PSHostProcess Windows PowerShell betikleri Windows PowerShell konsolunda çalışan geçerli işlemi ayrı işlemlerde hata ayıklama sağlar. Girin ya da belirli işlem kimliği için iliştirmek için ENTER-PSHostProcess çalıştırın ve ardından işlemdeki etkin çalışma alanlarını döndürmek için Get-çalışma çalıştırın. İşlem içindeki komut dosyası hata ayıklaması bittiğinde işleminden ayırmak için çıkış-PSHostProcess çalıştırın.

- Yeni bir bekleme hata ayıklayıcı cmdlet eklendi [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) modülü. Sonraki deyim komut dosyasını çalıştırmadan önce bir komut dosyası hata ayıklayıcı durdurmak için bekleme-hata ayıklayıcı çalıştırabilirsiniz.

- Windows PowerShell iş akışı hata ayıklayıcı komut veya sekme tamamlama artık destekler ve iç içe geçmiş iş akışı işlevleri ayıklayabilirsiniz. Şimdi basabilirsiniz **Ctrl + Break** çalışan bir komut dosyası, hem yerel hem de uzak oturumlar ve bir iş akışı komut dosyası hata ayıklayıcı girmek için.

- Hata ayıklama işi cmdlet eklendi [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) çalışan iş komutlar Windows PowerShell iş akışı, arka plan ve uzak oturumlarında çalışan işleri için hata ayıklamak için modülü.

- Yeni bir durum, AtBreakpoint, Windows PowerShell işleri eklendi. Komut dosyasını bir kesme noktası isabet ve bir iş kümesi kesme noktaları içeren bir komut dosyası çalıştırılırken AtBreakpoint durum geçerlidir. Bir işi hata ayıklama kesme noktasında durdurulduğunda, hata ayıklama işi cmdlet'ini çalıştırarak iş hata ayıklama gerekir.

- Windows PowerShell 5.0 $PSModulePath aynı klasörde birden fazla sürümünü tek bir Windows PowerShell modülü için destek uygular. RequiredVersion özelliği bir modülü istenen sürümü alma yardımcı olmak için ModuleSpecification sınıfı eklendi; Bu özellik ModuleVersion özelliğiyle karşılıklı olarak birbirini dışlar. Get-modülünün FullyQualifiedName parametresinin değeri bir parçası olarak RequiredVersion desteklenen şimdi Import-Module ve Kaldır-Module cmdlet'leri.

- Modül sürümü doğrulama artık Test ModuleManifest cmdlet'ini çalıştırarak da gerçekleştirebilirsiniz.

- Get-Command cmdlet'i sonuçlarını şimdi sürüm sütununda görüntüleyin; Yeni bir sürüm özelliği CommandInfo sınıfı eklendi. Get-Command aynı modülü birden fazla sürümünü komutları gösterir. Version özelliği de CmdletInfo türetilmiş sınıfları parçasıdır: CmdletInfo ve ApplicationInfo.

- Get-Command - PSObjects olarak ShowCommand bilgilerini döndürür ShowCommandInfo, yeni bir parametre vardır. Bu Windows PowerShell uzaktan iletişimi kullanarak, Göster komutu Windows PowerShell ISE çalıştırdığınızda için kullanışlı bir işlevdir. -ShowCommandInfo parametresi Microsoft.PowerShell.Utility modülü mevcut Get-SerializedCommand işlevinde değiştirir, ancak Get-SerializedCommand betik alt düzey komut dosyasını destekleyen hala kullanılabilir.

- Yeni bir Get-ItemPropertyValue cmdlet'i noktalı gösterim kullanmadan bir özelliğin değerini alabilmenizi sağlar. Örneğin, Windows PowerShell eski sürümlerini uygulama temel özellik PowerShellEngine kayıt defteri anahtarının değerini almak için aşağıdaki komutu çalıştırabilirsiniz: **(Get-ItemProperty-yolu HKLM:\\yazılım\\ Microsoft\\PowerShell\\3\\PowerShellEngine-ad ApplicationBase). ApplicationBase**. Windows PowerShell 5. 0'dan başlayarak, çalıştırabilirsiniz **Get-ItemPropertyValue-yolu HKLM:\\yazılım\\Microsoft\\PowerShell\\3\\PowerShellEngine-Name ApplicationBase** .

- Windows PowerShell Konsolu şimdi söz dizimi renklendirme, yalnızca Windows PowerShell ISE olduğu gibi kullanır.

- Yeni bir NetworkSwitch modül anahtarı, sanal LAN (VLAN) ve temel Katman 2 ağ anahtarı bağlantı noktası yapılandırmasını Windows Server 2012 R2 logo sertifikalı ağ anahtarlara uygulamak etkinleştirmeniz cmdlet'leri içerir.

- FullyQualifiedName parametresi, tek bir modülün birden fazla sürümünü depolama desteklemek için Import-Module ve Kaldır-Module cmdlet'leri için eklendi.

- Save-Help, Update-Help, içeri aktarma-PSSession, Export-PSSession ve Get-Command türü ModuleSpecification FullyQualifiedModule yeni bir parametre vardır. Bir modül tarafından tam olarak nitelenmiş adını belirtmek için bu parametreyi ekleyin.

- Değeri **$PSVersionTable.PSVersion** 5.0 için güncelleştirilmiştir.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Windows PowerShell istenen durum Yapılandırması'deki yeni özellikler

- Windows PowerShell dil geliştirmeleri, sınıflarını kullanarak Windows PowerShell istenen durum yapılandırması (DSC) kaynakları tanımlamanıza olanak sağlar. İçeri aktarma DscResource true dinamik anahtar sözcüğü sunulmuştur; Windows PowerShell Belirtilen modül ayrıştırır '™ DscResource özniteliği içeren sınıfları aranıyor s kök modül. Sınıfları artık hangi hiçbiri bir MOF dosyası ya da modül klasöründe DSCResource alt gerekli değil, DSC kaynakları tanımlamak için de kullanabilirsiniz. Bir Windows PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.

- ThrottleLimit, yeni bir parametre da PSDesiredStateConfiguration modülündeki aşağıdaki cmdlet'ler eklenmiştir. Hedef bilgisayarları ve aygıtları aynı anda çalışması için komutu istediğiniz sayısını belirtmek için ThrottleLimit parametresini ekleyin.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Restore-DscConfiguration

    -   Test-DscConfiguration

    -   Compare-DscConfiguration

    -   Yayımlama DscConfiguration

    -   Set-DscLocalConfigurationManager

    -   Start-DscConfiguration

    -   Update-DscConfiguration

- Olay günlüğü, ancak sonraki çözümleme için merkezi bir konuma gönderilebilir merkezi DSC hata raporlama ile zengin hata bilgileri yalnızca günlüğe kaydedilmez. Kullanıcıların, ortamlarında herhangi bir sunucu için oluşmuş DSC yapılandırma hataları depolamak için bu merkezi bir konum kullanın. Rapor sunucusu meta yapılandırmasında tanımlandıktan sonra tüm hataları rapor sunucusuna gönderilir ve sonra bir veritabanında depolanır. Bir çekme sunucudan yapılandırmaları çıkarmak için hedef düğüm yapılandırılmış olup olmadığına bakılmaksızın bu işlevselliği ayarlayabilirsiniz.

- Windows PowerShell ISE geliştirmeleri DSC kaynağı yazma kolaylaştırır. Şimdi aşağıdakileri yapabilirsiniz.

    -   İçindeki tüm DSC kaynakları listesinde bir **yapılandırma** veya **düğümü** girerek blok **Ctrl + Ara çubuğu** bloğu içinde boş bir satıra.

    -   Kaynak özelliklerini üzerinde otomatik tamamlama **numaralandırma** türü.

    -   Otomatik Tamamlama sonrasında **DependsOn** DSC kaynakları, diğer kaynak örnekleri yapılandırma temel özelliği.

    -   Geliştirilmiş sekme tamamlama kaynak özellik değeri.

- Kullanıcı artık belirtilen kimlik bilgileri kümesi altında bir kaynak ekleyerek çalıştırabilirsiniz **PSDscRunAsCredential** özniteliği bir düğüm bloğu. Örneğin, PSDscRunAsCredential Get-Credential Contoso =\\DscUser. Bu işlevsellik, Windows Installer ve yürütülebilir yükleyicileri çalıştırın, kullanıcı başına kayıt defteri kovanı erişim ya da diğer görevleri geçerli kullanıcı içeriğini dışında yapılandırmaları oluşturmak için kullanışlıdır.

- 32-bit (x86 tabanlı) desteği eklendi **yapılandırma** anahtar sözcüğü.

- Windows PowerShell artık ekleyerek tanımlanan DSC yapılandırmaları için özel Yardım için destek içerir \[CmdletBinding()] üretilen yapılandırma işlevi.

- Yeni bir **DscLocalConfigurationManager** özniteliği bir meta-DSC Local Configuration Manager yapılandırmak için kullanılan yapılandırma, bir yapılandırma bloğu belirler. Bu öznitelik, DSC Local Configuration Manager yapılandırma öğelerini içeren bir yapılandırma kısıtlar. Bu yapılandırma işlemi sırasında oluşturur bir \*. uygun hedef düğümleri kümesi DscLocalConfigurationManager cmdlet'ini çalıştırarak gönderilir meta.mof dosya.

- Kısmi yapılandırmaları artık Windows PowerShell 5. 0 ' izin verilir. Parçada bir düğüme yapılandırma belgelerini sunabilir. Birden çok düğüm yapılandırması belge parçalarını almak bir düğüm için '™ s yerel Configuration Manager önce ayarlanmalıdır beklenen parçaları belirtmek için

- Bilgisayarlar arası eşitleme DSC Windows PowerShell 5. 0'ın yeni bir özelliktir. Yerleşik WAITFOR kullanarak\* kaynakları (**WaitForAll**, **WaitForAny**, ve **WaitForSome**), bilgisayarlar arasında bağımlılıkları artık belirtebilirsiniz Yapılandırma çalıştığında sırasında dış düzenlemelerin olmadan. Bu kaynaklar, WS-Man protokolü üzerinden CIM bağlantıları kullanarak düğümü düğümü eşitleme sağlar. Başka bir bilgisayar için bir yapılandırma bekleyebilirsiniz '™ s belirli kaynak durumunu değiştirmek için.

- Yalnızca yetecek kadar Yönetim (JEA), yeni bir temsilci güvenlik özelliği, DSC yararlanır ve Windows PowerShell kısıtlı çalışma alanları olsa da kasıtlı olarak veya yanlışlıkla veri kaybı veya çalışanlar tarafından güvenliğinin aşılmasına güvenli kuruluşların Yardım. JEA, xJEA DSC kaynağı yükleyebileceğiniz dahil olmak üzere hakkında daha fazla bilgi için bkz: [yalnızca yeterince yönetim, adım adım](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- Da PSDesiredStateConfiguration Modülü aşağıdaki yeni cmdlet'ler eklenmiştir.

    -   Yeni bir Get-DscConfigurationStatus cmdlet'i, hedef düğüm yapılandırma durumu hakkında üst düzey bilgileri alır. Durum edinebilirsiniz son ya da tüm yapılandırmaları.

    -   Yeni bir karşılaştırma DscConfiguration cmdlet'i belirtilen bir yapılandırma bir veya daha fazla hedef düğümleri gerçek durumu ile karşılaştırır.

    -   Yeni bir yayımlama DscConfiguration cmdlet'i bir yapılandırma MOF dosyası hedef düğüme kopyalar, ancak yapılandırma uygulanmaz. Yapılandırma sonraki tutarlılık geçişi sırasında veya güncelleştirme DscConfiguration cmdlet'ini çalıştırdığınızda uygulanır.

    -   Yeni bir Test DscConfiguration cmdlet, sonuçta elde edilen yapılandırma yapılandırma istenen yapılandırma ya da False eşleşirse gerçek yapılandırma istenen eşleşmiyorsa ya da True döndürüyor, istenen yapılandırma ile eşleştiğini doğrulayın olanak tanır yapılandırma.

    -   Yeni bir güncelleştirme DscConfiguration cmdlet işlenmek üzere bir yapılandırma zorlar. Yerel Configuration Manager çekme modda ise, cmdlet uygulamadan önce istek sunucusundan yapılandırmasını alır.

### <a name="new-features-in-windows-powershell-ise"></a>Windows PowerShell ISE yeni özellikler

- Bilgisayarda bir uzak oturum başlatmak için Enter-PSSession çalıştırarak uzaktan Windows PowerShell komut dosyaları ve Windows PowerShell ISE, yerel bir kopyasını dosyalarında şimdi düzenleyebileceğiniz, '™ s düzenlemek istediğiniz dosyaları depolamak ve çalıştırmayı **PSEdit <path and file name on the remote computer>**. Bu özellik, Windows Server, Windows PowerShell ISE burada çalıştıramazsınız Sunucu Çekirdeği yükleme seçeneği depolanan düzenleme Windows PowerShell dosyaları kolaylaştırır.

- Başlangıç dökümü cmdlet, Windows PowerShell ISE'de artık desteklenmektedir.

- Şimdi, uzaktan komut dosyalarında Windows PowerShell ISE ayıklayabilirsiniz.

- Yeni bir menü komutu **bölün tüm** (Ctrl + B), hem yerel hem de uzaktan çalışan bir komut dosyası hata ayıklayıcı içine keser.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Windows PowerShell Web Hizmetleri (Yönetim OData IIS uzantısı)'deki yeni özellikler

- Windows PowerShell 5. 0'dan başlayarak, yeni bulunan verme ODataEndpointProxy cmdlet çalıştırılarak belirli bir OData uç tarafından sunulan işlevselliği temel Windows PowerShell cmdlet'leri kümesini oluşturabilir [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) modülü.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Windows PowerShell 5. 0 ' önemli hata düzeltmeleri

- Windows PowerShell 5. 0 ile COM nesneleri çalışırken önemli performans geliştirmeleri sunan yeni bir COM uygulaması içerir. Etkisi video gösterimi için bkz: [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Önemli performans geliştirmeleri sekme tamamlama süresi yaklaşık 500 ms tarafından kısaltmayı ilk sekme tamamlama bir Windows PowerShell oturumunda yapılmıştır.

## <a name="new-features-in-windows-powershell-40"></a>Windows PowerShell 4. 0'ı yeni özellikler
Windows PowerShell 4.0 geriye dönük olarak uyumludur. Cmdlet'leri, sağlayıcıları, modüller, ek bileşenler, komut dosyaları, İşlevler ve Windows PowerShell 3.0 ve Windows PowerShell 2.0 için tasarlanmış olan profilleri Windows PowerShell 4. 0 ' değişiklik yapılmadan çalışır.

Windows PowerShell 4.0, Windows 8.1 ve Windows Server 2012 R2 üzerinde varsayılan olarak yüklenir. Windows 7 SP1 veya Windows Server 2008 R2 ile Windows PowerShell 4.0 sürümünü yüklemek için karşıdan yükleyip [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Yükleme ayrıntılarını okuduğunuzdan ve Windows Management Framework 4.0 yüklemeden önce tüm sistem gereksinimlerini karşıladığından emin olun.

- [Windows PowerShell'de yeni özellikler](#new-features-in-windows-powershell-1)
- [Yeni özellikler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Windows PowerShell iş akışı yeni özellikler](#new-features-in-windows-powershell-workflow)
- [Windows PowerShell Web Hizmetleri'ndeki yeni özellikler](#new-features-in-windows-powershell-web-services)
- [Windows PowerShell Web Erişimi'nde yeni özellikler](#new-features-in-windows-powershell-web-access)
- [Windows PowerShell 4. 0 ' önemli hata düzeltmeleri](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0, aşağıdaki yeni özellikler içerir.

### <a name="new-features-in-windows-powershell"></a>Windows PowerShell'de yeni özellikler

- **Windows PowerShell istenen durum Yapılandırması** (DSC) olan Windows PowerShell 4.0'de, dağıtım ve yönetim yazılımı Hizmetleri ve bu hizmetleri çalıştırdığınız ortamı için yapılandırma verileri sağlayan yeni bir yönetim sistemi. DSC hakkında daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırması ile çalışmaya başlama](https://technet.microsoft.com/en-us/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Save-Help** şimdi Yardım uzak bilgisayarlarda yüklü olan modüller için kaydetme olanak sağlar. Save-Help (üzerinde tümü Yardım istediğiniz modüllerin mutlaka yüklenmez) bir Internet'e bağlı istemciden modül Yardım yükleyin ve kaydedilmiş Yardım uzak bir paylaşılan klasör veya Internet olmayan uzak bir bilgisayara kopyalamak için kullanabileceğiniz erişim.

- Windows PowerShell hata ayıklayıcıyı uzak bilgisayarlarda çalışan komut dosyalarının yanı sıra Windows PowerShell iş akışları, hata ayıklama izin verecek şekilde geliştirilmiştir. Windows PowerShell iş akışları artık Windows PowerShell komut satırı ya da Windows PowerShell ISE betik düzeyinde hata ayıklaması yapılabilir. İş akışları dahil olmak üzere Windows PowerShell komut dosyaları artık Uzak Oturumlar hata ayıklaması yapılabilir. Uzaktan hata ayıklama oturumları, bağlantısı kesilen ve daha sonra yeniden bağlantı kuruldu Windows PowerShell uzak oturum korunur.

- A **RunNow** parametresi için **Register-ScheduledJob** ve **Set-ScheduledJob** kullanarakbirhemenbaşlangıçtarihivesaatiprojeleriçinayarlamagereğiniortadankaldırır**Tetikleyici** parametresi.

- **Invoke-RestMethod** ve **Invoke-WebRequest** artık üstbilgileri parametresini kullanarak tüm üstbilgileri ayarlamanıza olanak tanır. Bu parametre her zaman olmamış rağmen özel durumlar veya hatalar sonuçlandı web cmdlet'leri için birkaç parametrelerden biri oluştu.

- **Get-Module** yeni bir parametre içeriyor **FullyQualifiedName**, türü **ModuleSpecification\[]**. **FullyQualifiedName** Get-Module parametresinin artık bir modül modülün adı, sürüm ve isteğe bağlı olarak, bunun GUID'sini kullanarak belirtmenizi sağlar.

- Varsayılan yürütme İlkesi ayarı Windows Server 2012 R2 üzerinde **RemoteSigned**. Windows 8.1 varsayılan ayarı değişiklik yoktur.

- Windows PowerShell 4. 0'dan başlayarak, dinamik yöntemi adlarını kullanarak yöntem çağırma desteklenmiyor. Değişkeni çağrılarak yöntemi dinamik olarak çağırmak ve bir yöntem adı depolamak için bir değişken kullanın.

- Zaman aşımı süresi, by belirtildiğinde, zaman uyumsuz iş akışı işleri silinmiş artık **PSElapsedTimeoutSec** iş akışı ortak parametresi geçtikten.

- Yeni bir parametre **RepeatIndefinitely**, eklendi **New-JobTrigger** ve **Set-JobTrigger** cmdlet'leri. Bu belirtmenin gerekliliğini ortadan kaldıran bir **TimeSpan.MaxValue** değerini **RepetitionDuration** zamanlanmış bir işi belirsiz bir süre için tekrar tekrar çalıştırmak için parametre.

- A **Passthru** parametresi eklenmiştir **Enable-JobTrigger** ve **devre dışı bırak-JobTrigger** cmdlet'leri. Passthru parametresi, komut tarafından değiştirilen veya oluşturulan tüm nesneleri görüntüler.

- Bir çalışma grubunda belirtmek için parametre adları **Add-Computer** ve **Remove-Computer** cmdlet'leri tutarlı şimdi. Her iki cmdlet'leri şimdi parametresini kullanın **ÇalışmaGrubuAdı**.

- Yeni bir ortak parametre **PipelineVariable**, eklendi. PipelineVariable yöneltilen komut (veya piped komutun bir parçası) sonuçlarını kaydetmenizi ardışık geri kalanı geçirilen bir değişken olarak sağlar.

- Bir yöntem sözdizimi kullanarak filtreleme koleksiyonu artık desteklenmez. Başka bir deyişle, artık nesneler koleksiyonunu Basitleştirilmiş söz dizimi, benzer Where() veya Where-Object, yöntem çağrısı biçimlendirilmiş kullanarak filtreleyebilirsiniz. Bir örnek şudur: (Get-Process) .where ({$_. Name - eşleşen 'powershell'})

- **Get-Process** cmdlet sahip yeni bir anahtar parametre **IncludeUserName**.

- Yeni bir cmdlet **Get-FileHash**, belirtilen bir dosya için birkaç biçimlerden birinde bir dosya karma değeri döndürür, eklendi.

- Bir modül kullanıyorsa, Windows PowerShell 4.0, **DefaultCommandPrefix** kendi bildiriminde anahtar ya da kullanıcı sahip bir modül alıyorsa **önek** parametresi **ExportedCommands**modülün özelliği önekle modülünde komutları gösterir. Modül adı Modül sözdizimini kullanarak komutları çalıştırdığınızda\\CommandName, komut adlarının öneki içermelidir.

- Değeri **$PSVersionTable.PSVersion** 4.0 için güncelleştirilmiştir.

- **WHERE()** işleci davranışı değişti. `Collection.Where('property -match name')` bir dize ifadesi biçimde kabul `"Property -CompareOperator Value"` artık desteklenmiyor. Ancak, **Where()** işleci bir scriptblock biçimde dizesi ifadeleri kabul eder; Bu hala desteklenmektedir.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Yeni özellikler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE)

- Windows PowerShell ISE hem Windows PowerShell iş akışı hata ayıklama ve uzaktan hata ayıklamayı destekler.

- Windows PowerShell istenen durum yapılandırması sağlayıcıları ve yapılandırmaları için IntelliSense desteği eklendi.

### <a name="new-features-in-windows-powershell-workflow"></a>Windows PowerShell iş akışı yeni özellikler

- Destek eklenmiştir yeni bir **PipelineVariable** olanlar gibi yinelemeli ardışık düzen bağlamında ortak parametresi System Center Orchestrator tarafından kullanılan; yalnızca soldan sağa, tersine komutları çalıştıran diğer bir deyişle, ardışık düzenleri Akış kullanarak karıştırılarak çalışıyor.

- Parametre bağlama, geçerli çalışma alanında var olmayan komutları gibi sekme tamamlama senaryoları dışında çalışmak için önemli ölçüde geliştirilmiştir.

- Windows PowerShell iş akışına özel kapsayıcı etkinlikler için destek eklenmiştir. Bir etkinlik parametresi türlerini ise **etkinlik**, **etkinlik\[]**' "veya bir genel koleksiyon etkinliklerin" ve kullanıcı bir betik bloğu bağımsız değişken olarak, sonra Windows sağlamadı. PowerShell iş akışı komut dosyası bloğunda normal olarak Windows PowerShell komut dosyası iş akışı derleme ile XAML biçimine dönüştürür.

- Kilitlenme sonrasında, Windows PowerShell iş akışı yönetilen düğümlere otomatik olarak yeniden bağlanır.

- Şimdi daraltabilir **Foreach-Parallel** kullanarak etkinlik deyimleri **ThrottleLimit** özelliği.

- **ErrorAction** ortak parametresine sahip yeni bir geçerli değer **askıya alma**, yani iş akışları için özel olarak.

- Hiçbir etkin oturumlar, devam eden işler ve bekleyen iş varsa bir iş akışı uç noktası artık otomatik olarak kapatılır. Bu özellik otomatik kapatma koşullar sağlandığında, iş akışı sunucusu gibi davranan bilgisayardaki kaynakların tasarrufu sağlar.

### <a name="new-features-in-windows-powershell-web-services"></a>Windows PowerShell Web Hizmetleri'ndeki yeni özellikler

- Windows PowerShell Web Hizmetleri (PSWS, ayrıca adlı yönetim OData IIS uzantısı), bir hata oluştuğunda bir cmdlet çalışıyor, ayrıntılı hata iletilerini çağırana döndürülür. Ayrıca, hata kodları izleyin [Windows Azure REST API hata kodu yönergeleri](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- Bir uç nokta şimdi API sürümü tanımlamak, aynı zamanda belirli bir API sürümü kullanımını zorunlu. İstemci ve sunucu arasında sürüm uyuşmazlığı meydana geldiğinde, hatalar için istemci ve sunucu görüntülenir.

- Eksik tüm alanlar için değerleri otomatik olarak şemada oluşturarak gönderme şema yönetimi basitleştirilmiştir. Gönderme şeması yok olsa bile oluşturma, yararlı bir başlangıç noktası olarak gerçekleşir.

- İçinde PSWS işleme türü, benzer şekilde davranmakta tarafından varsayılan oluşturucu daha farklı bir oluşturucu kullanın türlerini desteklemek için geliştirilmiştir **pstypeconverter'ı** Windows PowerShell'de. Bu karmaşık türler ile PSWS kullanmanıza olanak tanır.

- PSWS artık ilişkili bir örnek bir sorgu çalıştırılırken genişletilmesini sağlar. Büyük ikili içeriği (örneğin, görüntüler, ses veya video) aktarımı maliyeti önemlidir ve kodlamadan ikili veri aktarımı daha iyidir. PSWS kodlamadan aktarmak için adlandırılmış kaynak akışlarını kullanır. Adlandırılmış kaynak akışı, bir varlığın özelliğidir **Edm.Stream** türü. Her adlandırılmış kaynak akışı alma ya da güncelleştirme işlemleri için ayrı bir URI'ya sahip.

- OData eylemlerinin şimdi bir kaynakta CRUD olmayan (oluşturma, okuma, güncelleştirme ve silme) yöntemlerini çağırma için bir mekanizma sağlar. Bir eylem için eylem tanımlanan URI HTTP POST isteği göndererek çağırabilirsiniz. Eylem parametrelerini POST isteğinin gövdesinde tanımlanır.

- Windows Azure yönergelerle tutarlı olması için tüm URL'leri Basitleştirilmiş. Dahil bir değişiklik **anahtar olarak Segment** parçaları olarak gösterilemeyecek kadar tek anahtarlarına izin verir. Birden çok anahtar değerlerini kullanın başvuruları virgülle ayrılmış değerler parantez gösteriminde eskisi gerektiriyor unutmayın.

- PSWS, bu sürümünden önce şekilde oluştur, güncelleştirme veya silme gerçekleştirmek için işlemleri yalnızca Post çağırmak için Put veya üst düzey bir kaynakta silin. Yeni PSWS bu sürümünde bulunan kaynak işlemlerinin bu kaynakları yer alacağı yaklaşan aynı kaynak daha az doğrudan ulaşmasını sırasında aynı sonucu elde açmalarına olanak tanır.

### <a name="new-features-in-windows-powershell-web-access"></a>Windows PowerShell Web Erişimi'nde yeni özellikler

- Bağlantıyı kesmek ve web tabanlı Windows PowerShell Web erişimi konsolunda var olan oturumlar için yeniden bağlanın. A **kaydetmek** web tabanlı konsolda düğmesi silmeden bir oturumun bağlantısını kesmek ve başka bir oturuma yeniden olanak tanır zaman.

- Oturum açma sayfasında varsayılan parametreleri görüntülenebilir. Varsayılan parametreleri görüntülemek için görüntülenen tüm ayarlar değerlerini yapılandırmak **isteğe bağlı bağlantı ayarları** adlı bir dosyaya oturum açma sayfasının alanı **web.config**. Kullanabileceğiniz **web.config** ikinci veya alternatif bir kimlik bilgileri kümesi hariç tüm isteğe bağlı bağlantı ayarlarını yapılandırmak için bir dosya.

- Windows Server 2012 R2'de Windows PowerShell Web erişimi için yetkilendirme kuralları uzaktan yönetebilirsiniz. **Add-PswaAuthorizationRule** ve **Test-PswaAuthorizationRule** cmdlet'ler yöneticilerin yetkilendirme kuralları uzak bir bilgisayardan veya yönetmelerine olanak sağlayan bir kimlik bilgisi parametresi artık içeren bir Windows PowerShell Web erişimi oturumu.

- Her oturum için yeni bir tarayıcı sekmesi kullanarak tek bir tarayıcı oturumu içinde birden fazla Windows PowerShell Web erişimi oturumları artık olabilir. Artık web tabanlı Windows PowerShell konsolunda yeni bir oturumda bağlanmak için yeni bir tarayıcı oturumunu açmanız gerekir.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Windows PowerShell 4. 0 ' önemli hata düzeltmeleri

- **Get-Counter** Fransızca Windows sürümlerinde kesme işareti karakteri içeren sayaçları şimdi geri dönebilirsiniz.

- Artık görüntüleyebilirsiniz **GetType** seri durumdan çıkarılmış nesneler üzerinde yöntemi.

- **#Requires** deyimleri gerekirse yönetici erişim hakları gerektiren kullanıcılar artık sağlar.

- **Alma Csv** cmdlet şimdi boş satırlar yok sayar.

- Bir sorun olduğu Windows PowerShell ISE kullanan çok fazla bellek çalıştırırken bir **Invoke-WebRequest** komutu sabit.

- **Get-Module** şimdi modülü sürümlerde görüntüler bir **sürüm** sütun.

- Remove-Item - Recurse şimdi beklendiği gibi bu öğeleri alt kaldırır.

- A **kullanıcıadı** özelliği eklenmiştir **Get-Process** çıkış nesneleri.

- **Invoke-RestMethod** cmdlet'i şimdi tüm kullanılabilir sonuçlarını döndürür.

- **Üye Ekle** şimdi alır hashtable'da, etkisi hashtable'da değil henüz erişilene olsa bile.

- **Select-Object - genişletin** artık başarısız olduğunda veya özelliğin değeri null veya boş ise, bir özel durum oluşturur.

- **Get-Process** alma diğer komutlarla ardışık düzeninde artık kullanılabilir **ComputerName** nesnelerinden özelliği.

- **ConvertTo-Json** ve **ConvertFrom Json** şimdi çift tırnak işareti içinde koşullarını kabul edebilir ve kendi hata iletileri yerelleştirilebilir sunulmuştur.

- **Get-Job** şimdi herhangi tamamlandı zamanlanmış işler, hatta yeni oturumlar döndürür.

- Bağlama ve çıkarma VHD'ler kullanarak sorunları **FileSystem** sağlayıcısı Windows PowerShell 4. 0'ı sabit. Windows PowerShell artık aynı oturum bağlı oldukları zaman yeni sürücüsü algılayabilir.

- Artık açıkça yüklemek gereken **ScheduledJob** veya **iş akışı** modülleri kendi iş türleri ile çalışır.

- İç içe geçmiş iş akışları tanımlamak iş akışlarını içeri aktarma işlemi için performans iyileştirmeler yapılmıştır; Bu işlem şimdi daha hızlıdır.

## <a name="new-features-in-windows-powershell-30"></a>Windows PowerShell 3. 0'ı yeni özellikler
Windows PowerShell 3.0 aşağıdaki yeni özellikler içerir.

- [Windows PowerShell iş akışı](#windows-powershell-workflow)
- [Windows PowerShell Web erişimi](#windows-powershell-web-access)
- [Yeni Windows PowerShell ISE Özellikleri](#new-windows-powershell-ise-features)
- [Microsoft .NET Framework 4.0 için destek](#support-for-microsoft-net-framework-4)
- [Windows önyükleme ortamı için destek](#support-for-windows-preinstallation-environment)
- [Bağlantısı kesik oturumlar](#disconnected-sessions)
- [Robust Session Connectivity](#robust-session-connectivity)
- [Güncelleştirilebilir Yardımı](#updatable-help-system)
- [Gelişmiş çevrimiçi Yardım](#enhanced-online-help)
- [CIM tümleştirme](#cim-integration)
- [Oturum yapılandırma dosyaları](#session-configuration-files)
- [Zamanlanan işler ve Görev Zamanlayıcı tümleştirme](#scheduled-jobs-and-task-scheduler-integration)
- [Windows PowerShell dil geliştirmeleri](#windows-powershell-language-enhancements)
- [Yeni çekirdek cmdlet'leri](#new-core-cmdlets)
- [Varolan çekirdek cmdlet'leri ve sağlayıcıları geliştirmeleri](#improvements-to-existing-core-cmdlets-and-providers)
- [Uzak modülü içe aktarma ve bulma](#remote-module-import-and-discovery)
- [Gelişmiş sekmesi tamamlama](#enhanced-tab-completion)
- [Modül otomatik yükleme](#module-auto-loading)
- [Modül deneyimi geliştirmeleri](#module-experience-improvements)
- [Basitleştirilmiş komutu bulma](#simplified-command-discovery)
- [Gelişmiş günlüğe kaydetme, tanılama ve Grup İlkesi desteği](#improved-logging-diagnostics-and-group-policy-support)
- [Biçimlendirme ve çıktı geliştirmeleri](#formatting-and-output-improvements)
- [Gelişmiş konsol konak deneyimi](#enhanced-console-host-experience)
- [Yeni Cmdlet ve API'leri barındırma](#new-cmdlet-and-hosting-apis)
- [Performans iyileştirmeleri](#performance-improvements)
- [RunAs ve paylaşılan Host desteği](#runas-and-shared-host-support)
- [Özel karakter işleme geliştirmeleri](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell iş akışı
Windows PowerShell iş akışı Windows PowerShell için Windows Workflow Foundation kazandırır. İş akışı XAML veya Windows PowerShell dilde yazmak ve bir cmdlet çalıştırmak gibi çalıştırabilirsiniz. [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i workflw komutları alır ve [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet'i iş akışları için Yardım alır.

Uzun süre çalışan, yinelenebilir, sık, paralelleştirilebilir, kesilebilir, suspendable ve yeniden başlatılabilir multicomputer yönetim etkinlik iş akışlarıdır. İş akışları, bir ağ kesintisi, Windows yeniden başlatma veya elektrik kesintisi gibi bir kasıtlı olarak veya yanlışlıkla kesinti gelen ettirilebilir.

İş akışları da taşınabilir; Bunlar yüklenebilir olarak dışa veya XAML dosyalarını içeri aktarıldı. İş akışı veya etkinlikleri temsilci veya bağımlı kullanıcılar tarafından çalıştırılacak bir iş akışında izin veren özel oturum yapılandırmaları yazabilirsiniz.

Windows PowerShell iş akışının avantajları aşağıda verilmiştir

- Otomasyon sıralı, uzun süre çalışan görevler.

- **Uzun süre çalışan görevler Uzaktan izleme**. Durumunu ve ilerlemesini etkinliklerin herhangi bir zamanda görünür.

- **Multicomputer yönetimi.** Aynı anda görevlerini yüzlerce yönetilen düğüme iş akışları olarak çalıştırın. Windows PowerShell iş akışı içeren yerleşik bir kitaplık ortak yönetim parametrelerinin gibi **PSComputerName**, çoklu bilgisayar yönetimi senaryoları etkinleştirin.

- **Karmaşık işlemlere yürütülmesi tek bir görev.** Tüm uçtan uca senaryoda tek bir iş akışı ile uygulayan ilgili betikleri birleştirebilirsiniz.

- **Kalıcılık.** : bir iş akışı kaydedildi (onay işaret iş akışını en baştan yeniden başlatmak yerine son kalıcı görevi (veya denetim noktası) iş akışı devam edebilmek için yazar tarafından tanımlanan belirli zamanlarda ya da).

- **Sağlamlık.** Otomatik hatadan kurtarma. İş akışları planlanmış ve planlanmamış yeniden başlatmalarda. İş akışı yürütme askıya alma ve son Kalıcılık noktası iş akışını sürdürme. İş akışı yazarları başarısız olması durumunda bir veya daha fazla yönetilen düğümde yeniden çalıştırılacak belirli etkinlikleri belirleyebilirsiniz.

- **Özelliği bağlantısını kesmek için yeniden bağlanın ve bağlantısı kesilmiş oturumlarında çalıştırırlar.** Kullanıcılar bağlanabilir ve iş akışı sunucu bağlantısını kesin, ancak iş akışı sürekli olarak çalışır. İstemci bilgisayar oturumunu veya istemci bilgisayarı yeniden başlatın ve iş akışını kesintiye uğratmadan iş akışı yürütme başka bir bilgisayardan izleyebilirsiniz.

- **Zamanlama.** Herhangi bir Windows PowerShell cmdlet veya betik gibi iş akışı görevleri zamanlanabilir.

- **İş akışı ve bağlantı azaltma.** İş akışı yürütme ve düğümlerin bağlantılarını, böylece ölçeklenebilirlik ve yüksek kullanılabilirlik senaryolarını etkinleştirme kısıtlanan.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Erişimi
Windows PowerShell Web erişimi kullanıcıların bir web tabanlı konsolda Windows PowerShell komutları ve komut dosyaları çalıştırmasına olanak sağlayan bir Windows Server 2012 özelliğidir. Web tabanlı konsol kullanan cihazları, Windows PowerShell, uzaktan yönetim yazılımı veya tarayıcı eklentisi yüklemelerini gerektirmez. Gerekli olan tek şey düzgün yapılandırılmış Windows PowerShell Web erişimi ağ geçidi ve JavaScript destekleyen ve tanımlama bilgilerini kabul eden bir istemci cihazdır.

Daha fazla bilgi için bkz: [Windows PowerShell Web erişimi dağıtma](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Yeni Windows PowerShell ISE Özellikleri
Windows PowerShell 3.0, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) için IntelliSense, Göster komut penceresinde, birçok yeni özellik, bir birleşik Konsol bölmesinde, parçacıkları, ayraç eşleştirme genişletme-daraltma bölümleri, otomatik kayıt, son kullanılan öğeler Liste, zengin kopyalama, blok kopyalama ve Windows PowerShell komut dosyası iş akışları yazmak için tam destek. Daha fazla bilgi için bkz: [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/en-us/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Microsoft .NET Framework 4 için destek
Windows PowerShell ortak dil çalışma zamanı 4.0 karşı yerleşik olarak bulunur. Cmdlet, komut dosyası ve iş akışı yazarları yeni Microsoft .NET Framework 4 sınıfları içeren uygulama uyumluluğu ve dağıtım, Yönetilen Genişletilebilirlik Çerçevesi, paralel ağ, bilgi işlem, özelliklerle Windows Windows PowerShell'de kullanabilirsiniz Communication Foundation ve Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Windows önyükleme ortamı için destek
Windows PowerShell 3.0, Windows Önyükleme Ortamı (Windows PE) 4.0 Windows 8 için isteğe bağlı bir bileşenidir. Windows PE hiçbir işletim sistemi ve Windows yüklemesine hazırlayan bilgisayar başlatıldığında en az bir işletim sistemi ' dir. Windows PE bölümü için kullanılabilir ve sabit sürücüyü biçimlendirmek, disk görüntüleri bir bilgisayara kopyalayın ve bir ağ paylaşımından Windows Kurulum başlatılamadı. Windows PowerShell 3.0, dağıtım, tanılama ve kurtarma senaryolarını yönetmek için Windows PE üzerinde kullanılabilir.

### <a name="disconnected-sessions"></a>Bağlantısı kesik oturumlar
Windows PowerShell 3. 0'den itibaren New-PSSession cmdlet'i kullanarak oluşturduğunuz kalıcı kullanıcı yönetilen oturumları ("Pssessions'dan") uzak bilgisayarda kaydedilir. Artık, oluşturuldukları sırada oturum bağımlı değildir.

Artık oturumda çalışan komutlar kesintiye uğratmadan oturumu bağlantısını kesebilirsiniz. Oturumu kapatın ve bilgisayarınızı kapatın. Daha sonra aynı veya farklı bir bilgisayara farklı bir oturumdan oturuma bağlanabilirsiniz.

**ComputerName** parametresinin [Get-PSSession](https://technet.microsoft.com/en-us/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet'i şimdi alır bilgisayara bağlanan kullanıcının oturumlara farklı bir bilgisayara farklı bir oturumda başlatılmış olsa bile. Oturumlara bağlamak, komutları sonuçlar almak, yeni komutları başlatın ve oturum bağlantısını kesebilir.

Bağlantısı kesilen oturumlara özelliğini desteklemek için yeni cmdlet'ler eklenmiştir dahil olmak üzere [Disconnect-PSSession](https://technet.microsoft.com/en-us/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/en-us/library/b803dd29-f208-4079-80d4-db04d778f060), ve alma-PSSession ve yeni parametreler eklenmiştir Pssessions'dan, gibi yönetme cmdlet'leri **InDisconnectedSession** parametresinin [Invoke-Command](https://technet.microsoft.com/en-us/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet'i.

Bağlantısı kesilen oturumlara özelliği yalnızca her ikisi de bilgisayarların kaynaklanan ("istemci") ve bağlantı ("server") ucunun sonlandırma Windows PowerShell 3.0 çalıştırırken desteklenir.

### <a name="robust-session-connectivity"></a>Robust Session Connectivity
Windows PowerShell 3.0 istemci ve sunucu arasındaki bağlantı beklenmeyen zararları algılar ve bağlantıyı yeniden kurmak ve yürütme otomatik olarak devam dener. Ayrılan sürede istemci-sunucu bağlantısı kurulamıyor, kullanıcı bildirimi ve oturum bağlantısı kesilir. Yeniden bağlanma girişimi sırasında Windows PowerShell kullanıcıya sürekli geri bildirim sağlar.

Bağlantısı kesilmiş bir oturuma Invokecommand kullanılarak başlatıldıysa, Windows PowerShell için yeniden bağlanın ve yürütme sürdürmek daha kolay hale getirmek bağlantısı kesilmiş bir oturuma bir işi oluşturur.

Bu özellikleri daha güvenilir ve kurtarılabilir remoting deneyimi sağlar ve iş akışları gibi sağlam oturumları gerektiren uzun süre çalışan görevleri gerçekleştirmek kullanıcıların.

### <a name="updatable-help-system"></a>Güncelleştirilebilir Yardımı
Cmdlet'leri için güncelleştirilmiş Yardım dosyalarını modüllerinizi indirebilirsiniz. [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet en yeni Yardım dosyalarını tanımlar, Internet'ten indirir, bunları ayıklar, bunları doğrular ve bunları modülü için doğru dile özgü dizinde yükler.

Güncelleştirilmiş Yardım dosyalarını kullanmak için yalnızca yazın `Get-Help`. Windows veya Windows PowerShell yeniden başlatmanız gerekmez. $Pshome dizininde modülleri için Yardımı güncelleştirmek için Windows PowerShell'i "Yönetici olarak çalıştır" seçeneğiyle başlatın.

Internet erişimi ve güvenlik duvarı arkasında kullanıcıların, yeni olmayan kullanıcıları desteklemek üzere [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet'i bir dosya paylaşımı gibi bir dosya sistemi dizinine Yardım dosyalarını indirir. Kullanıcılar daha sonra kullanabilir [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) dosya paylaşımından güncelleştirilmiş Yardım dosyaları almak için cmdlet.

Kullanabileceğiniz [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet'i Yardımı güncelleştirmek için tüm dosyaları veya belirli modüller tüm desteklenen UI kültürü. Hatta koyabilirsiniz bir [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Windows PowerShell profilinizde komutu. Varsayılan olarak, Windows PowerShell modülü için Yardım dosyaları en fazla günde bir kez yükler.

Windows 8 ve Windows Server 2012 modülleri Yardım dosyalarını içermez. En son Yardım dosyalarını indirmek için şunu yazın `Update-Help`. Daha fazla bilgi için türü `Get-Help` (parametresiz) veya bkz [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Bir cmdlet için Yardım dosyalarını bilgisayarda yüklü olmadığında [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet artık otomatik olarak oluşturulan Yardımı görüntüler. Otomatik olarak oluşturulan Yardım komut sözdizimi ve kullanımıyla ilgili yönergeleri içerir [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet Yardım dosyalarını yükleyin.

Tüm modül yazarına güncelleştirilebilir Yardımı için kendi modülü destekler. Yardım dosyaları dahil modüldeki ve bunları güncelleştirin veya Yardım dosyalarını atlayın ve bunları yüklemek için güncelleştirilebilir Yardım'ı kullanmak için güncelleştirilebilir Yardımı kullanın. Güncelleştirilebilir Yardımı destekleme hakkında daha fazla bilgi için bkz: [güncelleştirilebilir Yardımı destekleme](http://go.microsoft.com/FWLink/?LinkID=242129) MSDN'de.

### <a name="enhanced-online-help"></a>Gelişmiş çevrimiçi Yardım
Windows PowerShell çevrimiçi Yardım, tüm kullanıcılar için değerli bir kaynak olmakla birlikte bulunmayan veya güncelleştirilmiş Yardım dosyaları yükleyemiyor kullanıcıları için özellikle önemlidir.

Herhangi bir Windows PowerShell cmdlet'i için çevrimiçi Yardım almak için şunu yazın:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell, varsayılan Internet tarayıcınız Yardım konusunun çevrimiçi sürümünü açar.

**Get-Help-çevrimiçi** özelliği Windows PowerShell 3. 0'ı şimdi daha güçlü bile cmdlet için Yardım dosyalarını bilgisayarda yüklenmediğinde çalıştığından. **Get-Help-çevrimiçi** özelliği cmdlet'ler ve gelişmiş işlevler HelpUri özelliğinden Yardım konusunun URI'sini alır.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Windows PowerShell 3. 0'den itibaren C# cmdlet'leri yazarları doldurabilirsiniz **HelpUri** oluşturarak özelliği bir **HelpUri** cmdlet Sınıf özniteliği. Gelişmiş işlevler yazarları tanımlayabilirsiniz bir **HelpUri** özelliği **CmdletBinding** özniteliği. Değeri **HelpUri** özelliği "http" veya "https" ile başlamalıdır.

Ayrıca ekleyebilirsiniz bir **HelpUri** bir XML temelli cmdlet Yardım dosyasının ilk ilgili bağlantı değeri veya. Bir işlevdeki açıklama tabanlı Yardım bağlantısını yönergesi.

Çevrimiçi Yardımı destekleme hakkında daha fazla bilgi için bkz: [çevrimiçi Yardımı destekleme](http://go.microsoft.com/fwlink/?LinkId=242132) MSDN'de.

### <a name="cim-integration"></a>CIM tümleştirme
Ortak Bilgi Modeli (CIM için destek sistemler, ağlar, uygulamalar ve hizmetler için ortak tanımlara yönetim bilgilerini sağlayan exchange arasında yönetim bilgisi vermeden), Windows PowerShell 3.0 içerir heterojen sistemler. Windows PowerShell 3.0, yeni veya var olan CIM sınıflarını, komutları temel Windows PowerShell cmdlet'leri yazma özelliği de dahil olmak üzere CIM desteği CIM .NET Framework desteği, XML dosyalarını cmdlet tanımına dayalı. API, CIM Yönetimi cmdlet'leri ve WMI 2.0 sağlayıcıları.

### <a name="session-configuration-files"></a>Oturum yapılandırma dosyaları
Windows PowerShell 3. 0'den başlayarak, bir dosyayı kullanarak özel bir oturum yapılandırması tasarlayabilirsiniz. Yeni oturum yapılandırma dosyası modüllerine, komut dosyaları da dahil olmak üzere oturum yapılandırması kullanan oturumları ortamının belirlemenize olanak tanır ve biçim dosyalarını modüllerine hangi cmdlet'leri ve dil öğeleri kullanıcılar kullanabilir, oturumlara yüklenir ve komut dosyaları çalıştırabilirler ve hangi değişkenleri görürler.

Hangi kullanıcıların yalnızca cmdlet'ler belirli bir modülden çalıştırabilirsiniz bir oturum ya da kullanıcıların tam dil, erişimi olan tüm modülleri ve erişim gelişmiş görevler gerçekleştirmek komut dosyalarına sahip bir oturum tasarlayabilirsiniz.

Windows PowerShell önceki sürümlerinde, bu düzeyde denetimi yalnızca bir C# programı veya karmaşık başlatma komut dosyası yazabilirsiniz olan aşağıdakiler için kullanılabilir. Şimdi, herhangi bir bilgisayarda Administrators grubunun üyesi bir yapılandırma dosyası kullanarak bir oturum yapılandırması özelleştirebilirsiniz.

Bir oturum yapılandırma dosyası oluşturmak üzere kullanmanız [yeni PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet'i. Bir oturum yapılandırması oturum yapılandırma dosyasını uygulamak için kullanmak [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) veya [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlet'leri.

Daha fazla bilgi için bkz: [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) ve [yeni PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Zamanlanan işler ve Görev Zamanlayıcı tümleştirme
Artık Windows PowerShell arka plan işleri zamanlamak ve bunları Windows PowerShell ve Görev Zamanlayıcı yönetin.

Windows PowerShell arka plan işleri Görev Zamanlayıcı görevlerini ve yararlı bir karma olan Windows PowerShell zamanlanan işleri.

Windows PowerShell arka plan işleri gibi zamanlanmış işler arka planda zaman uyumsuz olarak çalıştırın. Tamamlanan zamanlanmış işler örneklerini gibi iş cmdlet'lerini kullanarak yönetilebilir [başlangıç işi](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) ve [Get-Job](https://technet.microsoft.com/en-us/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Görev Zamanlayıcı görevlerini gibi tek seferlik veya yinelenen bir zamanlamaya göre veya yanıt olarak bir eylem veya olay zamanlanmış işler çalıştırabilirsiniz. Görüntülemek ve Görev Zamanlayıcı zamanlanmış işlerde yönetebilir, etkinleştirmek ve bunları, bunları çalıştırmak veya şablon olarak kullanın ve koşulları altında işler başlamadan ayarlayın gerektiği gibi devre dışı bırakın.

Ayrıca, zamanlanmış işler bunları yönetmek için cmdlet'ler özelleştirilmiş bir dizi gelir. Cmdlet'ler, oluşturma, düzenleme, yönetmek, devre dışı bırak ve zamanlanan işleri yeniden etkinleştirmek, zamanlanmış işi Tetikleyicileri oluşturma ve zamanlanmış işi seçeneklerini ayarlama olanak tanır.

Zamanlanan işler hakkında daha fazla bilgi için bkz: [about_Scheduled_Jobs](https://technet.microsoft.com/en-us/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Windows PowerShell dil geliştirmeleri
Windows PowerShell 3.0 daha basit ve kullanmak için ve ortak hatalarını önlemek için daha kolay dili sağlamak üzere tasarlanmış birçok özellik içerir. Özellik numaralandırma, sayısı ve uzunluğu özelliklerinin skaler nesneler, yeni yeniden yönlendirme işleçleri, $Using kapsam değiştiricisi, PSItem biçimlendirme otomatik değişken, esnek komut dosyası, değişkenleri, Basitleştirilmiş özniteliği özniteliklerini geliştirmeler bağımsız değişkenler, sayısal komut adları, Dur ayrıştırma işleci, geliştirilmiş dizi sıçratmaya, yeni bit işleçleri, sıralı sözlükler, PSCustomObject atama ve geliştirilmiş açıklama tabanlı Yardım.

### <a name="new-core-cmdlets"></a>Yeni çekirdek cmdlet'leri
Yeni cmdlet'leri zamanlanmış işler, bağlantısı kesilmiş oturumları, CIM tümleştirme ve güncelleştirilebilir Yardım sistemi yönetmek için cmdlet'leri dahil olmak üzere Windows PowerShell çekirdeği yüklemesine eklenmiştir.

|||
|-|-|
|Add-JobTrigger|New-JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Devre dışı bırak-ScheduledJob|New-ScheduledJobOption|
|Disconnect-PSSession|New-WinEvent|
|Enable-JobTrigger|Receive-PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Çağırma AsWorkflow|Göster komutu|
|Çağırma CimMethod|Show-ControlPanelItem|
|Çağırma RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|CimInstance yeni|Engellemesini dosyası|
|Yeni-CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|New-IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Varolan çekirdek cmdlet'leri ve sağlayıcıları geliştirmeleri
Windows PowerShell 3.0 Basitleştirilmiş söz dizimi ve aşağıdaki cmdlet'ler yeni parametreleri de dahil olmak üzere mevcut cmdlet'leri için yeni özellikler içerir: bilgisayar cmdlet'leri, CSV cmdlet'leri, Get-Childıtem, Get-Command, Get-içerik, Get-geçmişi, ölçü-nesnesi, güvenlik cmdlet, Select-Object, Seç-dize, bölünmüş yolu, Start-işlem, t-Object, Bağlantıyı Sına Üye Ekle ve WMI cmdlet'leri.

Windows PowerShell sağlayıcıları Ayrıca önemli ölçüde, web barındırma için Güvenli Yuva Katmanı (SSL) sertifikalarını yönetmek için sertifika sağlayıcı desteği de dahil olmak üzere geliştirilmiş, kimlik bilgisi, kalıcı ağ sürücülerini ve alternatif veri akışları için destek dosya sistemi sürücülerine.

### <a name="remote-module-import-and-discovery"></a>Uzak modülü içe aktarma ve bulma
Windows PowerShell 3.0 modülü bulma, içeri aktarma ve uzak bilgisayarlarda örtük remoting özelliklerini genişletir. Modül cmdlet modülleri uzak bilgisayarlarda alın ve Windows PowerShell uzaktan iletişimini kullanarak uzak veya yerel bilgisayarda modülleri alın. Yeni CIM oturum desteği, uzak bilgisayarda örtük olarak çalıştırmak yerel bilgisayarda komutları içeri aktararak Windows olmayan bilgisayarları yönetmek için CIM ve WMI kullanmanıza olanak sağlar.

Daha fazla bilgi için için Yardım konularına bakın [Get-Module](https://technet.microsoft.com/en-us/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) ve [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet'leri.

### <a name="enhanced-tab-completion"></a>Gelişmiş sekmesi tamamlama
Şimdi sekme tamamlama Windows PowerShell konsolunda cmdlet'leri, parametreleri, parametre değerlerini, listeleme, .NET Framework türleri, COM nesneleri, gizli dizinler ve daha fazla adlarını tamamlar. Sekme tamamlama özelliği, tamamen yeni Ayrıştırıcı ve bellek içi ayrıştırma ağacı ve Orta çizgi sekme tamamlama dahil olmak üzere daha fazla senaryoları desteklemek için soyut söz dizimi ağaç göre yeniden yazılmıştır.

### <a name="module-auto-loading"></a>Modül otomatik yükleme
[Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i şimdi alır tüm cmdlet'ler ve İşlevler bilgisayarda yüklü olan tüm modüllerdeki dahi modülü geçerli oturuma içe aktarılmaz.

Gereksinim duyduğunuz cmdlet'i aldığınızda, bunu hemen modülleriniz almadan kullanabilirsiniz. Modüldeki herhangi bir cmdlet'i kullandığınızda, Windows PowerShell modülleri artık otomatik olarak içeri aktarılır. Artık modülü aratın ve cmdlet'lerini kullanmak için almak gerekmez.

Otomatik modüllerini içeri aktarma tetiklenir cmdlet çalışan bir komut kullanarak **Get-Command** joker karakterler veya çalışan olmadan bir cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) joker karakter bulunmayan bir cmdlet için.

Etkinleştirme, devre dışı bırakın ve otomatik modülleri içeri kullanarak yapılandırma **$PSModuleAutoLoadingPreference** tercih değişkeni.

Daha fazla bilgi için bkz: [about_Modules [v4]](https://technet.microsoft.com/en-us/library/94f57429-a539-4aee-bb0d-205cd7e801f9), [tercih değişkenleri hakkında [v4]](https://technet.microsoft.com/en-us/library/31344314-be29-4286-b039-afa5460cbe8b)ve için Yardım konularını [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) ve [Import-Module ](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet'leri.

### <a name="module-experience-improvements"></a>Modül deneyimi geliştirmeleri
Windows PowerShell 3.0 Gelişmiş özellik desteği aşağıdaki yeni özellikler de dahil olmak üzere modüllerle getirir.

1. Tek tek modülleri (LogPipelineExecutionDetails) için modülü günlüğe kaydetme ve yeni "Kapatma modülü oturum" Grup İlkesi ayarı

2. Genişletilmiş modül bildirimi değerleri kullanıma modülü nesneleri

3. Yeni **ExportedCommands** özelliği de dahil olmak üzere modüllerin, her türlü komutları birleştirir modülleri, iç içe geçmiş

4. Gelişmiş bulma izin vererek dahil olmak üzere kullanılabilir (içe aktarılan beklemediğiniz) modülleri **yolu** ve **listavailable birlikte** aynı komutu parametreleri

5. Yeni **DefaultCommandPrefix** modülü kodunu değiştirmeden ad çakışmalarını önler modülü bildirimlerinde anahtar.

6. Geliştirilmiş tam gerekli modüllerini sürümü ve GUID ve otomatik gerekli modüllerini içeri aktarma ile dahil olmak üzere modülü gereksinimleri

7. Sessiz, kolaylaştırılmış işlemi [yeni ModuleManifest](https://technet.microsoft.com/en-us/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet'i.

8. Yeni **Modülü** parametresi için #Requires

9. Geliştirilmiş [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) her ikisi de cmdlet'iyle **MinimumVersion** ve **RequiredVersion** parametreleri.

### <a name="simplified-command-discovery"></a>Basitleştirilmiş komutu bulma
Artık oturumunuz için kullanılabilen komutları bulmak için tüm modülleri içeri aktarmanız gerekir. Windows PowerShell 3. 0'da, [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet'i tüm komutları yüklü olan tüm modülleri alır. Ve bir komutunu kullanırsanız, komut verir modülü oturumunuza otomatik olarak içeri aktarılır.

Yeni [Göster komutu](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet, özellikle yeni başlayanlar için tasarlanmıştır. Bir penceresindeki komutları arayabilirsiniz. Tüm komutları görüntülemek veya modülü tarafından filtre, bir düğmeye tıklayarak bir modülü içeri aktarmak, geçerli bir komut oluşturun ve ardından kopyalama veya pencere ayrılmadan komutu çalıştırmak için metin kutusu ve aşağı açılan listeleri kullanın.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Gelişmiş günlüğe kaydetme, tanılama ve Grup İlkesi desteği
Windows PowerShell 3.0 artırır günlüğe kaydetme ve olay izleme desteği Windows (ETW) günlüklerinde, bir düzenlenebilir komutları ve modülleri desteğiyle izleme **LogPipelineExecutionDetails** modülleri ve "kapatma üzerinde modülü özelliği Günlüğe kaydetme"Grup İlkesi ayarı. Parametre değerleri şimdi günlüğü ayrıntılarının günlük özelliklerini görüntüleyerek de alabilirsiniz.

### <a name="formatting-and-output-improvements"></a>Biçimlendirme ve çıktı geliştirmeleri
Yeni biçimlendirme ve çıkış geliştirmeleri tüm Windows PowerShell kullanıcıları verimliliğini artırmak. Çıktı yeniden yönlendirme tüm akışlar, türleri Format.ps1xml dosyaları, sözcük kaydırma çıkışında, olmadan dinamik olarak varsayılan biçimlendirme özel nesnelerin özelliklerini ekler Gelişmiş bir güncelleştirme türü cmdlet'i için geliştirmeler **PSCustomObject** WMI nesneleri ve heterojen nesneleri ve yöntemi aşırı bulmak için destek biçimlendirme geliştirilmiş türü.

### <a name="enhanced-console-host-experience"></a>Gelişmiş konsol konak deneyimi
Windows PowerShell Konsolu ana bilgisayar programı varsayılan olarak tek iş parçacıklı dahil olmak üzere Windows PowerShell 3.0 yeni özellikler vardır. Dosya Gezgini'nde yeni "PowerShell ile Çalıştır" seçeneğini yalnızca sağ tıklayarak sınırsız bir oturumda komut dosyalarını çalıştır olanak sağlar. Yeni konsol konak başlatma mantık Windows PowerShell daha hızlı başlatır ve yeni yazı tipleri tanıdık konsol penceresi deneyimini kişiselleştirmek izin verir.

Daha fazla bilgi için bkz: [about_Run_With_PowerShell](https://technet.microsoft.com/en-us/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Yeni Cmdlet ve API'leri barındırma
Yeni Cmdlet API ve barındırma API ardışık düzen disk belleği, iç içe geçmiş işlem hatları, çalışma havuzları sekme tamamlama, Windows RT, artık kullanılmayan cmdlet özniteliği ve FunctionInfo nesnesinin fiil ve isim özellikleri için ortak Gelişmiş sözdizimi ağacı (AST) API'ları ve API içerir.

### <a name="performance-improvements"></a>Performans iyileştirmeleri
Üzerinde dinamik çalışma zamanı dil (DLR) .NET Framework 4'te yerleşik yeni dil Ayrıştırıcıyı gelen Windows PowerShell önemli performans geliştirmeleri., çalışma zamanı komut dosyası derleme, altyapısı güvenilirlik yenilikleri ve değişiklikleri birlikte algoritması [Get-Childıtem](https://technet.microsoft.com/en-us/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) , kendi performansı artırır, özellikle ağ arama paylaştığında.

### <a name="runas-and-shared-host-support"></a>RunAs ve paylaşılan Host desteği
Windows PowerShell 3.0 RunAs ve paylaşılan konak özellikleri için destek içerir.

*RunAs* özelliği, Windows PowerShell iş akışı için tasarlanmış bir oturum yapılandırması paylaşılan bir kullanıcı hesabını izniyle çalıştırmak oturumları oluşturmak kullanıcılarının olanak sağlar. Bu daha az ayrıcalıklı kullanıcıların yönetici izinlerine sahip belirli komutları ve komut dosyaları çalıştırmasına izin verir ve daha az Kıdemli kullanıcı Administrators grubuna ekleme gereksinimini azaltır.

**SharedHost** özelliği birden çok kullanıcı aynı anda bir iş akışı oturumuna bağlanabilir ve bir iş akışı ilerlemesini izlemek için birden çok bilgisayar üzerinde sağlar. Kullanıcılar bir bilgisayarda bir iş akışı başlatmalarını ve sonra başka bir bilgisayarda iş akışı oturum özgün bilgisayardan oturumun bağlantısını kesmeden bağlanın. Kullanıcıları ve aynı oturum yapılandırması kullanan aynı izinlere sahip olmalıdır. Daha fazla bilgi için "Çalıştıran bir Windows PowerShell iş akışında" Windows PowerShell iş akışı ile çalışmaya başlama bakın.

### <a name="special-character-handling-improvements"></a>Özel karakter işleme geliştirmeleri
Yorumlar ve özel karakterler düzgün işlemek için Windows PowerShell 3.0 yeteneklerini geliştirmek için **LiteralPath** yolları bulunan özel karakterleri işler, parametre sahip neredeyse tüm cmdlet'leri üzerinde geçerli bir  **Yol** parametresi, yeni dahil olmak üzere [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) ve [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet'leri. Ayrıştırıcının da backtick karakter işlenmesini artırmak için özel bir mantık içerir (\`) ve dosya adlarını ve yollarını köşeli ayraç.

## <a name="see-also"></a>Ayrıca bkz:
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)