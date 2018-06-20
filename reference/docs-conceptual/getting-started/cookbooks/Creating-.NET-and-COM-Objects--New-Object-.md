---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: .NET ve COM nesnelerini yeni nesne oluşturma
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953397"
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET ve COM nesnelerini (nesne yeni) oluşturma

Yazılım bileşenleri birçok sistem yönetim görevlerini gerçekleştirmenize olanak sağlayan .NET Framework ve COM arabirimleri ile vardır. Windows PowerShell cmdlet'lerini kullanarak gerçekleştirdiği görevleri sınırlı olduklarından bu bileşenlerin kullanmanıza olanak sağlar. Birçok ilk sürümünde Windows PowerShell cmdlet'lerini uzak bilgisayarlarda çalışmaz. Olay günlükleri .NET Framework kullanarak yönetirken bu sınırlamaya geçici almak göstereceğiz **System.Diagnostics.EventLog** Windows powershell'den doğrudan sınıfı.

### <a name="using-new-object-for-event-log-access"></a>Yeni nesne olay günlüğüne erişimi için kullanma

.NET Framework sınıf kitaplığı adlı bir sınıf içerir **System.Diagnostics.EventLog** olay günlüklerini yönetmek için kullanılabilir. .NET Framework sınıfının yeni bir örneğini kullanarak oluşturabileceğiniz **New-Object** cmdlet'iyle **TypeName** parametresi. Örneğin, aşağıdaki komut, bir olay günlüğü başvuru oluşturur:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Örnek komut EventLog sınıfının bir örneği oluşturdu ancak herhangi bir veri içermez. Belirli bir olay günlüğü belirtmedi olmasıdır. Gerçek bir olay günlüğü nasıl alıyorum?

#### <a name="using-constructors-with-new-object"></a>Yeni-nesnesiyle oluşturucular kullanma

Belirli bir olay günlüğü'ne başvurun için günlük adını belirtmeniz gerekir. **Yeni nesne** sahip bir **bağımsızdeğişkenListesi** parametresi. Bu parametre için değerler olarak geçirdiğiniz bağımsız değişkenler nesnesi özel başlangıç yöntemi tarafından kullanılır. Çağrılan yöntemi bir *Oluşturucusu* çünkü nesnesi oluşturmak için kullanılır. Örneğin, uygulama günlüğüne bir başvuru almak için 'Uygulaması' dize bağımsız değişken olarak belirtin:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> .NET Framework temel sınıfları çoğunu System ad alanında bulunan olduğundan, Windows PowerShell belirttiğiniz typename yönelik bir eşleşme bulamazsanız System ad alanında belirtin sınıfları bulmak otomatik olarak çalışacaktır. Başka bir deyişle, System.Diagnostics.EventLog yerine Diagnostics.EventLog belirtebilirsiniz.

#### <a name="storing-objects-in-variables"></a>Nesne değişkenleri depolanması

Geçerli Kabuğu'nda kullanabilmeniz için bir nesneye başvuru depolamak isteyebilirsiniz. Windows PowerShell, çok sayıda ardışık çalışmak yapmak değişkenleri gereksinimini lessening olanak tanır ancak bazen nesnelerin referansları değişkenleri depolamak, bu nesneleri işlemek daha kullanışlı hale getirir.

Windows PowerShell, aslında nesneler adlandırılmış değişkenleri oluşturmanızı sağlar. Geçerli bir Windows PowerShell komut çıkışı bir değişkene depolanabilir. Değişken adları, her zaman $ ile başlar. Uygulama günlüğü başvurusu $AppLog adlı bir değişkende depolamak istiyorsanız adını yazın değişkeni ve ardından bir eşittir işareti ve uygulama günlüğü nesnesi oluşturmak için kullanılan komutu yazın:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Ardından $AppLog yazarsanız, uygulama günlüğüne içerdiği görebilirsiniz:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Yeni nesne ile bir uzak olay günlüğü erişme

Önceki bölümde kullanılan komutlar yerel bilgisayarı hedef; **Get-EventLog** cmdlet, yapabilir. Uzak bir bilgisayarda uygulama günlüğüne erişmek için hem günlük adını ve bir bilgisayar adı (veya IP adresi) bağımsız değişken olarak sağlamanız gerekir.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Biz $RemoteAppLog değişkeninde depolanan bir olay günlüğü başvuru sahip olduğunuza göre hangi görevleri biz üzerinde gerçekleştirebilirsiniz?

#### <a name="clearing-an-event-log-with-object-methods"></a>Bir olay günlüğü nesne yöntemleri ile temizleme

