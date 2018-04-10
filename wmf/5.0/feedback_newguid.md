---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="beb61-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="beb61-102">New-Guid</span></span>
<span data-ttu-id="beb61-103">Genellikle komut dosyası (veya belki de DSC kaynağı yazma) benzersiz bir tanımlayıcı gerek vardır.</span><span class="sxs-lookup"><span data-stu-id="beb61-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="beb61-104">GUID'ler işe ve çağrı biri oluşturmak için .NET Framework GUID sınıfı kolaydır, ancak bir cmdlet bu ile .NET Framework sınıf tanıdık olmayan kullanıcılar için daha bulunabilmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="beb61-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="beb61-105">PS C:\\ &gt; yeni GUID</span><span class="sxs-lookup"><span data-stu-id="beb61-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="beb61-106">GUID</span><span class="sxs-lookup"><span data-stu-id="beb61-106">Guid</span></span>

----

<span data-ttu-id="beb61-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="beb61-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>