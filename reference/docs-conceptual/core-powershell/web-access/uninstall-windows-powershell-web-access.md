---
ms.date: 2017-08-23
keywords: PowerShell cmdlet'i
title: "Windows powershell web erişimini kaldırma"
ms.openlocfilehash: b6e6a2374e6b4b2be8742019c5f1e4d5b5d1abe3
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2017
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="a7d18-103">Windows PowerShell Web Erişimini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a7d18-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="a7d18-104">Güncelleştirilmiş: 24 Haziran 2013</span><span class="sxs-lookup"><span data-stu-id="a7d18-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="a7d18-105">İçin geçerlidir: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a7d18-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="a7d18-106">Bu konudaki adımlarda Windows PowerShell Web erişimi ve karşılık gelen uygulama yüklü olduğu ağ geçidi sunucusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="a7d18-107">Kullanıcıları bildir</span><span class="sxs-lookup"><span data-stu-id="a7d18-107">Notify users</span></span>

<span data-ttu-id="a7d18-108">Başlamadan önce, web tabanlı konsolun kullanıcılarına web sitesini kaldırdığınızı bildirin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="a7d18-109">Windows PowerShell Web erişimini kaldırma IIS veya Windows PowerShell Web erişimi çalıştırmalarını gerektirdiğinden, otomatik olarak yüklenen diğer özellikler kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="a7d18-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="a7d18-110">Kaldırma işlemi, Windows PowerShell Web erişimi bağımlı özellikleri yüklü bırakır; Bu özellikleri gerekirse ayrı ayrı kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7d18-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="a7d18-111">Önerilen (hızlı) kaldırma</span><span class="sxs-lookup"><span data-stu-id="a7d18-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="a7d18-112">Bu bölümdeki yordamlar hem kaldırmanıza yardımcı:</span><span class="sxs-lookup"><span data-stu-id="a7d18-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="a7d18-113">Windows PowerShell Web erişimi web uygulaması ve</span><span class="sxs-lookup"><span data-stu-id="a7d18-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="a7d18-114">Windows PowerShell Web erişimi özelliği</span><span class="sxs-lookup"><span data-stu-id="a7d18-114">the Windows PowerShell Web Access feature</span></span>
 
