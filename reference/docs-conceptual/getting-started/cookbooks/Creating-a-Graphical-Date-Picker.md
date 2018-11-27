---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Grafik Tarih Seçici Oluşturma
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320338"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="87b03-103">Grafik Tarih Seçici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b03-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="87b03-104">Ayın gününü seçebilmelerini sağlayan bir grafik, Takvim stil denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="87b03-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="87b03-105">Grafik tarih seçici denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b03-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="87b03-106">Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="87b03-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="87b03-107">İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="87b03-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="87b03-108">Ardından yeni bir .NET Framework sınıfı örneğini Başlat **Windows.Forms.Form**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.</span><span class="sxs-lookup"><span data-stu-id="87b03-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="87b03-109">Form sınıfının bir örneğini oluşturduktan sonra bu sınıfın üç özelliğe değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="87b03-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="87b03-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="87b03-110">**Text.**</span></span> <span data-ttu-id="87b03-111">Bu pencerenin başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="87b03-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="87b03-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="87b03-112">**Size.**</span></span> <span data-ttu-id="87b03-113">Formun piksel cinsinden boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="87b03-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="87b03-114">Önceki komut 243 piksel genişliğinde ve 230 piksel yüksekliğinde bir formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87b03-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="87b03-115">**Başlangıçkonumu.**</span><span class="sxs-lookup"><span data-stu-id="87b03-115">**StartingPosition.**</span></span> <span data-ttu-id="87b03-116">Bu isteğe bağlı bir özellik kümesine **CenterScreen** önceki komut.</span><span class="sxs-lookup"><span data-stu-id="87b03-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="87b03-117">Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="87b03-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="87b03-118">Ayarlayarak **Başlangıçkonumu** için **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.</span><span class="sxs-lookup"><span data-stu-id="87b03-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="87b03-119">Ardından, oluşturma ve formunuza bir Takvim denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87b03-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="87b03-120">Bu örnekte, geçerli gün vurgulanmış daire içinde veya desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="87b03-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="87b03-121">Kullanıcılar yalnızca bir gününü Takvim üzerinde aynı anda seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87b03-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="87b03-122">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="87b03-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="87b03-123">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="87b03-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="87b03-124">Bu örnekte, düğmeyi formun üst kenarından 165 piksel ve sol kenarından 38 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="87b03-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="87b03-125">Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="87b03-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="87b03-126">Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="87b03-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="87b03-127">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="87b03-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="87b03-128">**İptal** düğmesidir üst 165 piksel, ancak pencerenin sol kenardan 113 piksel.</span><span class="sxs-lookup"><span data-stu-id="87b03-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="87b03-129">Ayarlama **en üstteki** özelliğini **$true** diğer pencereler ve iletişim kutuları penceresini zorlama.</span><span class="sxs-lookup"><span data-stu-id="87b03-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="87b03-130">Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87b03-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="87b03-131">Son olarak, kod içinde **varsa** blok bildirir Windows form ile kullanıcılar, bir takvim günü seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="87b03-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="87b03-132">Windows PowerShell, kullanıcılara seçilen tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="87b03-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="87b03-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="87b03-133">See Also</span></span>

- [<span data-ttu-id="87b03-134">Hey Scripting Guy: neden bu PowerShell GUI örnekler çalışmıyor?</span><span class="sxs-lookup"><span data-stu-id="87b03-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="87b03-135">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="87b03-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="87b03-136">Haftanın Windows PowerShell İpucu: bir grafik tarih seçici oluşturma</span><span class="sxs-lookup"><span data-stu-id="87b03-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)