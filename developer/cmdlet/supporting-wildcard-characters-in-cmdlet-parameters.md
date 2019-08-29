---
title: Cmdlet Parametrelerinde Joker Karakteri Destekleme
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104455"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="1141d-102">Cmdlet Parametrelerinde Joker Karakteri Destekleme</span><span class="sxs-lookup"><span data-stu-id="1141d-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="1141d-103">Genellikle, tek bir kaynağa karşı değil, bir grup kaynağa karşı çalışacak bir cmdlet tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1141d-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="1141d-104">Örneğin, bir cmdlet 'in aynı ada veya uzantıya sahip bir veri deposundaki tüm dosyaları bulması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1141d-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="1141d-105">Bir kaynak grubuna karşı çalıştırılacak bir cmdlet tasarlarken joker karakter desteği sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1141d-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="1141d-106">Joker karakter kullanmak bazen *Glob*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1141d-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="1141d-107">Joker karakterler kullanan Windows PowerShell cmdlet 'Leri</span><span class="sxs-lookup"><span data-stu-id="1141d-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="1141d-108">Birçok Windows PowerShell cmdlet 'i parametre değerleri için joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1141d-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="1141d-109">Örneğin, bir `Name` veya `Path` parametresi olan neredeyse her cmdlet bu parametreler için joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1141d-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="1141d-110">(Bir `Path` parametresi olan çoğu cmdlet 'in de joker karakterleri desteklemeyen `LiteralPath` bir parametresi olsa da). Aşağıdaki komut, geçerli oturumdaki adı Get fiilini içeren tüm cmdlet 'leri döndürmek için bir joker karakterin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1141d-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="1141d-111">Desteklenen joker karakterler</span><span class="sxs-lookup"><span data-stu-id="1141d-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="1141d-112">Windows PowerShell aşağıdaki joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1141d-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="1141d-113">Liyorsa</span><span class="sxs-lookup"><span data-stu-id="1141d-113">Wildcard</span></span> |                             <span data-ttu-id="1141d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1141d-114">Description</span></span>                             |  <span data-ttu-id="1141d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1141d-115">Example</span></span>   |     <span data-ttu-id="1141d-116">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="1141d-116">Matches</span></span>      | <span data-ttu-id="1141d-117">Eşleşmez</span><span class="sxs-lookup"><span data-stu-id="1141d-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="1141d-118">Belirtilen konumdan başlayarak sıfır veya daha fazla karakterle eşleşir</span><span class="sxs-lookup"><span data-stu-id="1141d-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="1141d-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="1141d-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="1141d-120">?</span><span class="sxs-lookup"><span data-stu-id="1141d-120">?</span></span>        | <span data-ttu-id="1141d-121">Belirtilen konumdaki herhangi bir karakterle eşleşir</span><span class="sxs-lookup"><span data-stu-id="1141d-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="1141d-122">Bir, üzerinde,</span><span class="sxs-lookup"><span data-stu-id="1141d-122">An, in, on</span></span>       | <span data-ttu-id="1141d-123">Çalıştır</span><span class="sxs-lookup"><span data-stu-id="1141d-123">ran</span></span>            |
| <span data-ttu-id="1141d-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="1141d-124">[ ]</span></span>      | <span data-ttu-id="1141d-125">Bir karakter aralığıyla eşleşir</span><span class="sxs-lookup"><span data-stu-id="1141d-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="1141d-126">kitap, Cook, görünüm</span><span class="sxs-lookup"><span data-stu-id="1141d-126">book, cook, look</span></span> | <span data-ttu-id="1141d-127">Nook, gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="1141d-127">nook, took</span></span>     |
| <span data-ttu-id="1141d-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="1141d-128">[ ]</span></span>      | <span data-ttu-id="1141d-129">Belirtilen karakterlerle eşleşir</span><span class="sxs-lookup"><span data-stu-id="1141d-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="1141d-130">kitap, Nook</span><span class="sxs-lookup"><span data-stu-id="1141d-130">book, nook</span></span>       | <span data-ttu-id="1141d-131">Cook, Look</span><span class="sxs-lookup"><span data-stu-id="1141d-131">cook, look</span></span>     |

