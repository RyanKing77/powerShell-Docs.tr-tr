---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çekme sunucusu en iyi uygulamaları
ms.openlocfilehash: da67f8fd793878b097ffb260afad0fcf5c69bb04
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405876"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="63e9c-103">Çekme sunucusu en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="63e9c-103">Pull server best practices</span></span>

<span data-ttu-id="63e9c-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="63e9c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63e9c-105">Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="63e9c-106">Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="63e9c-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="63e9c-107">Özet: Bu belge, işlem ve çözüm için hazırlama mühendislerine yardımcı olmak için genişletilebilirlik içerecek şekilde yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="63e9c-108">En iyi müşteriler tarafından tanımlandığı gibi sağlaması gerekir ve ardından önerileri gelecekte kullanıma yönelik iş ve kararlı kabul emin olmak için ürün ekibi tarafından doğrulanması ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="63e9c-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="63e9c-109">Belge bilgileri</span><span class="sxs-lookup"><span data-stu-id="63e9c-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="63e9c-110">Yazar</span><span class="sxs-lookup"><span data-stu-id="63e9c-110">Author</span></span> | <span data-ttu-id="63e9c-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="63e9c-111">Michael Greene</span></span>
<span data-ttu-id="63e9c-112">Gözden Geçirenler</span><span class="sxs-lookup"><span data-stu-id="63e9c-112">Reviewers</span></span> | <span data-ttu-id="63e9c-113">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="63e9c-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="63e9c-114">Yayımlanan</span><span class="sxs-lookup"><span data-stu-id="63e9c-114">Published</span></span> | <span data-ttu-id="63e9c-115">Nisan 2015</span><span class="sxs-lookup"><span data-stu-id="63e9c-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="63e9c-116">Özet</span><span class="sxs-lookup"><span data-stu-id="63e9c-116">Abstract</span></span>

<span data-ttu-id="63e9c-117">Bu belge, herhangi bir Windows PowerShell Desired State Configuration çekme sunucusu uygulaması için planlama için resmi bir Rehber sunmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="63e9c-118">Bir çekme sunucusu dağıtmak için yalnızca dakika süren basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="63e9c-119">Bu belgede bir dağıtımda kullanılan teknik nasıl yapılır kılavuzları sunar ancak bu belgenin en iyi yöntemler ve dağıtmadan önce dikkat etmeniz gerekenler için başvuru değerdir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="63e9c-120">Okuyucular DSC temel olarak bilindiğini olmalıdır ve bileşenlerini açıklamak için kullanılan terimler, DSC dağıtımında yer alır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="63e9c-121">Daha fazla bilgi için [Windows PowerShell Desired State Configuration genel](/powershell/dsc/overview) konu.</span><span class="sxs-lookup"><span data-stu-id="63e9c-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview)  topic.</span></span>
<span data-ttu-id="63e9c-122">DSC bulut temposunda gelişmesinin beklendiği gibi çekme sunucusu da dahil olmak üzere temel alınan teknoloji geliştirilebilen ve yeni özellikleri tanıtmak için de beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="63e9c-123">Bu belgenin önceki sürümlerine başvuruları ve başvurular forward-looking tasarımı teşvik etmek için gelecekteki görünümlü çözümler sağlayan ek bir sürüm tablosunu içerir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="63e9c-124">Bu belgenin iki ana bölümü:</span><span class="sxs-lookup"><span data-stu-id="63e9c-124">The two major sections of this document:</span></span>

- <span data-ttu-id="63e9c-125">Yapılandırma planlaması</span><span class="sxs-lookup"><span data-stu-id="63e9c-125">Configuration Planning</span></span>
- <span data-ttu-id="63e9c-126">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="63e9c-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="63e9c-127">Windows Management Framework sürümleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="63e9c-128">Bu belgedeki bilgiler için Windows Management Framework 5.0 uygulamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="63e9c-129">WMF 5.0 dağıtmak için gerekli değildir ve bu belgenin odak olduğu bir çekme sunucusu sürüm 5.0 işletim olsa da.</span><span class="sxs-lookup"><span data-stu-id="63e9c-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="63e9c-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="63e9c-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="63e9c-131">Desired State Configuration ' nı (DSC), ortak bilgi modeli (CIM) tanımlamak için Yönetilen Nesne Biçimi (MOF) adlı bir endüstri sözdizimini kullanarak dağıtma ve yönetme, yapılandırma verilerini sağlayan bir yönetim platformudur.</span><span class="sxs-lookup"><span data-stu-id="63e9c-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="63e9c-132">Bu standartlar, geliştirme platformları arasında Linux da dahil olmak üzere daha fazla ve ağ donanım işletim sistemleri için açık Yönetim Altyapısı (OMI) açık kaynaklı proje yok.</span><span class="sxs-lookup"><span data-stu-id="63e9c-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="63e9c-133">Daha fazla bilgi için [MOF belirtimlerine bağlama DMTF sayfa](https://www.dmtf.org/standards/cim), ve [OMI belgeler ve kaynak](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="63e9c-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="63e9c-134">Windows PowerShell Desired State Configuration oluşturmak ve bildirim temelli yapılandırmalar yönetmek için kullanabileceğiniz için dil uzantıları sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="63e9c-135">Çekme sunucusu rolü</span><span class="sxs-lookup"><span data-stu-id="63e9c-135">Pull server role</span></span>

