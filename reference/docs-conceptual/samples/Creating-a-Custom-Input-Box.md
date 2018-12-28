---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Özel bir Giriş Kutusu Oluşturma
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405689"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="b9c75-103">Özel bir Giriş Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9c75-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="b9c75-104">Windows PowerShell 3.0 ve sonraki sürümlerde Microsoft .NET Framework form oluşturma özelliklerini kullanarak grafik özel bir giriş kutusu betiği.</span><span class="sxs-lookup"><span data-stu-id="b9c75-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="b9c75-105">Grafik, özel bir giriş kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9c75-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="b9c75-106">Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b9c75-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="b9c75-107">İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="b9c75-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="b9c75-108">Ardından yeni bir .NET Framework sınıfı örneğini Başlat **System.Windows.Forms.Form'dan**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.</span><span class="sxs-lookup"><span data-stu-id="b9c75-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="b9c75-109">Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="b9c75-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="b9c75-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="b9c75-110">**Text.**</span></span> <span data-ttu-id="b9c75-111">Bu pencerenin başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="b9c75-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="b9c75-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="b9c75-112">**Size.**</span></span> <span data-ttu-id="b9c75-113">Formun piksel cinsinden boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="b9c75-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="b9c75-114">Önceki komut, 300 piksel genişliğinde ve 200 piksel yüksekliğinde bir formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9c75-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="b9c75-115">**Başlangıçkonumu.**</span><span class="sxs-lookup"><span data-stu-id="b9c75-115">**StartingPosition.**</span></span> <span data-ttu-id="b9c75-116">Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut.</span><span class="sxs-lookup"><span data-stu-id="b9c75-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="b9c75-117">Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="b9c75-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="b9c75-118">Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.</span><span class="sxs-lookup"><span data-stu-id="b9c75-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="b9c75-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b9c75-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="b9c75-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b9c75-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="b9c75-121">Bu örnekte, düğmeyi formun üst kenarından 120 piksel ve sol kenarından 75 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="b9c75-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="b9c75-122">Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="b9c75-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="b9c75-123">Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9c75-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="b9c75-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b9c75-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="b9c75-125">**İptal** düğmesidir üst 120 piksel, ancak pencerenin sol kenardan 150 piksel.</span><span class="sxs-lookup"><span data-stu-id="b9c75-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="b9c75-126">Ardından, etiket metnini sağlamak üzere kullanıcıları istediğiniz bilgileri tanımlar, penceresinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9c75-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="b9c75-127">Kullanıcıların, etiket metinde açıklanan bilgileri sağlayan olanak sağlayan denetimi (Bu durumda, bir metin kutusundaki) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b9c75-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="b9c75-128">Yanı sıra metin kutuları uygulayabileceğiniz birçok diğer denetimler bulunur; Daha fazla bilgi için bkz [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) MSDN'de.</span><span class="sxs-lookup"><span data-stu-id="b9c75-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="b9c75-129">Ayarlama **en üstteki** özelliğini **$true** diğer pencereler ve iletişim kutuları penceresini zorlama.</span><span class="sxs-lookup"><span data-stu-id="b9c75-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="b9c75-130">Ardından, bu formun etkinleştirmek için kod satırını ekleyin ve oluşturduğunuz metin kutusu için odağı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b9c75-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="b9c75-131">Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b9c75-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="b9c75-132">Son olarak, kod içinde **varsa** blok bildirir Windows formu, kullanıcıların metin kutusuna metin girin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="b9c75-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="b9c75-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b9c75-133">See Also</span></span>

- [<span data-ttu-id="b9c75-134">Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?</span><span class="sxs-lookup"><span data-stu-id="b9c75-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="b9c75-135">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="b9c75-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="b9c75-136">Haftanın Windows PowerShell İpucu:  Özel bir giriş kutusu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9c75-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)