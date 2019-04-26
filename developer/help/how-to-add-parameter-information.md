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
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="9af6f-102">Parametre Bilgileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="9af6f-102">How to Add Parameter Information</span></span>

<span data-ttu-id="9af6f-103">Bu bölümde, cmdlet Yardım konusunun parametreleri bölümünde görüntülenen içerik eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9af6f-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="9af6f-104">Yardım konusunun PARAMETRELER bölümü her cmdlet parametreleri listeler ve her parametre için ayrıntılı bir açıklaması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="9af6f-105">PARAMETRELER bölümü içeriğini söz DİZİMİ bölümünün Yardım konusunun içeriğini tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9af6f-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="9af6f-106">Söz dizimi ve parametreler düğüm benzer XML öğeleri içerdiğinden emin olmak için Yardım Yazar sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="9af6f-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="9af6f-107">Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için.</span><span class="sxs-lookup"><span data-stu-id="9af6f-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="9af6f-108">Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="9af6f-109">Parametre eklemek için</span><span class="sxs-lookup"><span data-stu-id="9af6f-109">To Add Parameters</span></span>

1. <span data-ttu-id="9af6f-110">Cmdlet Yardım dosyasını açın ve belgeleme cmdlet komutunu düğümünü bulun.</span><span class="sxs-lookup"><span data-stu-id="9af6f-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="9af6f-111">Yeni cmdlet ekliyorsanız, yeni bir komut düğümü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="9af6f-112">Bir komut düğümü için Yardım içeriği sağlanmaktadır her cmdlet için Yardım dosyanızı içerir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="9af6f-113">Boş bir komut düğümü bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="9af6f-114">Komut düğümü içindeki açıklama düğümü bulun ve aşağıda gösterildiği gibi bir parametre düğüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="9af6f-115">Yalnızca bir parametre düğümü izin verilir ve sözdizimi düğümü hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="9af6f-116">Parametreleri düğümünde cmdlet her parametre için bir parametre düğümünde aşağıda gösterildiği gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="9af6f-117">Bu örnekte, üç parametre için bir parametre düğümünde eklenir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="9af6f-118">Bu söz dizimi düğümünde kullanılır ve burada belirtilen parametreler için sözdizimi düğümü tarafından belirtilen parametreler eşleşmelidir aynı XML etiketleri olduğundan, parametre düğümleri sözdizimi düğümü kopyalayıp bunları parametreleri düğümüne yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9af6f-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="9af6f-119">Ancak, bir parametre düğümünde yalnızca bir örneğini kopyaladığınızdan emin olun, parametre olarak belirtilmiş olsa bile, birden çok parametre sözdiziminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9af6f-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="9af6f-120">Her parametre için düğümü, her parametrenin özelliklerini tanımlayan öznitelik değerleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9af6f-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="9af6f-121">Bu öznitelikleri şunlardır: genelleştirme, pipelineinput ve konum gerekli.</span><span class="sxs-lookup"><span data-stu-id="9af6f-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

5. <span data-ttu-id="9af6f-122">Her parametre düğüm için parametre adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="9af6f-123">Parametre adının parametre düğüme eklenmiş bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="9af6f-124">Her parametre düğüm için parametre açıklamasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="9af6f-125">Parametre açıklaması parametre düğüme eklenen bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-125">Here is an example of the parameter description added to the Parameter node.</span></span>

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

7. <span data-ttu-id="9af6f-126">Her parametre düğüm için .NET Framework türü parametre ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="9af6f-127">Parametre türü, parametre adı ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="9af6f-128">Parametre düğüme eklenen parametre .NET Framework türü örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

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

8. <span data-ttu-id="9af6f-129">Her parametre düğüm için parametresinin varsayılan değeri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="9af6f-130">İçerik görüntülendiğinde aşağıdaki cümle için parametre açıklaması eklenir: "DefaultValue" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9af6f-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="9af6f-131">İşte parametresi varsayılan değere örnek parametre düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

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

9. <span data-ttu-id="9af6f-132">Birden çok değeri var. her parametre için bir olası değerler düğüm ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9af6f-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="9af6f-133">İşte bir örnek tanımlayan iki olası değerler parametresi için olası değerler düğümü</span><span class="sxs-lookup"><span data-stu-id="9af6f-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

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

