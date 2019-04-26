---
title: Cmdlet kod öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068700"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="cc85b-102">Cmdlet Kodunda Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc85b-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="cc85b-103">Windows PowerShell tarafından sağlanan ortak işlevselliği kullanmak için cmdlet kod içinde tanımlanan ortak özellikler ve sınıfların öznitelikleri ile donatılmış.</span><span class="sxs-lookup"><span data-stu-id="cc85b-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="cc85b-104">Örneğin, aşağıdaki sınıf tanımını Microsoft .NET Framework sınıfında tanımlamak için Cmdlet özniteliğini kullanır **Get-Proc** cmdlet'i uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cc85b-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="cc85b-105">(Bu cmdlet, bu belgedeki bir örnek olarak kullanılır ve benzer `Get-Process` cmdlet'inin Windows PowerShell tarafından sağlanan.)</span><span class="sxs-lookup"><span data-stu-id="cc85b-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="cc85b-106">Bu öznitelikler, geliştirdikleri cmdlet kod uygulamadan ayrı olduğundan meta veriler olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="cc85b-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="cc85b-107">Çalışma zamanı Windows PowerShell cmdlet çalıştırıldığında, öznitelikleri algılar ve ardından her öznitelik için uygun eylemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cc85b-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="cc85b-108">Kendi sürümü bu öznitelikler tarafından sağlanan işlevselliği uygulamak isteyebilirsiniz ancak bu ortak işlevler iyi cmdlet'i tasarım kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc85b-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="cc85b-109">Cmdlet'lerinizi içinde bildirilebilir farklı öznitelikleri hakkında daha fazla bilgi için bkz. [öznitelik türlerini](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc85b-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc85b-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="cc85b-110">See Also</span></span>

[<span data-ttu-id="cc85b-111">Öznitelik türleri</span><span class="sxs-lookup"><span data-stu-id="cc85b-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="cc85b-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="cc85b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
