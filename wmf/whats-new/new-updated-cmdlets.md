---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Yeni ve güncelleştirilmiş cmdlet'ler
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298646"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="64dfc-103">Yeni ve güncelleştirilmiş cmdlet'ler</span><span class="sxs-lookup"><span data-stu-id="64dfc-103">New and updated cmdlets</span></span>

<span data-ttu-id="64dfc-104">Topluluk görüşlerine dayalı yeni ve güncelleştirilmiş mevcut cmdlet'ler ekledik.</span><span class="sxs-lookup"><span data-stu-id="64dfc-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="64dfc-105">Arşiv cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="64dfc-105">Archive cmdlets</span></span>

<span data-ttu-id="64dfc-106">İki yeni cmdlet `Compress-Archive` ve `Expand-Archive`, let sıkıştırma ve ZIP dosyaları genişletin.</span><span class="sxs-lookup"><span data-stu-id="64dfc-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="64dfc-107">Daha fazla bilgi için [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) modülü belgeleri.</span><span class="sxs-lookup"><span data-stu-id="64dfc-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="64dfc-108">Katalog cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="64dfc-108">Catalog Cmdlets</span></span>

<span data-ttu-id="64dfc-109">Microsoft.PowerShell.Security modülünde iki yeni cmdlet eklendi.</span><span class="sxs-lookup"><span data-stu-id="64dfc-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="64dfc-110">Yeni FileCatalog</span><span class="sxs-lookup"><span data-stu-id="64dfc-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="64dfc-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="64dfc-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="64dfc-112">Bu, oluşturmak ve Windows Katalog dosyaları doğrula.</span><span class="sxs-lookup"><span data-stu-id="64dfc-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="64dfc-113">Pano cmdlet’leri</span><span class="sxs-lookup"><span data-stu-id="64dfc-113">Clipboard cmdlets</span></span>

<span data-ttu-id="64dfc-114">`Get-Clipboard` ve `Set-Clipboard` için ve bir Windows PowerShell oturumundan içerik aktarımı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="64dfc-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="64dfc-115">Pano cmdlet'leri görüntüleri, ses dosyaları, dosya listeler ve metin destekler.</span><span class="sxs-lookup"><span data-stu-id="64dfc-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="64dfc-116">Daha fazla bilgi için bkz.:</span><span class="sxs-lookup"><span data-stu-id="64dfc-116">For more information, see:</span></span>

