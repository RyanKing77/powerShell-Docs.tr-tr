---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="b1c53-103">Azure Automation'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="b1c53-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="b1c53-104">Azure Otomasyonu button öğesi Ayrıntıları sayfasında Dağıt Azure Otomasyonu PowerShell Galerisi'nden öğesine dağıtır.</span><span class="sxs-lookup"><span data-stu-id="b1c53-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Azure Otomasyonu düğmesine dağıtma](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="b1c53-106">Tıklatıldığında, bunu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="b1c53-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="b1c53-107">Öğe bağımlılıklar içeriyorsa, tüm bağımlılıkları da Azure Otomasyonu dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="b1c53-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="b1c53-108">Uyarı: aynı öğe ve sürüm Otomasyon hesabınız zaten varsa PowerShell Galerisi'nden yeniden dağıtma Otomasyon hesabınızda öğenin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="b1c53-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="b1c53-109">Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b1c53-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="b1c53-110">Bir komut dosyası dağıtırsanız, Azure Automation runbook'ları bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b1c53-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="b1c53-111">Azure Otomasyonu düğmesine dağıtma öğe meta verileri için AzureAutomationNotSupported etiketi ekleyerek devre dışı bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="b1c53-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="b1c53-112">Azure Otomasyonu hakkında daha fazla bilgi için Azure Otomasyonu Web bakın [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="b1c53-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