<span data-ttu-id="63e9c-136">Hedef düğümler için erişilebilir olacak yapılandırmaları depolamak için merkezi bir hizmete bir çekme sunucusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="63e9c-137">Çekme sunucusu rolü, bir Web sunucusu örneğine veya bir SMB dosya paylaşımı dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="63e9c-138">Web sunucusu özelliği, bir OData arabirimi içerir ve yapılandırmaları uygulandıkça başarı veya başarısızlık onayı geri bildirmek hedef düğümler için özellikleri isteğe bağlı olarak içerebilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="63e9c-139">Bu işlevsellik, ortamlarında yararlıdır bulunduğu çok sayıda hedef düğümleri.</span><span class="sxs-lookup"><span data-stu-id="63e9c-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="63e9c-140">Son yapılandırmayı çekme sunucusuna işaret etmek için bir hedef düğümü (bir istemci olarak da bilinir) yapılandırdıktan sonra verileri ve gerekli tüm betikleri indirilen uygulanan ve.</span><span class="sxs-lookup"><span data-stu-id="63e9c-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="63e9c-141">Bu tek seferlik bir dağıtım veya değişiklik uygun ölçekte yönetmek için önemli bir varlık da çekme sunucusu olmasını sağlayan yeniden tekrarlanan bir iş olarak gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="63e9c-142">Daha fazla bilgi için [Windows PowerShell Desired State Configuration çekme sunucuları](/powershell/dsc/pullServer) ve</span><span class="sxs-lookup"><span data-stu-id="63e9c-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) and</span></span>

<span data-ttu-id="63e9c-143">[Gönderme ve çekme yapılandırma modlarından](/powershell/dsc/pullServer).</span><span class="sxs-lookup"><span data-stu-id="63e9c-143">[Push and Pull Configuration Modes](/powershell/dsc/pullServer).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="63e9c-144">Yapılandırma planlaması</span><span class="sxs-lookup"><span data-stu-id="63e9c-144">Configuration planning</span></span>

<span data-ttu-id="63e9c-145">Tüm kurumsal yazılım dağıtımı için doğru mimari planlamanıza yardımcı olacak ve dağıtımını tamamlamak için gereken adımları için hazırlıklı olmak için önceden toplanan bilgileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="63e9c-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="63e9c-146">Aşağıdaki bölümler, hazırlama ve büyük olasılıkla önceden yapılması gereken Kurumsal bağlantıları ile ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="63e9c-147">Yazılım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-147">Software requirements</span></span>

<span data-ttu-id="63e9c-148">Bir çekme sunucusu dağıtımını DSC hizmeti özelliği Windows Server'ın gerektirir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="63e9c-149">Bu özellik, Windows Server 2012'de kullanıma sunulmuştur ve devam eden yayınlar Windows Management Framework (WMF) güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="63e9c-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="63e9c-150">Yazılım yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-150">Software downloads</span></span>

<span data-ttu-id="63e9c-151">Windows Update'ten en yeni içerik yüklemenin yanı sıra, bir DSC çekme sunucusuna dağıtmak için en iyi uygulama olarak kabul iki yüklemeleri vardır: Windows Management Framework'ün en son sürümünü ve otomatik hale getirmek için DSC modülünü sunucu sağlama çekin.</span><span class="sxs-lookup"><span data-stu-id="63e9c-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="63e9c-152">WMF</span><span class="sxs-lookup"><span data-stu-id="63e9c-152">WMF</span></span>

