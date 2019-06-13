---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Birden Çok Seçim Liste Kutusu
ms.openlocfilehash: dcfa43ac8e7cc4ba6147f71791edbf7989af3583
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030103"
---
# <a name="multiple-selection-list-boxes"></a>Birden çok seçim liste kutuları

Windows PowerShell 3.0 ve sonraki sürümleri, özel bir Windows formunda birden çok seçim liste kutusu denetimi oluşturmak için kullanın.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Çoklu seçime izin ver kutusunu denetimleri listesi oluşturma

Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**. Ardından yeni bir .NET Framework sınıfı örneğini Başlat **System.Windows.Forms.Form'dan**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.

- **Metin.** Bu pencerenin başlığı olur.

- **Boyutu.** Formun piksel cinsinden boyutu budur. Önceki komut, 300 piksel genişliğinde ve 200 piksel yüksekliğinde bir formu oluşturur.

- **Başlangıçkonumu.** Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut. Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer. Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğmeyi formun üst kenarından 120 piksel ve sol kenarından 75 piksel konumdur. Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir. Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi. **İptal** düğmesidir üst 120 piksel, ancak pencerenin sol kenardan 150 piksel.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ardından, etiket metnini sağlamak üzere kullanıcıları istediğiniz bilgileri tanımlar, penceresinde sağlar.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Kullanıcıların, etiket metinde açıklanan bilgileri sağlayan olanak sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin. Yanı sıra metin kutuları uygulayabileceğiniz birçok diğer denetimler bulunur; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) MSDN'de.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

İşte nasıl listeden birden çok değer seçmek kullanıcılara izin vermek istediğiniz belirtin.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

Sonraki bölümde, kullanıcılara görüntülenecek liste kutusu istediğiniz değerleri belirtin.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

Liste kutusu denetimini maksimum yüksekliğini belirtin.

```powershell
$listBox.Height = 70
```

Liste kutusu denetimini formunuza eklemek ve diğer pencereler ve iletişim kutuları üzerine formu açıldığında açmak için Windows isteyin.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.

```powershell
$result = $form.ShowDialog()
```

Son olarak, kod içinde **varsa** blok bildirir Windows formu, kullanıcıların bir veya daha fazla seçenekleri kümesinden liste kutusunu seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **girin**  anahtarı.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu:  Birden çok seçim liste kutuları - ve daha fazlası!](https://technet.microsoft.com/library/ff730950.aspx)
