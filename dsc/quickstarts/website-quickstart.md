---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405680"
---
> <span data-ttu-id="b476e-103">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b476e-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="b476e-104">Hızlı Başlangıç - DSC ile bir Web sitesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b476e-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="b476e-105">Bu alıştırmada oluşturmak ve uygulamak başlangıçtan bitişe kadar bir Desired State Configuration ' nı (DSC) yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b476e-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="b476e-106">Kullanacağız örnek bir sunucuya sahip olmasını sağlar `Web-Server` (IIS) özelliği etkin ve basit bir "Hello World" Web sitesi için içeriğin mevcut olduğu `intepub\wwwroot` sunucusunun dizin.</span><span class="sxs-lookup"><span data-stu-id="b476e-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="b476e-107">DSC nedir ve nasıl çalıştığını genel bakış için bkz: [karar alıcılar için genel Desired State Configuration](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="b476e-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b476e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b476e-108">Requirements</span></span>

<span data-ttu-id="b476e-109">Bu örneği çalıştırmak için Windows Server 2012 veya sonraki sürümünü ve PowerShell 4.0 veya sonraki sürümü çalıştıran bir bilgisayar gerekir.</span><span class="sxs-lookup"><span data-stu-id="b476e-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="b476e-110">Yazma ve index.htm dosyası yerleştirin</span><span class="sxs-lookup"><span data-stu-id="b476e-110">Write and place the index.htm file</span></span>

<span data-ttu-id="b476e-111">İlk olarak, Web sitesi içeriği olarak kullanacağız HTML dosyası oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="b476e-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="b476e-112">Kök klasörünüzde adlı bir klasör oluşturun `test`.</span><span class="sxs-lookup"><span data-stu-id="b476e-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="b476e-113">Bir metin düzenleyicisinde, aşağıdaki metni yazın:</span><span class="sxs-lookup"><span data-stu-id="b476e-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="b476e-114">Bu olarak Kaydet `index.htm` içinde `test` daha önce oluşturduğunuz klasör.</span><span class="sxs-lookup"><span data-stu-id="b476e-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="b476e-115">Yapılandırmasını yazın</span><span class="sxs-lookup"><span data-stu-id="b476e-115">Write the configuration</span></span>

<span data-ttu-id="b476e-116">A [DSC Yapılandırması](../configurations/configurations.md) tanımlayan bir veya daha fazla hedef bilgisayarların (düğümlerin) yapılandırmak istediğiniz nasıl özel bir PowerShell işlevdir.</span><span class="sxs-lookup"><span data-stu-id="b476e-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="b476e-117">PowerShell ISE'de aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="b476e-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="b476e-118">Dosyayı Farklı Kaydet `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b476e-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="b476e-119">Anahtar sözcüğü ile birlikte bir PowerShell işlevi gibi görünüyor görebilirsiniz **yapılandırma** işlevin adını önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b476e-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="b476e-120">**Düğüm** blok belirtir, bu durumda yapılandırılması için hedef düğümü `localhost`.</span><span class="sxs-lookup"><span data-stu-id="b476e-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="b476e-121">İki yapılandırma çağırır [kaynakları](../resources/resources.md), **WindowsFeature** ve **dosya**.</span><span class="sxs-lookup"><span data-stu-id="b476e-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="b476e-122">Kaynak hedef düğüm yapılandırması tarafından tanımlanmış durumda sağlayarak iş yapın.</span><span class="sxs-lookup"><span data-stu-id="b476e-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="b476e-123">Yapılandırma derleme</span><span class="sxs-lookup"><span data-stu-id="b476e-123">Compile the configuration</span></span>

<span data-ttu-id="b476e-124">DSC yapılandırması düğüme uygulanacak ilk MOF dosyasına derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b476e-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="b476e-125">Bunu yapmak için yapılandırmanın bir işlev gibi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b476e-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="b476e-126">Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve bir MOF dosyasına yapılandırmayı derlemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b476e-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="b476e-127">Bu, aşağıdaki çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b476e-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="b476e-128">İlk satırı yapılandırma işlevi konsolunda kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b476e-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="b476e-129">İkinci satır yapılandırması çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="b476e-129">The second line runs the configuration.</span></span>
<span data-ttu-id="b476e-130">Adlı yeni bir klasörün sonucudur `WebsiteTest` bir alt klasör geçerli klasörde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b476e-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="b476e-131">`WebsiteTest` Klasör adlı dosyayı içeren `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="b476e-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="b476e-132">Ardından hedef düğüme uygulanan bu dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b476e-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="b476e-133">Yapılandırmasını Uygula</span><span class="sxs-lookup"><span data-stu-id="b476e-133">Apply the configuration</span></span>

<span data-ttu-id="b476e-134">Derlenmiş MOF olduğuna göre yapılandırma (Bu durumda, yerel bilgisayar) hedef düğüm çağırarak uygulayabileceğiniz [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="b476e-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="b476e-135">`Start-DscConfiguration` Cmdlet'i söyler [yerel Configuration Manager'ı (LCM)](../managing-nodes/metaConfig.md), yapılandırmayı uygulamak için DSC, altyapı olduğu.</span><span class="sxs-lookup"><span data-stu-id="b476e-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="b476e-136">LCM yapılandırmayı uygulamak için DSC kaynakları çağırma çalışır.</span><span class="sxs-lookup"><span data-stu-id="b476e-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="b476e-137">Bir PowerShell konsolunda yapılandırmanızı kaydettiğiniz klasöre gidin ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b476e-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="b476e-138">Test yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b476e-138">Test the configuration</span></span>

<span data-ttu-id="b476e-139">Çağırabilirsiniz [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) Yapılandırması başarılı olup olmadığını görmek için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b476e-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="b476e-140">Ayrıca sonuçları doğrudan, bu durumda göz atarak sınayabilirsiniz `http://localhost/` bir web tarayıcısında.</span><span class="sxs-lookup"><span data-stu-id="b476e-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="b476e-141">Bu örnekte ilk adım olarak, oluşturduğunuz "Hello World" HTML sayfası görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b476e-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b476e-142">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b476e-142">Next steps</span></span>

- <span data-ttu-id="b476e-143">DSC yapılandırmalar hakkında daha fazla bilgi edinin [DSC yapılandırmaları](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="b476e-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="b476e-144">Hangi DSC kaynakların kullanılabilir olduğundan ve özel DSC kaynakları oluşturmak nasıl [DSC kaynakları](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="b476e-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="b476e-145">DSC yapılandırmaları ve kaynakları Bul [PowerShell Galerisi](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b476e-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
