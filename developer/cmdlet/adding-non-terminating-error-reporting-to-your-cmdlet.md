---
title: Sonlandırıcı olmayan hata raporlama, cmdlet'e ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056065"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Cmdlet’inize Sonlandırıcı Olmayan Hata Raporlama Ekleme

Cmdlet'leri rapor olmak üzere sonlandırmasız hatalar çağırarak [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi ve geçerli giriş nesnesi ya da daha fazla gelen çalışmaya devam işlem hattı nesneleri. Bu bölümde, giriş işleme yöntemlerinden olmak üzere sonlandırmasız hatalar raporları bir cmdlet oluşturma açıklanmaktadır.

Olmak üzere sonlandırmasız hatalar (aynı zamanda için Sonlandırıcı hataları), cmdlet geçmesi gereken bir [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) hatayı tanımlayan nesne. Her hata kaydı "hata tanımlayıcı." adı verilen benzersiz bir dize tanımlanır. Tanımlayıcı yanı sıra her bir hata kategorisi tarafından tanımlanan sabitleri tarafından belirtilen bir [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) sabit listesi. Kullanıcı ayarlayarak kategorilerine göre hataları görüntüleyebilirsiniz `$ErrorView` "CategoryView" değişkenini.

Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).

Bu bölümdeki konular şunlardır:

