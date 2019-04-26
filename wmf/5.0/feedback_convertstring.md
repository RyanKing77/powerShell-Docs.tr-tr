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
# <a name="convert-string"></a>Convert-String
**Dize dönüştürme** "tarafından Sihirli replace" işlevselliği kullanıma sunma. Önce ve sonra aramak için metin istediğiniz örnekleri sağlamak ve **dize dönüştürme** metni otomatik olarak biçimlendirir. Birisi kişinin alan bir tanıtım - İşte adı ve soyadı ve bunların Soyadı, virgül, ilk ilk, son adı ve bir nokta ile değiştiriliyor. Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
