---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "Örnek şablon bilinen bir sorun veya sınırlaması raporu"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="0c1bc-103">Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama girin</span><span class="sxs-lookup"><span data-stu-id="0c1bc-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="0c1bc-104">Örnek: Hatalı ExecutionPolicy hataları</span><span class="sxs-lookup"><span data-stu-id="0c1bc-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="0c1bc-105">Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c1bc-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="0c1bc-106">Çözüm</span><span class="sxs-lookup"><span data-stu-id="0c1bc-106">Resolution</span></span>

<span data-ttu-id="0c1bc-107">Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="0c1bc-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

