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
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna Notlar Ekleme

Bu bölümde, Notlar bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar. Notlar bölümü diğer bölümlere yapılandırılmış, bir parametrenin daha ayrıntılı bir açıklama gibi kolayca uymayan ayrıntılarını açıklamak için kullanılır. Bu içerik, cmdlet belirli bir sağlayıcı ile nasıl çalıştığını, bazı benzersiz henüz önemli kullanımlarını cmdlet veya olası hata koşulları önlemenin yolları hakkında yorum içerebilir.

Notlar bölümüne ekleyebilirsiniz notları sayısı sınırı yoktur. Her bir not için bir çift ekleyin \<maml:alert > için etiketler \<maml:alertset > düğümü. Bir dizi içinde eklenen her Not içeriğini \<MAML > etiketleri. Kullanım boş \<MAML > aralığı için etiketler.

Aşağıdaki XML gösterildiği bir \<maml:alertset > düğümü ile iki notları. Her Not isteğe bağlı olduğunu göreceksiniz \<maml:title > etiketi (başlıklar, herhangi bir kümesini gruplamak için kullanılabilir \<maml:alert > etiketleri), ve her Not aralığı içeriğini aşağıdaki boş bir satır vardır.

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



