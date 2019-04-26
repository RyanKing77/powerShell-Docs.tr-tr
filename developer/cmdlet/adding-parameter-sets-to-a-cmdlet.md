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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068846"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Cmdlet’e Parametre Kümeleri Ekleme

Bu bölümde, Stop-Proc cmdlet'e parametre ayarlar eklemeyi açıklar (açıklanan [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)). Benzer şekilde bu Programcı Kılavuzu'nda açıklanan diğer Stop-Proc cmdlet'leri, bu cmdlet Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Bu bölümdeki konular şunlardır:

- [Parametre kümeleri hakkında bilmeniz gerekenler](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Cmdlet'i sınıf bildirme](#Declaring-the-Cmdlet-Class)

- [Cmdlet parametrelerini bildirme](#Declaring-the-Parameters-of-the-Cmdlet)

- [Bir giriş işleme yöntemi geçersiz kılma](#Overriding-an-Input-Processing-Method)

- [Kod örneği](#Declaring-the-Parameters-of-the-Cmdlet)

- [Nesne türlerini tanımlama ve biçimlendirme](#Defining-Object-Types-and-Formatting)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Parametre kümeleri hakkında bilmeniz gerekenler

Windows PowerShell, bir parametre kümesi parametrelerinin birlikte çalışan bir grup olarak tanımlar. Bir cmdlet parametreleri gruplanarak, kullanıcı hangi grupta parametrelerinin belirtir üzerinde temel işlevselliğini değiştirebilirsiniz tek bir cmdlet oluşturabilirsiniz.

Farklı işlevleri tanımlamak için iki parametre kümeleri kullanan bir cmdlet örneğidir `Get-EventLog` Windows PowerShell tarafından sağlanan cmdlet'i. Bu cmdlet kullanıcının belirttiği farklı bilgiler döndürür `List` veya `LogName` parametresi. Varsa `LogName` parametresi belirtildiğinde, cmdlet, belirli bir olay günlüğüne olaylar hakkında bilgi döndürür. Varsa `List` parametresi belirtildiğinde, cmdlet kendilerini (içerdikleri olay bilgileri değil) dosyaları günlüğü hakkında bilgi döndürür. Bu durumda, `List` ve `LogName` iki ayrı parametre kümesi parametreleri tanımlayın.

Parametre kümeleri hakkında unutmayın gereken iki önemli nokta, Windows PowerShell çalışma zamanı, yalnızca bir parametresi için belirli bir giriş kümesi kullanır ve her parametre kümesi en az bir parametresi olmalıdır, bu parametre kümesi için benzersiz olur.

Bu son nokta göstermek için üç parametre kümeleri bu Stop-Proc cmdlet'ini kullanır: `ProcessName`, `ProcessId`, ve `InputObject`. Bu parametre kümeleri, bir parametre kümeleri içinde olmayan bir parametre vardır. Diğer parametreler parametre kümeleri paylaşabilir, ancak cmdlet benzersiz parametreleri kullanan `ProcessName`, `ProcessId`, ve `InputObject` hangi Windows PowerShell çalışma zamanı kullanması gereken parametreleri kümesini tanımlamak için.

## <a name="declaring-the-cmdlet-class"></a>Cmdlet'i sınıf bildirme

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Cmdlet sistem işlemlerini durdurduğundan olduğundan bu cmdlet için yaşam döngüsü fiili "Durdur" kullanılır. Cmdlet'i işlemlerini çalıştığından isim adı "Proc" kullanılır. Cmdlet fiil ve isim adı cmdlet'i sınıfının adını yansıtılır bildiriminde unutmayın.

> [!NOTE]
> Onaylanan cmdlet fiili adları hakkında daha fazla bilgi için bkz. [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Cmdlet parametrelerini bildirme

Bu cmdlet (Bu parametreler parametre kümeleri ayrıca tanımlayın) cmdlet'i, girdi olarak gereken üç parametreleri tanımlar yanı sıra bir `Force` cmdlet yaptığı yöneten parametre ve bir `PassThru` cmdlet gönderip göndermeyeceğini belirten bir parametre bir komut zincirinden nesne çıktı. Varsayılan olarak, bu cmdlet bir nesneyi ardışık düzeni üzerinden geçmez. Son iki Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Name parametresi bildirme

Bu girdi parametresini durdurulması için işlemleri adını belirtmesini sağlar. Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessName` parametresi için bu parametreyi ayarlayın.

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

Ayrıca, "ProcessName" diğer ad bu parametreye belirtildiğine dikkat edin.

### <a name="declaring-the-id-parameter"></a>ID parametresi bildirme

Bu girdi parametresini durdurulması işlemlerin tanımlayıcıları belirtmesini sağlar. Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `ProcessId` parametre kümesi.

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

Ayrıca, "ProcessId" diğer ad bu parametreye belirtildiğine dikkat edin.

### <a name="declaring-the-inputobject-parameter"></a>Inputobject parametre bildirme

Bu girdi parametresini durdurulması işlemleri hakkındaki bilgileri içeren giriş nesnesi belirtmesini sağlar. Unutmayın `ParameterSetName` anahtar sözcüğü, öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği belirtir `InputObject` parametresi için bu parametreyi ayarlayın.

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

Ayrıca, bu parametre diğer adı yok unutmayın.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Birden fazla parametre kümesine parametrelerinde bildirme

Her parametre kümesi için benzersiz bir parametresi olmalıdır ancak parametreler birden fazla parametre kümesine ait olabilir. Bu durumlarda, paylaşılan parametre vermek bir [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) her olduğu parametre kümesi için öznitelik bildiriminin ait. Bir parametre içinde tüm parametre kümeleri ise yalnızca parametre özniteliği bir kez bildirmeniz gerekir ve parametre kümesi adı belirtmeniz gerekmez.

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

Her cmdlet'i, girdi işleme yöntemi geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi. Bu cmdlet, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet'i işlemlerini herhangi bir sayıda işleyebilmesi yöntemi geçersiz. Bu, farklı bir yöntem, kullanıcı üzerinde hangi parametre kümesi tabanlı aramalar belirttiği bir Select deyimi içerir.

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

Select deyimi tarafından çağrılan yardımcı yöntemler burada açıklanmamaktadır ancak kendi uygulamasında bir sonraki bölümde tam kod örneğini görebilirsiniz.

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [StopProcessSample04 örnek](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edin. İşte gösteren bazı testler nasıl `ProcessId` ve `InputObject` parametreleri, parametre kümeleri bir işlemini durdurmak için test etmek için kullanılabilir.

- Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `ProcessId` kendi tanımlayıcısına göre bir işlemini durdurmak için parametresini ayarlayın. Bu durumda, cmdlet kullanıyor `ProcessId` parametresini ayarlayın işlemi durdurmak için.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Stop-Proc cmdlet ile başlatılan Windows PowerShell ile Çalıştır `InputObject` parametre kümesi işlemleri tarafından alınan not defteri nesnede durdurmak için `Get-Process` komutu.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)

[Bir Windows PowerShell cmdlet'i oluşturma](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
