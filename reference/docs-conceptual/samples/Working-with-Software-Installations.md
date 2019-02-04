---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Yazılım Yüklemeleri ile Çalışma
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686729"
---
# <a name="working-with-software-installations"></a>Yazılım Yüklemeleri ile Çalışma

Windows Installer'ı kullanmak üzere tasarlanmış uygulamalar WMI'nin erişilebilir **Win32_Product** sınıfı, ancak kullanımda tüm uygulamalar Windows Yükleyici kullanmaya hemen başlayın. Windows Installer yüklenebilir uygulamalarla çalışmak için standart teknikleri yelpazedeki sağladığından, biz öncelikle bu uygulamalar üzerinde odaklanır. Alternatif kurulum yordamları kullanan uygulamalar genellikle Windows Installer tarafından yönetilmez. Bu uygulamalarla çalışmak için belirli teknik kararları uygulama geliştiricisi tarafından yapılan ve yükleyici yazılım bağlıdır.

> [!NOTE]
> Uygulama dosyaları genellikle bilgisayara kopyalayarak yüklü uygulamaları burada ele alınan teknikleri kullanarak tarafından yönetilemez. Bu uygulamalar olarak dosyalar ve klasörler "Çalışma ile dosyalar ve klasörler" bölümünde ele alınan teknikleri kullanarak yönetebilirsiniz.

### <a name="listing-windows-installer-applications"></a>Windows Installer uygulamaları listeleme

Windows Installer bir yerel veya uzak sistemde yüklü uygulamalar listelemek için aşağıdaki basit WMI sorgusunu kullanın:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Görüntülenecek Win32_Product nesne özelliklerini görüntülemek için değeri olan Format-List cmdlet'i gibi biçimlendirme cmdlet'lerinin özellikleri parametresini kullanın \* (Tümü).

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

Ya da kullanabileceğinizi **Get-WmiObject filtre** parametresini kullanarak yalnızca Microsoft .NET Framework 2. 0'ı seçin. Bu komutta kullanılan filtrede bir WMI filtresi olduğundan, Windows PowerShell sözdizimi değil WMI Sorgu Dili (WQL) söz dizimini kullanır. Bunun yerine:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

