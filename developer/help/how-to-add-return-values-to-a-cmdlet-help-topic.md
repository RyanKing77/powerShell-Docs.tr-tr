---
title: Return ekleme değerleri için Cmdlet Yardım konusunun | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849220"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna Dönüş Değerleri Ekleme

Bu bölümde, bir çıkış bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar. ÇIKTILAR bölümünü .NET sınıflarını cmdlet döndürür veya işlem hattını geçirir nesneleri listeler.

Çıkış bölümüne ekleyebilirsiniz sınıfları sayısı sınırı yoktur. Bir cmdlet dönüş türleri içine alınan bir \<komutu: returnValues > düğümle içine her sınıfın bir \<komutu: returnValue > öğesi.

Bir cmdlet herhangi bir çıktı oluşturmaz, hiçbir çıktı olduğunu belirtmek için bu bölümü kullanın. Örneğin, sınıf adı yerine "None" yazın ve kısa bir açıklama sağlayın. Cmdlet çıktı koşullu olarak oluşturursa, koşulları açıklamak ve koşullu çıktıyı açıklamak için bu düğümü kullanın.

Şema iki içerir \<maml:description > her öğeleri \<komutu: returnValue > öğesi. Ancak, `Get-Help` cmdlet'i yalnızca içeriğini görüntüler \<komutu: returnValue > /\<maml:description > öğesi.

Windows PowerShell 3. 0'den itibaren `Get-Help` cmdlet içeriğini görüntüler \<maml:uri > öğesi. Bu öğe, .NET sınıf açıklayan konulara kullanıcıları doğrudan sağlar.

Aşağıdaki XML gösterildiği \<maml:returnValues > düğümü.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Aşağıdaki XML kullanmaya bir örnek gösterilmektedir \<maml:returnValues > belge bir çıkış türüne düğümü.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



