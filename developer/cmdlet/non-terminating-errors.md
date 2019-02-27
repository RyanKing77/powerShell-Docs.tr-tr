---
title: Sonlandırıcı olmayan hatalar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845258"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="7bb22-102">Sonlandırıcı Olmayan Hatalar</span><span class="sxs-lookup"><span data-stu-id="7bb22-102">Non-Terminating Errors</span></span>

<span data-ttu-id="7bb22-103">Bu konuda, sonlandırıcı olmayan hatalara bildirmek için kullanılan yöntem anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bb22-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="7bb22-104">Ayrıca, cmdlet yöntemi çağırmak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bb22-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="7bb22-105">Sonlandırıcı olmayan bir hata oluştuğunda, cmdlet bu hatayı çağırarak bildirmelidir [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7bb22-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="7bb22-106">Cmdlet'i bir sonlandırıcı olmayan hata bildirdiğinde, cmdlet daha fazla gelen ve bu giriş nesnesi üzerinde çalışmaya devam edebilir işlem hattı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7bb22-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="7bb22-107">Cmdlet çağırırsa [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi, cmdlet sonlandırmayan hataya neden olan koşul açıklayan bir hata kaydı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb22-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="7bb22-108">Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="7bb22-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="7bb22-109">Cmdlet'leri çağırabilir [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gerektiğinde gelen yöntemleri işleme kendi girdideki.</span><span class="sxs-lookup"><span data-stu-id="7bb22-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="7bb22-110">Ancak, cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) çağrılan iş parçacığından [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), veya [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) giriş işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7bb22-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="7bb22-111">Çağırmayın [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) başka bir iş parçacığından.</span><span class="sxs-lookup"><span data-stu-id="7bb22-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="7bb22-112">Bunun yerine, hataları tekrar ana iş parçacığı iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="7bb22-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bb22-113">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7bb22-113">See Also</span></span>

[<span data-ttu-id="7bb22-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="7bb22-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="7bb22-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7bb22-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="7bb22-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="7bb22-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="7bb22-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7bb22-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="7bb22-118">Windows PowerShell hata kaydı</span><span class="sxs-lookup"><span data-stu-id="7bb22-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="7bb22-119">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="7bb22-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
