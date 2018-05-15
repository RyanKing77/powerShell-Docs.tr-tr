---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Azure Otomasyonuna Dağıtma
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="0f31e-103">Azure Otomasyonuna Dağıtma</span><span class="sxs-lookup"><span data-stu-id="0f31e-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="0f31e-104">Azure Otomasyonu button öğesi Ayrıntıları sayfasında Dağıt Azure Otomasyonu PowerShell Galerisi'nden öğesine dağıtır.</span><span class="sxs-lookup"><span data-stu-id="0f31e-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Otomasyonu düğmesine dağıtma](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="0f31e-106">Tıklatıldığında, bunu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="0f31e-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="0f31e-107">Öğe bağımlılıklar içeriyorsa, tüm bağımlılıkları da Azure Otomasyonu dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="0f31e-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="0f31e-108">PowerShell Galerisi'nden yeniden dağıtma, aynı öğe ve sürüm Automation hesabınız zaten varsa, Otomasyon hesabınızda öğenin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="0f31e-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="0f31e-109">Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f31e-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="0f31e-110">Bir komut dosyası dağıtırsanız, Azure Automation runbook'ları bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f31e-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="0f31e-111">Azure Otomasyonu düğmesine dağıtma öğe meta verileri için AzureAutomationNotSupported etiketi ekleyerek devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f31e-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="0f31e-112">Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir</span><span class="sxs-lookup"><span data-stu-id="0f31e-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="0f31e-113">Azure Otomasyonu dağıtılan modül lisans kabulünü gerektiriyorsa, portal UI sorumluluk reddi bildiren Göster ' Bu modül lisans kabulünü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0f31e-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="0f31e-114">Tamam'ı tıklatarak, lisans koşullarını kabul ediyorsunuz.'</span><span class="sxs-lookup"><span data-stu-id="0f31e-114">By clicking OK, you are accepting license terms.'</span></span>

![Azure'a dağıtma Otomasyon lisans kabulünü gerektirir](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="0f31e-116">Daha fazla ayrıntı</span><span class="sxs-lookup"><span data-stu-id="0f31e-116">More details</span></span>

- [<span data-ttu-id="0f31e-117">Lisans kabulünü PowerShellGet içinde gerektirir</span><span class="sxs-lookup"><span data-stu-id="0f31e-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="0f31e-118">Lisans kabulünü PowerShell galerisinde gerektirir</span><span class="sxs-lookup"><span data-stu-id="0f31e-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="0f31e-119">Azure Otomasyonu Web sitesi</span><span class="sxs-lookup"><span data-stu-id="0f31e-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)