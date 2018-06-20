---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Grafik Tarih Seçici Oluşturma
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954849"
---
# <a name="creating-a-graphical-date-picker"></a>Grafik Tarih Seçici Oluşturma

Ayın gününü kullanıcıların seçmesine izin veren bir grafik, Takvim stili denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümlerinde kullanın.

## <a name="create-a-graphical-date-picker-control"></a>Bir grafik tarih seçici denetim oluşturma

Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**. .NET Framework sınıfının yeni bir örneğini sonra Başlat **Windows.Forms.Form**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.

```powershell
$form = New-Object Windows.Forms.Form
```

Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.

- **metin.** Bu, pencere başlığı olur.

- **Boyutu.** Piksel cinsinden formun boyutudur. Önceki komut 243 piksel genişliğinde 230 piksel uzunluğunda olan bir form oluşturur.

- **StartingPosition.** Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut. Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer. Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Ardından, oluşturun ve ardından bir Takvim denetimi formunuzda ekleyin. Bu örnekte, geçerli gün vurgulanmış yuvarlak içine alınmıştır veya değil. Kullanıcıların yalnızca bir gününü takvimde bir kerede seçebilirsiniz.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğme formun üst köşeden 165 piksel ve sol kenarından 38 piksel konumdur. Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir. Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi. **İptal** üstten 165 piksel ancak penceresinin sol kenarından 113 piksel düğme vardır.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ayarlama **Topmost** özelliğine **$true** diğer pencereler ve iletişim kutuları üzerinde penceresini zorlamak için.

```powershell
$form.Topmost = $true
```

Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.

```powershell
$result = $form.ShowDialog()
```

Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları takvim günü seçin ve ardından sonra ne formla **Tamam** düğmesini veya tuşuna **Enter** anahtar. Windows PowerShell kullanıcıları için seçilen tarihi görüntüler.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu: bir grafik tarih seçici oluşturma](http://technet.microsoft.com/library/ff730942.aspx)