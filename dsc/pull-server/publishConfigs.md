---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme yapılandırma kimliklerinin (v4/v5) kullanarak sunucuda yayımlayın
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686372"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="0a575-103">Bir çekme yapılandırma kimliklerinin (v4/v5) kullanarak sunucuda yayımlayın</span><span class="sxs-lookup"><span data-stu-id="0a575-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="0a575-104">Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="0a575-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="0a575-105">Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0a575-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="0a575-106">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="0a575-107">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="0a575-108">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a575-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="0a575-109">Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a575-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="0a575-110">Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.</span><span class="sxs-lookup"><span data-stu-id="0a575-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="0a575-111">Derleme yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="0a575-111">Compile Configurations</span></span>

<span data-ttu-id="0a575-112">Depolama ilk adımı [yapılandırmaları](../configurations/configurations.md) bunları ".mof" dosyalarına derlemek için bir çekme sunucusu olduğunu.</span><span class="sxs-lookup"><span data-stu-id="0a575-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="0a575-113">Genel ve daha fazla istemci için geçerli bir yapılandırma oluşturmak için kullanın `localhost` , düğüm bloğundaki.</span><span class="sxs-lookup"><span data-stu-id="0a575-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="0a575-114">Aşağıdaki örnek, kullanan bir yapılandırma Kabuk gösterir `localhost` belirli istemci adı yerine.</span><span class="sxs-lookup"><span data-stu-id="0a575-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="0a575-115">Genel yapılandırma derlediğiniz sonra "localhost.mof" dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a575-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="0a575-116">MOF dosyasını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="0a575-116">Renaming the MOF file</span></span>

<span data-ttu-id="0a575-117">Bir çekme sunucusu tarafından yapılandırma ".mof" dosyalarını depoladığınız **ConfigurationName** veya **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="0a575-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="0a575-118">Nasıl çekme istemcilerinize ayarlanacak planladığınıza bağlı olarak, bir bölümü doğru derlenmiş ".mof" dosyaları yeniden adlandırmak için aşağıdaki seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a575-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="0a575-119">Yapılandırma Kimliği (GUID)</span><span class="sxs-lookup"><span data-stu-id="0a575-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="0a575-120">"Localhost.mof" dosyanızı yeniden adlandırmanız gerekir "<GUID>.mof" dosya.</span><span class="sxs-lookup"><span data-stu-id="0a575-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="0a575-121">Rastgele bir sıra oluşturabilirsiniz **GUID** kullanarak veya aşağıdaki örneği kullanarak [yeni GUID](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0a575-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="0a575-122">Örnek Çıkış</span><span class="sxs-lookup"><span data-stu-id="0a575-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="0a575-123">Ardından, kabul edilebilir herhangi bir yöntemi kullanarak ".mof" dosyanızı yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a575-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="0a575-124">Aşağıdaki örnekte [öğeyi yeniden adlandır](/powershell/module/microsoft.powershell.management/rename-item) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0a575-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="0a575-125">Kullanma hakkında daha fazla bilgi için **GUID'leri** ortamınızda bkz [planlama GUID'leri](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="0a575-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="0a575-126">Yapılandırma adları</span><span class="sxs-lookup"><span data-stu-id="0a575-126">Configuration Names</span></span>

<span data-ttu-id="0a575-127">"Localhost.mof" dosyanızı yeniden adlandırmanız gerekir "<Configuration Name>.mof" dosya.</span><span class="sxs-lookup"><span data-stu-id="0a575-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="0a575-128">Aşağıdaki örnekte, önceki bölümde yapılandırma adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a575-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="0a575-129">Ardından, kabul edilebilir herhangi bir yöntemi kullanarak ".mof" dosyanızı yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a575-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="0a575-130">Aşağıdaki örnekte [öğeyi yeniden adlandır](/powershell/module/microsoft.powershell.management/rename-item) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0a575-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="0a575-131">Sağlama toplamı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a575-131">Create the CheckSum</span></span>

<span data-ttu-id="0a575-132">Her ".mof" dosya ilişkili ".checksum" dosyasına sahip olacak şekilde gereksinimlerinize bir çekme sunucusu veya SMB paylaşımı üzerinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="0a575-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="0a575-133">Bu dosya, ilişkili ".mof" dosya değiştirildi ve yeniden indirilmesi gerektiğini bilmeniz istemcilerin izin verir.</span><span class="sxs-lookup"><span data-stu-id="0a575-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="0a575-134">Oluşturabileceğiniz bir **sağlama toplamı** ile [yeni DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0a575-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="0a575-135">Ayrıca çalıştırabileceğiniz `New-DSCCheckSum` kullanarak dosyaları dizini karşı `-Path` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0a575-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="0a575-136">Bir sağlama toplamı zaten varsa, ile yeniden oluşturulması zorlayabilirsiniz `-Force` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0a575-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="0a575-137">Aşağıdaki örnek, önceki bölümde ".mof" dosyasını içeren bir dizinin belirtilmiş ve kullandığı `-Force` parametresi.</span><span class="sxs-lookup"><span data-stu-id="0a575-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="0a575-138">Hiçbir çıkış gösterilir, ancak artık görmelisiniz bir "<GUID or Configuration Name>. mof.checksum" dosya.</span><span class="sxs-lookup"><span data-stu-id="0a575-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="0a575-139">MOF dosyaları ve sağlamalar depolanacağı konumu</span><span class="sxs-lookup"><span data-stu-id="0a575-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="0a575-140">DSC HTTP çekme sunucusunda</span><span class="sxs-lookup"><span data-stu-id="0a575-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="0a575-141">Ayarladığınızda, HTTP çekme sunucusu açıklandığı şekilde [bir DSC HTTP çekme sunucusu ayarlama](pullServer.md), dizinler için belirttiğiniz **ModulePath** ve **Yapılandırmayolu** anahtarları.</span><span class="sxs-lookup"><span data-stu-id="0a575-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="0a575-142">**Yapılandırmayolu** anahtar ".mof" dosyalar nerede depolanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a575-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="0a575-143">**Yapılandırmayolu** dosyaları ".mof" ve ".checksum" dosyaları burada depolanmalıdır gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a575-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="0a575-144">Bir SMB paylaşımında</span><span class="sxs-lookup"><span data-stu-id="0a575-144">On an SMB Share</span></span>

<span data-ttu-id="0a575-145">SMB paylaşımı kullanmak üzere bir çekme istemcisi ayarlama, belirttiğiniz bir **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="0a575-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="0a575-146">Tüm dosyaları ".mof" ve ".checksum" dosyaları ardından depolanması gereken **SourcePath** yer **ConfigurationRepositoryShare** blok.</span><span class="sxs-lookup"><span data-stu-id="0a575-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="0a575-147">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0a575-147">Next Steps</span></span>

<span data-ttu-id="0a575-148">Ardından, belirtilen yapılandırmayı almayı çekme istemcileri yapılandırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0a575-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="0a575-149">Daha fazla bilgi için aşağıdaki kılavuzlara birine bakın:</span><span class="sxs-lookup"><span data-stu-id="0a575-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="0a575-150">Bir çekme yapılandırma kimliklerinin (v4) kullanarak istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="0a575-151">Bir çekme yapılandırma kimliklerinin (v5) kullanarak istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="0a575-152">Bir çekme (v5) yapılandırma adlarını kullanarak istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="0a575-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a575-153">See also</span></span>

- [<span data-ttu-id="0a575-154">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="0a575-155">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="0a575-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="0a575-156">Paket ve karşıya yükleme kaynakları için bir çekme sunucusu</span><span class="sxs-lookup"><span data-stu-id="0a575-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
