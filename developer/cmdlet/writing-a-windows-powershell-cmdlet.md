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
ms.openlocfilehash: 743efcf23174a9521925c5c19dd670979bc0c523
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263822"
---
# <a name="writing-a-windows-powershell-cmdlet"></a><span data-ttu-id="791f4-102">Windows PowerShell Cmdlet’ini Yazma</span><span class="sxs-lookup"><span data-stu-id="791f4-102">Writing a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="791f4-103">"Bir Windows PowerShell cmdlet'i yazma" cmdlet'leri tasarlama program yöneticileri için ve cmdlet kod uygulama geliştiriciler içindir.</span><span class="sxs-lookup"><span data-stu-id="791f4-103">"Writing a Windows PowerShell Cmdlet" is for program managers who are designing cmdlets and for developers who are implementing cmdlet code.</span></span> <span data-ttu-id="791f4-104">Cmdlet'leri nasıl çalıştığını anlamanıza yardımcı olur, cmdlet'leri yazmaya başlamak için kullanabileceğiniz örnek kod sağlar ve arkasındaki cmdlet kod temellerini öğrenmek için kullanabileceğiniz öğreticiler içerir.</span><span class="sxs-lookup"><span data-stu-id="791f4-104">It will help you understand how cmdlets work, it provides sample code that you can use to start writing cmdlets, and it includes tutorials that you can use to learn the fundamentals behind the cmdlet code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="791f4-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="791f4-105">In This Section</span></span>

<span data-ttu-id="791f4-106">[Cmdlet'i genel bakış](./cmdlet-overview.md) bilmeniz gereken bazı önemli koşulları ve bu konuda ne bir cmdlet'tir genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="791f4-106">[Cmdlet Overview](./cmdlet-overview.md) This topic provides an overview of what a cmdlet is and of some important terms you need to know.</span></span>

<span data-ttu-id="791f4-107">[Windows PowerShell cmdlet'i kavramları](./windows-powershell-cmdlet-concepts.md) Bu bölümde cmdlet'leri nedir ve nasıl çalıştıkları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="791f4-107">[Windows PowerShell Cmdlet Concepts](./windows-powershell-cmdlet-concepts.md) This section describes what cmdlets are and how they work.</span></span>

<span data-ttu-id="791f4-108">[Cmdlet kod örnekleri](./examples-of-cmdlet-code.md) Bu bölüm, kendi cmdlet'leri yazmaya başlamak için kullanabileceğiniz örnek kod içerir.</span><span class="sxs-lookup"><span data-stu-id="791f4-108">[Examples of Cmdlet Code](./examples-of-cmdlet-code.md) This section contains example code that you can use to start writing your own cmdlets.</span></span>

<span data-ttu-id="791f4-109">[Cmdlet çıkışı için biçimlendirme dosyaları yazma](../format/writing-a-powershell-formatting-file.md) Bu bölümde biçimlendirme dosyalarının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="791f4-109">[Writing Formatting Files for Cmdlet Output](../format/writing-a-powershell-formatting-file.md) This section describe how to create formatting files.</span></span> <span data-ttu-id="791f4-110">Biçimlendirme dosyaları, PowerShell komut satırında nesneleri biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="791f4-110">Formatting files define how PowerShell displays objects at the command line.</span></span>

<span data-ttu-id="791f4-111">[Yazma cmdlet'leri için öğreticiler](./tutorials-for-writing-cmdlets.md) cmdlet kod arkasında temelleri hakkında bilgi edinmek için kullanabileceğiniz öğreticiler Bu bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="791f4-111">[Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md) This section contains tutorials that you can use to learn about the fundamentals behind the cmdlet code.</span></span>

<span data-ttu-id="791f4-112">[Cmdlet örnekleri](./cmdlet-samples.md) Bu bölüm, tam cmdlet örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="791f4-112">[Cmdlet Samples](./cmdlet-samples.md) This section contains samples of complete cmdlets.</span></span>

## <a name="reference"></a><span data-ttu-id="791f4-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="791f4-113">Reference</span></span>

[<span data-ttu-id="791f4-114">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="791f4-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
