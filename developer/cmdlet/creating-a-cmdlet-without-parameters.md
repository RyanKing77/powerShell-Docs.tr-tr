---
title: Parametresiz bir cmdlet'i oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 7f10acf59dedbb4af17bc5250e8624282ba22656
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854961"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Parametresiz Cmdlet Oluşturma

Bu bölümde, bir cmdlet'i parametreleri kullanımı ve yerel bilgisayardan bilgilerini alır ve ardından işlem hattının bilgi Yazar oluşturmayı açıklar. Burada açıklanan cmdlet'i yerel bilgisayar işlemleri hakkındaki bilgileri alır ve ardından bu bilgileri komut satırında görüntüleyen bir Get-Proc cmdlet'tir.

> [!NOTE]
> Cmdlet'leri yazarken Windows PowerShell® başvuru derlemeleri diske (varsayılan olarak C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0) yüklendiğini dikkat edin. Genel Derleme Önbelleği'ne (GAC) yüklü değil.

## <a name="naming-the-cmdlet"></a>Cmdlet adlandırma

Cmdlet adı cmdlet eylemde gösteren bir fiil ve cmdlet temel aldığı öğeleri gösteren bir isim oluşur. Bu örnek Get-Proc cmdlet işlem nesneleri getireceğinden "tarafından tanımlanan Al," fiili kullanan [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) numaralandırma ve isim cmdlet işlem öğeler üzerinde çalıştığını göstermek için "işlem".

Cmdlet'leri adlandırırken şu karakterlerin hiçbirini kullanmayın: #, () {} [] & - / \ $;: "' <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Bir isim seçme

Belirli bir isim seçmeniz gerekir. Ürün adının kısaltılmış bir sürümü ile önek tekil bir isim kullanmak en iyisidir. Bu tür bir örnek cmdlet adı "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Fiil seçme

Onaylanan cmdlet fiili adları kümesinden fiil kullanmanız gerekir. Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Cmdlet'i sınıf tanımlama

Cmdlet adı seçtikten sonra cmdlet uygulamak için bir .NET sınıfı tanımlayın. Bu örnek Get-Proc cmdlet'in sınıf tanımı aşağıda verilmiştir:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Sınıf tanımı önce dikkat [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) özniteliğiyle sözdizimi `[Cmdlet(verb, noun, ...)]`, bu sınıfı bir cmdlet olarak tanımlamak için kullanılır. Bu tüm cmdlet'ler için yalnızca gerekli öznitelik ve doğru bir şekilde çağırmak Windows PowerShell çalışma zamanı sağlar. Daha fazla gerekirse sınıf tanımlamak için öznitelik anahtar sözcükleri ayarlayabilirsiniz. Bizim örnek GetProcCommand sınıfı özniteliği bildirimi yalnızca Get-Proc cmdlet isim ve fiili adlarını bildirir dikkat edin.

> [!NOTE]
> Tüm Windows PowerShell öznitelik sınıfları için ayarlayabileceğiniz bir anahtar öznitelik sınıfının özelliklerine karşılık gelir.

Cmdlet'inin sınıfı adlandırırken sınıf adında cmdlet adı yansıtacak şekilde iyi bir uygulamadır. Bunu yapmak için "Eylem" ve "Ad" fiil ve isim kullanılan cmdlet adı ile değiştirin ve formu "VerbNounCommand" kullanın. Önceki sınıf tanımında gösterildiği örnek Get-Proc cmdlet türetilen GetProcCommand adlı bir sınıf tanımlar [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) temel sınıfı.

