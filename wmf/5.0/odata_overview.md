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
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>OData Uç Noktasına göre PowerShell Cmdlet’leri Oluşturma

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Bir OData uç noktasına göre Windows PowerShell cmdlet'leri oluşturma

**Dışarı aktarma ODataEndpointProxy** bir cmdlet'i belirtilen bir OData uç noktası tarafından sunulan işlevselliği temel Windows PowerShell cmdlet'leri bir dizi oluşturur.

Aşağıdaki örnek, yeni bu cmdlet'in nasıl kullanılacağı gösterilmektedir:

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

Hala geliştirme dahil ancak bunlarla sınırlı olmamak üzere, bu işlev için anahtar kullanım durumlarında bölümleri şunlardır:
-   İlişkilendirmeleri
-   Akışları geçirme

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>OData uç noktası ile ODataUtils temel Windows PowerShell cmdlet'leri oluşturma

ODataUtils modül OData desteği REST uç noktalarını Windows PowerShell cmdlet'lerinden oluşturulmasını sağlar. Aşağıdaki artımlı iyileştirmeleri Microsoft.PowerShell.ODataUtils Windows PowerShell modülünde olan.
-   Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.
-   İstemci tarafı sayfalama desteği
-   Kullanarak sunucu tarafı filtreleme Select parametresi
-   Web isteği üst bilgileri için destek

Dışarı aktarma ODataEndPointProxy cmdlet tarafından oluşturulan proxy cmdlet'leri ek bilgileri (istemci-tarafı proxy oluşturma sırasında kullanılan $metadata belirtilen değil) sunucudan yan OData uç noktası bilgi akışını (bir yeni Windows sağlar PowerShell 5.0 özelliği). Bu bilgileri almak nasıl bir örnek aşağıda verilmiştir.

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

Kayıtları, istemci tarafı sayfalama desteğini kullanarak sunucu tarafı toplu sayfasından edinebilirsiniz. Sunucudan ağ üzerinden büyük miktarda veri almalısınız istediğinizde yararlıdır.

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

Oluşturulan proxy cmdlet'leri desteği yalnızca istemci kayıt özelliklerini almak için filtre kullanabilir Select parametresini. Filtreleme sunucu tarafında oluştuğu için bu ağ üzerinden aktarılan veri miktarını azaltır.

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Dışarı aktarma ODataEndpointProxy cmdlet ve işlem tarafından oluşturulan proxy cmdlet'leri artık sunucu tarafı OData uç noktası tarafından beklenen herhangi bir ek bilgi kanal için kullanabileceğiniz üst bilgiler parametre (tedarik değerler) bir karma tablosu olarak destekler. Aşağıdaki örnekte, üst bilgileri ile kimlik doğrulaması için bir abonelik anahtarı görmeyi Hizmetleri için bir abonelik anahtarı yönlendirebilir.

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
