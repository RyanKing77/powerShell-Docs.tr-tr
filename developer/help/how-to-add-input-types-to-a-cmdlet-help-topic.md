---
title: Bir Cmdlet Yardım konusuna giriş türleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850179"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna Giriş Türleri Ekleme

Bu bölümde, bir giriş bölümü Windows PowerShell® cmdlet Yardım konuları eklemeyi açıklar. Giriş bölümü, değer veya özellik adı cmdlet işlem hattından girdi olarak kabul eden nesneler .NET sınıflarını listeler.

Bir giriş bölümüne ekleyebilirsiniz sınıfları sayısı sınırı yoktur. Giriş türleri içine alınan bir \<komutu: inputTypes > düğümle içine her sınıfın bir \<komutu: Inputtype > öğesi.

Şema iki içerir \<maml:description > her öğeleri \<komutu: Inputtype > öğesi. Ancak, `Get-Help` cmdlet'i yalnızca içeriğini görüntüler \<komutu: Inputtype > /\<maml:description >) öğesi.

Windows PowerShell 3. 0'den itibaren `Get-Help` cmdlet içeriğini görüntüler \<maml:uri > öğesi. Bu öğe, .NET sınıf açıklayan konulara kullanıcıları doğrudan sağlar.

Aşağıdaki XML gösterildiği \<maml:inputTypes > düğümü.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Aşağıdaki XML kullanmaya bir örnek gösterilmektedir \<maml:inputTypes > belge bir giriş türü için düğüm.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```