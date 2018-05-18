---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a><span data-ttu-id="033dc-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="033dc-102">Convert-String</span></span>
<span data-ttu-id="033dc-103">**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="033dc-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="033dc-104">Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="033dc-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="033dc-105">Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="033dc-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="033dc-106">Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="033dc-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
