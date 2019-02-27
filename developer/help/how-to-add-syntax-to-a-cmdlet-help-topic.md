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
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848212"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="ac88c-102">Cmdlet Yardım Konusuna Söz Dizimi Ekleme</span><span class="sxs-lookup"><span data-stu-id="ac88c-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="ac88c-103">Parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ac88c-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="ac88c-104">Parametre değeri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ac88c-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="ac88c-105">Söz dizimi bilgileri toplanıyor</span><span class="sxs-lookup"><span data-stu-id="ac88c-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="ac88c-106">Söz dizim diyagramı görülmektedir XML kodlama</span><span class="sxs-lookup"><span data-stu-id="ac88c-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="ac88c-107">Söz dizim diyagramı görülmektedir Cmdlet Yardım hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="ac88c-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="ac88c-108">Veri türünü NET bir görüntüsünü almak için bu bölümü okuyun için söz dizim diyagramı görülmektedir cmdlet Yardım dosyasındaki XML kodunu başlamadan önce parametre öznitelikleri ve bu verileri söz dizim diyagramı görülmektedir içinde nasıl görüntüleneceğini gibi sağlamanız gerekir...</span><span class="sxs-lookup"><span data-stu-id="ac88c-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="ac88c-109">Parametre öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ac88c-109">Parameter Attributes</span></span>

