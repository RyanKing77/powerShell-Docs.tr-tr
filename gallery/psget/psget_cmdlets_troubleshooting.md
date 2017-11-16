---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="362b4-103">Nasıl çözümleneceğini "Uyarı: 'paket adı,' paketi yükleyemedi" sorunu?</span><span class="sxs-lookup"><span data-stu-id="362b4-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="362b4-104">Modül yükleme veya güncelleştirme modülü bazen bazı makinelerde başarısız olduğunu bildirilir.</span><span class="sxs-lookup"><span data-stu-id="362b4-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="362b4-105">Araştırmamıza göre bunu ağ bağlantısı yapmak için bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="362b4-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="362b4-106">Yakın zamanda, güvenilir bir şekilde paketleri indirebilmesi biz NuGet sağlayıcı güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="362b4-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="362b4-107">NuGet Sağlayıcısı'nın en son sürüme yükleyin ve ardından yüklemek veya modülünüzün güncelleştirmek için aşağıdaki yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="362b4-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="362b4-108">Şimdi 'Azure' modülü bir örnek olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="362b4-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

