---
title: Cmdlet Yardım dosyasının nasıl oluşturulacağı | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083255"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="b1efa-102">Cmdlet Yardım Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1efa-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="b1efa-103">Bu bölümde Windows PowerShell cmdlet Yardım konuları için içeriği geçerli bir XML dosyası oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1efa-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="b1efa-104">Bu bölümde, nasıl Yardım dosyasını adlandırmak, uygun XML üstbilgileri ekleme ve Yardım içeriğini cmdlet'i farklı bölümlerini içerecek düğümleri ekleme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1efa-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="b1efa-105">Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için.</span><span class="sxs-lookup"><span data-stu-id="b1efa-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="b1efa-106">Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b1efa-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="b1efa-107">Bir Cmdlet Yardım dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1efa-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="b1efa-108">Bir metin dosyası oluşturun ve UTF8 Kodlaması kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b1efa-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="b1efa-109">Windows PowerShell cmdlet Yardım dosyası olarak algılayabilir, dosya adı şu biçimde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1efa-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="b1efa-110">Aşağıdaki XML üst bilgilerini metin dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1efa-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="b1efa-111">Dosya çok aracılı Modelleme Dili (MAML) şemayla doğrulandı dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b1efa-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="b1efa-112">Şu anda, Windows PowerShell dosyasını doğrulamak için herhangi bir araç sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b1efa-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="b1efa-113">Bir komut düğümü derlemedeki her cmdlet için cmdlet Yardım dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1efa-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="b1efa-114">Her düğümü komut düğümü cmdlet Yardım konusunun farklı bölümlere ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="b1efa-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="b1efa-115">Aşağıdaki tabloda her düğümün bir açıklaması tarafından izlenen her bir düğümün XML öğesi listeler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="b1efa-116">Düğüm</span><span class="sxs-lookup"><span data-stu-id="b1efa-116">Node</span></span>|<span data-ttu-id="b1efa-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1efa-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="b1efa-118">Cmdlet Yardım konusunun adını ve özeti bölümlerinin içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-119">Daha fazla bilgi için [Cmdlet adı ve özeti nasıl ekleneceğini](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="b1efa-120">Cmdlet Yardım konusunun Açıklama bölümünde için içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-121">Daha fazla bilgi için [Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="b1efa-122">Cmdlet Yardım konusunun söz DİZİMİ bölümünün içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-123">Daha fazla bilgi için [ekleme sözdizimi için Cmdlet Yardım konusunun nasıl](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="b1efa-124">PARAMETRELER bölümü cmdlet Yardım konusunun içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-125">Daha fazla bilgi için [parametreleri eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="b1efa-126">Cmdlet Yardım konusunun GİRİŞLERİ bölümünün içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-127">Daha fazla bilgi için [giriş türleri eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="b1efa-128">ÇIKTILAR bölümünü cmdlet Yardım konusunun içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-129">Daha fazla bilgi için [ekleme dönüş değerleri için Cmdlet Yardım konusunun nasıl](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="b1efa-130">İçerik cmdlet Yardım konusunun Notlar bölümüne ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-131">Daha fazla bilgi için [ekleme için Cmdlet Yardım konusunun notları](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="b1efa-132">İçerik için cmdlet Yardım konusunun ÖRNEKLER bölümüne ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-133">Daha fazla bilgi için [ekleme örnekleri için Cmdlet Yardım konusunun nasıl](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="b1efa-134">İçin cmdlet Yardım konusunun ilgili bağlantılar bölümüne içerik ekler.</span><span class="sxs-lookup"><span data-stu-id="b1efa-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b1efa-135">Daha fazla bilgi için [ilgili bağlantılar eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b1efa-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="b1efa-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1efa-136">Example</span></span>

 <span data-ttu-id="b1efa-137">Cmdlet Yardım konusunun çeşitli bölümlerini düğümleri içeren bir komut düğümü bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b1efa-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="b1efa-138">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b1efa-138">See Also</span></span>

 [<span data-ttu-id="b1efa-139">Cmdlet adı ve özeti nasıl ekleneceğini</span><span class="sxs-lookup"><span data-stu-id="b1efa-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-140">Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="b1efa-141">Cmdlet Yardım konuları söz dizimi ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-142">Cmdlet Yardım konuları parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="b1efa-143">Bir Cmdlet Yardım konusuna giriş türleri ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-144">Dönüş değerleri için Cmdlet Yardım konusunun ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-145">Ekleme için Cmdlet Yardım konusunun notları</span><span class="sxs-lookup"><span data-stu-id="b1efa-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-146">Bir Cmdlet Yardım konusunun örneklere ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-147">Cmdlet Yardım konuları ilgili bağlantılar ekleme</span><span class="sxs-lookup"><span data-stu-id="b1efa-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b1efa-148">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="b1efa-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)