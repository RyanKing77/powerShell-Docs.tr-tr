---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Çekme sunucusu en iyi uygulamaları
ms.openlocfilehash: 7de523ad16aee77d87ec4d3334d296997020aa19
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="c8980-103">Çekme sunucusu en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c8980-103">Pull server best practices</span></span>

><span data-ttu-id="c8980-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8980-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8980-105">Özeti: Bu belgede işlem ve çözüm için hazırlama mühendisleri yardımcı olmak için genişletilebilirlik dahil olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8980-105">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="c8980-106">En iyi yöntemler müşteriler tarafından tanımlandığı gibi sağlaması gerekir ve öneriler gelecekte kullanıma yönelik ve kararlı kabul emin olmak için ürün ekibi tarafından doğrulanmış ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="c8980-106">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="c8980-107">Belge bilgileri</span><span class="sxs-lookup"><span data-stu-id="c8980-107">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="c8980-108">Yazar</span><span class="sxs-lookup"><span data-stu-id="c8980-108">Author</span></span> | <span data-ttu-id="c8980-109">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="c8980-109">Michael Greene</span></span>
<span data-ttu-id="c8980-110">Gözden Geçirenler</span><span class="sxs-lookup"><span data-stu-id="c8980-110">Reviewers</span></span> | <span data-ttu-id="c8980-111">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="c8980-111">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="c8980-112">Yayımlanan</span><span class="sxs-lookup"><span data-stu-id="c8980-112">Published</span></span> | <span data-ttu-id="c8980-113">Nisan 2015</span><span class="sxs-lookup"><span data-stu-id="c8980-113">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="c8980-114">Özet</span><span class="sxs-lookup"><span data-stu-id="c8980-114">Abstract</span></span>

<span data-ttu-id="c8980-115">Bu belge, herkes için bir Windows PowerShell istenen durum yapılandırması çekme sunucu uygulama planlama için resmi bir kılavuz sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8980-115">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="c8980-116">Bir çekme sunucusuna dağıtmak için yalnızca dakika sürer basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="c8980-116">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="c8980-117">Bu belgede bir dağıtımda kullanılan teknik nasıl yapılır yönergeleri sunacaktır karşın, bu belgenin en iyi yöntemler ve ne dağıtmadan önce hakkında düşünmek için bir başvuru olarak değerdir.</span><span class="sxs-lookup"><span data-stu-id="c8980-117">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="c8980-118">Okuyucular DSC temel olarak bilindiğini olmalıdır ve bileşenleri açıklamak için kullanılan terimler bir DSC dağıtımda dahil edilen.</span><span class="sxs-lookup"><span data-stu-id="c8980-118">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="c8980-119">Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırması genel bakış](https://technet.microsoft.com/library/dn249912.aspx) konu.</span><span class="sxs-lookup"><span data-stu-id="c8980-119">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="c8980-120">Bulut tempoyla gelişmesi DSC beklendiği gibi çekme sunucusuna da dahil olmak üzere temel alınan teknoloji gelişmesi ve yeni özellikleri tanıtan için de beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8980-120">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="c8980-121">Bu belgenin önceki sürümlerden başvuruları ve forward-looking tasarımları teşvik eden gelecekteki görünümlü çözümler başvurular sağlayan ek bir sürüm tablosunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c8980-121">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="c8980-122">Bu belgenin iki ana bölümleri:</span><span class="sxs-lookup"><span data-stu-id="c8980-122">The two major sections of this document:</span></span>

 - <span data-ttu-id="c8980-123">Yapılandırmasını planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-123">Configuration Planning</span></span>
 - <span data-ttu-id="c8980-124">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8980-124">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="c8980-125">Windows Management Framework sürümleri</span><span class="sxs-lookup"><span data-stu-id="c8980-125">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="c8980-126">Bu belgedeki bilgiler Windows Management Framework 5.0 uygulamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8980-126">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="c8980-127">WMF 5.0 dağıtma ve çekme sunucu işletim için gerekli olmamasına karşın, sürüm 5.0, bu belgenin odak noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c8980-127">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="c8980-128">Windows PowerShell istenen durum yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c8980-128">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="c8980-129">İstenen durum Yapılandırması'nı (DSC) ortak bilgi modeli (CIM) tanımlamak için Yönetilen Nesne Biçimi (MOF) adlı bir endüstri sözdizimini kullanarak dağıtma ve yönetme yapılandırma verilerini sağlayan bir yönetim platformudur.</span><span class="sxs-lookup"><span data-stu-id="c8980-129">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="c8980-130">Bu standartlar geliştirilmesini Linux dahil olmak üzere platformları arasında daha ayrıntılı ve ağ donanım işletim sistemleri için açık Yönetim Altyapısı (OMI) açık kaynaklı proje yok.</span><span class="sxs-lookup"><span data-stu-id="c8980-130">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="c8980-131">Daha fazla bilgi için bkz: [MOF belirtimlerine bağlama DMTF sayfa](http://dmtf.org/standards/cim), ve [OMI belgeler ve kaynak](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="c8980-131">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="c8980-132">Windows PowerShell oluşturmak ve bildirim temelli yapılandırmaları yönetmek için kullanabileceğiniz ve istenen durum yapılandırması için bir dizi dil uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-132">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="c8980-133">Çekme sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="c8980-133">Pull server role</span></span>
