---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225598"
---
# <a name="new-guid"></a><span data-ttu-id="0d8e8-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="0d8e8-102">New-Guid</span></span>
<span data-ttu-id="0d8e8-103">Genellikle komut dosyası (veya belki de DSC kaynağı yazma) benzersiz bir tanımlayıcı gerek vardır.</span><span class="sxs-lookup"><span data-stu-id="0d8e8-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="0d8e8-104">GUID'ler işe ve çağrı biri oluşturmak için .NET Framework GUID sınıfı kolaydır, ancak bir cmdlet bu ile .NET Framework sınıf tanıdık olmayan kullanıcılar için daha bulunabilmesini sağlar:</span><span class="sxs-lookup"><span data-stu-id="0d8e8-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="0d8e8-105">PS C:\\ &gt; yeni GUID</span><span class="sxs-lookup"><span data-stu-id="0d8e8-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="0d8e8-106">GUID</span><span class="sxs-lookup"><span data-stu-id="0d8e8-106">Guid</span></span>

----

<span data-ttu-id="0d8e8-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="0d8e8-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
