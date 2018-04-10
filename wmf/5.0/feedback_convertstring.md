---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="32efd-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="32efd-102">Convert-String</span></span>
<span data-ttu-id="32efd-103">**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="32efd-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="32efd-104">Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="32efd-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="32efd-105">Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="32efd-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="32efd-106">Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32efd-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```