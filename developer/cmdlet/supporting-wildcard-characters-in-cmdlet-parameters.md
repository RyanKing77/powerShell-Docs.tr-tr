---
title: Cmdlet parametreleri joker karakterleri destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851376"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="d9701-102">Cmdlet Parametrelerinde Joker Karakteri Destekleme</span><span class="sxs-lookup"><span data-stu-id="d9701-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="d9701-103">Genellikle, kaynakların bir gruba göre yerine tek bir kaynak karşı çalıştırmak için bir cmdlet tasarım gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d9701-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="d9701-104">Örneğin, bir cmdlet tüm dosyaları uzantı ve aynı ada sahip bir veri deposunda bulun gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d9701-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="d9701-105">Bir kaynak grubu üzerinde çalıştırılacak bir cmdlet tasarlarken joker karakterleri için destek sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d9701-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="d9701-106">Joker karakterler kullanarak bazen olarak adlandırılır *Glob*.</span><span class="sxs-lookup"><span data-stu-id="d9701-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="d9701-107">Joker karakter Windows PowerShell cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="d9701-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="d9701-108">Birçok Windows PowerShell cmdlet'leri için parametre değerleri joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d9701-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="d9701-109">Örneğin, neredeyse her cmdlet'i olan bir `Name` veya `Path` parametresi bu parametreler için joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d9701-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="d9701-110">(Çoğu cmdlet olsa bir `Path` parametresi de bir `LiteralPath` parametresi joker karakterleri desteklemiyor.) Aşağıdaki komut, bir joker karakter tüm cmdlet'lerinin adında Get fiili içeren geçerli oturumda döndürmek için nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9701-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="d9701-111">**PS > get-command get -\***</span><span class="sxs-lookup"><span data-stu-id="d9701-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="d9701-112">Desteklenen joker karakterler</span><span class="sxs-lookup"><span data-stu-id="d9701-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="d9701-113">Windows PowerShell, joker karakterleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d9701-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="d9701-114">joker karakter</span><span class="sxs-lookup"><span data-stu-id="d9701-114">Wildcard character</span></span>|<span data-ttu-id="d9701-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9701-115">Description</span></span>|<span data-ttu-id="d9701-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9701-116">Example</span></span>|<span data-ttu-id="d9701-117">Eşleşmeler</span><span class="sxs-lookup"><span data-stu-id="d9701-117">Matches</span></span>|<span data-ttu-id="d9701-118">Eşleşmez</span><span class="sxs-lookup"><span data-stu-id="d9701-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="d9701-119">Belirtilen konumdan başlayarak, sıfır veya daha fazla karakter ile eşleşir</span><span class="sxs-lookup"><span data-stu-id="d9701-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="d9701-120">a\*</span><span class="sxs-lookup"><span data-stu-id="d9701-120">a\*</span></span>|<span data-ttu-id="d9701-121">Apple ag</span><span class="sxs-lookup"><span data-stu-id="d9701-121">A, ag, Apple</span></span>||
|<span data-ttu-id="d9701-122">?</span><span class="sxs-lookup"><span data-stu-id="d9701-122">?</span></span>|<span data-ttu-id="d9701-123">Belirli bir konumda eşleşen anycharacter</span><span class="sxs-lookup"><span data-stu-id="d9701-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="d9701-124">? n</span><span class="sxs-lookup"><span data-stu-id="d9701-124">?n</span></span>|<span data-ttu-id="d9701-125">Bir içinde üzerinde</span><span class="sxs-lookup"><span data-stu-id="d9701-125">An, in, on</span></span>|<span data-ttu-id="d9701-126">çalıştı</span><span class="sxs-lookup"><span data-stu-id="d9701-126">ran</span></span>|
|<span data-ttu-id="d9701-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="d9701-127">[ ]</span></span>|<span data-ttu-id="d9701-128">Bir dizi karakter ile eşleşir</span><span class="sxs-lookup"><span data-stu-id="d9701-128">Matches a range of characters</span></span>|<span data-ttu-id="d9701-129">[a-l] ook</span><span class="sxs-lookup"><span data-stu-id="d9701-129">[a-l]ook</span></span>|<span data-ttu-id="d9701-130">kitap, cook, Görünüm</span><span class="sxs-lookup"><span data-stu-id="d9701-130">book, cook, look</span></span>|<span data-ttu-id="d9701-131">sürdü</span><span class="sxs-lookup"><span data-stu-id="d9701-131">took</span></span>|
|<span data-ttu-id="d9701-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="d9701-132">[ ]</span></span>|<span data-ttu-id="d9701-133">Belirtilen karakter ile eşleşir</span><span class="sxs-lookup"><span data-stu-id="d9701-133">Matches the specified characters</span></span>|<span data-ttu-id="d9701-134">[bc] ook</span><span class="sxs-lookup"><span data-stu-id="d9701-134">[bc]ook</span></span>|<span data-ttu-id="d9701-135">kitap, cook</span><span class="sxs-lookup"><span data-stu-id="d9701-135">book, cook</span></span>|<span data-ttu-id="d9701-136">Ara</span><span class="sxs-lookup"><span data-stu-id="d9701-136">look</span></span>|

