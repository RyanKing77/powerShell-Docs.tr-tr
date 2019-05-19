---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Yeni ve güncelleştirilmiş cmdlet'ler
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856248"
---
# <a name="new-and-updated-cmdlets"></a>Yeni ve güncelleştirilmiş cmdlet'ler

Topluluk görüşlerine dayalı yeni ve güncelleştirilmiş mevcut cmdlet'ler ekledik.

## <a name="archive-cmdlets"></a>Arşiv cmdlet'leri

İki yeni cmdlet `Compress-Archive` ve `Expand-Archive`, let sıkıştırma ve ZIP dosyaları genişletin.

Daha fazla bilgi için [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) modülü belgeleri.

## <a name="catalog-cmdlets"></a>Katalog cmdlet'leri

Microsoft.PowerShell.Security modülünde iki yeni cmdlet eklendi.

- [Yeni FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Bu, oluşturmak ve Windows Katalog dosyaları doğrula.

## <a name="clipboard-cmdlets"></a>Pano cmdlet’leri

`Get-Clipboard` ve `Set-Clipboard` için ve bir Windows PowerShell oturumundan içerik aktarımı kolaylaştırır. Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listeler ve metin destekler.

Daha fazla bilgi için bkz.:

- [Get-Pano](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Pano Ayarla](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Şifreli ileti söz dizimi (CMS) cmdlet'leri

Şifreleme ve şifre çözme şifreli olarak iletileri tarafından belirtildiği gibi korumak için IETF standart biçimi kullanarak içeriğin şifreli ileti söz dizimi cmdlet'leri Destek [RFC5652](https://tools.ietf.org/html/rfc5652).

Burada içerik şifrelemek için kullanılan anahtarı, ortak anahtar şifrelemesi standart CMS şifreleme uygular ( *ortak anahtar*) ve içeriğin şifresini çözmek için kullanılan anahtarı ( *özel anahtarı*) ayrıdır.

Ortak anahtarınızı yaygın olarak paylaşılabilir ve hassas veriler değil. Ortak anahtar ile şifrelenmiş içerikler yalnızca özel anahtarı kullanarak çözülebilir. Daha fazla bilgi için [ortak anahtar şifrelemesi](https://en.wikipedia.org/wiki/Public-key_cryptography).

Daha fazla bilgi için bkz:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Koruma CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Korumasını CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

'Kod imzalama' veya 'Mail', şifreli veri şifreleme sertifikaları PowerShell olarak belirlenebilmesi için gibi bir benzersiz anahtar kullanımı (EKU) tanımlayıcı sertifikaları gerektirir. Sertifika Sağlayıcısı belge şifreleme sertifikaları görüntülemek için kullanabileceğiniz **DocumentEncryptionCert** dinamik parametresinin `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Dize içeriği yapılandırılmış nesnelerden çıkarma ve ayıklama

### <a name="convertfrom-string"></a>ConvertFrom-String

Yeni `ConvertFrom-String` cmdlet'i iki modu destekler:

- Ayrılmış basic ayrıştırma
- Otomatik örnek temelli ayrıştırma oluşturuldu

Varsayılan olarak, sınırlandırılmış ayrıştırma boşluk konumundaki giriş böler ve elde edilen gruplara özellik adlarını atar.

**UpdateTemplate** parametre sonuçları öğrenme algoritmasının şablon dosyasındaki bir yorumu kaydeder. Bu tek seferlik bir ücret (yavaş aşaması) işlem öğrenme sağlar. Çalışan `ConvertFrom-String` kodlanmış öğrenme algoritmasını içeren bir şablon ile neredeyse anında sunulmuştur.

Daha fazla bilgi için [ConvertFrom-dize](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` önce ve sonra örnekleri aramak için metin istediğiniz göndermenizi sağlar. Cmdlet metni otomatik olarak biçimlendirir.

Daha fazla bilgi için [dize dönüştürme](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>FileInfo nesnesi güncelleştirmeleri

Dosya sürümü bilgilerini, özellikle dosyasının nerede oluşturulmuştur durumlarda yanıltıcı. WMF 5.0 ekler yeni **FileVersionRaw** ve **ProductVersionRaw** betik özelliklerine **FileInfo** nesneleri.
Powershell.exe (PowerShell işlemin Kimliğini $pid olduğunu varsayarak) için görüntülenen özellikler şunlardır:

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` onaltılık biçimde metin veya ikili veri görüntülemenize olanak tanır.

Daha fazla bilgi için [biçimi onaltılık](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-childıtem öğesinin-Depth parametresi var

`Get-ChildItem` artık bir **derinliği** parametresi ile kullanmak için **Recurse** özyineleme sınırlamak için:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Sürüm aralıklarını (1.* vb.) bildirme için modüller desteği

Artık birleştirebilirsiniz **MinimumVersion** ve **MaximumVersion** belirli bir aralıkta modülünü içeri aktarın. Parametreleri de joker karakterleri destekler.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Birçok senaryo vardır burada üyedir benzersiz tanımlayıcısı. `New-GUID` Cmdlet'i yeni bir GUID oluşturmak için basit bir yol sağlar.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine parametresi

`Out-File`, `Add-Content`, ve `Set-Content` artık yeni bir sahip **NoNewline** çıktıdan sonra yeni bir satır atlar anahtarı. Örneğin:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

Olmadan **NoNewline** belirtilen her parça ayrı bir satırda olacaktır:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Geliştirilmiş öğe cmdlet'leri kullanarak simgesel bağlantılar ile etkileşim kurma

Öğe cmdlet ve birkaç ilgili cmdlet'lerini sembolik bağlantıları desteklemek için genişletilmiştir.

### <a name="symbolic-link-files"></a>Sembolik bağlantıyı dosyaları

Bu örnekte biz için $pshome\profile.ps1 bağlayan C:\Temp klasöründeki MySymLinkFile.txt adlı yeni bir sembolik bağlantı dosyası oluşturun. Üç örneğin hepsi aynı sonucu üretir.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Sembolik bağlantıyı dizinleri

Bu örnekte, MySymLinkDir $pshome klasöre bağlayan C:\Temp klasöründeki adlı yeni bir sembolik bağlantı dizini oluştururuz. Üç örneğin hepsi aynı sonucu üretir.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Sabit bağlantılar

Aynı birleşimlerini **yolu** ve **adı** yukarıda açıklanan şekilde izin verilir.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Dizin merkezleriyle

Aynı birleşimlerini **yolu** ve **adı** yukarıda açıklanan şekilde izin verilir.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-Childıtem

`Get-ChildItem` 'l' şimdi görüntüler **modu** sembolik bağlantıyı dosya veya dizin belirtmek için özelliği.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove öğesi

Sembolik bağlantılar kaldırma herhangi bir öğe türü kaldırma gibi çalışır.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Kullanım **zorla** dosyaları hedef dizin ve sembolik bağlantısını kaldırmak için parametre.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Bazen betiğinizde, geçici bir dosya oluşturmanız gerekir. Artık bunu `New-TemporaryFile` cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>PowerShell ile Ağ Anahtarı Yönetimi

WMF 5. 0'da, sunulan ağ anahtarı cmdlet'leri Windows Server 2012 R2 logo sertifikalı ağ anahtarları için anahtar ve sanal LAN (VLAN) temel Katman 2 ağ anahtarı bağlantı noktası yapılandırması uygulamanıza imkan sağlar. Bu cmdlet'leri kullanarak şunları yapabilirsiniz:

- Genel yapılandırma, aşağıdaki gibi geçin:
  - Kümesi konak adı
  - Set anahtar başlığı
  - Yapılandırma
  - Etkinleştirmek veya devre dışı özelliği

- VLAN yapılandırması:
  - Oluşturma veya VLAN'ı kaldırma
  - Etkinleştirmek veya VLAN devre dışı
  - VLAN listeleme
  - VLAN kolay adı ayarlayın

- Katman 2 bağlantı noktası yapılandırması:
  - Bağlantı noktalarını Listele
  - Etkinleştirmek veya devre dışı bağlantı noktaları
  - Küme bağlantı modları ve özellikleri
  - Ekleme veya VLAN santral veya numaralı bağlantı noktasında ilişkilendirin

Daha fazla bilgi için [NetworkSwitchManager](/powershell/module/networkswitchmanager/) belgeleri.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>OData uç noktası ile ODataUtils göre PowerShell cmdlet'leri oluşturma

ODataUtils modülü, PowerShell cmdlet'lerinden OData desteği REST uç noktalarını oluşturulmasını sağlar. Microsoft.PowerShell.ODataUtils Modülü aşağıdaki özellikleri içerir:

- Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.
- İstemci tarafı sayfalama desteği
- Kullanarak sunucu tarafı filtreleme Select parametresi
- Web isteği üst bilgileri için destek

Tarafından oluşturulan proxy cmdlet'leri `Export-ODataEndPointProxy` cmdlet'i üzerinde sunucu tarafı OData uç noktasından ek bilgi sağlamak **bilgi** akış.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

Aşağıdaki örnekte, biz en iyi ürün alınıyor ve Çıkışta yakalama `$infoStream` değişkeni.

Belirterek **IncludeTotalResponseCount** parametresi aldığımız toplam sayısını, tüm **ürün** kayıtları sunucu üzerinde kullanılabilir.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

İstemci tarafı sayfalama desteğini kullanarak toplu sunucudan kayıtları elde edebilirsiniz. Sunucudan ağ üzerinden büyük miktarda veri almalısınız istediğinizde yararlıdır.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Oluşturulan proxy cmdlet'leri Destek **seçin** istemci gereken kayıt özelliklerini almak için bir filtre olarak kullanılan parametre. Ağ üzerinden aktarılan veri miktarını azaltan sunucu üzerinde filtreleme gerçekleşir.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

`Export-ODataEndpointProxy` Cmdlet ve işlem tarafından oluşturulan proxy cmdlet'leri artık destek **üstbilgileri** parametresi. Üst bilgi, kanal OData uç noktası tarafından beklenen ek bilgiler için kullanılabilir.

Aşağıdaki örnekte, bir abonelik anahtarı içeren bir karma tablo için sağlanan **üstbilgileri** parametresi. Bu, kimlik doğrulaması için bir abonelik anahtarı görmeyi Hizmetleri için tipik bir örnektir.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
