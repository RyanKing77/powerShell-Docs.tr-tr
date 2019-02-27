---
title: Cmdlet'i parametre türleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849521"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet Parametresi Türleri

Bu konuda, cmdlet'ler bildirebilirsiniz parametreleri farklı türleri açıklanmaktadır. Cmdlet parametreleri, konumsal, adlandırılmış, gerekli, isteğe bağlı veya parametreleri geçin.

## <a name="positional-and-named-parameters"></a>Konumsal ve adlandırılmış parametreleri

Tüm cmdlet parametreleri, adlandırılmış ya da konumsal parametrelerdir. Adlandırılmış parametre cmdlet çağırırken parametre adı ve bağımsız değişken türü gerektirir. Konumsal bir parametre, yalnızca göreli sıralarını bağımsız değişken türü gerektiriyor. Sistem, sonra ilk konumsal parametresi ilk adsız bağımsız değişken eşler. Sistem ikinci adsız bağımsız değişken ikinci eşler adlandırılmamış parametreyi ve benzeri. Varsayılan olarak, tüm cmdlet parametreleri parametreleri olarak adlandırılır.

Adlandırılmış parametre tanımlamak için atla `Position` anahtar sözcüğünü **parametre** aşağıdaki parametreyi bildirimde gösterildiği gibi öznitelik bildirimi.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Konumsal bir parametre tanımlamak için ekleme `Position` anahtar sözcüğü parametresinde özniteliği bildirimi ve ardından bir konum belirtin. Aşağıdaki örnekte, `UserName` parametresi, konumu 0 ile konumsal bir parametre olarak bildirilir. Bu, ilk bağımsız değişken çağrısı Bu parametre için otomatik olarak bağlanacak anlamına gelir.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Kullanıcı, cmdlet çalıştırıldığında, parametre adını girin gerekmez. böylece en çok kullanılan parametreleri konumsal parametreler olarak bildirilmesi iyi cmdlet'i tasarım önerir.

Konumsal ve adlandırılmış parametreleri tek bağımsız değişkenler veya virgülle ayırarak birden çok bağımsız değişkeni kabul eder. Yalnızca bir dizi gibi dizeleri koleksiyonu parametreyi kabul eden birden çok bağımsız değişkeni izin verilir. Konumsal ve adlandırılmış parametreleri aynı cmdlet'inde karışımı. Bu durumda, sistem adlandırılmış bağımsız değişkenler ilk alır ve ardından kalan eşlemek için deneme konumsal parametreler için bağımsız değişkenler adlandırılmamış.

Aşağıdaki komutlar, belirtebileceğiniz tek ve birden çok bağımsız değişken parametreleri için farklı yolları göstermektedir `Get-Command` cmdlet'i. Son iki örnek olduğuna dikkat edin **-adı** çünkü belirtilmesi gerekmez `Name` parametresi, konumsal bir parametre olarak tanımlanır.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Zorunlu ve isteğe bağlı parametreler

Ayrıca, cmdlet parametreleri zorunlu veya isteğe bağlı parametreler olarak tanımlayabilirsiniz. (Çalışma zamanı Windows PowerShell cmdlet'ini çağırmadan önce zorunlu bir parametre belirtilmelidir.)  Varsayılan olarak, Parametreler, isteğe bağlı olarak tanımlanır.

Zorunlu bir parametre tanımlamak için ekleme `Mandatory` parametresinde anahtar sözcüğü özniteliği bildirimi ve ayarlamak `true`aşağıdaki parametreyi bildirimde gösterildiği gibi.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

İsteğe bağlı bir parametre tanımlamak için atla `Mandatory` anahtar sözcüğünü **parametre** aşağıdaki parametreyi bildirimde gösterildiği gibi öznitelik bildirimi.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Anahtar parametreleri

Windows PowerShell sağlayan bir [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) değerini bir parametre tanımlamanıza olanak tanıyan türü otomatik olarak ayarlandığından `false` cmdlet parametresi belirtilmezse çağrılır. Mümkün olduğunda yerine Boole parametreleri anahtar parametreleri kullanın.

Aşağıdaki örneği göz önünde bulundurun. Varsayılan olarak, birçok Windows PowerShell cmdlet'leri bir çıkış nesnesi işlem hattı aşağı geçirmeyin. Ancak, bu cmdlet'ler sahip bir `PassThru` varsayılan davranışı geçersiz kılan parametre geçin. Varsa `PassThru` bu cmdlet'ler çağrıldığında parametre belirtilirse, cmdlet ardışık düzene bir çıkış nesnesi döndürür.

Parametre bir varsayılan değerine sahip olacak şekilde ihtiyacınız varsa `true` arama parametresi belirtilmediğinde, parametre algılama ters göz önünde bulundurun. Parametre özniteliği için bir Boole değeri ayarlamak yerine örnek, `true`, özellik olarak bildirin [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) yazın ve ardından parametreninvarsayılandeğeriniayarlayın`false`.

Bir anahtar parametresi tanımlamak için özellik olarak bildirin [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) , aşağıdaki örnekte gösterildiği gibi yazın.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Cmdlet parametresi belirtildiğinde, bu işlem yapmak için aşağıdaki yöntemleri işleme giriş birini yapısında kullanın.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
