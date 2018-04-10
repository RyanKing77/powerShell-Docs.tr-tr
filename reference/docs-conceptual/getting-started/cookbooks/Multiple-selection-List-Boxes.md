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
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="f2f2b-103">Çoklu seçim liste kutuları</span><span class="sxs-lookup"><span data-stu-id="f2f2b-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="f2f2b-104">Windows PowerShell 3.0 ve sonraki sürümlerinde özel bir Windows formunda çoklu seçim liste kutusu denetimi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="f2f2b-105">Birden çok seçimin izin kutusu denetimleri listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2f2b-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="f2f2b-106">Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="f2f2b-107">İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="f2f2b-108">.NET Framework sınıfının yeni bir örneğini sonra Başlat **System.Windows.Forms.Form'dan**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="f2f2b-109">Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="f2f2b-110">**metin.**</span><span class="sxs-lookup"><span data-stu-id="f2f2b-110">**Text.**</span></span> <span data-ttu-id="f2f2b-111">Bu, pencere başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="f2f2b-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="f2f2b-112">**Size.**</span></span> <span data-ttu-id="f2f2b-113">Piksel cinsinden formun boyutudur.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="f2f2b-114">Önceki komut 300 piksel genişliğinde 200 piksel uzunluğunda olan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="f2f2b-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="f2f2b-115">**StartingPosition.**</span></span> <span data-ttu-id="f2f2b-116">Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="f2f2b-117">Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="f2f2b-118">Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="f2f2b-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="f2f2b-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="f2f2b-121">Bu örnekte, düğme formun üst köşeden 120 piksel ve sol kenarından 75 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="f2f2b-122">Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="f2f2b-123">Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="f2f2b-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="f2f2b-125">**İptal** üstten 120 piksel ancak penceresinin sol kenarından 150 piksel düğme vardır.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="f2f2b-126">Ardından, etiket metnini sağlamak için kullanıcıların istediğiniz bilgileri açıklayan pencerenizi üzerinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="f2f2b-127">Etiket metinde açıklanan bilgiler sağlayan kullanıcıların sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="f2f2b-128">Metin kutuları yanı sıra uygulayabilirsiniz birçok denetimleri vardır; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="f2f2b-129">İşte nasıl birden çok değer listesinden yapmalarına izin vermek istediğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="f2f2b-130">Sonraki bölümde, kullanıcılara görüntülenecek liste kutusu istediğiniz değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="f2f2b-131">Liste kutusu denetimi en fazla yüksekliği belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="f2f2b-132">Liste kutusu denetimini formunuza ekleyin ve diğer windows ve iletişim kutuları üzerinde formu açıldığında açmak için Windows isteyin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="f2f2b-133">Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="f2f2b-134">Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları liste kutusundan bir veya daha fazla seçenek seçin ve ardından sonra ne formla **Tamam** düğmesini veya tuşlarına basın **girin**  anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f2f2b-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="f2f2b-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f2f2b-135">See Also</span></span>

- [<span data-ttu-id="f2f2b-136">Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?</span><span class="sxs-lookup"><span data-stu-id="f2f2b-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="f2f2b-137">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="f2f2b-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="f2f2b-138">Haftanın Windows PowerShell İpucu: Çoklu seçim liste kutuları - ve daha fazlası!</span><span class="sxs-lookup"><span data-stu-id="f2f2b-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](http://technet.microsoft.com/library/ff730950.aspx)