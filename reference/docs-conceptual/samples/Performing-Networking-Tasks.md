---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ağ Görevleri Gerçekleştirme
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 250ae6e5f6431ce659b3600188d7e30e501c3247
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058293"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="db312-103">Ağ Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="db312-103">Performing Networking Tasks</span></span>

<span data-ttu-id="db312-104">TCP/IP'yi en sık kullanılan ağ protokolü olduğundan, en alt düzey ağ protokolü yönetim görevlerini TCP/IP'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="db312-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="db312-105">Bu bölümde, Windows PowerShell ve WMI bu görevleri gerçekleştirmek için kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="db312-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="db312-106">Bir bilgisayar için IP adresleri listesi</span><span class="sxs-lookup"><span data-stu-id="db312-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="db312-107">Yerel bilgisayarda tüm IP adreslerini almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db312-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="db312-108">Bu komutun çıktısı değerlerini küme ayraçları içine alınmış çoğu özelliği listelerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="db312-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="db312-109">Küme ayraçları neden görünüyor anlamak için incelemek için Get-Member cmdlet'ini kullanın **IPADDRESS** özelliği:</span><span class="sxs-lookup"><span data-stu-id="db312-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="db312-110">Her ağ bağdaştırıcısı için IP adresi gerçekte bir dizi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="db312-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="db312-111">Küme ayraçları tanımındaki belirtmek **IPADDRESS** değil bir **System.String** değeri, ancak bir dizi **System.String** değerleri.</span><span class="sxs-lookup"><span data-stu-id="db312-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="db312-112">IP yapılandırma verilerini listeleme</span><span class="sxs-lookup"><span data-stu-id="db312-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="db312-113">Her ağ bağdaştırıcısı için ayrıntılı IP yapılandırma verilerini görüntülemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db312-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="db312-114">Ağ bağdaştırıcısı yapılandırma nesnesi için varsayılan görünen bilgiler çok sınırlı bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="db312-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="db312-115">Ayrıntılı bir inceleme ve sorun giderme için Select-Object ya da Format-List gibi biçimlendirme bir cmdlet görüntülenecek özelliklerini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="db312-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="db312-116">IPX veya WINS özelliklerinde ilgilenmiyorsanız — büyük olasılıkla modern bir TCP/IP ağı durumda — Select-Object ExcludeProperty parametresi, "WINS" ile başlayan adları özelliklerle gizlemek için kullanabilirsiniz veya "IPX:"</span><span class="sxs-lookup"><span data-stu-id="db312-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="db312-117">Bu komut, DHCP, DNS, yönlendirme hakkında ayrıntılı bilgi ve diğer ikincil IP yapılandırma özellikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="db312-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="db312-118">Ping bilgisayarlar</span><span class="sxs-lookup"><span data-stu-id="db312-118">Pinging Computers</span></span>

