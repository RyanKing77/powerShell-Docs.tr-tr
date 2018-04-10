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
# <a name="convert-string"></a>Convert-String
**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar. Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir. Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor. Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```