<span data-ttu-id="63e9c-153">Windows Server 2012 R2 DSC hizmeti adlı bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="63e9c-154">DSC hizmeti özelliğini destekleyen OData uç noktasını ikili dosyaları dahil olmak üzere çekme sunucusu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="63e9c-155">WMF Windows Server'a dahil edilmiştir ve Windows Server sürümleri arasında bir Çevik temposu güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="63e9c-156">[WMF 5.0 yeni sürümlerini](https://www.microsoft.com/en-us/download/details.aspx?id=54616) DSC hizmeti özelliği için güncelleştirmeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="63e9c-157">Bu nedenle, buna WMF'ın en son sürümünü indirin ve yayın DSC hizmeti özelliği için bir güncelleştirme içerip içermediğini belirlemek için sürüm notlarını gözden geçirmek için en iyi yöntem var.</span><span class="sxs-lookup"><span data-stu-id="63e9c-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="63e9c-158">Bir güncelleştirme veya senaryo için Tasarım Durumu kararlı veya Deneysel olarak listelenip listelenmediğini gösterir sürüm notlarını bölümünü de gözden geçirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="63e9c-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="63e9c-159">Tek tek özellikler kararlı bildirilebilir bir Çevik sürüm döngüsü için izin vermek için özellik gösteren WMF önizlemede bile yayımlanır ancak bir üretim ortamında kullanılmak üzere hazırdır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="63e9c-160">Tarihsel olarak güncelleştirilip güncelleştirilmediğini diğer özellikler tarafından WMF sürümleri (daha fazla ayrıntı için WMF sürüm notlarına bakın):</span><span class="sxs-lookup"><span data-stu-id="63e9c-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="63e9c-161">Windows PowerShell Windows PowerShell Tümleşik komut dosyası</span><span class="sxs-lookup"><span data-stu-id="63e9c-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="63e9c-162">Ortamı (ISE) Windows PowerShell Web Hizmetleri (Yönetim OData</span><span class="sxs-lookup"><span data-stu-id="63e9c-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="63e9c-163">IIS uzantısı) Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="63e9c-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="63e9c-164">Windows Uzaktan Yönetim (WinRM) Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="63e9c-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="63e9c-165">DSC kaynak</span><span class="sxs-lookup"><span data-stu-id="63e9c-165">DSC resource</span></span>

<span data-ttu-id="63e9c-166">Bir çekme sunucusu dağıtımı, sağlama hizmetini kullanarak bir DSC yapılandırma betiği tarafından basitleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="63e9c-167">Bu belge, üretime hazır sunucu düğümünü dağıtmak için kullanılan yapılandırma betiklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="63e9c-168">Yapılandırma komut dosyaları kullanmak için bir DSC modülünü diğer bir deyişle gereklidir Windows Server'a dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="63e9c-169">Gerekli modül adı **xPSDesiredStateConfiguration**, DSC kaynağı içeren **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="63e9c-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="63e9c-170">XPSDesiredStateConfiguration modülü indirilebilir [burada](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="63e9c-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="63e9c-171">Kullanım `Install-Module` cmdlet'inden **PowerShellGet** modülü.</span><span class="sxs-lookup"><span data-stu-id="63e9c-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="63e9c-172">**PowerShellGet** modül modülünü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="63e9c-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="63e9c-173">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-173">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-174">Windows Server 2012 R2 için yükleme dosyalarına erişimi?</span><span class="sxs-lookup"><span data-stu-id="63e9c-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="63e9c-175">Dağıtım ortamı WMF ve modülü çevrimiçi galeriden indirmek için Internet erişimi gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="63e9c-176">Nasıl işletim sistemi yüklendikten sonra en son güvenlik güncelleştirmelerini yükler mi?</span><span class="sxs-lookup"><span data-stu-id="63e9c-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="63e9c-177">Ortam, güncelleştirmeleri almak için Internet erişimi gerekir veya yerel bir Windows Server Update Services (WSUS) sunucu gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="63e9c-178">Çevrimdışı ekleme aracılığıyla güncelleştirmeleri içeren Windows Server yükleme dosyalarını erişim zorunda mıyım?</span><span class="sxs-lookup"><span data-stu-id="63e9c-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="63e9c-179">Donanım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-179">Hardware requirements</span></span>

<span data-ttu-id="63e9c-180">Çekme sunucusuna dağıtımlar, sanal ve fiziksel sunucularda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="63e9c-181">Çekme sunucusu boyutlandırma gereksinimlerini, Windows Server 2012 R2 gereksinimleri ile hizalar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="63e9c-182">CPU: 1,4 GHz 64 bit işlemci bellek: 512 MB Disk alanı: 32 GB ağ: Gigabit Ethernet Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="63e9c-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="63e9c-183">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-183">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-184">Fiziksel donanım üzerinde veya bir sanallaştırma platformunda dağıtacak mısınız?</span><span class="sxs-lookup"><span data-stu-id="63e9c-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="63e9c-185">Hedef ortamınız için yeni bir sunucu isteği işlemi nedir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="63e9c-186">Bir sunucu kullanılabilir hale gelmesi için ortalama amortisman süresini nedir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="63e9c-187">Hangi boyutu sunucu, ister?</span><span class="sxs-lookup"><span data-stu-id="63e9c-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="63e9c-188">Hesaplar</span><span class="sxs-lookup"><span data-stu-id="63e9c-188">Accounts</span></span>

<span data-ttu-id="63e9c-189">Bir çekme sunucusu örneği dağıtmak için hizmet hesabı gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="63e9c-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="63e9c-190">Bununla birlikte, burada Web sitesi bir yerel kullanıcı hesabının bağlamında çalıştırabilirsiniz senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="63e9c-191">Örneğin, bir gereksinimi varsa Web sitesi içeriğini ve Windows Server veya depolama paylaşımı barındıran cihaz için bir depolama paylaşmak erişimi olmayan etki alanına katılmış.</span><span class="sxs-lookup"><span data-stu-id="63e9c-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="63e9c-192">DNS kayıtları</span><span class="sxs-lookup"><span data-stu-id="63e9c-192">DNS records</span></span>

<span data-ttu-id="63e9c-193">Bir çekme sunucusu ile çalışacak şekilde istemciler yapılandırırken kullanılacak bir sunucu adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="63e9c-194">Test ortamları genellikle sunucusu konak adı kullanılır veya sunucunun IP adresini DNS ad çözümleme mevcut değilse kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="63e9c-195">Üretim ortamlarında ya da bir laboratuvar ortamında Üretim dağıtımı temsil etmesi hedeflenen bir DNS CNAME kaydı oluşturmak için en iyi yöntem olacaktır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="63e9c-196">Bir DNS CNAME için konak (A) kaydı başvurmak için bir diğer ad oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="63e9c-197">Ek ad kaydı amacı esneklik bir değişiklik gelecekte gerekli olmalıdır artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="63e9c-198">CNAME değişikliği bir çekme sunucusu değiştirmek veya ek çekme sunucuları ekleme gibi sunucu ortamı için istemci yapılandırması için karşılık gelen değişiklik yapılması gerekmez, istemci yapılandırması yalıtmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="63e9c-199">DNS kaydı için bir ad seçerken çözüm mimarisini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="63e9c-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="63e9c-200">Kullanarak Yük Dengelemesi, trafik HTTPS üzerinden güvenli hale getirmek için kullanılan sertifikanın DNS kayıt olarak aynı adı paylaşan gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="63e9c-201">Senaryo</span><span class="sxs-lookup"><span data-stu-id="63e9c-201">Scenario</span></span> |<span data-ttu-id="63e9c-202">En iyi uygulama</span><span class="sxs-lookup"><span data-stu-id="63e9c-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="63e9c-203">Sınama Ortamı</span><span class="sxs-lookup"><span data-stu-id="63e9c-203">Test Environment</span></span> |<span data-ttu-id="63e9c-204">Planlı bir üretim ortamına mümkünse yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63e9c-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="63e9c-205">Bir sunucu ana bilgisayar adı, basit yapılandırmaları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="63e9c-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="63e9c-206">DNS kullanılamıyorsa, bir IP adresi yerine ana bilgisayar adı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="63e9c-207">Tek düğümlü dağıtım</span><span class="sxs-lookup"><span data-stu-id="63e9c-207">Single Node Deployment</span></span> |<span data-ttu-id="63e9c-208">Sunucu ana bilgisayar adı için bir DNS CNAME kaydı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63e9c-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="63e9c-209">Daha fazla bilgi için [yapılandırma DNS hepsini bir kez deneme Windows Server'da](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="63e9c-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="63e9c-210">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-210">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-211">Oluşturulan ve değiştirilen DNS kayıtları kişiye kimin biliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="63e9c-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="63e9c-212">DNS kaydı için bir istek için ortalama bir döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="63e9c-213">Sunucular için statik bir ana bilgisayar (A) kayıt isteği gerekiyor mu?</span><span class="sxs-lookup"><span data-stu-id="63e9c-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="63e9c-214">Ne bir CNAME ister?</span><span class="sxs-lookup"><span data-stu-id="63e9c-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="63e9c-215">Gerekli olursa, ne tür yük dengeleme çözümü, yararlanacaktır?</span><span class="sxs-lookup"><span data-stu-id="63e9c-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="63e9c-216">(Ayrıntılar için Yük Dengeleme başlıklı bölümüne bakın)</span><span class="sxs-lookup"><span data-stu-id="63e9c-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="63e9c-217">Ortak anahtar altyapısı</span><span class="sxs-lookup"><span data-stu-id="63e9c-217">Public Key Infrastructure</span></span>

<span data-ttu-id="63e9c-218">Çoğu kuruluş, ağ trafiğini, özellikle nasıl sunucuları yapılandırılır, bu gibi hassas veriler içeren trafiği gerekir doğrulandı ve/veya aktarım sırasında şifrelenir, bugün gerektirir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="63e9c-219">Kolaylaştıran HTTP kullanarak bir çekme sunucusu dağıtmayı mümkün olmakla birlikte istemci isteklerinde metni silin, HTTPS kullanan güvenli trafiği için en iyi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="63e9c-220">Hizmet, DSC kaynak parametreleri kümesini kullanarak HTTPS kullanacak şekilde yapılandırılabilir **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="63e9c-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="63e9c-221">Çekme sunucusu için HTTPS trafiğinin güvenliğini sağlamak için sertifika gereksinimleri, herhangi bir HTTPS web sitesini güvenli hale getirme değerinden farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="63e9c-222">**Web sunucusu** şablon bir Windows Server Sertifika Hizmetleri'nde gerekli yeteneklerin karşılar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="63e9c-223">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-223">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-224">Sertifika isteklerini otomatik olarak yapılmaz, kimin bir sertifika isteklerini başvurun gerekecek mi?</span><span class="sxs-lookup"><span data-stu-id="63e9c-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="63e9c-225">İstek için ortalama bir döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="63e9c-226">Nasıl sertifika dosyası için aktarılır?</span><span class="sxs-lookup"><span data-stu-id="63e9c-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="63e9c-227">Nasıl sertifika özel anahtarını size aktarılır?</span><span class="sxs-lookup"><span data-stu-id="63e9c-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="63e9c-228">Varsayılan zaman aşımı süresi ne kadardır?</span><span class="sxs-lookup"><span data-stu-id="63e9c-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="63e9c-229">Sertifika adı için kullanabileceğiniz çekme sunucusu ortamı için bir DNS adı kapatılan?</span><span class="sxs-lookup"><span data-stu-id="63e9c-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="63e9c-230">Bir mimari seçme</span><span class="sxs-lookup"><span data-stu-id="63e9c-230">Choosing an architecture</span></span>

<span data-ttu-id="63e9c-231">Bir çekme sunucusu, IIS veya bir SMB dosya paylaşımında barındırılan ya da bir web hizmeti kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="63e9c-232">Çoğu durumda, web hizmeti seçeneği daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="63e9c-233">SMB trafiği genellikle filtrelendiğine veya ağlar arasında engellenen ise ağ sınırlarını geçmesini HTTPS trafiği için sık karşılaşılan bir durum değil.</span><span class="sxs-lookup"><span data-stu-id="63e9c-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="63e9c-234">Web hizmeti ayrıca uyumluluk sunucu veya istemciler merkezi görünüm için bir sunucuya geri durumu raporlamak için bir mekanizma sağlar. bir Web raporlama Yöneticisi (Bu belgenin ileriki bir sürümde ele alınması için iki konuları) içerecek şekilde seçeneği de sunar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="63e9c-235">SMB, bir web sunucusu rolü istenmeyen olun diğer ortam gereksinimleri yanı sıra, burada bir web sunucusu kullanılmadı ilke belirleyen ortamları için bir seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="63e9c-236">İmzalama ve trafiği şifreleme gereksinimlerini değerlendirmek her iki durumda da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63e9c-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="63e9c-237">HTTPS, SMB imzalama ve IPSec ilkelerini dikkate değer tüm seçenekler değildir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="63e9c-238">Yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="63e9c-238">Load balancing</span></span>

<span data-ttu-id="63e9c-239">Web hizmetiyle etkileşim kurmanın istemciler, tek bir yanıtta döndürülen bilgileri için bir istek olması.</span><span class="sxs-lookup"><span data-stu-id="63e9c-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="63e9c-240">Yük Dengeleme oturumları zaman içinde herhangi bir noktada tek bir sunucuda tutulur emin olmak için platform için gerekli olmadığından sıralı istek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="63e9c-241">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-241">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-242">Yükü sunucular arasında trafiği Dengeleme için çözümün ne kullanılacak mı?</span><span class="sxs-lookup"><span data-stu-id="63e9c-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="63e9c-243">Yeni bir yapılandırma için bir cihaz eklemek için bir istek sürecek olan bir donanım yük dengeleyicisi kullanıyorsanız?</span><span class="sxs-lookup"><span data-stu-id="63e9c-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="63e9c-244">Yeni bir yük yapılandırmak bir istek için ortalama bir döngü nedir, web hizmeti dengeli?</span><span class="sxs-lookup"><span data-stu-id="63e9c-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="63e9c-245">Hangi bilgilerin istek için gerekli olacak mı?</span><span class="sxs-lookup"><span data-stu-id="63e9c-245">What information will be required for the request?</span></span>|
<span data-ttu-id="63e9c-246">Yük dengelemeden sorumlu takım, işleyecek veya ek IP istemek gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="63e9c-247">Gerekli DNS kayıtlarını var ve bu, yük dengeleme çözümü yapılandırmak için sorumlu ekip tarafından gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="63e9c-248">Yük Dengeleme çözümü PKI cihaz tarafından ele alınması gerekmez veya hiçbir oturum gereksinimleri var olduğu sürece, HTTPS trafiği Dengeleme yükleyebilir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="63e9c-249">Yapılandırmaları ve modülleri çekme sunucusunda hazırlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="63e9c-250">Yapılandırma planlaması kapsamında, hangi DSC hakkında modülleri ve yapılandırmaları çekme sunucusu tarafından barındırılacak düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="63e9c-251">Yapılandırmayı planlamak amacıyla hazırlamak ve içeriği bir çekme sunucusuna dağıtmak nasıl temel bir anlayış sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="63e9c-252">İleride bu bölümde genişletilmiş ve DSC çekme sunucusu için bir işlemler Kılavuzu'nda dahil.</span><span class="sxs-lookup"><span data-stu-id="63e9c-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="63e9c-253">Otomasyon ile zaman içinde modülleri ve yapılandırmaları yönetmek için günlük işlem kılavuzu ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="63e9c-254">DSC modülleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-254">DSC modules</span></span>

<span data-ttu-id="63e9c-255">Bir yapılandırma isteyen istemcilerin gerekli DSC modülleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="63e9c-256">Bir çekme sunucusu isteğe bağlı bir dağıtım istemcilere DSC modüllerinin otomatikleştirmek için bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="63e9c-257">İlk kez, belki de bir laboratuvar veya kavram kanıtı olarak bir çekme sunucusu dağıtıyorsanız, büyük olasılıkla PowerShell Galerisi gibi genel depolar veya PowerShell.org GitHub depoları DSC modüller için kullanılabilir olan DSC modülleri bağlıdır oluşturacağınız .</span><span class="sxs-lookup"><span data-stu-id="63e9c-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="63e9c-258">Bile güvenilir çevrimiçi kaynakları için PowerShell Galerisi gibi genel bir depodan indirilen herhangi bir modülü kişi tarafından PowerShell deneyimini ve modülleri olduğu ortamın bilgi ile incelenmelidir olduğunu unutmamak önemlidir Üretim ortamında kullanılan önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="63e9c-259">Bu görevi tamamlanırken herhangi ek belgeler ve örnek betikler gibi kaldırılabilir modül yükünde denetlemek için zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="63e9c-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="63e9c-260">Modüller, sunucudan istemciye ağ üzerinden indirilecek olduğunda bu ilk talebinde istemci başına ağ bant genişliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="63e9c-261">Her modülü, belirli bir biçimde, modül yükünü içeren ModuleName_Version.zip adında bir ZIP dosyasına paketlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="63e9c-262">Dosyayı sunucuya kopyalandıktan sonra bir sağlama toplamı dosyasına oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="63e9c-263">İstemcilerin sunucuya bağlandığınızda, sağlama toplamını yayımlandıktan sonra DSC modülünün içerik değiştirilmedi doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="63e9c-264">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-264">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-265">Bir test veya Laboratuvar ortamına planlıyorsanız hangi senaryolarını doğrulamak için anahtar misiniz?</span><span class="sxs-lookup"><span data-stu-id="63e9c-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="63e9c-266">İhtiyacınız olan her şey karşılamak için kaynakları içeren genel olarak kullanılabilir modüllerin vardır veya kendi kaynaklarını Yazar gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="63e9c-267">Ortamınızı ortak modüller almak için Internet erişimi gerekir?</span><span class="sxs-lookup"><span data-stu-id="63e9c-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="63e9c-268">Kimin DSC modülleri gözden geçirmek için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="63e9c-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="63e9c-269">Bir üretim ortamında planlıyorsanız ne yerel bir depo DSC modülleri depolamak için kullanacağınız?</span><span class="sxs-lookup"><span data-stu-id="63e9c-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="63e9c-270">Merkezi bir ekip, uygulama ekipleri DSC modüllerden kabul eder?</span><span class="sxs-lookup"><span data-stu-id="63e9c-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="63e9c-271">Hangi işlem olacak mı?</span><span class="sxs-lookup"><span data-stu-id="63e9c-271">What will the process be?</span></span>|
<span data-ttu-id="63e9c-272">Paketleme, kopyalama ve üretime hazır DSC modüller için sağlama toplamı sunucusuna kaynak deponuzdan oluşturma otomatik hale?</span><span class="sxs-lookup"><span data-stu-id="63e9c-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="63e9c-273">Takım, Otomasyon platformu da yönetmekten sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="63e9c-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="63e9c-274">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="63e9c-274">DSC configurations</span></span>

<span data-ttu-id="63e9c-275">Bir çekme sunucusu amacı, DSC yapılandırmaları istemci düğümlerine dağıtmak için merkezi bir mekanizma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="63e9c-276">Yapılandırma sunucusunda MOF belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="63e9c-277">Her belgenin benzersiz bir ile adlandırılacağını **GUID**.</span><span class="sxs-lookup"><span data-stu-id="63e9c-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="63e9c-278">İstemciler, bir çekme sunucusuna bağlanmak üzere yapılandırıldığında, kendisine de verilir **GUID** istek yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="63e9c-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="63e9c-279">Bu sistem yapılandırmaları tarafından başvuru **GUID** genel benzersizliği garanti eder ve düğüm başına ya da kapsayan olması gereken birçok sunucusu rolü yapılandırması ayrıntı düzeyi içeren bir yapılandırma uygulanabilir olduğunu esnektir aynı yapılandırmaları.</span><span class="sxs-lookup"><span data-stu-id="63e9c-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="63e9c-280">GUID'ler</span><span class="sxs-lookup"><span data-stu-id="63e9c-280">Guids</span></span>

<span data-ttu-id="63e9c-281">İçin yapılandırma planlaması **GUID'leri** ek dikkat çekme sunucu dağıtımı düşünürken, büyük.</span><span class="sxs-lookup"><span data-stu-id="63e9c-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="63e9c-282">İşlemek nasıl özel bir gereksinimi yoktur **GUID'leri** ve büyük olasılıkla her ortam için benzersiz bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="63e9c-283">İşlem basitten için karmaşık değişebilir: merkezi olarak depolanan bir CSV dosyası, basit bir SQL tablosunu, bir CMDB veya başka bir aracı ya da yazılım çözümü ile tümleştirme gerektiren karmaşık bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="63e9c-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="63e9c-284">İki genel yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="63e9c-284">There are two general approaches:</span></span>

- <span data-ttu-id="63e9c-285">**Sunucu başına GUID'leri atama** — bir ölçü her sunucu yapılandırması ayrı ayrı kontrol güvence sağlar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="63e9c-286">Bu güncelleştirmeleri etrafında duyarlılık düzeyi sağlar ve bazı sunucularla ortamlarda da çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="63e9c-287">**GUID'ler her sunucu rolü atama** — web sunucuları gibi aynı işlevi gerçekleştirir tüm sunucuların gerekli yapılandırma verileri başvurmak için aynı GUID'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="63e9c-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="63e9c-288">Birçok sunucuya aynı GUID paylaşıyorsanız, yapılandırma değiştiğinde tümünün aynı anda güncelleştirilecek olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63e9c-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="63e9c-289">GUID zeka nasıl sunucularına dağıtılır ve ortamınızda yapılandırılmış hakkında sağlamaya kötü amaçlı bir eyleme sahip biri tarafından kullanılabilir çünkü, hassas verileri düşünülmesi gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="63e9c-290">Daha fazla bilgi için [güvenli bir şekilde PowerShell Desired State Configuration çekme modunda GUID'leri ayrılırken](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="63e9c-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="63e9c-291">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="63e9c-291">Planning task</span></span>|
---|
<span data-ttu-id="63e9c-292">Kimin hazır olduğunuzda, yapılandırma çekme sunucu klasörüne kopyalamak için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="63e9c-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="63e9c-293">Bir uygulama ekibi tarafından yapılandırmaları yazılmışsa ne işlemi bunları devre dışı el olacak?</span><span class="sxs-lookup"><span data-stu-id="63e9c-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="63e9c-294">Bunlar, takımlar arasında yazılmış iş olarak yapılandırmaları depolamak için bir depo özelliğinden yararlanır?</span><span class="sxs-lookup"><span data-stu-id="63e9c-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="63e9c-295">Yapılandırmaları sunucuya kopyalamak ve hazır olduğunuzda, bir sağlama toplamı oluşturma işlemini otomatik hale?</span><span class="sxs-lookup"><span data-stu-id="63e9c-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="63e9c-296">Sunucular veya roller için GUID'leri nasıl eşler ve bu depolanacağı?</span><span class="sxs-lookup"><span data-stu-id="63e9c-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="63e9c-297">Neler işlem olarak istemci makineleri yapılandırmak için kullanacağınız ve bu işlemle oluşturma ve yapılandırma, GUID'leri depolama için nasıl tümleştirilecek?</span><span class="sxs-lookup"><span data-stu-id="63e9c-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="63e9c-298">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="63e9c-298">Installation Guide</span></span>

<span data-ttu-id="63e9c-299">*Bu belgede verilen komut kararlı verilebilir. Her zaman betikleri dikkatle bir üretim ortamında yürütmeden önce gözden geçirin.*</span><span class="sxs-lookup"><span data-stu-id="63e9c-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="63e9c-300">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="63e9c-300">Prerequisites</span></span>

<span data-ttu-id="63e9c-301">Sunucunuzdaki PowerShell sürümünü doğrulamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="63e9c-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="63e9c-302">Mümkünse, Windows Management Framework'ün en son sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="63e9c-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="63e9c-303">Ardından, indirme `xPsDesiredStateConfiguration` aşağıdaki komutu kullanarak modülü.</span><span class="sxs-lookup"><span data-stu-id="63e9c-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="63e9c-304">Komut modülünü yüklemeden önce onay ister.</span><span class="sxs-lookup"><span data-stu-id="63e9c-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="63e9c-305">Yükleme ve yapılandırma betikleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-305">Installation and configuration scripts</span></span>

<span data-ttu-id="63e9c-306">DSC çekme sunucusunu dağıtmak için en iyi yöntem, bir DSC yapılandırma betiği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="63e9c-307">Bu belge her iki temel ayarları yalnızca DSC web hizmeti yapılandırırsınız ve gelişmiş bir Windows Server uçtan uca dahil olmak üzere DSC web hizmeti yapılandırdığınız ayarlar dahil olmak üzere komut dosyaları sunar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="63e9c-308">Not:  Şu anda `xPSDesiredStateConfiguation` DSC modülü, sunucunun EN-US yerel ayarını olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-308">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="63e9c-309">Windows Server 2012 için temel yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63e9c-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="63e9c-310">Windows Server 2012 R2 için Gelişmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63e9c-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="63e9c-311">Çekme sunucusu işlevselliği doğrulayın</span><span class="sxs-lookup"><span data-stu-id="63e9c-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="63e9c-312">İstemcilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63e9c-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="63e9c-313">Ek başvurular, kod parçacıkları ve örnekleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="63e9c-314">Bu örnek, test etmek için (WMF5 gerektirir) istemci bağlantısı manuel olarak başlatmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="63e9c-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="63e9c-315">[Ekle DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet'i, bir tür CNAME kaydı bir DNS bölgesine eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="63e9c-316">PowerShell işleve [sağlama toplamı ve DSC MOF yayımlama SMB çekme sunucusu oluşturma](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) gerekli sağlama toplamı otomatik olarak oluşturur ve sonra MOF yapılandırma ve sağlama toplamı dosyaları SMB çekme sunucusuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="63e9c-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="63e9c-317">Ek - anlama ODATA hizmeti verilerini dosya türleri</span><span class="sxs-lookup"><span data-stu-id="63e9c-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="63e9c-318">Bir veri dosyası, bilgi OData web hizmetini içeren bir çekme sunucusu dağıtımı sırasında oluşturulacak depolanır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="63e9c-319">Dosya türü aşağıda açıklandığı gibi işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="63e9c-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="63e9c-320">**Windows Server 2012** dosya türü her zaman .mdb olur</span><span class="sxs-lookup"><span data-stu-id="63e9c-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="63e9c-321">**Windows Server 2012 R2** yapılandırmada bir .mdb belirtilmediği sürece, dosya türü için .edb varsayılan olur</span><span class="sxs-lookup"><span data-stu-id="63e9c-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="63e9c-322">İçinde [örnek betiğini Gelişmiş](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) bir çekme sunucusu yüklemek için otomatik olarak her dosya türüne göre neden olduğu hata olasılığını önlemek için web.config dosyası ayarlarını denetlemek nasıl bir örnek de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63e9c-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
