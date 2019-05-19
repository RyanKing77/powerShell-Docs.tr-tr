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
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855124"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="feef6-102">Cmdlet Yardım Konusuna Örnekler Ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="feef6-103">Örnek Cmdlet Yardım hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="feef6-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="feef6-104">Parametre adları isteğe bağlı olsa bile tüm komut parametre adları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="feef6-105">Bu komut bir kolayca yorumlamak için kullanıcı yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="feef6-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="feef6-106">Windows PowerShell® içinde çalıştıkları olsa da, diğer adlar ve kısmi parametre adları, kaçının.</span><span class="sxs-lookup"><span data-stu-id="feef6-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="feef6-107">Örnek açıklamasında rasyonel komutu oluşumu için açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="feef6-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="feef6-108">Belirli parametreleri ve değerleri neden seçtiğiniz ve değişkenleri nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="feef6-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="feef6-109">Komut ifadeleri kullanıyorsa, bunları ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="feef6-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="feef6-110">Komut özellikleri ve yöntemleri nesneleri, özellikle de varsayılan ekran görüntüsünde, görünmez özellikleri kullanıyorsa, kullanıcı nesnesi hakkında bir fırsat söyleyin gibi örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="feef6-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="feef6-111">Örnekler görüntüleyen Görüşnümleri Yardım</span><span class="sxs-lookup"><span data-stu-id="feef6-111">Help Views that Display Examples</span></span>

<span data-ttu-id="feef6-112">Örnekler yalnızca ayrıntılı ve tam görünümlerinde cmdlet Yardım görünür.</span><span class="sxs-lookup"><span data-stu-id="feef6-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="feef6-113">Örnekler düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-113">Adding an Examples Node</span></span>

<span data-ttu-id="feef6-114">Aşağıdaki XML, tek bir örnek düğümü içeren bir örnek düğüm ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="feef6-115">Konusundaki dahil etmek istediğiniz her örnek için ek örnek düğümler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="feef6-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="feef6-116">Bir örnek başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-116">Adding an Example Title</span></span>

<span data-ttu-id="feef6-117">Aşağıdaki XML, örnek için bir başlık ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="feef6-118">Başlık, örneğin diğer örnekler dışında ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="feef6-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="feef6-119">Windows PowerShell® ardışık örnek sayısı içeren standart üstbilgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="feef6-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="feef6-120">Karakter önceki ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-120">Adding Preceding Characters</span></span>

<span data-ttu-id="feef6-121">Aşağıdaki XML, örnek komut (olmadan, müdahalede bulunan tüm alanları) hemen önce görüntülenen gibi karakterler Windows PowerShell istemi ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="feef6-122">Windows PowerShell istemi Windows PowerShell® kullanır: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="feef6-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="feef6-123">Komut ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-123">Adding the Command</span></span>

<span data-ttu-id="feef6-124">Aşağıdaki XML, örneğin gerçek komut ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="feef6-125">Komut eklerken, adın tamamını yazın (diğer ad kullanmayın) cmdlet'leri ve parametreleri.</span><span class="sxs-lookup"><span data-stu-id="feef6-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="feef6-126">Ayrıca, mümkün olduğunda, küçük harf karakterler kullanın.</span><span class="sxs-lookup"><span data-stu-id="feef6-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="feef6-127">Bir açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-127">Adding a Description</span></span>

<span data-ttu-id="feef6-128">Aşağıdaki XML, örnek için bir açıklama ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="feef6-129">Windows PowerShell® kullanan tek bir dizi \<MAML > olsa bile bir açıklama etiketleri birden çok \<MAML > etiketleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="feef6-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="feef6-130">Örnek çıktı ekleme</span><span class="sxs-lookup"><span data-stu-id="feef6-130">Adding Example Output</span></span>

<span data-ttu-id="feef6-131">Aşağıdaki XML, komut çıktısı ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="feef6-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="feef6-132">Komutu sonuçları bilgileri isteğe bağlıdır, ancak bazı durumlarda belirli parametreler kullanılarak etkisini göstermeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="feef6-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="feef6-133">Windows PowerShell® kullanan iki boş \<MAML > komutundan komut çıktısı ayırmak için etiketler.</span><span class="sxs-lookup"><span data-stu-id="feef6-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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