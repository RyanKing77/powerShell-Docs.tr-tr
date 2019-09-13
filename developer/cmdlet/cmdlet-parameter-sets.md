---
title: Cmdlet parametre kümeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936195"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="a664e-102">Cmdlet parametre kümeleri</span><span class="sxs-lookup"><span data-stu-id="a664e-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="a664e-103">PowerShell, farklı senaryolar için farklı eylemler gerçekleştirebileceği tek bir cmdlet yazmanızı sağlamak üzere parametre kümelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a664e-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="a664e-104">Parametre kümeleri, kullanıcıya farklı parametreler sergileme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a664e-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="a664e-105">Ve, Kullanıcı tarafından belirtilen parametrelere göre farklı bilgiler döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="a664e-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="a664e-106">Parametre kümelerine örnekler</span><span class="sxs-lookup"><span data-stu-id="a664e-106">Examples of parameter sets</span></span>

<span data-ttu-id="a664e-107">Örneğin, PowerShell `Get-EventLog` cmdlet 'i, kullanıcının **list** veya **logName** parametresini belirttiğinden bağımsız olarak farklı bilgiler döndürür.</span><span class="sxs-lookup"><span data-stu-id="a664e-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="a664e-108">**List** parametresi belirtilirse, cmdlet, günlük dosyaları hakkında bilgileri döndürür ancak içerdikleri olay bilgilerini içermez.</span><span class="sxs-lookup"><span data-stu-id="a664e-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="a664e-109">**LogName** parametresi belirtilmişse, cmdlet belirli bir olay günlüğündeki olaylar hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a664e-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="a664e-110">**List** ve **logName** parametreleri iki ayrı parametre kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a664e-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="a664e-111">Unique parametresi</span><span class="sxs-lookup"><span data-stu-id="a664e-111">Unique parameter</span></span>

<span data-ttu-id="a664e-112">Her parametre kümesi, PowerShell çalışma zamanının uygun parametre kümesini açığa çıkarmak için kullandığı benzersiz bir parametreye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a664e-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="a664e-113">Mümkünse, Unique parametresi zorunlu bir parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a664e-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="a664e-114">Bir parametre zorunlu olduğunda, kullanıcının parametresini belirtmesi gerekir ve PowerShell çalışma zamanı, parametre kümesini tanımlamak için bu parametreyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a664e-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="a664e-115">Cmdlet 'leriniz herhangi bir parametre belirtilmeden çalışacak şekilde tasarlandıysa, Unique parametresi zorunlu olamaz.</span><span class="sxs-lookup"><span data-stu-id="a664e-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="a664e-116">Birden çok parametre kümesi</span><span class="sxs-lookup"><span data-stu-id="a664e-116">Multiple parameter sets</span></span>

<span data-ttu-id="a664e-117">Aşağıdaki çizimde, sol sütunda üç geçerli parametre kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a664e-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="a664e-118">**A parametresi** ilk parametre kümesi için benzersizdir, **B parametresi** ikinci parametre kümesi için benzersizdir ve **C parametresi** üçüncü parametre kümesine özeldir.</span><span class="sxs-lookup"><span data-stu-id="a664e-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="a664e-119">Sağ sütunda, parametre kümelerinin benzersiz bir parametresi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a664e-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="a664e-121">Parametre kümesi gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="a664e-121">Parameter set requirements</span></span>

<span data-ttu-id="a664e-122">Aşağıdaki gereksinimler tüm parametre kümeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a664e-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="a664e-123">Her parametre kümesi en az bir benzersiz parametreye sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a664e-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="a664e-124">Mümkünse, bu parametreyi zorunlu bir parametre yapın.</span><span class="sxs-lookup"><span data-stu-id="a664e-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="a664e-125">Birden çok Konumsal parametre içeren bir parametre kümesi, her bir parametre için benzersiz konumlar tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a664e-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="a664e-126">İki Konumsal parametre aynı konumu belirtemez.</span><span class="sxs-lookup"><span data-stu-id="a664e-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="a664e-127">Bir küme içinde yalnızca bir parametre bir `ValueFromPipeline` `true`değeri olan anahtar sözcüğü bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="a664e-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="a664e-128">Birden çok parametre, `ValueFromPipelineByPropertyName` bir `true`değeri olan anahtar sözcüğü tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a664e-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="a664e-129">Parametre için bir parametre kümesi belirtilmemişse parametre tüm parametre kümelerine aittir.</span><span class="sxs-lookup"><span data-stu-id="a664e-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="a664e-130">Bir cmdlet veya işlev için, 32 parametre kümesi sınırı vardır.</span><span class="sxs-lookup"><span data-stu-id="a664e-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="a664e-131">Varsayılan parametre kümeleri</span><span class="sxs-lookup"><span data-stu-id="a664e-131">Default parameter sets</span></span>

<span data-ttu-id="a664e-132">Birden çok parametre kümesi tanımlandığında, varsayılan parametre kümesini belirtmek için `DefaultParameterSetName` **cmdlet** özniteliğinin anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a664e-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="a664e-133">PowerShell, komut tarafından belirtilen bilgilere göre kullanılacak parametre kümesini belirleyeleyemiyorsa varsayılan parametre kümesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a664e-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="a664e-134">**Cmdlet** özniteliği hakkında daha fazla bilgi için bkz. [cmdlet öznitelik bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a664e-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="a664e-135">Parametre kümelerini bildirme</span><span class="sxs-lookup"><span data-stu-id="a664e-135">Declaring parameter sets</span></span>

<span data-ttu-id="a664e-136">Bir parametre kümesi oluşturmak için, parametre kümesindeki her parametre `ParameterSetName` için **parametre** özniteliğini bildirdiğinizde anahtar sözcüğünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a664e-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="a664e-137">Birden çok parametre kümesine ait parametreler için, her parametre kümesi için bir **parametre** özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a664e-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="a664e-138">Bu öznitelik, parametreyi her bir parametre kümesi için farklı tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a664e-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="a664e-139">Örneğin, bir parametreyi bir küme içinde zorunlu olarak tanımlayabilir ve başka bir şekilde isteğe bağlı olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a664e-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="a664e-140">Ancak, her bir parametre kümesi bir benzersiz parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="a664e-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="a664e-141">Daha fazla bilgi için bkz. [parametre öznitelik bildirimi](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a664e-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="a664e-142">Aşağıdaki örnekte **Kullanıcı adı** parametresi, `Test01` parametre kümesinin benzersiz parametresidir ve **ComputerName** parametresi `Test02` parametre kümesinin benzersiz parametresidir.</span><span class="sxs-lookup"><span data-stu-id="a664e-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="a664e-143">**Sharedparam** parametresi her iki kümeye aittir ve `Test01` parametre kümesi için zorunludur, `Test02` ancak parametre kümesi için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a664e-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

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
private string sharedParam;
```
