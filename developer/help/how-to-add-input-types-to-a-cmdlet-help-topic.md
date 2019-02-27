---
title: Bir Cmdlet Yardım konusuna giriş türleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850179"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="8bc5b-102">Cmdlet Yardım Konusuna Giriş Türleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="8bc5b-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="8bc5b-103">Bu bölümde, bir giriş bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="8bc5b-104">Giriş bölümü, değer veya özellik adı cmdlet işlem hattından girdi olarak kabul eden nesneler .NET sınıflarını listeler.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="8bc5b-105">Bir giriş bölümüne ekleyebilirsiniz sınıfları sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="8bc5b-106">Giriş türleri içine alınan bir \<komutu: inputTypes > düğümle içine her sınıfın bir \<komutu: Inputtype > öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="8bc5b-107">Şema iki içerir \<maml:description > her öğeleri \<komutu: Inputtype > öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="8bc5b-108">Ancak, `Get-Help` cmdlet'i yalnızca içeriğini görüntüler \<komutu: Inputtype > /\<maml:description >) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="8bc5b-109">Windows PowerShell 3. 0'den itibaren `Get-Help` cmdlet içeriğini görüntüler \<maml:uri > öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="8bc5b-110">Bu öğe, .NET sınıf açıklayan konulara kullanıcıları doğrudan sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="8bc5b-111">Aşağıdaki XML gösterildiği \<maml:inputTypes > düğümü.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-111">The following XML shows the \<maml:inputTypes> node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="8bc5b-112">Aşağıdaki XML kullanmaya bir örnek gösterilmektedir \<maml:inputTypes > belge bir giriş türü için düğüm.</span><span class="sxs-lookup"><span data-stu-id="8bc5b-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```