---
title: Cmdlet Yardım konuları not ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851201"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="7b48f-102">Cmdlet Yardım Konusuna Notlar Ekleme</span><span class="sxs-lookup"><span data-stu-id="7b48f-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7b48f-103">Bu bölümde, Notlar bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7b48f-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7b48f-104">Notlar bölümü diğer bölümlere yapılandırılmış, bir parametrenin daha ayrıntılı bir açıklama gibi kolayca uymayan ayrıntılarını açıklamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b48f-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="7b48f-105">Bu içerik, cmdlet belirli bir sağlayıcı ile nasıl çalıştığını, bazı benzersiz henüz önemli kullanımlarını cmdlet veya olası hata koşulları önlemenin yolları hakkında yorum içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7b48f-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="7b48f-106">Notlar bölümüne ekleyebilirsiniz notları sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7b48f-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="7b48f-107">Her bir not için bir çift ekleyin \<maml:alert > için etiketler \<maml:alertset > düğümü.</span><span class="sxs-lookup"><span data-stu-id="7b48f-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="7b48f-108">Bir dizi içinde eklenen her Not içeriğini \<MAML > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="7b48f-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="7b48f-109">Kullanım boş \<MAML > aralığı için etiketler.</span><span class="sxs-lookup"><span data-stu-id="7b48f-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="7b48f-110">Aşağıdaki XML gösterildiği bir \<maml:alertset > düğümü ile iki notları.</span><span class="sxs-lookup"><span data-stu-id="7b48f-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="7b48f-111">Her Not isteğe bağlı olduğunu göreceksiniz \<maml:title > etiketi (başlıklar, herhangi bir kümesini gruplamak için kullanılabilir \<maml:alert > etiketleri), ve her Not aralığı içeriğini aşağıdaki boş bir satır vardır.</span><span class="sxs-lookup"><span data-stu-id="7b48f-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



