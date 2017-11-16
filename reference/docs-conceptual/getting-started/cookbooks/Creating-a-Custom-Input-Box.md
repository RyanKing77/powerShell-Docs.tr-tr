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
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="0c7a5-103">Özel bir giriş kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c7a5-103">Creating a Custom Input Box</span></span>
<span data-ttu-id="0c7a5-104">Windows PowerShell 3.0 ve sonraki sürümlerinde Microsoft .NET Framework form oluşturma özellikleri kullanılarak bir grafik özel giriş kutusu komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="0c7a5-105">Grafik, özel bir giriş kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c7a5-105">Create a custom, graphical input box</span></span>
<span data-ttu-id="0c7a5-106">Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="0c7a5-107">İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="0c7a5-108">.NET Framework sınıfının yeni bir örneğini sonra Başlat **System.Windows.Forms.Form'dan**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="0c7a5-109">Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="0c7a5-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="0c7a5-110">**Text.**</span></span> <span data-ttu-id="0c7a5-111">Bu, pencere başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="0c7a5-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="0c7a5-112">**Size.**</span></span> <span data-ttu-id="0c7a5-113">Piksel cinsinden formun boyutudur.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="0c7a5-114">Önceki komut 300 piksel genişliğinde 200 piksel uzunluğunda olan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="0c7a5-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="0c7a5-115">**StartingPosition.**</span></span> <span data-ttu-id="0c7a5-116">Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="0c7a5-117">Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="0c7a5-118">Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="0c7a5-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="0c7a5-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="0c7a5-121">Bu örnekte, düğme formun üst köşeden 120 piksel ve sol kenarından 75 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="0c7a5-122">Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="0c7a5-123">Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="0c7a5-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="0c7a5-125">**İptal** üstten 120 piksel ancak penceresinin sol kenarından 150 piksel düğme vardır.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="0c7a5-126">Ardından, etiket metnini sağlamak için kullanıcıların istediğiniz bilgileri açıklayan pencerenizi üzerinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

<span data-ttu-id="0c7a5-127">Etiket metinde açıklanan bilgiler sağlayan kullanıcıların sağlayan denetimi (Bu durumda, bir metin kutusunda) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="0c7a5-128">Metin kutuları yanı sıra uygulayabilirsiniz birçok denetimleri vardır; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

<span data-ttu-id="0c7a5-129">Ayarlama **Topmost** özelliğine **$True** diğer pencereler ve iletişim kutuları üzerinde penceresini zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="0c7a5-130">Ardından, bu formun etkinleştirmek için kod satırını ekleyin ve oluşturduğunuz metin kutusu odağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="0c7a5-131">Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-131">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="0c7a5-132">Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları metin kutusundaki sağlayın ve ardından sonra ne formla **Tamam** düğmesini veya tuşuna **Enter** anahtar.</span><span class="sxs-lookup"><span data-stu-id="0c7a5-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="0c7a5-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0c7a5-133">See Also</span></span>
- [<span data-ttu-id="0c7a5-134">Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?</span><span class="sxs-lookup"><span data-stu-id="0c7a5-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="0c7a5-135">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="0c7a5-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="0c7a5-136">Haftanın Windows PowerShell İpucu: giriş kutusunu özel oluşturma</span><span class="sxs-lookup"><span data-stu-id="0c7a5-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)

