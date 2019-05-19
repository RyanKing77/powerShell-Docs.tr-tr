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
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855144"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="c7784-102">Cmdlet Yardım Konusuna Söz Dizimi Ekleme</span><span class="sxs-lookup"><span data-stu-id="c7784-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="c7784-103">Veri türünü NET bir görüntüsünü almak için bu bölümü okuyun için söz dizim diyagramı görülmektedir cmdlet Yardım dosyasındaki XML kodunu başlamadan önce parametre öznitelikleri ve bu verileri söz dizim diyagramı görülmektedir içinde nasıl görüntüleneceğini gibi sağlamanız gerekir...</span><span class="sxs-lookup"><span data-stu-id="c7784-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="c7784-104">Parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7784-104">Parameter Attributes</span></span>

- <span data-ttu-id="c7784-105">Gerekli</span><span class="sxs-lookup"><span data-stu-id="c7784-105">Required</span></span>

  - <span data-ttu-id="c7784-106">TRUE ise parametresi parametre kullanan tüm komutları yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="c7784-107">False ise parametre kümesi kullanan tüm komutlar, isteğe bağlı bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="c7784-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="c7784-108">Konum</span><span class="sxs-lookup"><span data-stu-id="c7784-108">Position</span></span>

  - <span data-ttu-id="c7784-109">Adlı, parametre adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c7784-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="c7784-110">Konumsal, parametre adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="c7784-111">Atlandığında, parametre değeri komut belirtilen konumda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="c7784-112">Konum değeri ise, örneğin, "1" = parametre değeri ilk veya yalnızca adlandırılmamış parametreyi komutta olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7784-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="c7784-113">Ardışık giriş</span><span class="sxs-lookup"><span data-stu-id="c7784-113">Pipeline Input</span></span>

  - <span data-ttu-id="c7784-114">TRUE ise (ByValue) giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="c7784-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="c7784-115">İlişkili bir giriştir ("bağlama") ile özellik adı ve nesne türü beklenen türle eşleşmiyor olsa bile parametresi.</span><span class="sxs-lookup"><span data-stu-id="c7784-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="c7784-116">Windows PowerShell? parametre bağlama bileşenleri doğru türde girişi dönüştürür ve yalnızca tür dönüştürülemiyorsa komutu başarısız deneyin.</span><span class="sxs-lookup"><span data-stu-id="c7784-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="c7784-117">Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="c7784-118">TRUE ise (ByPropertyName) giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="c7784-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="c7784-119">Ancak, parametre adı giriş nesnenin bir özelliğini adını eşleştiğinde giriş parametresi ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="c7784-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="c7784-120">Örneğin, parametre adı ise `Path`, yalnızca nesne yolu adlı bir özellik varsa cmdlet'e yöneltilen nesneler bu parametre ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="c7784-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="c7784-121">Varsa true (ByValue, ByPropertyName), özellik adı veya değer tarafından giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="c7784-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="c7784-122">Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="c7784-123">False ise, bu parametre için kanal oluşturarak giriş aktaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="c7784-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="c7784-124">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="c7784-124">Globbing</span></span>

  - <span data-ttu-id="c7784-125">TRUE ise kullanıcı için parametre değeri türleri metin joker karakterler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="c7784-126">False ise, kullanıcı için parametre değeri türleri metin joker karakterler içeremez.</span><span class="sxs-lookup"><span data-stu-id="c7784-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="c7784-127">Parametre değeri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c7784-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="c7784-128">Gerekli</span><span class="sxs-lookup"><span data-stu-id="c7784-128">Required</span></span>

  - <span data-ttu-id="c7784-129">TRUE ise belirtilen değer, bir komut parametresi kullanıldığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="c7784-130">Parametre değeri, false ise isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="c7784-131">Genellikle, yalnızca bir parametresi için geçerli değerlerden biri gibi bir listeden seçimli türü olduğunda bir değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7784-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="c7784-132">Gerekli bir parametre değeri parametre gerekli özniteliğinden farklı özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="c7784-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="c7784-133">Gerekli öznitelik parametresinin parametre (ve değerinin) cmdlet çağrılırken dahil edilmesi gereken olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7784-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="c7784-134">Buna karşılık, parametre yalnızca komutta eklendiğinde bir parametre değeri gerekli özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7784-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="c7784-135">Bu, bu özel değer parametresi kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7784-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="c7784-136">Genellikle, yer tutucuları olan parametre değerleri gereklidir ve parametresiyle birlikte kullanılan değerlerden birini olduklarından değişmez değer parametre değerlerini gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c7784-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="c7784-137">Söz dizimi bilgileri toplanıyor</span><span class="sxs-lookup"><span data-stu-id="c7784-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="c7784-138">Cmdlet adı ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="c7784-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="c7784-139">Cmdlet tüm parametreler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7784-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="c7784-140">Türü bir tire ("dash" veya "önce gelen eksi işaretinin" (ASCII 45) her parametre adı olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="c7784-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="c7784-141">Parametreler, parametre kümeleri halinde (bazı cmdlet'ler kümesi yalnızca bir parametreye sahip) ayırın.</span><span class="sxs-lookup"><span data-stu-id="c7784-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="c7784-142">Bu örnekte, Get-teknik cmdlet'i iki parametre kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7784-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="c7784-143">Her parametre kümesi cmdlet adı ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="c7784-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="c7784-144">İlk olarak varsayılan parametre listesi.</span><span class="sxs-lookup"><span data-stu-id="c7784-144">List the default parameter set first.</span></span> <span data-ttu-id="c7784-145">Varsayılan parametre cmdlet'i sınıfı tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="c7784-146">İlk görünmelidir konumsal parametreler olmadığı sürece her parametre kümesi için benzersiz, parametresinin ilk olarak listeleyin.</span><span class="sxs-lookup"><span data-stu-id="c7784-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="c7784-147">Önceki örnekte adı ve kimliği iki parametre kümesi için benzersiz parametreleri parametreleridir (her parametre kümesi bu parametre kümesi için benzersiz olan bir parametreye sahip olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="c7784-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="c7784-148">Bu, kullanıcıların hangi parametre parametresi için sağlamak için ihtiyaç duydukları tanımlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7784-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="c7784-149">Komut içinde görünmesi gereken sırayla parametreler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c7784-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="c7784-150">Sırası önemli değildir, ilgili parametreler birlikte listelemek veya öncelikle en sık kullanılan parametreleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c7784-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="c7784-151">Cmdlet ShouldProcess destekliyorsa WhatIf ve onaylama parametreleri listesi emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7784-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="c7784-152">Ortak parametreler (örneğin, ayrıntı, hata ayıklama ve ErrorAction) söz dizimi diyagramınızda listelemez.</span><span class="sxs-lookup"><span data-stu-id="c7784-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="c7784-153">`Get-Help` Cmdlet Yardım konusunu görüntüler, bu bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="c7784-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="c7784-154">Parametre değerlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7784-154">Add the parameter values.</span></span> <span data-ttu-id="c7784-155">Windows PowerShell'de?, parametre değerlerini .NET türlerine göre temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="c7784-156">Ancak, tür adı, System.String için "dize" gibi kısaltılmış.</span><span class="sxs-lookup"><span data-stu-id="c7784-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="c7784-157">Anlamları System.String için "dize" ve "int" System.Int32 gibi açık olduğu sürece türleri kısaltma.</span><span class="sxs-lookup"><span data-stu-id="c7784-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="c7784-158">Numaralandırmalar, tüm değerlerin listesi gibi tür parametresi önceki örnekte, "temel" veya "Gelişmiş" olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="c7784-159">-Önceki örnekte liste gibi parametreleri değiştirmek, değeri yok.</span><span class="sxs-lookup"><span data-stu-id="c7784-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="c7784-160">Açılı ayraçlar sabitleridir parametre değerlerini karşılaştırıldığında yer tutucu olan parametre değerleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7784-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="c7784-161">İsteğe bağlı parametreler ve bunların değerleri köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="c7784-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="c7784-162">İsteğe bağlı parametre adları (için konumsal parametreleri) köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="c7784-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="c7784-163">Adı aşağıdaki örnekte, Name parametresi gibi konumsal parametreler için komutta dahil edilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c7784-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="c7784-164">Name parametresi adları listesi gibi birden çok değer içeren bir parametre değeri, bir parametre değeri doğrudan aşağıdaki köşeli çift ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c7784-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="c7784-165">Kullanıcı, parametre veya parametre değerlerini seçebilir, tür parametresi gibi seçenekler kaşlı ayraçlar içine alın ve özel veya symbol(;) ile ayırarak.</span><span class="sxs-lookup"><span data-stu-id="c7784-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="c7784-166">Parametre değeri tırnak işareti veya parantezler, gibi belirli biçimlendirme kullanmanız gerekiyorsa sözdiziminde biçimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7784-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="c7784-167">Söz dizim diyagramı görülmektedir XML kodlama</span><span class="sxs-lookup"><span data-stu-id="c7784-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="c7784-168">XML sözdizimi düğümü hemen ile biten açıklama düğümü sonra başlar \</maml:description > etiketi.</span><span class="sxs-lookup"><span data-stu-id="c7784-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="c7784-169">Söz dizimi diyagramda kullanılan veri toplama hakkında daha fazla bilgi için bkz: [söz dizimi bilgi toplama](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="c7784-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="c7784-170">Sözdizimi düğümü ekleme</span><span class="sxs-lookup"><span data-stu-id="c7784-170">Adding a Syntax Node</span></span>

<span data-ttu-id="c7784-171">Cmdlet Yardım konusundaki görüntülenen söz dizim diyagramı görülmektedir XML sözdizimi düğümü verilerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7784-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="c7784-172">Sözdizimi düğümü ise bir çiftini alınmış \<sözdizimi: > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="c7784-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="c7784-173">Bir çift içine cmdlet her parametre kümesi ile \<komutu: syntaxitem > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="c7784-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="c7784-174">Sınırsız sayıda \<komutu: syntaxitem > etiketleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7784-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="c7784-175">Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7784-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="c7784-176">Veri kümesi Cmdlet adı parametresi ekleme</span><span class="sxs-lookup"><span data-stu-id="c7784-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="c7784-177">Her parametre kümesi cmdlet sözdizimi öğesi düğümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="c7784-178">Her sözdizimi öğesi düğüm çifti ile başlar \<maml:name > cmdlet'in adını içeren etiketler.</span><span class="sxs-lookup"><span data-stu-id="c7784-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="c7784-179">Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="c7784-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="c7784-180">Parametre ekleme</span><span class="sxs-lookup"><span data-stu-id="c7784-180">Adding Parameters</span></span>

<span data-ttu-id="c7784-181">Sözdizimi öğesi düğüme eklenen her bir parametre bir çift içinde belirtilen \<komut: parametresi > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="c7784-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="c7784-182">Bir çift ihtiyacınız \<komut: parametresi > etiketleri parametre kümesi, Windows PowerShell tarafından sağlanan ortak parametrelerin dışında bulunan her bir parametreye?</span><span class="sxs-lookup"><span data-stu-id="c7784-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="c7784-183">Açılış özniteliklerini \<komut: parametresi > etiketi belirlemek nasıl parametresi söz dizimi diyagramda görünür.</span><span class="sxs-lookup"><span data-stu-id="c7784-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="c7784-184">Parametre öznitelikleri hakkında daha fazla bilgi için bkz: [parametre öznitelikleri](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="c7784-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="c7784-185">\<Komut: parametresi > etiketi, bir alt öğesi destekliyor \<maml:description > içeriğe sahip hiçbir zaman görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c7784-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="c7784-186">Parametre açıklamaları parametre'XML düğümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c7784-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="c7784-187">Söz dizimi öğesi bilgiler arasındaki tutarsızlıkları önlemek için bodes ve parametre düğümü çıkarın (\<maml:description > veya bu alanı boş bırakın.</span><span class="sxs-lookup"><span data-stu-id="c7784-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="c7784-188">Aşağıdaki örnek, bir parametre kümesi ile iki parametre için bir sözdizimi öğe düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="c7784-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
