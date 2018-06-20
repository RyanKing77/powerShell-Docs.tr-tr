---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC çekme istemci ayarlama
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186669"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="8ac5e-103">DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ac5e-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="8ac5e-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8ac5e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ac5e-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="8ac5e-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8ac5e-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="8ac5e-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8ac5e-107">Çekme modunu kullanacak şekilde söylediyse ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucunun başvurabilirsiniz ve rapor verilerini göndermelisiniz burada verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8ac5e-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="8ac5e-108">Aşağıdaki konularda, çekme istemcilerini ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="8ac5e-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="8ac5e-109">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ac5e-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="8ac5e-110">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="8ac5e-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="8ac5e-111">**Not**: Bu konular PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8ac5e-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="8ac5e-112">Çekme istemci PowerShell 4. 0 olarak ayarlamak için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="8ac5e-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>