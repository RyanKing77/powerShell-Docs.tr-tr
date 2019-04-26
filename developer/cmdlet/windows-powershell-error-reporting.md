---
title: Windows PowerShell hata raporlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067102"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="2ec64-102">Windows PowerShell Hata Raporlama</span><span class="sxs-lookup"><span data-stu-id="2ec64-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="2ec64-103">Bu bölümdeki konularda, cmdlet'leri hataları nasıl rapor tartışın.</span><span class="sxs-lookup"><span data-stu-id="2ec64-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2ec64-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2ec64-104">In This Section</span></span>

<span data-ttu-id="2ec64-105">[Hata Raporlama kavramları](./error-reporting-concepts.md) cmdlet'leri hatalarını raporlamak için kullanabileceğiniz iki mekanizmalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ec64-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="2ec64-106">[Hataları sonlandıran](./terminating-errors.md) burada bu yöntem çağrıldığında gelen cmdlet'i, hataları ve yöntem çağrıldığında Windows PowerShell çalışma zamanı tarafından döndürülen özel durumları Sonlandırıcı bildirmek için kullanılan yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2ec64-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="2ec64-107">[Sonlandırıcı olmayan hatalar](./non-terminating-errors.md) Sonlandırıcı olmayan hatalara ve bu yöntem cmdlet'i çağrılabilir burada bildirmek için kullanılan yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2ec64-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="2ec64-108">[Kategoriye göre hata bilgilerini görüntüleme](./displaying-error-information.md) kullanıcılar hata görüntüleyebilir yollarını tartışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ec64-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="2ec64-109">[Windows PowerShell hata kaydı](./windows-powershell-error-records.md) bir hata kaydı bileşenlerinin açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ec64-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="2ec64-110">[ErrorRecord nesneleri yorumlama](./interpreting-errorrecord-objects.md) ErrorRecord nesneleri yorumlanma şeklini açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2ec64-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ec64-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2ec64-111">See Also</span></span>

[<span data-ttu-id="2ec64-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="2ec64-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
