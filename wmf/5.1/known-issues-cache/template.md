---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Örnek şablon bilinen bir sorun veya sınırlaması raporu
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="68c39-103">Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama girin</span><span class="sxs-lookup"><span data-stu-id="68c39-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="68c39-104">Örnek: Hatalı ExecutionPolicy hataları</span><span class="sxs-lookup"><span data-stu-id="68c39-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="68c39-105">Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="68c39-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="68c39-106">Çözüm</span><span class="sxs-lookup"><span data-stu-id="68c39-106">Resolution</span></span>

<span data-ttu-id="68c39-107">Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="68c39-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```