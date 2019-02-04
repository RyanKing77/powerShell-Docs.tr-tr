---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683768"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="1dd9e-102">PowerShell ile Ağ Anahtarı Yönetimi</span><span class="sxs-lookup"><span data-stu-id="1dd9e-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="1dd9e-103">**Get-NetworkSwitchEthernetPort** cmdlet örnekleri aşağıdaki ek bilgilerle artık döndürür:</span><span class="sxs-lookup"><span data-stu-id="1dd9e-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="1dd9e-104">IPADDRESS: bağlantı noktası ile ilişkili IP adresi</span><span class="sxs-lookup"><span data-stu-id="1dd9e-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="1dd9e-105">PortMode – bağlantı noktası modu: erişim, yönlendirme veya santral</span><span class="sxs-lookup"><span data-stu-id="1dd9e-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="1dd9e-106">Bu bağlantı noktası erişim modunda VLAN kimliği AccessVLAN – ilişkili</span><span class="sxs-lookup"><span data-stu-id="1dd9e-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="1dd9e-107">Bu bağlantı noktası santral modunda, kimlikleri VLAN'ların listesini TrunkedVLANList – ilişkili</span><span class="sxs-lookup"><span data-stu-id="1dd9e-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="1dd9e-108">Windows PowerShell ile temel ağ anahtarı yönetimi</span><span class="sxs-lookup"><span data-stu-id="1dd9e-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="1dd9e-109">WMF 5. 0'da, sunulan ağ anahtarı cmdlet'leri Windows Server 2012 R2 logo sertifikalı ağ anahtarları için anahtar ve sanal LAN (VLAN) temel Katman 2 ağ anahtarı bağlantı noktası yapılandırması uygulamanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dd9e-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="1dd9e-110">Microsoft kalır desteklemeye [veri merkezi soyutlama](http://technet.microsoft.com/cloud/dal.aspx) düzeyi (DAL) işleme ve müşterilerimiz ve iş ortakları bu alandaki değer göstermek için.</span><span class="sxs-lookup"><span data-stu-id="1dd9e-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="1dd9e-111">Bu cmdlet'leri kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1dd9e-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="1dd9e-112">Genel yapılandırma, aşağıdaki gibi geçin:</span><span class="sxs-lookup"><span data-stu-id="1dd9e-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="1dd9e-113">Kümesi konak adı</span><span class="sxs-lookup"><span data-stu-id="1dd9e-113">Set host name</span></span>
    - <span data-ttu-id="1dd9e-114">Set anahtar başlığı</span><span class="sxs-lookup"><span data-stu-id="1dd9e-114">Set switch banner</span></span>
    - <span data-ttu-id="1dd9e-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1dd9e-115">Persist configuration</span></span>
    - <span data-ttu-id="1dd9e-116">Etkinleştirmek veya devre dışı özelliği</span><span class="sxs-lookup"><span data-stu-id="1dd9e-116">Enable or disable feature</span></span>

- <span data-ttu-id="1dd9e-117">VLAN yapılandırması:</span><span class="sxs-lookup"><span data-stu-id="1dd9e-117">VLAN configuration:</span></span>
    - <span data-ttu-id="1dd9e-118">Oluşturma veya VLAN'ı kaldırma</span><span class="sxs-lookup"><span data-stu-id="1dd9e-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="1dd9e-119">Etkinleştirmek veya VLAN devre dışı</span><span class="sxs-lookup"><span data-stu-id="1dd9e-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="1dd9e-120">VLAN listeleme</span><span class="sxs-lookup"><span data-stu-id="1dd9e-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="1dd9e-121">VLAN kolay adı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="1dd9e-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="1dd9e-122">Katman 2 bağlantı noktası yapılandırması:</span><span class="sxs-lookup"><span data-stu-id="1dd9e-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="1dd9e-123">Bağlantı noktalarını Listele</span><span class="sxs-lookup"><span data-stu-id="1dd9e-123">Enumerate ports</span></span>
    - <span data-ttu-id="1dd9e-124">Etkinleştirmek veya devre dışı bağlantı noktaları</span><span class="sxs-lookup"><span data-stu-id="1dd9e-124">Enable or disable ports</span></span>
    - <span data-ttu-id="1dd9e-125">Küme bağlantı modları ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="1dd9e-125">Set port modes and properties</span></span>
    - <span data-ttu-id="1dd9e-126">Ekleme veya VLAN santral veya numaralı bağlantı noktasında ilişkilendirin</span><span class="sxs-lookup"><span data-stu-id="1dd9e-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="1dd9e-127">Tüm NetworkSwitch cmdlet'leri için bakarak keşfetmeye başlayın!</span><span class="sxs-lookup"><span data-stu-id="1dd9e-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="1dd9e-128">Daha fazla bilgi Jeffrey Snover'ın WMF 5.0 Önizleme Duyurusu blog gönderisinde bulabilirsiniz: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="1dd9e-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
