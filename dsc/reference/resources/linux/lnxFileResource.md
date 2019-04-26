---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxFile kaynağı
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078036"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="c17ef-103">DSC için Linux nxFile kaynağı</span><span class="sxs-lookup"><span data-stu-id="c17ef-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="c17ef-104">**NxFile** içinde PowerShell Desired State Configuration (DSC) kaynak dosyalar ve dizinler Linux düğümde yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c17ef-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c17ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c17ef-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c17ef-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c17ef-106">Properties</span></span>

|  <span data-ttu-id="c17ef-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="c17ef-107">Property</span></span> |  <span data-ttu-id="c17ef-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c17ef-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c17ef-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="c17ef-109">DestinationPath</span></span>| <span data-ttu-id="c17ef-110">Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c17ef-111">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="c17ef-111">SourcePath</span></span>| <span data-ttu-id="c17ef-112">Dosya veya klasör kaynak kopyalanacak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="c17ef-113">Bu yol, yerel bir yol olabilir veya bir `http/https/ftp` URL'si.</span><span class="sxs-lookup"><span data-stu-id="c17ef-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="c17ef-114">Uzak `http/https/ftp` URL'leri, yalnızca desteklenen zaman değerini **türü** özelliği dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="c17ef-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="c17ef-115">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c17ef-115">Ensure</span></span>| <span data-ttu-id="c17ef-116">Dosyanın mevcut olup olmadığını denetleyin belirler.</span><span class="sxs-lookup"><span data-stu-id="c17ef-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="c17ef-117">"Var" dosyası var. olmak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="c17ef-118">Kümesi "Yok" dosya sağlamak için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c17ef-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="c17ef-119">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-119">The default value is "Present".</span></span>|
| <span data-ttu-id="c17ef-120">Tür</span><span class="sxs-lookup"><span data-stu-id="c17ef-120">Type</span></span>| <span data-ttu-id="c17ef-121">Yapılandırılan kaynak bir dizin veya bir dosya olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="c17ef-122">Bu özelliği kaynak dizin olduğunu belirtmek için "dizin" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="c17ef-123">"Kaynak bir dosya olduğunu belirtmek için dosya için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="c17ef-124">"Dosya" varsayılan değer:</span><span class="sxs-lookup"><span data-stu-id="c17ef-124">The default value is "file"</span></span>|
| <span data-ttu-id="c17ef-125">İçerikler</span><span class="sxs-lookup"><span data-stu-id="c17ef-125">Contents</span></span>| <span data-ttu-id="c17ef-126">Belirli bir dize gibi bir dosyanın içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="c17ef-127">Sağlama toplamı</span><span class="sxs-lookup"><span data-stu-id="c17ef-127">Checksum</span></span>| <span data-ttu-id="c17ef-128">İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c17ef-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="c17ef-129">Varsa **sağlama toplamı** belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c17ef-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="c17ef-130">Değerler: "ctime", "mtime" veya "md5".</span><span class="sxs-lookup"><span data-stu-id="c17ef-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="c17ef-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="c17ef-131">Recurse</span></span>| <span data-ttu-id="c17ef-132">Alt dizinleri dahil olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="c17ef-133">Bu özellik kümesine **$true** dahil edilmesi için alt dizinler istediğinizi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c17ef-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="c17ef-134">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="c17ef-134">The default is **$false**.</span></span> <span data-ttu-id="c17ef-135">**Not:** Bu özellik yalnızca geçerlidir **türü** özelliği dizinine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c17ef-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="c17ef-136">Force</span><span class="sxs-lookup"><span data-stu-id="c17ef-136">Force</span></span>| <span data-ttu-id="c17ef-137">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="c17ef-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="c17ef-138">Kullanarak **zorla** özelliği, bu tür hatalar'ı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c17ef-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="c17ef-139">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="c17ef-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="c17ef-140">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="c17ef-140">Links</span></span>| <span data-ttu-id="c17ef-141">Sembolik bağlantılar için istenen davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="c17ef-142">"Sembolik bağlantıları izleyin ve bağlantı hedef (örn. işlem yapma izlemek için" Bu özelliği ayarlayın</span><span class="sxs-lookup"><span data-stu-id="c17ef-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="c17ef-143">bağlantı yerine dosya kopyalama).</span><span class="sxs-lookup"><span data-stu-id="c17ef-143">copy the file instead of the link).</span></span> <span data-ttu-id="c17ef-144">"Bağlantıya (ör. davranacak şekilde yönetmek için" Bu özelliği ayarlayın</span><span class="sxs-lookup"><span data-stu-id="c17ef-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="c17ef-145">bağlantıya Kopyala).</span><span class="sxs-lookup"><span data-stu-id="c17ef-145">copy the link itself).</span></span> <span data-ttu-id="c17ef-146">"Simgesel bağlantılar yoksaymak için yoksay'a için" Bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="c17ef-147">Grup</span><span class="sxs-lookup"><span data-stu-id="c17ef-147">Group</span></span>| <span data-ttu-id="c17ef-148">Adını **grubu** dosya veya dizin sahibi.</span><span class="sxs-lookup"><span data-stu-id="c17ef-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="c17ef-149">Mod</span><span class="sxs-lookup"><span data-stu-id="c17ef-149">Mode</span></span>| <span data-ttu-id="c17ef-150">Sekizlik veya sembolik gösterimde, kaynak için izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="c17ef-151">(örneğin, 777 veya rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="c17ef-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="c17ef-152">Sembolik gösterimini kullanarak, dizin veya dosya gösteren ilk karakteri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c17ef-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="c17ef-153">dependsOn</span><span class="sxs-lookup"><span data-stu-id="c17ef-153">DependsOn</span></span> | <span data-ttu-id="c17ef-154">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c17ef-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c17ef-155">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c17ef-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="c17ef-156">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="c17ef-156">Additional Information</span></span>


<span data-ttu-id="c17ef-157">Linux ve Windows farklı satır sonu karakterleri metin dosyalarında varsayılan olarak ve bunun bazı dosyaları bir Linux bilgisayarda yapılandırılırken beklenmeyen sonuçlara neden olabilir __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="c17ef-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="c17ef-158">Beklenmeyen satır sonu karakterleri tarafından neden olduğu sorunları kaçınarak Linux dosyası içeriğini yönetmek için birden çok yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="c17ef-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="c17ef-159">1. Adım: Bir uzak kaynaktan (http, https veya ftp) dosyasını kopyalayın: İstenen içeriği ile Linux üzerinde bir dosya oluşturun ve yapılandıracağınız düğümde bir web veya ftp sunucusunda erişilebilir hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="c17ef-160">Tanımlama __SourcePath__ özelliğinde __nxFile__ kaynak dosyanın web veya ftp URL'si ile.</span><span class="sxs-lookup"><span data-stu-id="c17ef-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="c17ef-161">2. Adım: PowerShell betiğiyle dosyanın içeriğini okumak [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) ayarlanmasından sonra __$OFS__ Linux satır sonu karakteri kullanmak için özelliği.</span><span class="sxs-lookup"><span data-stu-id="c17ef-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="c17ef-162">3. Adım: Windows ile Linux satır sonu karakterleri satır sonlarını değiştirmek için bir PowerShell işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c17ef-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="c17ef-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="c17ef-163">Example</span></span>

<span data-ttu-id="c17ef-164">Aşağıdaki örnek dizinin sağlar `/opt/mydir` var ve bir dosyanın belirtilen içeriğiyle bu dizinin var olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c17ef-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```