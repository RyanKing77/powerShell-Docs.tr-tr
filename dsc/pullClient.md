---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC çekme istemci ayarlama"
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="ee9d4-103">DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee9d4-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="ee9d4-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ee9d4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ee9d4-105">Çekme modunu kullanacak şekilde söylediyse ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucunun başvurabilirsiniz ve rapor verilerini göndermelisiniz burada verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ee9d4-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="ee9d4-106">Aşağıdaki konularda, çekme istemcilerini ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ee9d4-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="ee9d4-107">Yapılandırma adlarını kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee9d4-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="ee9d4-108">Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee9d4-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="ee9d4-109">**Not**: Bu konular PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ee9d4-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="ee9d4-110">Çekme istemci PowerShell 4. 0 olarak ayarlamak için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="ee9d4-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

