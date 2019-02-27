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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="7b464-102">Cmdlet Yardım Konusuna İlgili Bağlantılar Ekleme</span><span class="sxs-lookup"><span data-stu-id="7b464-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7b464-103">Bu bölümde, başvurular için Windows PowerShell® cmdlet Yardım konusunun ilgili diğer içeriklere eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b464-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7b464-104">Bu başvurular bir komut penceresinde göründüğünden, başvurulan içeriği doğrudan bağlamayın.</span><span class="sxs-lookup"><span data-stu-id="7b464-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="7b464-105">Cmdlet Yardım Windows PowerShell® içinde bulunan konularda, bu bağlantılar, diğer cmdlet'ler, kavramsal içerik ("about_") ve diğer belgeler ve Windows PowerShell® için ilgili olmayan Yardım dosyaları başvuru.</span><span class="sxs-lookup"><span data-stu-id="7b464-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="7b464-106">Aşağıdaki XML, ilgili konular iki başvuru içeren bir RelatedLinks düğüm ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b464-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