<span data-ttu-id="db312-119">Bir bilgisayar kullanarak karşı basit bir ping gerçekleştirebileceğiniz **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="db312-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="db312-120">Aşağıdaki komutu ping işlemi yapar, ancak uzun bir çıktı döndürür:</span><span class="sxs-lookup"><span data-stu-id="db312-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="db312-121">Aşağıdaki komutu tarafından oluşturulan daha kullanışlı form için Özet bilgiler görüntüleme adresi, yanıt süresi ve StatusCode özellikleri.</span><span class="sxs-lookup"><span data-stu-id="db312-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="db312-122">Böylece bunlar Windows PowerShell'de düzgün görüntülenmesi Format-Table Autosize parametresi tablo sütunları yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="db312-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="db312-123">Bir durum kodu 0 Başarılı ping gösterir.</span><span class="sxs-lookup"><span data-stu-id="db312-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="db312-124">Tek bir komutla birden çok bilgisayara ping işlemi yapmak için bir dizi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db312-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="db312-125">Birden fazla adres olduğundan **ForEach-Object** her adresi ayrı ayrı ping göndermek için:</span><span class="sxs-lookup"><span data-stu-id="db312-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="db312-126">Ağ sayısı 192.168.1.0 ve standart bir sınıf C alt ağ maskesi (255.255.255.0) kullanan bir özel ağ gibi bir alt ağda bulunan tüm bilgisayarların ping işlemi yapmak için aynı komutu biçimini kullanın., yalnızca 192.168.1.1 aracılığıyla 192.168.1.254 aralığındaki adresleri Yerel adresler (0, her zaman bir alt yayın adresi ağ sayısı ve 255 için ayrılmıştır) yasal.</span><span class="sxs-lookup"><span data-stu-id="db312-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="db312-127">1 ila 254 Windows PowerShell'de sayıdan oluşan bir diziyi temsil etmek için deyimini **1..254.**</span><span class="sxs-lookup"><span data-stu-id="db312-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="db312-128">Dizi oluşturma ve sonra değerleri kısmi bir adresi üzerine ping deyiminde ekleyerek eksiksiz bir alt ağ ping gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="db312-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="db312-129">Adres aralığı oluşturmak için bu tekniği de başka bir yerde kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db312-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="db312-130">Bu şekilde adresleri eksiksiz bir kümesini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db312-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="db312-131">Ağ bağdaştırıcısı özellikleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="db312-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="db312-132">Daha önce bu Kullanım Kılavuzu'nda genel yapılandırma özellikleri kullanarak alabilir olan belirttiğimiz **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="db312-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="db312-133">TCP/IP'yi bilgi gerektirmesidir rağmen ağ bağdaştırıcısı bilgileri gibi MAC adresleri ve bağdaştırıcısı türlerini içeren bir bilgisayar neler olduğunu anlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db312-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="db312-134">Bu bilgilerin özetini almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db312-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="db312-135">Bir ağ bağdaştırıcısı için DNS etki alanı atama</span><span class="sxs-lookup"><span data-stu-id="db312-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="db312-136">Otomatik ad çözümlemesi için DNS etki alanı atama **Win32_NetworkAdapterConfiguration SetDNSDomain** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="db312-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="db312-137">Her ağ bağdaştırıcısı yapılandırması için DNS etki alanı bağımsız olarak atamak için kullanmanız gereken bir **ForEach-Object** her bağdaştırıcı için etki alanı atama bildirimi:</span><span class="sxs-lookup"><span data-stu-id="db312-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="db312-138">Filtre ifadesi "IPEnabled $true =" yalnızca TCP/IP'yi kullanan bile bir ağ üzerinde bir bilgisayardaki ağ bağdaştırıcısı yapılandırmalarından bazılarını true TCP/IP'yi bağdaştırıcıları; olmadığı için gereklidir Bunlar genel yazılım öğeleri RAS, PPTP, QoS ve diğer hizmetleri tüm bağdaştırıcıları için destek ve bu nedenle, kendi bir adresi yok.</span><span class="sxs-lookup"><span data-stu-id="db312-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="db312-139">Komutunu kullanarak filtreleyebilirsiniz **Where-Object** cmdlet'ini kullanmak yerine **Get-WmiObject** filtre.</span><span class="sxs-lookup"><span data-stu-id="db312-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="db312-140">DHCP yapılandırma görevlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="db312-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="db312-141">DNS yapılandırması gibi DHCP ayrıntıları değiştirme ağ bağdaştırıcıları, bir dizi çalışma içerir.</span><span class="sxs-lookup"><span data-stu-id="db312-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="db312-142">WMI kullanarak gerçekleştirebileceğiniz çeşitli farklı eylemler vardır ve biz sık kullanılanlardan birkaç adım adım anlatır.</span><span class="sxs-lookup"><span data-stu-id="db312-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="db312-143">DHCP'nin etkin bağdaştırıcıları belirleme</span><span class="sxs-lookup"><span data-stu-id="db312-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="db312-144">Bir bilgisayarda DHCP özellikli bağdaştırıcıları bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db312-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="db312-145">IP yapılandırma sorunlarını Adaptörünün tutmak için yalnızca IP özellikli bağdaştırıcıları alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db312-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="db312-146">DHCP özellikleri alınıyor</span><span class="sxs-lookup"><span data-stu-id="db312-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="db312-147">DHCP ile ilgili özellikler için bir bağdaştırıcı "DHCP ile" genellikle başladığı için yalnızca bu özellikleri görüntülemek için Format-Table özellik parametresinin kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db312-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="db312-148">Her bağdaştırıcı DHCP etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="db312-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="db312-149">Tüm bağdaştırıcılarında DHCP'yi etkinleştirmek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="db312-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="db312-150">Kullanabileceğiniz **filtre** deyimi "IPEnabled $true ve DHCPEnabled = $false =" nerede zaten etkinleştirilmiş, ancak bu adımı atlayarak değil neden hataları DHCP etkinleştirme önlemek için.</span><span class="sxs-lookup"><span data-stu-id="db312-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="db312-151">Serbest bırakarak ve belirli bağdaştırıcılarında DHCP kiralarını yenileme</span><span class="sxs-lookup"><span data-stu-id="db312-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="db312-152">**Win32_NetworkAdapterConfiguration** sınıfında **ReleaseDHCPLease()** ve **RenewDHCPLease** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="db312-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="db312-153">Her ikisi de aynı şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db312-153">Both are used in the same way.</span></span> <span data-ttu-id="db312-154">Genel olarak, bırakmak veya belirli bir alt ağdaki bir bağdaştırıcı için adresleri yenilemek yalnızca ihtiyacınız varsa bu yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="db312-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="db312-155">Bir alt ağ bağdaştırıcılarında filtre için en kolay yolu, ağ geçidini kullanmak için bu alt ağ bağdaştırıcısı yapılandırmalarının seçmektir.</span><span class="sxs-lookup"><span data-stu-id="db312-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="db312-156">Örneğin, aşağıdaki komutu 192.168.1.254 DHCP kiraları elde etme bağdaştırıcılarında yerel bilgisayardaki tüm DHCP kirası serbest bırakır:</span><span class="sxs-lookup"><span data-stu-id="db312-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="db312-157">DHCP kirasını yenilemek için tek değişiklik kullanmaktır **RenewDHCPLease** yöntemi yerine **ReleaseDHCPLease()** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="db312-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="db312-158">Uzak bir bilgisayarda bu yöntemleri kullanırken, kendisine yayımlanmış veya yenilenen kira bağdaştırıcıyla aracılığıyla birbirine bağlandıysa uzak sisteme erişimi kaybedebilir miyim dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="db312-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="db312-159">Serbest bırakarak ve tüm bağdaştırıcılarında DHCP kiralarını yenileme</span><span class="sxs-lookup"><span data-stu-id="db312-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="db312-160">Kullanarak tüm bağdaştırıcılarında genel DHCP adresi sürümleri veya yenileme gerçekleştirebilirsiniz **Win32_NetworkAdapterConfiguration** yöntemleri **ReleaseDHCPLeaseAll** ve **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="db312-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="db312-161">Bununla birlikte, komut belirli bir bağdaştırıcı yerine WMI sınıfını serbest olduğundan uygulamanız gerekir ve genel olarak kira yenileme değil, belirli bir bağdaştırıcı sınıfı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="db312-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="db312-162">Tüm WMI sınıflarını listeleme ve ardından yalnızca istenen sınıf adına göre seçerek, sınıf örneklerinin yerine, WMI sınıfına bir başvuru alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db312-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="db312-163">Örneğin, aşağıdaki komutu Win32_NetworkAdapterConfiguration sınıfını döndürür:</span><span class="sxs-lookup"><span data-stu-id="db312-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="db312-164">Tüm komut sınıf olarak kabul et ve ardından çağırmak **ReleaseDHCPAdapterLease** yöntemini.</span><span class="sxs-lookup"><span data-stu-id="db312-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="db312-165">Aşağıdaki komutta, çevreleyen parantezler **Get-WmiObject** ve **Where-Object** ardışık öğeleri doğrudan Windows PowerShell'i ilk değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="db312-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="db312-166">Aynı komut biçimi çağırmak için kullanabileceğiniz **RenewDHCPLeaseAll** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="db312-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="db312-167">Bir ağ paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="db312-167">Creating a Network Share</span></span>

