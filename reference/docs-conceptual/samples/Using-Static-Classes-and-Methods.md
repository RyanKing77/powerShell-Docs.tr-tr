---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Statik Sınıflar ve Yöntemler Kullanma
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687037"
---
# <a name="using-static-classes-and-methods"></a>Statik Sınıflar ve Yöntemler Kullanma
Tüm .NET Framework sınıfları kullanarak oluşturulabilir **New-Object**. Örneğin, oluşturmayı denerseniz bir **System.Environment** veya **System.Math** nesnesi ile **New-Object**, aşağıdaki hata iletileri alırsınız:

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

Bu sınıflardan yeni bir nesne oluşturmak için hiçbir yolu olmadığından bu hataları oluşur. Bu sınıfları, yöntemleri ve durumunu değiştirmemesi özelliklerinin başvuru kitaplıkları vardır. Bunları oluşturmanız gerekmez, sadece bunları kullanın. Sınıflar ve yöntemler gibi bunlar yeniden adlandırılır *statik sınıflar* bunlar oluşturulmadığından yok veya değiştirildi. Bu netleştirmek için statik sınıflar kullanan örnekler sağlayacağız.

### <a name="getting-environment-data-with-systemenvironment"></a>Ortam verilerini System.Environment ile başlama
Genellikle, Windows PowerShell'de bir nesne ile çalışma ilk adımı içerdiği hangi üyelerin bulmak için Get-Member'ı kullanın sağlamaktır. Gerçek sınıfın bir nesnesi olmadığından statik sınıflar ile işlemi biraz farklıdır.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Statik System.Environment sınıfa başvuran
Sınıf adını köşeli parantez içine alarak statik bir sınıfa başvurabilir. Örneğin, başvurabilirsiniz **System.Environment** parantez içinde bir ad yazarak. Bunun yapılması, bazı genel tür bilgileri görüntüler:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Daha önce Windows PowerShell otomatik olarak belirttiğimiz gibi başına '**sistem.**' kullanırken adları türüne **New-Object**. Belirtebileceğiniz bir köşeli parantez içindeki tür adı kullanarak aynı şeyi olur  **\[System.Environment]** olarak  **\[ortam]**.

**System.Environment** sınıfı powershell.exe Windows PowerShell içinde çalışırken, geçerli işlem için çalışma ortamı hakkında genel bilgiler içerir.

Yazarak bu sınıfın ayrıntılarını görüntülemek denerseniz  **\[System.Environment] | Get-Member**, nesne türü olarak bildirilen **System.RuntimeType** değil **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Get-Member statik üyelerle görmesi için belirlediğiniz **statik** parametresi:

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

Biz, artık System.Environment görüntülemek için özellikleri seçebilirsiniz.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Statik System.Environment özelliklerini görüntüleme

System.Environment özelliklerini de statik ve normal özellikler farklı biçimde belirtilmesi gerekir. Kullandığımız **::** göstermek için Windows PowerShell, bir statik yöntem veya özellik ile çalışmak istiyoruz. Windows PowerShell'i başlatmak için kullanılan komut görmek için biz denetleyin **CommandLine** yazarak özelliği:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

İşletim sistemi sürümü denetlemek için OSVersion yazarak görüntü özelliği:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Biz bilgisayar kapatılmakta görüntüleyerek olup olmadığını kontrol edebilirsiniz **HasShutdownStarted** özelliği:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Matematik System.Math ile yapılması

System.Math statik sınıf, bazı matematik işlemlerini gerçekleştirmek için kullanışlıdır. Önemli üyeleri **System.Math** çoğunlukla yöntemler, biz kullanarak görüntüleyebilirsiniz **Get-Member**.

> [!NOTE]
> System.Math için çeşitli yöntemler aynı ada sahip olsa da, kendi parametrelerini türüne göre ayırt edilir.

Yöntemlerini listelemek için aşağıdaki komutu yazın **System.Math** sınıfı.

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

Bu, çeşitli matematik yöntemler görüntüler. Bazı genel yöntemleri nasıl çalıştığını gösteren komutların listesi aşağıda verilmiştir:

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```