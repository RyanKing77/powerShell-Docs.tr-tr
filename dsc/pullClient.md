---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC çekme istemci ayarlama"
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="f2da1-103">DSC çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="f2da1-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="f2da1-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f2da1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f2da1-105">Çekme modunu kullanacak şekilde söylediyse ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucunun başvurabilirsiniz ve rapor verilerini göndermelisiniz burada verilen her hedef düğüme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f2da1-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="f2da1-106">Aşağıdaki konularda, çekme istemcilerini ayarlama açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f2da1-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="f2da1-107">Yapılandırma adları kullanarak bir çekme istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="f2da1-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="f2da1-108">Yapılandırma kimliği kullanan bir çekme istemci ayarlama</span><span class="sxs-lookup"><span data-stu-id="f2da1-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="f2da1-109">**Not**: Bu konular PowerShell 5.0 için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f2da1-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="f2da1-110">Çekme istemci PowerShell 4. 0 olarak ayarlamak için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="f2da1-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

