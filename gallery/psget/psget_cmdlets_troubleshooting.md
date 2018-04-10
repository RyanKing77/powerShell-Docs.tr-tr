---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3aea0-103">Nasıl çözümleneceğini "Uyarı: 'paket adı,' paketi yükleyemedi" sorunu?</span><span class="sxs-lookup"><span data-stu-id="3aea0-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="3aea0-104">Modül yükleme veya güncelleştirme modülü bazen bazı makinelerde başarısız olduğunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3aea0-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="3aea0-105">Araştırmamıza göre bunu ağ bağlantısı yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="3aea0-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3aea0-106">Yakın zamanda, güvenilir bir şekilde paketleri indirebilmesi biz NuGet sağlayıcı güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="3aea0-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3aea0-107">NuGet Sağlayıcısı'nın en son sürüme yükleyin ve ardından yüklemek veya modülünüzün güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aea0-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3aea0-108">Şimdi 'Azure' modülü bir örnek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aea0-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```