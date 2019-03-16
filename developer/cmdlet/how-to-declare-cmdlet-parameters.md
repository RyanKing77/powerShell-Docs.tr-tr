---
title: Cmdlet parametreleri bildirmek nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059176"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="0dcc4-102">Cmdlet Parametrelerini Bildirme</span><span class="sxs-lookup"><span data-stu-id="0dcc4-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="0dcc4-103">Bu örnekler bildirir adlandırılmış, konumsal, gerekli, isteğe bağlı ve parametreleri geçiş işlemini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="0dcc4-104">Bu örnekler, ayrıca bir parametre diğer adını tanımlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="0dcc4-105">Adlandırılmış parametre bildirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="0dcc4-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="0dcc4-106">Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0dcc4-107">Parametre özniteliği eklediğinizde atlamak `Position` özniteliğinden anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0dcc4-108">Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc4-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="0dcc4-109">Konumsal bir parametre bildirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="0dcc4-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="0dcc4-110">Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0dcc4-111">Parametre özniteliği eklediğinizde ayarlamak `Position` bağımsız değişken konumu için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="0dcc4-112">0 değeri ilk konumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0dcc4-113">Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc4-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="0dcc4-114">Nasıl zorunlu bir parametre bildirmek için</span><span class="sxs-lookup"><span data-stu-id="0dcc4-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="0dcc4-115">Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0dcc4-116">Parametre özniteliği eklediğinizde ayarlamak `Mandatory` anahtar `true`.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0dcc4-117">Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc4-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="0dcc4-118">İsteğe bağlı bir parametre bildirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="0dcc4-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="0dcc4-119">Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0dcc4-120">Parametre özniteliği eklediğinizde atlamak `Mandatory` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="0dcc4-121">Nasıl bir anahtar parametresi eklendi</span><span class="sxs-lookup"><span data-stu-id="0dcc4-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="0dcc4-122">Bir ortak özellik türü olarak tanımlamanız [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)ve ardından parametre özniteliği bildirin.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="0dcc4-123">Parametre özniteliği hakkında daha fazla bilgi için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc4-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="0dcc4-124">Nasıl diğer adlar bir parametreyle bildirin</span><span class="sxs-lookup"><span data-stu-id="0dcc4-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="0dcc4-125">Ortak özelliği, aşağıdaki kodda gösterildiği gibi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="0dcc4-126">Parametresi için diğer adlar listeleyen bir diğer ad özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="0dcc4-127">Bu örnekte, üç diğer adları aynı parametresi için tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="0dcc4-128">İlk diğer bir kısayol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="0dcc4-129">İkinci ve üçüncü diğer adları farklı senaryolar için kullanabileceğiniz adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dcc4-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="0dcc4-130">Diğer ad özniteliği hakkında daha fazla bilgi için bkz. [diğer ad özniteliği bildirimi](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0dcc4-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dcc4-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0dcc4-131">See Also</span></span>

[<span data-ttu-id="0dcc4-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="0dcc4-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="0dcc4-133">Parametre özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="0dcc4-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="0dcc4-134">Diğer ad özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="0dcc4-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="0dcc4-135">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="0dcc4-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