- <span data-ttu-id="ac88c-110">Gerekli</span><span class="sxs-lookup"><span data-stu-id="ac88c-110">Required</span></span>

  - <span data-ttu-id="ac88c-111">TRUE ise parametresi parametre kullanan tüm komutları yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="ac88c-112">False ise parametre kümesi kullanan tüm komutlar, isteğe bağlı bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="ac88c-113">Konum</span><span class="sxs-lookup"><span data-stu-id="ac88c-113">Position</span></span>

  - <span data-ttu-id="ac88c-114">Adlı, parametre adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="ac88c-115">Konumsal, parametre adı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="ac88c-116">Atlandığında, parametre değeri komut belirtilen konumda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="ac88c-117">Konum değeri ise, örneğin, "1" = parametre değeri ilk veya yalnızca adlandırılmamış parametreyi komutta olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="ac88c-118">Ardışık giriş</span><span class="sxs-lookup"><span data-stu-id="ac88c-118">Pipeline Input</span></span>

  - <span data-ttu-id="ac88c-119">TRUE ise (ByValue) giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="ac88c-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="ac88c-120">İlişkili bir giriştir ("bağlama") ile özellik adı ve nesne türü beklenen türle eşleşmiyor olsa bile parametresi.</span><span class="sxs-lookup"><span data-stu-id="ac88c-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="ac88c-121">Windows PowerShell? parametre bağlama bileşenleri doğru türde girişi dönüştürür ve yalnızca tür dönüştürülemiyorsa komutu başarısız deneyin.</span><span class="sxs-lookup"><span data-stu-id="ac88c-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="ac88c-122">Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="ac88c-123">TRUE ise (ByPropertyName) giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="ac88c-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="ac88c-124">Ancak, parametre adı giriş nesnenin bir özelliğini adını eşleştiğinde giriş parametresi ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="ac88c-125">Örneğin, parametre adı ise `Path`, yalnızca nesne yolu adlı bir özellik varsa cmdlet'e yöneltilen nesneler bu parametre ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="ac88c-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="ac88c-126">Varsa true (ByValue, ByPropertyName), özellik adı veya değer tarafından giriş parametresine kanal oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="ac88c-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="ac88c-127">Parametre kümesi yalnızca bir parametre değerine göre ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="ac88c-128">False ise, bu parametre için kanal oluşturarak giriş aktaramazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac88c-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="ac88c-129">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="ac88c-129">Globbing</span></span>

  - <span data-ttu-id="ac88c-130">TRUE ise kullanıcı için parametre değeri türleri metin joker karakterler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="ac88c-131">False ise, kullanıcı için parametre değeri türleri metin joker karakterler içeremez.</span><span class="sxs-lookup"><span data-stu-id="ac88c-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="ac88c-132">Parametre değeri öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ac88c-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="ac88c-133">Gerekli</span><span class="sxs-lookup"><span data-stu-id="ac88c-133">Required</span></span>

  - <span data-ttu-id="ac88c-134">TRUE ise belirtilen değer, bir komut parametresi kullanıldığında kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="ac88c-135">Parametre değeri, false ise isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="ac88c-136">Genellikle, yalnızca bir parametresi için geçerli değerlerden biri gibi bir listeden seçimli türü olduğunda bir değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="ac88c-137">Gerekli bir parametre değeri parametre gerekli özniteliğinden farklı özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="ac88c-138">Gerekli öznitelik parametresinin parametre (ve değerinin) cmdlet çağrılırken dahil edilmesi gereken olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="ac88c-139">Buna karşılık, parametre yalnızca komutta eklendiğinde bir parametre değeri gerekli özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="ac88c-140">Bu, bu özel değer parametresi kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="ac88c-141">Genellikle, yer tutucuları olan parametre değerleri gereklidir ve parametresiyle birlikte kullanılan değerlerden birini olduklarından değişmez değer parametre değerlerini gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="ac88c-142">Söz dizimi bilgileri toplanıyor</span><span class="sxs-lookup"><span data-stu-id="ac88c-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="ac88c-143">Cmdlet adı ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="ac88c-144">Cmdlet tüm parametreler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="ac88c-145">Türü bir tire ("dash" veya "önce gelen eksi işaretinin" (ASCII 45) her parametre adı olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="ac88c-146">Parametreler, parametre kümeleri halinde (bazı cmdlet'ler kümesi yalnızca bir parametreye sahip) ayırın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="ac88c-147">Bu örnekte, Get-teknik cmdlet'i iki parametre kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="ac88c-148">Her parametre kümesi cmdlet adı ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="ac88c-149">İlk olarak varsayılan parametre listesi.</span><span class="sxs-lookup"><span data-stu-id="ac88c-149">List the default parameter set first.</span></span> <span data-ttu-id="ac88c-150">Varsayılan parametre cmdlet'i sınıfı tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="ac88c-151">İlk görünmelidir konumsal parametreler olmadığı sürece her parametre kümesi için benzersiz, parametresinin ilk olarak listeleyin.</span><span class="sxs-lookup"><span data-stu-id="ac88c-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="ac88c-152">Önceki örnekte adı ve kimliği iki parametre kümesi için benzersiz parametreleri parametreleridir (her parametre kümesi bu parametre kümesi için benzersiz olan bir parametreye sahip olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="ac88c-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="ac88c-153">Bu, kullanıcıların hangi parametre parametresi için sağlamak için ihtiyaç duydukları tanımlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ac88c-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="ac88c-154">Komut içinde görünmesi gereken sırayla parametreler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="ac88c-155">Sırası önemli değildir, ilgili parametreler birlikte listelemek veya öncelikle en sık kullanılan parametreleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ac88c-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="ac88c-156">Cmdlet ShouldProcess destekliyorsa WhatIf ve onaylama parametreleri listesi emin olun.</span><span class="sxs-lookup"><span data-stu-id="ac88c-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="ac88c-157">Ortak parametreler (örneğin, ayrıntı, hata ayıklama ve ErrorAction) söz dizimi diyagramınızda listelemez.</span><span class="sxs-lookup"><span data-stu-id="ac88c-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="ac88c-158">`Get-Help` Cmdlet Yardım konusunu görüntüler, bu bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="ac88c-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="ac88c-159">Parametre değerlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac88c-159">Add the parameter values.</span></span> <span data-ttu-id="ac88c-160">Windows PowerShell'de?, parametre değerlerini .NET türlerine göre temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="ac88c-161">Ancak, tür adı, System.String için "dize" gibi kısaltılmış.</span><span class="sxs-lookup"><span data-stu-id="ac88c-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="ac88c-162">Anlamları System.String için "dize" ve "int" System.Int32 gibi açık olduğu sürece türleri kısaltma.</span><span class="sxs-lookup"><span data-stu-id="ac88c-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="ac88c-163">Numaralandırmalar, tüm değerlerin gibi liste tür parametresi önceki örnekte sona eren "temel" veya "Gelişmiş" için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-163">List all values of enumerations, such as the -type parameter in the previous example, wich can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="ac88c-164">-Önceki örnekte liste gibi parametreleri değiştirmek, değeri yok.</span><span class="sxs-lookup"><span data-stu-id="ac88c-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="ac88c-165">Açılı ayraçlar sabitleridir parametre değerlerini karşılaştırıldığında yer tutucu olan parametre değerleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac88c-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="ac88c-166">İsteğe bağlı parametreler ve bunların değerleri köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="ac88c-167">İsteğe bağlı parametre adları (için konumsal parametreleri) köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="ac88c-168">Adı aşağıdaki örnekte, Name parametresi gibi konumsal parametreler için komutta dahil edilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ac88c-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="ac88c-169">Name parametresi adları listesi gibi birden çok değer içeren bir parametre değeri, bir parametre değeri doğrudan aşağıdaki köşeli çift ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac88c-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="ac88c-170">Kullanıcı, parametre veya parametre değerlerini seçebilir, tür parametresi gibi seçenekler kaşlı ayraçlar içine alın ve özel veya symbol(;) ile ayırarak.</span><span class="sxs-lookup"><span data-stu-id="ac88c-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="ac88c-171">Parametre değeri tırnak işareti veya parantezler, gibi belirli biçimlendirme kullanmanız gerekiyorsa sözdiziminde biçimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="ac88c-172">Söz dizim diyagramı görülmektedir XML kodlama</span><span class="sxs-lookup"><span data-stu-id="ac88c-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="ac88c-173">XML sözdizimi düğümü hemen ile biten açıklama düğümü sonra başlar \</maml:description > etiketi.</span><span class="sxs-lookup"><span data-stu-id="ac88c-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="ac88c-174">Söz dizimi diyagramda kullanılan veri toplama hakkında daha fazla bilgi için bkz: [söz dizimi bilgi toplama](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="ac88c-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="ac88c-175">Sözdizimi düğümü ekleme</span><span class="sxs-lookup"><span data-stu-id="ac88c-175">Adding a Syntax Node</span></span>

<span data-ttu-id="ac88c-176">Cmdlet Yardım konusundaki görüntülenen söz dizim diyagramı görülmektedir XML sözdizimi düğümü verilerden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ac88c-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="ac88c-177">Sözdizimi düğümü ise bir çiftini alınmış \<sözdizimi: > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="ac88c-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="ac88c-178">Bir çift içine cmdlet her parametre kümesi ile \<komutu: syntaxitem > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="ac88c-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="ac88c-179">Sınırsız sayıda \<komutu: syntaxitem > etiketleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac88c-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="ac88c-180">Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="ac88c-181">Veri kümesi Cmdlet adı parametresi ekleme</span><span class="sxs-lookup"><span data-stu-id="ac88c-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="ac88c-182">Her parametre kümesi cmdlet sözdizimi öğesi düğümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="ac88c-183">Her sözdizimi öğesi düğüm çifti ile başlar \<maml:name > cmdlet'in adını içeren etiketler.</span><span class="sxs-lookup"><span data-stu-id="ac88c-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="ac88c-184">Aşağıdaki örnek, iki parametre kümeleri için sözdizimi öğesi düğüme sahip bir sözdizimi düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="ac88c-185">Parametre ekleme</span><span class="sxs-lookup"><span data-stu-id="ac88c-185">Adding Parameters</span></span>

<span data-ttu-id="ac88c-186">Sözdizimi öğesi düğüme eklenen her bir parametre bir çift içinde belirtilen \<komut: parametresi > etiketleri.</span><span class="sxs-lookup"><span data-stu-id="ac88c-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="ac88c-187">Bir çift ihtiyacınız \<komut: parametresi > etiketleri parametre kümesi, Windows PowerShell tarafından sağlanan ortak parametrelerin dışında bulunan her bir parametreye?</span><span class="sxs-lookup"><span data-stu-id="ac88c-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="ac88c-188">Açılış özniteliklerini \<komut: parametresi > etiketi belirlemek nasıl parametresi söz dizimi diyagramda görünür.</span><span class="sxs-lookup"><span data-stu-id="ac88c-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="ac88c-189">Parametre öznitelikleri hakkında daha fazla bilgi için bkz: [parametre öznitelikleri](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="ac88c-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="ac88c-190">\<Komut: parametresi > etiketi, bir alt öğesi destekliyor \<maml:description > içeriğe sahip hiçbir zaman görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="ac88c-191">Parametre açıklamaları parametre'XML düğümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="ac88c-192">Söz dizimi öğesi bilgiler arasındaki tutarsızlıkları önlemek için bodes ve parametre düğümü çıkarın (\<maml:description > veya bu alanı boş bırakın.</span><span class="sxs-lookup"><span data-stu-id="ac88c-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="ac88c-193">Aşağıdaki örnek, bir parametre kümesi ile iki parametre için bir sözdizimi öğe düğümü içerir.</span><span class="sxs-lookup"><span data-stu-id="ac88c-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
