---
title: PowerShell cmdlet'leri için Yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083170"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="a2645-102">PowerShell cmdlet'leri için Yardım yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="a2645-103">PowerShell cmdlet'lerini yararlı olabilir, ancak, Yardım konuları açıkça cmdlet yaptığı ve nasıl kullanılacağını açıklayan sürece cmdlet kullanılmayan veya daha da kötüsü, kullanıcıları rahatsız.</span><span class="sxs-lookup"><span data-stu-id="a2645-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="a2645-104">XML temelli cmdlet Yardım dosyası biçimi tutarlılığı artırır, ancak çok daha yararlı bir Yardım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2645-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="a2645-105">Cmdlet Yardım hiçbir zaman yazdıysanız, aşağıdaki yönergeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="a2645-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="a2645-106">Cmdlet Yardım konusunun yazar için gereken XML Şeması, aşağıdaki bölümde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2645-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="a2645-107">İle başlayan [Cmdlet Yardım dosyası oluşturma](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="a2645-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="a2645-108">Bu konu, en üst düzey XML düğümlerini açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a2645-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="a2645-109">Cmdlet Yardım için yazma Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a2645-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="a2645-110">İyi yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-110">Write well</span></span>
<span data-ttu-id="a2645-111">Hiçbir şey iyi-yazılan konunun yerini alır.</span><span class="sxs-lookup"><span data-stu-id="a2645-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="a2645-112">Profesyonel bir yazıcı emin değilseniz, yazıcı veya Düzenleyicisi yardımcı olmak üzere bulun.</span><span class="sxs-lookup"><span data-stu-id="a2645-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="a2645-113">Yardım metni Microsoft Word'e kopyalayıp dilbilgisi kullanmak için başka bir alternatiftir ve işinizi geliştirmek için yazım denetimi yapar.</span><span class="sxs-lookup"><span data-stu-id="a2645-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="a2645-114">Yalnızca yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-114">Write simply</span></span>
<span data-ttu-id="a2645-115">Basit bir sözcük ve tümcecikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-115">Use simple words and phrases.</span></span>
<span data-ttu-id="a2645-116">Terimler kaçının.</span><span class="sxs-lookup"><span data-stu-id="a2645-116">Avoid jargon.</span></span>
<span data-ttu-id="a2645-117">Birçok okuyucu yalnızca bir yabancı dildeki sözlük ve Yardım konu başlığınız ile donatılmış göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a2645-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="a2645-118">Tutarlı bir şekilde yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-118">Write consistently</span></span>
<span data-ttu-id="a2645-119">İlgili cmdlet (örneğin, get-x ve set-x) benzer Yardımı.</span><span class="sxs-lookup"><span data-stu-id="a2645-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="a2645-120">Standart açıklamalar gibi standart parametreler için kullanmak **zorla** ve **Inputobject**.</span><span class="sxs-lookup"><span data-stu-id="a2645-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="a2645-121">(Bunları Yardım için çekirdek cmdlet'lerinin kopyalayın.) Standart terimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="a2645-122">Örnek, kullan "parametresi", değil "bağımsız değişken" ve kullanım "cmdlet'i" değil "komut" veya "command-let."</span><span class="sxs-lookup"><span data-stu-id="a2645-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="a2645-123">İle bir fiili özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="a2645-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="a2645-124">Özeti alanın hangi cmdlet desteklemiyor, bunun ne olduğunu veya nasıl çalıştığını kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="a2645-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="a2645-125">Bu cmdlet, kendi gereksinimlerini karşılıyorsa, kullanıcıları bilgilendirir ve görev tabanlı bir deyimi fiilleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2645-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="a2645-126">"Get", "oluşturma" ve "Değiştir" gibi basit fiilleri kullanın</span><span class="sxs-lookup"><span data-stu-id="a2645-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="a2645-127">"Set", "değiştirme" gibi belirsiz ve başvurmaktan sözcükleri olabilen kaçının.</span><span class="sxs-lookup"><span data-stu-id="a2645-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="a2645-128">Nesneler üzerinde odaklanın</span><span class="sxs-lookup"><span data-stu-id="a2645-128">Focus on objects</span></span>
<span data-ttu-id="a2645-129">Çoğu "cmdlet'leri görünen bir şey Al", ancak bir nesne almak için kendi birincil işlevi olduğu.</span><span class="sxs-lookup"><span data-stu-id="a2645-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="a2645-130">Böylece kullanıcılar varsayılan görüntüyü birçok biri olduğunu ve bunlar için farklı şekilde alınan nesnenin özelliklerini ve yöntemlerini kullanabilirsiniz anlamak, Yardım'da nesnede odaklanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="a2645-131">Ayrıntılı açıklamalar için yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-131">Write detailed descriptions</span></span>
<span data-ttu-id="a2645-132">Kısaca cmdlet'in ayrıntılı bir açıklama yapabileceğiniz her şeyi listeleyin.</span><span class="sxs-lookup"><span data-stu-id="a2645-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="a2645-133">Bu ayrıntılı bir açıklama listesinde, bir özelliği değiştirmek için ana işlevi olduğu, ancak cmdlet tüm özelliklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2645-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="a2645-134">Geleneksel söz dizimini kullanın</span><span class="sxs-lookup"><span data-stu-id="a2645-134">Use conventional syntax</span></span>
<span data-ttu-id="a2645-135">Windows ve UNIX komut satırı Yardımı için ortak olan standart Backus-Naur biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="a2645-136">Microsoft .NET Framework türleri için parametre değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="a2645-137">Parametre değerlerini (söz dizimi ve parametre açıklamaları) için yer tutucular .NET Framework türleri parametre kabul edecek nesnelerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2645-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="a2645-138">PowerShell ekibi, kullanıcıların .NET Framework hakkında öğretin yardımcı olmak için bu kural geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a2645-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="a2645-139">Tam parametre açıklamaları yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="a2645-140">Parametre açıklamaları, iki şey kullanıcıları bildirmelidir: (etkisini) parametrenin ne yapar ve bunların ne için parametre değerleri yazmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a2645-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="a2645-141">Pratik örnekler yazma</span><span class="sxs-lookup"><span data-stu-id="a2645-141">Write practical examples</span></span>
<span data-ttu-id="a2645-142">Tüm parametreleri kullanma örnekleri göstermesi gerekir, ancak en önemli şey gerçek görevleri cmdlet kullanmayı göstermektir.</span><span class="sxs-lookup"><span data-stu-id="a2645-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="a2645-143">Basit bir örnek ile başlayın ve giderek daha karmaşık örnekler yazma.</span><span class="sxs-lookup"><span data-stu-id="a2645-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="a2645-144">Son örnekte, bir işlem hattı, cmdlet kullanmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a2645-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="a2645-145">Notlar alanı kullanın</span><span class="sxs-lookup"><span data-stu-id="a2645-145">Use the Notes field</span></span>
<span data-ttu-id="a2645-146">Notlar alanı kullanıcılar cmdlet anlamanız gerekir, kavramları açıklamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2645-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="a2645-147">Notlar, sık karşılaşılan kayıt hatalarının önüne kullanıcılara yardımcı olmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2645-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="a2645-148">Değiştiklerinde URL'leri kaçının.</span><span class="sxs-lookup"><span data-stu-id="a2645-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="a2645-149">Bunun yerine, aranacak kullanıcıların koşulları belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2645-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="a2645-150">Yardım test</span><span class="sxs-lookup"><span data-stu-id="a2645-150">Test your Help</span></span>
<span data-ttu-id="a2645-151">Kodunuzu test yalnızca gibi Yardım test edin.</span><span class="sxs-lookup"><span data-stu-id="a2645-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="a2645-152">Arkadaş sahip ve iş arkadaşlarınızla Yardım içeriğiniz okuyun ve geri bildirim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a2645-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="a2645-153">Ayrıca, haber görüşleri gönderebilecekleri.</span><span class="sxs-lookup"><span data-stu-id="a2645-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2645-154">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a2645-154">See Also</span></span>

 [<span data-ttu-id="a2645-155">Cmdlet Yardım dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2645-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="a2645-156">Cmdlet adı ve özeti için Cmdlet Yardım konusunun ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-157">Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="a2645-158">Cmdlet Yardım konuları söz dizimi ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-159">Cmdlet Yardım konuları parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="a2645-160">Bir Cmdlet Yardım konusuna giriş türleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-161">Dönüş değerleri için Cmdlet Yardım konusunun ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-162">Ekleme için Cmdlet Yardım konusunun notları</span><span class="sxs-lookup"><span data-stu-id="a2645-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-163">Bir Cmdlet Yardım konusunun örneklere ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-164">Cmdlet Yardım konuları ilgili bağlantılar ekleme</span><span class="sxs-lookup"><span data-stu-id="a2645-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="a2645-165">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="a2645-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)