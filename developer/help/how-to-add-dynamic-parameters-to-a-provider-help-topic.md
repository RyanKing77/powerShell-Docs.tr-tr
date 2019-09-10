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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848123"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="a2e4d-102">Sağlayıcı Yardım Konusuna Dinamik Parametreler Ekleme</span><span class="sxs-lookup"><span data-stu-id="a2e4d-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="a2e4d-103">Bu bölümde, bir sağlayıcı Yardım konusunun **dınamık parametreler** bölümünün nasıl doldurulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="a2e4d-104">*Dinamik parametreler* yalnızca belirtilen koşullarda kullanılabilen bir cmdlet veya işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="a2e4d-105">Sağlayıcı yardım konusunda belgelenen dinamik parametreler, sağlayıcının cmdlet 'i veya işlevi sağlayıcı sürücüsünde kullanıldığında cmdlet veya işleve eklediği dinamik parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="a2e4d-106">Dinamik parametreler, bir sağlayıcı için özel cmdlet yardımı 'nda da açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="a2e4d-107">Sağlayıcı için hem sağlayıcı yardımını hem de özel cmdlet yardımını yazarken, dinamik parametre belgelerini her iki belgeye de ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="a2e4d-108">Bir sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, sağlayıcı yardım konusu boş `DynamicParameters` bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="a2e4d-109">Dinamik parametreler eklemek için</span><span class="sxs-lookup"><span data-stu-id="a2e4d-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="a2e4d-110">*AssemblyName*. dll-Help. xml dosyasında, `providerHelp` öğesi içinde, bir `DynamicParameters` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="a2e4d-111">Öğe, `Tasks` öğesinden sonra ve öğesinden önce `RelatedLinks` görünmelidir. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="a2e4d-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="a2e4d-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a2e4d-112">For example:</span></span>

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

   <span data-ttu-id="a2e4d-113">Sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, `DynamicParameters` öğe boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="a2e4d-114">Öğesi içinde, her dinamik parametre için bir `DynamicParameter` öğesi ekleyin. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="a2e4d-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="a2e4d-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a2e4d-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="a2e4d-116">Her `DynamicParameter` öğesinde bir `Name` ve `CmdletSupported` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="a2e4d-117">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="a2e4d-117">Element Name</span></span>|<span data-ttu-id="a2e4d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e4d-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="a2e4d-119">Adı</span><span class="sxs-lookup"><span data-stu-id="a2e4d-119">Name</span></span>|<span data-ttu-id="a2e4d-120">Parametrenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="a2e4d-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="a2e4d-121">CmdletSupported</span></span>|<span data-ttu-id="a2e4d-122">Parametresinin geçerli olduğu cmdlet 'leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="a2e4d-123">Cmdlet adlarının virgülle ayrılmış bir listesini yazın.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="a2e4d-124">Örneğin, aşağıdaki XML, Windows PowerShell FileSystem `Encoding` sağlayıcısının `Add-Content`, `Get-Content` `Set-Content` , cmdlet 'lerine eklediği dinamik parametreyi belgeler.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="a2e4d-125">Her `DynamicParameter` öğesinde bir `Type` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="a2e4d-126">Öğesi, dinamik parametre değerinin .NET türünü `Name` içeren öğesi için bir kapsayıcıdır. `Type`</span><span class="sxs-lookup"><span data-stu-id="a2e4d-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="a2e4d-127">Örneğin, aşağıdaki XML, `Encoding` dinamik parametrenin .NET türünün [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) numaralandırması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="a2e4d-128">Dinamik parametrenin kısa bir açıklamasını içeren öğesiniekleyin.`Description`</span><span class="sxs-lookup"><span data-stu-id="a2e4d-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="a2e4d-129">Açıklamayı oluştururken [parametre bilgilerini ekleme](./how-to-add-parameter-information.md)içindeki tüm cmdlet parametreleri için önceden belirlenmiş olan yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="a2e4d-130">Örneğin, aşağıdaki XML `Encoding` dinamik parametrenin açıklamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="a2e4d-131">`PossibleValues` Öğesi ve alt öğelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="a2e4d-132">Birlikte, bu öğeler dinamik parametrenin değerlerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="a2e4d-133">Bu öğe, numaralandırılmış değerler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="a2e4d-134">Dinamik parametre bir değer almaz (örneğin, bir switch parametresi ile birlikte) veya değerler numaralandırılamıyor, boş `PossibleValues` bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="a2e4d-135">Aşağıdaki tabloda `PossibleValues` öğesi ve alt öğeleri listelenmektedir ve açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="a2e4d-136">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="a2e4d-136">Element Name</span></span>|<span data-ttu-id="a2e4d-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e4d-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="a2e4d-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="a2e4d-138">PossibleValues</span></span>|<span data-ttu-id="a2e4d-139">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-139">This element is a container.</span></span> <span data-ttu-id="a2e4d-140">Alt öğeleri aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-140">Its child elements are described below.</span></span> <span data-ttu-id="a2e4d-141">Her sağlayıcı `PossibleValues` yardım konusuna bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="a2e4d-142">Öğe boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-142">The element can be empty.</span></span>|
   |<span data-ttu-id="a2e4d-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="a2e4d-143">PossibleValue</span></span>|<span data-ttu-id="a2e4d-144">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-144">This element is a container.</span></span> <span data-ttu-id="a2e4d-145">Alt öğeleri aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-145">Its child elements are described below.</span></span> <span data-ttu-id="a2e4d-146">Dinamik parametrenin `PossibleValue` her bir değeri için bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="a2e4d-147">Değer</span><span class="sxs-lookup"><span data-stu-id="a2e4d-147">Value</span></span>|<span data-ttu-id="a2e4d-148">Değer adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="a2e4d-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e4d-149">Description</span></span>|<span data-ttu-id="a2e4d-150">Bu öğe bir `Para` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-150">This element contains a `Para` element.</span></span> <span data-ttu-id="a2e4d-151">`Para` Öğesindeki metin, `Value` öğesinde adı geçen değeri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="a2e4d-152">Örneğin, aşağıdaki XML `PossibleValue` `Encoding` dinamik parametrenin bir öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="a2e4d-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2e4d-153">Example</span></span>

<span data-ttu-id="a2e4d-154">Aşağıdaki örnek, `Encoding` dinamik parametrenin `DynamicParameters` öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e4d-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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