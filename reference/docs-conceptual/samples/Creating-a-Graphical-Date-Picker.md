---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Grafik Tarih Seçici Oluşturma
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405677"
---
# <a name="creating-a-graphical-date-picker"></a>Grafik Tarih Seçici Oluşturma

Ayın gününü seçebilmelerini sağlayan bir grafik, Takvim stil denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümleri kullanın.

## <a name="create-a-graphical-date-picker-control"></a>Grafik tarih seçici denetimi oluşturma

Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.

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

İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**. Ardından yeni bir .NET Framework sınıfı örneğini Başlat **Windows.Forms.Form**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.

```powershell
$form = New-Object Windows.Forms.Form
```

Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.

- **Metin.** Bu pencerenin başlığı olur.

- **Boyutu.** Formun piksel cinsinden boyutu budur. Önceki komut 243 piksel genişliğinde ve 230 piksel yüksekliğinde bir formu oluşturur.

- **Başlangıçkonumu.** Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut. Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer. Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Ardından, oluşturma ve formunuza bir Takvim denetimi ekleyin. Bu örnekte, geçerli gün vurgulanmış daire içinde veya desteklenmez. Kullanıcılar yalnızca bir gününü Takvim üzerinde aynı anda seçebilirsiniz.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğmeyi formun üst kenarından 165 piksel ve sol kenarından 38 piksel konumdur. Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir. Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi. **İptal** düğmesidir üst 165 piksel, ancak pencerenin sol kenardan 113 piksel.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ayarlama **en üstteki** özelliğini **$true** diğer pencereler ve iletişim kutuları penceresini zorlama.

```powershell
$form.Topmost = $true
```

Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.

```powershell
$result = $form.ShowDialog()
```

Son olarak, kod içinde **varsa** blok bildirir Windows form ile kullanıcılar, bir takvim günü seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter** anahtarı. Windows PowerShell, kullanıcılara seçilen tarihi görüntüler.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu:  Grafik Tarih Seçici oluşturma](https://technet.microsoft.com/library/ff730942.aspx)