Nesneler genelde görevleri gerçekleştirmek için çağrılan yöntemler vardır. Kullanabileceğiniz **Get-üye** bir nesneyle ilişkilendirilmiş yöntemlerini görüntülemek için. Seçilen çıkış ve aşağıdaki komutu bazı olay günlüğüne sınıfı yöntemlerinin göster:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

**Clear()** yöntemi, olay günlüğü temizlemek için kullanılabilir. Yöntemin bağımsız değişkenleri gerektirmiyor olsa bile bir yöntem çağrılırken, her zaman yöntem adı parantez tarafından izlemelisiniz. Bu Windows PowerShell yöntemi ve olası bir özellik aynı ada sahip arasında ayrım sağlar. Çağırmak için aşağıdaki komutu yazın **Temizle** yöntemi:

```
PS> $RemoteAppLog.Clear()
```

Günlük görüntülemek için aşağıdakini yazın. Olay günlüğü temizlendi ve şimdi 262 yerine 0 girişlerine sahip görürsünüz:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Yeni nesne oluşturma COM nesneleri
Kullanabileceğiniz **New-Object** Bileşen Nesne Modeli (COM) bileşenleriyle çalışmak üzere. Çoğu sistemde yüklü ActiveX uygulamalara Internet Explorer gibi Windows Komut Dosyası Sistemi'ni (WSH) dahil çeşitli kitaplıkları bileşenleri arasındadır.

**Yeni nesne** .NET Framework COM nesneleri çağrılırken mu aynı sınırlamalara sahiptir COM nesneleri oluşturmak için .NET Framework çalışma zamanı aranabilir sarmalayıcılar kullanır. Bir COM nesnesi oluşturmak için belirtmeniz gerekir **ComObject** program tanımlayıcısı parametresiyle veya *ProgID* kullanmak istediğiniz COM sınıfı. COM kullanın ve ProgID bir sistemde kullanılabilir nelerdir belirleme sınırlamaları tam bir irdelemesi ve bu kullanıcı kılavuzu kapsamında değildir, ancak en iyi bilinen nesneleri ortamlarından WSH gibi Windows PowerShell içinde kullanılabilir.

Bu ProgID belirterek WSH nesneleri oluşturabilirsiniz: **wscript.Shell nesnesinin**, **WScript.Network**, **Scripting.Dictionary**, ve  **Scripting.FileSystemObject**. Aşağıdaki komutlar, bu nesnelerin oluşturun:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Bu sınıfların işlevselliğinin büyük kısmını yapıldığında rağmen başka şekillerde kullanılabilir Windows PowerShell içinde kısayol oluşturma gibi birkaç görevleri WSH sınıflarını kullanarak yapmak hala daha kolaydır.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Bir masaüstü kısayolu wscript.Shell nesnesinin ile oluşturma

Bir COM nesnesi ile kolayca gerçekleştirilebilir bir görev bir kısayol oluşturma. Bir kısayol masaüstünüzde giriş klasörü bağlanan için Windows PowerShell oluşturmak istediğinizi varsayalım. İlk olarak bir başvuru oluşturmanıza gerek **wscript.Shell nesnesinin**, hangi adlı bir değişkende depolayacak mı **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Nesne üyeleri yazarak gözatabilirsiniz get-üye COM nesneleri ile çalışır:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-üye** isteğe sahip **Inputobject** yerine yöneltme giriş sağlamak için kullanabileceğiniz parametre **Get-üye**. Bunun yerine komutu kullandıysanız yukarıda gösterildiği gibi çıktı aynı elde edebileceğiniz **Get-üye - Inputobject $WshShell**. Kullanırsanız **Inputobject**, bağımsız değişkeni tek bir öğe işler. Bir değişkende birden fazla nesneniz varsa buna **Get-üye** nesnelerinin bir dizisi değerlendirir. Örneğin:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**Wscript.Shell nesnesinin CreateShortcut** yöntemi tek bir değişken oluşturmak için kısayol dosyasının yolu kabul eder. Masaüstü tam yolunu yazabilirsiniz, ancak daha kolay bir yolu yoktur. Masaüstü normalde Masaüstü geçerli kullanıcının giriş klasörü içinde adlı bir klasör olarak temsil edilir. Windows PowerShell sahip bir değişken **$Home** bu klasörün yolunu içerir. Biz bu değişkeni kullanarak giriş klasörü yolunu belirtin ve ardından Masaüstü klasörün adını ve yazarak oluşturmak kısayol için ad ekleyin:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Bir değişken adı çift tırnak içine benzer bir şey kullandığınızda, Windows PowerShell eşleşen bir değer yerine dener. Tek tırnak işareti kullanırsanız, Windows PowerShell değişken değerini değiştirmeyi denemez. Örneğin, aşağıdaki komutları yazarak deneyin:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Şimdi adlı bir değişkene sahip olduğumuz **$lnk** yeni bir kısayol başvurusu içeriyor. Üyelerini görmek istiyorsanız, kendisine iletebildiğiniz **Get-üye**. Çıktı bizim kısayol oluşturmayı tamamlamak için kullanılacak ihtiyacımız üyeler gösterir:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Belirtmek ihtiyacımız **TargetPath**, Windows PowerShell ve ardından kısayol kaydetme uygulama klasörü olduğu **$lnk** çağırarak **kaydetmek** yöntemi. Windows PowerShell uygulama klasör yolu değişkende depolanır **$PSHome**, biz yazarak yapabilirsiniz:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Windows PowerShell Internet Explorer'dan kullanma