- [<span data-ttu-id="64dfc-117">Get-Pano</span><span class="sxs-lookup"><span data-stu-id="64dfc-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="64dfc-118">Pano Ayarla</span><span class="sxs-lookup"><span data-stu-id="64dfc-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="64dfc-119">Şifreli ileti söz dizimi (CMS) cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="64dfc-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="64dfc-120">Şifreleme ve şifre çözme şifreli olarak iletileri tarafından belirtildiği gibi korumak için IETF standart biçimi kullanarak içeriğin şifreli ileti söz dizimi cmdlet'leri Destek [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="64dfc-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="64dfc-121">Burada içerik şifrelemek için kullanılan anahtarı, ortak anahtar şifrelemesi standart CMS şifreleme uygular ( *ortak anahtar*) ve içeriğin şifresini çözmek için kullanılan anahtarı ( *özel anahtarı*) ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="64dfc-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="64dfc-122">Ortak anahtarınızı yaygın olarak paylaşılabilir ve hassas veriler değil.</span><span class="sxs-lookup"><span data-stu-id="64dfc-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="64dfc-123">Ortak anahtar ile şifrelenmiş içerikler yalnızca özel anahtarı kullanarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="64dfc-124">Daha fazla bilgi için [ortak anahtar şifrelemesi](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="64dfc-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="64dfc-125">Daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="64dfc-125">For more information see:</span></span>

- [<span data-ttu-id="64dfc-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="64dfc-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="64dfc-127">Koruma CmsMessage</span><span class="sxs-lookup"><span data-stu-id="64dfc-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="64dfc-128">Korumasını CmsMessage</span><span class="sxs-lookup"><span data-stu-id="64dfc-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="64dfc-129">'Kod imzalama' veya 'Mail', şifreli veri şifreleme sertifikaları PowerShell olarak belirlenebilmesi için gibi bir benzersiz anahtar kullanımı (EKU) tanımlayıcı sertifikaları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="64dfc-130">Sertifika Sağlayıcısı belge şifreleme sertifikaları görüntülemek için kullanabileceğiniz **DocumentEncryptionCert** dinamik parametresinin `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="64dfc-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="64dfc-131">Dize içeriği yapılandırılmış nesnelerden çıkarma ve ayıklama</span><span class="sxs-lookup"><span data-stu-id="64dfc-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="64dfc-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="64dfc-132">ConvertFrom-String</span></span>

<span data-ttu-id="64dfc-133">Yeni `ConvertFrom-String` cmdlet'i iki modu destekler:</span><span class="sxs-lookup"><span data-stu-id="64dfc-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="64dfc-134">Ayrılmış basic ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="64dfc-134">Basic delimited parsing</span></span>
- <span data-ttu-id="64dfc-135">Otomatik örnek temelli ayrıştırma oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="64dfc-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="64dfc-136">Varsayılan olarak, sınırlandırılmış ayrıştırma boşluk konumundaki giriş böler ve elde edilen gruplara özellik adlarını atar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="64dfc-137">**UpdateTemplate** parametre sonuçları öğrenme algoritmasının şablon dosyasındaki bir yorumu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="64dfc-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="64dfc-138">Bu tek seferlik bir ücret (yavaş aşaması) işlem öğrenme sağlar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="64dfc-139">Çalışan `ConvertFrom-String` kodlanmış öğrenme algoritmasını içeren bir şablon ile neredeyse anında sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="64dfc-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="64dfc-140">Daha fazla bilgi için [ConvertFrom-dize](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="64dfc-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="64dfc-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="64dfc-141">Convert-String</span></span>

<span data-ttu-id="64dfc-142">`Convert-String` önce ve sonra örnekleri aramak için metin istediğiniz göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="64dfc-143">Cmdlet metni otomatik olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="64dfc-144">Daha fazla bilgi için [dize dönüştürme](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="64dfc-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="64dfc-145">FileInfo nesnesi güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="64dfc-145">Updates to FileInfo object</span></span>

<span data-ttu-id="64dfc-146">Dosya sürümü bilgilerini, özellikle dosyasının nerede oluşturulmuştur durumlarda yanıltıcı.</span><span class="sxs-lookup"><span data-stu-id="64dfc-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="64dfc-147">WMF 5.0 ekler yeni **FileVersionRaw** ve **ProductVersionRaw** betik özelliklerine **FileInfo** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="64dfc-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="64dfc-148">Powershell.exe (PowerShell işlemin Kimliğini $pid olduğunu varsayarak) için görüntülenen özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="64dfc-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="64dfc-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="64dfc-149">Format-Hex</span></span>

<span data-ttu-id="64dfc-150">`Format-Hex` onaltılık biçimde metin veya ikili veri görüntülemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="64dfc-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="64dfc-151">Daha fazla bilgi için [biçimi onaltılık](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="64dfc-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="64dfc-152">Get-childıtem öğesinin-Depth parametresi var</span><span class="sxs-lookup"><span data-stu-id="64dfc-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="64dfc-153">`Get-ChildItem` artık bir **derinliği** parametresi ile kullanmak için **Recurse** özyineleme sınırlamak için:</span><span class="sxs-lookup"><span data-stu-id="64dfc-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="64dfc-154">Sürüm aralıklarını (1.\* vb.) bildirme için modüller desteği</span><span class="sxs-lookup"><span data-stu-id="64dfc-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="64dfc-155">Artık birleştirebilirsiniz **MinimumVersion** ve **MaximumVersion** belirli bir aralıkta modülünü içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="64dfc-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="64dfc-156">Parametreleri de joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="64dfc-156">The parameters also support wildcards.</span></span>

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

## <a name="new-guid"></a><span data-ttu-id="64dfc-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="64dfc-157">New-Guid</span></span>

<span data-ttu-id="64dfc-158">Birçok senaryo vardır burada üyedir benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="64dfc-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="64dfc-159">`New-GUID` Cmdlet'i yeni bir GUID oluşturmak için basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="64dfc-160">NoNewLine parametresi</span><span class="sxs-lookup"><span data-stu-id="64dfc-160">NoNewLine parameter</span></span>

<span data-ttu-id="64dfc-161">`Out-File`, `Add-Content`, ve `Set-Content` artık yeni bir sahip **NoNewline** çıktıdan sonra yeni bir satır atlar anahtarı.</span><span class="sxs-lookup"><span data-stu-id="64dfc-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="64dfc-162">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="64dfc-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="64dfc-163">Olmadan **NoNewline** belirtilen her parça ayrı bir satırda olacaktır:</span><span class="sxs-lookup"><span data-stu-id="64dfc-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="64dfc-164">Geliştirilmiş öğe cmdlet'leri kullanarak simgesel bağlantılar ile etkileşim kurma</span><span class="sxs-lookup"><span data-stu-id="64dfc-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="64dfc-165">Öğe cmdlet ve birkaç ilgili cmdlet'lerini sembolik bağlantıları desteklemek için genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="64dfc-166">Sembolik bağlantıyı dosyaları</span><span class="sxs-lookup"><span data-stu-id="64dfc-166">Symbolic link files</span></span>

<span data-ttu-id="64dfc-167">Bu örnekte biz için $pshome\profile.ps1 bağlayan C:\Temp klasöründeki MySymLinkFile.txt adlı yeni bir sembolik bağlantı dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64dfc-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="64dfc-168">Üç örneğin hepsi aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="64dfc-169">Sembolik bağlantıyı dizinleri</span><span class="sxs-lookup"><span data-stu-id="64dfc-169">Symbolic link directories</span></span>

<span data-ttu-id="64dfc-170">Bu örnekte, MySymLinkDir $pshome klasöre bağlayan C:\Temp klasöründeki adlı yeni bir sembolik bağlantı dizini oluştururuz.</span><span class="sxs-lookup"><span data-stu-id="64dfc-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="64dfc-171">Üç örneğin hepsi aynı sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="64dfc-172">Sabit bağlantılar</span><span class="sxs-lookup"><span data-stu-id="64dfc-172">Hard links</span></span>

<span data-ttu-id="64dfc-173">Aynı birleşimlerini **yolu** ve **adı** yukarıda açıklanan şekilde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="64dfc-174">Dizin merkezleriyle</span><span class="sxs-lookup"><span data-stu-id="64dfc-174">Directory junctions</span></span>

<span data-ttu-id="64dfc-175">Aynı birleşimlerini **yolu** ve **adı** yukarıda açıklanan şekilde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="64dfc-176">Get-Childıtem</span><span class="sxs-lookup"><span data-stu-id="64dfc-176">Get-ChildItem</span></span>

<span data-ttu-id="64dfc-177">`Get-ChildItem` 'l' şimdi görüntüler **modu** sembolik bağlantıyı dosya veya dizin belirtmek için özelliği.</span><span class="sxs-lookup"><span data-stu-id="64dfc-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

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

### <a name="remove-item"></a><span data-ttu-id="64dfc-178">Remove öğesi</span><span class="sxs-lookup"><span data-stu-id="64dfc-178">Remove-Item</span></span>

<span data-ttu-id="64dfc-179">Sembolik bağlantılar kaldırma herhangi bir öğe türü kaldırma gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="64dfc-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="64dfc-180">Kullanım **zorla** dosyaları hedef dizin ve sembolik bağlantısını kaldırmak için parametre.</span><span class="sxs-lookup"><span data-stu-id="64dfc-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="64dfc-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="64dfc-181">New-TemporaryFile</span></span>

<span data-ttu-id="64dfc-182">Bazen betiğinizde, geçici bir dosya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="64dfc-183">Artık bunu `New-TemporaryFile` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="64dfc-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="64dfc-184">PowerShell ile Ağ Anahtarı Yönetimi</span><span class="sxs-lookup"><span data-stu-id="64dfc-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="64dfc-185">WMF 5. 0'da, sunulan ağ anahtarı cmdlet'leri Windows Server 2012 R2 logo sertifikalı ağ anahtarları için anahtar ve sanal LAN (VLAN) temel Katman 2 ağ anahtarı bağlantı noktası yapılandırması uygulamanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="64dfc-186">Bu cmdlet'leri kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="64dfc-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="64dfc-187">Genel yapılandırma, aşağıdaki gibi geçin:</span><span class="sxs-lookup"><span data-stu-id="64dfc-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="64dfc-188">Kümesi konak adı</span><span class="sxs-lookup"><span data-stu-id="64dfc-188">Set host name</span></span>
  - <span data-ttu-id="64dfc-189">Set anahtar başlığı</span><span class="sxs-lookup"><span data-stu-id="64dfc-189">Set switch banner</span></span>
  - <span data-ttu-id="64dfc-190">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="64dfc-190">Persist configuration</span></span>
  - <span data-ttu-id="64dfc-191">Etkinleştirmek veya devre dışı özelliği</span><span class="sxs-lookup"><span data-stu-id="64dfc-191">Enable or disable feature</span></span>

- <span data-ttu-id="64dfc-192">VLAN yapılandırması:</span><span class="sxs-lookup"><span data-stu-id="64dfc-192">VLAN configuration:</span></span>
  - <span data-ttu-id="64dfc-193">Oluşturma veya VLAN'ı kaldırma</span><span class="sxs-lookup"><span data-stu-id="64dfc-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="64dfc-194">Etkinleştirmek veya VLAN devre dışı</span><span class="sxs-lookup"><span data-stu-id="64dfc-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="64dfc-195">VLAN listeleme</span><span class="sxs-lookup"><span data-stu-id="64dfc-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="64dfc-196">VLAN kolay adı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="64dfc-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="64dfc-197">Katman 2 bağlantı noktası yapılandırması:</span><span class="sxs-lookup"><span data-stu-id="64dfc-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="64dfc-198">Bağlantı noktalarını Listele</span><span class="sxs-lookup"><span data-stu-id="64dfc-198">Enumerate ports</span></span>
  - <span data-ttu-id="64dfc-199">Etkinleştirmek veya devre dışı bağlantı noktaları</span><span class="sxs-lookup"><span data-stu-id="64dfc-199">Enable or disable ports</span></span>
  - <span data-ttu-id="64dfc-200">Küme bağlantı modları ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="64dfc-200">Set port modes and properties</span></span>
  - <span data-ttu-id="64dfc-201">Ekleme veya VLAN santral veya numaralı bağlantı noktasında ilişkilendirin</span><span class="sxs-lookup"><span data-stu-id="64dfc-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="64dfc-202">Daha fazla bilgi için [NetworkSwitchManager](/powershell/module/networkswitchmanager/) belgeleri.</span><span class="sxs-lookup"><span data-stu-id="64dfc-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="64dfc-203">OData uç noktası ile ODataUtils göre PowerShell cmdlet'leri oluşturma</span><span class="sxs-lookup"><span data-stu-id="64dfc-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="64dfc-204">ODataUtils modülü, PowerShell cmdlet'lerinden OData desteği REST uç noktalarını oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="64dfc-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="64dfc-205">Microsoft.PowerShell.ODataUtils Modülü aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="64dfc-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="64dfc-206">Sunucu tarafı uç noktasından ek bilgi için istemci tarafı kanal.</span><span class="sxs-lookup"><span data-stu-id="64dfc-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="64dfc-207">İstemci tarafı sayfalama desteği</span><span class="sxs-lookup"><span data-stu-id="64dfc-207">Client-side paging support</span></span>
- <span data-ttu-id="64dfc-208">Kullanarak sunucu tarafı filtreleme Select parametresi</span><span class="sxs-lookup"><span data-stu-id="64dfc-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="64dfc-209">Web isteği üst bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="64dfc-209">Support for web request headers</span></span>

<span data-ttu-id="64dfc-210">Tarafından oluşturulan proxy cmdlet'leri `Export-ODataEndPointProxy` cmdlet'i üzerinde sunucu tarafı OData uç noktasından ek bilgi sağlamak **bilgi** akış.</span><span class="sxs-lookup"><span data-stu-id="64dfc-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="64dfc-211">Aşağıdaki örnekte, biz en iyi ürün alınıyor ve Çıkışta yakalama `$infoStream` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="64dfc-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="64dfc-212">Belirterek **IncludeTotalResponseCount** parametresi aldığımız toplam sayısını, tüm **ürün** kayıtları sunucu üzerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="64dfc-213">İstemci tarafı sayfalama desteğini kullanarak toplu sunucudan kayıtları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64dfc-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="64dfc-214">Sunucudan ağ üzerinden büyük miktarda veri almalısınız istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="64dfc-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="64dfc-215">Oluşturulan proxy cmdlet'leri Destek **seçin** istemci gereken kayıt özelliklerini almak için bir filtre olarak kullanılan parametre.</span><span class="sxs-lookup"><span data-stu-id="64dfc-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="64dfc-216">Ağ üzerinden aktarılan veri miktarını azaltan sunucu üzerinde filtreleme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="64dfc-217">`Export-ODataEndpointProxy` Cmdlet ve işlem tarafından oluşturulan proxy cmdlet'leri artık destek **üstbilgileri** parametresi.</span><span class="sxs-lookup"><span data-stu-id="64dfc-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="64dfc-218">Üst bilgi, kanal OData uç noktası tarafından beklenen ek bilgiler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="64dfc-219">Aşağıdaki örnekte, bir abonelik anahtarı içeren bir karma tablo için sağlanan **üstbilgileri** parametresi.</span><span class="sxs-lookup"><span data-stu-id="64dfc-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="64dfc-220">Bu, kimlik doğrulaması için bir abonelik anahtarı görmeyi Hizmetleri için tipik bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="64dfc-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
