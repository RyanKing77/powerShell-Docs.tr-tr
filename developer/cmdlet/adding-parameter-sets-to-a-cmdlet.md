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
ms.openlocfilehash: 6a3b592c5f85c1f065ad4b5b0290cf44dcef484e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854888"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="df99e-102">Cmdlet’e Parametre Kümeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="df99e-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="df99e-103">Parametre kümeleri hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="df99e-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="df99e-104">Windows PowerShell, bir parametre kümesi parametrelerinin birlikte çalışan bir grup olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df99e-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="df99e-105">Bir cmdlet parametreleri gruplanarak, kullanıcı hangi grupta parametrelerinin belirtir üzerinde temel işlevselliğini değiştirebilirsiniz tek bir cmdlet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df99e-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="df99e-106">Farklı işlevleri tanımlamak için iki parametre kümeleri kullanan bir cmdlet örneğidir `Get-EventLog` Windows PowerShell tarafından sağlanan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="df99e-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="df99e-107">Bu cmdlet kullanıcının belirttiği farklı bilgiler döndürür `List` veya `LogName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="df99e-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="df99e-108">Varsa `LogName` parametresi belirtildiğinde, cmdlet, belirli bir olay günlüğüne olaylar hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="df99e-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="df99e-109">Varsa `List` parametresi belirtildiğinde, cmdlet kendilerini (içerdikleri olay bilgileri değil) dosyaları günlüğü hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="df99e-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="df99e-110">Bu durumda, `List` ve `LogName` iki ayrı parametre kümesi parametreleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="df99e-111">Parametre kümeleri hakkında unutmayın gereken iki önemli nokta, Windows PowerShell çalışma zamanı, yalnızca bir parametresi için belirli bir giriş kümesi kullanır ve her parametre kümesi en az bir parametresi olmalıdır, bu parametre kümesi için benzersiz olur.</span><span class="sxs-lookup"><span data-stu-id="df99e-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="df99e-112">Bu son nokta göstermek için üç parametre kümeleri bu Stop-Proc cmdlet'ini kullanır: `ProcessName`, `ProcessId`, ve `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="df99e-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="df99e-113">Bu parametre kümeleri, bir parametre kümeleri içinde olmayan bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="df99e-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="df99e-114">Diğer parametreler parametre kümeleri paylaşabilir, ancak cmdlet benzersiz parametreleri kullanan `ProcessName`, `ProcessId`, ve `InputObject` hangi Windows PowerShell çalışma zamanı kullanması gereken parametreleri kümesini tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="df99e-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="df99e-115">Cmdlet'i sınıf bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="df99e-116">İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme.</span><span class="sxs-lookup"><span data-stu-id="df99e-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="df99e-117">Cmdlet sistem işlemlerini durdurduğundan olduğundan bu cmdlet için yaşam döngüsü fiili "Durdur" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df99e-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="df99e-118">Cmdlet'i işlemlerini çalıştığından isim adı "Proc" kullanılır.</span><span class="sxs-lookup"><span data-stu-id="df99e-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="df99e-119">Cmdlet fiil ve isim adı cmdlet'i sınıfının adını yansıtılır bildiriminde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="df99e-120">Onaylanan cmdlet fiili adları hakkında daha fazla bilgi için bkz. [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="df99e-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="df99e-121">Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="df99e-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="df99e-122">Cmdlet parametrelerini bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="df99e-123">Bu cmdlet (Bu parametreler parametre kümeleri ayrıca tanımlayın) cmdlet'i, girdi olarak gereken üç parametreleri tanımlar yanı sıra bir `Force` cmdlet yaptığı yöneten parametre ve bir `PassThru` cmdlet gönderip göndermeyeceğini belirten bir parametre bir komut zincirinden nesne çıktı.</span><span class="sxs-lookup"><span data-stu-id="df99e-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="df99e-124">Varsayılan olarak, bu cmdlet bir nesneyi ardışık düzeni üzerinden geçmez.</span><span class="sxs-lookup"><span data-stu-id="df99e-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="df99e-125">Son iki Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="df99e-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="df99e-126">Name parametresi bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="df99e-127">Bu girdi parametresini durdurulması için işlemleri adını belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="df99e-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="df99e-128">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessName` parametresi için bu parametreyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

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

<span data-ttu-id="df99e-129">Ayrıca, "ProcessName" diğer ad bu parametreye belirtildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="df99e-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="df99e-130">ID parametresi bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="df99e-131">Bu girdi parametresini durdurulması işlemlerin tanımlayıcıları belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="df99e-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="df99e-132">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessId` parametre kümesi.</span><span class="sxs-lookup"><span data-stu-id="df99e-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="df99e-133">Ayrıca, "ProcessId" diğer ad bu parametreye belirtildiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="df99e-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="df99e-134">Inputobject parametre bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="df99e-135">Bu girdi parametresini durdurulması işlemleri hakkındaki bilgileri içeren giriş nesnesi belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="df99e-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="df99e-136">Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `InputObject` parametresi için bu parametreyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="df99e-137">Ayrıca, bu parametre diğer adı yok unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="df99e-138">Birden fazla parametre kümesine parametrelerinde bildirme</span><span class="sxs-lookup"><span data-stu-id="df99e-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="df99e-139">Her parametre kümesi için benzersiz bir parametresi olmalıdır ancak parametreler birden fazla parametre kümesine ait olabilir.</span><span class="sxs-lookup"><span data-stu-id="df99e-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="df99e-140">Bu durumlarda, paylaşılan parametre vermek bir [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) her olduğu parametre kümesi için öznitelik bildiriminin ait.</span><span class="sxs-lookup"><span data-stu-id="df99e-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="df99e-141">Bir parametre içinde tüm parametre kümeleri ise yalnızca parametre özniteliği bir kez bildirmeniz gerekir ve parametre kümesi adı belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="df99e-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="df99e-142">Bir giriş işleme yöntemi geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="df99e-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="df99e-143">Her cmdlet'i, girdi işleme yöntemi geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="df99e-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="df99e-144">Bu cmdlet, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet'i işlemlerini herhangi bir sayıda işleyebilmesi yöntemi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="df99e-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="df99e-145">Bu, farklı bir yöntem, kullanıcı üzerinde hangi parametre kümesi tabanlı aramalar belirttiği bir Select deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="df99e-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="df99e-146">Select deyimi tarafından çağrılan yardımcı yöntemler burada açıklanmamaktadır ancak kendi uygulamasında bir sonraki bölümde tam kod örneğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df99e-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="df99e-147">Kod örneği</span><span class="sxs-lookup"><span data-stu-id="df99e-147">Code Sample</span></span>

<span data-ttu-id="df99e-148">Tamamlanmış C# örnek kod için bkz: [StopProcessSample04 örnek](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="df99e-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="df99e-149">Nesne türlerini tanımlama ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="df99e-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="df99e-150">Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="df99e-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="df99e-151">Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="df99e-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="df99e-152">Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="df99e-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="df99e-153">Cmdlet oluşturma</span><span class="sxs-lookup"><span data-stu-id="df99e-153">Building the Cmdlet</span></span>

<span data-ttu-id="df99e-154">Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="df99e-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="df99e-155">Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="df99e-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="df99e-156">Sınama cmdlet'i</span><span class="sxs-lookup"><span data-stu-id="df99e-156">Testing the Cmdlet</span></span>

<span data-ttu-id="df99e-157">Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edin.</span><span class="sxs-lookup"><span data-stu-id="df99e-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="df99e-158">İşte gösteren bazı testler nasıl `ProcessId` ve `InputObject` parametreleri, parametre kümeleri bir işlemini durdurmak için test etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="df99e-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="df99e-159">Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `ProcessId` kendi tanımlayıcısına göre bir işlemini durdurmak için parametresini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="df99e-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="df99e-160">Bu durumda, cmdlet kullanıyor `ProcessId` parametresini ayarlayın işlemi durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="df99e-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="df99e-161">Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `InputObject` parametre kümesi işlemleri tarafından alınan not defteri nesnede durdurmak için `Get-Process` komutu.</span><span class="sxs-lookup"><span data-stu-id="df99e-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="df99e-162">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="df99e-162">See Also</span></span>

[<span data-ttu-id="df99e-163">Bir Cmdlet oluşturma sistemi değiştirir</span><span class="sxs-lookup"><span data-stu-id="df99e-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="df99e-164">Bir Windows PowerShell cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="df99e-164">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="df99e-165">Nesne türlerini genişletme ve biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="df99e-165">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="df99e-166">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="df99e-166">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="df99e-167">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="df99e-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
