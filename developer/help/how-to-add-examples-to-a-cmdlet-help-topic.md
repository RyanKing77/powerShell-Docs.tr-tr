---
title: Bir Cmdlet Yardım konusunun örneklere ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855124"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna Örnekler Ekleme

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Örnek Cmdlet Yardım hakkında bilmeniz gerekenler

- Parametre adları isteğe bağlı olsa bile tüm komut parametre adları listelenmektedir. Bu komut bir kolayca yorumlamak için kullanıcı yardımcı olur.

- Windows PowerShell® içinde çalıştıkları olsa da, diğer adlar ve kısmi parametre adları, kaçının.

- Örnek açıklamasında rasyonel komutu oluşumu için açıklanmaktadır. Belirli parametreleri ve değerleri neden seçtiğiniz ve değişkenleri nasıl kullanabileceğinizi açıklar.

- Komut ifadeleri kullanıyorsa, bunları ayrıntılı olarak açıklanmaktadır.

- Komut özellikleri ve yöntemleri nesneleri, özellikle de varsayılan ekran görüntüsünde, görünmez özellikleri kullanıyorsa, kullanıcı nesnesi hakkında bir fırsat söyleyin gibi örneği kullanın.

## <a name="help-views-that-display-examples"></a>Örnekler görüntüleyen Görüşnümleri Yardım

Örnekler yalnızca ayrıntılı ve tam görünümlerinde cmdlet Yardım görünür.

## <a name="adding-an-examples-node"></a>Örnekler düğüm ekleme

Aşağıdaki XML, tek bir örnek düğümü içeren bir örnek düğüm ekleme işlemi gösterilmektedir. Konusundaki dahil etmek istediğiniz her örnek için ek örnek düğümler ekleyin.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Bir örnek başlık ekleme

Aşağıdaki XML, örnek için bir başlık ekleme işlemi gösterilmektedir. Başlık, örneğin diğer örnekler dışında ayarlamak için kullanılır. Windows PowerShell® ardışık örnek sayısı içeren standart üstbilgi kullanır.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Karakter önceki ekleme

Aşağıdaki XML, örnek komut (olmadan, müdahalede bulunan tüm alanları) hemen önce görüntülenen gibi karakterler Windows PowerShell istemi ekleme işlemi gösterilmektedir. Windows PowerShell istemi Windows PowerShell® kullanır: C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Komut ekleme

Aşağıdaki XML, örneğin gerçek komut ekleme işlemi gösterilmektedir. Komut eklerken, adın tamamını yazın (diğer ad kullanmayın) cmdlet'leri ve parametreleri. Ayrıca, mümkün olduğunda, küçük harf karakterler kullanın.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Bir açıklama ekleme

Aşağıdaki XML, örnek için bir açıklama ekleme işlemi gösterilmektedir. Windows PowerShell® kullanan tek bir dizi \<MAML > olsa bile bir açıklama etiketleri birden çok \<MAML > etiketleri kullanılabilir.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Örnek çıktı ekleme

Aşağıdaki XML, komut çıktısı ekleme işlemi gösterilmektedir. Komutu sonuçları bilgileri isteğe bağlıdır, ancak bazı durumlarda belirli parametreler kullanılarak etkisini göstermeye yardımcı olur. Windows PowerShell® kullanan iki boş \<MAML > komutundan komut çıktısı ayırmak için etiketler.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```