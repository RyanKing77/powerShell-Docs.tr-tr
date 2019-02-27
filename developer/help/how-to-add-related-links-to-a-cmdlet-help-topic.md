---
title: Cmdlet Yardım konuları ilgili bağlantılar ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846392"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna İlgili Bağlantılar Ekleme

Bu bölümde, başvurular için Windows PowerShell® cmdlet Yardım konusunun ilgili diğer içeriklere eklemeyi açıklar. Bu başvurular bir komut penceresinde göründüğünden, başvurulan içeriği doğrudan bağlamayın.

Cmdlet Yardım Windows PowerShell® içinde bulunan konularda, bu bağlantılar, diğer cmdlet'ler, kavramsal içerik ("about_") ve diğer belgeler ve Windows PowerShell® için ilgili olmayan Yardım dosyaları başvuru.

Aşağıdaki XML, ilgili konular iki başvuru içeren bir RelatedLinks düğüm ekleme işlemi gösterilmektedir.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



