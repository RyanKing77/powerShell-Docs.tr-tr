---
title: VSCode ve PowerShell dosya kodlama anlama
description: VSCode ve PowerShell dosya kodlamasını yapılandırma
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251730"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="8d5c8-103">VSCode ve PowerShell dosya kodlama anlama</span><span class="sxs-lookup"><span data-stu-id="8d5c8-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="8d5c8-104">VS Code kullanarak oluşturma ve PowerShell betiklerini Düzenle, dosyalarınızın doğru karakter kodlama biçimi kullanılarak kaydedilir önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="8d5c8-105">Dosya kodlama ve neden önemli olduğu nedir?</span><span class="sxs-lookup"><span data-stu-id="8d5c8-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="8d5c8-106">VSCode karakterlerin arabellek içine bir insan girme dizeleri ve dosya sistemi bayt okuma/yazma blokları arasındaki arabirim yönetir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="8d5c8-107">VSCode bir dosyayı kaydederken, bir metin kodlama Bunu yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="8d5c8-108">PowerShell komut dosyası çalıştığında benzer şekilde, bunu bir dosyadaki bayt PowerShell programa dosyayı yeniden oluşturmak için karakter dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="8d5c8-109">VSCode dosyaya yazar ve PowerShell dosyasını okur olduğundan, bunlar aynı kodlama sistem kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="8d5c8-110">Bu işlem, bir PowerShell Betiği ayrıştırma gider: *bayt* -> *karakter* -> *belirteçleri*  ->   *soyut sözdizimi ağacını* -> *yürütme*.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="8d5c8-111">VSCode hem PowerShell mantıklı varsayılan kodlama yapılandırma ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="8d5c8-112">Bununla birlikte, PowerShell uygulamaları tarafından kullanılan varsayılan kodlamayı PowerShell Core (v6.x) sürümü değişti.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="8d5c8-113">VSCode içinde PowerShell veya PowerShell uzantısını kullanarak herhangi bir sorun olduğundan emin VSCode ve PowerShell ayarlarınızı yapılandırmak gereken doğru.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="8d5c8-114">Sorunları kodlama yaygın nedenleri</span><span class="sxs-lookup"><span data-stu-id="8d5c8-114">Common causes of encoding issues</span></span>

