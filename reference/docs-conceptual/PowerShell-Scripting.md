---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell betik oluşturma
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094060"
---
# <a name="powershell"></a><span data-ttu-id="12d53-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="12d53-103">PowerShell</span></span>

<span data-ttu-id="12d53-104">PowerShell, .NET Framework üzerine oluşturulan bir görev tabanlı komut satırı kabuğu ve betik dilidir olur; Sistem yöneticileri ve ileri kullanıcılar, hızlı bir şekilde birden çok işletim sistemi (Linux, macOS, UNIX ve Windows) ve bu işletim sistemlerinde çalışan uygulamalar için ilgili işlemlerin yönetimini otomatik hale getirmek için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="12d53-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="12d53-105">PowerShell açık kaynaktır</span><span class="sxs-lookup"><span data-stu-id="12d53-105">PowerShell is open source</span></span>

<span data-ttu-id="12d53-106">PowerShell temel kaynak kodu github'da kullanılabilir ve topluluk Katkıları için açık sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="12d53-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="12d53-107">Bkz: [PowerShell GitHub üzerinde kaynak](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="12d53-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="12d53-108">Gereksinim duyduğunuz, BITS ile başlayabilirsiniz [alma PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="12d53-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="12d53-109">Veya belki de hızlı bir tura ile [kullanmaya başlama](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="12d53-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="12d53-110">PowerShell tasarım hedefleri</span><span class="sxs-lookup"><span data-stu-id="12d53-110">PowerShell design goals</span></span>
<span data-ttu-id="12d53-111">PowerShell, komut satırı ve betik ortamı değindiği sorunlarını ortadan kaldırılır ve yeni özellikler ekleyerek iyileştirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="12d53-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="12d53-112">Bulunabilirlik</span><span class="sxs-lookup"><span data-stu-id="12d53-112">Discoverability</span></span>
<span data-ttu-id="12d53-113">PowerShell özellikleri bulmak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="12d53-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="12d53-114">Örneğin, görüntüle ve Değiştir Windows Hizmetleri cmdlet'lerinin listesini bulmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="12d53-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="12d53-115">Hangi cmdlet'i bir görev gerçekleştirir keşfetme sonra cmdlet'i hakkında daha fazla kullanarak öğrenebilirsiniz `Get-Help` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="12d53-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="12d53-116">Örneğin, hakkında Yardım görüntülemek için `Get-Service` cmdlet'i, türü:</span><span class="sxs-lookup"><span data-stu-id="12d53-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="12d53-117">Çoğu cmdlet, yönetilebilir ve ardından metin görüntülemek için işlenen nesneleri gösterin.</span><span class="sxs-lookup"><span data-stu-id="12d53-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="12d53-118">Bu cmdlet'in çıktısı, tam olarak anlamak için kendi çıktı için kanal `Get-Member` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="12d53-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="12d53-119">Örneğin, aşağıdaki komut nesnesi çıktı tarafından üyeleri hakkında bilgi görüntüler `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="12d53-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="12d53-120">Tutarlılık</span><span class="sxs-lookup"><span data-stu-id="12d53-120">Consistency</span></span>
<span data-ttu-id="12d53-121">Sistemlerini yönetmeyi karmaşık bir çaba olabilir ve tutarlı bir arabirim üzerinden erişir Araçlar'ın devralınmış karmaşıklığı denetlemek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="12d53-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="12d53-122">Ne yazık ki, komut satırı araçları ne kodlanabilir COM nesneleri için kendi tutarlılık bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="12d53-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="12d53-123">PowerShell tutarlılığını birincil varlıklarını biridir.</span><span class="sxs-lookup"><span data-stu-id="12d53-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="12d53-124">Örneğin nasıl kullanacağınızı öğrenin, `Sort-Object` cmdlet'i, herhangi bir cmdlet'in çıkışını sıralamak için bu bilgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12d53-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="12d53-125">Farklı bir sıralama yordamları her cmdlet'in öğrenmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="12d53-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="12d53-126">Ayrıca, cmdlet geliştiriciler kendi cmdlet'leri için sıralama özellikleri tasarım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="12d53-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="12d53-127">PowerShell, bunları temel özellikleri sağlar ve bunları pek çok arabirimi yönleri hakkında tutarlı olmasını zorlar bir çerçeve sunar.</span><span class="sxs-lookup"><span data-stu-id="12d53-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="12d53-128">Framework bazı geliştiriciler için genellikle bırakılan seçeneklerin ortadan kaldırır, ancak buna karşılık, güçlü ve kullanımı kolay cmdlet'lerini geliştirmeyi çok daha kolay kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="12d53-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="12d53-129">Etkileşimli ve komut dosyası ortamlar</span><span class="sxs-lookup"><span data-stu-id="12d53-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="12d53-130">PowerShell komut satırı araçları ve COM nesneleri için erişmenizi ve ayrıca güç, .NET Framework Sınıf Kitaplığı'nı (FCL) kullanmanıza olanak sağlayan bir birleşik etkileşimli ve komut dosyası ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="12d53-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="12d53-131">Bu ortama bağlı Windows komut birden fazla komut satırı araçlarıyla etkileşimli bir ortam sağlayan istemi artırır.</span><span class="sxs-lookup"><span data-stu-id="12d53-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="12d53-132">Olanak veren Windows komut dosyası sistemi (WSH) betikleri da artırır birden çok komut satırı araçları ve COM Otomasyon nesneleri kullanabilirsiniz, ancak etkileşimli bir ortam sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="12d53-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="12d53-133">Bu özelliklerin tümü, erişim birleştirerek, PowerShell etkileşimli kullanıcı ve komut dosyası yazan yeteneklerini genişletir ve sistem yönetimini daha kolay yönetilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="12d53-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="12d53-134">Nesne yönü</span><span class="sxs-lookup"><span data-stu-id="12d53-134">Object Orientation</span></span>
<span data-ttu-id="12d53-135">PowerShell ile metinde komutları yazarak etkileşim olsa da, PowerShell metin olmayan nesneler üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="12d53-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="12d53-136">Komutun çıkışını bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="12d53-136">The output of a command is an object.</span></span>
<span data-ttu-id="12d53-137">Başka bir komuta çıkış nesnesi, giriş olarak gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="12d53-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="12d53-138">Sonuç olarak, PowerShell, yeni ve güçlü bir komut satırı paradigma tanıtırken diğer Kabuk ile karşılaşmış kişilere tanıdık bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="12d53-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="12d53-139">Metin yerine, nesneleri göndermek için yoluyla komutları arasında veri gönderme kavramı genişletir.</span><span class="sxs-lookup"><span data-stu-id="12d53-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="12d53-140">Komut dosyası için kolay geçiş</span><span class="sxs-lookup"><span data-stu-id="12d53-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="12d53-141">Oluşturma ve çalıştırma komut dosyaları yazmalarını geçiş kolay, etkileşimli olarak çok komutları PowerShell yapar.</span><span class="sxs-lookup"><span data-stu-id="12d53-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="12d53-142">Bir görev gerçekleştiren komutları bulmak için PowerShell komut isteminde komutları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12d53-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="12d53-143">Ardından, bunları bir dosyaya bir komut dosyası olarak kullanılmak üzere kopyalamadan önce bir döküm veya bir geçmiş komutlarda kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12d53-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
