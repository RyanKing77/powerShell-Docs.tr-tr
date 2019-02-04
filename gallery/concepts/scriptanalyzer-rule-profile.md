---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Galeri için ScriptAnalyzer kural profili
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683859"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="4d2e4-103">Galeri için ScriptAnalyzer kural profili</span><span class="sxs-lookup"><span data-stu-id="4d2e4-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="4d2e4-104">PowerShell Galerisi'nde yayımlanmış paketleri kalitesini sağlamak için çalıştırıyoruz [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) ihlaller gönderilen komut olup olmadığını belirlemek için kuralları.</span><span class="sxs-lookup"><span data-stu-id="4d2e4-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="4d2e4-105">ScriptAnalyzer üzerinde çalışan ki kurallarının listesini bulabilirsiniz [GitHub sayfasına](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="4d2e4-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="4d2e4-106">Çalıştırılmakta olan tüm kuralları ile ilgili endişeleriniz varsa lütfen PowerShell Galerisi yöneticileri ile iletişime geçin veya ScriptAnalzyer için bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="4d2e4-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="4d2e4-107">Her sayfada tek tek Paket galerisinde gelecek sürümde ScriptAnalyzer sonuçları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4d2e4-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="4d2e4-108">Yayımlanan paketleri ciddi bir hata olmadığından emin olmak için paketlerini denetlemek için paket sahipleri öneririz.</span><span class="sxs-lookup"><span data-stu-id="4d2e4-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
