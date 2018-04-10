---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Yazılım Yüklemeleri ile Çalışma
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-software-installations"></a>Yazılım Yüklemeleri ile Çalışma

Windows Installer kullanmak üzere tasarlanmış uygulamaları WMI aracılığıyla kişinin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar bugün Windows Installer kullanın. Windows Installer yüklenebilir uygulamaları ile çalışmak için standart teknikleri yelpazedeki sağladığından, bu uygulamaları öncelikle bulunacağınız konularına odaklanır. Alternatif kurulum yordamları kullanan uygulamalar genellikle Windows Installer tarafından yönetilmez. Bu uygulamalarla çalışmak için belirli teknikler yükleyici yazılım ve uygulama geliştiricisi tarafından kararlara bağlıdır.

> [!NOTE]
> Uygulama dosyaları genellikle bilgisayara kopyalayarak yüklenen uygulamalar, burada açıklanan teknikleri kullanarak tarafından yönetilemez. "Çalışma ile dosyalar ve klasörler" bölümünde açıklanan teknikleri kullanarak bu uygulamaları dosya ve klasörleri olarak yönetebilirsiniz.

### <a name="listing-windows-installer-applications"></a>Windows Installer uygulamaları listeleme

Windows Installer bir yerel veya uzak sistemde yüklü olan uygulamaları listelemek için aşağıdaki basit WMI sorgusu kullanın:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Görüntülenecek Win32_Product nesnenin özelliklerini görüntülemek için değeri olan Format-List cmdlet gibi biçimlendirme cmdlet'leri özellikleri parametresini kullanın \* (Tümü).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Ya da kullanabileceğinizi **Get-WmiObject filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin. Bu komutta kullanılan filtresini bir WMI filtresi olduğundan, WMI Sorgu Dili (WQL) sözdizimi, Windows PowerShell sözdizimi kullanır. Bunun yerine:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

