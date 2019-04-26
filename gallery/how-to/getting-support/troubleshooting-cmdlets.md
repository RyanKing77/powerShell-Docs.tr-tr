---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084190"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="757f7-103">Sorun giderme cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="757f7-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="757f7-104">Nasıl çözümleneceğini "Uyarı: Paket 'paket adı' karşıdan yüklenemedi"sorun</span><span class="sxs-lookup"><span data-stu-id="757f7-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="757f7-105">Bu rapor, `Install-Module` veya `Update-Module` bazen bazı makinelerde başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="757f7-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="757f7-106">Araştırmamıza göre bunu ağ bağlantısı ile yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="757f7-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="757f7-107">Güvenilir bir şekilde paketleri indirebilmeniz en son NuGet sağlayıcısı güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="757f7-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="757f7-108">NuGet sağlayıcısı en son derlemesini yüklemek ve yüklemeyi veya modülünüzde güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="757f7-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="757f7-109">Şimdi 'Azure' modülü bir örnek olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="757f7-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
