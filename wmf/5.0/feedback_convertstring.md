---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219275"
---
# <a name="convert-string"></a>Convert-String
**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar. Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir. Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor. Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
