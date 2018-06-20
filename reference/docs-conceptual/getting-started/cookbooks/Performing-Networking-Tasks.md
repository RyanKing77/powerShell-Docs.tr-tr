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
# <a name="performing-networking-tasks"></a><span data-ttu-id="d5789-103">Ağ Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d5789-103">Performing Networking Tasks</span></span>

<span data-ttu-id="d5789-104">TCP/IP'yi en yaygın kullanılan ağ protokolü olduğundan, en alt düzey ağ protokolü yönetim görevlerini TCP/IP'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="d5789-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="d5789-105">Bu bölümde, Windows PowerShell ve WMI bu görevleri gerçekleştirmek için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="d5789-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="d5789-106">Bir bilgisayar için IP adreslerini listeleme</span><span class="sxs-lookup"><span data-stu-id="d5789-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="d5789-107">Yerel bilgisayarda tüm IP adreslerini almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5789-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="d5789-108">Bu komutun çıktısı, çoğu özellik listelerinden farklıdır, bu değerleri ayraç içine çünkü:</span><span class="sxs-lookup"><span data-stu-id="d5789-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="d5789-109">Küme ayraçları neden görünüyor anlamak için incelemek için Get-üye cmdlet'ini kullanın **IPADDRESS** özelliği:</span><span class="sxs-lookup"><span data-stu-id="d5789-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="d5789-110">Her ağ bağdaştırıcısı için IPADDRESS aslında bir dizi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d5789-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="d5789-111">Küme ayraçları tanımında belirtmek **IPADDRESS** değil bir **System.String** değeri, ancak bir dizi **System.String** değerleri.</span><span class="sxs-lookup"><span data-stu-id="d5789-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="d5789-112">IP yapılandırma verilerini listeleme</span><span class="sxs-lookup"><span data-stu-id="d5789-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="d5789-113">Her ağ bağdaştırıcısı için ayrıntılı IP yapılandırma verilerini görüntülemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5789-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="d5789-114">Ağ bağdaştırıcısı yapılandırma nesnesi için varsayılan görüntü kullanılabilir bilgi çok sınırlı bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="d5789-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="d5789-115">Ayrıntılı inceleme ve sorun giderme için görüntülenecek özelliklerini belirtmek için Select-Object veya Format-List gibi bir biçimlendirme cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5789-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="d5789-116">IPX veya WINS özelliklerinde değil ilgileniyorsanız — büyük olasılıkla modern bir TCP/IP ağı durumda — "WINS" ile başlayan adları özelliklerle gizlemek için Select-Object ExcludeProperty parametresinin kullanabilirsiniz veya "IPX:"</span><span class="sxs-lookup"><span data-stu-id="d5789-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="d5789-117">Bu komut, DHCP, DNS, yönlendirme hakkında ayrıntılı bilgi ve diğer ikincil IP yapılandırma özellikleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5789-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="d5789-118">Ping bilgisayarlar</span><span class="sxs-lookup"><span data-stu-id="d5789-118">Pinging Computers</span></span>

