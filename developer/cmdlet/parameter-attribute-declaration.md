---
title: Parametre özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067561"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="f4bbe-102">Parametre Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f4bbe-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="f4bbe-103">Parametre özniteliği, bir cmdlet parametresi olarak cmdlet'i sınıfın ortak bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4bbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4bbe-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="f4bbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4bbe-105">Parameters</span></span>

<span data-ttu-id="f4bbe-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-107">`True` cmdlet parametresi gereklidir gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="f4bbe-108">Windows PowerShell cmdlet çalıştırıldığında bir gerekli parametresi sağlanmadı değilse, kullanıcı için bir parametre değeri ister.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="f4bbe-109">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-109">The default is `false`.</span></span>

<span data-ttu-id="f4bbe-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-111">Bu cmdlet parametresi ait olduğu parametre belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="f4bbe-112">Hiçbir parametre kümesi belirtilirse, parametre için tüm parametre kümeleri aittir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="f4bbe-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-113">`Position` ([System.Integer](/dotnet/api/System.Integer)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-114">Bir Windows PowerShell komutu içinde parametre konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="f4bbe-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-116">`True` cmdlet parametresi değerini bir işlem hattı nesnesinden aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="f4bbe-117">Cmdlet tam erişirse, bu anahtar sözcük belirtin. nesne, nesnenin yalnızca bir özellik.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="f4bbe-118">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-118">The default is `false`.</span></span>

<span data-ttu-id="f4bbe-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-120">`True` cmdlet parametresi değerini aynı ada veya bu parametre aynı ada sahip bir işlem hattı nesnenin bir özelliğini aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="f4bbe-121">Cmdlet varsa, örneğin, bir `Name` parametresi ve işlem hattı nesne de sahip bir `Name` özelliği, değeri `Name` özelliği atanır `Name` cmdlet parametresi.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="f4bbe-122">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-122">The default is `false`.</span></span>

<span data-ttu-id="f4bbe-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) isteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f4bbe-124">`True` cmdlet parametresi cmdlet'e geçirilen tüm kalan bağımsız değişkenleri kabul ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="f4bbe-125">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-125">The default is `false`.</span></span>

<span data-ttu-id="f4bbe-126">`HelpMessage` İsteğe bağlı parametre adı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="f4bbe-127">Parametre kısa bir açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="f4bbe-128">Windows PowerShell cmdlet'i çalıştırdığınızda ve zorunlu bir parametre belirtilmezse bu iletiyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="f4bbe-129">`HelpMessageBaseName` İsteğe bağlı parametre adı. Kaynak Tanımlayıcıları bulunduğu konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="f4bbe-130">Örneğin, bu parametre Yerelleştirmek istediğiniz Yardım iletileri içeren bir kaynak derlemesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="f4bbe-131">`HelpMessageResourceId` İsteğe bağlı parametre adı. Yardım iletisi kaynak tanımlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4bbe-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4bbe-132">Remarks</span></span>

- <span data-ttu-id="f4bbe-133">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f4bbe-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="f4bbe-134">Bir cmdlet parametreleri herhangi bir sayıda olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="f4bbe-135">Ancak, daha iyi bir kullanıcı deneyimi için parametre sayısını sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="f4bbe-136">Parametreler, genel statik olmayan alanlar veya özellikler üzerine bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="f4bbe-137">Parametre özellikleri bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="f4bbe-138">Özelliği, genel ayarlama erişimcisine sahip olmalıdır ve `ValueFromPipeline` veya `ValueFromPipelineByPropertyName` anahtar sözcüğü belirtilmediğinde, özelliği bir ortak get erişimcisine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="f4bbe-139">Konumsal parametreler belirttiğinizde, bir parametre kümesi en az beş konumsal parametreler sayısını sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="f4bbe-140">Ve konumsal parametreler bitişik olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="f4bbe-141">5, 100 ve 250 konumları aynı pozisyon 0, 1 ve 2 çalışır.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="f4bbe-142">Zaman `Position` anahtar sözcüğü belirtilmezse, cmdlet parametresi adlarıyla başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="f4bbe-143">Parametre kümeleri kullandığınızda, aşağıdakilere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="f4bbe-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="f4bbe-144">Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="f4bbe-145">İyi cmdlet'i tasarım benzersiz Bu parametre aynı zamanda mümkünse zorunlu olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="f4bbe-146">Cmdlet'inize parametresiz çalıştırılmak üzere tasarlanmışsa, benzersiz bir parametre zorunlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="f4bbe-147">Hiçbir parametre kümesi ile aynı konumda birden fazla konumsal parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="f4bbe-148">Parametre kümesi yalnızca bir parametresi bildirmelidir `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="f4bbe-149">Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="f4bbe-150">Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="f4bbe-151">Parametre adları yönergeleri hakkında daha fazla bilgi için bkz. [Cmdlet parametresi adları](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4bbe-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="f4bbe-152">Parametre özniteliği tarafından tanımlanan [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4bbe-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4bbe-153">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f4bbe-153">See Also</span></span>

[<span data-ttu-id="f4bbe-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="f4bbe-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="f4bbe-155">Cmdlet parametresi adları</span><span class="sxs-lookup"><span data-stu-id="f4bbe-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="f4bbe-156">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="f4bbe-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
