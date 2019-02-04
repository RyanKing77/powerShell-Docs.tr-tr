---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Bir Liste Kutusundan Öğe Seçme
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688500"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="3c888-103">Bir Liste Kutusundan Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="3c888-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="3c888-104">Windows PowerShell 3.0 ve sonraki sürümleri, kullanıcıların bir liste kutusu denetimi öğeleri seçin sağlayan bir iletişim kutusu oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c888-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="3c888-105">Liste kutusu denetimi oluşturun ve öğeleri seçin</span><span class="sxs-lookup"><span data-stu-id="3c888-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="3c888-106">Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3c888-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="3c888-107">İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="3c888-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="3c888-108">Ardından yeni bir .NET Framework sınıfı örneğini Başlat **System.Windows.Forms.Form'dan**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.</span><span class="sxs-lookup"><span data-stu-id="3c888-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="3c888-109">Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="3c888-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="3c888-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="3c888-110">**Text.**</span></span> <span data-ttu-id="3c888-111">Bu pencerenin başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="3c888-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="3c888-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="3c888-112">**Size.**</span></span> <span data-ttu-id="3c888-113">Formun piksel cinsinden boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="3c888-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="3c888-114">Önceki komut, 300 piksel genişliğinde ve 200 piksel yüksekliğinde bir formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c888-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="3c888-115">**Başlangıçkonumu.**</span><span class="sxs-lookup"><span data-stu-id="3c888-115">**StartingPosition.**</span></span> <span data-ttu-id="3c888-116">Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut.</span><span class="sxs-lookup"><span data-stu-id="3c888-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="3c888-117">Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="3c888-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="3c888-118">Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.</span><span class="sxs-lookup"><span data-stu-id="3c888-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="3c888-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3c888-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="3c888-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3c888-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="3c888-121">Bu örnekte, düğmeyi formun üst kenarından 120 piksel ve sol kenarından 75 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="3c888-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="3c888-122">Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="3c888-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="3c888-123">Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c888-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="3c888-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3c888-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="3c888-125">**İptal** düğmesidir üst 120 piksel, ancak pencerenin sol kenardan 150 piksel.</span><span class="sxs-lookup"><span data-stu-id="3c888-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="3c888-126">Ardından, etiket metnini sağlamak üzere kullanıcıları istediğiniz bilgileri tanımlar, penceresinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c888-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="3c888-127">Bu durumda, bir bilgisayar seçin seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="3c888-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="3c888-128">Kullanıcıların, etiket metinde açıklanan bilgileri sağlayan olanak sağlayan denetimi (Bu durumda, bir liste kutusunda) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c888-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="3c888-129">Liste kutuları yanı sıra uygulayabilirsiniz birçok diğer denetimler bulunur; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) MSDN'de.</span><span class="sxs-lookup"><span data-stu-id="3c888-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="3c888-130">Sonraki bölümde, kullanıcılara görüntülenecek liste kutusu istediğiniz değerleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="3c888-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="3c888-131">Bu betiği tarafından oluşturulan liste kutusu tek seçim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c888-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="3c888-132">Çoklu seçime izin veren bir liste kutusu denetimi oluşturmak için bir değer belirtin. **SelectionMode** aşağıdakine benzer şekilde, özellik: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="3c888-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="3c888-133">Daha fazla bilgi için [birden çok seçim liste kutusu](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="3c888-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="3c888-134">Liste kutusu denetimini formunuza eklemek ve diğer pencereler ve iletişim kutuları üzerine formu açıldığında açmak için Windows isteyin.</span><span class="sxs-lookup"><span data-stu-id="3c888-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="3c888-135">Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3c888-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="3c888-136">Son olarak, kod içinde **varsa** blok bildirir Windows form ile kullanıcılar liste kutusundan bir seçenek belirleyin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter**anahtarı.</span><span class="sxs-lookup"><span data-stu-id="3c888-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="3c888-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3c888-137">See Also</span></span>

- [<span data-ttu-id="3c888-138">Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?</span><span class="sxs-lookup"><span data-stu-id="3c888-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="3c888-139">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="3c888-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="3c888-140">Haftanın Windows PowerShell İpucu:  Bir liste kutusundan öğe seçme</span><span class="sxs-lookup"><span data-stu-id="3c888-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](https://technet.microsoft.com/library/ff730949.aspx)