---
title: Diğer adları, joker karakter genişletmesi, ekleme ve Cmdlet parametreleri için Yardım | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 0f025213087e6f308adf8e597fc01c1320251f76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849143"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Cmdlet Parametrelerinize Diğer Adlar, Joker Karakter Genişletmesi ve Yardım Ekleme

Bu bölümde, diğer adları, joker karakter genişletmesi eklemeyi açıklar ve Yardım iletileri Stop-Proc cmdlet parametreleri (açıklanan [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md)).

Bu Stop-Proc cmdlet Get-Proc cmdlet'ini kullanarak alınan işlemler durdurmaya çalışır (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Bu bölümdeki konular şunlardır:

- [Cmdlet tanımlama](#Defining-the-Cmdlet)

- [Sistem değiştirilmesi için parametreleri tanımlama](#Defining-Parameters-for-System-Modification)

- [Bir parametre diğer adını tanımlama](#Defining-a-Parameter-Alias)

- [Parametreleri için Yardım'ı oluşturma](#Creating-Help-for-Parameters)

- [Bir giriş işleme yöntemi geçersiz kılma](#Overriding-an-Input-Processing-Method)

- [Joker karakter genişletmesi destekleme](#Supporting-Wildcard-Expansion)

- [Kod örneği](#Defining-a-Parameter-Alias)

- [Nesne türlerini tanımlama ve biçimlendirme](#Define-Object-Types-and-Formatting)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Cmdlet tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Sistem değiştirmek için bir cmdlet yazıyorsanız olduğundan, buna uygun olarak adlandırılmalıdır. Bu cmdlet, sistem işlemleri durdurur, bu tarafından tanımlanan fiil "Durdur" kullanır, çünkü [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) sınıfıyla isim işlemi göstermek için "işlem". Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Aşağıdaki kod bu Stop-Proc cmdlet'in sınıfı tanımıdır.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Sistem değiştirilmesi için parametreleri tanımlama

Bu destek sistem değişiklikleri ve kullanıcı geri bildirimi parametrelerini tanımlamak, cmdlet gerekir. Cmdlet tanımlamalıdır bir `Name` parametresi veya eşdeğer bir böylece cmdlet'i bir tür tanımlayıcısı tarafından sistem değiştirmek mümkün olacaktır. Ayrıca, cmdlet tanımlamalıdır `Force` ve `PassThru` parametreleri. Bu parametreler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Bir parametre diğer adını tanımlama

Bir parametre diğer adı, başka bir ad veya bir cmdlet parametresi için iyi tanımlanmış bir 1 harf veya harf 2 kısa ad olabilir. Her iki durumda da, diğer adlarını kullanma amacıyla komut satırından kullanıcı girişi kolaylaştırmaktır. Windows PowerShell aracılığıyla parametre diğer adlarına destekler [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kullanan bildiriminin sözdizimi [Alias()] özniteliği.

Aşağıdaki kod bir diğer ad nasıl eklenir gösterir `Name` parametresi.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Kullanmanın yanı sıra [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) özniteliği, Windows PowerShell çalışma zamanı gerçekleştirir kısmi adıyla eşleşen, bile takma ad yok. Cmdlet'inize varsa, örneğin, bir `FileName` parametresi ve diğer bir deyişle ile başlayan tek parametre `F`, kullanıcı girebilirsiniz `Filename`, `Filenam`, `File`, `Fi`, veya `F` ve hala tanıması Giriş olarak `FileName` parametresi.

## <a name="creating-help-for-parameters"></a>Parametreleri için Yardım'ı oluşturma

Windows PowerShell cmdlet parametreleri için Yardım oluşturmanıza olanak sağlar. Sistemi değişikliği ve kullanıcı geri bildirimi için kullanılan herhangi bir parametre için bunu yapın. Yardım'ı desteklemek üzere her parametre için ayarladığınız `HelpMessage` anahtar öznitelik [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) öznitelik bildirimi. Bu anahtar sözcük parametresini kullanma konusunda yardım almak için kullanıcıya görüntülenecek metni tanımlar. Ayrıca `HelpMessageBaseName` ileti için kullanılacak bir kaynak temel adı tanımlamak için anahtar sözcüğü. Bu anahtar sözcük ayarlarsanız de ayarlamalısınız `HelpMessageResourceId` kaynak tanımlayıcısını belirtmek için anahtar sözcüğü.

Aşağıdaki kod bu Proc Stop cmdlet'inden tanımlar `HelpMessage` anahtar sözcüğü için öznitelik `Name` parametresi.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

Cmdlet'inize işleme yöntemi giriş geçersiz kılmanız gerekir, bu genellikle olacaktır [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Sistem değiştirirken, cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) izin veren yöntemleri bir değişiklik yapılmadan önce geri bildirim sağlamak için kullanıcı. Bu yöntemler hakkında daha fazla bilgi için bkz. [bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Joker karakter genişletmesi destekleme

Birden çok nesne seçimi izin vermek için cmdlet'i kullanabilirsiniz [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) ve [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) sağlayan sınıflar Giriş parametresi joker karakter genişletmesi desteği. Joker karakter düzeni örnekleri olan lsa * \*.txt ve [a-c]\*. Desen, tam anlamıyla kullanılması gereken bir karakter içerdiğinde bir kaçış karakteri geriye tırnak işareti karakteri (') kullanın.

Dosya ve yol adları joker genişletmeleri burada cmdlet'ini birden çok nesne seçimi gerekli olduğunda yolu girişleri için destek isteyebilirsiniz yaygın senaryoları bir örnektir. Burada geçerli klasörde bulunan tüm dosyaları görmek için bir kullanıcının istediği dosya sistemindeki genel durumu gösterir.

Nadiren özelleştirilmiş joker karakter deseni eşleştirme uygulaması gerekir. Bu durumda, cmdlet'inize tam POSIX 1003.2, joker karakter genişletmesi 3.13 belirtimi veya aşağıdaki Basitleştirilmiş alt desteklemesi gerekir:

- **Soru işareti (?).** Belirtilen konumda herhangi bir karakterle eşleşir.

- **Yıldız işareti (\*).** Belirtilen konumundan başlayan sıfır veya daha fazla karakter ile eşleşir.

- **Köşeli ayraç ([]) açın.** Karakter ya da karakter aralığını içerebilir bir desen köşeli ayraç ifadesi tanıtır. Bir aralık gerekiyorsa, tire (-) aralığını belirtmek için kullanılır.

- **Kapatma köşeli ayraç (]).** Bir desen köşeli ayraç ifadesi sona erer.

- **Arka-teklif kaçış karakteri (').** Sonraki karakteri tam anlamıyla alınması gerektiğini gösterir. (Programlı olarak belirtme) yerine komut satırından geri tırnak karakteri belirtirken, geri teklif kaçış karakteri'nin iki kez belirtilmiş gerekir dikkat edin.

> [!NOTE]
> Joker karakter düzenleri hakkında daha fazla bilgi için bkz: [joker karakterleri destekleme Cmdlet parametreleri](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Aşağıdaki kod, joker karakter seçeneklerini ayarlayın ve çözümlemek için kullanılan joker karakter deseni tanımlamak gösterilmektedir `Name` Bu cmdlet için parametre.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Aşağıdaki kod, test etme, işlem adı tanımlanmış bir joker karakter deseni ile eşleşip eşleşmediğini gösterir. İşlem adı desenle eşleşmez, bu durumda, cmdlet üzerinde sonraki işlem adı alma devam ettiğinden, dikkat edin.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [StopProcessSample03 örnek](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Nesne türleri ve biçimlendirme tanımlayın

Windows PowerShell cmdlet arasında .net nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra bunu Windows PowerShell ile bir Windows PowerShell ek bileşeni kayıtlı olması gerekir. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Şimdi örnek Stop-Proc cmdlet test edin. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Windows PowerShell'i başlatın ve ProcessName diğer kullanarak işlemi durdurmak için Stop-Proc `Name` parametresi.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Aşağıdaki çıktı görünür.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Komut satırında aşağıdaki giriş yapın. Name parametresi zorunlu olduğundan istenir. Girme "!?" parametresiyle ilgili Yardım metnini getirir.

    ```powershell
    PS> stop-proc
    ```

Aşağıdaki çıktı görünür.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Artık joker karakter deseni ile eşleşen tüm işlemler durdurmak için şu girdiyi olun "* Not\*". Desenle eşleşen her işlemi durdurmadan önce istenir.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Aşağıdaki çıktı görünür.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Aşağıdaki çıktı görünür.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Aşağıdaki çıktı görünür.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Sistem değiştiren bir Cmdlet oluşturma](./creating-a-cmdlet-that-modifies-the-system.md)

[Bir Windows PowerShell cmdlet'i oluşturma](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Nesne türlerini genişletme ve biçimlendirme](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cmdlet parametreleri joker karakterleri destekleme](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
