---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="4ff4e-102">Yeni bir GUID</span><span class="sxs-lookup"><span data-stu-id="4ff4e-102">New-Guid</span></span>
<span data-ttu-id="4ff4e-103">Genellikle komut dosyası (veya belki de DSC kaynağı yazma) benzersiz bir tanımlayıcı gerek vardır.</span><span class="sxs-lookup"><span data-stu-id="4ff4e-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="4ff4e-104">GUID'ler işe ve çağrı biri oluşturmak için .NET Framework GUID sınıfı kolaydır, ancak bir cmdlet bu ile .NET Framework sınıf tanıdık olmayan kullanıcılar için daha bulunabilmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ff4e-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="4ff4e-105">PS C:\\ &gt; yeni GUID</span><span class="sxs-lookup"><span data-stu-id="4ff4e-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="4ff4e-106">GUID</span><span class="sxs-lookup"><span data-stu-id="4ff4e-106">Guid</span></span>

----

<span data-ttu-id="4ff4e-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="4ff4e-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

