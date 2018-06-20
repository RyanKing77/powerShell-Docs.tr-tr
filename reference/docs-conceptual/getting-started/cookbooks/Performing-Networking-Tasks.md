---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ağ Görevleri Gerçekleştirme
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954135"
---
# <a name="performing-networking-tasks"></a>Ağ Görevleri Gerçekleştirme

TCP/IP'yi en yaygın kullanılan ağ protokolü olduğundan, en alt düzey ağ protokolü yönetim görevlerini TCP/IP'yi içerir. Bu bölümde, Windows PowerShell ve WMI bu görevleri gerçekleştirmek için kullanırız.

### <a name="listing-ip-addresses-for-a-computer"></a>Bir bilgisayar için IP adreslerini listeleme

Yerel bilgisayarda tüm IP adreslerini almak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

Bu komutun çıktısı, çoğu özellik listelerinden farklıdır, bu değerleri ayraç içine çünkü:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Küme ayraçları neden görünüyor anlamak için incelemek için Get-üye cmdlet'ini kullanın **IPADDRESS** özelliği:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

Her ağ bağdaştırıcısı için IPADDRESS aslında bir dizi özelliğidir. Küme ayraçları tanımında belirtmek **IPADDRESS** değil bir **System.String** değeri, ancak bir dizi **System.String** değerleri.

### <a name="listing-ip-configuration-data"></a>IP yapılandırma verilerini listeleme

Her ağ bağdaştırıcısı için ayrıntılı IP yapılandırma verilerini görüntülemek için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

Ağ bağdaştırıcısı yapılandırma nesnesi için varsayılan görüntü kullanılabilir bilgi çok sınırlı bir kümesidir. Ayrıntılı inceleme ve sorun giderme için görüntülenecek özelliklerini belirtmek için Select-Object veya Format-List gibi bir biçimlendirme cmdlet'ini kullanın.

IPX veya WINS özelliklerinde değil ilgileniyorsanız — büyük olasılıkla modern bir TCP/IP ağı durumda — "WINS" ile başlayan adları özelliklerle gizlemek için Select-Object ExcludeProperty parametresinin kullanabilirsiniz veya "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Bu komut, DHCP, DNS, yönlendirme hakkında ayrıntılı bilgi ve diğer ikincil IP yapılandırma özellikleri döndürür.

### <a name="pinging-computers"></a>Ping bilgisayarlar

Bir bilgisayar kullanarak karşı basit bir ping gerçekleştirebilirsiniz **Win32_PingStatus**. Aşağıdaki komutu ping işlemi gerçekleştirir, ancak uzun çıktıyı döndürür:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Aşağıdaki komutu tarafından oluşturulan bir daha kullanışlı form için Özet bilgiler bir görüntü adresi, yanıt süresi ve StatusCode özellikleri. Windows PowerShell'de düzgün görüntüledikleri böylece Format-Table Autosize parametresinin tablo sütunları yeniden boyutlandırır.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Durum kodu 0 PING başarılı gösterir.

Tek bir komutla birden çok bilgisayara ping işlemi yapmak için bir dizi kullanabilirsiniz. Birden fazla adres olduğundan kullanın **ForEach-Object** her adresi ayrı ayrı ping işlemi yapmak için:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Ağ sayısı 192.168.1.0 ve standart bir C sınıfı alt ağ maskesi (255.255.255.0) kullanan bir özel ağ gibi bir alt ağdaki tüm bilgisayarların ping işlemi yapmak için aynı komut biçimini kullanabilirsiniz., yalnızca 192.168.1.254 aracılığıyla 192.168.1.1 aralıktaki adresler Yerel adresler (0, her zaman bir alt ağ yayın adresi ağ sayısı ve 255 için ayrılmıştır) yasal.

Bir dizi sayının 1'den Windows PowerShell'de 254 temsil etmek için Ek Yardım deyimini **1..254.** Bir tam alt ping dizi oluşturmak ve ardından ping deyiminde kısmi bir adresi üzerine değerleri ekleyerek gerçekleştirilebilir:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Bir adres aralığı oluşturmak için bu tekniği de başka bir yerde kullanılabileceğini unutmayın. Bu şekilde adresleri eksiksiz bir kümesini oluşturabilirsiniz:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a>Ağ bağdaştırıcısı özelliklerini alma

Kılavuzda daha önce bu kullanıcının, biz genel yapılandırma özelliklerini kullanarak alınamadı bahsedilen **Win32_NetworkAdapterConfiguration**. Kesinlikle olmadığında TCP/IP'yi bilgi rağmen ağ bağdaştırıcı bilgileri gibi MAC adresleri ve bağdaştırıcısı türlerini bir bilgisayarla neler olduğunu anlamak için yararlı olabilir. Bu bilgilerin özetini almak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Bir ağ bağdaştırıcısı için DNS etki alanının atama

Otomatik ad çözümlemesi için DNS etki alanı atamak için kullandığınız **Win32_NetworkAdapterConfiguration SetDNSDomain** yöntemi. DNS etki alanı her ağ bağdaştırıcısı yapılandırması için bağımsız olarak atamak için kullanmak gereken bir **ForEach-Object** deyimi her bağdaştırıcı için etki alanı atamak için:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

Filtre ifadesi "IPEnabled $true =" yalnızca TCP/IP'yi kullanır bile bir ağ üzerinde birçok ağ bağdaştırıcısı yapılandırmalarından bir bilgisayarda doğru TCP/IP'yi bağdaştırıcıları; olmadığından gereklidir Bunlar RAS, PPTP, QoS ve diğer hizmetleri tüm bağdaştırıcıların destekleme Genel yazılım öğeleridir ve dolayısıyla kendi bir adresi yok.

