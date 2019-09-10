---
title: Çevrimiçi yardımı destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848082"
---
# <a name="supporting-online-help"></a><span data-ttu-id="54bf5-102">Çevrimiçi Yardımı Destekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-102">Supporting Online Help</span></span>

<span data-ttu-id="54bf5-103">Windows PowerShell 3,0 ' den başlayarak, Windows PowerShell komutlarının `Get-Help` çevrimiçi özelliğini desteklemeye yönelik iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="54bf5-104">Bu konu, farklı komut türleri için bu özelliğin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="54bf5-105">Çevrimiçi Yardım hakkında</span><span class="sxs-lookup"><span data-stu-id="54bf5-105">About Online Help</span></span>

<span data-ttu-id="54bf5-106">Çevrimiçi yardım her zaman Windows PowerShell 'in önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="54bf5-107">`Get-Help` Cmdlet 'i komut isteminde Yardım konularını görüntülüyor olsa da birçok kullanıcı, topluluk içerikleriyle ve wiki tabanlı belgelerde renk kodlama, köprüler ve paylaşma fikirleri dahil olmak üzere çevrimiçi okuma deneyimini tercih eder.</span><span class="sxs-lookup"><span data-stu-id="54bf5-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="54bf5-108">En önemlisi, güncelleştirilebilir yardım 'dan önce, yardım dosyalarının en güncel sürümünü sağlamadan önce çevrimiçi yardım.</span><span class="sxs-lookup"><span data-stu-id="54bf5-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="54bf5-109">Windows PowerShell 3,0 ' de güncelleştirilebilir yardım ile ilgili, çevrimiçi yardım hala önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="54bf5-110">Esnek kullanıcı deneyiminin yanı sıra, çevrimiçi yardım, yardım konularını indirmek için güncelleştirilebilir yardımı kullanmayan veya kullanmayan kullanıcılara yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="54bf5-111">Get-Help-online nasıl Işe yarar?</span><span class="sxs-lookup"><span data-stu-id="54bf5-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="54bf5-112">Kullanıcıların, komutlara yönelik çevrimiçi Yardım konularını bulmasına yardımcı olmak için, `Get-Help` kullanıcının varsayılan Internet tarayıcısında bir komutla ilgili Yardım konusunun çevrimiçi sürümünü açan bir çevrimiçi parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="54bf5-113">Örneğin, aşağıdaki komut, `Invoke-Command` cmdlet 'i için çevrimiçi Yardım konusunu açar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="54bf5-114">-Online `Get-Help` `Get-Help` 'ı uygulamak için, cmdlet aşağıdaki konumlarda yer alarak çevrimiçi sürüm yardım konusu için bir Tekdüzen Kaynak tanımlayıcısı (URI) arar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="54bf5-115">Komutun Yardım konusunun Ilgili bağlantılar bölümündeki ilk bağlantı.</span><span class="sxs-lookup"><span data-stu-id="54bf5-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="54bf5-116">Yardım konusunun kullanıcının bilgisayarında yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="54bf5-117">Bu özellik Windows PowerShell 2,0 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="54bf5-118">Herhangi bir komutun HelpUri özelliği.</span><span class="sxs-lookup"><span data-stu-id="54bf5-118">The HelpUri property of any command.</span></span> <span data-ttu-id="54bf5-119">HelpUri özelliği, komutun yardım konusu Kullanıcı bilgisayarında yüklü olmadığında bile erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="54bf5-120">Bu özellik Windows PowerShell 3,0 ' de tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="54bf5-121">`Get-Help`HelpUri özellik değerini almadan önce Ilgili bağlantılar bölümündeki ilk girişte bir URI arar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="54bf5-122">Özellik değeri yanlışsa veya değiştiyse, ilk Ilgili bağlantıya farklı bir değer girerek onu geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54bf5-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="54bf5-123">Ancak, ilk Ilişkili bağlantı yalnızca kullanıcının bilgisayarına yardım konuları yüklendiğinde işe yarar.</span><span class="sxs-lookup"><span data-stu-id="54bf5-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="54bf5-124">Komut Yardım konusunun ilk ilgili bağlantısına URI ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="54bf5-125">Komutu için XML `Get-Help` tabanlı Yardım konusunun ilgili bağlantılar bölümündeki ilk girişe geçerli bir URI ekleyerek, herhangi bir komut için-online 'ı destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54bf5-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="54bf5-126">Bu seçenek yalnızca, XML tabanlı yardım konularında geçerlidir ve yalnızca kullanıcının bilgisayarında yardım konusu yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="54bf5-127">Yardım konusu yüklendiğinde ve URI doldurulduğu zaman, bu değer komutun **HelpUri** özelliğinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="54bf5-128">Bu özelliği desteklemek için URI 'nin `maml:uri` `maml:relatedLinks` öğedeki ilk `maml:relatedLinks/maml:navigationLink` öğe altındaki öğesinde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="54bf5-129">Aşağıdaki XML URI 'nin doğru yerleşimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="54bf5-130">`maml:linkText` Öğedeki "Çevrimiçi sürüm:" metni en iyi uygulamadır, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="54bf5-131">Bir komuta HelpUri özelliğini ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="54bf5-132">Bu bölümde, HelpUri özelliğinin farklı türlerin komutlarına nasıl ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="54bf5-133">Bir cmdlet 'e HelpUri özelliği ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="54bf5-134">İçinde C#yazılan cmdlet 'ler Için, cmdlet sınıfına bir **helpurı** özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54bf5-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="54bf5-135">Özniteliğin değeri "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="54bf5-136">Aşağıdaki kod, `Get-History` cmdlet sınıfının HelpUri özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54bf5-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="54bf5-137">Gelişmiş Işleve HelpUri özelliği ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="54bf5-138">Gelişmiş işlevler için, **CmdletBinding** özniteliğine bir **HelpUri** özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54bf5-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="54bf5-139">Özelliğin değeri, "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="54bf5-140">Aşağıdaki kod, New-Calendar işlevinin HelpUri özniteliğini gösterir</span><span class="sxs-lookup"><span data-stu-id="54bf5-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="54bf5-141">CıM komutuna Helpurı özniteliği ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="54bf5-142">CıM komutları için CDXML dosyasındaki **Cmdletmetadata** öğesine bir **helpurı** özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="54bf5-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="54bf5-143">Özniteliğin değeri "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="54bf5-144">Aşağıdaki kod, Start-Debug CıM komutunun HelpUri özniteliğini gösterir</span><span class="sxs-lookup"><span data-stu-id="54bf5-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="54bf5-145">Bir Iş akışına Helpurı özniteliği ekleme</span><span class="sxs-lookup"><span data-stu-id="54bf5-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="54bf5-146">Windows PowerShell dilinde yazılmış iş akışları için bir ekleyin **.** İş akışı koduna ExternalHelp açıklama yönergesi.</span><span class="sxs-lookup"><span data-stu-id="54bf5-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="54bf5-147">Yönergesinin değeri, "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54bf5-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="54bf5-148">HelpUri özelliği, Windows PowerShell 'de XAML tabanlı iş akışları için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="54bf5-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="54bf5-149">Aşağıdaki kod, gösterir. Bir iş akışı dosyasında ExternalHelp yönergesi.</span><span class="sxs-lookup"><span data-stu-id="54bf5-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```