---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Grafik Tarih Seçici Oluşturma
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058616"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="65cad-103">Grafik Tarih Seçici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65cad-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="65cad-104">Ayın gününü seçebilmelerini sağlayan bir grafik, Takvim stil denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="65cad-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="65cad-105">Grafik tarih seçici denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="65cad-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="65cad-106">Kopyalayın ve ardından aşağıdaki Windows PowerShell ISE'ye yapıştırın ve bir Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="65cad-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="65cad-107">İki .NET Framework sınıfları yükleyerek komut başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="65cad-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="65cad-108">Ardından yeni bir .NET Framework sınıfı örneğini Başlat **Windows.Forms.Form**; sağlayan boş bir form veya denetimleri için başlangıç ekleme penceresi.</span><span class="sxs-lookup"><span data-stu-id="65cad-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="65cad-109">Bu örnekte, kullanarak bu sınıfın dört özellikleri için değerleri atar **özelliği** özelliği ve karma tablo.</span><span class="sxs-lookup"><span data-stu-id="65cad-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="65cad-110">**StartPosition**: Bu özellik eklemezseniz, Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="65cad-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="65cad-111">Bu özellik ayarlayarak **CenterScreen**, otomatik olarak formun ekranın ortasında her yüklenişinde görüntülediğinizden.</span><span class="sxs-lookup"><span data-stu-id="65cad-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="65cad-112">**Boyutu**: Formun piksel cinsinden boyutu budur.</span><span class="sxs-lookup"><span data-stu-id="65cad-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="65cad-113">Önceki komut 243 piksel genişliğinde ve 230 piksel yüksekliğinde bir formu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65cad-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="65cad-114">**Metin**: Bu pencerenin başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="65cad-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="65cad-115">**En üstteki**: Bu özellik ayarlayarak `$true`, diğer pencereler ve iletişim kutuları penceresini zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65cad-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="65cad-116">Ardından, oluşturma ve formunuza bir Takvim denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65cad-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="65cad-117">Bu örnekte, geçerli gün vurgulanmış daire içinde veya desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="65cad-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="65cad-118">Kullanıcılar yalnızca bir gününü Takvim üzerinde aynı anda seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65cad-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="65cad-119">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="65cad-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="65cad-120">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="65cad-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="65cad-121">Bu örnekte, düğmeyi formun üst kenarından 165 piksel ve sol kenarından 38 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="65cad-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="65cad-122">Düğme yüksekliği 23 piksel açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="65cad-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="65cad-123">Betik önceden tanımlanmış bir Windows Forms türleri düğmesi davranışlarını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="65cad-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="65cad-124">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="65cad-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="65cad-125">**İptal** düğmesidir üst 165 piksel, ancak pencerenin sol kenardan 113 piksel.</span><span class="sxs-lookup"><span data-stu-id="65cad-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="65cad-126">Kod içinde Windows formu görüntülemek için aşağıdaki satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="65cad-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="65cad-127">Son olarak, kod içinde `if` blok bildirir Windows form ile kullanıcılar, bir takvim günü seçin ve ardından sonra yapmanız gerekenler **Tamam** düğme veya basın **Enter** anahtarı.</span><span class="sxs-lookup"><span data-stu-id="65cad-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="65cad-128">Windows PowerShell, kullanıcılara seçilen tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="65cad-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="65cad-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="65cad-129">See Also</span></span>

- [<span data-ttu-id="65cad-130">Hey betik yazarı:  Bu PowerShell GUI örnekler neden çalışmıyor?</span><span class="sxs-lookup"><span data-stu-id="65cad-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="65cad-131">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="65cad-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="65cad-132">Haftanın Windows PowerShell İpucu:  Grafik Tarih Seçici oluşturma</span><span class="sxs-lookup"><span data-stu-id="65cad-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)