---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 11891587f59dc8a38e4ce267018160f7f9a28178
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="524f2-102">OData uç tabanlı PowerShell cmdlet'leri oluştur</span><span class="sxs-lookup"><span data-stu-id="524f2-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="524f2-103">Bir OData uç noktada tabanlı Windows PowerShell cmdlet'leri oluştur</span><span class="sxs-lookup"><span data-stu-id="524f2-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>
--------------------------------------------------------------

<span data-ttu-id="524f2-104">**Dışarı aktarma ODataEndpointProxy** belirli bir OData uç noktası tarafından sunulan işlevselliği temel Windows PowerShell cmdlet'leri kümesini oluşturan bir cmdlet.</span><span class="sxs-lookup"><span data-stu-id="524f2-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="524f2-105">Aşağıdaki örnek, bu yeni cmdlet'inin nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="524f2-105">The following example shows how to use this new cmdlet:</span></span>

<span data-ttu-id="524f2-106">\#Dışarı aktarma ODataEndpointProxy temel kullanım örneği</span><span class="sxs-lookup"><span data-stu-id="524f2-106">\# Basic use case of Export-ODataEndpointProxy</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="524f2-107">Geliştirme dahil ancak bunlarla sınırlı olmamak üzere, bu işlev için anahtar kullanım durumlarında bölümlerini hala vardır:</span><span class="sxs-lookup"><span data-stu-id="524f2-107">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="524f2-108">İlişkilendirmeleri</span><span class="sxs-lookup"><span data-stu-id="524f2-108">Associations</span></span>
-   <span data-ttu-id="524f2-109">Akışlar geçirme</span><span class="sxs-lookup"><span data-stu-id="524f2-109">Passing streams</span></span>

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="524f2-110">Bir OData uç nokta ODataUtils ile temel Windows PowerShell cmdlet'leri oluştur</span><span class="sxs-lookup"><span data-stu-id="524f2-110">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>
------------------------------------------------------------------------------
<span data-ttu-id="524f2-111">ODataUtils modülü OData desteği REST uç noktalarını Windows PowerShell cmdlet'leri oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="524f2-111">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="524f2-112">Aşağıdaki artımlı iyileştirmeleri Microsoft.PowerShell.ODataUtils Windows PowerShell modülündeki ' dir.</span><span class="sxs-lookup"><span data-stu-id="524f2-112">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="524f2-113">Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.</span><span class="sxs-lookup"><span data-stu-id="524f2-113">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="524f2-114">İstemci-tarafı sayfalama desteği</span><span class="sxs-lookup"><span data-stu-id="524f2-114">Client-side paging support</span></span>
-   <span data-ttu-id="524f2-115">Kullanarak sunucu tarafı filtreleme parametre seçimi</span><span class="sxs-lookup"><span data-stu-id="524f2-115">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="524f2-116">Web isteği üstbilgileri desteği</span><span class="sxs-lookup"><span data-stu-id="524f2-116">Support for web request headers</span></span>

<span data-ttu-id="524f2-117">Dışarı aktarma ODataEndPointProxy cmdlet tarafından oluşturulan proxy cmdlet'leri ek bilgileri (istemci-tarafı proxy oluşturma sırasında kullanılan $metadata belirtilen değil) sunucudan yan OData uç noktası bilgileri akışta (yeni Windows sağlar PowerShell 5.0 özelliği).</span><span class="sxs-lookup"><span data-stu-id="524f2-117">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="524f2-118">Bu bilgilerin nasıl alınacağını bir örneği burada verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="524f2-118">Here is an example of how to get that information.</span></span>
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="524f2-119">Kayıtları, istemci-tarafı sayfalama desteğini kullanarak sunucu tarafı yığınlardaki'nden edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="524f2-119">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="524f2-120">Bu, ağ üzerinde büyük miktarda veri sunucudan almalısınız durumunda faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="524f2-120">This is useful when you must get a large amount of data from the server over the network.</span></span>
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="524f2-121">Oluşturulan proxy cmdlet'leri destekleyen istemci gereken kaydı özellikler almak için bir filtre olarak kullanabilirsiniz Select parametresini.</span><span class="sxs-lookup"><span data-stu-id="524f2-121">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="524f2-122">Filtreleme sunucu tarafında oluştuğundan bu ağ üzerinden aktarılan veri miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="524f2-122">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="524f2-123">Dışarı aktarma ODataEndpointProxy cmdlet ve işlem tarafından oluşturulan proxy cmdlet'lerini artık sunucu tarafı OData uç noktası tarafından beklenen ek bilgileri kanal kullandığınız üstbilgileri parametre (tedarik değerler) bir karma tablosu olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="524f2-123">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="524f2-124">Aşağıdaki örnekte, kimlik doğrulaması için bir abonelik anahtar bekleniyor Hizmetleri için bir abonelik anahtar üstbilgileri aracılığıyla yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="524f2-124">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```

