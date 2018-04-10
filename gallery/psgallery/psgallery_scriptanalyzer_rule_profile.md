---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="246ed-103">Galeri için ScriptAnazlyer kural profili</span><span class="sxs-lookup"><span data-stu-id="246ed-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="246ed-104">PowerShell Galerisi yayımlanan öğeleri kalitesini emin olmak için çalıştıracağımız [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) gönderilen komut dosyalarında herhangi bir ihlal olup olmadığını belirlemek için kurallar.</span><span class="sxs-lookup"><span data-stu-id="246ed-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="246ed-105">ScriptAnalyzer üzerinde çalışan biz kuralları listesini bulabilirsiniz [GitHub sayfası](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="246ed-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="246ed-106">Çalıştırılmakta olan tüm kuralları ile ilgili endişeleriniz varsa lütfen PowerShell Galerisi yöneticileri ile iletişime geçin veya ScriptAnalzyer için bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="246ed-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="246ed-107">Her sayfada tek bir öğe galerisinde gelecek sürümünde ScriptAnalyzer sonuçları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="246ed-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="246ed-108">Yayınlanan öğeler ciddi hatalar yoktur emin olmak için kendi öğeleri denetlemek için öğesi sahiplerinin öneririz.</span><span class="sxs-lookup"><span data-stu-id="246ed-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>