---
title: Hata Raporlama kavramları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068190"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="916b5-102">Hata Raporlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="916b5-102">Error Reporting Concepts</span></span>

<span data-ttu-id="916b5-103">Windows PowerShell, hata raporlama için iki mekanizma sağlar: bir mekanizma *hataları sonlandıran* ve başka bir mekanizma *Sonlandırıcı olmayan hatalara*.</span><span class="sxs-lookup"><span data-stu-id="916b5-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="916b5-104">Cmdlet'lerinizi çalıştıran ana bilgisayar uygulaması uygun bir şekilde tepki verebilir böylece doğru cmdlet'inize hatalarını raporlamak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="916b5-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="916b5-105">Cmdlet'inize çağırmalıdır [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) bir hata oluştuğunda yöntemi yok ya da giriş nesnelerini işlemeye devam etmek cmdlet izin vermemelidir.</span><span class="sxs-lookup"><span data-stu-id="916b5-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="916b5-106">Cmdlet'inize çağırmalıdır [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) cmdlet giriş nesneleri işleme devam ederken Sonlandırıcı olmayan hatalara bildirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="916b5-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="916b5-107">Her iki yöntem de konak uygulama hatanın nedenini araştırmak için kullanabileceğiniz bir hata kaydı sağlar.</span><span class="sxs-lookup"><span data-stu-id="916b5-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="916b5-108">Bir sonlandırıcı bir hata olup veya Sonlandırıcı olmayan hata belirlemek için aşağıdaki kılavuzları kullanın.</span><span class="sxs-lookup"><span data-stu-id="916b5-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="916b5-109">Bir hata hatası ise, geçerli nesne işlenmeye devam veya başarıyla içeriklerini bağımsız olarak herhangi bir ek giriş nesne işleme cmdlet'inize engeller.</span><span class="sxs-lookup"><span data-stu-id="916b5-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="916b5-110">Geçerli nesne ya da içeriklerini bağımsız olarak herhangi bir ek giriş nesne işleme devam etmek için cmdlet istemiyorsanız bir sonlandırmalı hata hatadır.</span><span class="sxs-lookup"><span data-stu-id="916b5-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="916b5-111">Bir sonlandırma hatası kabul edin veya nesne döndüren bir cmdlet oluşursa veya kabul eder ya da yalnızca bir nesne döndürür bir cmdlet'i gerçekleşirse hatadır.</span><span class="sxs-lookup"><span data-stu-id="916b5-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="916b5-112">Cmdlet'inize geçerli nesne ve tüm ek giriş nesnelerin işleme devam etmek istiyorsanız, bir sonlandırıcı olmayan hata hatadır.</span><span class="sxs-lookup"><span data-stu-id="916b5-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="916b5-113">Belirli giriş nesnesi ya da alt giriş nesnelerinin ilgiliyse bir sonlandırıcı olmayan hata hatadır.</span><span class="sxs-lookup"><span data-stu-id="916b5-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="916b5-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="916b5-114">See Also</span></span>

[<span data-ttu-id="916b5-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="916b5-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="916b5-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="916b5-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="916b5-117">Windows PowerShell hata kaydı</span><span class="sxs-lookup"><span data-stu-id="916b5-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="916b5-118">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="916b5-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