<span data-ttu-id="c8980-134">Bir çekme sunucu hedef düğümleri için erişilebilir yapılandırmaları depolamak için merkezi bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="c8980-134">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="c8980-135">Çekme sunucu rolü, Web sunucusu örneğine veya bir SMB dosya paylaşımı dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-135">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="c8980-136">Web sunucusu özelliği bir OData arabirimi içerir ve isteğe bağlı olarak hedef düğümleri yapılandırmaları uygulanmış olarak başarı veya başarısızlık onayı geri bildirmek için özellikleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-136">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="c8980-137">Bu işlevsellik ortamlarda kullanışlıdır çok sayıda hedef düğümleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="c8980-137">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="c8980-138">En son yapılandırma çekme sunucusuna işaret etmek için (bir istemci olarak da bilinir) bir hedef düğümü yapılandırdıktan sonra veri ve tüm gerekli komut dosyalarını karşıdan uygulanan ve.</span><span class="sxs-lookup"><span data-stu-id="c8980-138">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="c8980-139">Bu bir kerelik dağıtımı veya kılan de çekme sunucunun önemli bir varlık değişikliği ölçekte yönetmek için yeniden tekrarlanan bir iş olarak meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-139">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="c8980-140">Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](https://technet.microsoft.com/library/dn249913.aspx) ve [anında iletme ve çekme yapılandırma modlarından](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="c8980-140">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="c8980-141">Yapılandırmasını planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-141">Configuration planning</span></span>

<span data-ttu-id="c8980-142">Tüm kurumsal yazılım dağıtımı için doğru mimari planlamanıza yardımcı olması için ve dağıtımını tamamlamak için gereken adımları için hazırlıklı olmak için önceden toplanan bilgileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="c8980-142">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="c8980-143">Aşağıdaki bölümler nasıl hazırlanacağı ve büyük olasılıkla önceden gerçekleşmesi gerekir kuruluş bağlantıları ile ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-143">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="c8980-144">Yazılım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="c8980-144">Software requirements</span></span>

<span data-ttu-id="c8980-145">Bir çekme sunucusuna dağıtımını DSC hizmeti özelliği Windows Server'ın gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8980-145">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="c8980-146">Bu özellik, Windows Server 2012'de sunulmuştur ve devam eden sürümleri Windows Management Framework (WMF) güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="c8980-146">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="c8980-147">Yazılım yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="c8980-147">Software downloads</span></span>

<span data-ttu-id="c8980-148">Windows Update'ten en son içerik yüklemenin yanı sıra, bir DSC çekme sunucusuna dağıtmak için en iyi yöntem olarak kabul iki yüklemeleri vardır: Windows Management Framework ve DSC modülü sunucu çekme sağlama otomatik hale getirmek için en son sürümünü.</span><span class="sxs-lookup"><span data-stu-id="c8980-148">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="c8980-149">WMF</span><span class="sxs-lookup"><span data-stu-id="c8980-149">WMF</span></span>

