---
title: Sağlayıcıya dinamik parametreler ekleme Yardım konusu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737594"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="35798-102">Sağlayıcı Yardım Konusuna Dinamik Parametreler Ekleme</span><span class="sxs-lookup"><span data-stu-id="35798-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="35798-103">Bu bölümde, bir sağlayıcı Yardım konusunun **dınamık parametreler** bölümünün nasıl doldurulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35798-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="35798-104">*Dinamik parametreler* yalnızca belirtilen koşullarda kullanılabilen bir cmdlet veya işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="35798-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="35798-105">Sağlayıcı yardım konusunda belgelenen dinamik parametreler, sağlayıcının cmdlet 'i veya işlevi sağlayıcı sürücüsünde kullanıldığında cmdlet veya işleve eklediği dinamik parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="35798-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="35798-106">Dinamik parametreler, bir sağlayıcı için özel cmdlet yardımı 'nda da açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35798-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="35798-107">Sağlayıcı için hem sağlayıcı yardımını hem de özel cmdlet yardımını yazarken, dinamik parametre belgelerini her iki belgeye de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="35798-108">Özel cmdlet yardımı hakkında daha fazla bilgi için bkz. [sağlayıcılar Için Windows PowerShell özel cmdlet yardımı yazma](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="35798-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="35798-109">Bir sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, sağlayıcı yardım konusu boş `DynamicParameters` bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="35798-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="35798-110">Dinamik parametreler eklemek için</span><span class="sxs-lookup"><span data-stu-id="35798-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="35798-111">*AssemblyName*. dll-Help. xml dosyasında, `providerHelp` öğesi içinde, bir `DynamicParameters` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="35798-112">Öğe, `Tasks` öğesinden sonra ve öğesinden önce `RelatedLinks` görünmelidir. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="35798-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="35798-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35798-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="35798-114">Sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, `DynamicParameters` öğe boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="35798-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="35798-115">Öğesi içinde, her dinamik parametre için bir `DynamicParameter` öğesi ekleyin. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="35798-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="35798-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35798-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="35798-117">Her `DynamicParameter` öğesinde bir `Name` ve `CmdletSupported` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="35798-118">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="35798-118">Element Name</span></span>|<span data-ttu-id="35798-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35798-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="35798-120">Adı</span><span class="sxs-lookup"><span data-stu-id="35798-120">Name</span></span>|<span data-ttu-id="35798-121">Parametrenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35798-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="35798-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="35798-122">CmdletSupported</span></span>|<span data-ttu-id="35798-123">Parametresinin geçerli olduğu cmdlet 'leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="35798-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="35798-124">Cmdlet adlarının virgülle ayrılmış bir listesini yazın.</span><span class="sxs-lookup"><span data-stu-id="35798-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="35798-125">Örneğin, aşağıdaki XML, Windows PowerShell FileSystem `Encoding` sağlayıcısının `Add-Content`, `Get-Content` `Set-Content` , cmdlet 'lerine eklediği dinamik parametreyi belgeler.</span><span class="sxs-lookup"><span data-stu-id="35798-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="35798-126">Her `DynamicParameter` öğesinde bir `Type` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="35798-127">Öğesi, dinamik parametre değerinin .NET türünü `Name` içeren öğesi için bir kapsayıcıdır. `Type`</span><span class="sxs-lookup"><span data-stu-id="35798-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="35798-128">Örneğin, aşağıdaki XML, `Encoding` dinamik parametrenin .NET türünün [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) numaralandırması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="35798-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="35798-129">Dinamik parametrenin kısa bir açıklamasını içeren öğesiniekleyin.`Description`</span><span class="sxs-lookup"><span data-stu-id="35798-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="35798-130">Açıklamayı oluştururken [parametre bilgilerini ekleme](./how-to-add-parameter-information.md)içindeki tüm cmdlet parametreleri için önceden belirlenmiş olan yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="35798-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="35798-131">Örneğin, aşağıdaki XML `Encoding` dinamik parametrenin açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="35798-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="35798-132">`PossibleValues` Öğesi ve alt öğelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="35798-133">Birlikte, bu öğeler dinamik parametrenin değerlerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35798-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="35798-134">Bu öğe, numaralandırılmış değerler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="35798-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="35798-135">Dinamik parametre bir değer almaz (örneğin, bir switch parametresi ile birlikte) veya değerler numaralandırılamıyor, boş `PossibleValues` bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="35798-136">Aşağıdaki tabloda `PossibleValues` öğesi ve alt öğeleri listelenmektedir ve açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35798-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="35798-137">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="35798-137">Element Name</span></span>|<span data-ttu-id="35798-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35798-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="35798-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="35798-139">PossibleValues</span></span>|<span data-ttu-id="35798-140">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="35798-140">This element is a container.</span></span> <span data-ttu-id="35798-141">Alt öğeleri aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="35798-141">Its child elements are described below.</span></span> <span data-ttu-id="35798-142">Her sağlayıcı `PossibleValues` yardım konusuna bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="35798-143">Öğe boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="35798-143">The element can be empty.</span></span>|
   |<span data-ttu-id="35798-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="35798-144">PossibleValue</span></span>|<span data-ttu-id="35798-145">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="35798-145">This element is a container.</span></span> <span data-ttu-id="35798-146">Alt öğeleri aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="35798-146">Its child elements are described below.</span></span> <span data-ttu-id="35798-147">Dinamik parametrenin `PossibleValue` her bir değeri için bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35798-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="35798-148">Değer</span><span class="sxs-lookup"><span data-stu-id="35798-148">Value</span></span>|<span data-ttu-id="35798-149">Değer adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35798-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="35798-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35798-150">Description</span></span>|<span data-ttu-id="35798-151">Bu öğe bir `Para` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="35798-151">This element contains a `Para` element.</span></span> <span data-ttu-id="35798-152">`Para` Öğesindeki metin, `Value` öğesinde adı geçen değeri açıklar.</span><span class="sxs-lookup"><span data-stu-id="35798-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="35798-153">Örneğin, aşağıdaki XML `PossibleValue` `Encoding` dinamik parametrenin bir öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="35798-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="35798-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="35798-154">Example</span></span>

<span data-ttu-id="35798-155">Aşağıdaki örnek, `Encoding` dinamik parametrenin `DynamicParameters` öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="35798-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```