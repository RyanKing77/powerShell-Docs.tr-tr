---
title: Parametre bilgileri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083374"
---
# <a name="how-to-add-parameter-information"></a>Parametre Bilgileri Ekleme

Bu bölümde, cmdlet Yardım konusunun parametreleri bölümünde görüntülenen içerik eklemeyi açıklar. Yardım konusunun PARAMETRELER bölümü her cmdlet parametreleri listeler ve her parametre için ayrıntılı bir açıklaması verilmiştir.

PARAMETRELER bölümü içeriğini söz DİZİMİ bölümünün Yardım konusunun içeriğini tutarlı olmalıdır. Söz dizimi ve parametreler düğüm benzer XML öğeleri içerdiğinden emin olmak için Yardım Yazar sorumluluğundadır.

> [!NOTE]
> Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için. Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.

### <a name="to-add-parameters"></a>Parametre eklemek için

1. Cmdlet Yardım dosyasını açın ve belgeleme cmdlet komutunu düğümünü bulun. Yeni cmdlet ekliyorsanız, yeni bir komut düğümü oluşturmanız gerekir. Bir komut düğümü için Yardım içeriği sağlanmaktadır her cmdlet için Yardım dosyanızı içerir. Boş bir komut düğümü bir örneği aşağıda verilmiştir.

    ```xml
    <command:command>
    </command:command>
    ```

2. Komut düğümü içindeki açıklama düğümü bulun ve aşağıda gösterildiği gibi bir parametre düğüm ekleyin. Yalnızca bir parametre düğümü izin verilir ve sözdizimi düğümü hemen izlemelidir.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Parametreleri düğümünde cmdlet her parametre için bir parametre düğümünde aşağıda gösterildiği gibi ekleyin.

   Bu örnekte, üç parametre için bir parametre düğümünde eklenir.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Bu söz dizimi düğümünde kullanılır ve burada belirtilen parametreler için sözdizimi düğümü tarafından belirtilen parametreler eşleşmelidir aynı XML etiketleri olduğundan, parametre düğümleri sözdizimi düğümü kopyalayıp bunları parametreleri düğümüne yapıştırın. Ancak, bir parametre düğümünde yalnızca bir örneğini kopyaladığınızdan emin olun, parametre olarak belirtilmiş olsa bile, birden çok parametre sözdiziminde ayarlar.

4. Her parametre için düğümü, her parametrenin özelliklerini tanımlayan öznitelik değerleri ayarlayın. Bu öznitelikleri şunlardır: genelleştirme, pipelineinput ve konum gerekli.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Her parametre düğüm için parametre adını ekleyin. Parametre adının parametre düğüme eklenmiş bir örnek aşağıda verilmiştir.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Her parametre düğüm için parametre açıklamasını ekleyin. Parametre açıklaması parametre düğüme eklenen bir örneği aşağıda verilmiştir.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Her parametre düğüm için .NET Framework türü parametre ekleyin. Parametre türü, parametre adı ile birlikte görüntülenir.

   Parametre düğüme eklenen parametre .NET Framework türü örneği aşağıda verilmiştir.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Her parametre düğüm için parametresinin varsayılan değeri ekleyin. İçerik görüntülendiğinde aşağıdaki cümle için parametre açıklaması eklenir: "DefaultValue" varsayılandır.

   İşte parametresi varsayılan değere örnek parametre düğümüne eklenir.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Birden çok değeri var. her parametre için bir olası değerler düğüm ekleyin.

   İşte bir örnek tanımlayan iki olası değerler parametresi için olası değerler düğümü

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Parametreleri eklerken hatırlamak işlemlerden bazıları aşağıda verilmiştir.

- Parametre öznitelikleri, cmdlet Yardım konusunun tüm görünümlerde görüntülenmez. Ancak, kullanıcı için tam istediğinde parametre açıklaması izleyen bir tablo görüntülenir (Get-Help \<cmdletname >-tam) veya bir parametre (Get-Help \<cmdletname >-parametresi) konunun görünümü.

- Parametre açıklaması cmdlet Yardım konusunun en önemli parçalarından biridir. Açıklama kısa yanı sıra eksiksiz olması gerekir. Ayrıca, parametre açıklaması iki parametre birbiriyle ne zaman etkileşim gibi çok uzun olursa, cmdlet Yardım konusunun Notlar bölümünde daha fazla içerik eklemek unutmayın.

  Parametre açıklaması, iki tür bilgisini sağlar.

- Parametresi kullanıldığında, cmdlet yapar.

- Parametresi hangi geçerli bir değer olmalıdır.

- Parametre değerlerini .NET Framework nesneleri ifade edilir çünkü kullanıcılar bu değerler hakkında daha fazla bilgi, geleneksel bir komut satırı Yardımı yaptıkları daha gerekir. Kullanıcı ne tür verilere parametre kabul etmek üzere tasarlanmıştır söyleyin ve örnek olarak verilebilir.

Komut satırında parametresi belirtilmezse, kullanılan değer parametresinin varsayılan değerdir. Varsayılan değer isteğe bağlıdır ve gerekli parametreleri gibi bazı parametreler için gerekli değildir unutmayın. Ancak, çoğu isteğe bağlı parametreler için varsayılan bir değer belirtmeniz gerekir.

Varsayılan değer parametresini kullanmayan etkisini anlamak için kullanıcı yardımcı olur. Varsayılan değer "geçerli dizin" veya "Windows PowerShell için yükleme diziniyle ($pshome)" isteğe bağlı bir yol gibi çok özellikle açıklanmaktadır. Ayrıca, varsayılan olarak kullanılan aşağıdaki cümle gibi açıklayan bir cümle yazabilirsiniz `PassThru` parametresi: "PassThru belirtilmemişse cmdlet aşağı işlem hattı nesneleri geçmez."  Ayrıca, değeri alan adı görüntülendiğinden "**varsayılan değer**", "varsayılan değer" terimi girişi eklemek gerekmez.

Parametrenin varsayılan değeri, cmdlet Yardım konusunun tüm görünümlerde görüntülenmez. Ancak, kullanıcı için tam istediğinde parametre açıklaması aşağıdaki tabloda (parametre öznitelikleri) ile birlikte görüntülenir (Get-Help \<cmdletname >-tam) veya parametresini (Get-Help \<cmdletname >-parametresi) görünümü konu.

Aşağıdaki XML bir çift gösterir `<dev:defaultValue>` eklenen etiketler `<command:parameter>` düğümü. Varsayılan değer kapattıktan sonra hemen takip eden bildirim `</command:parameterValue>` (parametre değeri belirtildiğinde) etiketi veya kapanış `</maml:description>` parametre açıklaması etiketi. Adı.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Numaralandırılmış türler için değerleri ekleyin

Parametresi birden çok değer veya bir listeden seçimli türü değerlerinin varsa, isteğe bağlı kullanabilirsiniz \<dev:possibleValues > düğümü. Bu düğüm, bir ad ve açıklama için birden çok değer belirtmenizi sağlar.

Numaralandırılmış değerler açıklamaları varsayılan hiçbirinde Yardım görünüm tarafından görüntülenen görünmediğini unutmayın `Get-Help` cmdlet'i, ancak diğer Yardım görüntüleyicileri görüntüleyebilir bu içerik, görünümlerde.

Aşağıdaki XML gösterildiği bir `<dev:possibleValues>` iki değer belirtilen düğümle.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```