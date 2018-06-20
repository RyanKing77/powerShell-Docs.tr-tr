---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Çekme sunucusu en iyi uygulamaları
ms.openlocfilehash: 1efc016df6882fa962f59dfd3e53eaa6d6b0c121
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190307"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="e1965-103">Çekme sunucusu en iyi uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e1965-103">Pull server best practices</span></span>

><span data-ttu-id="e1965-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e1965-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1965-105">Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır.</span><span class="sxs-lookup"><span data-stu-id="e1965-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e1965-106">Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="e1965-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e1965-107">Özeti: Bu belgede işlem ve çözüm için hazırlama mühendisleri yardımcı olmak için genişletilebilirlik dahil olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1965-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="e1965-108">En iyi yöntemler müşteriler tarafından tanımlandığı gibi sağlaması gerekir ve öneriler gelecekte kullanıma yönelik ve kararlı kabul emin olmak için ürün ekibi tarafından doğrulanmış ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="e1965-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="e1965-109">Belge bilgileri</span><span class="sxs-lookup"><span data-stu-id="e1965-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="e1965-110">Yazar</span><span class="sxs-lookup"><span data-stu-id="e1965-110">Author</span></span> | <span data-ttu-id="e1965-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="e1965-111">Michael Greene</span></span>
<span data-ttu-id="e1965-112">Gözden Geçirenler</span><span class="sxs-lookup"><span data-stu-id="e1965-112">Reviewers</span></span> | <span data-ttu-id="e1965-113">Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="e1965-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="e1965-114">Yayımlanan</span><span class="sxs-lookup"><span data-stu-id="e1965-114">Published</span></span> | <span data-ttu-id="e1965-115">Nisan 2015</span><span class="sxs-lookup"><span data-stu-id="e1965-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="e1965-116">Özet</span><span class="sxs-lookup"><span data-stu-id="e1965-116">Abstract</span></span>

<span data-ttu-id="e1965-117">Bu belge, herkes için bir Windows PowerShell istenen durum yapılandırması çekme sunucu uygulama planlama için resmi bir kılavuz sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1965-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="e1965-118">Bir çekme sunucusuna dağıtmak için yalnızca dakika sürer basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="e1965-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="e1965-119">Bu belgede bir dağıtımda kullanılan teknik nasıl yapılır yönergeleri sunacaktır karşın, bu belgenin en iyi yöntemler ve ne dağıtmadan önce hakkında düşünmek için bir başvuru olarak değerdir.</span><span class="sxs-lookup"><span data-stu-id="e1965-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="e1965-120">Okuyucular DSC temel olarak bilindiğini olmalıdır ve bileşenleri açıklamak için kullanılan terimler bir DSC dağıtımda dahil edilen.</span><span class="sxs-lookup"><span data-stu-id="e1965-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="e1965-121">Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırması genel bakış](https://technet.microsoft.com/library/dn249912.aspx) konu.</span><span class="sxs-lookup"><span data-stu-id="e1965-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="e1965-122">Bulut tempoyla gelişmesi DSC beklendiği gibi çekme sunucusuna da dahil olmak üzere temel alınan teknoloji gelişmesi ve yeni özellikleri tanıtan için de beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1965-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="e1965-123">Bu belgenin önceki sürümlerden başvuruları ve forward-looking tasarımları teşvik eden gelecekteki görünümlü çözümler başvurular sağlayan ek bir sürüm tablosunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e1965-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="e1965-124">Bu belgenin iki ana bölümleri:</span><span class="sxs-lookup"><span data-stu-id="e1965-124">The two major sections of this document:</span></span>

 - <span data-ttu-id="e1965-125">Yapılandırmasını planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-125">Configuration Planning</span></span>
 - <span data-ttu-id="e1965-126">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e1965-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="e1965-127">Windows Management Framework sürümleri</span><span class="sxs-lookup"><span data-stu-id="e1965-127">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="e1965-128">Bu belgedeki bilgiler Windows Management Framework 5.0 uygulamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1965-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="e1965-129">WMF 5.0 dağıtma ve çekme sunucu işletim için gerekli olmamasına karşın, sürüm 5.0, bu belgenin odak noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="e1965-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="e1965-130">Windows PowerShell istenen durum yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e1965-130">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="e1965-131">İstenen durum Yapılandırması'nı (DSC) ortak bilgi modeli (CIM) tanımlamak için Yönetilen Nesne Biçimi (MOF) adlı bir endüstri sözdizimini kullanarak dağıtma ve yönetme yapılandırma verilerini sağlayan bir yönetim platformudur.</span><span class="sxs-lookup"><span data-stu-id="e1965-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="e1965-132">Bu standartlar geliştirilmesini Linux dahil olmak üzere platformları arasında daha ayrıntılı ve ağ donanım işletim sistemleri için açık Yönetim Altyapısı (OMI) açık kaynaklı proje yok.</span><span class="sxs-lookup"><span data-stu-id="e1965-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="e1965-133">Daha fazla bilgi için bkz: [MOF belirtimlerine bağlama DMTF sayfa](http://dmtf.org/standards/cim), ve [OMI belgeler ve kaynak](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="e1965-133">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="e1965-134">Windows PowerShell oluşturmak ve bildirim temelli yapılandırmaları yönetmek için kullanabileceğiniz ve istenen durum yapılandırması için bir dizi dil uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="e1965-135">Çekme sunucu rolü</span><span class="sxs-lookup"><span data-stu-id="e1965-135">Pull server role</span></span>
