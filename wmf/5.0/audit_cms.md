---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059007"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Şifreli ileti söz dizimi (CMS) cmdlet'leri

Şifreleme ve şifre çözme şifreli olarak iletileri tarafından belirtildiği gibi korumak için IETF standart biçimi kullanarak içeriğin şifreli ileti söz dizimi cmdlet'leri Destek [RFC5652](https://tools.ietf.org/html/rfc5652).

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

Standart CMS şifreleme anahtarları kullanıldığı içeriği şifrelemek için ortak anahtar şifrelemesi uygular ( *ortak anahtar*) ve içeriğin şifresini çözmek için kullanılan anahtarları ( *özel anahtarı*) ayrıdır.

Ortak anahtarınızı yaygın olarak paylaşılabilir ve hassas veriler değil. Herhangi bir içerik bu ortak anahtarıyla şifrelenir, yalnızca özel anahtarınızı çözebilir. Daha fazla bilgi için [ortak anahtar şifrelemesi](https://en.wikipedia.org/wiki/Public-key_cryptography).

PowerShell'de tanınması için veri şifreleme sertifikaları (gibi tanımlayıcıları 'Kod imzalama için', 'Şifrelenmiş posta') olarak belirlenebilmesi için benzersiz anahtar kullanımı tanımlayıcı (EKU) şifreleme sertifikaları gerektirir.

Belge şifreleme için iyi bir sertifika oluşturma örneği aşağıda verilmiştir:

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

Ardından şunu çalıştırın:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

Ve şimdi şifreleme ve şifre çözme içeriği:

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

Herhangi bir parametre türü **CMSMessageRecipient** tanımlayıcıları aşağıdaki biçimlerde destekler:
- Gerçek bir sertifika (olarak sertifika sağlayıcısından alınan)
- Yolu için sertifikayı içeren bir dosya
- Sertifikayı içeren bir dizin yolu
- (Sertifika deposunda aramak için kullanılan) sertifikanın parmak izi
- (Sertifika deposunda aramak için kullanılan) sertifikanın konu adı

Sertifika Sağlayıcısı belge şifreleme sertifikaları görüntülemek için kullanabileceğiniz **- DocumentEncryptionCert** dinamik parametre:

```powershell
dir -DocumentEncryptionCert
```
