---
ms.date: 06/12/2017
contributor: manikb
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219836"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="da93c-103">Sorun giderme cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="da93c-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="da93c-104">Nasıl çözümleneceğini "Uyarı: 'paket adı,' paketi yükleyemedi" sorunu?</span><span class="sxs-lookup"><span data-stu-id="da93c-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="da93c-105">Modül yükleme veya güncelleştirme modülü bazen bazı makinelerde başarısız olduğunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="da93c-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="da93c-106">Araştırmamıza göre bunu ağ bağlantısı yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="da93c-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="da93c-107">Yakın zamanda, güvenilir bir şekilde paketleri indirebilmesi biz NuGet sağlayıcı güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="da93c-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="da93c-108">NuGet Sağlayıcısı'nın en son sürüme yükleyin ve ardından yüklemek veya modülünüzün güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da93c-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="da93c-109">Şimdi 'Azure' modülü bir örnek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da93c-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```