<span data-ttu-id="a7d18-115">Windows PowerShell cmdlet'lerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a7d18-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="a7d18-116">1. adım: cmdlet'lerini kullanarak web uygulamasını silme</span><span class="sxs-lookup"><span data-stu-id="a7d18-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="a7d18-117">Bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="a7d18-118">Windows masaüstünde, sağ **Windows PowerShell** görev çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="a7d18-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="a7d18-119">Windows **Başlat** ekranında **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="a7d18-120">Tür `Uninstall-PswaWebApplication`ve tuşuna basarak **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="a7d18-121">Kendi, özel web sitesi adınızı belirttiyseniz, komutunuza `-WebsiteName` parametresini ekleyin ve web sitesi adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="a7d18-122">Özel bir web uygulaması kullandıysanız (varsayılan uygulama değil, **pswa**, ekleme `-WebApplicationName` parametresi, komut ve web uygulamasının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="a7d18-123">Bir test sertifikası kullanıyorsanız, aşağıdaki örnekte gösterildiği gibi `DeleteTestCertificate` parametresini cmdlet’e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="a7d18-124">2. adım: Windows PowerShell Web erişimi cmdlet'leri kullanarak kaldırma</span><span class="sxs-lookup"><span data-stu-id="a7d18-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="a7d18-125">Yükseltilmiş kullanıcı haklarıyla bir Windows PowerShell oturumu açmak için aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="a7d18-126">Bir oturum zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="a7d18-127">Windows masaüstünde, sağ **Windows PowerShell** görev ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="a7d18-128">Windows **Başlat** ekranında, sağ **Windows PowerShell**ve ardından **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="a7d18-129">Aşağıdaki komutu yazın ve sonra basın **Enter**, burada *bilgisayar_adı* istediğiniz Windows PowerShell Web erişimi kaldırmak bir uzak sunucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7d18-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="a7d18-130">Kaldırma işlemi gerektiriyorsa `-Restart` parametresi otomatik olarak hedef sunucuları yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="a7d18-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="a7d18-131">Çevrimdışı bir VHD’den rolleri ve özellikleri kaldırmak için hem `-ComputerName` parametresini hem de `-VHD` parametresini eklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a7d18-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="a7d18-132">`-ComputerName` parametresi, VHD’nin bağlanacağı sunucunun adını içerir ve `-VHD` parametresi de belirtilen sunucuda VHD dosyasının yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7d18-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="a7d18-133">Kaldırma tamamlandığında, Windows PowerShell Web erişimi açarak kaldırdığını doğrulamak **tüm sunucuları** sayfası sunucu Özelliği Kaldırdığınız sunucuyu seçip ve görüntüleme Yöneticisi ' nde **rolleri ve Özellikler** döşeme seçilen sunucunun sayfasında.</span><span class="sxs-lookup"><span data-stu-id="a7d18-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="a7d18-134">De çalıştırabilirsiniz `Get-WindowsFeature` seçilen sunucuda hedeflenen cmdlet (Get-WindowsFeature - ComputerName &lt; *bilgisayar_adı*&gt;), sunucuda yüklü rol ve özellikleri listesini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="a7d18-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="a7d18-135">Özel kaldırma</span><span class="sxs-lookup"><span data-stu-id="a7d18-135">Custom uninstallation</span></span>

<span data-ttu-id="a7d18-136">Bu bölümdeki yordamlar hem Windows PowerShell Web erişimi web uygulaması hem de kaldırma roller ve Özellikler Sihirbazı'nı Sunucu Yöneticisi'nde ve IIS Yöneticisi konsolunu kullanarak Windows PowerShell Web erişimi özelliğini kaldırmanıza yardımcı.</span><span class="sxs-lookup"><span data-stu-id="a7d18-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="a7d18-137">1. adım: IIS Yöneticisi'ni kullanarak web uygulamasını silme</span><span class="sxs-lookup"><span data-stu-id="a7d18-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="a7d18-138">Aşağıdakilerden birini yaparak IIS Yöneticisi konsolunu açın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="a7d18-139">Zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="a7d18-140">Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="a7d18-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="a7d18-141">Üzerinde **Araçları** Sunucu Yöneticisi ' nde menüsünü **Internet Information Services (IIS) Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="a7d18-142">Windows **Başlat** adının bir kısmını ekranında, **Internet Information Services (IIS) Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="a7d18-143">İçinde gösterildiğinde kısayola tıklayın **uygulamaları** sonuçları.</span><span class="sxs-lookup"><span data-stu-id="a7d18-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="a7d18-144">IIS Yöneticisi ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="a7d18-145">İçinde **Eylemler** bölmesi altında **Web sitesini Yönet**, tıklatın **durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="a7d18-146">Ağaç bölmesinde, Windows PowerShell Web erişimi web uygulamasını çalıştıran Web sitesi web uygulamasında sağ tıklayın ve ardından **kaldırmak**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="a7d18-147">Ağaç bölmesinde seçin **uygulama havuzları**, Windows PowerShell Web erişimi uygulama havuzu klasörünü seçin, **durdurmak** içinde **Eylemler** bölmesinde ve 'ıtıklatın **Kaldırma** içerik bölmesindeki.</span><span class="sxs-lookup"><span data-stu-id="a7d18-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="a7d18-148">IIS Yöneticisi’ni kapatın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-148">Close IIS Manager.</span></span>

> <span data-ttu-id="a7d18-149">![Uyarı notu](images/SecurityNote.jpeg)**Not**:</span><span class="sxs-lookup"><span data-stu-id="a7d18-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="a7d18-150">Sertifika kaldırma sırasında silinmez.</span><span class="sxs-lookup"><span data-stu-id="a7d18-150">The certificate is not deleted during uninstallation.</span></span> 
>
> <span data-ttu-id="a7d18-151">Kendinden imzalı bir sertifika oluşturduysanız veya bir test sertifikası kullanıyor ve bunu kaldırmak istiyorsanız, IIS Yöneticisi'nde sertifikayı silin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span> 

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="a7d18-152">2. adım: Kaldırma rol ve Özellik Ekleme Sihirbazı'nı kullanarak Windows PowerShell Web erişimini kaldırma</span><span class="sxs-lookup"><span data-stu-id="a7d18-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="a7d18-153">Sunucu Yöneticisi'ni zaten açıksa sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="a7d18-154">Sunucu Yöneticisi'ni zaten açık değilse aşağıdakilerden birini yaparak açın.</span><span class="sxs-lookup"><span data-stu-id="a7d18-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="a7d18-155">Windows masaüstünde, Sunucu Yöneticisi'ni tıklatarak Başlat **Sunucu Yöneticisi'ni** Windows görev çubuğunda.</span><span class="sxs-lookup"><span data-stu-id="a7d18-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="a7d18-156">Windows **Başlat** ekranında **Sunucu Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="a7d18-157">Üzerinde **Yönet** menüsünde tıklatın **rolleri ve özellikleri Kaldır**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="a7d18-158">Üzerinde **Select hedef sunucu** sayfasında, özelliği kaldırmak istediğiniz sunucuyu veya çevrimdışı VHD'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="a7d18-159">Çevrimdışı bir VHD’yi seçmek için önce VHD’nin bağlanacağı sunucuyu ve sonra VHD dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="a7d18-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="a7d18-160">Hedef sunucuyu seçtikten sonra tıklayın **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="a7d18-161">Tıklatın **sonraki** atlamak için yeniden **kaldırma özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="a7d18-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="a7d18-162">Onay kutusunu temizleyin **Windows PowerShell Web erişimi**ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="a7d18-163">Üzerinde **Kaldırma Seçimlerini Onayla** sayfasında, **kaldırmak**.</span><span class="sxs-lookup"><span data-stu-id="a7d18-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d18-164">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a7d18-164">See Also</span></span>

- [<span data-ttu-id="a7d18-165">Yükleme ve Windows PowerShell Web erişimini kullanma</span><span class="sxs-lookup"><span data-stu-id="a7d18-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="a7d18-166">IIS Yöneticisi 7.0 Yardımı</span><span class="sxs-lookup"><span data-stu-id="a7d18-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)
