---
title: Windows PowerShell02 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082524"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="9d48e-102">Windows PowerShell02 Örneği</span><span class="sxs-lookup"><span data-stu-id="9d48e-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="9d48e-103">Bu örnek, bir çalışma alanı havuzunun çalışma alanlarını kullanarak zaman uyumsuz olarak komutları çalıştırmayı öğrenin gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d48e-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="9d48e-104">Örnek komutların bir listesini oluşturur ve gerektiğinde Windows PowerShell altyapısı havuzdan bir çalışma alanı açılırken komutları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d48e-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d48e-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d48e-105">Requirements</span></span>

- <span data-ttu-id="9d48e-106">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d48e-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9d48e-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="9d48e-107">Demonstrates</span></span>

<span data-ttu-id="9d48e-108">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="9d48e-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="9d48e-109">Çalışma alanları aynı zamanda açık izin verilen minimum ve Maksimum sayıda RunspacePool nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9d48e-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="9d48e-110">Komutların listesini oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9d48e-110">Creating a list of commands.</span></span>

- <span data-ttu-id="9d48e-111">Komutlar zaman uyumsuz olarak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="9d48e-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="9d48e-112">Çağırma [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) ücretsiz kaç çalışma alanlarını görmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d48e-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="9d48e-113">Komut çıktısı ile yakalama [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d48e-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="9d48e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d48e-114">Example</span></span>

<span data-ttu-id="9d48e-115">Bu örnek nasıl açılacağını çalışma havuzun çalışma alanları ve komutlar bu çalışma alanlarında zaman uyumsuz olarak çalıştırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d48e-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="9d48e-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9d48e-116">See Also</span></span>

[<span data-ttu-id="9d48e-117">Bir Windows PowerShell ana bilgisayar uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="9d48e-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)