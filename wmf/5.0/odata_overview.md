---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 01d4989711c22db20431876c52740afb350caad0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>OData Uç Noktasına göre PowerShell Cmdlet’leri Oluşturma
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Bir OData uç noktada tabanlı Windows PowerShell cmdlet'leri oluştur
--------------------------------------------------------------

**Dışarı aktarma ODataEndpointProxy** belirli bir OData uç noktası tarafından sunulan işlevselliği temel Windows PowerShell cmdlet'leri kümesini oluşturan bir cmdlet.

Aşağıdaki örnek, bu yeni cmdlet'inin nasıl kullanılacağı gösterilmektedir:

\# Dışarı aktarma ODataEndpointProxy temel kullanım örneği

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

Geliştirme dahil ancak bunlarla sınırlı olmamak üzere, bu işlev için anahtar kullanım durumlarında bölümlerini hala vardır:
-   İlişkilendirmeleri
-   Akışlar geçirme

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Bir OData uç nokta ODataUtils ile temel Windows PowerShell cmdlet'leri oluştur
------------------------------------------------------------------------------
ODataUtils modülü OData desteği REST uç noktalarını Windows PowerShell cmdlet'leri oluşturulmasını sağlar. Aşağıdaki artımlı iyileştirmeleri Microsoft.PowerShell.ODataUtils Windows PowerShell modülündeki ' dir.
-   Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.
-   İstemci-tarafı sayfalama desteği
-   Kullanarak sunucu tarafı filtreleme parametre seçimi
-   Web isteği üstbilgileri desteği

Dışarı aktarma ODataEndPointProxy cmdlet tarafından oluşturulan proxy cmdlet'leri ek bilgileri (istemci-tarafı proxy oluşturma sırasında kullanılan $metadata belirtilen değil) sunucudan yan OData uç noktası bilgileri akışta (yeni Windows sağlar PowerShell 5.0 özelliği). Bu bilgilerin nasıl alınacağını bir örneği burada verilmiştir.
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

Kayıtları, istemci-tarafı sayfalama desteğini kullanarak sunucu tarafı yığınlardaki'nden edinebilirsiniz. Bu, ağ üzerinde büyük miktarda veri sunucudan almalısınız durumunda faydalı olur.
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

Oluşturulan proxy cmdlet'leri destekleyen istemci gereken kaydı özellikler almak için bir filtre olarak kullanabilirsiniz Select parametresini. Filtreleme sunucu tarafında oluştuğundan bu ağ üzerinden aktarılan veri miktarını azaltır.
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Dışarı aktarma ODataEndpointProxy cmdlet ve işlem tarafından oluşturulan proxy cmdlet'lerini artık sunucu tarafı OData uç noktası tarafından beklenen ek bilgileri kanal kullandığınız üstbilgileri parametre (tedarik değerler) bir karma tablosu olarak destekler. Aşağıdaki örnekte, kimlik doğrulaması için bir abonelik anahtar bekleniyor Hizmetleri için bir abonelik anahtar üstbilgileri aracılığıyla yönlendirebilir.
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
