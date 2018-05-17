---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Şifreleme iletisi söz dizimi (CMS) cmdlet'leri

Şifreleme iletisi söz dizimi cmdlet'leri şifreleme ve şifre çözme içeriğin şifreli olarak iletileri tarafından belgelenen şekilde korumak için IETF standart biçimi kullanarak destek [RFC5652](https://tools.ietf.org/html/rfc5652).

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

Standart CMS şifreleme anahtarları kullanıldığı içerik şifrelemek için ortak anahtar şifrelemesi uygulayan ( *ortak anahtar*) ve içeriğin şifresini çözmek için kullanılan anahtarları ( *özel anahtarı*) ayrıdır.

Ortak anahtarınız yaygın paylaşılabilir ve hassas verileri değil. Yalnızca özel anahtarınızı herhangi bir içerik bu ortak anahtarla şifrelenmiş çözebilir. Daha fazla bilgi için bkz: [ortak anahtar şifrelemesini](https://en.wikipedia.org/wiki/Public-key_cryptography).

PowerShell'de tanınması için veri şifreleme sertifikaları (ör. 'Kod imzalama için', 'Şifrelenmiş posta' tanımlayıcılar) olarak tanımak için bir benzersiz anahtar kullanımı tanımlayıcısı (EKU) şifreleme sertifikaları gerektirir.

Belge şifreleme için iyi bir sertifika oluşturma örnek aşağıda verilmiştir:

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

Ve şimdi şifrelemek ve içeriğin şifresini:

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
- Gerçek bir sertifika (olarak sertifika Sağlayıcısı'ndan alınan)
- Yol için bir sertifikayı içeren dosyayı
- Sertifikayı içeren bir dizin yolu
- (Sertifika deposunda aramak için kullanılan) sertifikanın parmak izi
- (Sertifika deposunda aramak için kullanılan) sertifikanın konu adı

Belge Şifreleme sertifikaları sertifika sağlayıcısında görüntülemek için kullanabileceğiniz **- DocumentEncryptionCert** dinamik parametre:

```powershell
dir -DocumentEncryptionCert
```
