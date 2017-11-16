---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "İstenen durum yapılandırması PowerShell ile çalışmaya başlama"
ms.openlocfilehash: 403badd11749cfa5c6a5d07e1b537fa3a5f954da
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="16f18-103">İstenen durum yapılandırması PowerShell ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="16f18-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="16f18-104">Bu kılavuz, PowerShell istenen durum yapılandırması belgeleri oluşturmaya başlamak ve makinelere Uygula açıklar.</span><span class="sxs-lookup"><span data-stu-id="16f18-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="16f18-105">PowerShell cmdlet'leri, modüller ve işlevleri temel olarak bilindiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="16f18-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span> 


## <a name="create-a-configuration"></a><span data-ttu-id="16f18-106">Bir yapılandırma oluşturmak</span><span class="sxs-lookup"><span data-stu-id="16f18-106">Create a Configuration</span></span> ##

<span data-ttu-id="16f18-107">[**Yapılandırmaları** ](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) bir ortam açıklamak belgelerdir.</span><span class="sxs-lookup"><span data-stu-id="16f18-107">[**Configurations**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="16f18-108">Ortamlar oluşur "**düğümleri**", olan yaygın olarak sanal veya fiziksel makineler.</span><span class="sxs-lookup"><span data-stu-id="16f18-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span> 

<span data-ttu-id="16f18-109">Yapılandırmaları çeşitli formlarını gelebilir.</span><span class="sxs-lookup"><span data-stu-id="16f18-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="16f18-110">Yeni bir yapılandırma oluşturmak için en kolay yolu, bir .ps1 (PowerShell) betiği oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="16f18-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="16f18-111">Bunu yapmak için tercih düzenleyicide açın.</span><span class="sxs-lookup"><span data-stu-id="16f18-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="16f18-112">DSC yerel anladığı beri PowerShell ISE olduğunda iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="16f18-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="16f18-113">Aşağıdaki PS1 Kaydet:</span><span class="sxs-lookup"><span data-stu-id="16f18-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="16f18-114">Bir yapılandırma bölümlerini</span><span class="sxs-lookup"><span data-stu-id="16f18-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="16f18-115">**Yapılandırma** PowerShell 4.0 eklenen bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="16f18-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="16f18-116">İstenen durum yapılandırması tarafından kullanılan PowerShell işlevi özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="16f18-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="16f18-117">Bu örnekte, işlev myFirstConfiguration olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="16f18-117">In this example, the function is named myFirstConfiguration.</span></span> 

<span data-ttu-id="16f18-118">Sonraki satıra bir modülü içeri aktarmaya benzer bir içeri aktarma ifadesi olur.</span><span class="sxs-lookup"><span data-stu-id="16f18-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="16f18-119">Daha sonra incelenecektir.</span><span class="sxs-lookup"><span data-stu-id="16f18-119">It will be discussed later on.</span></span>

<span data-ttu-id="16f18-120">Bu yapılandırma üzerinde görecek makine adı "Düğümü" tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16f18-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="16f18-121">Bu yapılandırma yerel olarak düzenlenen rağmen yapılandırmaları uzak düğümlerine ulaşmak ve bunları yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16f18-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span> 

<span data-ttu-id="16f18-122">Düğümler, makine adı veya IP adresleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="16f18-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="16f18-123">Birden çok düğüm tek yapılandırma belgede olabilir.</span><span class="sxs-lookup"><span data-stu-id="16f18-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="16f18-124">Kullanarak [yapılandırma verilerini](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), birden çok düğümlerine uygulamak aynı yapılandırmaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="16f18-124">Using [configuration data](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="16f18-125">Bu durumda, "yerel bilgisayarda anlamı localhost" - düğümdür.</span><span class="sxs-lookup"><span data-stu-id="16f18-125">In this case, the node is "localhost" - which means the local computer.</span></span> 

<span data-ttu-id="16f18-126">Sonraki öğe bir [ **kaynak**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="16f18-126">The next item is a [**resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span></span> <span data-ttu-id="16f18-127">Kaynaklar, yapılandırmaları yapı taşlarıdır.</span><span class="sxs-lookup"><span data-stu-id="16f18-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="16f18-128">Her kaynak makinenin tek bir boyut uygulama mantığını tanımlayan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="16f18-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="16f18-129">Her kaynak makinenize çalıştırarak görüntüleyebileceğiniz **Get-DscResource** PowerShell'de.</span><span class="sxs-lookup"><span data-stu-id="16f18-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="16f18-130">Kaynaklar yerel makinede mevcut olması gerekir ve bir yapılandırmasında kullanılmadan önce içeri **alma DscResource** bu yapılandırma ikinci satırda olduğu.</span><span class="sxs-lookup"><span data-stu-id="16f18-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span> 

<span data-ttu-id="16f18-131">**Bir yapılandırma ederek ilerlemesini kabul ederek**</span><span class="sxs-lookup"><span data-stu-id="16f18-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="16f18-132">Yukarıdaki komut dosyasını çalıştırın ve kaydedilir, hiçbir çıkış oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16f18-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="16f18-133">Yalnızca bir işlevi bir yapılandırma olduğundan ve yukarıdaki betik işlevi tanımlanmış ancak çalışmıyor henüz bunu budur.</span><span class="sxs-lookup"><span data-stu-id="16f18-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="16f18-134">İşlev tanımlandıktan sonra çağrılan gerekir:</span><span class="sxs-lookup"><span data-stu-id="16f18-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="16f18-135">Çalıştırıldığında, yapılandırma işlevleri yapılandırmasını doğrulama geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="16f18-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="16f18-136">Sözdizimi hatası olmalıdır, kaynakları tanımlanan tüm zorunlu parametreler olmalıdır ve çalışmaya başlamadan önce tüm kaynakların aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16f18-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="16f18-137">Yapılandırma yürütüldükten sonra içeren yapılandırma adı ile bir klasör oluşturur bir **. MOF dosyası** yapılandırma kümedeki her düğüm için.</span><span class="sxs-lookup"><span data-stu-id="16f18-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="16f18-138">. MOF dosyasını ağ üzerinden iletişim kurmak için PowerShell DSC tarafından kullanılan Yönetimi standartlara dayalı bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="16f18-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="16f18-139">Yapılandırma yürürlüğe için:</span><span class="sxs-lookup"><span data-stu-id="16f18-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="16f18-140">Bu yapılandırma düğümlerin ulaşana ve bunları yapılandırır bir PowerShell iş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16f18-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="16f18-141">İş çıkışını görmek için kullanın - bekleyin.</span><span class="sxs-lookup"><span data-stu-id="16f18-141">To see the output of the job, use -Wait.</span></span> 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

