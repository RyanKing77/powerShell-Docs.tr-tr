---
title: Modul Skriptu Powershellu yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470790"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="8da19-102">PowerShell Betik Modülü Yazma</span><span class="sxs-lookup"><span data-stu-id="8da19-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="8da19-103">Betik modülündeki bir .psm1 uzantısında kaydedilen aslında herhangi geçerli PowerShell Betiği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8da19-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="8da19-104">Bu uzantı, onedrive'daki dosyanızda çok sayıda kural ve cmdlet'lerini kullanmak PowerShell altyapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8da19-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="8da19-105">Kodunuzun diğer sistemlerde yanı sıra kapsamı yönetme yüklemenize yardımcı olması için bu özelliklerin çoğu vardır.</span><span class="sxs-lookup"><span data-stu-id="8da19-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="8da19-106">Ayrıca, daha karmaşık yüklemeleri ve çözümleri açıklamak bir modül bildirim dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da19-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="8da19-107">Modul Skriptu Powershellu yazma</span><span class="sxs-lookup"><span data-stu-id="8da19-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="8da19-108">Geçerli bir PowerShell Betiği, bir .psm1 dosyasına kaydetme ve ardından bu dosyayı PowerShell bulabileceğiniz bir yerde bulunan bir dizinde kaydederek bir betik modülüne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8da19-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="8da19-109">Ayrıca, betiğinizi çalıştırmak için ihtiyacınız olan tüm kaynakları yerleştirebilirsiniz bu klasörde yanı sıra bir bildirim dosyası, PowerShell modülünüzde nasıl çalıştığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8da19-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="8da19-110">Temel bir PowerShell modülü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8da19-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="8da19-111">Varolan bir PowerShell komut dosyasını alın ve komut dosyasını bir .psm1 uzantısıyla kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8da19-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="8da19-112">Bir komut dosyasıyla .psm1 kaydetme uzantısı anlamına gelir modülü cmdlet'lerini aşağıdaki gibi kullanabilirsiniz [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), onunla ilgili.</span><span class="sxs-lookup"><span data-stu-id="8da19-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="8da19-113">Öncelikle kolayca içeri aktarabilir ve kodunuzun diğer kullanıcının sistemlerine dışarı aktarmak için bu cmdlet'ler mevcut.</span><span class="sxs-lookup"><span data-stu-id="8da19-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="8da19-114">(Alternatif bir çözüm diğer sistemler ve ardından nokta kaynak kodunuzu özellikle ölçeklenebilir bir çözüm değilse, etkin belleğe yüklemek olacaktır.) Daha fazla bilgi için **modülü cmdlet'lerini ve değişkenleri** konusundaki [Windows PowerShell modülleri](./understanding-a-windows-powershell-module.md) varsayılan olarak, komut dosyanızdaki tüm işlevleri .psm1 dosyanızı içeri kullanıcılar için erişilebilir olduğunu unutmayın ancak özellikleri değildir.</span><span class="sxs-lookup"><span data-stu-id="8da19-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="8da19-115">Başlıklı bir örnek PowerShell Betiği `Show-Calendar`, bu konunun sonunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8da19-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="8da19-116">Kullanıcı erişimi belirli işlevleri ve özellikleri denetlemek için çağrı [dışarı aktarma ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) betiğinizi sonunda.</span><span class="sxs-lookup"><span data-stu-id="8da19-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="8da19-117">Sayfanın alt kısmındaki örnek kod eline, varsayılan olarak yalnızca tek bir işlevi vardır.</span><span class="sxs-lookup"><span data-stu-id="8da19-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="8da19-118">Ancak, açıkça göstermek için aşağıdaki kodda açıklandığı şekilde istediğiniz hangi işlevleri kullanıma çağırmanızı önerilir:</span><span class="sxs-lookup"><span data-stu-id="8da19-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="8da19-119">Ayrıca, ne bir modül bildirimi kullanılarak alınır kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da19-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="8da19-120">Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md) ve [bildirim PowerShell modülü yazma](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="8da19-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="8da19-121">Kendi modülünüzü yüklü gereken modülleri varsa, bunları bir çağrı ile kullanabileceğiniz `Import-Module`, kendi modülünüzü üstünde.</span><span class="sxs-lookup"><span data-stu-id="8da19-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="8da19-122">`Import-Module` bir sistemin hedeflenen bir modülü içe aktaran bir cmdlet olur.</span><span class="sxs-lookup"><span data-stu-id="8da19-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="8da19-123">Bu nedenle, bu da yordamdaki sonraki bir zamanda de kendi modülünü yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8da19-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="8da19-124">Bu sayfanın sonundaki örnek kodu alma modüllerin kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="8da19-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="8da19-125">Ancak olsaydı, dosyasının en üstüne aşağıdaki kodu açıklandığı listelenir:</span><span class="sxs-lookup"><span data-stu-id="8da19-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="8da19-126">Modülünüzün PowerShell Yardım sistemine tanımlamak için standart Yardım açıklamaları içindeki dosyanın kullanabilir veya ek Yardım dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8da19-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="8da19-127">Kod örneği, bu konunun altındaki yorumlar bölümünde Yardım bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8da19-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="8da19-128">Ayrıca, Ek Yardım içeriğini içeren genişletilmiş XML dosyaları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da19-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="8da19-129">Daha fazla bilgi için [yazma yardımcı olmak için Windows PowerShell modülleri](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="8da19-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="8da19-130">Ek modüller, XML dosyaları ya da modülünüzde ile paket istediğiniz diğer içerik varsa, bir modül bildirimi ile bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da19-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="8da19-131">Bir modül bildirimi diğer modüller, dizin düzenleri, sürüm numaralarını, veri yazar ve diğer bilgilere adlarını içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="8da19-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="8da19-132">PowerShell modülü bildirim dosyasını düzenlemek ve çözümünüzü dağıtmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8da19-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="8da19-133">Ancak, bu örnekte görece basit yapısı nedeniyle, bir bildirim dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8da19-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="8da19-134">Daha fazla bilgi için [modülü bildirimlerini](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="8da19-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="8da19-135">Yükleme ve modülünüzde çalıştırmak için uygun PowerShell yollardan biri modülü kaydedin ve çağrı yapmak `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="8da19-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="8da19-136">Modülünüzün yükleyebileceğiniz yolları bulunur `$env:PSModulePath` genel değişkeni.</span><span class="sxs-lookup"><span data-stu-id="8da19-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="8da19-137">Örneğin, bir sistemde bir modüle kaydetmek için yaygın bir yolu olabilir `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="8da19-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="8da19-138">Yalnızca tek bir .psm1 dosya olsa bile, modülü, mevcut bir klasör oluşturmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8da19-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="8da19-139">Modülünüzde bu yollardan birine kaydetmediyseniz, modülünüzde çağrısında konumunu geçirin gerekirdi `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="8da19-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="8da19-140">(Aksi halde, PowerShell bulmak mümkün olmazdı.) PowerShell modülü yollardan biri, modül yerleştirdiyseniz, PowerShell 3.0 ile başlayarak, onu açıkça içeri aktaran gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8da19-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="8da19-141">Bir kullanıcı, bir işlevi çağırdığında, modülü otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8da19-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="8da19-142">Modül yolu hakkında daha fazla bilgi için bkz. [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md) ve [PSModulePath ortam değişkeni](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="8da19-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="8da19-143">Bir modül etkin hizmetten kaldırmak için çağrı yapmak [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="8da19-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="8da19-144">Unutmayın [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) modülünüzde kaldırır etkin bellekten - bu aslında onu Modülü dosyaları kaydettiğiniz silmez.</span><span class="sxs-lookup"><span data-stu-id="8da19-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="8da19-145">Show-Takvim kod örneği</span><span class="sxs-lookup"><span data-stu-id="8da19-145">Show-Calendar code example</span></span>

<span data-ttu-id="8da19-146">Aşağıdaki örnekte adlı tek bir işlev içeren bir basit betik modüldür `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="8da19-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="8da19-147">Bu işlev, bir takvim görsel bir temsilini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8da19-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="8da19-148">Ayrıca, örnek doğrulanır, açıklama, parametre değerleri ve örnek için PowerShell Yardım dizelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8da19-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="8da19-149">Son kod satırının, güvence altına `Show-Calendar` modülü içeri aktarıldığında işlevi modülü üye olarak aktarılır.</span><span class="sxs-lookup"><span data-stu-id="8da19-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
