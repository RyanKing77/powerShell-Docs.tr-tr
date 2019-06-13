---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ağ Görevleri Gerçekleştirme
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030866"
---
# <a name="performing-networking-tasks"></a>Ağ Görevleri Gerçekleştirme

TCP/IP'yi en sık kullanılan ağ protokolü olduğundan, en alt düzey ağ protokolü yönetim görevlerini TCP/IP'yi içerir. Bu bölümde, Windows PowerShell ve WMI bu görevleri gerçekleştirmek için kullanıyoruz.

## <a name="listing-ip-addresses-for-a-computer"></a>Bir bilgisayar için IP adresleri listesi

Yerel bilgisayarda tüm IP adreslerini almak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

Bu komutun çıktısı değerlerini küme ayraçları içine alınmış çoğu özelliği listelerinden farklıdır:

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Küme ayraçları neden görünüyor anlamak için incelemek için Get-Member cmdlet'ini kullanın **IPADDRESS** özelliği:

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

Her ağ bağdaştırıcısı için IP adresi gerçekte bir dizi özelliğidir. Küme ayraçları tanımındaki belirtmek **IPADDRESS** değil bir **System.String** değeri, ancak bir dizi **System.String** değerleri.

## <a name="listing-ip-configuration-data"></a>IP yapılandırma verilerini listeleme

Her ağ bağdaştırıcısı için ayrıntılı IP yapılandırma verilerini görüntülemek için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

Ağ bağdaştırıcısı yapılandırma nesnesi için varsayılan görünen bilgiler çok sınırlı bir kümesidir. Ayrıntılı bir inceleme ve sorun giderme için Select-Object ya da Format-List gibi biçimlendirme bir cmdlet görüntülenecek özelliklerini belirtmek için kullanın.

IPX veya WINS özelliklerinde ilgilenmiyorsanız — büyük olasılıkla modern bir TCP/IP ağı durumda — Select-Object ExcludeProperty parametresi, "WINS" ile başlayan adları özelliklerle gizlemek için kullanabilirsiniz veya "IPX:"

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Bu komut, DHCP, DNS, yönlendirme hakkında ayrıntılı bilgi ve diğer ikincil IP yapılandırma özellikleri döndürür.

## <a name="pinging-computers"></a>Ping bilgisayarlar

Bir bilgisayar kullanarak karşı basit bir ping gerçekleştirebileceğiniz **Win32_PingStatus**. Aşağıdaki komutu ping işlemi yapar, ancak uzun bir çıktı döndürür:

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Aşağıdaki komutu tarafından oluşturulan daha kullanışlı form için Özet bilgiler görüntüleme adresi, yanıt süresi ve StatusCode özellikleri. Böylece bunlar Windows PowerShell'de düzgün görüntülenmesi Format-Table Autosize parametresi tablo sütunları yeniden boyutlandırır.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Bir durum kodu 0 Başarılı ping gösterir.

Tek bir komutla birden çok bilgisayara ping işlemi yapmak için bir dizi kullanabilirsiniz. Birden fazla adres olduğundan **ForEach-Object** her adresi ayrı ayrı ping göndermek için:

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Ağ sayısı 192.168.1.0 ve standart bir sınıf C alt ağ maskesi (255.255.255.0) kullanan bir özel ağ gibi bir alt ağda bulunan tüm bilgisayarların ping işlemi yapmak için aynı komutu biçimini kullanın., yalnızca 192.168.1.1 aracılığıyla 192.168.1.254 aralığındaki adresleri Yerel adresler (0, her zaman bir alt yayın adresi ağ sayısı ve 255 için ayrılmıştır) yasal.

1 ila 254 Windows PowerShell'de sayıdan oluşan bir diziyi temsil etmek için deyimini **1..254.** Dizi oluşturma ve sonra değerleri kısmi bir adresi üzerine ping deyiminde ekleyerek eksiksiz bir alt ağ ping gerçekleştirilebilir:

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Adres aralığı oluşturmak için bu tekniği de başka bir yerde kullanılabileceğini unutmayın. Bu şekilde adresleri eksiksiz bir kümesini oluşturabilirsiniz:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Ağ bağdaştırıcısı özellikleri alınıyor

Daha önce bu Kullanım Kılavuzu'nda genel yapılandırma özellikleri kullanarak alabilir olan belirttiğimiz **Win32_NetworkAdapterConfiguration**. TCP/IP'yi bilgi gerektirmesidir rağmen ağ bağdaştırıcısı bilgileri gibi MAC adresleri ve bağdaştırıcısı türlerini içeren bir bilgisayar neler olduğunu anlamak için yararlı olabilir. Bu bilgilerin özetini almak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Bir ağ bağdaştırıcısı için DNS etki alanı atama

Otomatik ad çözümlemesi için DNS etki alanı atama **Win32_NetworkAdapterConfiguration SetDNSDomain** yöntemi. Her ağ bağdaştırıcısı yapılandırması için DNS etki alanı bağımsız olarak atamak için kullanmanız gereken bir **ForEach-Object** her bağdaştırıcı için etki alanı atama bildirimi:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

Filtre ifadesi "IPEnabled $true =" yalnızca TCP/IP'yi kullanan bile bir ağ üzerinde bir bilgisayardaki ağ bağdaştırıcısı yapılandırmalarından bazılarını true TCP/IP'yi bağdaştırıcıları; olmadığı için gereklidir Bunlar genel yazılım öğeleri RAS, PPTP, QoS ve diğer hizmetleri tüm bağdaştırıcıları için destek ve bu nedenle, kendi bir adresi yok.

