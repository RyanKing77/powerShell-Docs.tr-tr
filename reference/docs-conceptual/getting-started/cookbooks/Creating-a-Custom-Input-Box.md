---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Özel bir giriş kutusu oluşturma"
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 94172102fb81a9b31b7e84188f3e60a372e9cba2
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-custom-input-box"></a>Özel bir giriş kutusu oluşturma
Windows PowerShell 3.0 ve sonraki sürümlerinde Microsoft .NET Framework form oluşturma özellikleri kullanılarak bir grafik özel giriş kutusu komut dosyası.

## <a name="create-a-custom-graphical-input-box"></a>Grafik, özel bir giriş kutusu oluşturma
Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**. .NET Framework sınıfının yeni bir örneğini sonra Başlat **System.Windows.Forms.Form'dan**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.

```
$form = New-Object System.Windows.Forms.Form
```

Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.

- **Metin.** Bu, pencere başlığı olur.

- **Boyutu.** Piksel cinsinden formun boyutudur. Önceki komut 300 piksel genişliğinde 200 piksel uzunluğunda olan bir form oluşturur.

- **StartingPosition.** Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut. Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer. Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Ardından, oluşturun bir **Tamam** formunuz için düğmesi. Boyut ve davranışını belirtin **Tamam** düğmesi. Bu örnekte, düğme formun üst köşeden 120 piksel ve sol kenarından 75 piksel konumdur. Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir. Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi. **İptal** üstten 120 piksel ancak penceresinin sol kenarından 150 piksel düğme vardır.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ardından, etiket metnini sağlamak için kullanıcıların istediğiniz bilgileri açıklayan pencerenizi üzerinde sağlar.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

Etiket metinde açıklanan bilgiler sağlayan kullanıcıların sağlayan denetimi (Bu durumda, bir metin kutusunda) ekleyin. Metin kutuları yanı sıra uygulayabilirsiniz birçok denetimleri vardır; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) konusuna bakın.

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

Ayarlama **Topmost** özelliğine **$True** diğer pencereler ve iletişim kutuları üzerinde penceresini zorlamak için.

```
$form.Topmost = $True
```

Ardından, bu formun etkinleştirmek için kod satırını ekleyin ve oluşturduğunuz metin kutusu odağı ayarlayın.

```
$form.Add_Shown({$textBox.Select()})
```

Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.

```
$result = $form.ShowDialog()
```

Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları metin kutusundaki sağlayın ve ardından sonra ne formla **Tamam** düğmesini veya tuşuna **Enter** anahtar.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Ayrıca bkz:
- [Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt'ın WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Haftanın Windows PowerShell İpucu: giriş kutusunu özel oluşturma](http://technet.microsoft.com/library/ff730941.aspx)

