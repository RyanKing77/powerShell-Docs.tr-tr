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
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848919"
---
# <a name="how-to-write-a-powershell-script-module"></a>PowerShell Betik Modülü Yazma

Betik modülündeki bir .psm1 uzantısında kaydedilen aslında herhangi geçerli PowerShell Betiği verilmiştir. Bu uzantı, onedrive'daki dosyanızda çok sayıda kural ve cmdlet'lerini kullanmak PowerShell altyapısı sağlar. Kodunuzun diğer sistemlerde yanı sıra kapsamı yönetme yüklemenize yardımcı olması için bu özelliklerin çoğu vardır. Ayrıca, daha karmaşık yüklemeleri ve çözümleri açıklamak bir modül bildirim dosyası kullanabilirsiniz.

## <a name="writing-a-powershell-script-module"></a>Modul Skriptu Powershellu yazma

Geçerli bir PowerShell Betiği, bir .psm1 dosyasına kaydetme ve ardından bu dosyayı PowerShell bulabileceğiniz bir yerde bulunan bir dizinde kaydederek bir betik modülüne oluşturun. Ayrıca, betiğinizi çalıştırmak için ihtiyacınız olan tüm kaynakları yerleştirebilirsiniz bu klasörde yanı sıra bir bildirim dosyası, PowerShell modülünüzde nasıl çalıştığını açıklar.

#### <a name="to-create-a-basic-powershell-module"></a>Temel bir PowerShell modülü oluşturmak için

1. Varolan bir PowerShell komut dosyasını alın ve komut dosyasını bir .psm1 uzantısıyla kaydedin.

   Bir komut dosyasıyla .psm1 kaydetme uzantısı anlamına gelir modülü cmdlet'lerini aşağıdaki gibi kullanabilirsiniz [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), onunla ilgili. Öncelikle kolayca içeri aktarabilir ve kodunuzun diğer kullanıcının sistemlerine dışarı aktarmak için bu cmdlet'ler mevcut. (Alternatif bir çözüm diğer sistemler ve ardından nokta kaynak kodunuzu özellikle ölçeklenebilir bir çözüm değilse, etkin belleğe yüklemek olacaktır.) Daha fazla bilgi için **modülü cmdlet'lerini ve değişkenleri** konusundaki [Windows PowerShell modülleri](./understanding-a-windows-powershell-module.md) varsayılan olarak, komut dosyanızdaki tüm İşlevler, bir .psm1 alma kullanıcılar için erişilebilir olacağını unutmayın. Dosya, ancak özellikleri sağlamaz.

   Bu konunun sonunda show-Takvim başlıklı bir örnek PowerShell Betiği, kullanılabilir.

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

2. Kullanıcı erişimi belirli işlevleri ve özellikleri denetlemek istiyorsanız, çağrı [dışarı aktarma ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) betiğinizi sonunda.

   Sayfanın alt kısmındaki örnek kod eline, varsayılan olarak yalnızca tek bir işlevi vardır. Ancak, açıkça göstermek için aşağıdaki kodda açıklandığı şekilde istediğiniz hangi işlevleri kullanıma çağırmanızı önerilir:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Ayrıca, ne bir modül bildirimi kullanılarak alınır kısıtlayabilirsiniz. Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md) ve [bildirim PowerShell modülü yazma](./how-to-write-a-powershell-module-manifest.md).

3. Kendi modülünüzü yüklü gereken modülleri varsa, bunları bir çağrı ile kullanabileceğiniz `Import-Module`, kendi modülünüzü üstünde.

   `Import-Module` bir sistemin hedeflenen bir modülü içe aktaran bir cmdlet olur. Bu nedenle, bu da yordamdaki sonraki bir zamanda de kendi modülünü yüklemek için kullanılır. Bu sayfanın sonundaki örnek kodu alma modüllerin kullanmaz. Ancak olsaydı, dosyasının en üstüne aşağıdaki kodu açıklandığı listelenir:

   ```powershell
   Import-Module GenericModule
   ```

4. Modülünüzün PowerShell Yardım sistemine tanımlamak istiyorsanız, dosya içinde standart Yardım yorumlarla veya ek Yardım dosyası ile bunu yapabilirsiniz.

   Kod örneği, bu konunun altındaki yorumlar bölümünde Yardım bilgilerini içerir. Bu nedenle tercih ederseniz, Ek Yardım içeriğini içeren genişletilmiş XML dosyaları da yazabilirsiniz. Daha fazla bilgi için [yazma yardımcı olmak için Windows PowerShell modülleri](./writing-help-for-windows-powershell-modules.md).

5. Ek modüller, XML dosyaları ya da modülünüzde ile paket istediğiniz diğer içerik varsa, bir modül bildirimi ile bunu yapabilirsiniz.

   Bir modül bildirimi diğer modüller, dizin düzenleri, sürüm numaralarını, veri yazar ve diğer bilgilere adlarını içeren bir dosyadır. PowerShell modülü bildirim dosyasını düzenlemek ve çözümünüzü dağıtmak için kullanır. Ancak, bu örnekte görece basit yapısı nedeniyle, bir bildirim dosyası gerekli değildir. Daha fazla bilgi için [modülü bildirimlerini](./how-to-write-a-powershell-module-manifest.md).

6. Yükleme ve modülünüzde çalıştırmak için uygun PowerShell yollardan biri modülü kaydedin ve çağrı yapmak `Import-Module`.

   Modülünüzün yükleyebileceğiniz yolları bulunur `$env:PSModulePath` genel değişkeni. Örneğin, bir sistemde bir modüle kaydetmek için yaygın bir yolu olabilir `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Yalnızca tek bir .psm1 dosya olsa bile, modülü, mevcut bir klasör oluşturmayı unutmayın. Modülünüzde bu yollardan birine kaydetmediyseniz, modülünüzde çağrısında konumunu geçirin gerekirdi `Import-Module`. (Aksi halde, PowerShell bulmak mümkün olmazdı.) PowerShell modülü yollardan birinde modülünüzde yerleştirdiyseniz, PowerShell 3.0 ile başlayarak, onu açıkça içeri aktaran gerekmez: işlevinize çağrı bir kullanıcı yalnızca sahip otomatik olarak yükler. Modül yolu hakkında daha fazla bilgi için bkz. [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md) ve [PSModulePath ortam değişkeni](./modifying-the-psmodulepath-installation-path.md).

7. Bir modül etkin hizmetten kaldırmak için çağrı yapmak [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Unutmayın [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) modülünüzde kaldırır etkin bellekten - bu aslında onu Modülü dosyaları kaydettiğiniz silmez.

### <a name="show-calendar-code-example"></a>Show-Takvim kod örneği

Aşağıdaki örnek Show-Takvim adlı tek bir işlevi içeren basit bir komut dosyası bir modüldür. Bu işlev, bir takvim görsel bir temsilini görüntüler. Ayrıca, örnek doğrulanır, açıklama, parametre değerleri ve örnek için PowerShell Yardım dizelerini içerir. Son kod satırının, modülü içeri aktarıldığında, Show-Takvim işlev modülü üye olarak dışarı aktarılacak olduğuna dikkat edin.

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
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
