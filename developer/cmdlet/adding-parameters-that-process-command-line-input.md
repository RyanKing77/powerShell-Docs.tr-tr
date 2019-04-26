---
title: Komut satırı giriş parametreleri ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068819"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Komut Satırı Girişini İşleyen Parametreler Ekleme

Bir giriş bir cmdlet için komut satırı kaynağıdır. Bu konuda, bir parametre eklemeyi açıklar **Get-Proc** cmdlet (açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md)) cmdlet'ini ve yerel bilgisayardan üzerinde açık göre giriş işleyebilmesi nesneleri cmdlet'e geçirilen. **Get-Proc** açıklanan cmdlet'i burada adlarına göre işlemler alır ve ardından bir komut isteminde işlemleri hakkındaki bilgileri görüntüler.

Bu konuda aşağıdaki bölümleri şunlardır:

- [Cmdlet'i sınıf tanımlama](#Defining-the-Cmdlet-Class)

- [Parametreleri bildirme](#Declaring-Parameters)

- [Parametre doğrulaması destekleme](#Supporting-Parameter-Validation)

- [Bir giriş işleme yöntemi geçersiz kılma](#Overriding-an-Input-Processing-Method)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Defining-Object-Types-and-Formatting)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Cmdlet'i sınıf tanımlama

İlk cmdlet oluşturma cmdlet'i adlandırma ve cmdlet uygulayan .NET Framework sınıf bildirimi adımdır. Burada seçilen fiil adı "Get", bu nedenle bu cmdlet, işlem bilgilerini alır. (Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Sınıf bildirimi işte **Get-Proc** cmdlet'i. Bu tanımı hakkında ayrıntılar verilmiştir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Parametreleri bildirme

Bir cmdlet parametresi cmdlet giriş sağlamak kullanıcının sağlar. Aşağıdaki örnekte, **Get-Proc** ve `Get-Member` ardışık cmdlet'leri adlarının ve `MemberType` parametresi için `Get-Member` cmdlet'i. Parametresinin "özelliği" bağımsız değişken

**PS > get-proc; `get-member` - membertype özelliği**

Bir cmdlet için parametreleri bildirmek için önce parametreleri temsil eden özelliklerinin tanımlamanız gerekir. İçinde **Get-Proc** cmdlet'i, yalnızca bir parametredir `Name`, bu durumda temsil eden almak için .NET Framework işlem nesnesinin adı. Bu nedenle, cmdlet'i sınıfı bir dizi adını kabul etmek için dize türünde bir özelliğini tanımlar.

Parametre bildirimi için işte `Name` parametresinin **Get-Proc** cmdlet'i.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Bu özellik, Windows PowerShell çalışma zamanı bildirmek için `Name` parametresi bir [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) özniteliği, property tanımına eklenir. Bu öznitelik bildirmek için temel söz dizimi `[Parameter()]`.

> [!NOTE]
> Bir parametre açıkça genel olarak işaretlenmelidir. İç ortak varsayılan olarak işaretlenmez ve Windows PowerShell çalışma zamanı tarafından bulunamadı parametreler.

Bu cmdlet için bir dize dizisi kullanan `Name` parametresi. Bu cmdlet birden fazla öğe kabul etmek izin verdiğinden Mümkünse, cmdlet'inize ayrıca bir parametre bir dizi olarak tanımlamanız gerekir.

#### <a name="things-to-remember-about-parameter-definitions"></a>Parametre tanımları hakkında bunları unutmayın

- Önceden tanımlanmış Windows PowerShell parametre adları ve veri türleri cmdlet'inize Windows PowerShell cmdlet'leri ile uyumlu olduğundan emin olmak mümkün olduğunca yeniden. Örneğin, önceden tanımlanmış tüm cmdlet'leri kullanıyorsanız `Id` kullanıcı olacak bir kaynak bir kolayca belirlemek için parametre adı parametrenin kullanıyordur hangi cmdlet bağımsız olarak anlamı anlama. Temelde, parametre adları, ortak dil çalışma zamanı (CLR) değişken adları için kullanılanlarla aynı kurallara izleyin. Parametre adlandırma hakkında daha fazla bilgi için bkz. [Cmdlet parametresi adları](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell, tutarlı bir kullanıcı deneyimi sağlamak için birkaç parametre adlarını saklar. Bu parametre adlarını kullanmayın: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, ve `OutBuffer`. Ayrıca, aşağıdaki diğer adlar için bu parametre adları ayrılmıştır: `vb`, `db`, `ea`, `ev`, `ov`, ve `ob`.

- `Name` cmdlet'lerinizi kullanmak için önerilen bir basit ve ortak parametre adıdır. Belirli bir cmdlet için benzersiz ve hatırlamak zor olan bir karmaşık adı yerine böyle bir parametre adı seçmek daha iyidir.

- Varsayılan olarak, kabuk durumu korur. ancak Windows PowerShell'de, büyük küçük harf duyarsız parametrelerdir. Büyük küçük harf duyarlılığı bağımsız değişkenlerinin işlemi cmdlet'inin bağlıdır. Bağımsız değişkenler olarak komut satırında belirtilen parametresi geçirilir.

- Diğer parametre bildirimleri örnekleri için bkz: [Cmdlet parametreleri](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Konumsal veya adlandırılmış parametreleri bildirme

Bir cmdlet her parametre konumsal veya adlandırılmış bir parametre olarak ayarlamalısınız. Her iki tür parametreleri tek bağımsız değişken, virgül ve Boole ayarları tarafından ayrılmış birden çok bağımsız değişkeni kabul eder. Bir Boole parametresi olarak da adlandırılan bir *geçiş*, yalnızca Boole ayarları işler. Anahtar parametresinin varolup olmadığını belirlemek için kullanılır. Önerilen varsayılan `false`.

Örnek **Get-Proc** cmdlet'i tanımlar `Name` parametre pozisyon 0 ile konumsal bir parametre olarak. Başka bir deyişle, ilk bağımsız değişkeni komut satırında kullanıcının girdiği Bu parametre için otomatik olarak eklenir. Adlandırılmış parametre tanımlamak istiyorsanız, komut satırından, parametre adı kullanıcı belirtmeniz gerekir bırakın `Position` öznitelik bildiriminin dışında anahtar sözcüğü.

> [!NOTE]
> Parametre olarak adlandırılmalıdır yoksa, kullanıcılar, parametre adı gerekmez. böylece en çok kullanılan parametreleri konumsal yapmanızı öneririz.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Parametreler, zorunlu veya isteğe bağlı olarak bildirme

Bir cmdlet her parametrenin isteğe bağlı veya zorunlu bir parametre olarak ayarlamanız gerekir. Örnekteki **Get-Proc** cmdlet'ini `Name` çünkü parametre olarak isteğe bağlı tanımlanır `Mandatory` anahtar sözcüğü, öznitelik bildiriminde ayarlanmadı.

## <a name="supporting-parameter-validation"></a>Parametre doğrulaması destekleme

Örnek **Get-Proc** cmdlet'i bir giriş doğrulama özniteliği ekler [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), `Name` parametresi doğrulamasını etkinleştirmek için Giriş ne olduğunu `null` ya da boş. Bu öznitelik Windows PowerShell tarafından sağlanan çeşitli doğrulama özniteliklerinin biridir. Diğer doğrulama öznitelikleri örnekleri için bkz. [parametre girişi doğrulama](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Bir giriş işleme yöntemi geçersiz kılma

Komut satırı girdi işlemek üzere cmdlet'inize ise, yöntem işleme uygun giriş geçersiz kılması gerekir. Temel giriş işleme yöntemleri de sunulan [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

**Get-Proc** cmdlet'i geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) işlemek için yöntemi `Name` kullanıcı veya bir betik tarafından sağlanan parametre girişi. Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı ya da tüm işlemler için alır. Dikkat [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), çağrı [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) çıktı mekanizması, çıkış göndermek için işlem hattına nesneleri. Bu çağrı, ikinci parametresinin `enumerateCollection`, ayarlanır `true` çıkış dizisi süreç nesneleri numaralandırır ve bir işlem aynı anda komut satırına yazmak için Windows PowerShell çalışma zamanı bildirmek için.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [GetProcessSample02 örnek](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Windows PowerShell cmdlet'lerini kullanarak .NET Framework nesneleri arasında bilgi geçirir. Sonuç olarak, bir cmdlet'in kendi türü tanımlamanız gerekebilir veya bir cmdlet başka bir cmdlet tarafından sağlanan mevcut türü genişletmek gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra bir Windows PowerShell ek bileşenini kullanarak Windows PowerShell ile kaydetmelisiniz. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydettiğinizde, komut satırında çalıştırarak test edebilirsiniz. Örnek cmdlet kodunu test etmek için iki yolu vardır. Komut satırından cmdlet'leri kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Windows PowerShell komut isteminde, Internet Explorer işlemi, "IEXPLORE." adlı listelemek için aşağıdaki komutu kullanın.

    ```powershell
    PS> get-proc -name iexplore
    ```

Aşağıdaki çıktı görünür.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- "IEXPLORE" adlı Internet Explorer, Outlook ve not defteri işlemleri listelemek için "OUTLOOK" ve "Not", aşağıdaki komutu kullanın. Birden çok işlem varsa, bunların tümünün görüntülenir.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Aşağıdaki çıktı görünür.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Ayrıca bkz:

[İşlem ardışık düzen giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md)

[İlk Cmdlet'inize oluşturma](./creating-a-cmdlet-without-parameters.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell başvurusu](../windows-powershell-reference.md)

[Cmdlet örnekleri](./cmdlet-samples.md)
