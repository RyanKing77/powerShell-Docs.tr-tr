---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC dosya kaynağı
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048749"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="bbf21-103">DSC dosya kaynağı</span><span class="sxs-lookup"><span data-stu-id="bbf21-103">DSC File Resource</span></span>

> <span data-ttu-id="bbf21-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bbf21-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bbf21-105">Dosya kaynağı, Windows PowerShell Desired State Configuration (DSC) hedef düğüm üzerindeki dosya ve klasörleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbf21-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="bbf21-106">**Not:** Varsa **MatchSource** özelliği **$false** (varsayılan değer olan), yapılandırmanın geçerli olduğu ilk kez kopyalanacak içeriği önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="bbf21-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span>
><span data-ttu-id="bbf21-107">Yapılandırmanın sonraki uygulamalar için güncelleştirilmiş dosyaları ve/veya klasörleri tarafından belirtilen yoldaki kontrol etmez **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="bbf21-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="bbf21-108">Dosyaları ve/veya klasörleri güncelleştirmeleri denetlemesini istiyorsanız **SourcePath** yapılandırmanın uygulanması her zaman ayarlamak **MatchSource** için **$true**.</span><span class="sxs-lookup"><span data-stu-id="bbf21-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbf21-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbf21-109">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="bbf21-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bbf21-110">Properties</span></span>

|  <span data-ttu-id="bbf21-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="bbf21-111">Property</span></span>  |  <span data-ttu-id="bbf21-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbf21-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="bbf21-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="bbf21-113">DestinationPath</span></span>| <span data-ttu-id="bbf21-114">Bir dosya veya dizin durumu sağlamak istediğiniz yeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="bbf21-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbf21-115">Attributes</span></span>| <span data-ttu-id="bbf21-116">İstenen durum hedeflenen dosya veya dizin özniteliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>|
| <span data-ttu-id="bbf21-117">Sağlama</span><span class="sxs-lookup"><span data-stu-id="bbf21-117">Checksum</span></span>| <span data-ttu-id="bbf21-118">İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="bbf21-119">Varsa __sağlama toplamı__ belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbf21-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="bbf21-120">Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="bbf21-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|
| <span data-ttu-id="bbf21-121">İçerikler</span><span class="sxs-lookup"><span data-stu-id="bbf21-121">Contents</span></span>| <span data-ttu-id="bbf21-122">Belirli bir dize gibi bir dosyanın içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-122">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="bbf21-123">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="bbf21-123">Credential</span></span>| <span data-ttu-id="bbf21-124">Erişimi gerekiyorsa, kaynak dosyaları gibi kaynaklarına erişmek için gerekli kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>|
| <span data-ttu-id="bbf21-125">Emin olun</span><span class="sxs-lookup"><span data-stu-id="bbf21-125">Ensure</span></span>| <span data-ttu-id="bbf21-126">Dosya veya dizin var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="bbf21-127">"Yok" dosya veya dizin yok sağlamak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbf21-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="bbf21-128">"Dosya veya dizin var olmadığından emin olmak için mevcut" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbf21-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="bbf21-129">"Var" varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bbf21-129">The default is "Present".</span></span>|
| <span data-ttu-id="bbf21-130">Force</span><span class="sxs-lookup"><span data-stu-id="bbf21-130">Force</span></span>| <span data-ttu-id="bbf21-131">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="bbf21-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="bbf21-132">Zorla özelliğini kullanarak bu tür hatalar geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bbf21-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="bbf21-133">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="bbf21-133">The default value is __$false__.</span></span>|
| <span data-ttu-id="bbf21-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="bbf21-134">Recurse</span></span>| <span data-ttu-id="bbf21-135">Alt dizinleri dahil olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="bbf21-136">Bu özellik kümesine __$true__ dahil edilmesi için alt dizinler istediğinizi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="bbf21-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="bbf21-137">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="bbf21-137">The default is __$false__.</span></span> <span data-ttu-id="bbf21-138">**Not**: Bu özellik yalnızca dizinine Type özelliği ayarlandığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>|
| <span data-ttu-id="bbf21-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bbf21-139">DependsOn</span></span> | <span data-ttu-id="bbf21-140">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bbf21-141">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bbf21-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="bbf21-142">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="bbf21-142">SourcePath</span></span>| <span data-ttu-id="bbf21-143">Dosya veya klasör kaynak kopyalanacak yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-143">Indicates the path from which to copy the file or folder resource.</span></span>|
| <span data-ttu-id="bbf21-144">Tür</span><span class="sxs-lookup"><span data-stu-id="bbf21-144">Type</span></span>| <span data-ttu-id="bbf21-145">Yapılandırılan kaynak bir dizin veya bir dosya olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="bbf21-146">Bu özelliği kaynak dizin olduğunu belirtmek için "dizin" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbf21-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="bbf21-147">"Kaynağı bir dosya olduğunu belirtmek üzere dosyaya" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbf21-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="bbf21-148">"Dosya" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-148">The default value is “File”.</span></span>|
| <span data-ttu-id="bbf21-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="bbf21-149">MatchSource</span></span>| <span data-ttu-id="bbf21-150">Varsayılan değerine ayarlanmasından __$false__, ardından yapılandırmanın geçerli olduğu ilk kez hedefe (örneğin, A, B ve C dosyaları) kaynak dosyaları eklenir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="bbf21-151">(D) yeni bir dosya için kaynak eklediyseniz, hatta yapılandırmayı daha sonra yeniden uygulandığında, bu hedefe eklenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="bbf21-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="bbf21-152">Değer ise __$true__, ardından yapılandırma uygulanır, her zaman sonradan kaynak (örneğin, bu örnekte dosyası D) bulunan yeni dosyaları hedefe eklenir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="bbf21-153">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="bbf21-153">The default value is **$false**.</span></span>|

## <a name="example"></a><span data-ttu-id="bbf21-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbf21-154">Example</span></span>

<span data-ttu-id="bbf21-155">Aşağıdaki örnek bir dizin yolu ile emin olmak için dosyayı kaynak kullanmayı gösterir `C:\Users\Public\Documents\DSCDemo\DemoSource` bir kaynak bilgisayar (örneğin, "çekme" sunucusu) de (yanı sıra tüm alt dizinleri) varsa hedef düğümde bulunan.</span><span class="sxs-lookup"><span data-stu-id="bbf21-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="bbf21-156">Ayrıca günlüğe tamamlandığında confirmatory bir ileti yazar ve dosya denetimini işlemi önce günlüğe kaydetme işlemi çalıştığından emin olmak için bir deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="bbf21-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

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