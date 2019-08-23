---
ms.date: 12/12/2018
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Yapılandırma kimliklerini (v4/V5) kullanarak bir çekme sunucusuna yayımlama
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986569"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="a5113-103">Yapılandırma kimliklerini (v4/V5) kullanarak bir çekme sunucusuna yayımlama</span><span class="sxs-lookup"><span data-stu-id="a5113-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="a5113-104">Aşağıdaki bölümler, zaten bir çekme sunucusu ayarlamış olduğunuz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5113-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="a5113-105">Çekme sunucunuzu ayarlamadıysanız Aşağıdaki kılavuzlardan yararlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a5113-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="a5113-106">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a5113-107">DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a5113-108">Her hedef düğüm, yapılandırmaların, kaynakların indirileceği ve hatta durumunu rapor etmek üzere yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5113-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a5113-109">Bu makalede, karşıdan yüklenmek üzere kullanılabilir olmaları için kaynakları karşıya yükleme ve istemcileri otomatik olarak kaynakları yükleyecek şekilde yapılandırma işlemlerinin nasıl yapılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a5113-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="a5113-110">Düğüm, **çekme** veya **Push** (V5) aracılığıyla atanan bir yapılandırma aldığında, yapılandırma Için gereken tüm kaynakları yerel Configuration Manager (LCM) ' de belirtilen konumdan otomatik olarak indirir.</span><span class="sxs-lookup"><span data-stu-id="a5113-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="a5113-111">Derleme yapılandırması</span><span class="sxs-lookup"><span data-stu-id="a5113-111">Compile configurations</span></span>

<span data-ttu-id="a5113-112">[Yapılandırma](../configurations/configurations.md) bir çekme sunucusunda depolamanın ilk adımı, bunları dosyalar halinde `.mof` derlemek.</span><span class="sxs-lookup"><span data-stu-id="a5113-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="a5113-113">Bir yapılandırmayı genel hale getirmek ve daha fazla istemci için geçerli olan düğüm `localhost` blosonra kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5113-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="a5113-114">Aşağıdaki örnekte, belirli bir istemci adı yerine tarafından `localhost` kullanılan bir yapılandırma kabuğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5113-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="a5113-115">Genel yapılandırmanızı derledikten sonra bir `localhost.mof` dosyanız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5113-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="a5113-116">MOF dosyasını yeniden adlandırma</span><span class="sxs-lookup"><span data-stu-id="a5113-116">Renaming the MOF file</span></span>

<span data-ttu-id="a5113-117">Yapılandırma `.mof` dosyalarını, bir çekme sunucusunda **ConfigurationName** veya **ConfigurationId**ile saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="a5113-118">Çekme istemcilerinizi nasıl ayarlamayı planladığınıza bağlı olarak, derlenmiş `.mof` dosyalarınızı düzgün şekilde yeniden adlandırmak için aşağıdan bir bölüm seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="a5113-119">Yapılandırma kimlikleri (GUID)</span><span class="sxs-lookup"><span data-stu-id="a5113-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="a5113-120">Dosyanızı dosya olarak `localhost.mof` `<GUID>.mof` yeniden adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5113-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="a5113-121">Aşağıdaki örneği kullanarak veya [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet 'ini kullanarak rastgele bir **GUID** oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="a5113-122">Örnek çıkış</span><span class="sxs-lookup"><span data-stu-id="a5113-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="a5113-123">Daha sonra, kabul edilebilir `.mof` herhangi bir yöntemi kullanarak dosyanızı yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="a5113-124">Aşağıdaki örnek, [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet 'ini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5113-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="a5113-125">Ortamınızda **GUID 'leri** kullanma hakkında daha fazla bilgi için bkz. [GUID için plan](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="a5113-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="a5113-126">Yapılandırma adları</span><span class="sxs-lookup"><span data-stu-id="a5113-126">Configuration names</span></span>

<span data-ttu-id="a5113-127">Dosyanızı dosya olarak `localhost.mof` `<Configuration Name>.mof` yeniden adlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5113-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="a5113-128">Aşağıdaki örnekte, önceki bölümdeki yapılandırma adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5113-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="a5113-129">Daha sonra, kabul edilebilir `.mof` herhangi bir yöntemi kullanarak dosyanızı yeniden adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="a5113-130">Aşağıdaki örnek, [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet 'ini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5113-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="a5113-131">Sağlama toplamını oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5113-131">Create the checkSum</span></span>

<span data-ttu-id="a5113-132">Bir `.mof` çekme sunucusunda depolanan her bir dosyanın veya SMB paylaşımının ilişkili `.checksum` bir dosyası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5113-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="a5113-133">Bu dosya, istemcilerin ilişkili `.mof` dosyanın değiştiğini bilmesini sağlar ve yeniden indirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5113-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="a5113-134">[New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet 'i Ile bir **sağlama toplamı** oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="a5113-135">Ayrıca, parametresini kullanarak `New-DSCCheckSum` bir dosya dizini için `-Path` de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="a5113-136">Bir sağlama toplamı zaten varsa, bu `-Force` parametre ile yeniden oluşturulmasını zorunlu hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="a5113-137">Aşağıdaki örnek, önceki bölümden `.mof` dosyasını içeren bir dizin belirtti ve `-Force` parametresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5113-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="a5113-138">Çıktı gösterilmez, ancak artık bir `<GUID or Configuration Name>.mof.checksum` dosya görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5113-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="a5113-139">MOF dosyalarının ve sağlama toplamlarını nerede depolayabileceğiniz</span><span class="sxs-lookup"><span data-stu-id="a5113-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="a5113-140">DSC HTTP çekme sunucusunda</span><span class="sxs-lookup"><span data-stu-id="a5113-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="a5113-141">HTTP çekme sunucunuzu ayarlarken [DSC http çekme sunucusu ayarlama](pullServer.md)bölümünde açıklandığı gibi, **ModulePath** ve **ConfigurationPath** anahtarlarının dizinlerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="a5113-142">**ModulePath** anahtarı, bir modülün paketlenmiş `.zip` dosyalarının nerede depolanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5113-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="a5113-143">**ConfigurationPath** , herhangi bir `.mof` dosya ve `.checksum` dosyanın nerede depolanması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5113-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="a5113-144">Bir SMB paylaşımında</span><span class="sxs-lookup"><span data-stu-id="a5113-144">On an SMB share</span></span>

<span data-ttu-id="a5113-145">Bir SMB paylaşımının kullanılması için bir Istek temelli Istemci ayarladığınızda, bir **Configurationdepotorshare**belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="a5113-146">Tüm `.mof` dosyalar ve `.checksum` dosyalar, **configurationdepotorshare** bloğunun **SourcePath** dizininde depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5113-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="a5113-147">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a5113-147">Next steps</span></span>

<span data-ttu-id="a5113-148">Ardından, belirtilen yapılandırmayı çekmek için çekme Istemcilerini yapılandırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a5113-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="a5113-149">Daha fazla bilgi için aşağıdaki kılavuzlardan birine bakın:</span><span class="sxs-lookup"><span data-stu-id="a5113-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="a5113-150">Yapılandırma kimlikleri (v4) kullanarak çekme Istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="a5113-151">Yapılandırma kimliklerini (V5) kullanarak çekme Istemcisi ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="a5113-152">Yapılandırma adlarını (V5) kullanarak çekme Istemcisini ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="a5113-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5113-153">See also</span></span>

- [<span data-ttu-id="a5113-154">DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a5113-155">DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="a5113-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="a5113-156">Kaynakları bir çekme sunucusuna paketleme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="a5113-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