Birçok uygulama (uygulamalar ve Internet Explorer'ın Microsoft Office ailesi dahil) COM kullanarak otomatikleştirilebilir. Internet Explorer bazı tipik teknikleri ve COM tabanlı uygulamalarla çalışma ilgili sorunları gösterir.

Internet Explorer ProgID, belirterek bir Internet Explorer örneği oluşturma **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Bu komut, Internet Explorer'ı başlatır, ancak görünür yapmaz. Get-Process yazarsanız, Iexplore adlı bir işlem çalıştığından görebilirsiniz. Aslında, Windows PowerShell çıkarsanız işlemi çalışmaya devam eder. Bilgisayarı yeniden başlatın veya Iexplore işlemi sonlandırmak için bir aracı gibi Görev Yöneticisi'ni kullanın.

> [!NOTE]
> Ayrı işlemler Başlat COM nesneleri genellikle adlı *ActiveX yürütülebilir dosyalar*başlatıldığında bir kullanıcı arabirimi penceresi görüntülenmeyebilir veya olabilir. Bir pencere oluşturma ancak Internet Explorer gibi görünür yapmayın odak genellikle Windows Masaüstü için taşınır ve penceresi ile etkileşim için görünür yapın.

Yazarak **$IE | Get-üye**, Internet Explorer için özellikleri ve yöntemleri görüntüleyebilirsiniz. Internet Explorer penceresi görmek için yazarak Vısıble özelliği $true olarak ayarlayın:

```powershell
$ie.Visible = $true
```

Belirli bir Web adresine gidin yöntemini kullanarak sonra gidebilirsiniz:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Internet Explorer nesne modeli diğer üyeleriyle kullanarak, Web sayfasından metin içeriği almak mümkün değildir. Aşağıdaki komutu, geçerli Web sayfasının gövdesindeki HTML metin görüntülenir:

```powershell
$ie.Document.Body.InnerText
```

Internet Explorer PowerShell içinden kapatmak için kendi Quit() yöntemini çağırırsınız:

```powershell
$ie.Quit()
```

Bu kapanmaya zorlar. Hala bir COM nesnesi olarak görünen olsa bile IE değişken $ artık geçerli bir başvuru içeriyor. Bunu kullanmayı denerseniz, bir Otomasyon hatası alırsınız:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Kalan başvuru $ gibi bir komutla IE kaldırabilir ya da $null = ya da yazarak değişkeni tamamen kaldırın:

```powershell
Remove-Variable ie
```

> [!NOTE]
> ActiveX yürütülebilir dosyalar çıkmak veya bir başvuru kaldırdığınızda çalışmaya devam için ortak bir standart yoktur. Uygulamanın görünür olup, düzenlenen bir belge içine çalışıp çalışmadığını ve hatta Windows PowerShell hala çalışıp çalışmadığını gibi durumlarda, bağlı olarak uygulama olabilir veya değil sonlandırılabilir. Bu nedenle, Windows PowerShell içinde kullanmak istediğiniz yürütülebilir her ActiveX için sonlandırma davranışını test etmeniz gerekir.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>.NET Framework Sarmalanan COM nesneleri hakkında uyarılar alma

Bazı durumlarda, ilişkili bir .NET Framework bir COM nesnesi olabilir *çalışma zamanı aranabilir sarmalayıcısı* veya RCW ve bu işlem tarafından kullanılan **New-Object**. RCW davranışını normal COM nesnesi davranışından farklı olabileceğinden **New-Object** sahip bir **Strıct** RCW erişimi hakkında uyarmak için parametre. Belirtirseniz **Strıct** parametre ve ardından bir RCW kullanan bir COM nesnesi oluşturun, bir uyarı iletisi Al:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Nesne hala oluşturulur, ancak standart bir COM nesnesi olmadığını uyarılırsınız.