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
# <a name="convert-string"></a>Dize dönüştürme
**Dönüştürme dizesi** "Sihirli tarafından replace" işlevselliği kullanıma sunar. Önce ve sonra aramak için metin istediğiniz örnekleri sağlar ve **dönüştürme dizesi** metninizi otomatik olarak biçimlendirir. Görmesini alma demo - İşte adı ve soyadı ve son kullanıcıların adı, virgül, ilk ilk ve son kullanıcıların adı, bir nokta ile değiştiriliyor. Regex ile deneyin ve ne kadar sürdüğünü görebilirsiniz.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

