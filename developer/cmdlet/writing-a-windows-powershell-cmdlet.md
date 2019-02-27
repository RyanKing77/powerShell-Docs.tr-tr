---
title: Bir Windows PowerShell cmdlet'i yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a82aba91-71af-447d-b9ef-b6b6ac7d9de4
caps.latest.revision: 19
ms.openlocfilehash: d1abdca9ecbb5ab0a13593072e6dcb0d647b0b14
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846112"
---
# <a name="writing-a-windows-powershell-cmdlet"></a><span data-ttu-id="94c4b-102">Windows PowerShell Cmdlet’ini Yazma</span><span class="sxs-lookup"><span data-stu-id="94c4b-102">Writing a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="94c4b-103">"Bir Windows PowerShell cmdlet'i yazma" cmdlet'leri tasarlama program yöneticileri için ve cmdlet kod uygulama geliştiriciler içindir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-103">"Writing a Windows PowerShell Cmdlet" is for program managers who are designing cmdlets and for developers who are implementing cmdlet code.</span></span> <span data-ttu-id="94c4b-104">Cmdlet'leri nasıl çalıştığını anlamanıza yardımcı olur, cmdlet'leri yazmaya başlamak için kullanabileceğiniz örnek kod sağlar ve arkasındaki cmdlet kod temellerini öğrenmek için kullanabileceğiniz öğreticiler içerir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-104">It will help you understand how cmdlets work, it provides sample code that you can use to start writing cmdlets, and it includes tutorials that you can use to learn the fundamentals behind the cmdlet code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="94c4b-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94c4b-105">In This Section</span></span>

<span data-ttu-id="94c4b-106">[Cmdlet'i genel bakış](./cmdlet-overview.md) bilmeniz gereken bazı önemli koşulları ve bu konuda ne bir cmdlet'tir genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="94c4b-106">[Cmdlet Overview](./cmdlet-overview.md) This topic provides an overview of what a cmdlet is and of some important terms you need to know.</span></span>

<span data-ttu-id="94c4b-107">[Windows PowerShell cmdlet'i kavramları](./windows-powershell-cmdlet-concepts.md) Bu bölümde cmdlet'leri nedir ve nasıl çalıştıkları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="94c4b-107">[Windows PowerShell Cmdlet Concepts](./windows-powershell-cmdlet-concepts.md) This section describes what cmdlets are and how they work.</span></span>

<span data-ttu-id="94c4b-108">[Cmdlet kod örnekleri](./examples-of-cmdlet-code.md) Bu bölüm, kendi cmdlet'leri yazmaya başlamak için kullanabileceğiniz örnek kod içerir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-108">[Examples of Cmdlet Code](./examples-of-cmdlet-code.md) This section contains example code that you can use to start writing your own cmdlets.</span></span>

<span data-ttu-id="94c4b-109">[Cmdlet çıktı biçimlendirme örnekleri](https://msdn.microsoft.com/en-us/65829249-124d-47d0-9bf3-8e397dc55855) Bu bölüm, cmdlet çıktı Biçimlendirme gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-109">[Examples of Formatting Cmdlet Output](https://msdn.microsoft.com/en-us/65829249-124d-47d0-9bf3-8e397dc55855) This section contains examples that demonstrate how to format cmdlet output.</span></span>

<span data-ttu-id="94c4b-110">[Yazma cmdlet'leri için öğreticiler](./tutorials-for-writing-cmdlets.md) cmdlet kod arkasında temelleri hakkında bilgi edinmek için kullanabileceğiniz öğreticiler Bu bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-110">[Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md) This section contains tutorials that you can use to learn about the fundamentals behind the cmdlet code.</span></span>

<span data-ttu-id="94c4b-111">[Cmdlet örnekleri](./cmdlet-samples.md) Bu bölüm, tam cmdlet örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="94c4b-111">[Cmdlet Samples](./cmdlet-samples.md) This section contains samples of complete cmdlets.</span></span>

## <a name="reference"></a><span data-ttu-id="94c4b-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="94c4b-112">Reference</span></span>

[<span data-ttu-id="94c4b-113">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="94c4b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
