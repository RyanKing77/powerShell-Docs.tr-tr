---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="0f2a2-103">Azure Otomasyonuna Dağıtma</span><span class="sxs-lookup"><span data-stu-id="0f2a2-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="0f2a2-104">Azure Otomasyonu button öğesi Ayrıntıları sayfasında Dağıt Azure Otomasyonu PowerShell Galerisi'nden öğesine dağıtır.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Otomasyonu düğmesine dağıtma](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="0f2a2-106">Tıklatıldığında, bunu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="0f2a2-107">Öğe bağımlılıklar içeriyorsa, tüm bağımlılıkları da Azure Otomasyonu dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="0f2a2-108">Uyarı: aynı öğe ve sürüm Otomasyon hesabınız zaten varsa PowerShell Galerisi'nden yeniden dağıtma Otomasyon hesabınızda öğenin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="0f2a2-109">Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="0f2a2-110">Bir komut dosyası dağıtırsanız, Azure Automation runbook'ları bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="0f2a2-111">Azure Otomasyonu düğmesine dağıtma öğe meta verileri için AzureAutomationNotSupported etiketi ekleyerek devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f2a2-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="0f2a2-112">Azure Otomasyonu hakkında daha fazla bilgi için Azure Otomasyonu Web bakın [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="0f2a2-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>