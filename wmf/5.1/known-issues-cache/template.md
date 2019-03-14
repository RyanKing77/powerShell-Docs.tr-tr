---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: bilinen bir sorun veya sınırlama writeup örnek şablonu
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794509"
---
 ><span data-ttu-id="57ce9-103">Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="57ce9-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="57ce9-104">Örnek: Hatalı ExecutionPolicy hataları</span><span class="sxs-lookup"><span data-stu-id="57ce9-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="57ce9-105">Windows 7'de PowerShell modülleri ve DSC kaynakları ExecutionPolicy hakkında rapor edilen hata neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="57ce9-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="57ce9-106">Çözüm</span><span class="sxs-lookup"><span data-stu-id="57ce9-106">Resolution</span></span>

<span data-ttu-id="57ce9-107">Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="57ce9-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
