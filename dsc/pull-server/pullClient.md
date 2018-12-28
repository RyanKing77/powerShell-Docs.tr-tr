---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC çekme istemcisi ayarlama
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405685"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="9dbd7-103">DSC çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9dbd7-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="9dbd7-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9dbd7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dbd7-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="9dbd7-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="9dbd7-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="9dbd7-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="9dbd7-107">Çekme modu kullanmak için bir uyarıyla ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucusu başvurabilir ve raporu verileri gönderip burada verilen her hedef düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="9dbd7-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="9dbd7-108">Aşağıdaki konular, çekme istemcilerini ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="9dbd7-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="9dbd7-109">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9dbd7-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="9dbd7-110">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9dbd7-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="9dbd7-111">**Not**: Bu konular, PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9dbd7-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="9dbd7-112">PowerShell 4.0 çekme istemcisi ayarlama hakkında bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="9dbd7-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>