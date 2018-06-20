---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Birden Çok Seçim Liste Kutusu
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 81708fd5d7204fb7d136e9d8e808303f4d3f4c30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954900"
---
# <a name="multiple-selection-list-boxes"></a>Çoklu seçim liste kutuları

Windows PowerShell 3.0 ve sonraki sürümlerinde özel bir Windows formunda çoklu seçim liste kutusu denetimi oluşturmak için kullanın.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Birden çok seçimin izin kutusu denetimleri listesi oluşturma

Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.

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

İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**. .NET Framework sınıfının yeni bir örneğini sonra Başlat **System.Windows.Forms.Form'dan**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.

- **metin.** Bu, pencere başlığı olur.

- **Boyutu.** Piksel cinsinden formun boyutudur. Önceki komut 300 piksel genişliğinde 200 piksel uzunluğunda olan bir form oluşturur.

- **StartingPosition.** Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut. Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer. Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğme formun üst köşeden 120 piksel ve sol kenarından 75 piksel konumdur. Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir. Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi. **İptal** üstten 120 piksel ancak penceresinin sol kenarından 150 piksel düğme vardır.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ardından, etiket metnini sağlamak için kullanıcıların istediğiniz bilgileri açıklayan pencerenizi üzerinde sağlar.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Etiket metinde açıklanan bilgiler sağlayan kullanıcıların sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin. Metin kutuları yanı sıra uygulayabilirsiniz birçok denetimleri vardır; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) konusuna bakın.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

İşte nasıl birden çok değer listesinden yapmalarına izin vermek istediğinizi belirtin.

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

Liste kutusu denetimi en fazla yüksekliği belirtin.

```powershell
$listBox.Height = 70
```

Liste kutusu denetimini formunuza ekleyin ve diğer windows ve iletişim kutuları üzerinde formu açıldığında açmak için Windows isteyin.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.

```powershell
$result = $form.ShowDialog()
```

Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları liste kutusundan bir veya daha fazla seçenek seçin ve ardından sonra ne formla **Tamam** düğmesini veya tuşlarına basın **girin**  anahtarı.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu: Çoklu seçim liste kutuları - ve daha fazlası!](http://technet.microsoft.com/library/ff730950.aspx)