<span data-ttu-id="c8980-150">Windows Server 2012 R2 DSC hizmeti adlı bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="c8980-150">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="c8980-151">DSC hizmeti özelliğini destekleyen OData uç noktasını ikili dosyaları dahil olmak üzere çekme sunucu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-151">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="c8980-152">WMF Windows Server'a dahil edilmiştir ve Windows Server sürümleri arasında Çevik bir tempoyla üzerinde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-152">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="c8980-153">[WMF 5.0 yeni sürümlerini](http://aka.ms/wmf5latest) DSC servis özelliği için güncelleştirmeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-153">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="c8980-154">Bu nedenle, bu en iyi WMF en son sürümü karşıdan yüklemek ve yayın DSC hizmeti özelliği için bir güncelleştirme içerip içermediğini belirlemek için sürüm notlarını gözden geçirmek için uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="c8980-154">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="c8980-155">Bir güncelleştirme veya senaryo için Tasarım Durumu kararlı veya Deneysel olarak listelenip listelenmediğini gösteren Sürüm Notları bölümünü incelemeniz de gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8980-155">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="c8980-156">Tek tek özellikleri kararlı bildirilebilir bir Çevik yayın döngüsü için izin vermek için özellik gösterir WMF Önizleme'de serbest bile olsa bir üretim ortamında kullanılmak üzere hazırdır.</span><span class="sxs-lookup"><span data-stu-id="c8980-156">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="c8980-157">Geçmişten bu yana güncelleştirilen diğer özellikleri (bkz. daha fazla ayrıntı için WMF sürüm notları) WMF sürümleri tarafından:</span><span class="sxs-lookup"><span data-stu-id="c8980-157">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="c8980-158">Windows PowerShell Windows PowerShell Tümleşik komut dosyası</span><span class="sxs-lookup"><span data-stu-id="c8980-158">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="c8980-159">(Yönetim OData ortamı (ISE) Windows PowerShell Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c8980-159">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="c8980-160">IIS uzantısı) Windows PowerShell istenen durum yapılandırması (DSC)</span><span class="sxs-lookup"><span data-stu-id="c8980-160">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="c8980-161">Windows Uzaktan Yönetim (WinRM) Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="c8980-161">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="c8980-162">DSC kaynağı</span><span class="sxs-lookup"><span data-stu-id="c8980-162">DSC resource</span></span>

<span data-ttu-id="c8980-163">Bir çekme sunucu dağıtımı DSC yapılandırma betiği kullanarak hizmet sağlama tarafından basit hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-163">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="c8980-164">Bu belge, bir üretim hazır sunucu düğümü dağıtmak için kullanılan yapılandırma komut dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="c8980-164">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="c8980-165">Yapılandırma komut dosyaları kullanmak için DSC modülü diğer bir deyişle gereklidir Windows Server'da dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="c8980-165">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="c8980-166">Gerekli modül adı **xPSDesiredStateConfiguration**, DSC kaynağı içeren **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="c8980-166">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="c8980-167">XPSDesiredStateConfiguration modülü indirilebilir [burada](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="c8980-167">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="c8980-168">Kullanım **yükleme-Module** cmdlet'inden **PowerShellGet** modülü.</span><span class="sxs-lookup"><span data-stu-id="c8980-168">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="c8980-169">**PowerShellGet** modül için modülü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c8980-169">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="c8980-170">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-170">Planning task</span></span>|
---|
<span data-ttu-id="c8980-171">Windows Server 2012 R2 için yükleme dosyalarına erişimi?</span><span class="sxs-lookup"><span data-stu-id="c8980-171">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="c8980-172">Dağıtım ortamı WMF ve modül çevrimiçi galeriden indirmek için Internet erişimi olacak mı?</span><span class="sxs-lookup"><span data-stu-id="c8980-172">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="c8980-173">Nasıl işletim sisteminin yükledikten sonra en son güvenlik güncelleştirmelerini yükler mi?</span><span class="sxs-lookup"><span data-stu-id="c8980-173">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="c8980-174">Ortam güncelleştirmeleri almak için Internet erişimine sahip olur veya yerel bir Windows Server Update Services (WSUS) sunucusu gerekir?</span><span class="sxs-lookup"><span data-stu-id="c8980-174">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="c8980-175">Erişim zaten çevrimdışı ekleme işlemi aracılığıyla güncelleştirmeleri içeren Windows Server yükleme dosyalarını gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="c8980-175">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="c8980-176">Donanım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="c8980-176">Hardware requirements</span></span>

<span data-ttu-id="c8980-177">Çekme sunucusuna dağıtımlar, hem fiziksel hem de sanal sunucularda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c8980-177">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="c8980-178">Windows Server 2012 R2 için gereksinimlerle çekme server boyutlandırma gereksinimleri hizalayın.</span><span class="sxs-lookup"><span data-stu-id="c8980-178">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="c8980-179">CPU: 1,4 GHz 64-bit işlemci bellek: 512 MB Disk alanı: 32 GB ağ: Gigabit Ethernet Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="c8980-179">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="c8980-180">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-180">Planning task</span></span>|
---|
<span data-ttu-id="c8980-181">Fiziksel donanım üzerinde veya bir sanallaştırma platformunda dağıtacak mısınız?</span><span class="sxs-lookup"><span data-stu-id="c8980-181">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="c8980-182">Hedef ortamınız için yeni bir sunucu isteği işlemi nedir?</span><span class="sxs-lookup"><span data-stu-id="c8980-182">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="c8980-183">Bir sunucu kullanılabilir hale gelmesi için ortalama bir döngü süresi nedir?</span><span class="sxs-lookup"><span data-stu-id="c8980-183">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="c8980-184">Hangi boyutu sunucu, ister?</span><span class="sxs-lookup"><span data-stu-id="c8980-184">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="c8980-185">Hesaplar</span><span class="sxs-lookup"><span data-stu-id="c8980-185">Accounts</span></span>

<span data-ttu-id="c8980-186">Bir çekme server örneği dağıtmak için hizmet hesabı gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c8980-186">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="c8980-187">Ancak, Web sitesi yerel bir kullanıcı hesabı bağlamında çalıştırdığı senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="c8980-187">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="c8980-188">Örneğin, bir gereksinimi varsa Web sitesi içeriğini ve Windows Server veya depolama paylaşımı barındırma aygıtı için bir depolama paylaşmak erişimi olmayan etki alanına katılmış.</span><span class="sxs-lookup"><span data-stu-id="c8980-188">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="c8980-189">DNS kayıtları</span><span class="sxs-lookup"><span data-stu-id="c8980-189">DNS records</span></span>

<span data-ttu-id="c8980-190">Bir çekme sunucu ortamı ile çalışmak için istemciler yapılandırırken kullanılacak bir sunucu adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8980-190">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="c8980-191">Sınama ortamlarında sunucusu konak adı genellikle kullanılan veya DNS ad çözümlemesi kullanılamıyorsa, sunucunun IP adresini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-191">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="c8980-192">Üretim ortamlarında ya da bir laboratuvar ortamında Üretim dağıtımı temsil etmek üzere tasarlanmıştır bir DNS CNAME kaydı oluşturmak için en iyi yöntem olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-192">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="c8980-193">Bir DNS CNAME, ana bilgisayar (A) kaydı başvurmak için bir diğer ad oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-193">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="c8980-194">Ek ad kaydı amacı, bir değişiklik gelecekte gerekip gerekmeyeceğini esneklik artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-194">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="c8980-195">CNAME değişiklikler çekme sunucusunu değiştirme ya ek çekme sunucuları ekleme gibi sunucu ortamınıza karşılık gelen bir istemci yapılandırmasında değişiklik gerektirmez istemci yapılandırmasını ayırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-195">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="c8980-196">DNS kaydı için bir ad seçerken, çözüm mimarisi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c8980-196">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="c8980-197">Kullanarak Yük Dengelemesi, trafik HTTPS üzerinden güvenli hale getirmek için kullanılan sertifikanın DNS kaydı olarak aynı adı paylaşan gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="c8980-197">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="c8980-198">Senaryo</span><span class="sxs-lookup"><span data-stu-id="c8980-198">Scenario</span></span> |<span data-ttu-id="c8980-199">En iyi uygulama</span><span class="sxs-lookup"><span data-stu-id="c8980-199">Best Practice</span></span>
:---|:---
<span data-ttu-id="c8980-200">Sınama Ortamı</span><span class="sxs-lookup"><span data-stu-id="c8980-200">Test Environment</span></span> |<span data-ttu-id="c8980-201">Planlanan bir üretim ortamına mümkünse yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8980-201">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="c8980-202">Sunucu ana bilgisayar adı basit yapılandırmaları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="c8980-202">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="c8980-203">DNS kullanılamıyorsa, bir IP adresi yerine ana bilgisayar adı kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-203">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="c8980-204">Tek düğüm dağıtım</span><span class="sxs-lookup"><span data-stu-id="c8980-204">Single Node Deployment</span></span> |<span data-ttu-id="c8980-205">Sunucu ana bilgisayar adı için işaret eden bir DNS CNAME kaydı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8980-205">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="c8980-206">Daha fazla bilgi için bkz: [yapılandırma DNS hepsini bir kez Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="c8980-206">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="c8980-207">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-207">Planning task</span></span>|
---|
<span data-ttu-id="c8980-208">Kimin oluşturulan ve değiştirilen DNS kayıtları kişiye biliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="c8980-208">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="c8980-209">Bir DNS kaydı için bir istek için ortalama döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="c8980-209">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="c8980-210">Sunucular için statik ana bilgisayar (A) kayıtları isteği gerekiyor mu?</span><span class="sxs-lookup"><span data-stu-id="c8980-210">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="c8980-211">Ne bir CNAME isteyecek?</span><span class="sxs-lookup"><span data-stu-id="c8980-211">What will you request as a CNAME?</span></span>|
<span data-ttu-id="c8980-212">Gerekirse, ne tür yük dengeleme çözümü, yararlanacak olan?</span><span class="sxs-lookup"><span data-stu-id="c8980-212">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="c8980-213">(Ayrıntılar için Yük Dengeleme başlıklı bölüme bakın)</span><span class="sxs-lookup"><span data-stu-id="c8980-213">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="c8980-214">Ortak anahtar altyapısı</span><span class="sxs-lookup"><span data-stu-id="c8980-214">Public Key Infrastructure</span></span>

<span data-ttu-id="c8980-215">Çoğu kuruluş, ağ trafiğini, özellikle gibi hassas verileri yapılandırılmış sunucuları nasıl gibi içeren trafiği gerekir doğrulandı ve/veya iletim sırasında şifrelenmiş olduğunu bugün gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8980-215">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="c8980-216">Kolaylaştıran HTTP kullanarak bir çekme sunucusuna dağıtmak mümkün olmakla birlikte, istemci isteklerini metni silin, HTTPS kullanan güvenli trafiği için en iyi uygulama olur.</span><span class="sxs-lookup"><span data-stu-id="c8980-216">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="c8980-217">Hizmet DSC kaynağı bir parametre kümesi kullanarak HTTPS kullanmak üzere yapılandırılan **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="c8980-217">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="c8980-218">Çekme sunucusuna HTTPS trafiğinin güvenliğini sağlamak için sertifika gereksinimleri herhangi bir HTTPS web sitesini güvenli hale getirme daha farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="c8980-218">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="c8980-219">**Web sunucusu** şablonu bir Windows Server Sertifika Hizmetleri'nde gerekli yeteneklerin karşılar.</span><span class="sxs-lookup"><span data-stu-id="c8980-219">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="c8980-220">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-220">Planning task</span></span>|
---|
<span data-ttu-id="c8980-221">Sertifika isteklerini otomatik olarak yapılmaz, kimin sertifika isteklerini başvurun gerekecek mi?</span><span class="sxs-lookup"><span data-stu-id="c8980-221">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="c8980-222">İstek için ortalama döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="c8980-222">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="c8980-223">Nasıl sertifika dosyası için aktarılır?</span><span class="sxs-lookup"><span data-stu-id="c8980-223">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="c8980-224">Nasıl sertifika özel anahtarı size aktarılır?</span><span class="sxs-lookup"><span data-stu-id="c8980-224">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="c8980-225">Varsayılan süre uzunluğu nedir?</span><span class="sxs-lookup"><span data-stu-id="c8980-225">How long is the default expiration time?</span></span>|
<span data-ttu-id="c8980-226">Sertifika adı için kullanabileceğiniz çekme sunucu ortamı için bir DNS adı üzerinde kapatılan mi?</span><span class="sxs-lookup"><span data-stu-id="c8980-226">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="c8980-227">Bir mimari seçme</span><span class="sxs-lookup"><span data-stu-id="c8980-227">Choosing an architecture</span></span>

<span data-ttu-id="c8980-228">IIS veya bir SMB dosya paylaşımında barındırılan ya da bir web hizmetini kullanarak bir çekme sunucusuna dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-228">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="c8980-229">Çoğu durumda, web hizmeti seçeneği büyük esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-229">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="c8980-230">SMB trafiğini genellikle filtrelenmiş veya ağlar arasında engellenen ancak ağ sınırları geçiş yapmak HTTPS trafiği için seyrek değil.</span><span class="sxs-lookup"><span data-stu-id="c8980-230">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="c8980-231">Web hizmeti ayrıca uyumluluk sunucu veya istemciler merkezi görünürlük sunucusuna geri durumu raporlamak için bir mekanizma sağlar bir Web raporlama Yöneticisi (Bu belgenin sonraki bir sürümde ele alınması gereken iki konuları) içerecek şekilde seçeneği de sunar.</span><span class="sxs-lookup"><span data-stu-id="c8980-231">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="c8980-232">SMB burada İlkesi bir web sunucusu değil göstermesi belirler. ortamlar için ve bir web sunucusu rolü istenmeyen olun diğer çevre gereksinimleri için bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-232">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="c8980-233">İmzalama ve trafiği şifreleme gereksinimlerini değerlendirmek her iki durumda da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c8980-233">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="c8980-234">HTTPS, SMB imzalama ve IPSec ilkelerini dikkate değer tüm seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="c8980-234">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="c8980-235">Yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="c8980-235">Load balancing</span></span>
<span data-ttu-id="c8980-236">İstemciler web hizmetiyle etkileşmek tek bir yanıtta döndürülen bilgi isteğini olun.</span><span class="sxs-lookup"><span data-stu-id="c8980-236">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="c8980-237">Yük Dengeleyici oturumları zamanında herhangi bir noktada tek bir sunucu üzerinde saklanır emin olmak için platform için gerekli değildir sıralı istekler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c8980-237">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="c8980-238">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-238">Planning task</span></span>|
---|
<span data-ttu-id="c8980-239">Yük Dengeleme trafiğini sunucular arasında hangi çözüm kullanılacak mı?</span><span class="sxs-lookup"><span data-stu-id="c8980-239">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="c8980-240">Kimin yeni bir yapılandırma aygıt eklemek için bir istek sürer bir donanım yük dengeleyicisi kullanıyorsanız?</span><span class="sxs-lookup"><span data-stu-id="c8980-240">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="c8980-241">Yeni bir yük yapılandırmak bir istek için ortalama döngü nedir web hizmeti dengeli?</span><span class="sxs-lookup"><span data-stu-id="c8980-241">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="c8980-242">Hangi bilgilerin istek için gerekli olacak mı?</span><span class="sxs-lookup"><span data-stu-id="c8980-242">What information will be required for the request?</span></span>|
<span data-ttu-id="c8980-243">Bir ek IP istemeniz gerekir veya yük dengelemeden sorumlu takım, kullanacak mı?</span><span class="sxs-lookup"><span data-stu-id="c8980-243">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="c8980-244">Gereken DNS kayıtlarını var ve bu çözümü dengelemesini yapılandırmak için sorumlu ekibi tarafından gerekli?</span><span class="sxs-lookup"><span data-stu-id="c8980-244">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="c8980-245">PKI aygıt tarafından işlenmesi Yük Dengeleme çözümüne ihtiyacı yoktur veya hiçbir oturum gereksinimleri vardır sürece HTTPS trafiği dengelemek yükleyebilir?</span><span class="sxs-lookup"><span data-stu-id="c8980-245">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="c8980-246">Yapılandırmaları ve modülleri çekme sunucusunda hazırlama</span><span class="sxs-lookup"><span data-stu-id="c8980-246">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="c8980-247">Yapılandırma planlaması kapsamında, hangi DSC hakkında modülleri ve yapılandırmaları çekme sunucu tarafından barındırılacak düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8980-247">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="c8980-248">Yapılandırma planlama amacıyla hazırlamak ve içerik bir çekme sunucusuna dağıtmak nasıl temel bir anlayış olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c8980-248">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="c8980-249">Gelecekte, bu bölümde genişletilmiş ve DSC çekme sunucusu için bir işlemler Kılavuzu'nda bulunan.</span><span class="sxs-lookup"><span data-stu-id="c8980-249">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="c8980-250">Kılavuzu otomasyon ile zamanla modülleri ve yapılandırmaları yönetmek için günlük işlem ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-250">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="c8980-251">DSC modülleri</span><span class="sxs-lookup"><span data-stu-id="c8980-251">DSC modules</span></span>
<span data-ttu-id="c8980-252">Bir yapılandırma isteyen istemcilerin gerekli DSC modüllerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8980-252">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="c8980-253">Çekme sunucunun işlevselliğini isteğe bağlı bir dağıtım istemcilere DSC modüllerin otomatik hale getirmektir.</span><span class="sxs-lookup"><span data-stu-id="c8980-253">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="c8980-254">Bir çekme sunucusuna ilk kez, belki de bir laboratuvar veya kavram kanıtı olarak dağıtıyorsanız, büyük olasılıkla PowerShell Galerisi gibi ortak depoları veya PowerShell.org GitHub depoları DSC modülleri için kullanılabilir DSC modülleri bağımlı olmaz .</span><span class="sxs-lookup"><span data-stu-id="c8980-254">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="c8980-255">Bile güvenilen çevrimiçi kaynakları için PowerShell Galerisi gibi ortak bir depodan indirilen herhangi bir modül biri tarafından PowerShell deneyimi ve modülleri burada olacaktır ortamının bilgi gözden geçirilmesi gereken olduğunu unutmamak önemlidir Üretimde kullanılan önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8980-255">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="c8980-256">Bu görev tamamlanırken herhangi ek yükü belgeler ve örnek komut dosyaları gibi kaldırılabilir modülünde denetlemek için bir zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="c8980-256">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="c8980-257">Modülleri sunucudan istemciye ağ üzerinden yüklenen bu ilk talebinde istemcisinde başına ağ bant genişliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="c8980-257">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="c8980-258">Belirli bir biçimde, modül yükünü içeren ModuleName_Version.zip adlı bir ZIP dosyası modüllerin paketlenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8980-258">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="c8980-259">Dosyayı sunucuya kopyalandıktan sonra bir sağlama toplamı dosya oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8980-259">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="c8980-260">İstemcilerin sunucuya bağlandığınızda, sağlama toplamı yayımlandıktan sonra DSC modülü içeriğini değişmemiştir doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8980-260">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="c8980-261">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-261">Planning task</span></span>|
---|
<span data-ttu-id="c8980-262">Bir test veya laboratuvar ortamında planlıyorsanız hangi senaryolarını doğrulamak için anahtar misiniz?</span><span class="sxs-lookup"><span data-stu-id="c8980-262">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="c8980-263">Gereksinim duyduğunuz her şeyi karşılamak için kaynakları içeren genel kullanıma açık modülleri vardır veya kendi kaynaklarını Yazar gerekir?</span><span class="sxs-lookup"><span data-stu-id="c8980-263">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="c8980-264">Ortamınızı ortak modüller almak için Internet erişimi olacak mı?</span><span class="sxs-lookup"><span data-stu-id="c8980-264">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="c8980-265">Kimin DSC modülleri gözden geçirmek için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="c8980-265">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="c8980-266">Bir üretim ortamında planlıyorsanız ne yerel depo olarak DSC modülleri depolamak için kullanacaksınız?</span><span class="sxs-lookup"><span data-stu-id="c8980-266">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="c8980-267">Merkezi bir takım uygulama ekipleri DSC modüllerden kabul eder?</span><span class="sxs-lookup"><span data-stu-id="c8980-267">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="c8980-268">İşlem ne olacak?</span><span class="sxs-lookup"><span data-stu-id="c8980-268">What will the process be?</span></span>|
<span data-ttu-id="c8980-269">Paketleme, kopyalama ve üretime hazır DSC modülleri için bir sağlama toplamı sunucuya, kaynak deposu oluşturma otomatikleştirmek?</span><span class="sxs-lookup"><span data-stu-id="c8980-269">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="c8980-270">Ekibinizin Otomasyon platform de yönetmekten sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="c8980-270">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="c8980-271">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="c8980-271">DSC configurations</span></span>

<span data-ttu-id="c8980-272">Bir çekme sunucusuna amacı, istemci düğümlere DSC yapılandırmaları dağıtmak için merkezi bir düzenek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-272">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="c8980-273">Yapılandırmaları sunucuda MOF belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="c8980-273">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="c8980-274">Her bir belgenin benzersiz bir GUID ile adlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-274">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="c8980-275">İstemciler, bir çekme sunucusuna bağlanmak üzere yapılandırıldığında, bunlar GUID isteği yapılandırma için de verilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-275">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="c8980-276">Bu sistem yapılandırmaları GUID tarafından başvuru genel benzersizliği garanti eder ve düğüm başına ya da aynı yapılandırmalara sahip olması çok sayıda sunucuya yayılan bir rol yapılandırma olarak ayrıntı düzeyi içeren bir yapılandırma uygulanabilir şekilde esnektir.</span><span class="sxs-lookup"><span data-stu-id="c8980-276">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="c8980-277">GUID</span><span class="sxs-lookup"><span data-stu-id="c8980-277">GUIDs</span></span>

<span data-ttu-id="c8980-278">Yapılandırma GUID'lerini planlama ek dikkat bir çekme sunucu dağıtımı düşünürken, büyük.</span><span class="sxs-lookup"><span data-stu-id="c8980-278">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="c8980-279">GUID'ler nasıl ele alınacağını için belirli bir gereksinimi yoktur ve büyük olasılıkla her ortam için benzersiz bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="c8980-279">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="c8980-280">İşlem basitten için karmaşık değişebilir: merkezi olarak depolanmış bir CSV dosyası, basit bir SQL tablo, bir CMDB veya başka bir aracı ya da yazılım çözümü ile tümleştirme gerektiren karmaşık bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="c8980-280">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="c8980-281">İki genel yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="c8980-281">There are two general approaches:</span></span>

 - <span data-ttu-id="c8980-282">**Sunucu başına GUID'ler atama** — bir ölçü her sunucu yapılandırması ayrı ayrı kontrol güvence sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8980-282">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="c8980-283">Bu güncelleştirmeleri geçici duyarlılık düzeyi sağlar ve birkaç sunucularıyla ortamlarda da çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c8980-283">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="c8980-284">**Her sunucu rolü GUID'ler atama** — gerekli yapılandırma verileri başvurmak için web sunucuları gibi aynı işlevi gerçekleştirir tüm sunucuları aynı GUID'ye kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8980-284">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="c8980-285">Birçok sunucuları aynı GUID'ye paylaşıyorsanız, yapılandırma değiştiğinde, bunların tümünün aynı anda güncelleştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c8980-285">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="c8980-286">GUID sunucuları nasıl dağıtıldığını ve ortamınızda yapılandırıldığını hakkında Intelligence kazanmak için kötü amaçlı sahip biri tarafından işlevden çünkü, hassas verileri kabul şeydir.</span><span class="sxs-lookup"><span data-stu-id="c8980-286">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="c8980-287">Daha fazla bilgi için bkz: [güvenli bir şekilde modunda PowerShell istenen durum yapılandırması çekme GUID'ler ayırma](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="c8980-287">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="c8980-288">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="c8980-288">Planning task</span></span>|
---|
<span data-ttu-id="c8980-289">Kimin hazır olduğunuzda, yapılandırmalarında çekme sunucu klasörüne kopyalamak için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="c8980-289">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="c8980-290">Yapılandırmaları bir uygulama ekibi tarafından yazılan varsa, bunları devre dışı elle ne işlem olacak?</span><span class="sxs-lookup"><span data-stu-id="c8980-290">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="c8980-291">Bunlar, ekibin yazılan gibi yapılandırmaları depolamak için bir depo özelliğinden yararlanır?</span><span class="sxs-lookup"><span data-stu-id="c8980-291">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="c8980-292">Sunucuya yapılandırmalarını kopyalama ve hazır olduğunuzda bir sağlama toplamı oluşturma işlemini otomatikleştirmek?</span><span class="sxs-lookup"><span data-stu-id="c8980-292">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="c8980-293">Sunucuları veya rolleri için GUID'leri nasıl eşler ve bu depolanacağı?</span><span class="sxs-lookup"><span data-stu-id="c8980-293">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="c8980-294">Ne bir işlem olarak istemci makineleri yapılandırmak için kullanacağınız ve nasıl oluşturma ve yapılandırma GUID'ler saklamak için işleminizi ile tümleştirecek?</span><span class="sxs-lookup"><span data-stu-id="c8980-294">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="c8980-295">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c8980-295">Installation Guide</span></span>

<span data-ttu-id="c8980-296">*Bu belgede verilen komut kararlı örnektir. Her zaman komut dosyalarını dikkatle bir üretim ortamında yürütmeden önce gözden geçirin.*</span><span class="sxs-lookup"><span data-stu-id="c8980-296">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c8980-297">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c8980-297">Prerequisites</span></span>

<span data-ttu-id="c8980-298">PowerShell sürümü sunucunuzda doğrulamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8980-298">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="c8980-299">Mümkünse, Windows Management Framework'ün en son sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="c8980-299">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="c8980-300">Ardından, indirme `xPsDesiredStateConfiguration` aşağıdaki komutu kullanarak modülü.</span><span class="sxs-lookup"><span data-stu-id="c8980-300">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="c8980-301">Komut modülü yüklemeden önce onayınız istenir.</span><span class="sxs-lookup"><span data-stu-id="c8980-301">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="c8980-302">Yükleme ve yapılandırma komut dosyaları</span><span class="sxs-lookup"><span data-stu-id="c8980-302">Installation and configuration scripts</span></span>
-

<span data-ttu-id="c8980-303">Bir DSC çekme sunucusuna dağıtmak için en iyi yöntem DSC yapılandırma betiği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-303">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="c8980-304">Bu belgede yalnızca DSC web hizmeti yapılandırırsınız ve gelişmiş bir Windows Server uçtan uca dahil olmak üzere DSC web hizmeti yapılandırırsınız ayarları her iki temel ayarlar dahil olmak üzere komut dosyaları sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8980-304">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="c8980-305">Not: Şu anda `xPSDesiredStateConfiguation` DSC modülü server'ın EN-US yerel olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8980-305">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="c8980-306">Windows Server 2012 için temel yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8980-306">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="c8980-307">Windows Server 2012 R2 için Gelişmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8980-307">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="c8980-308">Çekme sunucu işlevselliğini doğrulayın</span><span class="sxs-lookup"><span data-stu-id="c8980-308">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="c8980-309">İstemcilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8980-309">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="c8980-310">Ek başvurular, parçacıkları ve örnekler</span><span class="sxs-lookup"><span data-stu-id="c8980-310">Additional references, snippets, and examples</span></span>

<span data-ttu-id="c8980-311">Bu örnek, test etmek için el ile (WMF5 gerektirir) bir istemci bağlantı başlatmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8980-311">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="c8980-312">[Ekle DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet türü CNAME kaydı bir DNS bölgesine eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8980-312">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="c8980-313">PowerShell işlevi [bir sağlama toplamı oluşturup yayımlama DSC MOF SMB çekme sunucusuna](http://bit.ly/1E46BhI) gerekli sağlama toplamı otomatik olarak oluşturur ve ardından MOF yapılandırma ve sağlama toplamı dosyaları SMB çekme sunucusuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c8980-313">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="c8980-314">Ek - anlama ODATA hizmeti verilerini dosya türleri</span><span class="sxs-lookup"><span data-stu-id="c8980-314">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="c8980-315">Bir veri dosyası, bilgileri bir OData web hizmetini içeren bir çekme sunucu dağıtımı sırasında oluşturmak için depolanır.</span><span class="sxs-lookup"><span data-stu-id="c8980-315">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="c8980-316">Dosya türü aşağıda açıklandığı gibi işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8980-316">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="c8980-317">**Windows Server 2012** dosya türü her zaman .mdb olacaktır</span><span class="sxs-lookup"><span data-stu-id="c8980-317">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="c8980-318">**Windows Server 2012 R2** bir .mdb yapılandırmada belirtilmediği sürece dosya türü için .edb varsayılan olur</span><span class="sxs-lookup"><span data-stu-id="c8980-318">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="c8980-319">İçinde [örnek komut dosyası Gelişmiş](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) bir çekme sunucusuna yüklemek için tüm dosya türüne göre neden hata olasılığını önlemek için web.config dosyası ayarları otomatik olarak denetlemek nasıl bir örnek da bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c8980-319">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>