<span data-ttu-id="e1965-136">Bir çekme sunucu hedef düğümleri için erişilebilir yapılandırmaları depolamak için merkezi bir hizmet sunar.</span><span class="sxs-lookup"><span data-stu-id="e1965-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="e1965-137">Çekme sunucu rolü, Web sunucusu örneğine veya bir SMB dosya paylaşımı dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="e1965-138">Web sunucusu özelliği bir OData arabirimi içerir ve isteğe bağlı olarak hedef düğümleri yapılandırmaları uygulanmış olarak başarı veya başarısızlık onayı geri bildirmek için özellikleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="e1965-139">Bu işlevsellik ortamlarda kullanışlıdır çok sayıda hedef düğümleri olduğu.</span><span class="sxs-lookup"><span data-stu-id="e1965-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="e1965-140">En son yapılandırma çekme sunucusuna işaret etmek için (bir istemci olarak da bilinir) bir hedef düğümü yapılandırdıktan sonra veri ve tüm gerekli komut dosyalarını karşıdan uygulanan ve.</span><span class="sxs-lookup"><span data-stu-id="e1965-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="e1965-141">Bu bir kerelik dağıtımı veya kılan de çekme sunucunun önemli bir varlık değişikliği ölçekte yönetmek için yeniden tekrarlanan bir iş olarak meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="e1965-142">Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](https://technet.microsoft.com/library/dn249913.aspx) ve [anında iletme ve çekme yapılandırma modlarından](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="e1965-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="e1965-143">Yapılandırmasını planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-143">Configuration planning</span></span>

<span data-ttu-id="e1965-144">Tüm kurumsal yazılım dağıtımı için doğru mimari planlamanıza yardımcı olması için ve dağıtımını tamamlamak için gereken adımları için hazırlıklı olmak için önceden toplanan bilgileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1965-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="e1965-145">Aşağıdaki bölümler nasıl hazırlanacağı ve büyük olasılıkla önceden gerçekleşmesi gerekir kuruluş bağlantıları ile ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="e1965-146">Yazılım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="e1965-146">Software requirements</span></span>

<span data-ttu-id="e1965-147">Bir çekme sunucusuna dağıtımını DSC hizmeti özelliği Windows Server'ın gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1965-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="e1965-148">Bu özellik, Windows Server 2012'de sunulmuştur ve devam eden sürümleri Windows Management Framework (WMF) güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="e1965-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="e1965-149">Yazılım yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="e1965-149">Software downloads</span></span>

<span data-ttu-id="e1965-150">Windows Update'ten en son içerik yüklemenin yanı sıra, bir DSC çekme sunucusuna dağıtmak için en iyi yöntem olarak kabul iki yüklemeleri vardır: Windows Management Framework ve DSC modülü sunucu çekme sağlama otomatik hale getirmek için en son sürümünü.</span><span class="sxs-lookup"><span data-stu-id="e1965-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="e1965-151">WMF</span><span class="sxs-lookup"><span data-stu-id="e1965-151">WMF</span></span>

