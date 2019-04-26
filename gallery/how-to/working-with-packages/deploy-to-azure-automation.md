---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Azure Otomasyonuna Dağıtma
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084903"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="fd385-103">Azure Otomasyonuna Dağıtma</span><span class="sxs-lookup"><span data-stu-id="fd385-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="fd385-104">Azure Otomasyonu düğmesine Paket Ayrıntıları sayfasındaki dağıtma, Azure Otomasyonu PowerShell Galerisi'ndeki paketi dağıtır.</span><span class="sxs-lookup"><span data-stu-id="fd385-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Otomasyonu düğmeye dağıtma](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="fd385-106">Tıklandığında, bu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fd385-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="fd385-107">Tüm bağımlılıkları paketin bağımlılıklar içeriyorsa, Azure Otomasyonu de dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="fd385-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="fd385-108">PowerShell Galerisi'nden yeniden dağıtım paketi Otomasyon hesabınızdaki aynı Paket sürümü ve Otomasyon hesabınız zaten varsa üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="fd385-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="fd385-109">Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="fd385-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="fd385-110">Bir betik dağıtırsanız, Azure Otomasyonu runbook'ları bölümünde görünür.</span><span class="sxs-lookup"><span data-stu-id="fd385-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="fd385-111">Paket meta verileri AzureAutomationNotSupported etiketi ekleyerek Azure Otomasyonu düğmesi Dağıt devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd385-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="fd385-112">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="fd385-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="fd385-113">Azure Otomasyonu dağıtılan modül lisans kabulü gerektiriyorsa, portalı kullanıcı arabirimini sorumluluk reddi bildiren gösterecektir ' Bu modül lisans kabulü gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="fd385-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="fd385-114">Tamam'a tıklayarak lisans koşullarını kabul edersiniz.'</span><span class="sxs-lookup"><span data-stu-id="fd385-114">By clicking OK, you are accepting license terms.'</span></span>

![Azure'a dağıtma Otomasyon lisans kabulü gerektiriyor](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="fd385-116">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="fd385-116">More details</span></span>

- [<span data-ttu-id="fd385-117">PowerShellGet, lisans kabulü gerektir</span><span class="sxs-lookup"><span data-stu-id="fd385-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="fd385-118">PowerShell galerisinde lisans kabulü gerektir</span><span class="sxs-lookup"><span data-stu-id="fd385-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="fd385-119">Azure Otomasyonu Web sitesi</span><span class="sxs-lookup"><span data-stu-id="fd385-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
