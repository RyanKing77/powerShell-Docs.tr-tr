---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: PowerShell betik oluşturma
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451039"
---
# <a name="powershell"></a><span data-ttu-id="0fcb0-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fcb0-103">PowerShell</span></span>

<span data-ttu-id="0fcb0-104">Bir görev tabanlı komut satırı kabuğu ve betik dilidir .NET üzerinde oluşturulmuş powershell'dir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="0fcb0-105">PowerShell, sistem yöneticileri yardımcı olur ve ileri kullanıcılar (Linux, macOS ve Windows) işletim sistemleri ve işlemleri yönetme görevleri hızla otomatikleştirin.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="0fcb0-106">PowerShell komutları, komut satırından bilgisayarları yönetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="0fcb0-107">PowerShell sağlayıcıları, kayıt defteri gibi veri depolarında erişmek ve sertifika deposunu, dosya sistemine erişmelerini olarak kolayca belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="0fcb0-108">PowerShell, kapsamlı bir ifade ayrıştırıcısı ve tam olarak geliştirilen bir betik dilini içerir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="0fcb0-109">PowerShell açık kaynak</span><span class="sxs-lookup"><span data-stu-id="0fcb0-109">PowerShell is open-source</span></span>

<span data-ttu-id="0fcb0-110">PowerShell temel kaynak kodu github'da kullanılabilir ve topluluk Katkıları için açık sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="0fcb0-111">Bkz: [PowerShell GitHub üzerinde kaynak](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="0fcb0-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="0fcb0-112">Gereksinim duyduğunuz, BITS ile başlayabilirsiniz [alma PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="0fcb0-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="0fcb0-113">Veya belki de hızlı bir tura ile [Başlarken](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="0fcb0-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="0fcb0-114">PowerShell tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="0fcb0-114">PowerShell design goals</span></span>

<span data-ttu-id="0fcb0-115">PowerShell, komut satırı ve betik ortamı değindiği sorunlarını ortadan kaldırılır ve yeni özellikler ekleyerek iyileştirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="0fcb0-116">Bulunabilirlik</span><span class="sxs-lookup"><span data-stu-id="0fcb0-116">Discoverability</span></span>

<span data-ttu-id="0fcb0-117">PowerShell özellikleri bulmak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="0fcb0-118">Örneğin, görüntüle ve Değiştir Windows Hizmetleri cmdlet'lerinin listesini bulmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="0fcb0-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="0fcb0-119">Hangi cmdlet'i bir görev gerçekleştirir keşfetme sonra cmdlet'i hakkında daha fazla kullanarak öğrenebilirsiniz `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0fcb0-120">Örneğin, hakkında Yardım görüntülemek için `Get-Service` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="0fcb0-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="0fcb0-121">Yönetilen ve ardından görüntülemek için metin olarak işlenen çoğu cmdlet'leri dönüş nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="0fcb0-122">Bir cmdlet'in çıktısı, tam olarak anlamak için çıktı için kanal `Get-Member` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="0fcb0-123">Örneğin, aşağıdaki komut nesnesi çıktı tarafından üyeleri hakkında bilgi görüntüler `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="0fcb0-124">Tutarlılık</span><span class="sxs-lookup"><span data-stu-id="0fcb0-124">Consistency</span></span>

<span data-ttu-id="0fcb0-125">Sistemlerini yönetmeye, karmaşık bir görev olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="0fcb0-126">Tutarlı bir arabirimi olan araçlar, devralınan karmaşıklığı denetlemek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="0fcb0-127">Ne yazık ki, komut satırı araçları ve kodlanabilir COM nesneleri için kendi tutarlılık bilinen değildir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="0fcb0-128">PowerShell tutarlılığını birincil varlıklarını biridir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="0fcb0-129">Örneğin nasıl kullanacağınızı öğrenin, `Sort-Object` cmdlet'i, herhangi bir cmdlet'in çıkışını sıralamak için bu bilgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="0fcb0-130">Farklı bir sıralama yordamları her cmdlet'in öğrenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="0fcb0-131">Ayrıca, cmdlet geliştiriciler kendi cmdlet'leri için sıralama özellikleri tasarım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="0fcb0-132">PowerShell, tutarlılık zorlayan temel özelliklere sahip bir çerçeve sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="0fcb0-133">Framework, geliştiriciler için sol bazı seçenekler ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="0fcb0-134">Ancak, cmdlet'leri geliştirilmesini çok daha kolay kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="0fcb0-135">Etkileşimli ve komut dosyası ortamlar</span><span class="sxs-lookup"><span data-stu-id="0fcb0-135">Interactive and scripting environments</span></span>

<span data-ttu-id="0fcb0-136">Windows komut istemi, etkileşimli bir kabuk komut satırı araçları ve temel betik erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="0fcb0-137">Windows betik sistemi (WSH) kodlanabilir komut satırı araçları ve COM Otomasyon nesneleri var, ancak etkileşimli bir kabuk sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="0fcb0-138">PowerShell, etkileşimli bir kabuk ve komut dosyası ortamı birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="0fcb0-139">PowerShell komut satırı araçları, COM nesnelerini ve .NET sınıf kitaplıkları erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="0fcb0-140">Bu özellik bileşimi etkileşimli kullanıcı, betik yazarı ve Sistem Yöneticisi yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="0fcb0-141">Nesne yönü</span><span class="sxs-lookup"><span data-stu-id="0fcb0-141">Object orientation</span></span>

<span data-ttu-id="0fcb0-142">PowerShell değil metin nesnesinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="0fcb0-143">Komutun çıkışını bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-143">The output of a command is an object.</span></span> <span data-ttu-id="0fcb0-144">İşlem hattı aracılığıyla çıkış nesnesi giriş olarak başka bir komut gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="0fcb0-145">Bu işlem hattı ile diğer Kabukları deneyimli kişiler için tanıdık bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="0fcb0-146">PowerShell, metin yerine nesneleri göndererek bu kavramı genişletir.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="0fcb0-147">Komut dosyası için kolay geçiş</span><span class="sxs-lookup"><span data-stu-id="0fcb0-147">Easy transition to scripting</span></span>

<span data-ttu-id="0fcb0-148">Oluşturma ve çalıştırma komut dosyaları yazmalarını geçiş kolay, etkileşimli olarak çok komutları PowerShell'in komut bulunabilirliği yapar.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="0fcb0-149">PowerShell dökümleri ve geçmişi, komutları bir komut dosyası olarak kullanılmak üzere bir dosya kopyalamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0fcb0-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
