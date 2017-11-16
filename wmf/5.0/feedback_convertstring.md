---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="79ef2-102">Dize dönüştürme</span><span class="sxs-lookup"><span data-stu-id="79ef2-102">Convert-String</span></span>
<span data-ttu-id="79ef2-103">**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="79ef2-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="79ef2-104">Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="79ef2-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="79ef2-105">Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="79ef2-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="79ef2-106">Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79ef2-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

