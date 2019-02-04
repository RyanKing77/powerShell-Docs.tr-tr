---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Betiklerde Hata Ayıklama
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684580"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="73ced-103">Windows PowerShell ISE’de Betiklerde Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="73ced-103">How to Debug Scripts in Windows PowerShell ISE</span></span>

<span data-ttu-id="73ced-104">Bu makalede, betikleri yerel bir bilgisayardaki Windows PowerShell Tümleşik komut dosyası ortamı (ISE) visual hata ayıklama özelliklerini kullanarak hata ayıklama açıklar.</span><span class="sxs-lookup"><span data-stu-id="73ced-104">This article describes how to debug scripts on a local computer by using the Windows PowerShell Integrated Scripting Environment (ISE) visual debugging features.</span></span>

## <a name="how-to-manage-breakpoints"></a><span data-ttu-id="73ced-105">Kesme noktaları yönetme</span><span class="sxs-lookup"><span data-stu-id="73ced-105">How to manage breakpoints</span></span>

<span data-ttu-id="73ced-106">Bir kesme noktası işlemi değişkenler ve betiğinizi çalıştırıldığı ortamın geçerli durumu inceleyebilirsiniz duraklatmak için istediğiniz bir belirtilen bir betikte yerdir.</span><span class="sxs-lookup"><span data-stu-id="73ced-106">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span> <span data-ttu-id="73ced-107">Betiğinizi bir kesme noktası tarafından duraklatıldı sonra konsol bölmesinde betiğinizi durumunu incelemek için komutları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-107">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span>  <span data-ttu-id="73ced-108">Çıkış değişkenleri veya diğer komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73ced-108">You can output variables or run other commands.</span></span> <span data-ttu-id="73ced-109">Hatta, şu anda çalışan betik bağlamı için görünür olan tüm değişkenler değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-109">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="73ced-110">Görmek istediğiniz inceledikten sonra betiğin devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-110">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="73ced-111">Windows PowerShell hata ayıklama ortamında üç tür kesme noktaları ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="73ced-111">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1. <span data-ttu-id="73ced-112">**Satır kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-112">**Line breakpoint**.</span></span> <span data-ttu-id="73ced-113">Komut dosyası işlemi sırasında belirtilen satırın ulaşıldığında betik duraklatır.</span><span class="sxs-lookup"><span data-stu-id="73ced-113">The script pauses when the designated line is reached during the operation of the script</span></span>

2. <span data-ttu-id="73ced-114">**Değişken kesme noktası.**</span><span class="sxs-lookup"><span data-stu-id="73ced-114">**Variable breakpoint.**</span></span> <span data-ttu-id="73ced-115">Belirtilen değişken değerini değiştiğinde betik duraklatır.</span><span class="sxs-lookup"><span data-stu-id="73ced-115">The script pauses whenever the designated variable's value changes.</span></span>

3. <span data-ttu-id="73ced-116">**Kesme noktası komutu.**</span><span class="sxs-lookup"><span data-stu-id="73ced-116">**Command breakpoint.**</span></span> <span data-ttu-id="73ced-117">Belirtilen komut hakkında komut dosyası işlemi sırasında çalıştırılacak olduğunda betiği duraklatır.</span><span class="sxs-lookup"><span data-stu-id="73ced-117">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="73ced-118">Bu, daha fazla kesme noktası yalnızca, istediğiniz işlemi için filtre uygulamak için parametre içerebilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-118">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="73ced-119">Komut, oluşturduğunuz bir işlev de olabilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-119">The command can also be a function you created.</span></span>

<span data-ttu-id="73ced-120">Bu, Windows PowerShell ISE hata ayıklama ortamında, yalnızca satır kesme noktaları menüsünü veya klavye kısayolları kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-120">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="73ced-121">Diğer iki tür kesme noktaları ayarlayın, ancak ve konsol bölmesinde kullanarak ayarlanırlar [kümesi PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-121">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet.</span></span> <span data-ttu-id="73ced-122">Bu bölümde, nasıl kullanılabiliyorsa menüleri kullanarak Windows PowerShell ISE'de hata ayıklama görevlerini gerçekleştirmek ve komut dosyası kullanarak bir yelpazede komutları ve konsol bölmesinde gerçekleştirmek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73ced-122">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="73ced-123">Bir kesme noktası ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="73ced-123">To set a breakpoint</span></span>

