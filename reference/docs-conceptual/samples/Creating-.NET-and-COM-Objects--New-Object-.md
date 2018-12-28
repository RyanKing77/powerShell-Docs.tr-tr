---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: .NET ve COM nesneleri yeni nesne oluşturma
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406039"
---
# <a name="creating-net-and-com-objects-new-object"></a>.NET ve COM nesneleri (New-Object) oluşturma

Birçok sistem yönetim görevlerini gerçekleştirmenize olanak tanıyan .NET Framework ve COM arabirimleri ile yazılım bileşenleri vardır. Windows PowerShell cmdlet'lerini kullanarak gerçekleştirilen görevler için sınırlı olmadıklarından bu bileşenlerin kullanmanıza olanak sağlar. İlk sürümde Windows PowerShell cmdlet'lerinin birçoğunu uzak bilgisayarlarda çalışmaz. Biz bu sınırlamayı olay günlükleri, .NET Framework kullanarak yönetirken almak nasıl sürdürebileceğiniz gösterilecek **System.Diagnostics.EventLog** Windows powershell'den doğrudan sınıfı.

### <a name="using-new-object-for-event-log-access"></a>Yeni nesne için olay günlüğüne erişimi kullanma

.NET Framework sınıf kitaplığı adlı bir sınıf içeren **System.Diagnostics.EventLog** olay günlüklerini yönetmek için kullanılabilir. Kullanarak bir .NET Framework sınıfının yeni bir örneğini oluşturabilirsiniz **New-Object** cmdlet'iyle **TypeName** parametresi. Örneğin, aşağıdaki komut, bir olay günlüğü başvuru oluşturur:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Komutu EventLog sınıfının bir örneği oluşturdu ancak örneği hiçbir veri içermez. Belirli bir olay günlüğü belirtmedi olmasıdır. Gerçek bir olay günlüğü nasıl alır?

#### <a name="using-constructors-with-new-object"></a>Nesne ile yeni oluşturucular kullanma

Belirli bir olay günlüğüne başvurmak için günlüğün adını belirtmenize gerek. **Yeni nesne** sahip bir **ArgumentList** parametresi. Bu parametre için değer olarak geçirdiğiniz bağımsız değişkenleri, bir nesnenin özel başlangıç yöntemi tarafından kullanılır. Çağrılan yöntemi bir *Oluşturucusu* nesneyi oluşturmak için kullanıldığından. Örneğin, uygulama günlüğüne bir başvuru almak için 'Uygulama' dize bağımsız değişken olarak belirtin:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> .NET Framework temel sınıf çoğunu System ad alanında bulunan olduğundan, Windows PowerShell otomatik olarak belirttiğiniz tür adı için bir eşleşme bulamazsa System ad alanında, belirttiğiniz sınıfları bulmayı dener. Bu, Diagnostics.EventLog System.Diagnostics.EventLog yerine belirtebileceğiniz anlamına gelir.

#### <a name="storing-objects-in-variables"></a>Değişkenleri nesneler depolanıyor

Geçerli shell'de kullanabilmesi için bir nesneye bir başvuru depolamak isteyebilirsiniz. Windows PowerShell birçok iş işlem hatları ile yapmanıza gerek değişkenleri lessening sağlar. ancak, bazen nesnelere başvuru değişkenleri depolamak bu nesneleri işlemek daha kullanışlı kolaylaştırır.

Windows PowerShell, aslında nesneler adlandırılmış değişkenler oluşturmanızı sağlar. Herhangi bir geçerli Windows PowerShell komutu çıkışı bir değişkene depolanabilir. Değişken adları, her zaman $ ile başlar. Uygulama günlük başvurusu $AppLog adlı bir değişkende depolamak istiyorsanız adını yazın değişkeni bir eşittir işareti tarafından izlenen ve uygulama günlüğü nesnesi oluşturmak için kullanılan komutu yazın:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Ardından $AppLog yazarsanız, uygulama günlüğüne içerdiğini görebilirsiniz:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Yeni nesne ile bir uzak olay günlüğü erişme

Önceki bölümde kullanılan komutlar yerel bilgisayarı hedef; **Get-EventLog** cmdlet'i, yapabilir. Uzak bir bilgisayarda uygulama günlüğüne erişmek için hem günlük adını ve bir bilgisayar adı (veya IP adresi) bağımsız sağlamanız gerekir.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Biz $RemoteAppLog değişkeninde depolanan bir olay günlüğüne bir başvurusu sahip olduğunuza göre hangi görevleri üzerinde gerçekleştirebiliriz?

#### <a name="clearing-an-event-log-with-object-methods"></a>Nesnesi yöntemleri ile bir olay günlüğü temizleme