<span data-ttu-id="d5789-119">Bir bilgisayar kullanarak karşı basit bir ping gerçekleştirebilirsiniz **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="d5789-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="d5789-120">Aşağıdaki komutu ping işlemi gerçekleştirir, ancak uzun çıktıyı döndürür:</span><span class="sxs-lookup"><span data-stu-id="d5789-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="d5789-121">Aşağıdaki komutu tarafından oluşturulan bir daha kullanışlı form için Özet bilgiler bir görüntü adresi, yanıt süresi ve StatusCode özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d5789-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="d5789-122">Windows PowerShell'de düzgün görüntüledikleri böylece Format-Table Autosize parametresinin tablo sütunları yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="d5789-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="d5789-123">Durum kodu 0 PING başarılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5789-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="d5789-124">Tek bir komutla birden çok bilgisayara ping işlemi yapmak için bir dizi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5789-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="d5789-125">Birden fazla adres olduğundan kullanın **ForEach-Object** her adresi ayrı ayrı ping işlemi yapmak için:</span><span class="sxs-lookup"><span data-stu-id="d5789-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="d5789-126">Ağ sayısı 192.168.1.0 ve standart bir C sınıfı alt ağ maskesi (255.255.255.0) kullanan bir özel ağ gibi bir alt ağdaki tüm bilgisayarların ping işlemi yapmak için aynı komut biçimini kullanabilirsiniz., yalnızca 192.168.1.254 aracılığıyla 192.168.1.1 aralıktaki adresler Yerel adresler (0, her zaman bir alt ağ yayın adresi ağ sayısı ve 255 için ayrılmıştır) yasal.</span><span class="sxs-lookup"><span data-stu-id="d5789-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="d5789-127">Bir dizi sayının 1'den Windows PowerShell'de 254 temsil etmek için Ek Yardım deyimini **1..254.**</span><span class="sxs-lookup"><span data-stu-id="d5789-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="d5789-128">Bir tam alt ping dizi oluşturmak ve ardından ping deyiminde kısmi bir adresi üzerine değerleri ekleyerek gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="d5789-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="d5789-129">Bir adres aralığı oluşturmak için bu tekniği de başka bir yerde kullanılabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d5789-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="d5789-130">Bu şekilde adresleri eksiksiz bir kümesini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5789-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="d5789-131">Ağ bağdaştırıcısı özelliklerini alma</span><span class="sxs-lookup"><span data-stu-id="d5789-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="d5789-132">Kılavuzda daha önce bu kullanıcının, biz genel yapılandırma özelliklerini kullanarak alınamadı bahsedilen **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="d5789-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="d5789-133">Kesinlikle olmadığında TCP/IP'yi bilgi rağmen ağ bağdaştırıcı bilgileri gibi MAC adresleri ve bağdaştırıcısı türlerini bir bilgisayarla neler olduğunu anlamak için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5789-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="d5789-134">Bu bilgilerin özetini almak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5789-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="d5789-135">Bir ağ bağdaştırıcısı için DNS etki alanının atama</span><span class="sxs-lookup"><span data-stu-id="d5789-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="d5789-136">Otomatik ad çözümlemesi için DNS etki alanı atamak için kullandığınız **Win32_NetworkAdapterConfiguration SetDNSDomain** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d5789-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="d5789-137">DNS etki alanı her ağ bağdaştırıcısı yapılandırması için bağımsız olarak atamak için kullanmak gereken bir **ForEach-Object** deyimi her bağdaştırıcı için etki alanı atamak için:</span><span class="sxs-lookup"><span data-stu-id="d5789-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="d5789-138">Filtre ifadesi "IPEnabled $true =" yalnızca TCP/IP'yi kullanır bile bir ağ üzerinde birçok ağ bağdaştırıcısı yapılandırmalarından bir bilgisayarda doğru TCP/IP'yi bağdaştırıcıları; olmadığından gereklidir Bunlar RAS, PPTP, QoS ve diğer hizmetleri tüm bağdaştırıcıların destekleme Genel yazılım öğeleridir ve dolayısıyla kendi bir adresi yok.</span><span class="sxs-lookup"><span data-stu-id="d5789-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="d5789-139">Komutunu kullanarak filtreleyebilirsiniz **Where-Object** kullanmak yerine cmdlet **Get-WmiObject** Filtresi.</span><span class="sxs-lookup"><span data-stu-id="d5789-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="d5789-140">DHCP yapılandırma görevlerini gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d5789-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="d5789-141">DNS yapılandırması gibi DHCP ayrıntıları değiştirme ağ bağdaştırıcıları, bir dizi çalışma içerir.</span><span class="sxs-lookup"><span data-stu-id="d5789-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="d5789-142">WMI kullanarak gerçekleştirebileceğiniz çeşitli farklı eylemler vardır ve ortak olanlara birkaç adım.</span><span class="sxs-lookup"><span data-stu-id="d5789-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="d5789-143">DHCP etkin bağdaştırıcıları belirleme</span><span class="sxs-lookup"><span data-stu-id="d5789-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="d5789-144">Bir bilgisayarda DHCP etkin bağdaştırıcıları bulmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5789-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="d5789-145">IP yapılandırma sorunlarını bağdaştırıcılarla dışlamak için yalnızca IP etkin bağdaştırıcıları alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5789-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="d5789-146">DHCP özelliklerini alma</span><span class="sxs-lookup"><span data-stu-id="d5789-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="d5789-147">DHCP ile ilgili özellikler için bir bağdaştırıcı genellikle "DHCP" ile başladığı için yalnızca bu özellikleri görüntülemek için Tablo Biçimlendir özellik parametresinin kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5789-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="d5789-148">Her bağdaştırıcı üzerindeki DHCP etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d5789-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="d5789-149">Tüm bağdaştırıcıları DHCP etkinleştirmek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5789-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="d5789-150">Kullanabileceğiniz **filtre** deyimi "IPEnabled $true ve DHCPEnabled = $false =", zaten etkin, ancak bu adımı atlayarak değil neden olacak hataları DHCP etkinleştirme önlemek için.</span><span class="sxs-lookup"><span data-stu-id="d5789-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="d5789-151">Serbest bırakma ve DHCP kiralarını belirli bağdaştırıcılarında yenileniyor</span><span class="sxs-lookup"><span data-stu-id="d5789-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="d5789-152">**Win32_NetworkAdapterConfiguration** sınıfına sahip **ReleaseDHCPLease()** ve **RenewDHCPLease** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d5789-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="d5789-153">Her ikisi de aynı şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5789-153">Both are used in the same way.</span></span> <span data-ttu-id="d5789-154">Genel olarak, yalnızca bırakmak veya belirli bir alt ağdaki bir bağdaştırıcı için adresleri yenilemek gerekiyorsa bu yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5789-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="d5789-155">Filtre bağdaştırıcılarına bir alt ağda en kolay yolu, ağ geçidini kullanmak için bu alt ağ bağdaştırıcısı yapılandırmalarından seçmektir.</span><span class="sxs-lookup"><span data-stu-id="d5789-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="d5789-156">Örneğin, aşağıdaki komut, DHCP kiralarını 192.168.1.254 alma bağdaştırıcılarda yerel bilgisayardaki tüm DHCP kiralarını serbest bırakır:</span><span class="sxs-lookup"><span data-stu-id="d5789-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="d5789-157">Bir DHCP kiralama yenileme için tek değişiklik kullanmaktır **RenewDHCPLease** yöntemi yerine **ReleaseDHCPLease()** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d5789-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="d5789-158">Uzak bir bilgisayarda bu yöntemleri kullanarak, yayımlanan veya yenilenen kira ile bağdaştırıcısından kendisine bağlıysanız, uzak sisteme erişimi kaybedebilir miyim unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d5789-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="d5789-159">Serbest bırakma ve DHCP kiralarını tüm bağdaştırıcılarda yenileniyor</span><span class="sxs-lookup"><span data-stu-id="d5789-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="d5789-160">Kullanarak tüm bağdaştırıcılarında genel DHCP adresi sürümleri veya yenilemeleri gerçekleştirebileceğiniz **Win32_NetworkAdapterConfiguration** yöntemleri **ReleaseDHCPLeaseAll** ve **RenewDHCPLeaseAll** .</span><span class="sxs-lookup"><span data-stu-id="d5789-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="d5789-161">Ancak, komut belirli bir bağdaştırıcı yerine WMI sınıfı bırakılıyor çünkü uygulamanız gerekir ve genel kira yenileme değil, belirli bir bağdaştırıcı sınıfı gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d5789-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="d5789-162">Tüm WMI sınıflarını listeleme ve ardından istediğiniz sınıfı adıyla seçerek sınıf örneklerinin yerine bir WMI sınıfı başvurusu elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5789-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="d5789-163">Örneğin, aşağıdaki komut, Win32_NetworkAdapterConfiguration sınıfını döndürür:</span><span class="sxs-lookup"><span data-stu-id="d5789-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="d5789-164">Tüm komut sınıfı olarak davranmak ve ardından çağırma **ReleaseDHCPAdapterLease** yöntemini.</span><span class="sxs-lookup"><span data-stu-id="d5789-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="d5789-165">Aşağıdaki komutta, çevreleyen parantez **Get-WmiObject** ve **Where-Object** ardışık düzen öğeleri doğrudan Windows PowerShell'i ilk değerlendirin:</span><span class="sxs-lookup"><span data-stu-id="d5789-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="d5789-166">Çağrılacak aynı komut biçimini kullanabilirsiniz **RenewDHCPLeaseAll** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d5789-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="d5789-167">Bir ağ paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5789-167">Creating a Network Share</span></span>