WQL boşluk ya da Windows PowerShell içinde özel bir anlamı olan eşittir işareti gibi kullanım karakterleri sık sorgular unutmayın. Bu nedenle, her zaman filtresi parametresinin değerini tırnak içine alın akıllıca olur. Windows PowerShell kaçış karakteri olan bir vurgulamasını belirtir de kullanabilirsiniz (\`), ancak bunu okunabilirliği artırmak değildir. Aşağıdaki komut önceki komutu eşdeğerdir ve aynı sonuçları döndürür, ancak tüm filtre dize Alıntısı yerine özel karakterler, kaçış için vurgulamasını belirtir kullanır.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

İlginizi çeken özelliklerini listelemek için istenen özellikleri listelemek için özellik parametresi biçimlendirme cmdlet'leri kullanın.

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

Son olarak, yalnızca adlarını bulmak için uygulamalar, basit bir yüklü **biçimi genelinde** deyimi çıkış kolaylaştırır:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Şimdi Windows Installer yükleme için kullanılan uygulamaların bakmak için çeşitli yollar vardır ancak diğer uygulamaları dikkate değil. Çoğu standart uygulamaları Windows ile kendi uninstaller kaydetmek için biz bunları Windows kayıt defterinde bulma tarafından yerel olarak çalışabilirsiniz.

### <a name="listing-all-uninstallable-applications"></a>Tüm Uninstallable uygulamaları listeleme

Bir sistemde her uygulamayı bulmak için garantili yolu olsa da, Program Ekle veya Kaldır iletişim kutusunda görüntülenen listeleri içeren tüm programları bulmak mümkündür. Ekle veya Kaldır bu uygulamalar aşağıdaki kayıt defteri anahtarında bulur:

**HKEY_LOCAL_MACHINE\\yazılım\\Microsoft\\Windows\\CurrentVersion\\kaldırma**.

Biz de uygulamaları bulmak için bu anahtarı inceleyebilirsiniz. Kaldırma anahtarı görüntülemek kolaylaştırmak için şu Windows PowerShell sürücüsünü bu kayıt defteri konumuna eşleyebilirsiniz:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> **HKLM:** sürücünün köküne eşlenen **HKEY_LOCAL_MACHINE**, bu sürücüyü kaldırma anahtar yolunu kullandık. Yerine **HKLM:** şu kayıt defteri yolunu kullanarak belirtmiş olabilirsiniz **HKLM** veya **HKEY_LOCAL_MACHINE**. Var olan kayıt defteri sürücüsüne kullanmanın avantajı biz sekme tamamlama biz bunları türüne gerek yoktur, anahtarları adlarında doldurmak için kullanabilmenizdedir.

Artık uygulama yüklemeleri için hızla ve kolayca aramak için kullanılan "Kaldır" adlı bir sürücüsü sahibiz. Kayıt defteri anahtarlarını kaldırma sayısı sayılarak yüklü uygulamaların sayısını bulabiliriz: Windows PowerShell sürücüsü:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Biz bu listeyi daha fazla uygulama çeşitli teknikler kullanarak başlayarak arayabilirsiniz **Get-Childıtem**. Uygulamaların bir listesini almak ve bunları kaydetmek için **$UninstallableApplications** değişken, aşağıdaki komutu kullanın:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Uzun Buraya bir değişken adı anlaşılması için kullanıyoruz. Gerçek kullanımda uzun adlarını kullanmak için bir neden yoktur. Değişken adları için sekme tamamlama kullanabilirsiniz, ancak 1-2 karakter adları hızı için de kullanabilirsiniz. Kod yeniden kullanımı için geliştirirken, uzun, açıklayıcı adlar ekseriyetle faydalıdır.

Kayıt defteri anahtarları kaldırma altında kayıt defteri girdilerinin değerlerini görüntülemek için kayıt defteri anahtarlarını GetValue yöntemini kullanın. Yöntem değeri kayıt defteri girişini adıdır.

Örneğin, Uninstall anahtarında uygulamaları görünen adlarını bulmak için aşağıdaki komutu kullanın:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Bu değerler benzersiz olmasını garanti yoktur. Aşağıdaki örnekte, "Windows Media Encoder 9 Serisi" yüklü iki öğe görünür:

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

Kullanabileceğiniz **Win32_Product** Windows Installer paketleri uzaktan veya yerel olarak yüklemek için sınıf.

> [!NOTE]
> Bir uygulamayı yüklemek için Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde, Windows PowerShell "Yönetici olarak çalıştır" seçeneğiyle başlatmanız gerekir.

WMI alt sistemi, Windows PowerShell yolları anlamıyor çünkü .msi paketin yolu belirtmek için bir Evrensel Adlandırma Kuralı (UNC) ağ yolu uzaktan yüklerken kullanın. Örneğin, NewPackage.msi paketini yüklemek için bulunan ağ paylaşımına \\ \\AppServ\\dsp PC01, uzak bilgisayarda Windows PowerShell komut isteminde aşağıdaki komutu yazın:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Windows Yükleyici teknolojisi kullanmayan uygulamalar, otomatik dağıtım için uygulamaya özgü yöntemleri olabilir. Bir dağıtım otomasyonunu yöntemi olup olmadığını belirlemek için uygulama için belgelere bakın veya uygulama satıcısının destek sistemi başvurun. Bazı durumlarda bile uygulamanın satıcısına özellikle uygulama için yükleme Otomasyon tasarlamak değil yükleyici yazılımın Otomasyon için bazı teknikleri olabilir.

### <a name="removing-applications"></a>Uygulamaları kaldırma

Windows PowerShell kullanarak bir Windows Installer paketi kaldırma paket yükleme yaklaşık aynı şekilde çalışır. Kaldırmak için paket adına göre seçen bir örneği aşağıda verilmiştir; Bazı durumlarda ile filtrelemek daha kolay olabilir **Identifyingnumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Diğer uygulamaları kaldırma bile yerel olarak işiniz bittiğinde konu bu kadar basit değil. Komut satırı kaldırma dizeleri için bu uygulamaları ayıklayarak bulabiliriz **UninstallString** özelliği. Bu yöntem, kaldırma anahtarı altında görünen eski programları ve Windows Installer uygulamaları için çalışır:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

İsterseniz, görünen ada göre çıkışı filtreleyebilirsiniz:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Ancak, bu dizeler Windows PowerShell isteminden bazı değişiklik yapmadan doğrudan kullanılabilir olmayabilir.

### <a name="upgrading-windows-installer-applications"></a>Windows Installer uygulamalarını yükseltme

Bir uygulamayı yükseltmek için uygulama yükseltme paketini uygulama ve yolun adını bilmeniz gerekir. Bu bilgileri kullanarak bir Windows PowerShell komutu ile bir uygulama yükseltebilirsiniz:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```