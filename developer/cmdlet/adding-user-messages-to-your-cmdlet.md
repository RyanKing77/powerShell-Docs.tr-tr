---
title: Kullanıcı iletileri, cmdlet'e ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854933"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Cmdlet’inize Kullanıcı İletileri Ekleme

Cmdlet'leri, kullanıcı için Windows PowerShell çalışma zamanı tarafından görüntülenebilen iletileri çeşitli türlerde yazabilirsiniz. Bu iletiler, aşağıdaki türleri şunlardır:

- Genel kullanıcı bilgilerini içeren ayrıntılı iletiler.

- Sorun giderme bilgilerini içeren bir ileti hata ayıklayın.

- İlgili olabilecek bir işlemi gerçekleştirmek için cmdlet, bir bildirimi içeren bir uyarı iletilerini beklenmeyen sonuçlar.

- Cmdlet hakkında ne kadar bilgi içeren iletileri iş ilerleme durumu raporunu, uzun süren bir işlem gerçekleştirirken tamamlandı.

Cmdlet'inize yazabilirsiniz ileti sayısını veya cmdlet'inize Yazar iletilerin türünü sınırı yoktur. Her ileti, giriş işleme yöntemi, cmdlet'in içinde özel bir çağrı yaparak yazılır.

## <a name="defining-the-cmdlet"></a>Cmdlet tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Cmdlet'ini her türlü kullanıcı bildirimleri yöntemleri işleme kendi girişten yazabilirsiniz; Bu nedenle, genel olarak, cmdlet gerçekleştirir hangi sistem değişiklikleri belirten herhangi bir fiil kullanarak bu cmdlet adı verebilirsiniz. Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Stop-Proc cmdlet sistem değiştirmek için tasarlanmıştır; Bu nedenle, [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET sınıfı için bildirimi içermelidir `SupportsShouldProcess` özniteliği anahtar sözcüğü ve ayarlanması `true`.

Aşağıdaki kod bu Stop-Proc cmdlet'i sınıf için tanımıdır. Bu tanımı hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Sistem değiştirilmesi için parametreleri tanımlama

Stop-Proc cmdlet, üç parametre tanımlar: `Name`, `Force`, ve `PassThru`. Bu parametreleri tanımlama hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

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

Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, en sık olacaktır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Bu Stop-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) giriş işleme yöntemi. Stop-Proc cmdlet bu uygulamada ayrıntılı iletileri, hata ayıklama iletileri ve uyarı iletileri yazmak için çağrı yapılır.

> [!NOTE]
> Bu yöntem çağırması hakkında daha fazla bilgi için [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemleri bkz [Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Ayrıntılı bir ileti yazma

[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi belirli hata koşulları için ilişkisiz genel kullanıcı düzeyi bilgileri yazmak için kullanılır. Sistem Yöneticisi, sonra diğer komutların işleme devam etmek için bu bilgileri kullanabilirsiniz. Ayrıca, bu yöntem kullanılarak yazılmış herhangi bir bilgi gerektiğinde yerelleştirilmiş olmalıdır.

Aşağıdaki kod bu Proc Stop cmdlet'inden iki çağrıları gösterir [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) geçersiz kılmasını yönteminden [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Hata ayıklama iletisi yazma

[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi cmdlet'inin işlemi sorun giderme için kullanılan hata ayıklama ileti yazmak için kullanılır. İşleme yöntemi girdi çağrı yapılır.

> [!NOTE]
> Windows PowerShell de tanımlayan bir `Debug` ayrıntılı hem de sunar ve hata ayıklama bilgilerini bir parametre. Cmdlet'inize bu parametreyi destekliyorsa, bu çağrı gerekmez [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) çağıran koddaki [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

Kod örnek Proc Stop cmdlet'inden aşağıdaki iki bölümü çağrıları Göster [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.

Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrılır.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Bu hata ayıklama iletisi hemen önce yazılmış [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) çağrılır.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell otomatik olarak yönlendirir herhangi [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) cmdlet'leri ve altyapı izleme çağrıları. Bu, barındırma uygulaması, bir dosya veya bir hata ayıklayıcı cmdlet'inin içinde herhangi bir ek geliştirme iş yapmak zorunda kalmadan izlenecek yöntem çağrılarını sağlar. Aşağıdaki komut satırı girişi izleme işlemi uygular.

**PS > İzleme ifadesi stop-proc-proc.log dosya-komut stop-proc not defteri**

## <a name="writing-a-warning-message"></a>Bir uyarı iletisi yazma

[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) yöntemi cmdlet'i bir salt okunur dosyanın üzerine beklenmeyen bir sonuç, örneğin, olabilecek bir işlem gerçekleştirmek üzere olduğunda bir uyarı yazmak için kullanılır.

Aşağıdaki kod örnek Proc Stop cmdlet'inden çağrısını gösterir [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) geçersiz kılmasını yönteminden [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Bir ilerleme iletisi yazma

[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) işleminin tamamlanma süresi cmdlet'i işlemlerini alırken ilerleme iletilerini yazmak için kullanılır. Bir çağrı [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) geçirmeden bir [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) nesnesini işlemek için kullanıcı barındırma uygulamaya gönderilir.

> [!NOTE]
> Bu Stop-Proc cmdlet çağrısı içermez [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) yöntemi.

Aşağıdaki kod, bir öğeyi kopyalamaya çalışırken bir cmdlet tarafından yazılmış bir ilerleme iletisi örneğidir.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [StopProcessSample02 örnek](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Nesne türleri ve biçimlendirme tanımlayın

Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Şimdi örnek Stop-Proc cmdlet test edin. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Aşağıdaki komut satırı girişi Stop-Proc hata ayıklama bilgilerini yazdır "Not" adlı işlemi durdurur ve ayrıntılı bildirimleri sağlamak için kullanır.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Aşağıdaki çıktı görünür.

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Sistem değiştiren bir Cmdlet oluşturma](./creating-a-cmdlet-that-modifies-the-system.md)

[Bir Windows PowerShell cmdlet'i oluşturma](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
