---
title: Bir Cmdlet Yardım konusunun örneklere ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083476"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="58a65-102">Cmdlet Yardım Konusuna Örnekler Ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="58a65-103">Örnek Cmdlet Yardım hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="58a65-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="58a65-104">Örnekler görüntüleyen Görüşnümleri Yardım</span><span class="sxs-lookup"><span data-stu-id="58a65-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="58a65-105">Örnekler düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="58a65-106">Karakter önceki ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="58a65-107">Komut ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="58a65-108">Bir açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="58a65-109">Örnek çıktı ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="58a65-110">Örnek Cmdlet Yardım hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="58a65-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="58a65-111">Parametre adları isteğe bağlı olsa bile tüm komut parametre adları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="58a65-112">Bu komut bir kolayca yorumlamak için kullanıcı yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="58a65-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="58a65-113">Windows PowerShell® içinde çalıştıkları olsa da, diğer adlar ve kısmi parametre adları, kaçının.</span><span class="sxs-lookup"><span data-stu-id="58a65-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="58a65-114">Örnek açıklamasında rasyonel komutu oluşumu için açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58a65-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="58a65-115">Belirli parametreleri ve değerleri neden seçtiğiniz ve değişkenleri nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="58a65-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="58a65-116">Komut ifadeleri kullanıyorsa, bunları ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58a65-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="58a65-117">Komut özellikleri ve yöntemleri nesneleri, özellikle de varsayılan ekran görüntüsünde, görünmez özellikleri kullanıyorsa, kullanıcı nesnesi hakkında bir fırsat söyleyin gibi örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="58a65-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="58a65-118">Örnekler görüntüleyen Görüşnümleri Yardım</span><span class="sxs-lookup"><span data-stu-id="58a65-118">Help Views that Display Examples</span></span>

<span data-ttu-id="58a65-119">Örnekler yalnızca ayrıntılı ve tam görünümlerinde cmdlet Yardım görünür.</span><span class="sxs-lookup"><span data-stu-id="58a65-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="58a65-120">Örnekler düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-120">Adding an Examples Node</span></span>

<span data-ttu-id="58a65-121">Aşağıdaki XML, tek bir örnek düğümü içeren bir örnek düğüm ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="58a65-122">Konusundaki dahil etmek istediğiniz her örnek için ek örnek düğümler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58a65-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="58a65-123">Bir örnek başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-123">Adding an Example Title</span></span>

<span data-ttu-id="58a65-124">Aşağıdaki XML, örnek için bir başlık ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="58a65-125">Başlık, örneğin diğer örnekler dışında ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58a65-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="58a65-126">Windows PowerShell® ardışık örnek sayısı içeren standart üstbilgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="58a65-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="58a65-127">Karakter önceki ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-127">Adding Preceding Characters</span></span>

<span data-ttu-id="58a65-128">Aşağıdaki XML, örnek komut (olmadan, müdahalede bulunan tüm alanları) hemen önce görüntülenen gibi karakterler Windows PowerShell istemi ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="58a65-129">Windows PowerShell istemi Windows PowerShell® kullanır: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="58a65-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="58a65-130">Komut ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-130">Adding the Command</span></span>

<span data-ttu-id="58a65-131">Aşağıdaki XML, örneğin gerçek komut ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="58a65-132">Komut eklerken, adın tamamını yazın (diğer ad kullanmayın) cmdlet'leri ve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="58a65-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="58a65-133">Ayrıca, mümkün olduğunda, küçük harf karakterler kullanın.</span><span class="sxs-lookup"><span data-stu-id="58a65-133">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="58a65-134">Bir açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-134">Adding a Description</span></span>

<span data-ttu-id="58a65-135">Aşağıdaki XML, örnek için bir açıklama ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="58a65-136">Windows PowerShell® kullanan tek bir dizi \<MAML > olsa bile bir açıklama etiketleri birden çok \<MAML > etiketleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58a65-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="58a65-137">Örnek çıktı ekleme</span><span class="sxs-lookup"><span data-stu-id="58a65-137">Adding Example Output</span></span>

<span data-ttu-id="58a65-138">Aşağıdaki XML, komut çıktısı ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a65-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="58a65-139">Komutu sonuçları bilgileri isteğe bağlıdır, ancak bazı durumlarda belirli parametreler kullanılarak etkisini göstermeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="58a65-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="58a65-140">Windows PowerShell® kullanan iki boş \<MAML > komutundan komut çıktısı ayırmak için etiketler.</span><span class="sxs-lookup"><span data-stu-id="58a65-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```