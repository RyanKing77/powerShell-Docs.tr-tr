---
ms.date: 08/23/2017
keywords: PowerShell cmdlet'i
title: Windows powershell web erişimini kaldırma
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405939"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="80fb6-103">Windows PowerShell Web Erişimini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="80fb6-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="80fb6-104">Güncelleştirme tarihi: 24 Haziran 2013</span><span class="sxs-lookup"><span data-stu-id="80fb6-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="80fb6-105">Şunun için geçerlidir: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="80fb6-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="80fb6-106">Bu konu başlığındaki adımları karşılık gelen uygulama ve Windows PowerShell Web Erişimi Web sitesinin yüklü olduğu ağ geçidi sunucusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="80fb6-107">Kullanıcılara bildirme</span><span class="sxs-lookup"><span data-stu-id="80fb6-107">Notify users</span></span>

<span data-ttu-id="80fb6-108">Başlamadan önce, web tabanlı konsolun kullanıcılarına web sitesini kaldırdığınızı bildirin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="80fb6-109">Windows PowerShell Web erişimini kaldırma, IIS veya çalıştırmak için Windows PowerShell Web erişimi için gerekli olduğundan, otomatik olarak yüklenen diğer özellikler kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="80fb6-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="80fb6-110">Kaldırma işlemi, Windows PowerShell Web erişimi bağımlı özellikleri yüklü bırakır; Bu özellikleri gerekirse ayrı ayrı kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80fb6-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="80fb6-111">Önerilen (hızlı) kaldırma</span><span class="sxs-lookup"><span data-stu-id="80fb6-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="80fb6-112">Bu bölümdeki yordamlar hem kaldırmanıza yardımcı:</span><span class="sxs-lookup"><span data-stu-id="80fb6-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="80fb6-113">Windows PowerShell Web erişimi web uygulaması ve</span><span class="sxs-lookup"><span data-stu-id="80fb6-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="80fb6-114">Windows PowerShell Web erişim özelliği</span><span class="sxs-lookup"><span data-stu-id="80fb6-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="80fb6-115">Windows PowerShell cmdlet'lerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="80fb6-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="80fb6-116">Adım 1: Cmdlet'lerini kullanarak web uygulamasını silme</span><span class="sxs-lookup"><span data-stu-id="80fb6-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="80fb6-117">Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="80fb6-118">Windows masaüstünde, sağ **Windows PowerShell** görev.</span><span class="sxs-lookup"><span data-stu-id="80fb6-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="80fb6-119">Windows üzerinde **Başlat** ekranında **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="80fb6-120">Tür `Uninstall-PswaWebApplication`ve tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="80fb6-121">Kendi, özel web sitesi adınızı belirttiyseniz, komutunuza `-WebsiteName` parametresini ekleyin ve web sitesi adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="80fb6-122">Özel bir web uygulaması kullandıysanız (varsayılan uygulama **pswa**, ekleme `-WebApplicationName` parametresini komutunuza, web uygulamasının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="80fb6-123">Bir test sertifikası kullanıyorsanız, aşağıdaki örnekte gösterildiği gibi `DeleteTestCertificate` parametresini cmdlet’e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="80fb6-124">Adım 2: Cmdlet'lerini kullanarak Windows PowerShell Web erişimini kaldırma</span><span class="sxs-lookup"><span data-stu-id="80fb6-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="80fb6-125">Bir Windows PowerShell oturumu yükseltilmiş kullanıcı haklarıyla açmak için aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="80fb6-126">Bir oturum zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="80fb6-127">Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="80fb6-128">Windows üzerinde **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="80fb6-129">Aşağıdaki komutu yazın ve ardından basın **Enter**burada *bilgisayar_adı* Windows PowerShell Web erişimini kaldırmak istediğiniz uzak bir sunucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="80fb6-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="80fb6-130">Kaldırma işlemi gerektiriyorsa `-Restart` parametresi otomatik olarak hedef sunucuları yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="80fb6-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="80fb6-131">Çevrimdışı bir VHD’den rolleri ve özellikleri kaldırmak için hem `-ComputerName` parametresini hem de `-VHD` parametresini eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="80fb6-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="80fb6-132">`-ComputerName` parametresi, VHD’nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="80fb6-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="80fb6-133">Kaldırma tamamlandığında, Windows PowerShell Web erişimi açarak kaldırdığını doğrulamak **tüm sunucuları** sayfası sunucu Özelliği Kaldırdığınız bir sunucuyu seçerek ve görüntüleme Yöneticisi ' nde **rolleri ve Özellikleri** döşeme sonra seçtiğiniz sunucu için sayfadaki.</span><span class="sxs-lookup"><span data-stu-id="80fb6-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="80fb6-134">Da çalıştırabilirsiniz `Get-WindowsFeature` seçilen sunucuda hedeflenen cmdlet (Get-WindowsFeature - ComputerName &lt; *bilgisayar_adı*&gt;), sunucuda yüklü rol ve özellikleri bir listesini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="80fb6-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="80fb6-135">Özel kaldırma</span><span class="sxs-lookup"><span data-stu-id="80fb6-135">Custom uninstallation</span></span>

