---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057817"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="846ce-102">OData Uç Noktasına göre PowerShell Cmdlet’leri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="846ce-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="846ce-103">Bir OData uç noktasına göre Windows PowerShell cmdlet'leri oluşturma</span><span class="sxs-lookup"><span data-stu-id="846ce-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="846ce-104">**Dışarı aktarma ODataEndpointProxy** bir cmdlet'i belirtilen bir OData uç noktası tarafından sunulan işlevselliği temel Windows PowerShell cmdlet'leri bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="846ce-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="846ce-105">Aşağıdaki örnek, yeni bu cmdlet'in nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="846ce-105">The following example shows how to use this new cmdlet:</span></span>

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

<span data-ttu-id="846ce-106">Hala geliştirme dahil ancak bunlarla sınırlı olmamak üzere, bu işlev için anahtar kullanım durumlarında bölümleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="846ce-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="846ce-107">İlişkilendirmeleri</span><span class="sxs-lookup"><span data-stu-id="846ce-107">Associations</span></span>
-   <span data-ttu-id="846ce-108">Akışları geçirme</span><span class="sxs-lookup"><span data-stu-id="846ce-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="846ce-109">OData uç noktası ile ODataUtils temel Windows PowerShell cmdlet'leri oluşturma</span><span class="sxs-lookup"><span data-stu-id="846ce-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="846ce-110">ODataUtils modül OData desteği REST uç noktalarını Windows PowerShell cmdlet'lerinden oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="846ce-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="846ce-111">Aşağıdaki artımlı iyileştirmeleri Microsoft.PowerShell.ODataUtils Windows PowerShell modülünde olan.</span><span class="sxs-lookup"><span data-stu-id="846ce-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="846ce-112">Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.</span><span class="sxs-lookup"><span data-stu-id="846ce-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="846ce-113">İstemci tarafı sayfalama desteği</span><span class="sxs-lookup"><span data-stu-id="846ce-113">Client-side paging support</span></span>
-   <span data-ttu-id="846ce-114">Kullanarak sunucu tarafı filtreleme Select parametresi</span><span class="sxs-lookup"><span data-stu-id="846ce-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="846ce-115">Web isteği üst bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="846ce-115">Support for web request headers</span></span>

<span data-ttu-id="846ce-116">Dışarı aktarma ODataEndPointProxy cmdlet tarafından oluşturulan proxy cmdlet'leri ek bilgileri (istemci-tarafı proxy oluşturma sırasında kullanılan $metadata belirtilen değil) sunucudan yan OData uç noktası bilgi akışını (bir yeni Windows sağlar PowerShell 5.0 özelliği).</span><span class="sxs-lookup"><span data-stu-id="846ce-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="846ce-117">Bu bilgileri almak nasıl bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="846ce-117">Here is an example of how to get that information.</span></span>

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

<span data-ttu-id="846ce-118">Kayıtları, istemci tarafı sayfalama desteğini kullanarak sunucu tarafı toplu sayfasından edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="846ce-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="846ce-119">Sunucudan ağ üzerinden büyük miktarda veri almalısınız istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="846ce-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

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

<span data-ttu-id="846ce-120">Oluşturulan proxy cmdlet'leri desteği yalnızca istemci kayıt özelliklerini almak için filtre kullanabilir Select parametresini.</span><span class="sxs-lookup"><span data-stu-id="846ce-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="846ce-121">Filtreleme sunucu tarafında oluştuğu için bu ağ üzerinden aktarılan veri miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="846ce-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="846ce-122">Dışarı aktarma ODataEndpointProxy cmdlet ve işlem tarafından oluşturulan proxy cmdlet'leri artık sunucu tarafı OData uç noktası tarafından beklenen herhangi bir ek bilgi kanal için kullanabileceğiniz üst bilgiler parametre (tedarik değerler) bir karma tablosu olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="846ce-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="846ce-123">Aşağıdaki örnekte, üst bilgileri ile kimlik doğrulaması için bir abonelik anahtarı görmeyi Hizmetleri için bir abonelik anahtarı yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="846ce-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
