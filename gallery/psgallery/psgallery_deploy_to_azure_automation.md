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
<a name="deploy-to-azure-automation"></a>Azure Otomasyonuna Dağıtma
===========================

Azure Otomasyonu button öğesi Ayrıntıları sayfasında Dağıt Azure Otomasyonu PowerShell Galerisi'nden öğesine dağıtır.

![Azure Otomasyonu düğmesine dağıtma](Images/DeployToAzureAutomationButton.png)

Tıklatıldığında, bunu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.
Öğe bağımlılıklar içeriyorsa, tüm bağımlılıkları da Azure Otomasyonu dağıtılır.

Uyarı: aynı öğe ve sürüm Otomasyon hesabınız zaten varsa PowerShell Galerisi'nden yeniden dağıtma Otomasyon hesabınızda öğenin üzerine yazılır.

Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görüntülenir.  Bir komut dosyası dağıtırsanız, Azure Automation runbook'ları bölümünde görüntülenir.

Azure Otomasyonu düğmesine dağıtma öğe meta verileri için AzureAutomationNotSupported etiketi ekleyerek devre dışı bırakılabilir.

Azure Otomasyonu hakkında daha fazla bilgi için Azure Otomasyonu Web bakın [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/services/automation/).