- [Cmdlet tanımlama](#Defining-the-Cmdlet)

- [Parametreleri tanımlama](#Defining-Parameters)

- [Geçersiz kılma yöntemleri işleme giriş](#Overriding-Input-Processing-Methods)

- [Raporlama olmak üzere Sonlandırmasız hatalar](#Reporting-Nonterminating-Errors)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Define-Object-Types-and-Formatting)

- [Cmdlet oluşturma](#Building-the-Cmdlet)

- [Sınama cmdlet'i](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Cmdlet tanımlama

İlk adımda cmdlet'i oluşturma her zaman cmdlet adlandırma ve cmdlet uygulayan .NET sınıf bildirme. Bu cmdlet, burada seçilen fiil adı "Get", bu nedenle işlem bilgilerini alır. (Komut satırı girişi neredeyse her türlü bilgi alma özelliğine sahip olan cmdlet işleyebilir.) Onaylanan cmdlet fiilleri hakkında daha fazla bilgi için bkz: [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).

Bu Get-Proc cmdlet tanımı aşağıda verilmiştir. Bu tanımın ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Parametreleri tanımlama

Gerekirse, cmdlet'inize girişini işleme parametrelerini tanımlamanız gerekir. Bu Get-Proc cmdlet tanımlayan bir `Name` açıklandığı parametresi [parametreler, işlem komut satırı girişi ekleme](./adding-parameters-that-process-command-line-input.md).

Parametre bildirimi için işte `Name` bu Get-Proc cmdlet parametresi.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a>Geçersiz kılma yöntemleri işleme giriş

Tüm cmdlet'ler tarafından sağlanan yöntemleri işleme giriş en az biri geçersiz kılmanız gerekir [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı. Bu yöntemleri ele alınmıştır [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Cmdlet'inize her bir kayıt olarak bağımsız olarak işlemelidir.

Bu Get-Proc cmdlet geçersiz kılmalar [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) işlemek için gereken yöntemini `Name` kullanıcı veya bir betik tarafından sağlanan giriş parametresi. Adsız sağlanırsa, bu yöntem işlemleri her istenen işlem adı veya tüm işlemler için alırsınız. Bu geçersiz kılma ayrıntıları verilir [oluşturma bilgisayarınızı ilk Cmdlet](./creating-a-cmdlet-without-parameters.md).

#### <a name="things-to-remember-when-reporting-errors"></a>Hata raporlama, bunları unutmayın

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne yazılırken bir hata özel durum özellikleri temel alınarak gerektirdiğinde cmdlet geçirir. Kullanılacak özel durum belirlerken .NET yönergeleri izleyin. Temel olarak, hata anlamsal olarak var olan bir özel durum ile aynı ise, cmdlet kullanın veya bu özel durumdan türetilen. Aksi takdirde, yeni özel durum ya da doğrudan özel durum hiyerarşisi türetilmelidir [System.Exception](/dotnet/api/System.Exception) sınıfı.

Hata tanımlayıcıları (ErrorRecord sınıfın FullyQualifiedErrorId özelliği erişilir) oluştururken aşağıdakileri göz önünde bulundurun.

- Tanılama amacıyla, böylelikle tam tanımlayıcı incelerken, hangi hata belirleyebilirsiniz ve hata geldiği burada hedeflenen kullanım dizeleri.

- Biçimlendirilmiş tam hata tanımlayıcısı şu şekilde olabilir.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

Önceki örnekte, hata tanımlayıcı (ilk belirteç) hatanın ne olduğunu belirler ve kalan bölümü hata nereden geldiğini belirten olduğuna dikkat edin.

- Daha karmaşık senaryolarda, inceleme üzerinde ayrıştırılabilir bir nokta ayrılmış belirteç hata tanımlayıcı olabilir. Bu hata tanımlayıcısı ve hata kategorisi yanı sıra hata tanımlayıcı kısımlarına çok dal sağlar.

Cmdlet'i belirli hata tanımlayıcıları farklı kod yolları atamanız gerekir. Hata tanımlayıcıların ataması için aşağıdaki bilgileri unutmayın:

- Hata tanımlayıcı cmdlet'i süresince sabit kalması gerekir. Hata tanımlayıcı cmdlet'i sürümleri arasında semantiği değiştirmeyin.

- Bildirilen hata tersely karşılık gelen hata tanımlayıcı için metin kullanın. Boşluk veya noktalama işareti kullanmayın.

- Tekrarlanabilir hata tanımlayıcılar oluşturma cmdlet'inize vardır. Örneğin, bir işlem tanımlayıcısını içeren bir tanımlayıcı üretmemelidir. Yalnızca bunlar aynı sorunu yaşayan başka kullanıcılar tarafından görülen tanımlayıcıları karşılık hata tanımlayıcılar bir kullanıcı için yararlıdır.

İşlenmeyen özel durumları aşağıdaki koşul Windows PowerShell tarafından yakalanan değil:

- Bir cmdlet yeni bir iş parçacığı ve iş parçacığı işlenmeyen bir özel durum oluşturduğunda çalışan kodu oluşturur, Windows PowerShell hata yakalayamaz ve işlemini sonlandırır.

- Bir nesne işlenmeyen bir özel durum neden kodu yok Edicisi veya atma yöntemleri varsa, Windows PowerShell hata yakalayamaz ve işlemini sonlandırır.

## <a name="reporting-nonterminating-errors"></a>Raporlama olmak üzere Sonlandırmasız hatalar

Çıkış akışı kullanarak, yöntemleri işleme giriş herhangi biri olmak üzere sonlandırmasız bir hata rapor edebilirsiniz [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi. İşte bir kod örneği bu Get-Proc cmdlet'inden yapılan çağrıyı gösterir [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gelen geçersiz kılmasını içinde [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi. Cmdlet'i bir işlem için belirtilen işlem tanımlayıcısı bulamazsa, bu durumda, bir çağrı yapılır.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Olmak üzere Sonlandırmasız hatalar yazmakla ilgili bunları unutmayın

Olmak üzere sonlandırmasız bir hata için cmdlet belirli her giriş nesnesi için bir özel hata tanımlayıcı oluşturmanız gerekir.

Bir cmdlet sık olmak üzere sonlandırmasız bir hata tarafından oluşturulan Windows PowerShell eylem değiştirmesi gerekiyor. Bunu tanımlayarak yapabilirsiniz `ErrorAction` ve `ErrorVariable` parametreleri. Tanımlanıyorsa `ErrorAction` parametresi, cmdlet kullanıcı seçenekleri sunan [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), eylem ayarlayarak da doğrudan etkileyebilir `$ErrorActionPreference` değişkeni.

Cmdlet'ini kullanarak değişken için olmak üzere sonlandırmasız hatalar kaydedebilirsiniz `ErrorVariable` , bu ayardan etkilenmez parametresini `ErrorAction`. Hataları var olan bir hata değişkenine bir artı işareti (+) ekleyerek değişken adının önüne eklenerek.

## <a name="code-sample"></a>Kod örneği

Tamamlanmış C# örnek kod için bkz: [GetProcessSample04 örnek](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Nesne türleri ve biçimlendirme tanımlayın

Windows PowerShell cmdlet arasında .NET nesneleri kullanarak bilgileri geçirir. Sonuç olarak, bir cmdlet kendi türü tanımlamanız gerekebilir veya başka bir cmdlet tarafından sağlanan mevcut türü genişletmek cmdlet gerekebilir. Yeni türleri tanımlama veya varolan türleri genişletme hakkında daha fazla bilgi için bkz. [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Cmdlet oluşturma

Bir cmdlet uyguladıktan sonra Windows PowerShell ile bir Windows PowerShell ek bileşeni kaydetmelisiniz. Cmdlet'leri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Sınama cmdlet'i

Windows PowerShell ile cmdlet'ini kaydedildi, komut satırında çalıştırarak test edebilirsiniz. Şimdi hata raporlarını olup olmadığını görmek için örnek Get-Proc cmdlet sınama:

- Windows PowerShell'i başlatın ve "TEST" adlı işlem almak için Get-Proc cmdlet'ini kullanın.

    ```powershell
    PS> get-proc -name test
    ```

Aşağıdaki çıktı görünür.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Ayrıca bkz:

[İşlem ardışık düzen giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md)

[Komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md)

[İlk Cmdlet'inize oluşturma](./creating-a-cmdlet-without-parameters.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell başvurusu](../windows-powershell-reference.md)

[Cmdlet örnekleri](./cmdlet-samples.md)
