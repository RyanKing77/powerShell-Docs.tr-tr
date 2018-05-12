---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeri, powershell, cmdlet, psgallery
title: Azure Otomasyonuna Dağıtma
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a>Azure Otomasyonuna Dağıtma

Azure Otomasyonu button öğesi Ayrıntıları sayfasında Dağıt Azure Otomasyonu PowerShell Galerisi'nden öğesine dağıtır.

![Azure Otomasyonu düğmesine dağıtma](../../Images/DeployToAzureAutomationButton.png)

Tıklatıldığında, bunu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.
Öğe bağımlılıklar içeriyorsa, tüm bağımlılıkları da Azure Otomasyonu dağıtılır.

> [!WARNING]
> PowerShell Galerisi'nden yeniden dağıtma, aynı öğe ve sürüm Automation hesabınız zaten varsa, Otomasyon hesabınızda öğenin üzerine yazılır.

Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görüntülenir.  Bir komut dosyası dağıtırsanız, Azure Automation runbook'ları bölümünde görüntülenir.

Azure Otomasyonu düğmesine dağıtma öğe meta verileri için AzureAutomationNotSupported etiketi ekleyerek devre dışı bırakılabilir.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir

Azure Otomasyonu dağıtılan modül lisans kabulünü gerektiriyorsa, portal UI sorumluluk reddi bildiren Göster ' Bu modül lisans kabulünü gereklidir. Tamam'ı tıklatarak, lisans koşullarını kabul ediyorsunuz.'

![Azure'a dağıtma Otomasyon lisans kabulünü gerektirir](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Daha fazla ayrıntı

- [Lisans kabulünü PowerShellGet içinde gerektirir](../../concepts/module-license-acceptance.md)
- [Lisans kabulünü PowerShell galerisinde gerektirir](items-that-require-license-acceptance.md)
- [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/services/automation/)
