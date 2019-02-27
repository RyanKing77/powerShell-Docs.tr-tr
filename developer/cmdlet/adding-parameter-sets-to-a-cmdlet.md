---
title: Ayarlar bir cmdlet'e parametre ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849101"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="72b01-102">Cmdlet’e Parametre Kümeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="72b01-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="72b01-103">Bu bölümde, Stop-Proc cmdlet'e parametre ayarlar eklemeyi açıklar (açıklanan [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="72b01-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="72b01-104">Benzer şekilde bu Programcı Kılavuzu'nda açıklanan diğer Stop-Proc cmdlet'leri, bu cmdlet Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="72b01-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="72b01-105">Bu bölümdeki konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="72b01-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="72b01-106">Parametre kümeleri hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="72b01-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="72b01-107">Cmdlet'i sınıf bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="72b01-108">Cmdlet parametrelerini bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="72b01-109">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="72b01-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="72b01-110">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="72b01-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="72b01-111">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="72b01-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="72b01-112">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="72b01-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="72b01-113">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="72b01-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="72b01-114">Parametre kümeleri hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="72b01-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="72b01-115">Windows PowerShell, bir parametre kümesi parametrelerinin birlikte çalışan bir grup olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72b01-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="72b01-116">Bir cmdlet parametreleri gruplanarak, kullanıcı hangi grupta parametrelerinin belirtir üzerinde temel işlevselliğini değiştirebilirsiniz tek bir cmdlet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72b01-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="72b01-117">Farklı işlevleri tanımlamak için iki parametre kümeleri kullanan bir cmdlet örneğidir `Get-EventLog` Windows PowerShell tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="72b01-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="72b01-118">Bu cmdlet kullanıcının belirttiği farklı bilgiler döndürür `List` veya `LogName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="72b01-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="72b01-119">Varsa `LogName` parametresi belirtildiğinde, cmdlet, belirli bir olay günlüğüne olaylar hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="72b01-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="72b01-120">Varsa `List` parametresi belirtildiğinde, cmdlet kendilerini (içerdikleri olay bilgileri değil) dosyaları günlüğü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="72b01-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="72b01-121">Bu durumda, `List` ve `LogName` iki ayrı parametre kümesi parametreleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="72b01-122">Parametre kümeleri hakkında unutmayın gereken iki önemli nokta, Windows PowerShell çalışma zamanı, yalnızca bir parametresi için belirli bir giriş kümesi kullanır ve her parametre kümesi en az bir parametresi olmalıdır, bu parametre kümesi için benzersiz olur.</span><span class="sxs-lookup"><span data-stu-id="72b01-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="72b01-123">Bu son nokta göstermek için üç parametre kümeleri bu Stop-Proc cmdlet'ini kullanır: `ProcessName`, `ProcessId`, ve `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="72b01-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="72b01-124">Bu parametre kümeleri, bir parametre kümeleri içinde olmayan bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="72b01-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="72b01-125">Diğer parametreler parametre kümeleri paylaşabilir, ancak cmdlet benzersiz parametreleri kullanan `ProcessName`, `ProcessId`, ve `InputObject` hangi Windows PowerShell çalışma zamanı kullanması gereken parametreleri kümesini tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="72b01-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="72b01-126">Cmdlet'i sınıf bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="72b01-127">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="72b01-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="72b01-128">Cmdlet sistem işlemlerini durdurduğundan olduğundan bu cmdlet için yaşam döngüsü fiili "Durdur" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72b01-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="72b01-129">Cmdlet'i işlemlerini çalıştığından isim adı "Proc" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72b01-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="72b01-130">Cmdlet fiil ve isim adı cmdlet'i sınıfının adını yansıtılır bildiriminde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="72b01-131">Onaylanan cmdlet fiili adları hakkında daha fazla bilgi için bkz. [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="72b01-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="72b01-132">Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="72b01-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="72b01-133">Cmdlet parametrelerini bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="72b01-134">Bu cmdlet (Bu parametreler parametre kümeleri ayrıca tanımlayın) cmdlet'i, girdi olarak gereken üç parametreleri tanımlar yanı sıra bir `Force` cmdlet yaptığı yöneten parametre ve bir `PassThru` cmdlet gönderip göndermeyeceğini belirten bir parametre bir komut zincirinden nesne çıktı.</span><span class="sxs-lookup"><span data-stu-id="72b01-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="72b01-135">Varsayılan olarak, bu cmdlet bir nesneyi ardışık düzeni üzerinden geçmez.</span><span class="sxs-lookup"><span data-stu-id="72b01-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="72b01-136">Son iki Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="72b01-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="72b01-137">Name parametresi bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="72b01-138">Bu girdi parametresini durdurulması için işlemleri adını belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b01-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="72b01-139">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessName` parametresi için bu parametreyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="72b01-140">Ayrıca, "ProcessName" diğer ad bu parametreye belirtildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="72b01-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="72b01-141">ID parametresi bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="72b01-142">Bu girdi parametresini durdurulması işlemlerin tanımlayıcıları belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b01-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="72b01-143">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessId` parametre kümesi.</span><span class="sxs-lookup"><span data-stu-id="72b01-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="72b01-144">Ayrıca, "ProcessId" diğer ad bu parametreye belirtildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="72b01-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="72b01-145">Inputobject parametre bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="72b01-146">Bu girdi parametresini durdurulması işlemleri hakkındaki bilgileri içeren giriş nesnesi belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b01-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="72b01-147">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `InputObject` parametresi için bu parametreyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="72b01-148">Ayrıca, bu parametre diğer adı yok unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="72b01-149">Birden fazla parametre kümesine parametrelerinde bildirme</span><span class="sxs-lookup"><span data-stu-id="72b01-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="72b01-150">Her parametre kümesi için benzersiz bir parametresi olmalıdır ancak parametreler birden fazla parametre kümesine ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="72b01-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="72b01-151">Bu durumlarda, paylaşılan parametre vermek bir [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) her olduğu parametre kümesi için öznitelik bildiriminin ait.</span><span class="sxs-lookup"><span data-stu-id="72b01-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="72b01-152">Bir parametre içinde tüm parametre kümeleri ise yalnızca parametre özniteliği bir kez bildirmeniz gerekir ve parametre kümesi adı belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="72b01-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="72b01-153">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="72b01-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="72b01-154">Her cmdlet'i, girdi işleme yöntemi geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72b01-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="72b01-155">Bu cmdlet, [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet'i işlemlerini herhangi bir sayıda işleyebilmesi yöntemi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="72b01-155">In this cmdlet, the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="72b01-156">Bu, farklı bir yöntem, kullanıcı üzerinde hangi parametre kümesi tabanlı aramalar belirttiği bir Select deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="72b01-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="72b01-157">Select deyimi tarafından çağrılan yardımcı yöntemler burada açıklanmamaktadır ancak kendi uygulamasında bir sonraki bölümde tam kod örneğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72b01-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="72b01-158">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="72b01-158">Code Sample</span></span>

<span data-ttu-id="72b01-159">Tamamlanmış C# örnek kod için bkz: [StopProcessSample04 örnek](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="72b01-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="72b01-160">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="72b01-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="72b01-161">Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="72b01-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="72b01-162">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="72b01-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="72b01-163">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="72b01-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="72b01-164">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="72b01-164">Building the Cmdlet</span></span>

<span data-ttu-id="72b01-165">Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="72b01-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="72b01-166">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="72b01-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="72b01-167">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="72b01-167">Testing the Cmdlet</span></span>

<span data-ttu-id="72b01-168">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edin.</span><span class="sxs-lookup"><span data-stu-id="72b01-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="72b01-169">İşte gösteren bazı testler nasıl `ProcessId` ve `InputObject` parametreleri, parametre kümeleri bir işlemini durdurmak için test etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72b01-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="72b01-170">Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `ProcessId` kendi tanımlayıcısına göre bir işlemini durdurmak için parametresini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="72b01-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="72b01-171">Bu durumda, cmdlet kullanıyor `ProcessId` parametresini ayarlayın işlemi durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="72b01-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="72b01-172">Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `InputObject` parametre kümesi işlemleri tarafından alınan not defteri nesnede durdurmak için `Get-Process` komutu.</span><span class="sxs-lookup"><span data-stu-id="72b01-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="72b01-173">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="72b01-173">See Also</span></span>

[<span data-ttu-id="72b01-174">Bir Cmdlet oluşturma sistemi değiştirir</span><span class="sxs-lookup"><span data-stu-id="72b01-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="72b01-175">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="72b01-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="72b01-176">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="72b01-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="72b01-177">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="72b01-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="72b01-178">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="72b01-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
