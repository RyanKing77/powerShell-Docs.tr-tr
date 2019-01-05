---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxArchive kaynağı
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048712"
---
# <a name="dsc-for-linux-nxarchive-resource"></a><span data-ttu-id="85b6e-103">DSC için Linux nxArchive kaynağı</span><span class="sxs-lookup"><span data-stu-id="85b6e-103">DSC for Linux nxArchive Resource</span></span>

<span data-ttu-id="85b6e-104">**NxArchive** kaynak içinde PowerShell Desired State Configuration (DSC), belirli bir yola Arşivi (.tar, .zip) dosyaları bir Linux düğümde açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="85b6e-104">The **nxArchive** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.tar, .zip) files at a specific path on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="85b6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85b6e-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="85b6e-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="85b6e-106">Properties</span></span>

|  <span data-ttu-id="85b6e-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="85b6e-107">Property</span></span> |  <span data-ttu-id="85b6e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85b6e-108">Description</span></span> |
|---|---|
| <span data-ttu-id="85b6e-109">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="85b6e-109">SourcePath</span></span>| <span data-ttu-id="85b6e-110">Arşiv dosyasının kaynak yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b6e-110">Specifies the source path of the archive file.</span></span> <span data-ttu-id="85b6e-111">Bu bir .tar olmalıdır, .zip veya. tar.gz dosyasını.</span><span class="sxs-lookup"><span data-stu-id="85b6e-111">This should be a .tar, .zip, or .tar.gz file.</span></span> |
| <span data-ttu-id="85b6e-112">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="85b6e-112">DestinationPath</span></span>| <span data-ttu-id="85b6e-113">Arşiv içeriğini ayıklanan sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="85b6e-113">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="85b6e-114">Sağlama</span><span class="sxs-lookup"><span data-stu-id="85b6e-114">Checksum</span></span>| <span data-ttu-id="85b6e-115">Kaynak arşiv güncelleştirilip güncelleştirilmediğini belirlenirken kullanılacak türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85b6e-115">Defines the type to use when determining whether the source archive has been updated.</span></span> <span data-ttu-id="85b6e-116">Değerler: "ctime", "mtime" veya "md5".</span><span class="sxs-lookup"><span data-stu-id="85b6e-116">Values are: "ctime", "mtime", or "md5".</span></span> <span data-ttu-id="85b6e-117">Varsayılan değer "md5"'tir.</span><span class="sxs-lookup"><span data-stu-id="85b6e-117">The default value is "md5".</span></span>|
| <span data-ttu-id="85b6e-118">Force</span><span class="sxs-lookup"><span data-stu-id="85b6e-118">Force</span></span>| <span data-ttu-id="85b6e-119">Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="85b6e-119">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="85b6e-120">Kullanarak **zorla** özelliği, bu tür hatalar'ı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="85b6e-120">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="85b6e-121">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="85b6e-121">The default value is **$false**.</span></span>|
| <span data-ttu-id="85b6e-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="85b6e-122">DependsOn</span></span> | <span data-ttu-id="85b6e-123">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="85b6e-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="85b6e-124">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="85b6e-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="85b6e-125">Emin olun</span><span class="sxs-lookup"><span data-stu-id="85b6e-125">Ensure</span></span>| <span data-ttu-id="85b6e-126">Arşiv içeriğini, mevcut olup olmadığını denetleyin belirler **hedef**.</span><span class="sxs-lookup"><span data-stu-id="85b6e-126">Determines whether to check if the content of the archive exists at the **Destination**.</span></span> <span data-ttu-id="85b6e-127">Bu özelliği içeriği mevcut emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="85b6e-127">Set this property to "Present" to ensure the contents exist.</span></span> <span data-ttu-id="85b6e-128">"Eksik için" mevcut emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="85b6e-128">Set it to "Absent" to ensure they do not exist.</span></span> <span data-ttu-id="85b6e-129">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="85b6e-129">The default value is "Present".</span></span>|

## <a name="example"></a><span data-ttu-id="85b6e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="85b6e-130">Example</span></span>

<span data-ttu-id="85b6e-131">Aşağıdaki örnek nasıl kullanılacağını gösterir **nxArchive** Arşiv dosyasının içeriğini adlı emin olmak için kaynak `website.tar` var ve belirli bir hedefe ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="85b6e-131">The following example shows how to use the **nxArchive** resource to ensure that the contents of an archive file called `website.tar` exist and are extracted at a given destination.</span></span>

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