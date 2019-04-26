---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Grafik Tarih Seçici Oluşturma
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058616"
---
# <a name="creating-a-graphical-date-picker"></a>Grafik Tarih Seçici Oluşturma

Ayın gününü seçebilmelerini sağlayan bir grafik, Takvim stil denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümleri kullanın.

## <a name="create-a-graphical-date-picker-control"></a>Grafik tarih seçici denetimi oluşturma

Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.
Ardından yeni bir .NET Framework sınıfı örneğini Başlat **Windows.Forms.Form**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

Bu örnekte, kullanarak bu sınıfın dört özellikleri için değerleri atar **özelliği** özelliği ve karma tablo.

1. **StartPosition**: Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.
   Bu özellik ayarlayarak **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.

2. **Boyutu**: Formun piksel cinsinden boyutu budur.
   Önceki komut 243 piksel genişliğinde ve 230 piksel yüksekliğinde bir formu oluşturur.

3. **Metin**: Bu pencerenin başlığı olur.

4. **En üstteki**: Bu özellik ayarlayarak `$true`, diğer pencereler ve iletişim kutuları penceresini zorlayabilirsiniz.

Ardından, oluşturma ve formunuza bir Takvim denetimi ekleyin.
Bu örnekte, geçerli gün vurgulanmış daire içinde veya desteklenmez.
Kullanıcılar yalnızca bir gününü Takvim üzerinde aynı anda seçebilirsiniz.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi.
Boyut ve davranışını belirtin **Tamam** düğmesi.
Bu örnekte, düğmeyi formun üst kenarından 165 piksel ve sol kenarından 38 piksel konumdur.
Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.
Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.
**İptal** düğmesidir üst 165 piksel, ancak pencerenin sol kenardan 113 piksel.

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.

```powershell
$result = $form.ShowDialog()
```

Son olarak, kod içinde `if` blok bildirir Windows form ile kullanıcılar, bir takvim günü seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter** anahtarı.
Windows PowerShell, kullanıcılara seçilen tarihi görüntüler.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu:  Grafik Tarih Seçici oluşturma](https://technet.microsoft.com/library/ff730942.aspx)