> [!IMPORTANT]
> Windows PowerShell çalışma zamanı doğrudan erişen bir cmdlet tanımlamak istiyorsanız, .NET sınıfınıza öğesinden türetilmelidir [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı. Bu sınıf hakkında daha fazla bilgi için bkz: [bir Cmdlet tanımlar, parametre kümeleri oluşturma](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Sınıf bir cmdlet için genel olarak açıkça işaretlenmelidir. Genel olarak işaretlenmemiş sınıflar için iç varsayılan ve Windows PowerShell çalışma zamanı tarafından bulunmaz.

Windows PowerShell kullanan [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) cmdlet'i sınıflarına için ad alanı. Bir API ad alanınız, örneğin, xxx.PS.Commands komutları ad alanında cmdlet'i sınıflarınızı yerleştirmek için önerilir.

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı en az biri cmdlet'inize geçersiz kılması gerekir, üç ana giriş işleme yöntemler sağlar. Windows PowerShell kayıtları nasıl işlediği hakkında daha fazla bilgi için bkz. [nasıl Windows PowerShell çalışır](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

Tüm giriş türleri için Windows PowerShell çalışma zamanı çağırır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) işlemeyi etkinleştirmek için. Bazı ön işleme veya Kurulum cmdlet'inize gerçekleştirmesi gerekiyorsa, bu yöntemi geçersiz kılarak, bunu yapabilirsiniz.

> [!NOTE]
> Windows PowerShell cmdlet çağrıldığında sağlanan parametre değerleri kümesi tanımlamak için "kayıt" terimini kullanır.

Ardışık giriş cmdlet'inize kabul ederse kılmalı [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi ve isteğe bağlı olarak [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)yöntemi. Örneğin, tüm giriş kullanarak toplar, bir cmdlet'i her iki yöntem de kılabilir [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ve ardından Giriş bir öğe yerine bir bütün olarak teker teker olarak çalışır `Sort-Object` cmdlet yapıyorsa.

Ardışık giriş cmdlet'inize almaz, geçersiz kılmalıdır [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi. Bu yöntem yerine sık kullanıldığını unutmayın [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) zaman cmdlet çalışamaz bir öğede bir kerede bir sıralama cmdlet için olduğu gibi.

Bu örnek Get-Proc cmdlet ardışık giriş alması gerektiğinden, onu geçersiz kılar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi ve varsayılan uygulamaları için kullandığı [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ve [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) geçersiz kılma işlemlerini alır ve komut satırını kullanarak Yazar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi.

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Giriş işleme hakkında bunları unutmayın

- Komut satırında kullanıcı tarafından sağlanan açık bir nesnenin (örneğin, bir dize) girişi için varsayılan kaynağıdır. Daha fazla bilgi için [bir cmdlet'e işlem komut satırı girişi oluşturma](./adding-parameters-that-process-command-line-input.md).

- İşleme yöntemi giriş giriş işlem hattında bir Yukarı Akış cmdlet'i çıkış nesnesinin de alabilir. Daha fazla bilgi için [işlem ardışık Giriş bir cmdlet'e oluşturma](./adding-parameters-that-process-pipeline-input.md). Unutmayın, cmdlet komut satırı bir bileşiminden girişi almak ve işlem hattı kaynakları.

- Aşağı Akış cmdlet'i, uzun süre veya hiç döndürmeyebilir. Bu nedenle, işleme yöntemi, cmdlet'inde giriş kilitleri çağrı sırasında tutmak zorunda değil [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), özellikle kilit kapsamı cmdlet'i örneği genişletir.

> [!IMPORTANT]
> Cmdlet hiçbir zaman çağırmalıdır [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) ya da eşdeğerine.

- Cmdlet'inize sona erdiğinde temizlemek için nesne değişkenleri olabilir. işleme (örneğin, bir dosya tanıtıcısı olarak açarsa [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi ve tanıtıcı tarafındankullanılmaküzereaçıktutar[ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Windows PowerShell çalışma zamanı her zaman arama olduğunu unutmamak önemlidir [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) nesne temizlemesi gerçekleştirmesi gereken yöntemini.

Örneğin, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet midway iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir, çağrılabilir değil. Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) deseni, çalışma zamanı, her ikisi de çağırabilirsiniz Sonlandırıcı dahil olmak üzere [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ve [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda.

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [GetProcessSample01 örnek](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Bizim örnek Get-Proc cmdlet'i için kod küçüktür, ancak yine de Windows PowerShell çalışma zamanı ve kullanışlı hale getirmek için yeterli olan mevcut bir .NET nesnesini kullanır. Şimdi, Get-Proc neler yapabileceğinizi ve nasıl çıktısını kullanılabilir daha iyi anlamak için test edin. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Windows PowerShell'i başlatın ve bilgisayar üzerinde çalışan geçerli işlemler alın.

    ```powershell
    get-proc
    ```

    Aşağıdaki çıktı görünür.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Cmdlet'i sonuçları daha kolay düzenlemesi için bir değişkene atayın.

    ```powershell
    $p=get-proc
    ```

3. İşlem sayısını alın.

    ```powershell
    $p.length
    ```

    Aşağıdaki çıktı görünür.

    ```output
    63
    ```

4. Belirli bir işlem alın.

    ```powershell
    $p[6]
    ```

    Aşağıdaki çıktı görünür.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Bu işlemin başlangıç zamanı alın.

    ```powershell
    $p[6].starttime
    ```

    Aşağıdaki çıktı görünür.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Tanıtıcı sayısı 500'den büyük olan işlemleri Al ve sonucu sıralayın.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Aşağıdaki çıktı görünür.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Kullanım `Get-Member` her işlem için kullanılabilen özellikleri listelemek için kullanın.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Aşağıdaki çıktı görünür.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Komut satırı girişi işlemek için bir Cmdlet oluşturma](./adding-parameters-that-process-command-line-input.md)

[İşlem hattı girdiyi işlemek üzere bir Cmdlet oluşturma](./adding-parameters-that-process-pipeline-input.md)

[Bir Windows PowerShell cmdlet'i oluşturma](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Nesne türlerini genişletme ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell nasıl çalışır?](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell başvurusu](../windows-powershell-reference.md)

[Cmdlet örnekleri](./cmdlet-samples.md)