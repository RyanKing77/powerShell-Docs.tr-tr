---
title: Açıklama tabanlı Yardım konuları yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e619ab16-90ad-46e9-9bde-d6dce492ba56
caps.latest.revision: 4
ms.openlocfilehash: e3d32f36b597088abc41e229bb0955c1b25504e6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083187"
---
# <a name="writing-comment-based-help-topics"></a><span data-ttu-id="f089c-102">Yorum Tabanlı Yardım Konuları Yazma</span><span class="sxs-lookup"><span data-stu-id="f089c-102">Writing Comment-Based Help Topics</span></span>

<span data-ttu-id="f089c-103">Özel Yardım açıklama anahtar sözcüğü kullanarak açıklama tabanlı Yardım konuları işlevleri ve komut dosyaları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f089c-103">You can write comment-based Help topics for functions and scripts by using special Help comment keywords.</span></span>

 <span data-ttu-id="f089c-104">`Get-Help` Cmdlet'i, XML dosyalarından oluşturulan cmdlet'i Yardım konularını gösterir aynı biçimde açıklama tabanlı Yardım görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f089c-104">The `Get-Help` cmdlet displays comment-based Help in the same format in which it displays the cmdlet Help topics that are generated from XML files.</span></span> <span data-ttu-id="f089c-105">Kullanıcılar, tüm parametrelerinin kullanabilir `Get-Help`ayrıntılı, tam, örnek ve çevrimiçi, işlevi görüntüler ve Yardım betik gibi.</span><span class="sxs-lookup"><span data-stu-id="f089c-105">Users can use all of the parameters of `Get-Help`, such as Detailed, Full, Example, and Online, to display function and script Help.</span></span>

 <span data-ttu-id="f089c-106">Ayrıca, betikleri ve işlevleri için XML tabanlı Yardım konuları yazmak ve XML tabanlı konular veya diğer konular için kullanıcılara yönlendirmek için Yardım açıklaması anahtar sözcükleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f089c-106">You can also write XML-based Help topics for scripts and functions and use the Help comment keywords to redirect users to the XML-based topics or other topics.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f089c-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f089c-107">In This Section</span></span>

 <span data-ttu-id="f089c-108">[Açıklama tabanlı Yardım sözdizimi](./syntax-of-comment-based-help.md) açıklama tabanlı Yardım söz dizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f089c-108">[Syntax of Comment-Based Help](./syntax-of-comment-based-help.md) Describes the syntax of comment-based help.</span></span>

 <span data-ttu-id="f089c-109">[Açıklama tabanlı Yardım anahtar](./comment-based-help-keywords.md) açıklama tabanlı Yardım anahtar sözcükleri listeler.</span><span class="sxs-lookup"><span data-stu-id="f089c-109">[Comment-Based Help Keywords](./comment-based-help-keywords.md) Lists the keywords in comment-based help.</span></span>

 <span data-ttu-id="f089c-110">[Açıklama tabanlı Yardım işlevlerde yerleştirme](./placing-comment-based-help-in-functions.md) bir işlev için açıklama tabanlı Yardım yerleştirileceği yeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f089c-110">[Placing Comment-Based Help in Functions](./placing-comment-based-help-in-functions.md) Shows where to place comment-based help for a function.</span></span>

 <span data-ttu-id="f089c-111">[Açıklama tabanlı Yardım betiklerde yerleştirme](./placing-comment-based-help-in-scripts.md) bir komut dosyası için açıklama tabanlı Yardım yerleştirileceği yeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f089c-111">[Placing Comment-Based Help in Scripts](./placing-comment-based-help-in-scripts.md) Shows where to place comment-based help for a script.</span></span>