<span data-ttu-id="d9701-137">Joker karakterler destekleyen cmdlet'ler tasarlarken, joker karakter birleşimleri için izin verin.</span><span class="sxs-lookup"><span data-stu-id="d9701-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="d9701-138">Örneğin, aşağıdaki kullanan komut `Get-ChildItem` c:\Techdocs klasöründe olan ve "a" ile "l." harflerle başlayan tüm .txt dosyaları almak için cmdlet</span><span class="sxs-lookup"><span data-stu-id="d9701-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="d9701-139">**Get-childıtem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="d9701-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="d9701-140">Önceki komutun aralığı joker karakter kullanan **[a-l]** dosya adı "a" ile "l." karakterleriyle başlaması gereken belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d9701-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="d9701-141">Daha sonra komut \* joker karakterini dosya adının ilk harfi ve .txt uzantısı arasındaki herhangi bir karakter için bir yer tutucu olarak.</span><span class="sxs-lookup"><span data-stu-id="d9701-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="d9701-142">Aşağıdaki örnek, "d" harfi dahil değildir, ancak "a" ile "f." den tüm diğer harfler içeren bir aralık joker karakter deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9701-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="d9701-143">**Get-childıtem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="d9701-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="d9701-144">Joker karakter düzenleri bir sabit karakterin işleme</span><span class="sxs-lookup"><span data-stu-id="d9701-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="d9701-145">Belirttiğiniz joker karakter deseni, değişmez karakterler içeriyorsa, bir kaçış karakteri vurgulamasını belirtir karakteri (') kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9701-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="d9701-146">Değişmez karakterler programlı olarak belirttiğinizde, tek bir vurgulamasını belirtir kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9701-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="d9701-147">Komut isteminde değişmez karakterler belirttiğinizde, iki tik kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9701-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="d9701-148">Örneğin, şu desene tam anlamıyla alınması gereken iki ayraçlar içerir.</span><span class="sxs-lookup"><span data-stu-id="d9701-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="d9701-149">"John Smith \`[\*']" (program aracılığıyla belirtilen)</span><span class="sxs-lookup"><span data-stu-id="d9701-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="d9701-150">"John Smith \` \`[\*\`']" (komut isteminde belirtilen)</span><span class="sxs-lookup"><span data-stu-id="d9701-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="d9701-151">Bu, "John Smith [pazarlama]" veya "John Smith [Geliştirme]" eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d9701-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="d9701-152">Cmdlet çıktı ve joker karakterler</span><span class="sxs-lookup"><span data-stu-id="d9701-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="d9701-153">Cmdlet parametrelerini joker karakterlerini desteklediğinde, bir cmdlet işlemi genellikle bir dizi çıkışını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9701-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="d9701-154">Bazen, bir kullanıcı aynı anda yalnızca tek bir öğe kullanabilir olduğundan çıkış dizisi desteklemek için hiçbir mantıklı.</span><span class="sxs-lookup"><span data-stu-id="d9701-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="d9701-155">Örneğin, `Set-Location` kullanıcı tek bir konuma IGNORE_DUP_KEY çıkış dizisi cmdlet'ini destekler.</span><span class="sxs-lookup"><span data-stu-id="d9701-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="d9701-156">Bu örnekte, cmdlet hala joker karakterleri destekler, ancak tek bir konuma çözümleme zorlar.</span><span class="sxs-lookup"><span data-stu-id="d9701-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9701-157">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d9701-157">See Also</span></span>

[<span data-ttu-id="d9701-158">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="d9701-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="d9701-159">WildcardPattern sınıfı</span><span class="sxs-lookup"><span data-stu-id="d9701-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)