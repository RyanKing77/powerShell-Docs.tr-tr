---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Karar Verenler için İstenen Durum Yapılandırmasına Genel Bakış
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079600"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="2ad27-103">Karar Verenler için İstenen Durum Yapılandırmasına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2ad27-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="2ad27-104">Bu belgede, Windows PowerShell Desired State Configuration (DSC) kullanarak iş avantajları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ad27-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="2ad27-105">Bu teknik bir kılavuz değildir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="2ad27-106">Nedir Desired State Configuration?</span><span class="sxs-lookup"><span data-stu-id="2ad27-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="2ad27-107">PowerShell Desired State Configuration açık standartları temel alan Windows yerleşik bir yapılandırma yönetim platformudur.</span><span class="sxs-lookup"><span data-stu-id="2ad27-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="2ad27-108">DSC (geliştirme, test, üretim öncesi ve üretim) dağıtım yaşam döngüsünün yanı sıra ölçek genişletme sırasında her aşamasında güvenilir ve tutarlı bir şekilde çalışması için yeterince esnektir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="2ad27-109">DSC merkezleri etrafında [yapılandırmaları](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="2ad27-109">DSC centers around [configurations](../configurations/configurations.md).</span></span>
<span data-ttu-id="2ad27-110">("Düğüm") belirli özelliklere sahip bilgisayarlardan oluşan bir ortamı tanımlayan bir kolay okunur belgesi bir yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="2ad27-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="2ad27-111">Bu özelliklere, belirli bir Windows özelliği etkin veya SharePoint dağıtımı gibi karmaşık sunulmasını sağlarken diğer yandan olarak basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="2ad27-112">DSC ayrıca sahip izleme ve raporlama yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ad27-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="2ad27-113">Bir sistem artık uyumlu değilse, DSC bir uyarı oluşturmalı ve sistem düzeltmek için harekete geçin.</span><span class="sxs-lookup"><span data-stu-id="2ad27-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="2ad27-114">Desired State Configuration ' ı kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="2ad27-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="2ad27-115">Yapılandırmaları kolayca okuyun, güncelleştirilen ve depolanacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2ad27-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="2ad27-116">Yapılandırmaları durumu hedef cihazlar durumundaki koymak yönergeleri yazmak yerine olması bildirin.</span><span class="sxs-lookup"><span data-stu-id="2ad27-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="2ad27-117">Bu, benimseme, uygulamak ve aracılığıyla DSC yapılandırması korumak daha az yüke neden olur.</span><span class="sxs-lookup"><span data-stu-id="2ad27-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="2ad27-118">Yapılandırmaları oluşturma, tek bir konumda bir "tek gerçeklik kaynağı" karmaşık dağıtım adımları yakalanan anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="2ad27-119">Bu yinelenen dağıtımlar, belirli makineler kümesinden çok daha az hata yapmaya açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="2ad27-120">Buna karşılık, karmaşık dağıtımları üzerinde hızlı bir döngü sağlayan dağıtımları daha hızlı ve daha güvenilir yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="2ad27-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="2ad27-121">Yapılandırmaları aracılığıyla paylaşılabilir ayrıca [PowerShell Galerisi](https://powershellgallery.com) yaygın senaryolar ve en iyi anlamına zaten var olabilecek için yapılması gereken çalışmayı.</span><span class="sxs-lookup"><span data-stu-id="2ad27-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="2ad27-122">Desired State Configuration ve DevOps</span><span class="sxs-lookup"><span data-stu-id="2ad27-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="2ad27-123">DSC ile tasarlanmış [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) göz önünde bulundurun, kişileri, süreçleri ve hızlı dağıtım ve yineleme izin araçları birleşimi odaklanmış iç veya dış değeri son kullanıcılara sunmaya.</span><span class="sxs-lookup"><span data-stu-id="2ad27-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="2ad27-124">Geliştiriciler kendi yapılandırma gereksinimleri kodlama, kaynak denetimine bu yapılandırmayı kontrol edin ve işlem ekipleri bir ortam tanımlayabilme tek bir yapılandırma kolayca kod hataya Git gerek kalmadan dağıtabilirsiniz el ile gerçekleştirilen işlemleri.</span><span class="sxs-lookup"><span data-stu-id="2ad27-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="2ad27-125">Yapılandırmalarıdır ayrıca [verilerle](../configurations/configData.md), kolaylaştırır tanımlamak ve geliştirici müdahalesi olmadan ortamları değiştirmek ops için.</span><span class="sxs-lookup"><span data-stu-id="2ad27-125">Configurations are also [data-driven](../configurations/configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on-premises-and-off-premises"></a><span data-ttu-id="2ad27-126">Şirket içi ve şirket dışı Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="2ad27-126">Desired State Configuration On-Premises and Off-Premises</span></span>
<span data-ttu-id="2ad27-127">DSC, hem şirket içi hem de kapalı içi dağıtımlarını yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="2ad27-128">Şirket içi çözümler için DSC sahip bir [çekme sunucusu](../pull-server/pullServer.md) makinelerin yönetimini merkezileştirme ve bunların durumunu raporlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-128">For on-premise solutions, DSC has a [pull server](../pull-server/pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="2ad27-129">Bulut çözümleri için DSC Windows kullanılabilir her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="2ad27-130">Azure Desired State Configuration ' üzerinde gibi yerleşik belirli teklifleri de vardır [Azure Otomasyonu](https://azure.microsoft.com/en-us/documentation/services/automation/), DSC raporlama merkezileştirir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="2ad27-131">DSC ve uyumluluk</span><span class="sxs-lookup"><span data-stu-id="2ad27-131">DSC and Compatibility</span></span>

<span data-ttu-id="2ad27-132">DSC, Windows Server 2012 R2'de kullanılmaya başlanan olsa da, alt düzey işletim sistemleri için Windows Management Framework (WMF) paketi aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="2ad27-133">WMF hakkında daha fazla bilgi bulunabilir [PowerShell giriş sayfası](/powershell/).</span><span class="sxs-lookup"><span data-stu-id="2ad27-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="2ad27-134">DSC, Linux'ı yönetmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2ad27-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="2ad27-135">Daha fazla bilgi için [Linux için DSC ile çalışmaya başlama](../getting-started/lnxGettingStarted.md).</span><span class="sxs-lookup"><span data-stu-id="2ad27-135">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>
