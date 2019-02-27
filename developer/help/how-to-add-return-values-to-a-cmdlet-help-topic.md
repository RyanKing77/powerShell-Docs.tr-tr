---
title: Return ekleme değerleri için Cmdlet Yardım konusunun | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849220"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="541fe-102">Cmdlet Yardım Konusuna Dönüş Değerleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="541fe-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="541fe-103">Bu bölümde, bir çıkış bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="541fe-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="541fe-104">ÇIKTILAR bölümünü .NET sınıflarını cmdlet döndürür veya işlem hattını geçirir nesneleri listeler.</span><span class="sxs-lookup"><span data-stu-id="541fe-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="541fe-105">Çıkış bölümüne ekleyebilirsiniz sınıfları sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="541fe-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="541fe-106">Bir cmdlet dönüş türleri içine alınan bir \<komutu: returnValues > düğümle içine her sınıfın bir \<komutu: returnValue > öğesi.</span><span class="sxs-lookup"><span data-stu-id="541fe-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="541fe-107">Bir cmdlet herhangi bir çıktı oluşturmaz, hiçbir çıktı olduğunu belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="541fe-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="541fe-108">Örneğin, sınıf adı yerine "None" yazın ve kısa bir açıklama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="541fe-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="541fe-109">Cmdlet çıktı koşullu olarak oluşturursa, koşulları açıklamak ve koşullu çıktıyı açıklamak için bu düğümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="541fe-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="541fe-110">Şema iki içerir \<maml:description > her öğeleri \<komutu: returnValue > öğesi.</span><span class="sxs-lookup"><span data-stu-id="541fe-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="541fe-111">Ancak, `Get-Help` cmdlet'i yalnızca içeriğini görüntüler \<komutu: returnValue > /\<maml:description > öğesi.</span><span class="sxs-lookup"><span data-stu-id="541fe-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="541fe-112">Windows PowerShell 3. 0'den itibaren `Get-Help` cmdlet içeriğini görüntüler \<maml:uri > öğesi.</span><span class="sxs-lookup"><span data-stu-id="541fe-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="541fe-113">Bu öğe, .NET sınıf açıklayan konulara kullanıcıları doğrudan sağlar.</span><span class="sxs-lookup"><span data-stu-id="541fe-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="541fe-114">Aşağıdaki XML gösterildiği \<maml:returnValues > düğümü.</span><span class="sxs-lookup"><span data-stu-id="541fe-114">The following XML shows the \<maml:returnValues> node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="541fe-115">Aşağıdaki XML kullanmaya bir örnek gösterilmektedir \<maml:returnValues > belge bir çıkış türüne düğümü.</span><span class="sxs-lookup"><span data-stu-id="541fe-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



