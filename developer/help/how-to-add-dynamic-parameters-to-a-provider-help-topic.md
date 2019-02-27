---
title: Dinamik parametreler için sağlayıcı Yardım konusunun ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849528"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="c0f8b-102">Sağlayıcı Yardım Konusuna Dinamik Parametreler Ekleme</span><span class="sxs-lookup"><span data-stu-id="c0f8b-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="c0f8b-103">Bu bölümde doldurmak açıklanmaktadır **dinamik parametreleri** sağlayıcısı Yardım konusunun bölümü.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="c0f8b-104">*Dinamik parametreleri* bir cmdlet parametreleri veya yalnızca şuranın altında kullanılabilir işlev belirtilen koşullar.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="c0f8b-105">Bir sağlayıcı Yardım konusunda belgelenen dinamik parametreleri cmdlet'ini veya işlev sağlayıcısı sürücüde kullanıldığında, cmdlet veya işlevi için sağlayıcı ekler dinamik parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="c0f8b-106">Sağlayıcı için özel cmdlet Yardımı'nda dinamik parametreler de belgelenen.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="c0f8b-107">Sağlayıcısı için sağlayıcı Yardım hem özel cmdlet yardımına yazarken, hem belgelerde dinamik parametre belgeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="c0f8b-108">Özel cmdlet Yardım hakkında daha fazla bilgi için bkz: [yazma Windows PowerShell özel Cmdlet için Yardım sağlayıcıları](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="c0f8b-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="c0f8b-109">Bir sağlayıcı, herhangi bir dinamik parametre uygulamaz, boş bir sağlayıcı Yardım konusuna içeren `DynamicParameters` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="c0f8b-110">Dinamik parametreleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="c0f8b-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="c0f8b-111">İçinde *AssemblyName*içinde help.xml .dll dosyası `providerHelp` öğe, Ekle bir `DynamicParameters` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="c0f8b-112">`DynamicParameters` Öğesi sonra görüntülenmelidir `Tasks` öğesi ve önce `RelatedLinks` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="c0f8b-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c0f8b-113">For example:</span></span>

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

   <span data-ttu-id="c0f8b-114">Sağlayıcı, herhangi bir dinamik parametre uygulamıyorsa `DynamicParameters` öğesi boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="c0f8b-115">İçinde `DynamicParameters` her dinamik bir parametre için bir öğe ekleme bir `DynamicParameter` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="c0f8b-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c0f8b-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="c0f8b-117">Her `DynamicParameter` öğe, Ekle bir `Name` ve `CmdletSupported` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="c0f8b-118">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="c0f8b-118">Element Name</span></span>|<span data-ttu-id="c0f8b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0f8b-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c0f8b-120">Adı</span><span class="sxs-lookup"><span data-stu-id="c0f8b-120">Name</span></span>|<span data-ttu-id="c0f8b-121">Parametre adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="c0f8b-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="c0f8b-122">CmdletSupported</span></span>|<span data-ttu-id="c0f8b-123">Parametrenin geçerli olduğundan cmdlet'leri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="c0f8b-124">Cmdlet adları virgülle ayrılmış bir listesini yazın.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="c0f8b-125">Örneğin, aşağıdaki XML belgeleri `Encoding` Windows PowerShell dosya sistemi sağlayıcısı ekler dinamik parametre `Add-Content`, `Get-Content`, `Set-Content` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="c0f8b-126">Her `DynamicParameter` öğe, Ekle bir `Type` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="c0f8b-127">`Type` Öğesi için bir kapsayıcıdır `Name` dinamik parametre değerini .NET türünü içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="c0f8b-128">Örneğin, .NET türünü gösteren aşağıdaki XML `Encoding` dinamik parametredir [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="c0f8b-129">Ekleme `Description` dinamik parametre kısa bir açıklamasını içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="c0f8b-130">Açıklama oluştururken de tüm cmdlet parametreleri için belirlenen yönergeleri kullanın [parametre bilgilerini ekleme](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="c0f8b-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="c0f8b-131">Örneğin, aşağıdaki XML açıklamasını içerir `Encoding` dinamik parametre.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="c0f8b-132">Ekleme `PossibleValues` öğesi ve onun alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="c0f8b-133">Birlikte, bu öğeleri dinamik parametre değerleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="c0f8b-134">Bu öğe Enum değerleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="c0f8b-135">Dinamik parametre bir değer almaz, anahtar parametresi gibi olduğu ve değerleri numaralandırılamıyor, boş bir ekleme `PossibleValues` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="c0f8b-136">Aşağıdaki tabloda listelenmekte ve açıklanmaktadır `PossibleValues` öğesi ve onun alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="c0f8b-137">Öğe Adı</span><span class="sxs-lookup"><span data-stu-id="c0f8b-137">Element Name</span></span>|<span data-ttu-id="c0f8b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0f8b-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="c0f8b-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="c0f8b-139">PossibleValues</span></span>|<span data-ttu-id="c0f8b-140">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-140">This element is a container.</span></span> <span data-ttu-id="c0f8b-141">Alt öğeleri, aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-141">Its child elements are described below.</span></span> <span data-ttu-id="c0f8b-142">Eklemesini `PossibleValues` her sağlayıcısı Yardım konusu öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="c0f8b-143">Öğe boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-143">The element can be empty.</span></span>|
   |<span data-ttu-id="c0f8b-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="c0f8b-144">PossibleValue</span></span>|<span data-ttu-id="c0f8b-145">Bu öğe bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-145">This element is a container.</span></span> <span data-ttu-id="c0f8b-146">Alt öğeleri, aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-146">Its child elements are described below.</span></span> <span data-ttu-id="c0f8b-147">Eklemesini `PossibleValue` her dinamik parametresinin değeri için öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="c0f8b-148">Değer</span><span class="sxs-lookup"><span data-stu-id="c0f8b-148">Value</span></span>|<span data-ttu-id="c0f8b-149">Değer adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="c0f8b-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0f8b-150">Description</span></span>|<span data-ttu-id="c0f8b-151">Bu öğeyi içeren bir `Para` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-151">This element contains a `Para` element.</span></span> <span data-ttu-id="c0f8b-152">Metinde `Para` açıklar adlı değer `Value` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="c0f8b-153">Örneğin, aşağıdaki XML bir gösterir `PossibleValue` öğesinin `Encoding` dinamik parametre.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="c0f8b-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0f8b-154">Example</span></span>

<span data-ttu-id="c0f8b-155">Aşağıdaki örnekte gösterildiği `DynamicParameters` öğesinin `Encoding` dinamik parametre.</span><span class="sxs-lookup"><span data-stu-id="c0f8b-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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