Komutunu kullanarak filtreleyebilirsiniz **Where-Object** kullanmak yerine cmdlet **Get-WmiObject** Filtresi.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a>DHCP yapılandırma görevlerini gerçekleştirme

DNS yapılandırması gibi DHCP ayrıntıları değiştirme ağ bağdaştırıcıları, bir dizi çalışma içerir. WMI kullanarak gerçekleştirebileceğiniz çeşitli farklı eylemler vardır ve ortak olanlara birkaç adım.

#### <a name="determining-dhcp-enabled-adapters"></a>DHCP etkin bağdaştırıcıları belirleme

Bir bilgisayarda DHCP etkin bağdaştırıcıları bulmak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

IP yapılandırma sorunlarını bağdaştırıcılarla dışlamak için yalnızca IP etkin bağdaştırıcıları alabilirsiniz:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>DHCP özelliklerini alma

DHCP ile ilgili özellikler için bir bağdaştırıcı genellikle "DHCP" ile başladığı için yalnızca bu özellikleri görüntülemek için Tablo Biçimlendir özellik parametresinin kullanabilirsiniz:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>Her bağdaştırıcı üzerindeki DHCP etkinleştirme

Tüm bağdaştırıcıları DHCP etkinleştirmek için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Kullanabileceğiniz **filtre** deyimi "IPEnabled $true ve DHCPEnabled = $false =", zaten etkin, ancak bu adımı atlayarak değil neden olacak hataları DHCP etkinleştirme önlemek için.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Serbest bırakma ve DHCP kiralarını belirli bağdaştırıcılarında yenileniyor

**Win32_NetworkAdapterConfiguration** sınıfına sahip **ReleaseDHCPLease()** ve **RenewDHCPLease** yöntemleri. Her ikisi de aynı şekilde kullanılır. Genel olarak, yalnızca bırakmak veya belirli bir alt ağdaki bir bağdaştırıcı için adresleri yenilemek gerekiyorsa bu yöntemleri kullanın. Filtre bağdaştırıcılarına bir alt ağda en kolay yolu, ağ geçidini kullanmak için bu alt ağ bağdaştırıcısı yapılandırmalarından seçmektir. Örneğin, aşağıdaki komut, DHCP kiralarını 192.168.1.254 alma bağdaştırıcılarda yerel bilgisayardaki tüm DHCP kiralarını serbest bırakır:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Bir DHCP kiralama yenileme için tek değişiklik kullanmaktır **RenewDHCPLease** yöntemi yerine **ReleaseDHCPLease()** yöntemi:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Uzak bir bilgisayarda bu yöntemleri kullanarak, yayımlanan veya yenilenen kira ile bağdaştırıcısından kendisine bağlıysanız, uzak sisteme erişimi kaybedebilir miyim unutmayın.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Serbest bırakma ve DHCP kiralarını tüm bağdaştırıcılarda yenileniyor

Kullanarak tüm bağdaştırıcılarında genel DHCP adresi sürümleri veya yenilemeleri gerçekleştirebileceğiniz **Win32_NetworkAdapterConfiguration** yöntemleri **ReleaseDHCPLeaseAll** ve **RenewDHCPLeaseAll** . Ancak, komut belirli bir bağdaştırıcı yerine WMI sınıfı bırakılıyor çünkü uygulamanız gerekir ve genel kira yenileme değil, belirli bir bağdaştırıcı sınıfı gerçekleştirilir.

Tüm WMI sınıflarını listeleme ve ardından istediğiniz sınıfı adıyla seçerek sınıf örneklerinin yerine bir WMI sınıfı başvurusu elde edebilirsiniz. Örneğin, aşağıdaki komut, Win32_NetworkAdapterConfiguration sınıfını döndürür:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Tüm komut sınıfı olarak davranmak ve ardından çağırma **ReleaseDHCPAdapterLease** yöntemini. Aşağıdaki komutta, çevreleyen parantez **Get-WmiObject** ve **Where-Object** ardışık düzen öğeleri doğrudan Windows PowerShell'i ilk değerlendirin:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Çağrılacak aynı komut biçimini kullanabilirsiniz **RenewDHCPLeaseAll** yöntemi:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Bir ağ paylaşımı oluşturma

Bir ağ paylaşımı oluşturmak için kullanmak **Win32_Share oluşturmak** yöntemi:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Kullanarak paylaşım oluşturabilirsiniz **ağ paylaşımı** Windows PowerShell'de:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Bir ağ paylaşımı kaldırma

Bir ağ paylaşımı ile kaldırabilirsiniz **Win32_Share**, ancak kaldırılması için özel paylaşım almak gerektiğinden biraz farklı bir paylaşım oluşturma işlemidir yerine **Win32_Share** sınıf. Aşağıdaki deyim "TempShare" Paylaşımı siler:

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Ağ Paylaşımı** de çalışır:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Windows erişilebilir bir ağ sürücüsü bağlanma

**Yeni PSDrive** cmdlet'leri bir Windows PowerShell sürücüsü oluşturur, ancak bu yolla oluşturulan sürücüleri yalnızca Windows PowerShell için kullanılabilir. Yeni bir ağ sürücüsü oluşturmak için kullanabileceğiniz **WScript.Network** COM nesnesi. Aşağıdaki komutu paylaşım eşlemeleri \\ \\FPS01\\kullanıcılar yerel sürücüye B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

**Net kullanım** komutu çalışır de:

```powershell
net use B: \\FPS01\users
```

Biriyle eşlenen sürücüler **WScript.Network** veya net kullanmak için Windows PowerShell hemen kullanılabilir.