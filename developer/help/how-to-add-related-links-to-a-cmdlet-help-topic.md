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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083357"
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



