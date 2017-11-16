---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Grafik Tarih Seçici oluşturma"
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 7be72be7e9732737f00b15b6b2b83adcca4393ae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="1c7dc-103">Grafik Tarih Seçici oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c7dc-103">Creating a Graphical Date Picker</span></span>
<span data-ttu-id="1c7dc-104">Ayın gününü kullanıcıların seçmesine izin veren bir grafik, Takvim stili denetimi ile bir form oluşturmak için Windows PowerShell 3.0 ve sonraki sürümlerinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="1c7dc-105">Bir grafik tarih seçici denetim oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c7dc-105">Create a graphical date-picker control</span></span>
<span data-ttu-id="1c7dc-106">Kopyalayın ve aşağıdaki Windows PowerShell ISE yapıştırın ve sonra Windows PowerShell Betiği (.ps1) kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="1c7dc-107">İki .NET Framework sınıf yükleyerek komut dosyasının başlar: **System.Drawing** ve **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="1c7dc-108">.NET Framework sınıfının yeni bir örneğini sonra Başlat **Windows.Forms.Form**; boş bir form sağlayan veya olduğu başlatabilirsiniz ekleme penceresi denetler.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="1c7dc-109">Form sınıfının bir örneği oluşturduktan sonra bu sınıfın üç özelliklerine değerler atayın.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="1c7dc-110">**Metin.**</span><span class="sxs-lookup"><span data-stu-id="1c7dc-110">**Text.**</span></span> <span data-ttu-id="1c7dc-111">Bu, pencere başlığı olur.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="1c7dc-112">**Boyutu.**</span><span class="sxs-lookup"><span data-stu-id="1c7dc-112">**Size.**</span></span> <span data-ttu-id="1c7dc-113">Piksel cinsinden formun boyutudur.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="1c7dc-114">Önceki komut 243 piksel genişliğinde 230 piksel uzunluğunda olan bir form oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="1c7dc-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="1c7dc-115">**StartingPosition.**</span></span> <span data-ttu-id="1c7dc-116">Bu isteğe bağlı özellik kümesine **CenterScreen** yukarıdaki komut.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="1c7dc-117">Bu özellik eklemezseniz Windows formu açıldığında bir konum seçer.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="1c7dc-118">Ayarlayarak **StartingPosition** için **CenterScreen**, otomatik olarak formun ekran ortasında her yüklenişinde görüntülediğiniz.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="1c7dc-119">Ardından, oluşturun ve ardından bir Takvim denetimi formunuzda ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="1c7dc-120">Bu örnekte, geçerli gün vurgulanmış yuvarlak içine alınmıştır veya değil.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="1c7dc-121">Kullanıcıların yalnızca bir gününü takvimde bir kerede seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-121">Users can select only one day on the calendar at one time.</span></span>

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="1c7dc-122">Ardından, oluşturun bir **Tamam** formunuz için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="1c7dc-123">Boyut ve davranışını belirtin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="1c7dc-124">Bu örnekte, düğme formun üst köşeden 165 piksel ve sol kenarından 38 piksel konumdur.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="1c7dc-125">Düğme yüksekliği 23 piksel cinsinden açıkken düğmesi uzunluğu 75 pikseldir.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="1c7dc-126">Komut dosyasını önceden tanımlanmış Windows Forms türleri düğmesi davranışları belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="1c7dc-127">Benzer şekilde, oluşturduğunuz bir **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="1c7dc-128">**İptal** üstten 165 piksel ancak penceresinin sol kenarından 113 piksel düğme vardır.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="1c7dc-129">Ayarlama **Topmost** özelliğine **$True** diğer pencereler ve iletişim kutuları üzerinde penceresini zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="1c7dc-130">Aşağıdaki Windows formu görüntülemek için kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-130">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="1c7dc-131">Son olarak, içinde kod **varsa** blok bildirir Windows kullanıcıları takvim günü seçin ve ardından sonra ne formla **Tamam** düğmesini veya tuşuna **Enter** anahtar.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="1c7dc-132">Windows PowerShell kullanıcıları için seçilen tarihi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c7dc-132">Windows PowerShell displays the selected date to users.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="1c7dc-133">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1c7dc-133">See Also</span></span>
- [<span data-ttu-id="1c7dc-134">Merhaba Scripting Guy: neden bu PowerShell GUI örnekler çalışmaz?</span><span class="sxs-lookup"><span data-stu-id="1c7dc-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="1c7dc-135">GitHub: Dave Wyatt'ın WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="1c7dc-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="1c7dc-136">Haftanın Windows PowerShell İpucu: bir grafik tarih seçici oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c7dc-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)

