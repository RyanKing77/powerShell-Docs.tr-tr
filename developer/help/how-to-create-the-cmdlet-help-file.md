---
title: Cmdlet Yardım dosyasının nasıl oluşturulacağı | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848898"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Cmdlet Yardım Dosyası Oluşturma

Bu bölümde Windows PowerShell cmdlet Yardım konuları için içeriği geçerli bir XML dosyası oluşturmayı açıklar. Bu bölümde, nasıl Yardım dosyasını adlandırmak, uygun XML üstbilgileri ekleme ve Yardım içeriğini cmdlet'i farklı bölümlerini içerecek düğümleri ekleme açıklanmaktadır.

> [!NOTE]
> Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için. Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.

### <a name="how-to-create-a-cmdlet-help-file"></a>Bir Cmdlet Yardım dosyası oluşturma

1. Bir metin dosyası oluşturun ve UTF8 Kodlaması kullanarak kaydedin. Windows PowerShell cmdlet Yardım dosyası olarak algılayabilir, dosya adı şu biçimde olması gerekir.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Aşağıdaki XML üst bilgilerini metin dosyasına ekleyin. Dosya çok aracılı Modelleme Dili (MAML) şemayla doğrulandı dikkat edin. Şu anda, Windows PowerShell dosyasını doğrulamak için herhangi bir araç sağlamaz.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Bir komut düğümü derlemedeki her cmdlet için cmdlet Yardım dosyasına ekleyin. Her düğümü komut düğümü cmdlet Yardım konusunun farklı bölümlere ilişkilendirir.

   Aşağıdaki tabloda her düğümün bir açıklaması tarafından izlenen her bir düğümün XML öğesi listeler.

   |Düğüm|Açıklama|
   |----------|-----------------|
   |`<details>`|Cmdlet Yardım konusunun adını ve özeti bölümlerinin içeriğini ekler. Daha fazla bilgi için [Cmdlet adı ve özeti nasıl ekleneceğini](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Cmdlet Yardım konusunun Açıklama bölümünde için içerik ekler. Daha fazla bilgi için [Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Cmdlet Yardım konusunun söz DİZİMİ bölümünün içerik ekler. Daha fazla bilgi için [ekleme sözdizimi için Cmdlet Yardım konusunun nasıl](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|PARAMETRELER bölümü cmdlet Yardım konusunun içeriğini ekler. Daha fazla bilgi için [parametreleri eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Cmdlet Yardım konusunun GİRİŞLERİ bölümünün içerik ekler. Daha fazla bilgi için [giriş türleri eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|ÇIKTILAR bölümünü cmdlet Yardım konusunun içeriğini ekler. Daha fazla bilgi için [ekleme dönüş değerleri için Cmdlet Yardım konusunun nasıl](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|İçerik cmdlet Yardım konusunun Notlar bölümüne ekler. Daha fazla bilgi için [ekleme için Cmdlet Yardım konusunun notları](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|İçerik için cmdlet Yardım konusunun ÖRNEKLER bölümüne ekler. Daha fazla bilgi için [ekleme örnekleri için Cmdlet Yardım konusunun nasıl](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|İçin cmdlet Yardım konusunun ilgili bağlantılar bölümüne içerik ekler. Daha fazla bilgi için [ilgili bağlantılar eklemek için Cmdlet Yardım konusunun nasıl](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Örnek

 Cmdlet Yardım konusunun çeşitli bölümlerini düğümleri içeren bir komut düğümü bir örneği aşağıda verilmiştir.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Ayrıca bkz:

 [Cmdlet adı ve özeti nasıl ekleneceğini](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları ayrıntılı bir açıklama ekleme](./how-to-add-a-cmdlet-description.md)

 [Cmdlet Yardım konuları söz dizimi ekleme](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları parametreleri ekleme](./how-to-add-parameter-information.md)

 [Bir Cmdlet Yardım konusuna giriş türleri ekleme](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Dönüş değerleri için Cmdlet Yardım konusunun ekleme](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Ekleme için Cmdlet Yardım konusunun notları](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Bir Cmdlet Yardım konusunun örneklere ekleme](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cmdlet Yardım konuları ilgili bağlantılar ekleme](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK'sı](../windows-powershell-reference.md)