---
title: Çalışma alanları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848149"
---
# <a name="creating-runspaces"></a><span data-ttu-id="ba8f5-102">Çalışma Alanları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba8f5-102">Creating Runspaces</span></span>

<span data-ttu-id="ba8f5-103">Bir çalışma alanı bir ana bilgisayar uygulaması tarafından çağrılan komutları için işletim ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="ba8f5-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="ba8f5-104">Bu ortam, komutlar ve şu anda mevcut olan verileri şu anda uygulanan herhangi bir dil kısıtlama içerir.</span><span class="sxs-lookup"><span data-stu-id="ba8f5-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="ba8f5-105">Uygulamaları barındırmak tüm kullanılabilir çekirdek komutlar içeren Windows PowerShell tarafından sağlanan varsayılan çalışma alanı kullanabilir veya yalnızca bir alt kümesini kullanılabilir komutları içeren özel bir çalışma alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba8f5-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="ba8f5-106">Özelleştirilmiş bir çalışma alanı oluşturmak için oluşturduğunuz bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne ve, bir çalışma atayın.</span><span class="sxs-lookup"><span data-stu-id="ba8f5-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="ba8f5-107">Çalışma alanı görevleri</span><span class="sxs-lookup"><span data-stu-id="ba8f5-107">Runspace tasks</span></span>

1. [<span data-ttu-id="ba8f5-108">Bir InitialSessionState oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba8f5-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="ba8f5-109">Kısıtlı bir çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba8f5-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="ba8f5-110">Birden çok çalışma alanları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba8f5-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="ba8f5-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ba8f5-111">See Also</span></span>