<span data-ttu-id="d5789-168">Bir ağ paylaşımı oluşturmak için kullanmak **Win32_Share oluşturmak** yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d5789-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="d5789-169">Kullanarak paylaşım oluşturabilirsiniz **ağ paylaşımı** Windows PowerShell'de:</span><span class="sxs-lookup"><span data-stu-id="d5789-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="d5789-170">Bir ağ paylaşımı kaldırma</span><span class="sxs-lookup"><span data-stu-id="d5789-170">Removing a Network Share</span></span>

<span data-ttu-id="d5789-171">Bir ağ paylaşımı ile kaldırabilirsiniz **Win32_Share**, ancak kaldırılması için özel paylaşım almak gerektiğinden biraz farklı bir paylaşım oluşturma işlemidir yerine **Win32_Share** sınıf.</span><span class="sxs-lookup"><span data-stu-id="d5789-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="d5789-172">Aşağıdaki deyim "TempShare" Paylaşımı siler:</span><span class="sxs-lookup"><span data-stu-id="d5789-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="d5789-173">**Ağ Paylaşımı** de çalışır:</span><span class="sxs-lookup"><span data-stu-id="d5789-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="d5789-174">Windows erişilebilir bir ağ sürücüsü bağlanma</span><span class="sxs-lookup"><span data-stu-id="d5789-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="d5789-175">**Yeni PSDrive** cmdlet'leri bir Windows PowerShell sürücüsü oluşturur, ancak bu yolla oluşturulan sürücüleri yalnızca Windows PowerShell için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5789-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="d5789-176">Yeni bir ağ sürücüsü oluşturmak için kullanabileceğiniz **WScript.Network** COM nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d5789-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="d5789-177">Aşağıdaki komutu paylaşım eşlemeleri \\ \\FPS01\\kullanıcılar yerel sürücüye B:</span><span class="sxs-lookup"><span data-stu-id="d5789-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="d5789-178">**Net kullanım** komutu çalışır de:</span><span class="sxs-lookup"><span data-stu-id="d5789-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="d5789-179">Biriyle eşlenen sürücüler **WScript.Network** veya net kullanmak için Windows PowerShell hemen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5789-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>