---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Birden Çok Seçim Liste Kutusu
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: a762145dc197ec7e1424b2fbdcef5e7380d13803
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405769"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="bd4bf-103">Birden çok seçim liste kutuları</span><span class="sxs-lookup"><span data-stu-id="bd4bf-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="bd4bf-104">Windows PowerShell 3.0 ve sonraki sürümleri, özel bir Windows formunda birden çok seçim liste kutusu denetimi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="bd4bf-105">Çoklu seçime izin ver kutusunu denetimleri listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bd4bf-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="bd4bf-106">Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="bd4bf-107">İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="bd4bf-108">Ardından yeni bir .NET Framework sınıfı örneğini Başlat **System.Windows.Forms.Form'dan**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="bd4bf-109">Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="bd4bf-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="bd4bf-110">**Text.**</span></span> <span data-ttu-id="bd4bf-111">Bu pencerenin başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="bd4bf-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="bd4bf-112">**Size.**</span></span> <span data-ttu-id="bd4bf-113">Formun piksel cinsinden boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="bd4bf-114">Önceki komut, 300 piksel genişliğinde ve 200 piksel yüksekliğinde bir formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="bd4bf-115">**Başlangıçkonumu.**</span><span class="sxs-lookup"><span data-stu-id="bd4bf-115">**StartingPosition.**</span></span> <span data-ttu-id="bd4bf-116">Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="bd4bf-117">Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="bd4bf-118">Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="bd4bf-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="bd4bf-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="bd4bf-121">Bu örnekte, düğmeyi formun üst kenarından 120 piksel ve sol kenarından 75 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="bd4bf-122">Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="bd4bf-123">Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="bd4bf-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="bd4bf-125">**İptal** düğmesidir üst 120 piksel, ancak pencerenin sol kenardan 150 piksel.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="bd4bf-126">Ardından, etiket metnini sağlamak üzere kullanıcıları istediğiniz bilgileri tanımlar, penceresinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="bd4bf-127">Kullanıcıların, etiket metinde açıklanan bilgileri sağlayan olanak sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="bd4bf-128">Yanı sıra metin kutuları uygulayabileceğiniz birçok diğer denetimler bulunur; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) MSDN'de.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="bd4bf-129">İşte nasıl listeden birden çok değer seçmek kullanıcılara izin vermek istediğiniz belirtin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="bd4bf-130">Sonraki bölümde, kullanıcılara görüntülenecek liste kutusu istediğiniz değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="bd4bf-131">Liste kutusu denetimini maksimum yüksekliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="bd4bf-132">Liste kutusu denetimini formunuza eklemek ve diğer pencereler ve iletişim kutuları üzerine formu açıldığında açmak için Windows isteyin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="bd4bf-133">Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="bd4bf-134">Son olarak, kod içinde **varsa** blok bildirir Windows formu, kullanıcıların bir veya daha fazla seçenekleri kümesinden liste kutusunu seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **girin**  anahtarı.</span><span class="sxs-lookup"><span data-stu-id="bd4bf-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="bd4bf-135">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="bd4bf-135">See Also</span></span>

- [<span data-ttu-id="bd4bf-136">Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?</span><span class="sxs-lookup"><span data-stu-id="bd4bf-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="bd4bf-137">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="bd4bf-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="bd4bf-138">Haftanın Windows PowerShell İpucu:  Birden çok seçim liste kutuları - ve daha fazlası!</span><span class="sxs-lookup"><span data-stu-id="bd4bf-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](https://technet.microsoft.com/library/ff730950.aspx)