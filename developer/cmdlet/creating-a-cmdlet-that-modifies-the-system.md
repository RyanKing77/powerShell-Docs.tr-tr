---
title: Bir Cmdlet oluşturma sistemi değiştirir | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055147"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Sistemi Değiştiren bir Cmdlet Oluşturma

Bazı durumlarda bir cmdlet, yalnızca Windows PowerShell çalışma zamanı durumunu sistemin çalışma durumu değiştirmeniz gerekir. Bu gibi durumlarda cmdlet değişikliği yapmanız gerekip gerekmediğini doğrulamak bir fırsat kullanıcı izin vermelidir.

Onay desteklemek için bir cmdlet'in iki işlem yapmalısınız.

- Belirttiğinizde cmdlet onay desteklediğini bildirmek [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) SupportsShouldProcess anahtar sözcüğü ayarlayarak özniteliği `true`.

- Çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (aşağıdaki örnekte gösterildiği gibi) cmdlet'inin yürütülmesi sırasında.

Onay destekleyerek, bir cmdlet kullanıma sunan `Confirm` ve `WhatIf` Windows PowerShell tarafından sağlanan ve ayrıca geliştirme yönergelere cmdlet'leri için uygun parametreleri ( cmdlet'igeliştirmekılavuzlarıhakkındadahafazlabilgiiçinbkz.[ Cmdlet geliştirme yönergeleri](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Sistem değiştirme

"Sistem değiştirme" işlemi, potansiyel olarak Windows PowerShell dışında sistem durumunu değiştiren herhangi bir cmdlet'i ifade eder. Örneğin, bir veritabanı tablosunda bir satıra onaylanması sistemde yapılan tüm değişiklikleri Koleksiyonlar'a etkinleştirme veya bir kullanıcı hesabı devre dışı bırakma işlemi durduruluyor. Buna karşılık, veri okuma veya geçici bağlantı işlemleri sistem değiştirmeyin ve genellikle onay gerektirmez. Onay ayrıca gerekli değildir, etkili sınırlıdır ve Windows PowerShell çalışma zamanı içinde olduğu gibi eylemler için `set-variable`. Kalıcı bir değişiklik yapmamanız veya cmdlet'leri bildirmelidir `SupportsShouldProcess` ve çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yalnızca kalıcı bir değişiklik yapmak üzere olmaları durumunda.

> [!NOTE]
> ShouldProcess onay yalnızca cmdlet'ler için geçerli olur. Bir komut veya betik .NET yöntemleri veya özellikleri doğrudan çağırma veya Windows PowerShell dışında çağıran uygulamalardan bir sistemin çalışır duruma değiştirir, bu formu onayının kullanılabilir olmaz.

## <a name="the-stopproc-cmdlet"></a>StopProc cmdlet'i

Bu konu Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır bir Stop-Proc cmdlet açıklar (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Bu bölümdeki konular şunlardır:

- [Cmdlet tanımlama](#Defining-the-Cmdlet)

- [Sistem değiştirilmesi için parametreleri tanımlama](#Defining-Parameters-for-System-Modification)

- [Bir giriş işleme yöntemi geçersiz kılma](#Overriding-an-Input-Processing-Method)

- [ShouldProcess yöntemi çağırma](#Calling-the-ShouldProcess-Method)

- [ShouldContinue yöntemi çağırma](#Calling-the-ShouldContinue-Method)

- [Durdurma giriş işleme](#Stopping-Input-Processing)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Defining-Object-Types-and-Formatting)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Cmdlet tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Sistem değiştirmek için bir cmdlet yazıyorsanız olduğundan, buna uygun olarak adlandırılmalıdır. "Durdur" seçeneğini fiili adı, bu nedenle bu cmdlet'i durakları sistem işlemleri, tanımlanan [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) sınıfıyla isim cmdlet'i işlemlerini durdurduğundan belirtmek için "işlem". Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Bu Stop-Proc cmdlet için sınıf tanımının verilmiştir.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Unutmayın, [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) bildirimi `SupportsShouldProcess` özniteliği anahtar sözcüğü ayarlandığında `true` çağrı yapmak cmdlet etkinleştirmek için [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Bu anahtar sözcük kümesi olmadan `Confirm` ve `WhatIf` parametreleri kullanılabilir olmayacak.

### <a name="extremely-destructive-actions"></a>Son derece bozucu Eylemler

Bazı işlemler, bir etkin sabit disk bölümü yeniden biçimlendirme gibi son derece yıkıcı. Bu gibi durumlarda cmdlet ayarlamalısınız `ConfirmImpact`  =  `ConfirmImpact.High` bildirirken [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) özniteliği. Bu ayar bile kullanıcı belirtilmemişse cmdlet isteği kullanıcı onayı zorlar. `Confirm` parametresi. Aşırı kullanımı cmdlet'i geliştiriciler ancak kaçınmalısınız `ConfirmImpact` bir kullanıcı hesabı silme gibi yalnızca potansiyel olarak zararlı işlemler için. Unutmayın `ConfirmImpact` ayarlanır [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Benzer şekilde, bazı işlemler teorik olarak çalışan Windows PowerShell dışında bir sistem durumunu değiştirebilir ancak yıkıcı, olması olası değildir. Bu cmdlet'leri ayarlayabilirsiniz `ConfirmImpact` için [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Bu kullanıcının yalnızca orta etkisi ve yüksek etkili işlemlerini doğrulamak için burada istedi onay istekleri atlayacaktır.

## <a name="defining-parameters-for-system-modification"></a>Sistem değiştirilmesi için parametreleri tanımlama

Bu bölümde, destek sistem değiştirilmesi için gerekli olanlar da dahil, bir cmdlet parametreleri tanımlayın açıklar. Bkz: [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md) parametreleri tanımlama hakkında genel bilgi gerekiyorsa.

Stop-Proc cmdlet, üç parametre tanımlar: `Name`, `Force`, ve `PassThru`.

`Name` Karşılık gelen parametre `Name` özelliği işlem giriş nesnesi. Unutmayın, `Name` durdurmak için adlandırılmış bir işlem yoksa cmdlet başarısız olacağından bu parametre zorunludur.

`Force` Parametresi çağrısına geçersiz kılmasına izin verir [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Aslında, herhangi bir cmdlet'i çağırır [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) olmalıdır bir `Force` parametre için zaman `Force` belirtilirse, cmdlet çağrısı atlar [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ve işleme devam eder. Bu çağrılar etkilemez unutmayın [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

`PassThru` Parametresi bir işlemi durdurulduktan sonra cmdlet'i bir çıkış nesnesi aracılığıyla işlem hattı, bu durumda, geçirmediğini belirtmek için kullanıcı olanak sağlar. Bu parametre cmdlet'e giriş nesnenin kendisi yerine bir özelliğe bağlı olduğunu unutmayın.

Stop-Proc cmdlet'i için parametre bildirimi aşağıda verilmiştir.

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

Cmdlet'i, girdi işleme yöntemi geçersiz kılmanız gerekir. Aşağıdaki kod gösterir [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kullanılan örnek Stop-Proc cmdlet'te geçersiz kılma. Bu yöntem her istenen işlem adı için işlem özel bir işlem değil, işlemi durdurmak çalışır ve bir çıkış nesnesi daha sonra gönderir sağlar `PassThru` parametre belirtildi.

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>ShouldProcess yöntemi çağırma

Yöntemi, cmdlet'in işleme giriş çağırmalıdır [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çalışma durumuna (örneğin, silme dosyaları) bir değişiklik yapılmadan önce bir işlemin yürütülmesi onaylamak için yöntemi sistemi. Bu, kabuktan doğru "WhatIf" ve "Onayla" davranışı sağlamak Windows PowerShell çalışma zamanı sağlar.

> [!NOTE]
> Bir cmdlet onu desteklediğini belirten işlemelisiniz ve yapma başarısız [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrısı, kullanıcı Sistem beklenmedik bir şekilde değiştirebilirsiniz.

Çağrı [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak Windows PowerShell çalışma zamanı ile değiştirilmesi kaynağın adını gönderir kullanıcıya görüntülenen belirlemede.

Aşağıdaki örnek, çağrısını gösterir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) geçersiz kılmasını gelen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi Stop-Proc cmdlet'i.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>ShouldContinue yöntemi çağırma

Çağrı [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntem, kullanıcı için ikincil bir ileti gönderir. Bu çağrı çağrısından sonra yapılan [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) döndürür `true` ve `Force` parametresi ayarlanmamış `true`. Kullanıcı, sonra işlemi devam olmadığını düşünelim için geri bildirim sunabilir. Cmdlet çağrılarınızı [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) olarak tehlikeli olabilecek bir sistem değişiklikleri veya kullanıcı için tüm için Evet ve Hayır tüm seçenekleri sağlamak istediğinizde için ek bir denetim.

Aşağıdaki örnek, çağrısını gösterir [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) geçersiz kılmasını gelen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi Stop-Proc cmdlet'i.

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>Durdurma giriş işleme

Sistem değişiklikleri yapan bir cmdlet'in yöntemi işleme giriş, giriş işleme durdurma bir yol sağlamanız gerekir. Bu Stop-Proc cmdlet söz konusu olduğunda, gelen bir çağrı yapılır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yönteme [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) yöntemi. Çünkü `PassThru` parametrenin ayarlanmış `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) de çağırır [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) göndermek için işlem hattı için işlem nesnesi.

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [StopProcessSample01 örnek](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Stop-Proc cmdlet test birkaç testi aşağıda verilmiştir. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Windows PowerShell'i başlatın ve aşağıda gösterildiği gibi durdurmak için Stop-Proc cmdlet'ini kullanın. Cmdlet belirttiğinden `Name` parametre zorunlu olarak, cmdlet sorgu parametresi için.

    ```powershell
    PS> stop-proc
    ```

Aşağıdaki çıktı görünür.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Artık "Not" adlı işlemi durdurmak için cmdlet kullanalım. Cmdlet eylemi onaylamanızı ister.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Aşağıdaki çıktı görünür.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Stop-Proc "WINLOGON" adlı kritik işlemini durdurmak için gösterildiği gibi kullanın. İstenir ve işletim sisteminin yeniden neden olacağından bu eylemi gerçekleştirme hakkında uyarı alırsınız.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Aşağıdaki çıktı görünür.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Artık bir uyarı almadan WINLOGON işlemini durdurmak deneyelim. Bu komut girişini kullandığını unutmayın `Force` uyarıyı geçersiz kılmak için parametre.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Aşağıdaki çıktı görünür.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md)

[Nesne türlerini genişletme ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)

[Cmdlet örnekleri](./cmdlet-samples.md)