<span data-ttu-id="db312-168">Bir ağ paylaşımı oluşturmak için kullanın **Win32_Share oluşturma** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="db312-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="db312-169">Kullanarak bir paylaşım oluşturabilirsiniz **ağ paylaşımı** Windows PowerShell'de:</span><span class="sxs-lookup"><span data-stu-id="db312-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="db312-170">Bir ağ paylaşımı kaldırma</span><span class="sxs-lookup"><span data-stu-id="db312-170">Removing a Network Share</span></span>

<span data-ttu-id="db312-171">Bir ağ paylaşımı ile kaldırabilirsiniz **Win32_Share**, ancak belirli bir paylaşım kaldırılacak, alınacak gerektiğinden bir paylaşımı oluşturmaktan biraz farklı işlemidir yerine **Win32_Share** sınıf.</span><span class="sxs-lookup"><span data-stu-id="db312-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="db312-172">Aşağıdaki deyim, paylaşım "TempShare" siler:</span><span class="sxs-lookup"><span data-stu-id="db312-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="db312-173">**Ağ Paylaşımı** de çalışır:</span><span class="sxs-lookup"><span data-stu-id="db312-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="db312-174">Bir Windows erişilebilir bir ağ sürücüsü bağlanma</span><span class="sxs-lookup"><span data-stu-id="db312-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="db312-175">**Yeni PSDrive** cmdlet'lerini Windows PowerShell sürücüsünü oluşturur, ancak bu şekilde oluşturulan sürücüleri yalnızca Windows PowerShell için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db312-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="db312-176">Yeni bir ağ sürücüsü oluşturmak için kullanabileceğiniz **WScript.Network** COM nesnesi.</span><span class="sxs-lookup"><span data-stu-id="db312-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="db312-177">Aşağıdaki komutu paylaşım eşler \\ \\FPS01\\kullanıcılar yerel sürücüye B:</span><span class="sxs-lookup"><span data-stu-id="db312-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="db312-178">**Net kullanım** komutu de çalışır:</span><span class="sxs-lookup"><span data-stu-id="db312-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="db312-179">İle eşleşen sürücüler **WScript.Network** veya Windows PowerShell için hemen kullanılabilir ağ kullanın.</span><span class="sxs-lookup"><span data-stu-id="db312-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>