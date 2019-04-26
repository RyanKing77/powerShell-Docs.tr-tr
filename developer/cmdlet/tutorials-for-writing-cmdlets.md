---
title: Cmdlet'leri yazmak için öğreticiler | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0b548aa-febf-45dd-bf71-2077730b9b73
caps.latest.revision: 6
ms.openlocfilehash: 767b392bd1603e83d80bad5b3fd9cb42ff142ce6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067255"
---
# <a name="tutorials-for-writing-cmdlets"></a><span data-ttu-id="d9b5d-102">Cmdlet Yazma Öğreticileri</span><span class="sxs-lookup"><span data-stu-id="d9b5d-102">Tutorials for Writing Cmdlets</span></span>

<span data-ttu-id="d9b5d-103">Bu bölüm, cmdlet'leri yazmak için öğreticiler içerir.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-103">This section contains tutorials for writing cmdlets.</span></span> <span data-ttu-id="d9b5d-104">Bu öğreticiler cmdlet'lerin yanı sıra, kod neden gereklidir açıklama yazmak için gerekli kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-104">These tutorials include the code needed to write the cmdlets, plus an explanation of why the code is needed.</span></span> <span data-ttu-id="d9b5d-105">Bu konu başlıkları cmdlet'leri yazmak için yeni başlayan olanlar için çok yararlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-105">These topics will be very helpful for those who are just starting to write cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9b5d-106">İsteyenler için daha az açıklama ile kod örnekleri, bkz: [Cmdlet örnekleri](./cmdlet-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d9b5d-106">For those who want code examples with less description, see [Cmdlet Samples](./cmdlet-samples.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d9b5d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d9b5d-107">In This Section</span></span>

<span data-ttu-id="d9b5d-108">[GetProc öğretici](./getproc-tutorial.md) -Bu öğreticide, bir cmdlet'i sınıf tanımlamak ve parametreler ekleme ve hata raporlama gibi temel işlevler eklemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-108">[GetProc Tutorial](./getproc-tutorial.md) - This tutorial describes how to define a cmdlet class and add basic functionality such as adding parameters and reporting errors.</span></span> <span data-ttu-id="d9b5d-109">Bu eğiticide açıklananlarla cmdlet'e çok benzer [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-109">The cmdlet described in this tutorial is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="d9b5d-110">[StopProc öğretici](./stopproc-tutorial.md) - Bu öğreticide, bir cmdlet tanımlamak ve kullanıcı komut istemleri, joker karakter desteği gibi işlev eklemek açıklar ve parametre kullanımı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-110">[StopProc Tutorial](./stopproc-tutorial.md) - This tutorial describes how to define a cmdlet and add functionality such as user prompts, wildcard support, and the use of parameter sets.</span></span> <span data-ttu-id="d9b5d-111">Burada açıklanan cmdlet aynı görevi gerçekleştirir [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-111">The cmdlet described here performs the same task as the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="d9b5d-112">[SelectStr öğretici](./selectstr-tutorial.md) -Bu öğreticide bir veri deposu erişen bir cmdlet tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-112">[SelectStr Tutorial](./selectstr-tutorial.md) - This tutorial describes how to define a cmdlet that accesses a data store.</span></span> <span data-ttu-id="d9b5d-113">Burada açıklanan cmdlet aynı görevi gerçekleştirir [seçin dize](/powershell/module/microsoft.powershell.utility/select-string) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d9b5d-113">The cmdlet described here performs the same task as the [Select-String](/powershell/module/microsoft.powershell.utility/select-string) cmdlet provided by Windows PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9b5d-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d9b5d-114">See Also</span></span>

[<span data-ttu-id="d9b5d-115">GetProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="d9b5d-115">GetProc Tutorial</span></span>](./getproc-tutorial.md)

[<span data-ttu-id="d9b5d-116">StopProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="d9b5d-116">StopProc Tutorial</span></span>](./stopproc-tutorial.md)

[<span data-ttu-id="d9b5d-117">SelectStr Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="d9b5d-117">SelectStr Tutorial</span></span>](./selectstr-tutorial.md)

[<span data-ttu-id="d9b5d-118">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="d9b5d-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