<span data-ttu-id="9af6f-134">Parametreleri eklerken hatırlamak işlemlerden bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="9af6f-135">Parametre öznitelikleri, cmdlet Yardım konusunun tüm görünümlerde görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="9af6f-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="9af6f-136">Ancak, kullanıcı için tam istediğinde parametre açıklaması izleyen bir tablo görüntülenir (Get-Help \<cmdletname >-tam) veya bir parametre (Get-Help \<cmdletname >-parametresi) konunun görünümü.</span><span class="sxs-lookup"><span data-stu-id="9af6f-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="9af6f-137">Parametre açıklaması cmdlet Yardım konusunun en önemli parçalarından biridir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="9af6f-138">Açıklama kısa yanı sıra eksiksiz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="9af6f-139">Ayrıca, parametre açıklaması iki parametre birbiriyle ne zaman etkileşim gibi çok uzun olursa, cmdlet Yardım konusunun Notlar bölümünde daha fazla içerik eklemek unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9af6f-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="9af6f-140">Parametre açıklaması, iki tür bilgisini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9af6f-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="9af6f-141">Parametresi kullanıldığında, cmdlet yapar.</span><span class="sxs-lookup"><span data-stu-id="9af6f-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="9af6f-142">Parametresi hangi geçerli bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9af6f-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="9af6f-143">Parametre değerlerini .NET Framework nesneleri ifade edilir çünkü kullanıcılar bu değerler hakkında daha fazla bilgi, geleneksel bir komut satırı Yardımı yaptıkları daha gerekir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="9af6f-144">Kullanıcı ne tür verilere parametre kabul etmek üzere tasarlanmıştır söyleyin ve örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="9af6f-145">Komut satırında parametresi belirtilmezse, kullanılan değer parametresinin varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="9af6f-146">Varsayılan değer isteğe bağlıdır ve gerekli parametreleri gibi bazı parametreler için gerekli değildir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9af6f-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="9af6f-147">Ancak, çoğu isteğe bağlı parametreler için varsayılan bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9af6f-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="9af6f-148">Varsayılan değer parametresini kullanmayan etkisini anlamak için kullanıcı yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9af6f-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="9af6f-149">Varsayılan değer "geçerli dizin" veya "Windows PowerShell için yükleme diziniyle ($pshome)" isteğe bağlı bir yol gibi çok özellikle açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9af6f-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="9af6f-150">Ayrıca, varsayılan olarak kullanılan aşağıdaki cümle gibi açıklayan bir cümle yazabilirsiniz `PassThru` parametresi: "PassThru belirtilmemişse cmdlet aşağı işlem hattı nesneleri geçmez."</span><span class="sxs-lookup"><span data-stu-id="9af6f-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="9af6f-151">Ayrıca, değeri alan adı görüntülendiğinden "**varsayılan değer**", "varsayılan değer" terimi girişi eklemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9af6f-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="9af6f-152">Parametrenin varsayılan değeri, cmdlet Yardım konusunun tüm görünümlerde görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="9af6f-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="9af6f-153">Ancak, kullanıcı için tam istediğinde parametre açıklaması aşağıdaki tabloda (parametre öznitelikleri) ile birlikte görüntülenir (Get-Help \<cmdletname >-tam) veya parametresini (Get-Help \<cmdletname >-parametresi) görünümü konu.</span><span class="sxs-lookup"><span data-stu-id="9af6f-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="9af6f-154">Aşağıdaki XML bir çift gösterir `<dev:defaultValue>` eklenen etiketler `<command:parameter>` düğümü.</span><span class="sxs-lookup"><span data-stu-id="9af6f-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="9af6f-155">Varsayılan değer kapattıktan sonra hemen takip eden bildirim `</command:parameterValue>` (parametre değeri belirtildiğinde) etiketi veya kapanış `</maml:description>` parametre açıklaması etiketi.</span><span class="sxs-lookup"><span data-stu-id="9af6f-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="9af6f-156">Adı.</span><span class="sxs-lookup"><span data-stu-id="9af6f-156">name.</span></span>

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

<span data-ttu-id="9af6f-157">Numaralandırılmış türler için değerleri ekleyin</span><span class="sxs-lookup"><span data-stu-id="9af6f-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="9af6f-158">Parametresi birden çok değer veya bir listeden seçimli türü değerlerinin varsa, isteğe bağlı kullanabilirsiniz \<dev:possibleValues > düğümü.</span><span class="sxs-lookup"><span data-stu-id="9af6f-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="9af6f-159">Bu düğüm, bir ad ve açıklama için birden çok değer belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9af6f-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="9af6f-160">Numaralandırılmış değerler açıklamaları varsayılan hiçbirinde Yardım görünüm tarafından görüntülenen görünmediğini unutmayın `Get-Help` cmdlet'i, ancak diğer Yardım görüntüleyicileri görüntüleyebilir bu içerik, görünümlerde.</span><span class="sxs-lookup"><span data-stu-id="9af6f-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="9af6f-161">Aşağıdaki XML gösterildiği bir `<dev:possibleValues>` iki değer belirtilen düğümle.</span><span class="sxs-lookup"><span data-stu-id="9af6f-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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