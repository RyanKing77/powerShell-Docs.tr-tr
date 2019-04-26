---
title: Cmdlet Yardım konuları söz dizimi ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083391"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konusuna Söz Dizimi Ekleme

- [Parametre öznitelikleri](#Parameter-Attributes)

- [Parametre değeri öznitelikleri](#Parameter-Value-Attributes)

- [Söz dizimi bilgileri toplanıyor](#Gathering-Syntax-Information)

- [Söz dizim diyagramı görülmektedir XML kodlama](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Söz dizim diyagramı görülmektedir Cmdlet Yardım hakkında bilmeniz gerekenler

Veri türünü NET bir görüntüsünü almak için bu bölümü okuyun için söz dizim diyagramı görülmektedir cmdlet Yardım dosyasındaki XML kodunu başlamadan önce parametre öznitelikleri ve bu verileri söz dizim diyagramı görülmektedir içinde nasıl görüntüleneceğini gibi sağlamanız gerekir...

### <a name="parameter-attributes"></a>Parametre öznitelikleri

- Gerekli

  - TRUE ise parametresi parametre kullanan tüm komutları yer almalıdır.

  - False ise parametre kümesi kullanan tüm komutlar, isteğe bağlı bir parametredir.

- Konum

  - Adlı, parametre adı gereklidir.

  - Konumsal, parametre adı isteğe bağlıdır. Atlandığında, parametre değeri komut belirtilen konumda olmalıdır. Konum değeri ise, örneğin, "1" = parametre değeri ilk veya yalnızca adlandırılmamış parametreyi komutta olması gerekir.

- Ardışık giriş

  - TRUE ise (ByValue) giriş parametresine kanal oluşturarak. İlişkili bir giriştir ("bağlama") ile özellik adı ve nesne türü beklenen türle eşleşmiyor olsa bile parametresi. Windows PowerShell? parametre bağlama bileşenleri doğru türde girişi dönüştürür ve yalnızca tür dönüştürülemiyorsa komutu başarısız deneyin. Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.

  - TRUE ise (ByPropertyName) giriş parametresine kanal oluşturarak. Ancak, parametre adı giriş nesnenin bir özelliğini adını eşleştiğinde giriş parametresi ile ilişkilidir. Örneğin, parametre adı ise `Path`, yalnızca nesne yolu adlı bir özellik varsa cmdlet'e yöneltilen nesneler bu parametre ile ilişkili.

  - Varsa true (ByValue, ByPropertyName), özellik adı veya değer tarafından giriş parametresine kanal oluşturarak. Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.

  - False ise, bu parametre için kanal oluşturarak giriş aktaramazsınız.

- Genelleştirme

  - TRUE ise kullanıcı için parametre değeri türleri metin joker karakterler içerebilir.

  - False ise, kullanıcı için parametre değeri türleri metin joker karakterler içeremez.

### <a name="parameter-value-attributes"></a>Parametre değeri öznitelikleri

- Gerekli

  - TRUE ise belirtilen değer, bir komut parametresi kullanıldığında kullanılmalıdır.

  - Parametre değeri, false ise isteğe bağlıdır. Genellikle, yalnızca bir parametresi için geçerli değerlerden biri gibi bir listeden seçimli türü olduğunda bir değer isteğe bağlıdır.

Gerekli bir parametre değeri parametre gerekli özniteliğinden farklı özniteliğidir.

Gerekli öznitelik parametresinin parametre (ve değerinin) cmdlet çağrılırken dahil edilmesi gereken olup olmadığını gösterir. Buna karşılık, parametre yalnızca komutta eklendiğinde bir parametre değeri gerekli özniteliği kullanılır. Bu, bu özel değer parametresi kullanılıp kullanılmayacağını belirtir.

Genellikle, yer tutucuları olan parametre değerleri gereklidir ve parametresiyle birlikte kullanılan değerlerden birini olduklarından değişmez değer parametre değerlerini gerekli değildir.

### <a name="gathering-syntax-information"></a>Söz dizimi bilgileri toplanıyor

1. Cmdlet adı ile başlatın.

   ```
   SYNTAX
       Get-Tech
   ```

2. Cmdlet tüm parametreler listelenmektedir. Türü bir tire ("dash" veya "önce gelen eksi işaretinin" (ASCII 45) her parametre adı olarak da bilinir. Parametreler, parametre kümeleri halinde (bazı cmdlet'ler kümesi yalnızca bir parametreye sahip) ayırın. Bu örnekte, Get-teknik cmdlet'i iki parametre kümesine sahiptir.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Her parametre kümesi cmdlet adı ile başlatın.

   İlk olarak varsayılan parametre listesi. Varsayılan parametre cmdlet'i sınıfı tarafından belirtilir.

   İlk görünmelidir konumsal parametreler olmadığı sürece her parametre kümesi için benzersiz, parametresinin ilk olarak listeleyin. Önceki örnekte adı ve kimliği iki parametre kümesi için benzersiz parametreleri parametreleridir (her parametre kümesi bu parametre kümesi için benzersiz olan bir parametreye sahip olmalıdır). Bu, kullanıcıların hangi parametre parametresi için sağlamak için ihtiyaç duydukları tanımlamak kolaylaştırır.

   Komut içinde görünmesi gereken sırayla parametreler listelenmektedir. Sırası önemli değildir, ilgili parametreler birlikte listelemek veya öncelikle en sık kullanılan parametreleri listeler.

   Cmdlet ShouldProcess destekliyorsa WhatIf ve onaylama parametreleri listesi emin olun.

   Ortak parametreler (örneğin, ayrıntı, hata ayıklama ve ErrorAction) söz dizimi diyagramınızda listelemez. `Get-Help` Cmdlet Yardım konusunu görüntüler, bu bilgileri ekler.

3. Parametre değerlerini ekleyin. Windows PowerShell'de?, parametre değerlerini .NET türlerine göre temsil edilir. Ancak, tür adı, System.String için "dize" gibi kısaltılmış.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Anlamları System.String için "dize" ve "int" System.Int32 gibi açık olduğu sürece türleri kısaltma.

   Numaralandırmalar, tüm değerlerin listesi gibi tür parametresi önceki örnekte, "temel" veya "Gelişmiş" olarak ayarlanabilir.

   -Önceki örnekte liste gibi parametreleri değiştirmek, değeri yok.

4. Açılı ayraçlar sabitleridir parametre değerlerini karşılaştırıldığında yer tutucu olan parametre değerleri ekleyin.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. İsteğe bağlı parametreler ve bunların değerleri köşeli ayraç içine alın.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. İsteğe bağlı parametre adları (için konumsal parametreleri) köşeli ayraç içine alın. Adı aşağıdaki örnekte, Name parametresi gibi konumsal parametreler için komutta dahil edilmesi gerekmez.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Name parametresi adları listesi gibi birden çok değer içeren bir parametre değeri, bir parametre değeri doğrudan aşağıdaki köşeli çift ekleyin.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Kullanıcı, parametre veya parametre değerlerini seçebilir, tür parametresi gibi seçenekler kaşlı ayraçlar içine alın ve özel veya symbol(;) ile ayırarak.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Parametre değeri tırnak işareti veya parantezler, gibi belirli biçimlendirme kullanmanız gerekiyorsa sözdiziminde biçimi gösterir.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Söz dizim diyagramı görülmektedir XML kodlama

XML sözdizimi düğümü hemen ile biten açıklama düğümü sonra başlar \</maml:description > etiketi. Söz dizimi diyagramda kullanılan veri toplama hakkında daha fazla bilgi için bkz: [söz dizimi bilgi toplama](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Sözdizimi düğümü ekleme

Cmdlet Yardım konusundaki görüntülenen söz dizim diyagramı görülmektedir XML sözdizimi düğümü verilerden oluşturulur. Sözdizimi düğümü ise bir çiftini alınmış \<sözdizimi: > etiketleri. Bir çift içine cmdlet her parametre kümesi ile \<komutu: syntaxitem > etiketleri. Sınırsız sayıda \<komutu: syntaxitem > etiketleri ekleyebilirsiniz.

Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü gösterir.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Veri kümesi Cmdlet adı parametresi ekleme

Her parametre kümesi cmdlet sözdizimi öğesi düğümünde belirtilir. Her sözdizimi öğesi düğüm çifti ile başlar \<maml:name > cmdlet'in adını içeren etiketler.

Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü içerir.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Parametre ekleme

Sözdizimi öğesi düğüme eklenen her bir parametre bir çift içinde belirtilen \<komut: parametresi > etiketleri. Bir çift ihtiyacınız \<komut: parametresi > etiketleri parametre kümesi, Windows PowerShell tarafından sağlanan ortak parametrelerin dışında bulunan her bir parametreye?

Açılış özniteliklerini \<komut: parametresi > etiketi belirlemek nasıl parametresi söz dizimi diyagramda görünür. Parametre öznitelikleri hakkında daha fazla bilgi için bkz: [parametre öznitelikleri](#Parameter-Attributes).

> [!NOTE]
> \<Komut: parametresi > etiketi, bir alt öğesi destekliyor \<maml:description > içeriğe sahip hiçbir zaman görüntülenir. Parametre açıklamaları parametre'XML düğümünde belirtilir. Söz dizimi öğesi bilgiler arasındaki tutarsızlıkları önlemek için bodes ve parametre düğümü çıkarın (\<maml:description > veya bu alanı boş bırakın.

Aşağıdaki örnek, bir parametre kümesi ile iki parametre için bir sözdizimi öğe düğümü içerir.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