WQL boşluk ya da Windows PowerShell içinde özel bir anlamı olan eşittir işareti gibi kullanılabilecek karakterleri sık sorgular unutmayın. Bu nedenle, her zaman filtresi parametresinin değeri tırnak işaretleri içine alın akıllıca olur. Windows PowerShell kaçış karakteri bir backtick de kullanabilirsiniz (\`), ancak bunu okunabilirliğini artırmak değil. Aşağıdaki komutu önceki komutu ile eşdeğerdir ve aynı sonuçları verir, ancak tüm filtre dizesi tırnak içine almak yerine özel karakterler kaçınmak için backtick kullanır.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Sizi ilgilendiren özellikleri listelemek için istenen özellikleri listelemek için biçimlendirme cmdlet'leri özelliği parametresini kullanın.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Son olarak, yalnızca adlarını bulmak için basit bir yüklü uygulamaların **biçimi genelinde** deyimi basitleştirir çıktı:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Artık Windows Installer yükleme için kullanılan uygulamalar bakmak için çeşitli yollar sahibiz rağmen biz diğer uygulamaları kabul değil. Çoğu standart uygulamaları Windows ile bunların kaldırıcı kaydetmek için Biz bu yerel Windows Kayıt Defteri'nde bulma tarafından ile çalışabilirsiniz.

### <a name="listing-all-uninstallable-applications"></a>Tüm Uninstallable uygulamaları listeleme

Bir sistem üzerinde her uygulamayı bulmak için hiçbir garanti edilen şekilde olsa da, tüm programlar Program Ekle veya Kaldır iletişim kutusunda görüntülenen listelerini bulmak mümkündür. Ekle veya Kaldır'ı bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

Ayrıca, biz uygulamaları bulmak için bu anahtarı inceleyebilirsiniz. Kaldırma anahtarını görüntülemek kolaylaştırmak için size bir Windows PowerShell sürücüsü bu kayıt defteri konumuna eşleyebilirsiniz:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** sürücüsünün köküne eşlenen **HKEY_LOCAL_MACHINE**, o sürücüye kaldırma anahtarını yolunu kullandık. Yerine **HKLM:** şu kayıt defteri yolunu kullanarak belirttiğiniz **HKLM** veya **HKEY_LOCAL_MACHINE**. Var olan bir kayıt defteri sürücüsüne kullanmanın avantajı, biz sekme tamamlama biz bunları yazmaya gerek yoktur anahtarları adlarında doldurmak için kullanabilirsiniz ' dir.

Biz şimdi "hızla ve kolayca uygulama yüklemeleri için aramak için kullanılan Uninstall" adlı bir sürücüye sahip. Biz kaldırma kayıt defteri anahtarlarında sayısı sayım tarafından yüklenen uygulamaların sayısı bulabilirsiniz: Windows PowerShell sürücüsü:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Biz bu uygulamaların daha fazla listesini teknikler, çeşitli kullanarak itibaren arayabilirsiniz **Get-Childıtem**. Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Uzun Buraya bir değişken adı daha anlaşılır olması için kullanıyoruz. Gerçek kullanımda uzun adlar kullanmak için bir neden yoktur. Değişken adları için sekme tamamlama kullanabilmenize karşın, 1-2 karakter adları hızı için de kullanabilirsiniz. Kod yeniden kullanım için geliştirirken uzun, açıklayıcı adlar en kullanışlıdır.

Kayıt defteri anahtarları kaldırma altındaki kayıt defteri girdilerini değerlerini görüntülemek için kayıt defteri anahtarlarının GetValue yöntemini kullanın. Yönteminin değerini kayıt defteri girdisini adıdır.

Örneğin, uygulamaların görünen adları Uninstall anahtarında bulmak için aşağıdaki komutu kullanın:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Bu değerler benzersiz garantisi yoktur. Aşağıdaki örnekte, "Windows Media Kodlayıcısı 9 Series" iki yüklü öğeleri görünür:

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a>Uygulamaları yükleme

Kullanabileceğiniz **Win32_Product** uzaktan veya yerel olarak Windows Installer paketleri yüklemek için sınıf.

> [!NOTE]
> Bir uygulamayı yüklemek için Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde Windows PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.

WMI alt sistemi, Windows PowerShell yolları anlamıyor olduğundan Uzaktan Yükleme, bir Evrensel Adlandırma Kuralı (UNC) ağ yolu .msi paketin yolunu belirtmek için kullanın. Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımında \\ \\AppServ\\dsp PC01, uzak bilgisayarda Windows PowerShell komut isteminde aşağıdaki komutu yazın:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Windows Installer teknolojisi kullanmayın uygulamalar otomatik dağıtım için kullanılabilir uygulamaya özgü yöntemleri sahip olabilir. Dağıtım Otomasyon için bir yöntem olup olmadığını belirlemek için uygulamanın belgelerine bakın veya uygulama satıcısının destek sistem başvurun. Uygulamanın satıcısına özellikle uygulama yükleme Otomasyon için tasarım değil olsa bile bazı durumlarda, otomasyon için bazı teknikleri yükleyici yazılım üreticisine sahip olabilir.

### <a name="removing-applications"></a>Uygulamaları kaldırma

Windows PowerShell kullanarak bir Windows Installer paketi kaldırma yaklaşık bir paket yükleme olarak aynı şekilde çalışır. Kaldırılacak paketin adına göre seçen örnek aşağıda verilmiştir; Bazı durumlarda Filtrele daha kolay olabilir **Identifyingnumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Diğer uygulamaların kaldırılması bile yerel olarak işiniz bittiğinde nedenle oldukça basit değil. Biz çıkartarak bu uygulamalar için komut satırı kaldırma dizeleri bulabilirsiniz **UninstallString** özelliği. Bu yöntem, eski programları kaldırma anahtarı altında görünen ve Windows Installer uygulamaları için çalışır:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

İsterseniz, çıktı görünen ada göre filtreleyebilirsiniz:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Ancak, bu dizeler doğrudan bazı değişiklik yapmadan Windows PowerShell isteminden kullanılamayabilir.

### <a name="upgrading-windows-installer-applications"></a>Windows Installer uygulamalarını yükseltme

Uygulama yükseltme için uygulama yükseltme paketi uygulama ve yolun adını bilmeniz gerekir. Bu bilgi ile tek bir Windows PowerShell komut uygulamayla yükseltebilirsiniz:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```