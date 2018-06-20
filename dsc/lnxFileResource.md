---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxFile kaynak için
ms.openlocfilehash: f1eb98092049ae837d144ccf99a84fe5614144e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189865"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="16ea9-103">DSC Linux nxFile kaynak için</span><span class="sxs-lookup"><span data-stu-id="16ea9-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="16ea9-104">**NxFile** kaynak olarak PowerShell istenen durum yapılandırması (DSC) dosyaları ve dizinleri Linux düğümde yönetmek üzere bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="16ea9-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="16ea9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16ea9-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="16ea9-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="16ea9-106">Properties</span></span>

|  <span data-ttu-id="16ea9-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="16ea9-107">Property</span></span> |  <span data-ttu-id="16ea9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16ea9-108">Description</span></span> |
|---|---|
| <span data-ttu-id="16ea9-109">HedefYolu</span><span class="sxs-lookup"><span data-stu-id="16ea9-109">DestinationPath</span></span>| <span data-ttu-id="16ea9-110">Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="16ea9-111">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="16ea9-111">SourcePath</span></span>| <span data-ttu-id="16ea9-112">Dosya veya klasör kaynak kopyalanacak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="16ea9-113">Bu yol, yerel bir yol olabilir veya bir `http/https/ftp` URL.</span><span class="sxs-lookup"><span data-stu-id="16ea9-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="16ea9-114">Uzak `http/https/ftp` URL'leri, yalnızca zaman desteklenen değerini **türü** özelliği dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="16ea9-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="16ea9-115">Emin olun</span><span class="sxs-lookup"><span data-stu-id="16ea9-115">Ensure</span></span>| <span data-ttu-id="16ea9-116">Dosyanın var olup olmadığını denetlemek belirler.</span><span class="sxs-lookup"><span data-stu-id="16ea9-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="16ea9-117">Bu özelliği dosyanın var olduğundan emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="16ea9-118">"Mevcut için" dosya yok emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="16ea9-119">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-119">The default value is "Present".</span></span>|
| <span data-ttu-id="16ea9-120">Tür</span><span class="sxs-lookup"><span data-stu-id="16ea9-120">Type</span></span>| <span data-ttu-id="16ea9-121">Yapılandırılmakta kaynak bir dizin veya bir dosya olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="16ea9-122">Bu özelliği kaynak bir dizin olduğunu belirtmek için "dizin" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="16ea9-123">Kaynak dosya olduğunu belirtmek için "dosyası için" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="16ea9-124">"Dosya" varsayılan değer:</span><span class="sxs-lookup"><span data-stu-id="16ea9-124">The default value is "file"</span></span>|
| <span data-ttu-id="16ea9-125">İçerikler</span><span class="sxs-lookup"><span data-stu-id="16ea9-125">Contents</span></span>| <span data-ttu-id="16ea9-126">Belirli bir dize gibi bir dosyanın içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="16ea9-127">Sağlama</span><span class="sxs-lookup"><span data-stu-id="16ea9-127">Checksum</span></span>| <span data-ttu-id="16ea9-128">İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16ea9-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="16ea9-129">Varsa **sağlama toplamı** belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16ea9-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="16ea9-130">Değerler: "ctime", "mtime" veya "md5".</span><span class="sxs-lookup"><span data-stu-id="16ea9-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="16ea9-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="16ea9-131">Recurse</span></span>| <span data-ttu-id="16ea9-132">Alt dizinleri dahil olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="16ea9-133">Bu özelliği ayarlamak **$true** dahil edilmesi için alt dizinler istediğinizi belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="16ea9-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="16ea9-134">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="16ea9-134">The default is **$false**.</span></span> <span data-ttu-id="16ea9-135">**Not:** bu özellik yalnızca geçerlidir **türü** özelliği dizinine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="16ea9-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="16ea9-136">Force</span><span class="sxs-lookup"><span data-stu-id="16ea9-136">Force</span></span>| <span data-ttu-id="16ea9-137">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="16ea9-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="16ea9-138">Kullanarak **zorla** özelliği gibi hataları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="16ea9-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="16ea9-139">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="16ea9-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="16ea9-140">Bağlantılar</span><span class="sxs-lookup"><span data-stu-id="16ea9-140">Links</span></span>| <span data-ttu-id="16ea9-141">Sembolik bağlantılar için istenen davranış belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="16ea9-142">"Sembolik bağlantılar izleyin ve bağlantıları hedefe (örneğin, hareket izlemek için" Bu özelliği ayarlayın</span><span class="sxs-lookup"><span data-stu-id="16ea9-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="16ea9-143">bağlantı yerine dosya Kopyala).</span><span class="sxs-lookup"><span data-stu-id="16ea9-143">copy the file instead of the link).</span></span> <span data-ttu-id="16ea9-144">"Bağlantısına (örneğin, davranacak şekilde yönetmek için" Bu özelliği ayarlayın</span><span class="sxs-lookup"><span data-stu-id="16ea9-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="16ea9-145">Bağlantıyı Kopyala).</span><span class="sxs-lookup"><span data-stu-id="16ea9-145">copy the link itself).</span></span> <span data-ttu-id="16ea9-146">"Sembolik bağlantılar yoksaymak için yoksay'a için" Bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="16ea9-147">Grup</span><span class="sxs-lookup"><span data-stu-id="16ea9-147">Group</span></span>| <span data-ttu-id="16ea9-148">Adını **grup** dosya veya dizin sahibi.</span><span class="sxs-lookup"><span data-stu-id="16ea9-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="16ea9-149">Mod</span><span class="sxs-lookup"><span data-stu-id="16ea9-149">Mode</span></span>| <span data-ttu-id="16ea9-150">Kaynak için istenen izinleri sekizli veya sembolik gösterimde belirtir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="16ea9-151">(örneğin, 777 veya rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="16ea9-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="16ea9-152">Simgesel gösterimini kullanarak, dizin veya dosya gösteren ilk karakter sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="16ea9-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="16ea9-153">dependsOn</span><span class="sxs-lookup"><span data-stu-id="16ea9-153">DependsOn</span></span> | <span data-ttu-id="16ea9-154">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="16ea9-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="16ea9-155">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="16ea9-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="16ea9-156">Ek Bilgi</span><span class="sxs-lookup"><span data-stu-id="16ea9-156">Additional Information</span></span>


