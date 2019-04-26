---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Paket ve karşıya yükleme kaynakları için bir çekme sunucusu
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079582"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="4a369-103">Paket ve karşıya yükleme kaynakları için bir çekme sunucusu</span><span class="sxs-lookup"><span data-stu-id="4a369-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="4a369-104">Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="4a369-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="4a369-105">Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4a369-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="4a369-106">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="4a369-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="4a369-107">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="4a369-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="4a369-108">Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a369-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="4a369-109">Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a369-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="4a369-110">Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.</span><span class="sxs-lookup"><span data-stu-id="4a369-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="4a369-111">Paket kaynak modülleri</span><span class="sxs-lookup"><span data-stu-id="4a369-111">Package Resource Modules</span></span>

<span data-ttu-id="4a369-112">Her kaynak indirmek bir istemci için kullanılabilen bir ".zip" dosyasında depolanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a369-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="4a369-113">Aşağıdaki örneği kullanarak gerekli adımları gösterilir [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) kaynak.</span><span class="sxs-lookup"><span data-stu-id="4a369-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="4a369-114">PowerShell 4.0 sürümünü kullanan istemcileri varsa, kaynak klasör yapısı için flaten gerekir ve sürüm klasörleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4a369-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="4a369-115">Daha fazla bilgi için [birden çok kaynak sürümü](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="4a369-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="4a369-116">Herhangi bir yardımcı programını, komut dosyası veya tercih ettiğiniz yöntemi kullanarak kaynak dizini sıkıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a369-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="4a369-117">Windows içinde yapabilecekleriniz *sağ* "xPSDesiredStateConfiguration" dizin ve "Göndermek için" sonra "Sıkıştırılmış klasörü" seçin.</span><span class="sxs-lookup"><span data-stu-id="4a369-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Sağ tıklayın](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="4a369-119">Kaynak arşiv adlandırma</span><span class="sxs-lookup"><span data-stu-id="4a369-119">Naming the Resource Archive</span></span>

<span data-ttu-id="4a369-120">Kaynak arşiv şu biçimde adlandırılır gerekir:</span><span class="sxs-lookup"><span data-stu-id="4a369-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="4a369-121">Yukarıdaki örnekte, "xPSDesiredStateConfiguration.zip" olarak yeniden adlandırıldı "xPSDesiredStateConfiguration_8.4.4.0.zip" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a369-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="4a369-122">Sağlama toplamları oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a369-122">Create CheckSums</span></span>

<span data-ttu-id="4a369-123">Kaynak modülü sıkıştırılmış ve yeniden oluşturmanıza gerek bir **sağlama toplamı**.</span><span class="sxs-lookup"><span data-stu-id="4a369-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="4a369-124">**Sağlama toplamı** , istemci üzerindeki LCM tarafından kaynak değiştirildi ve yeniden indirilmesi gereken belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a369-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="4a369-125">Oluşturabileceğiniz bir **sağlama toplamı** ile [yeni DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet'i, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="4a369-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="4a369-126">Hiçbir çıkış gösterilir, ancak artık "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a369-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="4a369-127">Ayrıca çalıştırabileceğiniz `New-DSCCheckSum` kullanarak dosyaları dizini karşı `-Path` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4a369-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="4a369-128">Bir sağlama toplamı zaten varsa, ile yeniden oluşturulması zorlayabilirsiniz `-Force` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4a369-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="4a369-129">Kaynak arşivi depolanacağı konumu</span><span class="sxs-lookup"><span data-stu-id="4a369-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="4a369-130">DSC HTTP çekme sunucusunda</span><span class="sxs-lookup"><span data-stu-id="4a369-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="4a369-131">Ayarladığınızda, HTTP çekme sunucusu açıklandığı şekilde [bir DSC HTTP çekme sunucusu ayarlama](pullServer.md), dizinler için belirttiğiniz **ModulePath** ve **Yapılandırmayolu** anahtarları.</span><span class="sxs-lookup"><span data-stu-id="4a369-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="4a369-132">**Yapılandırmayolu** anahtar ".mof" dosyalar nerede depolanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a369-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="4a369-133">**ModulePath** DSC kaynak modüllerin depolandığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a369-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="4a369-134">Bir SMB paylaşımında</span><span class="sxs-lookup"><span data-stu-id="4a369-134">On an SMB Share</span></span>

<span data-ttu-id="4a369-135">Belirttiyseniz bir **ResourceRepositoryShare**, kullanarak çekme istemcisi ayarlama arşivler ve sağlama toplamı olarak depoladığınızda **SourcePath** yer **ResourceRepositoryShare** blok.</span><span class="sxs-lookup"><span data-stu-id="4a369-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="4a369-136">Yalnızca belirtilen bir **ConfigurationRepositoryShare**, kullanarak çekme istemcisi ayarlama arşivler ve sağlama toplamı olarak depoladığınızda **SourcePath** yer  **ConfigurationRepositoryShare** blok.</span><span class="sxs-lookup"><span data-stu-id="4a369-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="4a369-137">Kaynaklar güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="4a369-137">Updating resources</span></span>

<span data-ttu-id="4a369-138">Arşivin adı sürüm numarasını değiştirmek veya yeni bir sağlama toplamı oluşturarak kaynaklarını güncelleştirmek için bir düğüm zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a369-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="4a369-139">Çekme istemcisi daha yeni sürümleri gerekli kaynakları için kontrol eder, aynı zamanda kendi LCM yenilendiğinde sağlama, güncelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="4a369-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a369-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a369-140">See also</span></span>

- [<span data-ttu-id="4a369-141">Bir DSC SMB çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="4a369-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="4a369-142">Bir DSC HTTP çekme sunucusu ayarlama</span><span class="sxs-lookup"><span data-stu-id="4a369-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
