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
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="4fea7-102">Şifreli ileti söz dizimi (CMS) cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="4fea7-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="4fea7-103">Şifreleme ve şifre çözme şifreli olarak iletileri tarafından belirtildiği gibi korumak için IETF standart biçimi kullanarak içeriğin şifreli ileti söz dizimi cmdlet'leri Destek [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="4fea7-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

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

<span data-ttu-id="4fea7-104">Standart CMS şifreleme anahtarları kullanıldığı içeriği şifrelemek için ortak anahtar şifrelemesi uygular ( *ortak anahtar*) ve içeriğin şifresini çözmek için kullanılan anahtarları ( *özel anahtarı*) ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="4fea7-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="4fea7-105">Ortak anahtarınızı yaygın olarak paylaşılabilir ve hassas veriler değil.</span><span class="sxs-lookup"><span data-stu-id="4fea7-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="4fea7-106">Herhangi bir içerik bu ortak anahtarıyla şifrelenir, yalnızca özel anahtarınızı çözebilir.</span><span class="sxs-lookup"><span data-stu-id="4fea7-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="4fea7-107">Daha fazla bilgi için [ortak anahtar şifrelemesi](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="4fea7-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="4fea7-108">PowerShell'de tanınması için veri şifreleme sertifikaları (gibi tanımlayıcıları 'Kod imzalama için', 'Şifrelenmiş posta') olarak belirlenebilmesi için benzersiz anahtar kullanımı tanımlayıcı (EKU) şifreleme sertifikaları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fea7-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="4fea7-109">Belge şifreleme için iyi bir sertifika oluşturma örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4fea7-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

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

<span data-ttu-id="4fea7-110">Ardından şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4fea7-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="4fea7-111">Ve şimdi şifreleme ve şifre çözme içeriği:</span><span class="sxs-lookup"><span data-stu-id="4fea7-111">And you can now encrypt and decrypt content:</span></span>

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

<span data-ttu-id="4fea7-112">Herhangi bir parametre türü **CMSMessageRecipient** tanımlayıcıları aşağıdaki biçimlerde destekler:</span><span class="sxs-lookup"><span data-stu-id="4fea7-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="4fea7-113">Gerçek bir sertifika (olarak sertifika sağlayıcısından alınan)</span><span class="sxs-lookup"><span data-stu-id="4fea7-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="4fea7-114">Yolu için sertifikayı içeren bir dosya</span><span class="sxs-lookup"><span data-stu-id="4fea7-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="4fea7-115">Sertifikayı içeren bir dizin yolu</span><span class="sxs-lookup"><span data-stu-id="4fea7-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="4fea7-116">(Sertifika deposunda aramak için kullanılan) sertifikanın parmak izi</span><span class="sxs-lookup"><span data-stu-id="4fea7-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="4fea7-117">(Sertifika deposunda aramak için kullanılan) sertifikanın konu adı</span><span class="sxs-lookup"><span data-stu-id="4fea7-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="4fea7-118">Sertifika Sağlayıcısı belge şifreleme sertifikaları görüntülemek için kullanabileceğiniz **- DocumentEncryptionCert** dinamik parametre:</span><span class="sxs-lookup"><span data-stu-id="4fea7-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```
