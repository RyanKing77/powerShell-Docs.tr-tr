---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="d35fb-102">Sınıf tabanlı DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="d35fb-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="d35fb-103">DSC kaynakları ile sınıfları tanımlama</span><span class="sxs-lookup"><span data-stu-id="d35fb-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="d35fb-104">Geri bildirimi doğrultusunda, sınıf tabanlı DSC kaynakları daha basit ve anlaşılması daha kolay geliştirme yaptık.</span><span class="sxs-lookup"><span data-stu-id="d35fb-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="d35fb-105">Bir sınıf tabanlı DSC kaynağı bir cmdlet DSC kaynak sağlayıcısı arasındaki temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d35fb-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="d35fb-106">MOF dosyası şeması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d35fb-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="d35fb-107">A **DSCResource** modül klasöründe alt gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d35fb-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="d35fb-108">PowerShell modülü dosyası birden çok DSC kaynağı sınıfları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d35fb-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="d35fb-109">Daha fazla bilgi için bkz: [PowerShell sınıfları içeren özel bir DSC kaynağı yazma](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="d35fb-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

