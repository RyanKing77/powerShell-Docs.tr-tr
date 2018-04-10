---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Statik Sınıflar ve Yöntemler Kullanma
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="398fb-103">Statik Sınıflar ve Yöntemler Kullanma</span><span class="sxs-lookup"><span data-stu-id="398fb-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="398fb-104">Tüm .NET Framework sınıfları kullanarak oluşturulabilir **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="398fb-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="398fb-105">Örneğin, oluşturmayı denerseniz bir **System.Environment** veya **System.Math** nesnesi ile **New-Object**, aşağıdaki hata iletileri alırsınız:</span><span class="sxs-lookup"><span data-stu-id="398fb-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

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

<span data-ttu-id="398fb-106">Bu sınıflardan yeni bir nesne oluşturmak mümkün olduğundan bu hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="398fb-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="398fb-107">Bu yöntemleri ve durumunu değiştirmemesi özelliklerinin başvuru kitaplıkları sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="398fb-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="398fb-108">Bunları oluşturmanız gerekmez, bunları yalnızca kullanın.</span><span class="sxs-lookup"><span data-stu-id="398fb-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="398fb-109">Sınıflar ve yöntemler bunlar gibi çağrılır *statik sınıflar* bunlar oluşturulmadığından yok ya da değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="398fb-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="398fb-110">Bu netleştirmek için statik sınıfları kullanan örnekler sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="398fb-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="398fb-111">System.Environment ile ortam verilerini alma</span><span class="sxs-lookup"><span data-stu-id="398fb-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="398fb-112">Genellikle, Windows PowerShell'de bir nesne ile çalışma ilk adımı Get-üye içerdiği hangi üyeleri bulmak için kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="398fb-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="398fb-113">Gerçek sınıfın bir nesnesi olmadığından statik sınıflarıyla işlemi biraz farklıdır.</span><span class="sxs-lookup"><span data-stu-id="398fb-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="398fb-114">Statik System.Environment sınıfına başvurma</span><span class="sxs-lookup"><span data-stu-id="398fb-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="398fb-115">Sınıf adı köşeli ayraç içine çevreleyen tarafından bir statik sınıf başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="398fb-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="398fb-116">Örneğin, başvurabilirsiniz **System.Environment** köşeli ayraçlar içinde adını yazarak.</span><span class="sxs-lookup"><span data-stu-id="398fb-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="398fb-117">Bunun yapılması, bazı genel tür bilgileri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="398fb-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="398fb-118">Biz daha önce Windows PowerShell otomatik olarak belirtildiği gibi başına '**sistem.**'</span><span class="sxs-lookup"><span data-stu-id="398fb-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="398fb-119">kullandığınızda adlarını yazmak için **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="398fb-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="398fb-120">Belirleyebileceğiniz bir köşeli parantez içindeki tür adı kullanarak aynı şeyi olur  **\[System.Environment]** olarak  **\[ortam]**.</span><span class="sxs-lookup"><span data-stu-id="398fb-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="398fb-121">**System.Environment** sınıfı powershell.exe Windows PowerShell içinde çalışırken, geçerli işlem için çalışma ortamını hakkında genel bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="398fb-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="398fb-122">Yazarak bu sınıf ayrıntılarını görüntülemeyi deneyin  **\[System.Environment] | Get-üye**, nesne türü olarak bildirilen **System.RuntimeType** değil **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="398fb-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="398fb-123">Get-üyeyle statik üyeleri görüntülemek için belirtmek **statik** parametre:</span><span class="sxs-lookup"><span data-stu-id="398fb-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

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

<span data-ttu-id="398fb-124">Biz, artık System.Environment görüntülemek özelliklerini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="398fb-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="398fb-125">System.Environment statik özelliklerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="398fb-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="398fb-126">System.Environment özelliklerini de statik ve normal Özellikler'den farklı bir şekilde belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="398fb-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="398fb-127">Kullanırız **::** belirtmek için bir statik yöntemi veya özelliği ile çalışmak için istiyoruz Windows PowerShell için.</span><span class="sxs-lookup"><span data-stu-id="398fb-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="398fb-128">Windows PowerShell'i başlatmak için kullanılan komut, biz denetleyin **CommandLine** yazarak özelliği:</span><span class="sxs-lookup"><span data-stu-id="398fb-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="398fb-129">İşletim sistemi sürümünü denetlemek için yazarak OSVersion özelliği görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="398fb-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="398fb-130">Biz bilgisayar görüntüleyerek kapanma sürecinde olup olmadığını denetleyebilirsiniz **HasShutdownStarted** özelliği:</span><span class="sxs-lookup"><span data-stu-id="398fb-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="398fb-131">Matematik System.Math ile yapılması</span><span class="sxs-lookup"><span data-stu-id="398fb-131">Doing Math with System.Math</span></span>

<span data-ttu-id="398fb-132">System.Math statik sınıf, bazı matematiksel işlemleri gerçekleştirmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="398fb-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="398fb-133">Önemli üyeleri **System.Math** çoğunlukla yöntemleri, biz kullanarak görüntüleyebilirsiniz **Get-üye**.</span><span class="sxs-lookup"><span data-stu-id="398fb-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="398fb-134">System.Math için çeşitli yöntemler aynı ada sahip olsa da, bunların parametrelerini türüne göre ayırt edilir.</span><span class="sxs-lookup"><span data-stu-id="398fb-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="398fb-135">Yöntemlerinin listelemek için aşağıdaki komutu yazın **System.Math** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="398fb-135">Type the following command to list the methods of the **System.Math** class.</span></span>

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

<span data-ttu-id="398fb-136">Bu, birkaç matematiksel yöntemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="398fb-136">This displays several mathematical methods.</span></span> <span data-ttu-id="398fb-137">Ortak yöntemlerin bazıları nasıl çalıştığını göstermek komutların listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="398fb-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

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