<span data-ttu-id="80fb6-136">Bu bölümdeki yordamlar hem Windows PowerShell Web erişimi web uygulamasını hem de Kaldır rolleri ve özellikleri Sihirbazı'nı Sunucu Yöneticisi'nde ve IIS Yöneticisi konsolunu kullanarak Windows PowerShell Web erişimi özelliğini kaldırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="80fb6-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="80fb6-137">Adım 1: IIS Yöneticisi'ni kullanarak web uygulamasını silme</span><span class="sxs-lookup"><span data-stu-id="80fb6-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="80fb6-138">Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="80fb6-139">Zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="80fb6-140">Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="80fb6-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="80fb6-141">Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="80fb6-142">Windows üzerinde **Başlat** ekranında, adının bir kısmını **Internet Information Services (IIS) Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="80fb6-143">İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.</span><span class="sxs-lookup"><span data-stu-id="80fb6-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="80fb6-144">IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesini seçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="80fb6-145">İçinde **eylemleri** bölmesi altında **Web sitesini Yönet**, tıklayın **Durdur**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="80fb6-146">Ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesindeki web uygulamaya sağ tıklayın ve ardından **Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="80fb6-147">Ağaç bölmesinde seçin **uygulama havuzları**, Windows PowerShell Web erişimi uygulama havuzu klasörünü seçin, **Durdur** içinde **eylemleri** bölmesinde ve 'yetıklayın **Kaldırma** içerik bölmesinde.</span><span class="sxs-lookup"><span data-stu-id="80fb6-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="80fb6-148">IIS Yöneticisi’ni kapatın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-148">Close IIS Manager.</span></span>

> <span data-ttu-id="80fb6-149">![Uyarı Not](images/SecurityNote.jpeg)**Not**:</span><span class="sxs-lookup"><span data-stu-id="80fb6-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="80fb6-150">Sertifika kaldırma sırasında silinmez.</span><span class="sxs-lookup"><span data-stu-id="80fb6-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="80fb6-151">Kendinden imzalı bir sertifika oluşturduysanız veya bir test sertifikası kullanıyor ve bunu kaldırmak istiyorsanız, IIS Yöneticisi'nde sertifikayı silin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="80fb6-152">Adım 2: Kaldır rolleri ve özellikleri Sihirbazı'nı kullanarak Windows PowerShell Web erişimini kaldırma</span><span class="sxs-lookup"><span data-stu-id="80fb6-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="80fb6-153">Sunucu Yöneticisi zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="80fb6-154">Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.</span><span class="sxs-lookup"><span data-stu-id="80fb6-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="80fb6-155">Tıklayarak Windows masaüstünde, Sunucu Yöneticisi'ni başlatın **Sunucu Yöneticisi'ni** Windows görev çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="80fb6-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="80fb6-156">Windows üzerinde **Başlat** ekranında **Sunucu Yöneticisi**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="80fb6-157">Üzerinde **Yönet** menüsünü tıklatın **Kaldır rolleri ve özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="80fb6-158">Üzerinde **hedef sunucuyu seçin** sayfasında, özelliği kaldırmak istediğiniz sunucuyu veya çevrimdışı VHD'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="80fb6-159">Çevrimdışı bir VHD’yi seçmek için önce VHD’nin bağlanacağı sunucuyu ve sonra VHD dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="80fb6-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="80fb6-160">Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="80fb6-161">Tıklayın **sonraki** atlamak için yeniden **Özellik Kaldır** sayfası.</span><span class="sxs-lookup"><span data-stu-id="80fb6-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="80fb6-162">Onay kutusunu temizleyin **Windows PowerShell Web erişimi**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="80fb6-163">Üzerinde **kaldırma seçimlerini onaylayın** sayfasında **Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="80fb6-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="80fb6-164">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="80fb6-164">See Also</span></span>

- [<span data-ttu-id="80fb6-165">Windows PowerShell Web erişimi yükleme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="80fb6-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="80fb6-166">IIS Yöneticisi 7.0 Yardımı</span><span class="sxs-lookup"><span data-stu-id="80fb6-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)