<span data-ttu-id="73ced-124">Yalnızca kaydedildikten sonra bir kesme noktası komut dosyasında ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-124">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="73ced-125">Bir satır kesme noktası ayarlayın ve ardından istediğiniz satıra sağ tıklayın **iki durumlu kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-125">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="73ced-126">Veya bir satır kesme noktası ayarlamak istediğiniz satıra tıklayın ve basın **F9** veya **hata ayıklama** menüsünde tıklayın **iki durumlu kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-126">Or, click the line where you want to set a line breakpoint, and press **F9** or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="73ced-127">Aşağıdaki betik ve konsol bölmesinde kullanarak değişken bir kesme noktası nasıl ayarlayabilirsiniz ilişkin bir örnektir [kümesi PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-127">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.</span></span>

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="73ced-128">Tüm kesme noktalarını listeleyin</span><span class="sxs-lookup"><span data-stu-id="73ced-128">List all breakpoints</span></span>

<span data-ttu-id="73ced-129">Tüm kesme noktalarını, geçerli Windows PowerShell oturumunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73ced-129">Displays all breakpoints in the current Windows PowerShell session.</span></span>

<span data-ttu-id="73ced-130">Üzerinde **hata ayıklama** menüsünde tıklatın **listesi kesme noktaları**.</span><span class="sxs-lookup"><span data-stu-id="73ced-130">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="73ced-131">Aşağıdaki betiği kullanarak tüm kesme noktalarını Konsol bölmesinde nasıl listeleyebilirsiniz ilişkin bir örnektir [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-131">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.</span></span>

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="73ced-132">Bir kesme noktasını Kaldır</span><span class="sxs-lookup"><span data-stu-id="73ced-132">Remove a breakpoint</span></span>

<span data-ttu-id="73ced-133">Bir kesme noktası kaldırma siler.</span><span class="sxs-lookup"><span data-stu-id="73ced-133">Removing a breakpoint deletes it.</span></span>

<span data-ttu-id="73ced-134">Daha sonra yeniden kullanmak için göz önünde bulundurun isteyebilirsiniz düşünüyorsanız [bir kesme noktası devre dışı](#disable-a-breakpoint) , bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="73ced-134">If you think you might want to use it again later, consider [Disable a Breakpoint](#disable-a-breakpoint) it instead.</span></span>
<span data-ttu-id="73ced-135">Bir kesme noktası kaldırın ve ardından istediğiniz satıra sağ tıklayın **iki durumlu kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-135">Right-click the line where you want to remove a breakpoint, and then click **Toggle Breakpoint**.</span></span>
<span data-ttu-id="73ced-136">Veya, bir kesme noktasını kaldırmak istediğiniz satırına tıklayın ve **hata ayıklama** menüsünde tıklayın **iki durumlu kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-136">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span>
<span data-ttu-id="73ced-137">Aşağıdaki betiği kullanarak belirtilen Kimliğe sahip bir kesme noktası konsol bölmesinden kaldırma örneğidir [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-137">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="73ced-138">Tüm kesme noktalarını Kaldır</span><span class="sxs-lookup"><span data-stu-id="73ced-138">Remove All Breakpoints</span></span>

<span data-ttu-id="73ced-139">Geçerli oturumda tanımlanan tüm kesme noktalarını kaldırmak için **hata ayıklama** menüsünü tıklatın **tüm kesme noktalarını Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="73ced-139">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="73ced-140">Aşağıdaki betiği kullanarak tüm kesme noktalarını ve konsol bölmesinde kaldırma örneğidir [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-140">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a><span data-ttu-id="73ced-141">Bir kesme noktası devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="73ced-141">Disable a Breakpoint</span></span>

<span data-ttu-id="73ced-142">Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.</span><span class="sxs-lookup"><span data-stu-id="73ced-142">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="73ced-143">Belirli satıra bir kesme noktasını devre dışı bırakmak için bir kesme noktası devre dışı bırakın ve ardından istediğiniz satıra sağ tıklayın **devre dışı kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-143">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="73ced-144">Ya da bir kesme noktasını devre dışı bırakmak istediğiniz satıra tıklayın ve basın **F9** veya **hata ayıklama** menüsünde tıklayın **devre dışı kesme noktası**.</span><span class="sxs-lookup"><span data-stu-id="73ced-144">Or, click the line where you want to disable a breakpoint, and press **F9** or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="73ced-145">Aşağıdaki betik ve konsol bölmesinde kullanarak belirtilen Kimliğe sahip bir kesme noktası nasıl kaldırabilirsiniz ilişkin bir örnektir [devre dışı bırak PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-145">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="73ced-146">Tüm kesme noktalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="73ced-146">Disable All Breakpoints</span></span>

<span data-ttu-id="73ced-147">Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.</span><span class="sxs-lookup"><span data-stu-id="73ced-147">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="73ced-148">Tüm kesme noktalarını devre dışı geçerli oturum için **hata ayıklama** menüsünde tıklayın **tüm kesme noktalarını devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="73ced-148">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="73ced-149">Aşağıdaki komut dosyasını nasıl, konsol bölmesinde tüm kesme noktalarını kullanarak devre dışı bırakabilirsiniz, bir örnektir [devre dışı bırak PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-149">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="73ced-150">Bir kesme noktasını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="73ced-150">Enable a Breakpoint</span></span>

<span data-ttu-id="73ced-151">Belirli bir kesme noktası etkinleştirmek için bir kesme noktasını etkinleştir ve ardından istediğiniz satıra sağ tıklayın **kesme noktasını etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="73ced-151">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="73ced-152">Ya da bir kesme noktasını etkinleştir ve ENTER tuşuna basın istediğiniz satıra tıklayın **F9** veya **hata ayıklama** menüsünde tıklatın **kesme noktasını etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="73ced-152">Or, click the line where you want to enable a breakpoint, and then press **F9** or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="73ced-153">Aşağıdaki betiği kullanarak belirli kesme noktaları Konsol bölmesinde nasıl olanak sağlayabileceğiniz ilişkin bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-153">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="73ced-154">Tüm kesme noktalarını etkinleştir</span><span class="sxs-lookup"><span data-stu-id="73ced-154">Enable All Breakpoints</span></span>

<span data-ttu-id="73ced-155">Geçerli oturumda tanımlanan tüm kesme noktalarını etkinleştirmek için **hata ayıklama** menüsünü tıklatın **tüm kesme noktalarını etkinleştir**.</span><span class="sxs-lookup"><span data-stu-id="73ced-155">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="73ced-156">Aşağıdaki betiği kullanarak tüm kesme noktalarını Konsol bölmesinde nasıl olanak sağlayabileceğiniz ilişkin bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="73ced-156">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a><span data-ttu-id="73ced-157">Hata ayıklama oturumu yönetme</span><span class="sxs-lookup"><span data-stu-id="73ced-157">How to manage a debugging session</span></span>

<span data-ttu-id="73ced-158">Hata ayıklamaya başlamadan önce bir veya daha fazla kesme noktası ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73ced-158">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="73ced-159">Hata ayıklamak istediğiniz komut kaydedilmezse bir kesme noktası ayarlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="73ced-159">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="73ced-160">Yönleri üzerinde nasıl bir kesme noktası ayarlamak için bkz: [kesme noktaları yönetme](#how-to-manage-breakpoints) veya [kümesi PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint).</span><span class="sxs-lookup"><span data-stu-id="73ced-160">For directions on of how to set a breakpoint, see [How to manage breakpoints](#how-to-manage-breakpoints) or [Set-PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint).</span></span> <span data-ttu-id="73ced-161">Hata ayıklamayı başlattıktan sonra bir komut dosyası hata ayıklamayı durdurmak kadar düzenleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-161">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="73ced-162">Çalıştırmadan önce ayarlanan bir veya daha fazla kesme noktaları olan bir komut dosyası otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-162">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="73ced-163">Hata ayıklamayı başlatmak için</span><span class="sxs-lookup"><span data-stu-id="73ced-163">To start debugging</span></span>

<span data-ttu-id="73ced-164">Tuşuna **F5** veya araç çubuğunda **betiğini Çalıştır** simgesini veya **hata ayıklama** menüsünü tıklatın **Çalıştır/Continue**.</span><span class="sxs-lookup"><span data-stu-id="73ced-164">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="73ced-165">İlk kesme noktasına karşılaşana kadar betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="73ced-165">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="73ced-166">Bu işlemi burada duraklatır ve üzerinde duraklatıldı satırı vurgular.</span><span class="sxs-lookup"><span data-stu-id="73ced-166">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="73ced-167">Hata ayıklamaya devam etmek için</span><span class="sxs-lookup"><span data-stu-id="73ced-167">To continue debugging</span></span>

<span data-ttu-id="73ced-168">Tuşuna **F5** veya araç çubuğunda **betiğini Çalıştır** simgesini veya **hata ayıklama** menüsünde tıklayın **Çalıştır/devam** veya Konsol bölmesinde, yazın **C** ve tuşuna **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-168">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type **C** and then press **ENTER**.</span></span> <span data-ttu-id="73ced-169">Bu, kodun sonraki kesme noktasına veya betiğin sonundaki başka hiçbir kesme noktası karşılaşıldığında çalışmaya devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="73ced-169">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="73ced-170">Çağrı yığınını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="73ced-170">To view the call stack</span></span>

<span data-ttu-id="73ced-171">Betik konumu çalıştırmak geçerli çağrı yığınını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73ced-171">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="73ced-172">Betik farklı bir işlev tarafından çağrılan bir işlevde çalışıyorsa, ardından, ekranda ek satır çıktıda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="73ced-172">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="73ced-173">En alttaki satır özgün komut dosyası ve satır bir işlev çağrıldı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73ced-173">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="73ced-174">Bu işlev ve bunu, başka bir işleve çağrılmış bir satırda sonraki satır gösterileceğini.</span><span class="sxs-lookup"><span data-stu-id="73ced-174">The next line up shows that function and the line in it in which another function might have been called.</span></span>  <span data-ttu-id="73ced-175">En üst satır üzerinde Kesme noktasının ayarlandığını geçerli satırın geçerli bağlam gösterir.</span><span class="sxs-lookup"><span data-stu-id="73ced-175">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="73ced-176">Geçerli çağrı yığınını görmek için duraklatıldığı sırada basın **CTRL + SHIFT + D** veya **hata ayıklama** menüsünde, tıklayın **görünen çağrı yığını** veya Konsol bölmesinde, yazın **K**  ve tuşuna **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-176">While paused, to see the current call stack, press **CTRL+SHIFT+D** or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type **K** and then press **ENTER**.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="73ced-177">Hata ayıklamayı durdurmak için</span><span class="sxs-lookup"><span data-stu-id="73ced-177">To stop debugging</span></span>

<span data-ttu-id="73ced-178">Basın **SHIFT + F5** veya **hata ayıklama** menüsünde, tıklayın **durdurma hata ayıklayıcı**, ya da konsol bölmesinde, yazın **Q** ve tuşuna  **GİRİN**.</span><span class="sxs-lookup"><span data-stu-id="73ced-178">Press **SHIFT-F5** or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type **Q** and then press **ENTER**.</span></span>

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a><span data-ttu-id="73ced-179">Nasıl Atla, adımlama ve hata ayıklama sırasında dışına adımla</span><span class="sxs-lookup"><span data-stu-id="73ced-179">How to step over, step into, and step out while debugging</span></span>

<span data-ttu-id="73ced-180">Adımlama aynı anda çalıştırılan bir deyim işlemidir.</span><span class="sxs-lookup"><span data-stu-id="73ced-180">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="73ced-181">Bir kod satırının durdurun ve değişkenleri ve sistem durumunu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="73ced-181">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="73ced-182">Aşağıdaki tablo üzerinden Adımlama, içine adımlama ve Adımlama gibi yaygın hata ayıklama görevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73ced-182">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="73ced-183">Görev hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="73ced-183">Debugging Task</span></span> | <span data-ttu-id="73ced-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73ced-184">Description</span></span> | <span data-ttu-id="73ced-185">PowerShell ISE'de yerine getirmeyi</span><span class="sxs-lookup"><span data-stu-id="73ced-185">How to accomplish it in PowerShell ISE</span></span> |
| --- | --- | --- |
| <span data-ttu-id="73ced-186">**Adımla**</span><span class="sxs-lookup"><span data-stu-id="73ced-186">**Step Into**</span></span> | <span data-ttu-id="73ced-187">Geçerli deyimi yürütür ve ardından sonraki deyimi durdurur.</span><span class="sxs-lookup"><span data-stu-id="73ced-187">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="73ced-188">Geçerli deyimi bir işlev veya komut dosyası çağrısı, sonra da, işlev veya komut dosyası hata ayıklayıcı adımlamayla ise, aksi halde sonraki deyimi durdurur.</span><span class="sxs-lookup"><span data-stu-id="73ced-188">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span> | <span data-ttu-id="73ced-189">Basın **F11** veya **hata ayıklama** menüsünde, tıklayın **içine adımla**, veya Konsol bölmesinde, **S** basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-189">Press **F11** or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type **S** and press **ENTER**.</span></span> |
| <span data-ttu-id="73ced-190">**Üzerinden adımla**</span><span class="sxs-lookup"><span data-stu-id="73ced-190">**Step Over**</span></span> | <span data-ttu-id="73ced-191">Geçerli deyimi yürütür ve ardından sonraki deyimi durdurur.</span><span class="sxs-lookup"><span data-stu-id="73ced-191">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="73ced-192">Geçerli deyimi ise bir işlev veya betiği çağrı ve hata ayıklayıcı tüm işlev veya betiği çalıştırır ve sonraki deyim işlev çağrısından sonra durakları.</span><span class="sxs-lookup"><span data-stu-id="73ced-192">If the current statement is a function or script call, then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="73ced-193">Basın **F10** veya **hata ayıklama** menüsünde, tıklayın **Step Over**, veya Konsol bölmesinde, **V** basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-193">Press **F10** or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type **V** and press **ENTER**.</span></span> |
| <span data-ttu-id="73ced-194">**Dışına adımla**</span><span class="sxs-lookup"><span data-stu-id="73ced-194">**Step Out**</span></span> | <span data-ttu-id="73ced-195">Geçerli işlev ve işlev iç içe bir düzey adımlar.</span><span class="sxs-lookup"><span data-stu-id="73ced-195">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="73ced-196">Ana gövdesinde, komut sonuna ya da sonraki kesme noktasına yürütülürse.</span><span class="sxs-lookup"><span data-stu-id="73ced-196">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="73ced-197">Atlanan deyimleri yürütülür, ancak aracılığıyla basamaklı değil.</span><span class="sxs-lookup"><span data-stu-id="73ced-197">The skipped statements are executed, but not stepped through.</span></span> | <span data-ttu-id="73ced-198">Basın **SHIFT + F11**, veya **hata ayıklama** menüsünde tıklatın **Step Out**, veya Konsol bölmesinde, **O** tuşuna basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-198">Press **SHIFT+F11**, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type **O** and press **ENTER**.</span></span> |
| <span data-ttu-id="73ced-199">**Devam et**</span><span class="sxs-lookup"><span data-stu-id="73ced-199">**Continue**</span></span> | <span data-ttu-id="73ced-200">Sonuna ya da sonraki kesme noktasına yürütme devam eder.</span><span class="sxs-lookup"><span data-stu-id="73ced-200">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="73ced-201">Atlanan işlevleri ve çağrılarını yürütülür, ancak aracılığıyla basamaklı değil.</span><span class="sxs-lookup"><span data-stu-id="73ced-201">The skipped functions and invocations are executed, but not stepped through.</span></span> | <span data-ttu-id="73ced-202">Basın **F5** veya **hata ayıklama** menüsünde, tıklayın **Çalıştır/devam**, veya Konsol bölmesinde, **C** basın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-202">Press **F5** or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type **C** and press **ENTER**.</span></span> |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a><span data-ttu-id="73ced-203">Hata ayıklama sırasında değişkenlerin değerlerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="73ced-203">How to display the values of variables while debugging</span></span>

<span data-ttu-id="73ced-204">Kodunuz içinde adım adım olarak, betikte değişkenlerin geçerli değerleri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-204">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="73ced-205">Standart değişkenlerin değerleri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="73ced-205">To display the values of standard variables</span></span>

<span data-ttu-id="73ced-206">Aşağıdaki yöntemlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="73ced-206">Use one of the following methods:</span></span>

- <span data-ttu-id="73ced-207">Betik bölmesinde bir araç ipucu değerini görüntülemek için değişkenin üzerine gelin.</span><span class="sxs-lookup"><span data-stu-id="73ced-207">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

- <span data-ttu-id="73ced-208">Konsol bölmesinde, tuşuna basın ve değişken adını yazın **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="73ced-208">In the Console Pane, type the variable name and press **ENTER**.</span></span>

<span data-ttu-id="73ced-209">ISE tüm bölmelerde aynı kapsam içinde her zaman olur.</span><span class="sxs-lookup"><span data-stu-id="73ced-209">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="73ced-210">Bu nedenle, bir komut dosyası hata ayıklama sırasında kod kapsamında Konsol bölmesinde yazdığınız komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73ced-210">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="73ced-211">Bu değişkenlerin değerleri bulmak ve yalnızca komut dosyasında tanımlanan işlevleri çağırmak için konsol bölmesinde kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="73ced-211">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="73ced-212">Otomatik değişkenlerin değerleri görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="73ced-212">To display the values of automatic variables</span></span>

<span data-ttu-id="73ced-213">Bir komut dosyası hata ayıklama sırasında neredeyse tüm değişkenlerin değerini görüntülemek için yukarıdaki yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ced-213">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="73ced-214">Ancak, bu yöntemler aşağıdaki otomatik değişkenleri çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="73ced-214">However, these methods do not work for the following automatic variables.</span></span>

- <span data-ttu-id="73ced-215">$_</span><span class="sxs-lookup"><span data-stu-id="73ced-215">$_</span></span>

- <span data-ttu-id="73ced-216">$Input</span><span class="sxs-lookup"><span data-stu-id="73ced-216">$Input</span></span>

- <span data-ttu-id="73ced-217">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="73ced-217">$MyInvocation</span></span>

- <span data-ttu-id="73ced-218">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="73ced-218">$PSBoundParameters</span></span>

- <span data-ttu-id="73ced-219">$Args</span><span class="sxs-lookup"><span data-stu-id="73ced-219">$Args</span></span>

<span data-ttu-id="73ced-220">Bu değişkenlerin değerini görüntülemek çalışırsanız, hata ayıklayıcı bir iç işlem hattında kullandığı için değildir komut dosyasında değişkeninin değeri değişken değerini alın.</span><span class="sxs-lookup"><span data-stu-id="73ced-220">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="73ced-221">Bu sorunu ($_, $Input, $MyInvocation, $PSBoundParameters ve $Args) birkaç değişkenleri aşağıdaki yöntemi kullanarak çalışabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="73ced-221">You can work around this for a few variables ($_, $Input, $MyInvocation, $PSBoundParameters, and $Args) by using the following method:</span></span>

1. <span data-ttu-id="73ced-222">Betik, otomatik değişkeninin değerini yeni bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="73ced-222">In the script, assign the value of the automatic variable to a new variable.</span></span>

2. <span data-ttu-id="73ced-223">Betik bölmesine yeni değişkenin üzerine geldiğinizde veya Konsol bölmesinde yeni bir değişken yazarak yeni bir değişkenin değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="73ced-223">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="73ced-224">Örneğin, betikte $MyInvocation değişkenin değerini görüntülemek için $scriptname gibi yeni bir değişken bir değer atayın ve ardından üzerine gelin veya $scriptname değişkenin değerini görüntülemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="73ced-224">For example, to display the value of the $MyInvocation variable, in the script, assign the value to a new variable, such as $scriptname, and then hover over or type the $scriptname variable to display its value.</span></span>

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="73ced-225">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="73ced-225">See Also</span></span>

- [<span data-ttu-id="73ced-226">Windows PowerShell ISE’yi Keşfetme</span><span class="sxs-lookup"><span data-stu-id="73ced-226">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)