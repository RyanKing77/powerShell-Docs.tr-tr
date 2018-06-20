---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bir Liste Kutusundan Öğe Seçme
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 6ff6bff8f6ce4e9236d7877c4cca24a10932cbe0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951690"
---
# <a name="selecting-items-from-a-list-box"></a>Bir Liste Kutusundan Öğe Seçme

Windows PowerShell 3.0 ve sonraki sürümlerinde öğeleri bir liste kutusu denetimini kullanıcıların seçmesine izin veren bir iletişim kutusu oluşturmak için kullanın.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Liste kutusu denetimi oluşturma ve öğeleri seçin

Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**. .NET Framework sınıfının yeni bir örneğini sonra Başlat **System.Windows.Forms.Form'dan**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.

- **metin.** Bu, pencere başlığı olur.

- **Boyutu.** Piksel cinsinden formun boyutudur. Önceki komut 300 piksel genişliğinde 200 piksel uzunluğunda olan bir form oluşturur.

- **StartingPosition.** Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut. Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer. Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğme formun üst köşeden 120 piksel ve sol kenarından 75 piksel konumdur. Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir. Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
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

Ardından, etiket metnini sağlamak için kullanıcıların istediğiniz bilgileri açıklayan pencerenizi üzerinde sağlar. Bu durumda, bir bilgisayar seçin seçeneğini belirleyin.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Etiket metinde açıklanan bilgiler sağlayan kullanıcıların sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin. Liste kutuları yanı sıra uygulayabilirsiniz birçok denetimleri vardır; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) konusuna bakın.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

Sonraki bölümde, kullanıcılara görüntülenecek liste kutusu istediğiniz değerleri belirtin.

> [!NOTE]
> Bu komut dosyası tarafından oluşturulan liste kutusu yalnızca bir seçilmesine izin verir. Birden çok seçimin sağlayan bir liste kutusu denetimi oluşturmak için bir değer belirtin **SelectionMode** özelliği, aşağıdakine benzer: `$listBox.SelectionMode = 'MultiExtended'`. Daha fazla bilgi için bkz: [çoklu seçim liste kutuları](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
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

Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları liste kutusundan bir seçenek belirleyin ve ardından sonra ne formla **Tamam** düğmesini veya tuşuna **Enter**anahtarı.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Ayrıca bkz:

- [Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu: bir liste kutusundan öğeler seçme](http://technet.microsoft.com/library/ff730949.aspx)