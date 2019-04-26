---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057800"
---
# <a name="convert-string"></a><span data-ttu-id="d0d2e-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="d0d2e-102">Convert-String</span></span>
<span data-ttu-id="d0d2e-103">**Dize dönüştürme** "tarafından Sihirli replace" işlevselliği kullanıma sunma.</span><span class="sxs-lookup"><span data-stu-id="d0d2e-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="d0d2e-104">Önce ve sonra aramak için metin istediğiniz örnekleri sağlamak ve **dize dönüştürme** metni otomatik olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="d0d2e-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="d0d2e-105">Birisi kişinin alan bir tanıtım - İşte adı ve soyadı ve bunların Soyadı, virgül, ilk ilk, son adı ve bir nokta ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="d0d2e-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="d0d2e-106">Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0d2e-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