<span data-ttu-id="e1965-152">Windows Server 2012 R2 DSC hizmeti adlı bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="e1965-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="e1965-153">DSC hizmeti özelliğini destekleyen OData uç noktasını ikili dosyaları dahil olmak üzere çekme sunucu işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="e1965-154">WMF Windows Server'a dahil edilmiştir ve Windows Server sürümleri arasında Çevik bir tempoyla üzerinde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="e1965-155">[WMF 5.0 yeni sürümlerini](http://aka.ms/wmf5latest) DSC servis özelliği için güncelleştirmeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-155">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="e1965-156">Bu nedenle, bu en iyi WMF en son sürümü karşıdan yüklemek ve yayın DSC hizmeti özelliği için bir güncelleştirme içerip içermediğini belirlemek için sürüm notlarını gözden geçirmek için uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e1965-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="e1965-157">Bir güncelleştirme veya senaryo için Tasarım Durumu kararlı veya Deneysel olarak listelenip listelenmediğini gösteren Sürüm Notları bölümünü incelemeniz de gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1965-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="e1965-158">Tek tek özellikleri kararlı bildirilebilir bir Çevik yayın döngüsü için izin vermek için özellik gösterir WMF Önizleme'de serbest bile olsa bir üretim ortamında kullanılmak üzere hazırdır.</span><span class="sxs-lookup"><span data-stu-id="e1965-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="e1965-159">Geçmişten bu yana güncelleştirilen diğer özellikleri (bkz. daha fazla ayrıntı için WMF sürüm notları) WMF sürümleri tarafından:</span><span class="sxs-lookup"><span data-stu-id="e1965-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="e1965-160">Windows PowerShell Windows PowerShell Tümleşik komut dosyası</span><span class="sxs-lookup"><span data-stu-id="e1965-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="e1965-161">(Yönetim OData ortamı (ISE) Windows PowerShell Web Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e1965-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="e1965-162">IIS uzantısı) Windows PowerShell istenen durum yapılandırması (DSC)</span><span class="sxs-lookup"><span data-stu-id="e1965-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="e1965-163">Windows Uzaktan Yönetim (WinRM) Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="e1965-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="e1965-164">DSC kaynağı</span><span class="sxs-lookup"><span data-stu-id="e1965-164">DSC resource</span></span>

<span data-ttu-id="e1965-165">Bir çekme sunucu dağıtımı DSC yapılandırma betiği kullanarak hizmet sağlama tarafından basit hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="e1965-166">Bu belge, bir üretim hazır sunucu düğümü dağıtmak için kullanılan yapılandırma komut dosyaları içerir.</span><span class="sxs-lookup"><span data-stu-id="e1965-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="e1965-167">Yapılandırma komut dosyaları kullanmak için DSC modülü diğer bir deyişle gereklidir Windows Server'da dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="e1965-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="e1965-168">Gerekli modül adı **xPSDesiredStateConfiguration**, DSC kaynağı içeren **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="e1965-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="e1965-169">XPSDesiredStateConfiguration modülü indirilebilir [burada](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="e1965-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="e1965-170">Kullanım **yükleme-Module** cmdlet'inden **PowerShellGet** modülü.</span><span class="sxs-lookup"><span data-stu-id="e1965-170">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="e1965-171">**PowerShellGet** modül için modülü yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e1965-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="e1965-172">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-172">Planning task</span></span>|
---|
<span data-ttu-id="e1965-173">Windows Server 2012 R2 için yükleme dosyalarına erişimi?</span><span class="sxs-lookup"><span data-stu-id="e1965-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="e1965-174">Dağıtım ortamı WMF ve modül çevrimiçi galeriden indirmek için Internet erişimi olacak mı?</span><span class="sxs-lookup"><span data-stu-id="e1965-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="e1965-175">Nasıl işletim sisteminin yükledikten sonra en son güvenlik güncelleştirmelerini yükler mi?</span><span class="sxs-lookup"><span data-stu-id="e1965-175">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="e1965-176">Ortam güncelleştirmeleri almak için Internet erişimine sahip olur veya yerel bir Windows Server Update Services (WSUS) sunucusu gerekir?</span><span class="sxs-lookup"><span data-stu-id="e1965-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="e1965-177">Erişim zaten çevrimdışı ekleme işlemi aracılığıyla güncelleştirmeleri içeren Windows Server yükleme dosyalarını gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="e1965-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="e1965-178">Donanım gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="e1965-178">Hardware requirements</span></span>

<span data-ttu-id="e1965-179">Çekme sunucusuna dağıtımlar, hem fiziksel hem de sanal sunucularda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e1965-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="e1965-180">Windows Server 2012 R2 için gereksinimlerle çekme server boyutlandırma gereksinimleri hizalayın.</span><span class="sxs-lookup"><span data-stu-id="e1965-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="e1965-181">CPU: 1,4 GHz 64-bit işlemci bellek: 512 MB Disk alanı: 32 GB ağ: Gigabit Ethernet Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="e1965-181">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="e1965-182">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-182">Planning task</span></span>|
---|
<span data-ttu-id="e1965-183">Fiziksel donanım üzerinde veya bir sanallaştırma platformunda dağıtacak mısınız?</span><span class="sxs-lookup"><span data-stu-id="e1965-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="e1965-184">Hedef ortamınız için yeni bir sunucu isteği işlemi nedir?</span><span class="sxs-lookup"><span data-stu-id="e1965-184">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="e1965-185">Bir sunucu kullanılabilir hale gelmesi için ortalama bir döngü süresi nedir?</span><span class="sxs-lookup"><span data-stu-id="e1965-185">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="e1965-186">Hangi boyutu sunucu, ister?</span><span class="sxs-lookup"><span data-stu-id="e1965-186">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="e1965-187">Hesaplar</span><span class="sxs-lookup"><span data-stu-id="e1965-187">Accounts</span></span>

