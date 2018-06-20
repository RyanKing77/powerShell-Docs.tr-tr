---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kaynakları
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219819"
---
# <a name="dsc-resources"></a><span data-ttu-id="b24a1-103">DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="b24a1-103">DSC Resources</span></span>

><span data-ttu-id="b24a1-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b24a1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b24a1-105">İstenen durum Yapılandırması'nı (DSC) kaynaklar, DSC yapılandırması için yapı taşlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b24a1-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="b24a1-106">Bir kaynak yapılandırılmış (şema) olabilir ve "Bunu yapmak için" yerel Configuration Manager (LCM'yi) çağıran PowerShell Betiği işlevleri içeren özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="b24a1-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="b24a1-107">Bir kaynak olarak bir dosya olarak genel veya bir IIS sunucu ayarı olarak belirli bir şey model oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b24a1-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="b24a1-108">Grupları, kaynaklar gibi tüm gerekli dosyaları, taşınabilir ve nasıl kullanılmaya kaynaklara yönelik tanımlamak için meta verileri içeren bir yapı düzenler bir DSC modülü, birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b24a1-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="b24a1-109">Aşağıdaki konularda, DSC kaynakları açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b24a1-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="b24a1-110">Yerleşik DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="b24a1-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="b24a1-111">Özel DSC kaynakları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b24a1-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="b24a1-112">Linux için yerleşik DSC kaynakları</span><span class="sxs-lookup"><span data-stu-id="b24a1-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)