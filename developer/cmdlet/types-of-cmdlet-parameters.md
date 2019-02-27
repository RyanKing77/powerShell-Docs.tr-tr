---
title: Cmdlet'i parametre türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849521"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="1c39f-102">Cmdlet Parametresi Türleri</span><span class="sxs-lookup"><span data-stu-id="1c39f-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="1c39f-103">Bu konuda, cmdlet'ler bildirebilirsiniz parametreleri farklı türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c39f-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="1c39f-104">Cmdlet parametreleri, konumsal, adlandırılmış, gerekli, isteğe bağlı veya parametreleri geçin.</span><span class="sxs-lookup"><span data-stu-id="1c39f-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="1c39f-105">Konumsal ve adlandırılmış parametreleri</span><span class="sxs-lookup"><span data-stu-id="1c39f-105">Positional and Named Parameters</span></span>

<span data-ttu-id="1c39f-106">Tüm cmdlet parametreleri, adlandırılmış ya da konumsal parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="1c39f-107">Adlandırılmış parametre cmdlet çağırırken parametre adı ve bağımsız değişken türü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="1c39f-108">Konumsal bir parametre, yalnızca göreli sıralarını bağımsız değişken türü gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="1c39f-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="1c39f-109">Sistem, sonra ilk konumsal parametresi ilk adsız bağımsız değişken eşler.</span><span class="sxs-lookup"><span data-stu-id="1c39f-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="1c39f-110">Sistem ikinci adsız bağımsız değişken ikinci eşler adlandırılmamış parametreyi ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="1c39f-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="1c39f-111">Varsayılan olarak, tüm cmdlet parametreleri parametreleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1c39f-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="1c39f-112">Adlandırılmış parametre tanımlamak için atla `Position` anahtar sözcüğünü **parametre** aşağıdaki parametreyi bildirimde gösterildiği gibi öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1c39f-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="1c39f-113">Konumsal bir parametre tanımlamak için ekleme `Position` anahtar sözcüğü parametresinde özniteliği bildirimi ve ardından bir konum belirtin.</span><span class="sxs-lookup"><span data-stu-id="1c39f-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="1c39f-114">Aşağıdaki örnekte, `UserName` parametresi, konumu 0 ile konumsal bir parametre olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="1c39f-115">Bu, ilk bağımsız değişken çağrısı Bu parametre için otomatik olarak bağlanacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="1c39f-116">Kullanıcı, cmdlet çalıştırıldığında, parametre adını girin gerekmez. böylece en çok kullanılan parametreleri konumsal parametreler olarak bildirilmesi iyi cmdlet'i tasarım önerir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="1c39f-117">Konumsal ve adlandırılmış parametreleri tek bağımsız değişkenler veya virgülle ayırarak birden çok bağımsız değişkeni kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1c39f-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="1c39f-118">Yalnızca bir dizi gibi dizeleri koleksiyonu parametreyi kabul eden birden çok bağımsız değişkeni izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1c39f-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="1c39f-119">Konumsal ve adlandırılmış parametreleri aynı cmdlet'inde karışımı.</span><span class="sxs-lookup"><span data-stu-id="1c39f-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="1c39f-120">Bu durumda, sistem adlandırılmış bağımsız değişkenler ilk alır ve ardından kalan eşlemek için deneme konumsal parametreler için bağımsız değişkenler adlandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="1c39f-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="1c39f-121">Aşağıdaki komutlar, belirtebileceğiniz tek ve birden çok bağımsız değişken parametreleri için farklı yolları göstermektedir `Get-Command` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="1c39f-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="1c39f-122">Son iki örnek olduğuna dikkat edin **-adı** çünkü belirtilmesi gerekmez `Name` parametresi, konumsal bir parametre olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1c39f-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="1c39f-123">Zorunlu ve isteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="1c39f-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="1c39f-124">Ayrıca, cmdlet parametreleri zorunlu veya isteğe bağlı parametreler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c39f-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="1c39f-125">(Çalışma zamanı Windows PowerShell cmdlet'ini çağırmadan önce zorunlu bir parametre belirtilmelidir.)  Varsayılan olarak, Parametreler, isteğe bağlı olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1c39f-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="1c39f-126">Zorunlu bir parametre tanımlamak için ekleme `Mandatory` parametresinde anahtar sözcüğü özniteliği bildirimi ve ayarlamak `true`aşağıdaki parametreyi bildirimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1c39f-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="1c39f-127">İsteğe bağlı bir parametre tanımlamak için atla `Mandatory` anahtar sözcüğünü **parametre** aşağıdaki parametreyi bildirimde gösterildiği gibi öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1c39f-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="1c39f-128">Anahtar parametreleri</span><span class="sxs-lookup"><span data-stu-id="1c39f-128">Switch Parameters</span></span>

<span data-ttu-id="1c39f-129">Windows PowerShell sağlayan bir [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) değerini bir parametre tanımlamanıza olanak tanıyan türü otomatik olarak ayarlandığından `false` cmdlet parametresi belirtilmezse çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1c39f-129">Windows PowerShell provides a [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="1c39f-130">Mümkün olduğunda yerine Boole parametreleri anahtar parametreleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c39f-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="1c39f-131">Aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1c39f-131">Consider the following sample.</span></span> <span data-ttu-id="1c39f-132">Varsayılan olarak, birçok Windows PowerShell cmdlet'leri bir çıkış nesnesi işlem hattı aşağı geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="1c39f-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="1c39f-133">Ancak, bu cmdlet'ler sahip bir `PassThru` varsayılan davranışı geçersiz kılan parametre geçin.</span><span class="sxs-lookup"><span data-stu-id="1c39f-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="1c39f-134">Varsa `PassThru` bu cmdlet'ler çağrıldığında parametre belirtilirse, cmdlet ardışık düzene bir çıkış nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c39f-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="1c39f-135">Parametre bir varsayılan değerine sahip olacak şekilde ihtiyacınız varsa `true` arama parametresi belirtilmediğinde, parametre algılama ters göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1c39f-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="1c39f-136">Parametre özniteliği için bir Boole değeri ayarlamak yerine örnek, `true`, özellik olarak bildirin [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) yazın ve ardından parametreninvarsayılandeğeriniayarlayın`false`.</span><span class="sxs-lookup"><span data-stu-id="1c39f-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="1c39f-137">Bir anahtar parametresi tanımlamak için özellik olarak bildirin [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) , aşağıdaki örnekte gösterildiği gibi yazın.</span><span class="sxs-lookup"><span data-stu-id="1c39f-137">To define a switch parameter, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="1c39f-138">Cmdlet parametresi belirtildiğinde, bu işlem yapmak için aşağıdaki yöntemleri işleme giriş birini yapısında kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c39f-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="1c39f-139">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1c39f-139">See Also</span></span>

[<span data-ttu-id="1c39f-140">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="1c39f-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
