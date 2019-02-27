---
title: Çevrimiçi Yardımı destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848156"
---
# <a name="supporting-online-help"></a><span data-ttu-id="dc3bd-102">Çevrimiçi Yardımı Destekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-102">Supporting Online Help</span></span>

<span data-ttu-id="dc3bd-103">Windows PowerShell 3. 0'den itibaren desteklemek için iki yolu vardır `Get-Help` Windows PowerShell komutları için çevrimiçi özelliği.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="dc3bd-104">Bu konuda, farklı komut türleri için bu özelliği uygulamanız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="dc3bd-105">Çevrimiçi Yardım hakkında</span><span class="sxs-lookup"><span data-stu-id="dc3bd-105">About Online Help</span></span>

<span data-ttu-id="dc3bd-106">Çevrimiçi Yardım her zaman Windows PowerShell sürecinin hayati bir parçası olmuştur.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="dc3bd-107">Ancak `Get-Help` cmdlet Yardım konuları komut isteminde görüntüler, birçok kullanıcı deneyimi çevrimiçi okuma, renk kodlaması, köprüler ve topluluk içeriği ve belgeleri wiki tabanlı paylaşım fikirler dahil olmak üzere tercih eder.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="dc3bd-108">En önemlisi de güncelleştirilebilir Yardımı gelişinden önce Yardım dosyaları en güncel sürümüne çevrimiçi Yardım sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="dc3bd-109">Güncelleştirilebilir Yardımı'ndaki Windows PowerShell 3.0 gelişinden ile çevrimiçi Yardım yine de önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="dc3bd-110">Esnek kullanıcı deneyiminin yanı sıra çevrimiçi Yardım olmayan veya Yardım konuları indirmek için güncelleştirilebilir Yardımı kullanamazsınız kullanıcıları için Yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="dc3bd-111">Nasıl Get-Help-Online çalışır</span><span class="sxs-lookup"><span data-stu-id="dc3bd-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="dc3bd-112">Komutlar için çevrimiçi Yardım konularını bulmalarına yardımcı olmak için `Get-Help` komutu bir komut için Yardım konusunun çevrimiçi sürümünü kullanıcının varsayılan Internet tarayıcısında açar. çevrimiçi bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="dc3bd-113">Örneğin, aşağıdaki komutu için çevrimiçi Yardım konusuna açılır `Invoke-Command` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="dc3bd-114">Uygulamak için `Get-Help` -çevrimiçi `Get-Help` cmdlet'i için bir Tekdüzen Kaynak Tanımlayıcısı (URI) çevrimiçi sürümünü Yardım konusunun aşağıdaki konumlarda arar.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="dc3bd-115">Komut için Yardım konusunun ilgili bağlantılar bölümündeki ilk bağlantıyı.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="dc3bd-116">Yardım konusu kullanıcının bilgisayarında yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="dc3bd-117">Bu özellik, Windows PowerShell 2.0 kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="dc3bd-118">HelpUri özellik, herhangi bir komutu.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-118">The HelpUri property of any command.</span></span> <span data-ttu-id="dc3bd-119">HelpUri özellik bile komut için Yardım konusu kullanıcının bilgisayarında yüklü değilken erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="dc3bd-120">Bu özellik, Windows PowerShell 3. 0 ' sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="dc3bd-121">`Get-Help` HelpUri özellik değerinin almadan önce bir URI ilgili bağlantılar bölümündeki ilk giriş arar.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="dc3bd-122">Özellik değeri yanlış veya değiştirildiyse, ilk ilgili bağlantıyı farklı bir değer girerek geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="dc3bd-123">Ancak, yalnızca Yardım konularının kullanıcının bilgisayarında yüklü olduğunda ilk ilgili bağlantıyı çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="dc3bd-124">Komutun Yardım konusunun ilgili ilk bağlantı için bir URI ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="dc3bd-125">Destekleyebilirsiniz `Get-Help` -Online komutu için XML tabanlı Yardım konusunun ilgili bağlantılar bölümündeki ilk giriş geçerli bir URI ekleyerek herhangi bir komutu.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="dc3bd-126">Bu seçenek yalnızca XML tabanlı Yardım konularında geçerlidir ve yalnızca kullanıcının bilgisayarında Yardım konusuna yüklendiğinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="dc3bd-127">Yardım konusu URI doldurulur aldığında, bu değer önceliklidir **HelpUri** özelliği komutu.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="dc3bd-128">Komutları için XML tabanlı Yardım konuları hakkında daha fazla bilgi için bkz. [Writing XML-Based komutlar için Yardım konularını](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="dc3bd-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="dc3bd-129">Bu özelliği desteklemek için URI görünmelidir `maml:uri` altına ilk öğe `maml:relatedLinks/maml:navigationLink` öğesinde `maml:relatedLinks` öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="dc3bd-130">Aşağıdaki XML URI'nin doğru yerleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="dc3bd-131">"Çevrimiçi sürüm:" metin `maml:linkText` öğesi en iyi bir uygulamadır, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="dc3bd-132">HelpUri özellik için bir komut ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="dc3bd-133">Bu bölüm, farklı türlerdeki komutları HelpUri özelliğini eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="dc3bd-134">Bir Cmdlet için HelpUri özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="dc3bd-135">Yazılmış cmdlet'lerinin C#, ekleme bir **HelpUri** cmdlet'i sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="dc3bd-136">Özniteliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="dc3bd-137">Aşağıdaki kod HelpUri özniteliğini gösterir `Get-History` cmdlet'i sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="dc3bd-138">Gelişmiş bir işleve HelpUri özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="dc3bd-139">Gelişmiş işlevler için ekleme bir **HelpUri** özelliğini **CmdletBinding** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="dc3bd-140">Özelliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="dc3bd-141">Aşağıdaki kod New-Takvim işlevinin HelpUri özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="dc3bd-142">HelpUri özniteliğini CIM komut ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="dc3bd-143">CIM komutları için ekleme bir **HelpUri** özniteliğini **CmdletMetadata** CDXML dosyasındaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="dc3bd-144">Özniteliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="dc3bd-145">Aşağıdaki kod hata ayıklama başlangıç CIM komut HelpUri özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="dc3bd-146">HelpUri özniteliğini bir iş akışına ekleme</span><span class="sxs-lookup"><span data-stu-id="dc3bd-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="dc3bd-147">Windows PowerShell dilinde yazılır, iş akışları için ekleme bir **. ExternalHelp** iş akışı kodu comment yönergesi.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="dc3bd-148">Yönerge değerini "http" veya "https" ile başlayan bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="dc3bd-149">HelpUri özellik iş akışı XAML tabanlı Windows PowerShell için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="dc3bd-150">Aşağıdaki kod gösterir. Bir iş akışı dosyasındaki ExternalHelp yönergesi.</span><span class="sxs-lookup"><span data-stu-id="dc3bd-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```