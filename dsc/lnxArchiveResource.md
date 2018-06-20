---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxArchive kaynak için
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188675"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="5c4b1-103">DSC Linux nxArchive kaynak için</span><span class="sxs-lookup"><span data-stu-id="5c4b1-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="5c4b1-104">**NxArchive** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), belirli bir yola Arşivi (.tar, .zip) dosyaları bir Linux düğümündeki açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c4b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c4b1-105">Syntax</span></span>

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="5c4b1-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c4b1-106">Properties</span></span>

|  <span data-ttu-id="5c4b1-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="5c4b1-107">Property</span></span> |  <span data-ttu-id="5c4b1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c4b1-108">Description</span></span> |
|---|---|
| <span data-ttu-id="5c4b1-109">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="5c4b1-109">SourcePath</span></span>| <span data-ttu-id="5c4b1-110">Arşiv dosyasını kaynak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="5c4b1-111">Bu bir .tar olmalıdır .zip, veya. tar.gz dosyasını.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="5c4b1-112">HedefYolu</span><span class="sxs-lookup"><span data-stu-id="5c4b1-112">DestinationPath</span></span>| <span data-ttu-id="5c4b1-113">Arşiv içeriği ayıklanır sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="5c4b1-114">Sağlama</span><span class="sxs-lookup"><span data-stu-id="5c4b1-114">Checksum</span></span>| <span data-ttu-id="5c4b1-115">Kaynak arşiv güncelleştirilip güncelleştirilmediğini belirlenirken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="5c4b1-116">Değerler: "ctime", "mtime" veya "md5".</span><span class="sxs-lookup"><span data-stu-id="5c4b1-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="5c4b1-117">Varsayılan değer "md5" dir.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-117">The default value is "md5".</span></span>|
| <span data-ttu-id="5c4b1-118">Force</span><span class="sxs-lookup"><span data-stu-id="5c4b1-118">Force</span></span>| <span data-ttu-id="5c4b1-119">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="5c4b1-120">Kullanarak **zorla** özelliği gibi hataları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="5c4b1-121">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="5c4b1-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5c4b1-122">DependsOn</span></span> | <span data-ttu-id="5c4b1-123">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5c4b1-124">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="5c4b1-125">Emin olun</span><span class="sxs-lookup"><span data-stu-id="5c4b1-125">Ensure</span></span>| <span data-ttu-id="5c4b1-126">Arşiv içeriğini adresindeki var olup olmadığını denetlemek belirler **hedef**.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="5c4b1-127">Bu özelliği içeriği mevcut emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="5c4b1-128">"Mevcut için" mevcut emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="5c4b1-129">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="5c4b1-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c4b1-130">Example</span></span>

<span data-ttu-id="5c4b1-131">Aşağıdaki örnekte nasıl kullanılacağını gösterir **nxArchive** bir arşiv dosyasının içeriğini adlı emin olmak için kaynak `website.tar` var ve belirli bir hedefe ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="5c4b1-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```