Nesneler genellikle görevleri gerçekleştirmek için çağrılan yöntemler vardır. Kullanabileceğiniz **Get-Member** bir nesneyle ilişkili yöntemler görüntülenecek. Aşağıdaki komut ve seçili çıkış bazı EventLog sınıfının yöntemlerini göster:

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

**Clear()** yöntemi, olay günlüğünü temizlemek için kullanılabilir. Yöntem bağımsız değişkenleri gerektirmiyor olsa bile bir yöntemi çağırırken, her zaman yöntem adı parantez ile izlemelisiniz. Bu Windows PowerShell yöntemi ve olası bir özelliği aynı ada sahip arasında ayrım sağlar. Çağırmak için aşağıdaki komutu yazın **Temizle** yöntemi:

```
PS> $RemoteAppLog.Clear()
```

Günlüğü görüntülemek için aşağıdakini yazın. Olay günlüğü temizlendi ve artık 262 yerine 0 girdi olduğunu görürsünüz:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Nesnesi yeni ile COM nesneleri oluşturma
Kullanabileceğiniz **New-Object** Bileşen Nesne Modeli (COM) bileşenleri ile çalışmak için. Çoğu sistemde yüklü ActiveX uygulamalar Internet Explorer gibi Windows betik sistemi (WSH) dahil çeşitli kitaplıklara bileşenleri çeşitler barındırır.

**Yeni nesne** COM nesneleri çağırırken .NET Framework yapan onunla aynı sınırlamalara sahiptir, COM nesneleri oluşturmak için .NET Framework çalışma zamanı aranabilir sarmalayıcıları kullanır. Bir COM nesnesi oluşturmak için belirtmeniz gerekir **ComObject** programlı tanımlayıcı parametresi veya *ProgID* kullanmak istediğiniz COM sınıfı. COM kullanımı ve ProgIDs bir sistemde kullanılabilir nelerdir belirleyen sınırlamaları hakkında kapsamlı bir açıklama, bu kullanıcının kılavuzun kapsamı dışındadır olmakla birlikte en iyi bilinen nesneleri ortamlarından WSH gibi Windows PowerShell içinde kullanılabilir.

Bu progid'ler belirterek WSH nesneleri oluşturabilirsiniz: **WScript.Shell nesnesinin**, **WScript.Network**, **Scripting.Dictionary**, ve **Scripting.FileSystemObject**. Aşağıdaki komutlar bu nesneleri oluşturur:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Bu sınıfların işlevselliğinin büyük kısmını yapılan olsa da başka şekillerde kullanılabilir Windows PowerShell'de, kısayol oluşturma gibi birkaç görev WSH sınıflarını kullanarak yapmak yine de kolaydır.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Bir masaüstü kısayolu wscript.Shell nesnesinin ile oluşturma

Bir COM nesnesi ile kolayca gerçekleştirilebilir bir görev bir kısayol oluşturur. Bir kısayol masaüstünüzde giriş klasörü için bağlantılar için Windows PowerShell oluşturmak istediğinizi varsayalım. Önce bir başvuru oluşturmak gereken **wscript.Shell nesnesinin**, hangi adlı bir değişkende depolarız **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member COM nesneleriyle birlikte çalışarak yazarak bir nesnenin üyelerine keşfedebilirsiniz:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** isteğe sahip **Inputobject** yöneltme yerine Giriş sağlamak için kullanabileceğiniz bir parametre **Get-Member**. Aynı komutu yerine kullanılan, yukarıda gösterildiği gibi çıkış elde edebileceğiniz **Get-Member - Inputobject $WshShell**. Kullanırsanız **Inputobject**, tek bir öğe kendi bağımsız değişkeni değerlendirir. Çeşitli nesneleri değişkene varsa buna **Get-Member** bunları bir dizi nesne olarak değerlendirir. Örneğin:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

**Wscript.Shell nesnesinin CreateShortcut** yöntemi tek bir değişken oluşturmak için kısayol dosyasının yolu kabul eder. Masaüstünde tam yolunu yazabilirsiniz, ancak daha kolay bir yolu yoktur. Masaüstü genellikle geçerli kullanıcının giriş klasörü içinde Masaüstü adlı bir klasör temsil edilir. Windows PowerShell bir değişkene sahip **$Home** , bu klasörün yolunu içerir. Biz bu değişkeni kullanarak giriş klasörünün yolunu belirtin ve Masaüstü klasörün adını ve kısayol tuşlarına basarak oluşturmak adını ekleyin:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Çift tırnak içinde bir değişken adı şuna benzer bir şey kullandığınızda, Windows PowerShell, eşleşen bir değer yerine dener. Tek tırnak işareti kullanırsanız, değişken değeri yerine Windows PowerShell denemez. Örneğin, aşağıdaki komutları yazarak deneyin:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Adlı bir değişken artık sahibiz **$lnk** , yeni bir kısayol başvuru içeriyor. Üyelerini görmek istiyorsanız, kendisine iletebildiğiniz **Get-Member**. Çıktıyı aşağıya bizim kısayol oluşturma işlemini kullanmak ihtiyacımız olan üyeleri gösterir:

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

