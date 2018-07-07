---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892483"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="3ede4-103">Sorun giderme cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="3ede4-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3ede4-104">Nasıl çözümleneceğini "Uyarı: ', paket adı' paket başarısız indirmek" sorun</span><span class="sxs-lookup"><span data-stu-id="3ede4-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="3ede4-105">Bu rapor, `Install-Module` veya `Update-Module` bazen bazı makinelerde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3ede4-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="3ede4-106">Araştırmamıza göre bunu ağ bağlantısı ile yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="3ede4-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3ede4-107">Güvenilir bir şekilde paketleri indirebilmeniz en son NuGet sağlayıcısı güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="3ede4-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3ede4-108">NuGet sağlayıcısı en son derlemesini yüklemek ve yüklemeyi veya modülünüzde güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ede4-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3ede4-109">Şimdi 'Azure' modülü bir örnek olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ede4-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```