<span data-ttu-id="e1965-188">Bir çekme server örneği dağıtmak için hizmet hesabı gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e1965-188">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="e1965-189">Ancak, Web sitesi yerel bir kullanıcı hesabı bağlamında çalıştırdığı senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="e1965-189">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="e1965-190">Örneğin, bir gereksinimi varsa Web sitesi içeriğini ve Windows Server veya depolama paylaşımı barındırma aygıtı için bir depolama paylaşmak erişimi olmayan etki alanına katılmış.</span><span class="sxs-lookup"><span data-stu-id="e1965-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="e1965-191">DNS kayıtları</span><span class="sxs-lookup"><span data-stu-id="e1965-191">DNS records</span></span>

<span data-ttu-id="e1965-192">Bir çekme sunucu ortamı ile çalışmak için istemciler yapılandırırken kullanılacak bir sunucu adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1965-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="e1965-193">Sınama ortamlarında sunucusu konak adı genellikle kullanılan veya DNS ad çözümlemesi kullanılamıyorsa, sunucunun IP adresini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="e1965-194">Üretim ortamlarında ya da bir laboratuvar ortamında Üretim dağıtımı temsil etmek üzere tasarlanmıştır bir DNS CNAME kaydı oluşturmak için en iyi yöntem olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="e1965-195">Bir DNS CNAME, ana bilgisayar (A) kaydı başvurmak için bir diğer ad oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="e1965-196">Ek ad kaydı amacı, bir değişiklik gelecekte gerekip gerekmeyeceğini esneklik artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="e1965-197">CNAME değişiklikler çekme sunucusunu değiştirme ya ek çekme sunucuları ekleme gibi sunucu ortamınıza karşılık gelen bir istemci yapılandırmasında değişiklik gerektirmez istemci yapılandırmasını ayırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="e1965-198">DNS kaydı için bir ad seçerken, çözüm mimarisi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1965-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="e1965-199">Kullanarak Yük Dengelemesi, trafik HTTPS üzerinden güvenli hale getirmek için kullanılan sertifikanın DNS kaydı olarak aynı adı paylaşan gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="e1965-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="e1965-200">Senaryo</span><span class="sxs-lookup"><span data-stu-id="e1965-200">Scenario</span></span> |<span data-ttu-id="e1965-201">En iyi uygulama</span><span class="sxs-lookup"><span data-stu-id="e1965-201">Best Practice</span></span>
:---|:---
<span data-ttu-id="e1965-202">Sınama Ortamı</span><span class="sxs-lookup"><span data-stu-id="e1965-202">Test Environment</span></span> |<span data-ttu-id="e1965-203">Planlanan bir üretim ortamına mümkünse yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1965-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="e1965-204">Sunucu ana bilgisayar adı basit yapılandırmaları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="e1965-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="e1965-205">DNS kullanılamıyorsa, bir IP adresi yerine ana bilgisayar adı kullanılıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="e1965-206">Tek düğüm dağıtım</span><span class="sxs-lookup"><span data-stu-id="e1965-206">Single Node Deployment</span></span> |<span data-ttu-id="e1965-207">Sunucu ana bilgisayar adı için işaret eden bir DNS CNAME kaydı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1965-207">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="e1965-208">Daha fazla bilgi için bkz: [yapılandırma DNS hepsini bir kez Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="e1965-208">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="e1965-209">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-209">Planning task</span></span>|
---|
<span data-ttu-id="e1965-210">Kimin oluşturulan ve değiştirilen DNS kayıtları kişiye biliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="e1965-210">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="e1965-211">Bir DNS kaydı için bir istek için ortalama döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="e1965-211">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="e1965-212">Sunucular için statik ana bilgisayar (A) kayıtları isteği gerekiyor mu?</span><span class="sxs-lookup"><span data-stu-id="e1965-212">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="e1965-213">Ne bir CNAME isteyecek?</span><span class="sxs-lookup"><span data-stu-id="e1965-213">What will you request as a CNAME?</span></span>|
<span data-ttu-id="e1965-214">Gerekirse, ne tür yük dengeleme çözümü, yararlanacak olan?</span><span class="sxs-lookup"><span data-stu-id="e1965-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="e1965-215">(Ayrıntılar için Yük Dengeleme başlıklı bölüme bakın)</span><span class="sxs-lookup"><span data-stu-id="e1965-215">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="e1965-216">Ortak anahtar altyapısı</span><span class="sxs-lookup"><span data-stu-id="e1965-216">Public Key Infrastructure</span></span>

<span data-ttu-id="e1965-217">Çoğu kuruluş, ağ trafiğini, özellikle gibi hassas verileri yapılandırılmış sunucuları nasıl gibi içeren trafiği gerekir doğrulandı ve/veya iletim sırasında şifrelenmiş olduğunu bugün gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1965-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="e1965-218">Kolaylaştıran HTTP kullanarak bir çekme sunucusuna dağıtmak mümkün olmakla birlikte, istemci isteklerini metni silin, HTTPS kullanan güvenli trafiği için en iyi uygulama olur.</span><span class="sxs-lookup"><span data-stu-id="e1965-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="e1965-219">Hizmet DSC kaynağı bir parametre kümesi kullanarak HTTPS kullanmak üzere yapılandırılan **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="e1965-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="e1965-220">Çekme sunucusuna HTTPS trafiğinin güvenliğini sağlamak için sertifika gereksinimleri herhangi bir HTTPS web sitesini güvenli hale getirme daha farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="e1965-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="e1965-221">**Web sunucusu** şablonu bir Windows Server Sertifika Hizmetleri'nde gerekli yeteneklerin karşılar.</span><span class="sxs-lookup"><span data-stu-id="e1965-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="e1965-222">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-222">Planning task</span></span>|
---|
<span data-ttu-id="e1965-223">Sertifika isteklerini otomatik olarak yapılmaz, kimin sertifika isteklerini başvurun gerekecek mi?</span><span class="sxs-lookup"><span data-stu-id="e1965-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="e1965-224">İstek için ortalama döngü nedir?</span><span class="sxs-lookup"><span data-stu-id="e1965-224">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="e1965-225">Nasıl sertifika dosyası için aktarılır?</span><span class="sxs-lookup"><span data-stu-id="e1965-225">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="e1965-226">Nasıl sertifika özel anahtarı size aktarılır?</span><span class="sxs-lookup"><span data-stu-id="e1965-226">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="e1965-227">Varsayılan süre uzunluğu nedir?</span><span class="sxs-lookup"><span data-stu-id="e1965-227">How long is the default expiration time?</span></span>|
<span data-ttu-id="e1965-228">Sertifika adı için kullanabileceğiniz çekme sunucu ortamı için bir DNS adı üzerinde kapatılan mi?</span><span class="sxs-lookup"><span data-stu-id="e1965-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="e1965-229">Bir mimari seçme</span><span class="sxs-lookup"><span data-stu-id="e1965-229">Choosing an architecture</span></span>

<span data-ttu-id="e1965-230">IIS veya bir SMB dosya paylaşımında barındırılan ya da bir web hizmetini kullanarak bir çekme sunucusuna dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="e1965-231">Çoğu durumda, web hizmeti seçeneği büyük esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="e1965-232">SMB trafiğini genellikle filtrelenmiş veya ağlar arasında engellenen ancak ağ sınırları geçiş yapmak HTTPS trafiği için seyrek değil.</span><span class="sxs-lookup"><span data-stu-id="e1965-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="e1965-233">Web hizmeti ayrıca uyumluluk sunucu veya istemciler merkezi görünürlük sunucusuna geri durumu raporlamak için bir mekanizma sağlar bir Web raporlama Yöneticisi (Bu belgenin sonraki bir sürümde ele alınması gereken iki konuları) içerecek şekilde seçeneği de sunar.</span><span class="sxs-lookup"><span data-stu-id="e1965-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="e1965-234">SMB burada İlkesi bir web sunucusu değil göstermesi belirler. ortamlar için ve bir web sunucusu rolü istenmeyen olun diğer çevre gereksinimleri için bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="e1965-235">İmzalama ve trafiği şifreleme gereksinimlerini değerlendirmek her iki durumda da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1965-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="e1965-236">HTTPS, SMB imzalama ve IPSec ilkelerini dikkate değer tüm seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="e1965-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="e1965-237">Yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="e1965-237">Load balancing</span></span>
<span data-ttu-id="e1965-238">İstemciler web hizmetiyle etkileşmek tek bir yanıtta döndürülen bilgi isteğini olun.</span><span class="sxs-lookup"><span data-stu-id="e1965-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="e1965-239">Yük Dengeleyici oturumları zamanında herhangi bir noktada tek bir sunucu üzerinde saklanır emin olmak için platform için gerekli değildir sıralı istekler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1965-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="e1965-240">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-240">Planning task</span></span>|
---|
<span data-ttu-id="e1965-241">Yük Dengeleme trafiğini sunucular arasında hangi çözüm kullanılacak mı?</span><span class="sxs-lookup"><span data-stu-id="e1965-241">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="e1965-242">Kimin yeni bir yapılandırma aygıt eklemek için bir istek sürer bir donanım yük dengeleyicisi kullanıyorsanız?</span><span class="sxs-lookup"><span data-stu-id="e1965-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="e1965-243">Yeni bir yük yapılandırmak bir istek için ortalama döngü nedir web hizmeti dengeli?</span><span class="sxs-lookup"><span data-stu-id="e1965-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="e1965-244">Hangi bilgilerin istek için gerekli olacak mı?</span><span class="sxs-lookup"><span data-stu-id="e1965-244">What information will be required for the request?</span></span>|
<span data-ttu-id="e1965-245">Bir ek IP istemeniz gerekir veya yük dengelemeden sorumlu takım, kullanacak mı?</span><span class="sxs-lookup"><span data-stu-id="e1965-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="e1965-246">Gereken DNS kayıtlarını var ve bu çözümü dengelemesini yapılandırmak için sorumlu ekibi tarafından gerekli?</span><span class="sxs-lookup"><span data-stu-id="e1965-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="e1965-247">PKI aygıt tarafından işlenmesi Yük Dengeleme çözümüne ihtiyacı yoktur veya hiçbir oturum gereksinimleri vardır sürece HTTPS trafiği dengelemek yükleyebilir?</span><span class="sxs-lookup"><span data-stu-id="e1965-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="e1965-248">Yapılandırmaları ve modülleri çekme sunucusunda hazırlama</span><span class="sxs-lookup"><span data-stu-id="e1965-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="e1965-249">Yapılandırma planlaması kapsamında, hangi DSC hakkında modülleri ve yapılandırmaları çekme sunucu tarafından barındırılacak düşünmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1965-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="e1965-250">Yapılandırma planlama amacıyla hazırlamak ve içerik bir çekme sunucusuna dağıtmak nasıl temel bir anlayış olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e1965-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="e1965-251">Gelecekte, bu bölümde genişletilmiş ve DSC çekme sunucusu için bir işlemler Kılavuzu'nda bulunan.</span><span class="sxs-lookup"><span data-stu-id="e1965-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="e1965-252">Kılavuzu otomasyon ile zamanla modülleri ve yapılandırmaları yönetmek için günlük işlem ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="e1965-253">DSC modülleri</span><span class="sxs-lookup"><span data-stu-id="e1965-253">DSC modules</span></span>
<span data-ttu-id="e1965-254">Bir yapılandırma isteyen istemcilerin gerekli DSC modüllerini gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1965-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="e1965-255">Çekme sunucunun işlevselliğini isteğe bağlı bir dağıtım istemcilere DSC modüllerin otomatik hale getirmektir.</span><span class="sxs-lookup"><span data-stu-id="e1965-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="e1965-256">Bir çekme sunucusuna ilk kez, belki de bir laboratuvar veya kavram kanıtı olarak dağıtıyorsanız, büyük olasılıkla PowerShell Galerisi gibi ortak depoları veya PowerShell.org GitHub depoları DSC modülleri için kullanılabilir DSC modülleri bağımlı olmaz .</span><span class="sxs-lookup"><span data-stu-id="e1965-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="e1965-257">Bile güvenilen çevrimiçi kaynakları için PowerShell Galerisi gibi ortak bir depodan indirilen herhangi bir modül biri tarafından PowerShell deneyimi ve modülleri burada olacaktır ortamının bilgi gözden geçirilmesi gereken olduğunu unutmamak önemlidir Üretimde kullanılan önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1965-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="e1965-258">Bu görev tamamlanırken herhangi ek yükü belgeler ve örnek komut dosyaları gibi kaldırılabilir modülünde denetlemek için bir zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="e1965-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="e1965-259">Modülleri sunucudan istemciye ağ üzerinden yüklenen bu ilk talebinde istemcisinde başına ağ bant genişliğini azaltır.</span><span class="sxs-lookup"><span data-stu-id="e1965-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="e1965-260">Belirli bir biçimde, modül yükünü içeren ModuleName_Version.zip adlı bir ZIP dosyası modüllerin paketlenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1965-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="e1965-261">Dosyayı sunucuya kopyalandıktan sonra bir sağlama toplamı dosya oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1965-261">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="e1965-262">İstemcilerin sunucuya bağlandığınızda, sağlama toplamı yayımlandıktan sonra DSC modülü içeriğini değişmemiştir doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1965-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="e1965-263">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-263">Planning task</span></span>|
---|
<span data-ttu-id="e1965-264">Bir test veya laboratuvar ortamında planlıyorsanız hangi senaryolarını doğrulamak için anahtar misiniz?</span><span class="sxs-lookup"><span data-stu-id="e1965-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="e1965-265">Gereksinim duyduğunuz her şeyi karşılamak için kaynakları içeren genel kullanıma açık modülleri vardır veya kendi kaynaklarını Yazar gerekir?</span><span class="sxs-lookup"><span data-stu-id="e1965-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="e1965-266">Ortamınızı ortak modüller almak için Internet erişimi olacak mı?</span><span class="sxs-lookup"><span data-stu-id="e1965-266">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="e1965-267">Kimin DSC modülleri gözden geçirmek için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="e1965-267">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="e1965-268">Bir üretim ortamında planlıyorsanız ne yerel depo olarak DSC modülleri depolamak için kullanacaksınız?</span><span class="sxs-lookup"><span data-stu-id="e1965-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="e1965-269">Merkezi bir takım uygulama ekipleri DSC modüllerden kabul eder?</span><span class="sxs-lookup"><span data-stu-id="e1965-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="e1965-270">İşlem ne olacak?</span><span class="sxs-lookup"><span data-stu-id="e1965-270">What will the process be?</span></span>|
<span data-ttu-id="e1965-271">Paketleme, kopyalama ve üretime hazır DSC modülleri için bir sağlama toplamı sunucuya, kaynak deposu oluşturma otomatikleştirmek?</span><span class="sxs-lookup"><span data-stu-id="e1965-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="e1965-272">Ekibinizin Otomasyon platform de yönetmekten sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="e1965-272">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="e1965-273">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="e1965-273">DSC configurations</span></span>

<span data-ttu-id="e1965-274">Bir çekme sunucusuna amacı, istemci düğümlere DSC yapılandırmaları dağıtmak için merkezi bir düzenek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="e1965-275">Yapılandırmaları sunucuda MOF belgeleri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e1965-275">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="e1965-276">Her bir belgenin benzersiz bir GUID ile adlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-276">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="e1965-277">İstemciler, bir çekme sunucusuna bağlanmak üzere yapılandırıldığında, bunlar GUID isteği yapılandırma için de verilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-277">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="e1965-278">Bu sistem yapılandırmaları GUID tarafından başvuru genel benzersizliği garanti eder ve düğüm başına ya da aynı yapılandırmalara sahip olması çok sayıda sunucuya yayılan bir rol yapılandırma olarak ayrıntı düzeyi içeren bir yapılandırma uygulanabilir şekilde esnektir.</span><span class="sxs-lookup"><span data-stu-id="e1965-278">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="e1965-279">GUID</span><span class="sxs-lookup"><span data-stu-id="e1965-279">GUIDs</span></span>

<span data-ttu-id="e1965-280">Yapılandırma GUID'lerini planlama ek dikkat bir çekme sunucu dağıtımı düşünürken, büyük.</span><span class="sxs-lookup"><span data-stu-id="e1965-280">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="e1965-281">GUID'ler nasıl ele alınacağını için belirli bir gereksinimi yoktur ve büyük olasılıkla her ortam için benzersiz bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="e1965-281">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="e1965-282">İşlem basitten için karmaşık değişebilir: merkezi olarak depolanmış bir CSV dosyası, basit bir SQL tablo, bir CMDB veya başka bir aracı ya da yazılım çözümü ile tümleştirme gerektiren karmaşık bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="e1965-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="e1965-283">İki genel yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="e1965-283">There are two general approaches:</span></span>

 - <span data-ttu-id="e1965-284">**Sunucu başına GUID'ler atama** — bir ölçü her sunucu yapılandırması ayrı ayrı kontrol güvence sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1965-284">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="e1965-285">Bu güncelleştirmeleri geçici duyarlılık düzeyi sağlar ve birkaç sunucularıyla ortamlarda da çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="e1965-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="e1965-286">**Her sunucu rolü GUID'ler atama** — gerekli yapılandırma verileri başvurmak için web sunucuları gibi aynı işlevi gerçekleştirir tüm sunucuları aynı GUID'ye kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1965-286">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="e1965-287">Birçok sunucuları aynı GUID'ye paylaşıyorsanız, yapılandırma değiştiğinde, bunların tümünün aynı anda güncelleştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1965-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="e1965-288">GUID sunucuları nasıl dağıtıldığını ve ortamınızda yapılandırıldığını hakkında Intelligence kazanmak için kötü amaçlı sahip biri tarafından işlevden çünkü, hassas verileri kabul şeydir.</span><span class="sxs-lookup"><span data-stu-id="e1965-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="e1965-289">Daha fazla bilgi için bkz: [güvenli bir şekilde modunda PowerShell istenen durum yapılandırması çekme GUID'ler ayırma](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="e1965-289">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="e1965-290">Görev Planlama</span><span class="sxs-lookup"><span data-stu-id="e1965-290">Planning task</span></span>|
---|
<span data-ttu-id="e1965-291">Kimin hazır olduğunuzda, yapılandırmalarında çekme sunucu klasörüne kopyalamak için sorumlu olacak?</span><span class="sxs-lookup"><span data-stu-id="e1965-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="e1965-292">Yapılandırmaları bir uygulama ekibi tarafından yazılan varsa, bunları devre dışı elle ne işlem olacak?</span><span class="sxs-lookup"><span data-stu-id="e1965-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="e1965-293">Bunlar, ekibin yazılan gibi yapılandırmaları depolamak için bir depo özelliğinden yararlanır?</span><span class="sxs-lookup"><span data-stu-id="e1965-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="e1965-294">Sunucuya yapılandırmalarını kopyalama ve hazır olduğunuzda bir sağlama toplamı oluşturma işlemini otomatikleştirmek?</span><span class="sxs-lookup"><span data-stu-id="e1965-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="e1965-295">Sunucuları veya rolleri için GUID'leri nasıl eşler ve bu depolanacağı?</span><span class="sxs-lookup"><span data-stu-id="e1965-295">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="e1965-296">Ne bir işlem olarak istemci makineleri yapılandırmak için kullanacağınız ve nasıl oluşturma ve yapılandırma GUID'ler saklamak için işleminizi ile tümleştirecek?</span><span class="sxs-lookup"><span data-stu-id="e1965-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="e1965-297">Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e1965-297">Installation Guide</span></span>

<span data-ttu-id="e1965-298">*Bu belgede verilen komut kararlı örnektir. Her zaman komut dosyalarını dikkatle bir üretim ortamında yürütmeden önce gözden geçirin.*</span><span class="sxs-lookup"><span data-stu-id="e1965-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e1965-299">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e1965-299">Prerequisites</span></span>

<span data-ttu-id="e1965-300">PowerShell sürümü sunucunuzda doğrulamak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1965-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="e1965-301">Mümkünse, Windows Management Framework'ün en son sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="e1965-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="e1965-302">Ardından, indirme `xPsDesiredStateConfiguration` aşağıdaki komutu kullanarak modülü.</span><span class="sxs-lookup"><span data-stu-id="e1965-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="e1965-303">Komut modülü yüklemeden önce onayınız istenir.</span><span class="sxs-lookup"><span data-stu-id="e1965-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="e1965-304">Yükleme ve yapılandırma komut dosyaları</span><span class="sxs-lookup"><span data-stu-id="e1965-304">Installation and configuration scripts</span></span>
-

<span data-ttu-id="e1965-305">Bir DSC çekme sunucusuna dağıtmak için en iyi yöntem DSC yapılandırma betiği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="e1965-306">Bu belgede yalnızca DSC web hizmeti yapılandırırsınız ve gelişmiş bir Windows Server uçtan uca dahil olmak üzere DSC web hizmeti yapılandırırsınız ayarları her iki temel ayarlar dahil olmak üzere komut dosyaları sunacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1965-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="e1965-307">Not: Şu anda `xPSDesiredStateConfiguation` DSC modülü server'ın EN-US yerel olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1965-307">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="e1965-308">Windows Server 2012 için temel yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1965-308">Basic configuration for Windows Server 2012</span></span>
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="e1965-309">Windows Server 2012 R2 için Gelişmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1965-309">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="e1965-310">Çekme sunucu işlevselliğini doğrulayın</span><span class="sxs-lookup"><span data-stu-id="e1965-310">Verify pull server functionality</span></span>

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

### <a name="configure-clients"></a><span data-ttu-id="e1965-311">İstemcilerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1965-311">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="e1965-312">Ek başvurular, parçacıkları ve örnekler</span><span class="sxs-lookup"><span data-stu-id="e1965-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="e1965-313">Bu örnek, test etmek için el ile (WMF5 gerektirir) bir istemci bağlantı başlatmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1965-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="e1965-314">[Ekle DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet türü CNAME kaydı bir DNS bölgesine eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1965-314">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="e1965-315">PowerShell işlevi [bir sağlama toplamı oluşturup yayımlama DSC MOF SMB çekme sunucusuna](http://bit.ly/1E46BhI) gerekli sağlama toplamı otomatik olarak oluşturur ve ardından MOF yapılandırma ve sağlama toplamı dosyaları SMB çekme sunucusuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e1965-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="e1965-316">Ek - anlama ODATA hizmeti verilerini dosya türleri</span><span class="sxs-lookup"><span data-stu-id="e1965-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="e1965-317">Bir veri dosyası, bilgileri bir OData web hizmetini içeren bir çekme sunucu dağıtımı sırasında oluşturmak için depolanır.</span><span class="sxs-lookup"><span data-stu-id="e1965-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="e1965-318">Dosya türü aşağıda açıklandığı gibi işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e1965-318">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="e1965-319">**Windows Server 2012** dosya türü her zaman .mdb olacaktır</span><span class="sxs-lookup"><span data-stu-id="e1965-319">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="e1965-320">**Windows Server 2012 R2** bir .mdb yapılandırmada belirtilmediği sürece dosya türü için .edb varsayılan olur</span><span class="sxs-lookup"><span data-stu-id="e1965-320">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="e1965-321">İçinde [örnek komut dosyası Gelişmiş](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) bir çekme sunucusuna yüklemek için tüm dosya türüne göre neden hata olasılığını önlemek için web.config dosyası ayarları otomatik olarak denetlemek nasıl bir örnek da bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e1965-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>