Belirtmek ihtiyacımız **TargetPath**, Windows PowerShell ve ardından kısayol kaydetme uygulama klasörü **$lnk** çağırarak **Kaydet** yöntemi. Windows PowerShell uygulama klasörü yolu değişkeninde depolanan **$PSHome**, yazarak bunu yapabilirsiniz:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Windows powershell'den Internet Explorer'ı kullanma

Birçok uygulama (Microsoft Office uygulamaları ve Internet Explorer ailesinin dahil) COM kullanılarak otomatikleştirilebilir. Internet Explorer, bazı tipik teknikleri ve içinde COM tabanlı uygulamalar ile çalışma konuları gösterilmiştir.

Internet Explorer ProgID, belirterek bir Internet Explorer örneği oluşturma **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Bu komut, Internet Explorer'ı başlatır, ancak görünür yapmaz. Get-Process yazarsanız Iexplore adlı bir işlemin çalıştığını görebilirsiniz. Windows PowerShell betiğinden çıkın, aslında, işlem çalışmaya devam eder. Bilgisayarı yeniden başlatmanız gerekir ya da Iexplore işlemi sonlandırmak için bir aracı gibi Görev Yöneticisi'ni kullanın.

> [!NOTE]
> Ayrı işlem başlatmak COM nesneleri yaygın olarak adlandırılan *ActiveX yürütülebilir dosyaları*, olabilir veya başlatma sırasında bir kullanıcı arabirimi pencere görüntülenmeyebilir. Bir pencere oluşturma ancak Internet Explorer gibi görünür yapmayın odağı genellikle Windows masaüstüne taşınır ve pencerenin etkileşim görünür yapmanız gerekir.

Yazarak **$IE | Get-Member**, Internet Explorer için özellikleri ve yöntemleri görüntüleyebilirsiniz. Internet Explorer penceresi görmek için yazarak Visible özelliğini $true olarak ayarlayın:

```powershell
$ie.Visible = $true
```

Ardından, Navigate yöntemi kullanarak belirli bir Web adresi gidebilirsiniz:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Diğer üyeleri Internet Explorer nesne modeli kullanarak Web sayfasında metin içeriğini almak mümkündür. Aşağıdaki komut, geçerli Web sayfasının gövdesinde HTML metni görüntülenir:

```powershell
$ie.Document.Body.InnerText
```

PowerShell içinden Internet Explorer'ı kapatmak için kendi Quit() yöntemi çağırın:

```powershell
$ie.Quit()
```

Bu, kapatmak için zorlar. Olsa da hala bir COM nesnesi gibi görünüyor $IE değişken artık geçerli bir başvuru içerir. Bunu kullanmayı denerseniz, bir Otomasyon hata alırsınız:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Kalan başvuru $ gibi bir komutla IE kaldırabilir ya da $null = ya da tamamen değişken yazarak kaldırın:

```powershell
Remove-Variable ie
```

> [!NOTE]
> ActiveX yürütülebilir dosyaları çıkmayın veya bir başvuru kaldırdığınızda çalışmaya devam hiçbir ortak standart yoktur. Uygulamanın görünür olup düzenlenmiş bir belge içinde kullanılıp kullanılmadığını ve hatta olup Windows PowerShell hala çalışıyor gibi durumlarda, bağlı olarak uygulama olabilir veya olmayan sonlandırılabilir. Bu nedenle, her ActiveX Windows PowerShell'de kullanmak istediğiniz yürütülebilir için sonlandırma davranışı test etmeniz gerekir.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>.NET Framework sarılı bir COM nesneleri hakkında uyarılar alma

Bazı durumlarda, bir COM nesnesi ilişkili bir .NET Framework olabilir *çalışma zamanı çağrılabilir sarmalayıcı* veya RCW ve bu işlem tarafından kullanılan **New-Object**. RCW davranışı, davranış normal COM nesnesinin farklı olabileceğinden **New-Object** sahip bir **katı** parametresi RCW erişimi hakkında sizi uyarır. Belirtirseniz **katı** parametresi ve ardından bir RCW kullanan bir COM nesnesi oluşturur, bir uyarı iletisi alın:

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