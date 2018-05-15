---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Sorun giderme cmdlet'leri
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="90c7a-103">Sorun giderme cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="90c7a-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="90c7a-104">Nasıl çözümleneceğini "Uyarı: 'paket adı,' paketi yükleyemedi" sorunu?</span><span class="sxs-lookup"><span data-stu-id="90c7a-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="90c7a-105">Modül yükleme veya güncelleştirme modülü bazen bazı makinelerde başarısız olduğunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="90c7a-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="90c7a-106">Araştırmamıza göre bunu ağ bağlantısı yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="90c7a-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="90c7a-107">Yakın zamanda, güvenilir bir şekilde paketleri indirebilmesi biz NuGet sağlayıcı güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="90c7a-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="90c7a-108">NuGet Sağlayıcısı'nın en son sürüme yükleyin ve ardından yüklemek veya modülünüzün güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90c7a-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="90c7a-109">Şimdi 'Azure' modülü bir örnek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90c7a-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```