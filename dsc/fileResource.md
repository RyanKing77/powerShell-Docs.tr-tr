---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC dosya kaynağı
ms.openlocfilehash: 7964eabe5f4585600ae80f3e5ff7439c0d954769
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="c8f0b-103">DSC dosya kaynağı</span><span class="sxs-lookup"><span data-stu-id="c8f0b-103">DSC File Resource</span></span>

> <span data-ttu-id="c8f0b-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c8f0b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c8f0b-105">Dosya kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC) dosyaları ve klasörleri hedef düğümde bulunan yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="c8f0b-106">**Not:** varsa **MatchSource** özelliği ayarlanmış **$false** (varsayılan değer olan), yapılandırma uygulanan ilk kez kopyalanacak içeriği önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="c8f0b-107">Yapılandırmanın sonraki uygulamalar için güncelleştirilmiş dosyaları ve/veya klasörleri tarafından belirtilen yoldaki kontrol etmez **KaynakYolu**.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="c8f0b-108">Dosyaları ve/veya klasörlerde güncelleştirmeleri denetlemek istiyorsanız **KaynakYolu** yapılandırmanın uygulanması her zaman ayarlamak **MatchSource** için **$true**.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8f0b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8f0b-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="c8f0b-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c8f0b-110">Properties</span></span>

|  <span data-ttu-id="c8f0b-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="c8f0b-111">Property</span></span>  |  <span data-ttu-id="c8f0b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8f0b-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="c8f0b-113">HedefYolu</span><span class="sxs-lookup"><span data-stu-id="c8f0b-113">DestinationPath</span></span>| <span data-ttu-id="c8f0b-114">Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c8f0b-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c8f0b-115">Attributes</span></span>| <span data-ttu-id="c8f0b-116">Belirtilen istenen duruma hedeflenen dosya veya dizin özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="c8f0b-117">Sağlama</span><span class="sxs-lookup"><span data-stu-id="c8f0b-117">Checksum</span></span>| <span data-ttu-id="c8f0b-118">İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="c8f0b-119">Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="c8f0b-120">Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="c8f0b-121">İçerikler</span><span class="sxs-lookup"><span data-stu-id="c8f0b-121">Contents</span></span>| <span data-ttu-id="c8f0b-122">Belirli bir dize gibi bir dosyanın içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="c8f0b-123">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="c8f0b-123">Credential</span></span>| <span data-ttu-id="c8f0b-124">Bu tür erişimi gerekiyorsa kaynak dosyaları gibi kaynaklara erişmek için gerekli kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="c8f0b-125">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c8f0b-125">Ensure</span></span>| <span data-ttu-id="c8f0b-126">Dosya veya dizin var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="c8f0b-127">Bu özelliği dosya veya dizin yok emin olmak için "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="c8f0b-128">"Dosya veya dizin var olmadığından emin olmak için mevcut" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="c8f0b-129">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-129">The default is "Present".</span></span>|
| <span data-ttu-id="c8f0b-130">Force</span><span class="sxs-lookup"><span data-stu-id="c8f0b-130">Force</span></span>| <span data-ttu-id="c8f0b-131">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c8f0b-132">Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="c8f0b-133">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="c8f0b-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="c8f0b-134">Recurse</span></span>| <span data-ttu-id="c8f0b-135">Alt dizinleri dahil olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="c8f0b-136">Bu özelliği ayarlamak __$true__ dahil edilmesi için alt dizinler istediğinizi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="c8f0b-137">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-137">The default is __$false__.</span></span> <span data-ttu-id="c8f0b-138">**Not**: Bu özellik yalnızca Type özelliği dizinine olarak ayarlandığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="c8f0b-139">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c8f0b-139">DependsOn</span></span> | <span data-ttu-id="c8f0b-140">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c8f0b-141">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c8f0b-142">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="c8f0b-142">SourcePath</span></span>| <span data-ttu-id="c8f0b-143">Dosya veya klasör kaynak kopyalanacak yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="c8f0b-144">Tür</span><span class="sxs-lookup"><span data-stu-id="c8f0b-144">Type</span></span>| <span data-ttu-id="c8f0b-145">Yapılandırılmakta kaynak bir dizin veya bir dosya olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="c8f0b-146">Bu özelliği kaynak bir dizin olduğunu belirtmek için "dizin" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="c8f0b-147">"Kaynak dosya olduğunu belirtmek için dosyaya" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="c8f0b-148">Varsayılan değer "Dosyası" dir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-148">The default value is “File”.</span></span>|
| <span data-ttu-id="c8f0b-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="c8f0b-149">MatchSource</span></span>| <span data-ttu-id="c8f0b-150">Varsa varsayılan değer olarak ayarlı __$false__, sonra tüm dosyalar (örneğin, A, B ve C dosyaları) kaynak üzerinde yapılandırma uygulanan ilk kez hedefe eklenir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="c8f0b-151">Yeni bir dosya (D) kaynağına eklediyseniz, bile yapılandırmayı daha sonra yeniden uygulandığında, bu hedefe eklenmez.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="c8f0b-152">Değer ise __$true__, yapılandırma uygulanır, her zaman hedefe sonradan kaynak (örneğin, bu örnekte dosyası D) bulunan yeni dosyalar eklenirken sonra.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="c8f0b-153">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="c8f0b-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8f0b-154">Example</span></span>

<span data-ttu-id="c8f0b-155">Aşağıdaki örnekte bir dizin yolu ile emin olmak için dosya kaynağı kullanmayı gösterir `C:\Users\Public\Documents\DSCDemo\DemoSource` üzerinde bir kaynağı (örneğin, "çekme" sunucu) de (yanı sıra tüm alt dizinler) mevcut bilgisayardır hedef düğümde bulunan.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="c8f0b-156">Ayrıca günlüğe tamamlandığında confirmatory bir ileti yazar ve dosyası denetleniyor işlemi önce günlüğe kaydetme işlemi çalıştığından emin olmak için bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="c8f0b-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```