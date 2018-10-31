---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery
title: Azure Otomasyonuna Dağıtma
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004140"
---
# <a name="deploy-to-azure-automation"></a>Azure Otomasyonuna Dağıtma

Azure Otomasyonu düğmesine Paket Ayrıntıları sayfasındaki dağıtma, Azure Otomasyonu PowerShell Galerisi'ndeki paketi dağıtır.

![Azure Otomasyonu düğmeye dağıtma](../../Images/DeployToAzureAutomationButton.png)

Tıklandığında, bu, burada Azure hesabı kimlik bilgilerinizi kullanarak oturum Azure yönetim portalına yönlendirir.
Tüm bağımlılıkları paketin bağımlılıklar içeriyorsa, Azure Otomasyonu de dağıtılır.

> [!WARNING]
> PowerShell Galerisi'nden yeniden dağıtım paketi Otomasyon hesabınızdaki aynı Paket sürümü ve Otomasyon hesabınız zaten varsa üzerine yazar.

Bir modül dağıtırsanız, Azure Automation modülleri bölümünde görünür.  Bir betik dağıtırsanız, Azure Otomasyonu runbook'ları bölümünde görünür.

Paket meta verileri AzureAutomationNotSupported etiketi ekleyerek Azure Otomasyonu düğmesi Dağıt devre dışı bırakılabilir.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Azure Otomasyonuna Dağıtmada Lisans Kabulü Gerektir

Azure Otomasyonu dağıtılan modül lisans kabulü gerektiriyorsa, portalı kullanıcı arabirimini sorumluluk reddi bildiren gösterecektir ' Bu modül lisans kabulü gerektiriyor. Tamam'a tıklayarak lisans koşullarını kabul edersiniz.'

![Azure'a dağıtma Otomasyon lisans kabulü gerektiriyor](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Daha fazla ayrıntı

- [PowerShellGet, lisans kabulü gerektir](../../concepts/module-license-acceptance.md)
- [PowerShell galerisinde lisans kabulü gerektir](packages-that-require-license-acceptance.md)
- [Azure Otomasyonu Web sitesi](http://azure.microsoft.com/services/automation/)