<span data-ttu-id="1141d-132">Joker karakterleri destekleyen cmdlet 'leri tasarladığınızda, joker karakter bileşimleri için izin verin.</span><span class="sxs-lookup"><span data-stu-id="1141d-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="1141d-133">Örneğin, aşağıdaki komut, c:\techdocs `Get-ChildItem` klasöründe olan ve "a"-"l" harfleriyle başlayan tüm. txt dosyalarını almak için cmdlet 'ini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1141d-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="1141d-134">Önceki komut, "a"- `[a-l]` "l" karakterleriyle başlaması gerektiğini belirtmek için Aralık joker karakterini kullanır ve `*` joker karakteri, dosya adının ilk harfi ve **. txt** uzantısı.</span><span class="sxs-lookup"><span data-stu-id="1141d-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="1141d-135">Aşağıdaki örnek, "d" harfini dışlayan, ancak "a" ile "f" arasındaki diğer tüm harfleri içeren bir Aralık joker karakter modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1141d-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="1141d-136">Joker karakter desenlerinde değişmez karakterleri işleme</span><span class="sxs-lookup"><span data-stu-id="1141d-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="1141d-137">Belirttiğiniz joker karakter deseninin joker karakter olarak yorumlanmamalıdır sabit karakterler içeriyorsa, bir kaçış karakteri olarak backtick karakterini (`` ` ``) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1141d-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="1141d-138">PowerShell API 'sinin tamsayı karakterlerini belirttiğinizde, tek bir geri nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="1141d-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="1141d-139">PowerShell komut isteminde sabit karakterler belirttiğinizde, iki geri ölçü kullanın.</span><span class="sxs-lookup"><span data-stu-id="1141d-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="1141d-140">Örneğin, aşağıdaki model, tam anlamıyla alınması gereken iki köşeli ayraç içerir.</span><span class="sxs-lookup"><span data-stu-id="1141d-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="1141d-141">PowerShell API 'sinde kullanıldığında şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1141d-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="1141d-142">"John Smith \`[\* ']"</span><span class="sxs-lookup"><span data-stu-id="1141d-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="1141d-143">PowerShell komut isteminden kullanıldığında:</span><span class="sxs-lookup"><span data-stu-id="1141d-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="1141d-144">"John Smith \` \`[\*\`']"</span><span class="sxs-lookup"><span data-stu-id="1141d-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="1141d-145">Bu kalıp "John Smith [Marketing]" veya "John Smith [Development]" ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1141d-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="1141d-146">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1141d-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="1141d-147">Cmdlet çıktısı ve joker karakterler</span><span class="sxs-lookup"><span data-stu-id="1141d-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="1141d-148">Cmdlet parametreleri joker karakterleri destekledikleri zaman, işlem genellikle bir dizi çıktısı üretir.</span><span class="sxs-lookup"><span data-stu-id="1141d-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="1141d-149">Bazen, Kullanıcı yalnızca tek bir öğe kullanabileceğinden, bir dizi çıkışını desteklemeye yönelik bir fikir vermez.</span><span class="sxs-lookup"><span data-stu-id="1141d-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="1141d-150">Örneğin, `Set-Location` Kullanıcı yalnızca tek bir konum ayarlamadığı için cmdlet dizi çıkışını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1141d-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="1141d-151">Bu örnekte, cmdlet joker karakterleri hala destekliyor, ancak çözümü tek bir konuma zorlar.</span><span class="sxs-lookup"><span data-stu-id="1141d-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="1141d-152">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1141d-152">See Also</span></span>

[<span data-ttu-id="1141d-153">Windows PowerShell cmdlet 'ı yazma</span><span class="sxs-lookup"><span data-stu-id="1141d-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1141d-154">Yada CardModel sınıfı</span><span class="sxs-lookup"><span data-stu-id="1141d-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
