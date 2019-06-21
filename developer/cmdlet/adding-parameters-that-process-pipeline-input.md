---
title: Ardışık Düzen giriş parametreleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 34643d20c16f8cc45e7fb20dc2a87d78b18bbf10
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298636"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Komut Zinciri Girişini İşleyen Parametreler Ekleme

Giriş bir cmdlet için bir kaynak, bir Yukarı Akış cmdlet'inden kaynaklanan işlem hattında bir nesnedir. Bu bölümde, Get-Proc cmdlet'e parametre eklemeyi açıklar (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)) cmdlet'i, işlem hattı nesneleri işleyebilmesi.

Bu Get-Proc cmdlet'i kullanan bir `Name` kabul eden bir işlem hattı nesnesinden giriş parametresi ve yerel bilgisayardan sağlanan adlarına göre işlem bilgilerini alır ve sonra komut satırında işlemleri hakkındaki bilgileri görüntüler.

## <a name="defining-the-cmdlet-class"></a>Cmdlet'i sınıf tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Bu cmdlet, burada seçilen fiil adı "Get", bu nedenle işlem bilgilerini alır. (Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Bu Get-Proc cmdlet tanımı aşağıda verilmiştir. Bu tanımın ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Ardışık düzendeki girişi tanımlama

Bu bölümde, bir cmdlet için ardışık düzendeki girişi tanımlamak açıklar. Bu Get-Proc cmdlet temsil eden bir özelliğini tanımlar `Name` açıklandığı parametresi [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md). (Parametre bildirme hakkında genel bilgi için bu konuya bakın.)

Ancak, bir cmdlet, işlem hattı girdiyi işlemek üzere gerektiğinde parametrelerinin değerleri girmek için Windows PowerShell çalışma zamanı tarafından bağlı olması gerekir. Bunu yapmak için eklemelisiniz `ValueFromPipeline` anahtar sözcüğü veya ekleme `ValueFromPipelineByProperty` anahtar [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelik bildirimi. Belirtin `ValueFromPipeline` tam giriş nesnesi cmdlet'i erişirse, anahtar sözcüğü. Belirtin `ValueFromPipelineByProperty` cmdlet'i yalnızca nesnenin bir özelliğini erişiyorsa.

Parametre bildirimi için işte `Name` parametresi Get-Proc cmdlet'in ardışık giriş kabul eder.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Önceki bildirim kümeleri `ValueFromPipeline` anahtar `true` böylece aynı türde parametre olarak nesne ise, Windows PowerShell çalışma zamanı gelen nesnesine parametre bağlama ya da aynı türüne dönüştürülebilen. `ValueFromPipelineByPropertyName` De anahtar sözcüğü ayarlanmasını `true` gelen nesne için Windows PowerShell çalışma zamanını kontrol eder, böylece bir `Name` özelliği. Gelen nesne, böyle bir özellik varsa, çalışma zamanı bağlayacaksınız `Name` parametresi `Name` gelen nesnesinin özelliği.

> [!NOTE]
> Ayarını `ValueFromPipeline` özniteliğinin anahtar sözcüğü bir parametre ayarı önceliklidir `ValueFromPipelineByPropertyName` anahtar sözcüğü.

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

İşlem hattı girdi işlemek üzere cmdlet'inize ise, yöntem işleme uygun giriş geçersiz kılmak gerekir. Temel giriş işleme yöntemleri de sunulan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

Bu Get-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) işlemek için gereken yöntemini `Name` kullanıcı veya bir betik tarafından sağlanan parametre girişi. Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı veya tüm işlemler için alırsınız. Dikkat edin [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), çağrı [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) çıkış nesnelerini göndermek için çıkış mekanizması işlem hattı. Bu çağrı, ikinci parametresinin `enumerateCollection`, ayarlanır `true` işlem nesneleri dizisi numaralandırabilir ve bir işlem aynı anda komut satırına yazma Windows PowerShell çalışma zamanı söylemek için.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [GetProcessSample03 örnek](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edin. Örneğin, örnek cmdlet kodu test edin. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Windows PowerShell komut isteminde, işlem hattı aracılığıyla işlem adları almak için aşağıdaki komutları girin.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Aşağıdaki çıktı görünür.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Sahip işlem nesneleri almak için aşağıdaki satırları girin bir `Name` "IEXPLORE" adlı işlemlerden özelliği. Bu örnekte `Get-Process` (Windows PowerShell tarafından sağlanan) cmdlet'i "IEXPLORE" işlemleri almak için Yukarı Akış komutu.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Aşağıdaki çıktı görünür.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md)

[İlk Cmdlet'inize oluşturma](./creating-a-cmdlet-without-parameters.md)

[Nesne türlerini genişletme ve biçimlendirme](/previous-versions//ms714665(v=vs.85))

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell başvurusu](../windows-powershell-reference.md)

[Cmdlet örnekleri](./cmdlet-samples.md)
