---
title: Cmdlet parametresi ayarlar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847701"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="0d033-102">Cmdlet Parametre Kümeleri</span><span class="sxs-lookup"><span data-stu-id="0d033-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="0d033-103">Windows PowerShell, parametre kümeleri sağlamak için farklı senaryolar farklı eylemler gerçekleştiren tek bir cmdlet yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d033-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="0d033-104">Parametre kümeleri farklı parametreler kullanıcıya kullanıma sunmak ve kullanıcı tarafından belirtilen parametrelere bağlı olarak farklı bilgiler döndürmek için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0d033-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="0d033-105">Parametre kümeleri örnekleri</span><span class="sxs-lookup"><span data-stu-id="0d033-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="0d033-106">Örneğin, `Get-EventLog` cmdlet (Windows PowerShell tarafından sağlanan) olup olmadığını kullanıcının belirttiği bağlı olarak farklı bilgi döndürür `List` veya `LogName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0d033-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="0d033-107">Varsa `List` parametresi belirtildiğinde, cmdlet kendilerini ancak içerdikleri olay bilgileri değil yalnızca günlük dosyaları hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d033-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="0d033-108">Varsa `LogName` parametresi belirtildiğinde, cmdlet, belirli bir olay günlüğüne olaylar hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d033-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="0d033-109">`List` Ve `LogName` iki ayrı parametre kümesi parametreleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0d033-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="0d033-110">Benzersiz bir parametre</span><span class="sxs-lookup"><span data-stu-id="0d033-110">Unique Parameter</span></span>

<span data-ttu-id="0d033-111">Her parametre kümesi, Windows PowerShell çalışma zamanı uygun parametre kümesi kullanıma sunmak için kullanabileceğiniz benzersiz bir parametreye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d033-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="0d033-112">Mümkünse, benzersiz bir parametre zorunlu bir parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d033-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="0d033-113">Bir parametre zorunlu olduğunda, kullanıcı bir parametreyi belirtmek için zorlanır ve Windows PowerShell çalışma zamanı bu parametreyi kullanacak şekilde parametreyi tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d033-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="0d033-114">Benzersiz parametre cmdlet'inize herhangi bir parametre belirtmeden çalıştırılmak üzere tasarlanmışsa zorunlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="0d033-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="0d033-115">Birden çok parametre kümeleri</span><span class="sxs-lookup"><span data-stu-id="0d033-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="0d033-116">Aşağıdaki çizimde, sol sütunda üç geçerli parametre kümeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d033-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="0d033-117">Bir parametre ilk parametre kümesi için benzersiz olan, parametresi B ikinci parametre kümesi için benzersiz ve üçüncü parametre kümesi için parametre C benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="0d033-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="0d033-118">Ancak, sağ sütunda, parametre kümeleri benzersiz bir parametre yok.</span><span class="sxs-lookup"><span data-stu-id="0d033-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="0d033-120">Parametre kümesi gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="0d033-120">Parameter Set Requirements</span></span>

<span data-ttu-id="0d033-121">Tüm parametre kümeleri için aşağıdaki gereksinimler karşılanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d033-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="0d033-122">Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d033-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="0d033-123">Mümkünse, bu parametre zorunlu bir parametre olun.</span><span class="sxs-lookup"><span data-stu-id="0d033-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="0d033-124">Birden çok konumsal parametreler içeren bir parametre kümesi her parametre için benzersiz konumları tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d033-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="0d033-125">Hiçbir iki konumsal parametreler aynı konumu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d033-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="0d033-126">Bir kümedeki tek bir parametre bildirebilirsiniz `ValueFromPipeline` anahtar sözcüğü değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="0d033-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="0d033-127">Birden çok parametre tanımlayabilirsiniz `ValueFromPipelineByPropertyName` anahtar sözcüğü değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="0d033-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="0d033-128">Hiçbir parametre kümesi için bir parametre belirtilirse, parametre için tüm parametre kümeleri aittir.</span><span class="sxs-lookup"><span data-stu-id="0d033-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="0d033-129">Varsayılan parametre kümeleri</span><span class="sxs-lookup"><span data-stu-id="0d033-129">Default Parameter Sets</span></span>

<span data-ttu-id="0d033-130">Birden fazla parametre kümesine tanımlandığında, kullanabileceğiniz `DefaultParameterSetName` varsayılan parametre kümesi belirtmek için Cmdlet özniteliğinin anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0d033-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="0d033-131">Windows PowerShell kullanmak üzere parametre komutu tarafından sağlanan bilgilere dayanarak belirleyemiyorsa ayarlayın varsayılan parametresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d033-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="0d033-132">Cmdlet özniteliği hakkında daha fazla bilgi için bkz. [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0d033-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="0d033-133">Parametre kümeleri bildirme</span><span class="sxs-lookup"><span data-stu-id="0d033-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="0d033-134">Parametre kümesi oluşturmak için belirtmelisiniz `ParameterSetName` Parameter özniteliği parametre kümesindeki her parametre için bildirdiğinizde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0d033-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="0d033-135">Birden fazla parametre kümesine ait parametreler için her parametre kümesi için bir parametre özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0d033-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="0d033-136">Bu parametre her parametre kümesi için farklı bir şekilde tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d033-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="0d033-137">Örneğin, bir parametre zorunlu bir kümede bulunan ve başka bir isteğe bağlı olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d033-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="0d033-138">Ancak, her parametre kümesi benzersiz bir parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0d033-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="0d033-139">Aşağıdaki örnekte, `UserName` parametredir benzersiz Test01 parametre kümesi ve `ComputerName` parametredir benzersiz Test02 parametre kümesi.</span><span class="sxs-lookup"><span data-stu-id="0d033-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="0d033-140">`SharedParam` Parametresi hem kümelerine ait olan ve Test02 parametre kümesi için isteğe bağlı ancak ayarlamak Test01 parametresi zorunludur.</span><span class="sxs-lookup"><span data-stu-id="0d033-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```