<span data-ttu-id="16ea9-157">Linux ve Windows kullanın farklı satır sonu karakterleri metin dosyalarında varsayılan olarak, ve bu bazı dosyaları ile Linux bilgisayarda yapılandırılırken beklenmeyen sonuçlara neden olabilir __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="16ea9-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="16ea9-158">Beklenmeyen satır sonu karakterleri tarafından nedeniyle oluşan sorunları kaçınarak Linux dosyasının içeriği yönetmek için birden çok yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="16ea9-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="16ea9-159">1. adım: dosyayı bir uzak kaynaktan (http, https veya ftp) kopyalayın: İstenen içeriği ile Linux üzerinde bir dosya oluşturun ve bir web veya ftp sunucusunda erişilebilir yapılandıracağınız düğümlerini hazırlama.</span><span class="sxs-lookup"><span data-stu-id="16ea9-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="16ea9-160">Tanımlamak __KaynakYolu__ özelliğinde __nxFile__ kaynak dosyasının web veya ftp URL'si ile.</span><span class="sxs-lookup"><span data-stu-id="16ea9-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

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


<span data-ttu-id="16ea9-161">2. adım: PowerShell Betiği ile dosya içeriğini okuma [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) ayarlanmasından sonra __$OFS__ Linux satır sonu karakteri kullanmak için özelliği.</span><span class="sxs-lookup"><span data-stu-id="16ea9-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


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


<span data-ttu-id="16ea9-162">3. adım: Windows satır sonları ile Linux satır sonu karakterleri değiştirmek için bir PowerShell işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="16ea9-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

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

## <a name="example"></a><span data-ttu-id="16ea9-163">Örnek</span><span class="sxs-lookup"><span data-stu-id="16ea9-163">Example</span></span>

<span data-ttu-id="16ea9-164">Aşağıdaki örnek dizini sağlar `/opt/mydir` var olduğundan ve belirtilen içeriği dosyasıyla bu dizin mevcut.</span><span class="sxs-lookup"><span data-stu-id="16ea9-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

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