<span data-ttu-id="8d5c8-115">VSCode veya komut dosyanızı kodlama beklenen PowerShell kodlamasıyla eşleşmiyor kodlama sorunlar ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="8d5c8-116">Dosya kodlama otomatik olarak belirlemek PowerShell bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="8d5c8-117">Büyük olasılıkla içinde olmayan karakter kullanırken sorunları kodlamalı [7 bit ASCII karakter kümesi](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="8d5c8-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-118">For example:</span></span>

- <span data-ttu-id="8d5c8-119">Latin karakterler vurgulu (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="8d5c8-120">Cyrilice gibi latin olmayan karakterler (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="8d5c8-121">Han Çince (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="8d5c8-122">Kodlama sorunlarına yaygın nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="8d5c8-123">VSCode ve PowerShell için Kodlamalar kendi varsayılanlarından değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="8d5c8-124">Kodlama PowerShell 5.1 ve altında varsayılan Vscode'dan 's farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="8d5c8-125">Başka bir düzenleyicide açtığı ya da yeni bir kodlama dosyanın üzerine.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="8d5c8-126">Bu genellikle işe ile gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="8d5c8-127">Dosyayı farklı bir kodlama kaynak denetimine hangi VSCode ya da PowerShell bekliyor denetlenir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="8d5c8-128">Ortak Çalışanlar ile farklı kodlama yapılandırmaları düzenleyicileri kullandığınızda bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="8d5c8-129">Kodlama sorunlarına sahip olduğunuzda anlatma</span><span class="sxs-lookup"><span data-stu-id="8d5c8-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="8d5c8-130">Genellikle kodlama hatalarını kendilerini ayrıştırma hataları komut olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="8d5c8-131">Betiğinizde garip karakter sıraları fark ederseniz, bu sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="8d5c8-132">Bir tire aşağıdaki örnekte (`–`) karakterleriyle görünür `â€“`:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="8d5c8-133">Bu sorun oluşur VSCode karakter kodlar `–` UTF-8 bayt olarak `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="8d5c8-134">Bu bayt Windows-1252 çözülür, karakter olarak yorumlanır `â€“`.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="8d5c8-135">Görebileceğiniz bazı ilginç karakter sıraları içerir:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="8d5c8-136">`â€“` Onun yerine `–`</span><span class="sxs-lookup"><span data-stu-id="8d5c8-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="8d5c8-137">`â€”` Onun yerine `—`</span><span class="sxs-lookup"><span data-stu-id="8d5c8-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="8d5c8-138">`Ã„2` Onun yerine `Ä`</span><span class="sxs-lookup"><span data-stu-id="8d5c8-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="8d5c8-139">`Â` yerine ` ` (bölünemez boşluk)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="8d5c8-140">`Ã©` Onun yerine `é`</span><span class="sxs-lookup"><span data-stu-id="8d5c8-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="8d5c8-141">Bu kullanışlı [başvuru](https://www.i18nqa.com/debug/utf8-debug.html) UTF-8/Windows-1252 kodlama bir sorunu işaret eden ortak desenler listeler.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="8d5c8-142">VSCode PowerShell uzantı Kodlamalar ile nasıl etkileşim girer</span><span class="sxs-lookup"><span data-stu-id="8d5c8-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="8d5c8-143">PowerShell uzantısı solucanlar, betiklerde etkileşime geçer:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="8d5c8-144">VSCode içinde komut dosyaları düzenlenirken, içeriği uzantısı tarafından VSCode gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="8d5c8-145">[Dil sunucusu Protokolü][] gerektiren bu içerik UTF-8'de aktarılır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="8d5c8-146">Bu nedenle, uzantısı yanlış kodlama almak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="8d5c8-147">Doğrudan tümleşik konsolunda komut yürütüldüğünde dosyasından PowerShell tarafından doğrudan okurlar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="8d5c8-148">Tf PowerShell'in kodlama Vscode'dan 's farklıdır, bir şey burada yanlış gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-148">Tf PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="8d5c8-149">VSCode içinde açık olan bir betik VSCode içinde açık değil başka bir komut dosyası başvuruları, genişletme dosya sisteminden, betiğin içeriği yüklemek için geri döner.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="8d5c8-150">PowerShell uzantısı UTF-8 kodlaması için'varsayılan olarak, ancak kullandığı [bayt sırası işareti][], veya AĞACI, algılama doğru kodlama seçin.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="8d5c8-151">BOM daha az biçimlerini kodlama varsayılarak sorun oluşur (gibi [UTF-8][] hiçbir BOM ile ve [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="8d5c8-152">PowerShell uzantısı varsayılan UTF-8 olarak.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="8d5c8-153">Uzantı VSCode'nın kodlama ayarlarını değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="8d5c8-154">Daha fazla bilgi için [sorun #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="8d5c8-155">Doğru kodlamayı seçme</span><span class="sxs-lookup"><span data-stu-id="8d5c8-155">Choosing the right encoding</span></span>

<span data-ttu-id="8d5c8-156">Farklı sistemler ve uygulamalar farklı kodlamaları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="8d5c8-157">.NET Standard'da web üzerinde ve Linux dünyada, UTF-8 baskın encoding'i şimdi içindir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="8d5c8-158">Çoğu .NET Framework uygulamaları [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="8d5c8-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="8d5c8-159">Geçmiş nedeniyle buna bazen "Unicode" adı verilir, artık bir dönem için bir geniş başvuruyor [standart](https://en.wikipedia.org/wiki/Unicode) hem UTF-8 ve UTF-16 içerir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="8d5c8-160">Windows üzerinde Unicode geçerler birçok yerel uygulamalar varsayılan olarak Windows-1252 kullanmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="8d5c8-161">Unicode kodlamaları de (BOM) işaretlemek bayt sırası kavramı vardır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="8d5c8-162">Hangi kodlama metnini kullanarak bir kod çözücü bildirmek için metin başında ağaçları oluşur.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="8d5c8-163">Çok baytlı kodlamaları için ayrıca ürün reçetesi gösterir [endianness](https://en.wikipedia.org/wiki/Endianness) kodlaması.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="8d5c8-164">Ağaçları, bir ürün reçetesi mevcut olduğunda Unicode metin olduğunu makul bir tahmin izin vererek Unicode olmayan metinde nadiren gerçekleşen bayt olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="8d5c8-165">Ağaçları isteğe bağlıdır ve güvenilir bir kuralı UTF-8'in her yerde kullanılan Linux dünyada yaygın olarak kullanıcıların benimseme değildir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="8d5c8-166">Çoğu Linux uygulamaları, metin girişi UTF-8 olarak kodlanmış olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="8d5c8-167">Çok sayıda Linux uygulamaları tanıması ve doğru bir şekilde bir BOM işlemek bir sayı yoktur, bu uygulamalarla yönetilen metin yapılara önde gelen.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="8d5c8-168">**Bu nedenle**:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-168">**Therefore**:</span></span>

- <span data-ttu-id="8d5c8-169">Öncelikle Windows uygulamaları ve Windows PowerShell ile çalışıyorsanız, UTF-16 ya da BOM ile UTF-8 gibi bir kodlama tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="8d5c8-170">Platformlar arası çalışması, BOM ile UTF-8 tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="8d5c8-171">Ağırlıklı olarak Linux ilişkili bağlamlarda işe, UTF-8 içermeyen ürün reçetesi tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="8d5c8-172">Mümkünse kaçınmalısınız temelde eski Kodlamalar şunlardır: Windows-1252 ve latin-1.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="8d5c8-173">Ancak, bazı eski Windows uygulamaları bunlara bağımlı.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="8d5c8-174">Ayrıca kod imzalama olduğunu hatalarının ayıklanabileceğini belirtmekte yarar [kodlama bağımlı](https://github.com/PowerShell/PowerShell/issues/3466), imzalı bir komut kodlama değişikliği anlamı gerektirecek teslim.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="8d5c8-175">VSCode yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d5c8-175">Configuring VSCode</span></span>

<span data-ttu-id="8d5c8-176">VSCode'nın varsayılan kodlama: UTF-8 içermeyen ürün reçetesi.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="8d5c8-177">Ayarlanacak [VSCode'nın kodlama][]VSCode Ayarları'na gidin (<kbd>Ctrl<kbd>+</kbd>,</kbd>) ayarlayıp `"files.encoding"` ayarı:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="8d5c8-178">Bazı olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-178">Some possible values are:</span></span>

- <span data-ttu-id="8d5c8-179">`utf8`: [UTF-8] içermeyen ürün reçetesi</span><span class="sxs-lookup"><span data-stu-id="8d5c8-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="8d5c8-180">`utf8bom`: [UTF-8] BOM ile</span><span class="sxs-lookup"><span data-stu-id="8d5c8-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="8d5c8-181">`utf16le`: Küçük endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="8d5c8-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="8d5c8-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="8d5c8-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="8d5c8-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="8d5c8-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="8d5c8-184">Bunun için bir açılan GUI Görünümü'nde almalısınız veya onun için tamamlamalar json'da görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="8d5c8-185">Ayrıca, mümkün olduğunda kodlamasını otomatik algıla için aşağıdakileri ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="8d5c8-186">Bu ayarlar, tüm dosya türlerini etkilemesini istemiyorsanız VSCode dil başına yapılandırmaları da sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="8d5c8-187">Ayarları koyarak bir dile özgü ayarı oluşturarak bir `[<language-name>]` alan.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="8d5c8-188">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="8d5c8-189">PowerShell yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8d5c8-189">Configuring PowerShell</span></span>

<span data-ttu-id="8d5c8-190">PowerShell'in varsayılan kodlamayı sürümüne göre farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="8d5c8-191">PowerShell 6 +, kodlama varsayılan UTF-8 içermeyen ürün reçetesi tüm platformlarda kodlamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="8d5c8-192">Windows PowerShell'de varsayılan kodlamayı genellikle Windows-1252'ın bir uzantısı olan [latin-1][], ISO 8859-1 olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="8d5c8-193">PowerShell'de 5 + varsayılan bu kodlamanızın bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="8d5c8-194">Aşağıdaki [betik](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) ne kodlama PowerShell oturumunuzda bir komut dosyası içermeyen bir ürün reçetesi çıkarsar belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="8d5c8-195">PowerShell bir verilen daha genel profil ayarları kullanarak kodlama kullanmak için yapılandırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="8d5c8-196">Aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-196">See the following articles:</span></span>

- <span data-ttu-id="8d5c8-197">[@mklement0]ın [PowerShell StackOverflow kodlama hakkında yanıt](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="8d5c8-198">[@rkeithhill]ın [PowerShell BOM daha az UTF-8 girişinde uğraşmanızı hakkındaki blog gönderisini](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="8d5c8-199">Belirli bir giriş kodlama kullanmak için PowerShell kullanmaya zorlamak mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="8d5c8-200">PowerShell 5.1 ve varsayılan Windows-1252 hiçbir BOM olmadığında kodlama için aşağıda.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="8d5c8-201">Birlikte çalışabilirlik nedeniyle, bir Unicode biçiminde bir BOM ile komut dosyaları kaydetmek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d5c8-202">Diğer araçlardan PowerShell betikleri kodlama seçimlerinizi tarafından etkilenebilecek veya başka bir kodlama için komut dosyalarınızı yeniden kodlamak dokunma sahip.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="8d5c8-203">Var olan betikler</span><span class="sxs-lookup"><span data-stu-id="8d5c8-203">Existing scripts</span></span>

<span data-ttu-id="8d5c8-204">Zaten dosya sisteminde betikleri, yeni seçilen kodlama için yeniden kodlanmış gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="8d5c8-205">Alt çubuğu, VSCode içinde UTF-8 etiket görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="8d5c8-206">Eylem çubuğunu açın ve seçmek için tıklatın **kodlamayla kaydetme**.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="8d5c8-207">Şimdi, bu dosya için yeni bir kodlama seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="8d5c8-208">Bkz: [VSCode'nın kodlama][] tam yönergeler için.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="8d5c8-209">Birden çok dosyayı yeniden kodlamanız gerekirse, aşağıdaki betiği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="8d5c8-210">PowerShell Tümleşik komut dosyası ortamı (ISE)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="8d5c8-211">PowerShell ISE kullanarak komut dosyalarını da düzenlerseniz, kodlama ayarlarını eşitlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="8d5c8-212">ISE bir BOM uymanız, ancak aynı zamanda yansıma için kullanılacak olası [kümesi kodlaması](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="8d5c8-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="8d5c8-213">Bu yeni işletmeler arasında kalıcı olmasını mıydı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="8d5c8-214">Kaynak Denetim yazılımı</span><span class="sxs-lookup"><span data-stu-id="8d5c8-214">Source control software</span></span>

<span data-ttu-id="8d5c8-215">Bazı, git gibi kaynak denetimi araçları Kodlamalar yoksayın; Git, yalnızca bayt izler.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="8d5c8-216">Diğer TFS veya Mercurial, gibi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="8d5c8-217">Hatta bazı git tabanlı araçlar, metin, kod çözme hakkında kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="8d5c8-218">Bu durum söz konusu olduğunda emin olun:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="8d5c8-219">Metin kodlaması kaynak denetiminizi VSCode yapılandırmanızla eşleşecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="8d5c8-220">Tüm dosyaları kaynak denetimine ilgili kodlamada seçildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="8d5c8-221">Kaynak denetimi alınan kodlama için değişiklikleri dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="8d5c8-222">Bir anahtar bu değişiklikler, ancak burada bir şey (bayta sahiptir ancak karakter olmayan çünkü) değiştirilmiş gibi görünüyor belirten bir fark işaretidir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="8d5c8-223">Ortak Çalışanlar ortamları</span><span class="sxs-lookup"><span data-stu-id="8d5c8-223">Collaborators' environments</span></span>

<span data-ttu-id="8d5c8-224">Kaynak denetimini yapılandırma üzerinde herhangi bir dosya paylaşımını şirket, çalışanlar, PowerShell dosyaları yeniden kodlayarak kodlama geçersiz kılma ayarları olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="8d5c8-225">Diğer programları</span><span class="sxs-lookup"><span data-stu-id="8d5c8-225">Other programs</span></span>

<span data-ttu-id="8d5c8-226">Diğer program okuyan veya yazan bir PowerShell Betiği yeniden kodlayın.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="8d5c8-227">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-227">Some examples are:</span></span>

- <span data-ttu-id="8d5c8-228">Bir betiği kopyalayıp Pano'yu kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="8d5c8-229">Bu gibi senaryolarda yaygındır:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="8d5c8-230">Bir betiği bir VM'ye kopyalama</span><span class="sxs-lookup"><span data-stu-id="8d5c8-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="8d5c8-231">Bir e-posta veya Web sayfası dışında bir komut dosyası kopyalanıyor</span><span class="sxs-lookup"><span data-stu-id="8d5c8-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="8d5c8-232">Bir komut dosyası içine veya dışına Microsoft Word veya PowerPoint belge kopyalama</span><span class="sxs-lookup"><span data-stu-id="8d5c8-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="8d5c8-233">Başka bir metin düzenleyicisi gibi:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="8d5c8-234">Not Defteri</span><span class="sxs-lookup"><span data-stu-id="8d5c8-234">Notepad</span></span>
  - <span data-ttu-id="8d5c8-235">vim</span><span class="sxs-lookup"><span data-stu-id="8d5c8-235">vim</span></span>
  - <span data-ttu-id="8d5c8-236">Diğer bir PowerShell komut dosyası Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="8d5c8-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="8d5c8-237">Gibi yardımcı programlar, düzenleme metni:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="8d5c8-238">PowerShell yönlendirme işleçlerini ister `>` ve `>>`</span><span class="sxs-lookup"><span data-stu-id="8d5c8-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="8d5c8-239">Aktarım programları gibi dosya:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="8d5c8-240">Komut dosyaları indirirken bir web tarayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d5c8-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="8d5c8-241">Bir dosya paylaşımı</span><span class="sxs-lookup"><span data-stu-id="8d5c8-241">A file share</span></span>

<span data-ttu-id="8d5c8-242">Bu araçlardan bazılarını ilgilenmenize metin yerine bayt, ancak diğerleri kodlama yapılandırmaları sunar.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="8d5c8-243">Bir kodlama yapılandırmak için gerek duyduğunuz Böyle durumlarda, bu sorunları önlemek için kodlama düzenleyiciniz aynı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d5c8-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="8d5c8-244">PowerShell'de kodlama diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="8d5c8-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="8d5c8-245">Okuma olan kodlama ve kodlama PowerShell'de yapılandırma birkaç diğer iyi gönderileri vardır:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="8d5c8-246">[@mklement0]ın [PowerShell StackOverflow kodlama özeti](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="8d5c8-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="8d5c8-247">Önceki sorunları, sorunlar kodlaması için vscode-PowerShell açıldı:</span><span class="sxs-lookup"><span data-stu-id="8d5c8-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="8d5c8-248">#1308</span><span class="sxs-lookup"><span data-stu-id="8d5c8-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="8d5c8-249">#1628</span><span class="sxs-lookup"><span data-stu-id="8d5c8-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="8d5c8-250">#1680</span><span class="sxs-lookup"><span data-stu-id="8d5c8-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="8d5c8-251">#1744</span><span class="sxs-lookup"><span data-stu-id="8d5c8-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="8d5c8-252">#1751</span><span class="sxs-lookup"><span data-stu-id="8d5c8-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="8d5c8-253">Klasik *Joel yazılım* Unicode hakkında Düzenle</span><span class="sxs-lookup"><span data-stu-id="8d5c8-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="8d5c8-254">.NET Standard'da kodlama</span><span class="sxs-lookup"><span data-stu-id="8d5c8-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[bayt sırası işareti]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Dil sunucusu Protokolü]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode'nın kodlama]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support