Komutunu kullanarak filtreleyebilirsiniz **Where-Object** cmdlet'ini kullanmak yerine **Get-WmiObject** filtre.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>DHCP yapılandırma görevlerini gerçekleştirme

DNS yapılandırması gibi DHCP ayrıntıları değiştirme ağ bağdaştırıcıları, bir dizi çalışma içerir. WMI kullanarak gerçekleştirebileceğiniz çeşitli farklı eylemler vardır ve biz sık kullanılanlardan birkaç adım adım anlatır.

### <a name="determining-dhcp-enabled-adapters"></a>DHCP'nin etkin bağdaştırıcıları belirleme

Bir bilgisayarda DHCP özellikli bağdaştırıcıları bulmak için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

IP yapılandırma sorunlarını Adaptörünün tutmak için yalnızca IP özellikli bağdaştırıcıları alabilirsiniz:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a>DHCP özellikleri alınıyor

DHCP ile ilgili özellikler için bir bağdaştırıcı "DHCP ile" genellikle başladığı için yalnızca bu özellikleri görüntülemek için Format-Table özellik parametresinin kullanabilirsiniz:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Her bağdaştırıcı DHCP etkinleştirme

Tüm bağdaştırıcılarında DHCP'yi etkinleştirmek için aşağıdaki komutu kullanın:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Kullanabileceğiniz **filtre** deyimi "IPEnabled $true ve DHCPEnabled = $false =" nerede zaten etkinleştirilmiş, ancak bu adımı atlayarak değil neden hataları DHCP etkinleştirme önlemek için.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Serbest bırakarak ve belirli bağdaştırıcılarında DHCP kiralarını yenileme

**Win32_NetworkAdapterConfiguration** sınıfında **ReleaseDHCPLease()** ve **RenewDHCPLease** yöntemleri. Her ikisi de aynı şekilde kullanılır. Genel olarak, bırakmak veya belirli bir alt ağdaki bir bağdaştırıcı için adresleri yenilemek yalnızca ihtiyacınız varsa bu yöntemleri kullanın. Bir alt ağ bağdaştırıcılarında filtre için en kolay yolu, ağ geçidini kullanmak için bu alt ağ bağdaştırıcısı yapılandırmalarının seçmektir. Örneğin, aşağıdaki komutu 192.168.1.254 DHCP kiraları elde etme bağdaştırıcılarında yerel bilgisayardaki tüm DHCP kirası serbest bırakır:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

DHCP kirasını yenilemek için tek değişiklik kullanmaktır **RenewDHCPLease** yöntemi yerine **ReleaseDHCPLease()** yöntemi:

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Uzak bir bilgisayarda bu yöntemleri kullanırken, kendisine yayımlanmış veya yenilenen kira bağdaştırıcıyla aracılığıyla birbirine bağlandıysa uzak sisteme erişimi kaybedebilir miyim dikkat edin.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Serbest bırakarak ve tüm bağdaştırıcılarında DHCP kiralarını yenileme

Kullanarak tüm bağdaştırıcılarında genel DHCP adresi sürümleri veya yenileme gerçekleştirebilirsiniz **Win32_NetworkAdapterConfiguration** yöntemleri **ReleaseDHCPLeaseAll** ve **RenewDHCPLeaseAll** . Bununla birlikte, komut belirli bir bağdaştırıcı yerine WMI sınıfını serbest olduğundan uygulamanız gerekir ve genel olarak kira yenileme değil, belirli bir bağdaştırıcı sınıfı gerçekleştirilir.

Tüm WMI sınıflarını listeleme ve ardından yalnızca istenen sınıf adına göre seçerek, sınıf örneklerinin yerine, WMI sınıfına bir başvuru alabilirsiniz. Örneğin, aşağıdaki komutu Win32_NetworkAdapterConfiguration sınıfını döndürür:

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Tüm komut sınıf olarak kabul et ve ardından çağırmak **ReleaseDHCPAdapterLease** yöntemini. Aşağıdaki komutta, çevreleyen parantezler **Get-WmiObject** ve **Where-Object** ardışık öğeleri doğrudan Windows PowerShell'i ilk değerlendirin:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Aynı komut biçimi çağırmak için kullanabileceğiniz **RenewDHCPLeaseAll** yöntemi:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Bir ağ paylaşımı oluşturma

Bir ağ paylaşımı oluşturmak için kullanın **Win32_Share oluşturma** yöntemi:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Kullanarak bir paylaşım oluşturabilirsiniz **ağ paylaşımı** Windows PowerShell'de:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Bir ağ paylaşımı kaldırma

Bir ağ paylaşımı ile kaldırabilirsiniz **Win32_Share**, ancak belirli bir paylaşım kaldırılacak, alınacak gerektiğinden bir paylaşımı oluşturmaktan biraz farklı işlemidir yerine **Win32_Share** sınıf. Aşağıdaki deyim, paylaşım "TempShare" siler:

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

**Ağ Paylaşımı** de çalışır:

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Bir Windows erişilebilir bir ağ sürücüsü bağlanma

**Yeni PSDrive** cmdlet'lerini Windows PowerShell sürücüsünü oluşturur, ancak bu şekilde oluşturulan sürücüleri yalnızca Windows PowerShell için kullanılabilir. Yeni bir ağ sürücüsü oluşturmak için kullanabileceğiniz **WScript.Network** COM nesnesi. Aşağıdaki komutu paylaşım eşler \\ \\FPS01\\kullanıcılar yerel sürücüye B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

**Net kullanım** komutu de çalışır:

```powershell
net use B: \\FPS01\users
```

İle eşleşen sürücüler **WScript.Network** veya Windows PowerShell için hemen kullanılabilir ağ kullanın.
