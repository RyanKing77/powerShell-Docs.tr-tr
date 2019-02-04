---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galeri, powershell, psgallery
title: Lisans kabulü gerektir
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684139"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="bf941-103">Lisans kabulü gerektir</span><span class="sxs-lookup"><span data-stu-id="bf941-103">Require license acceptance</span></span>

<span data-ttu-id="bf941-104">Öğe Ayrıntıları sayfasında lisans kabulü gerektiren modüller için lisans kabulü metin gösterilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf941-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="bf941-105">'Görünüm License.txt' bağlantısına tıklayarak lisans modülü için görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf941-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Lisans kabulü gerektir](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="bf941-107">Kullanıcılar, yükleme, kaydetme veya Azure Otomasyonu'na ekleme dağıtırken veya aracılığıyla PowerShellGet modülü güncelleştirme lisansını kabul etmek için istenir.</span><span class="sxs-lookup"><span data-stu-id="bf941-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="bf941-108">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="bf941-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="bf941-109">Azure Otomasyonu dağıtılan modül lisans kabulü gerektiriyorsa, portalı kullanıcı arabirimini sorumluluk reddi bildiren gösterecektir ' Bu modül lisans kabulü gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="bf941-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="bf941-110">Tamam'a tıklayarak lisans koşullarını kabul edersiniz.'</span><span class="sxs-lookup"><span data-stu-id="bf941-110">By clicking OK, you are accepting license terms.'</span></span>

![Azure'a dağıtma Otomasyon lisans kabulü gerektiriyor](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="bf941-112">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="bf941-112">More details</span></span>

<span data-ttu-id="bf941-113">[PowerShellGet, lisans kabulü gerektir](../../concepts/module-license-acceptance.md)
[Azure Otomasyonu Web sitesi](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="bf941-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
