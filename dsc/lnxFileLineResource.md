---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxFileLine kaynak için"
ms.openlocfilehash: 281f08c1dbf42372762a2b1b9838427b910ea791
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="e04c8-103">DSC Linux nxFileLine kaynak için</span><span class="sxs-lookup"><span data-stu-id="e04c8-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="e04c8-104">**NxFileLine** kaynak olarak PowerShell istenen durum yapılandırması (DSC) yapılandırma dosyasında bir Linux düğümünde satırları yönetmek üzere bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e04c8-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e04c8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e04c8-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="e04c8-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e04c8-106">Properties</span></span>

|  <span data-ttu-id="e04c8-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="e04c8-107">Property</span></span> |  <span data-ttu-id="e04c8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e04c8-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="e04c8-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="e04c8-109">FilePath</span></span>| <span data-ttu-id="e04c8-110">Hedef düğümde bulunan satırları yönetmek için dosyanın tam yolu.</span><span class="sxs-lookup"><span data-stu-id="e04c8-110">The full path to the file to manage lines in on the target node.</span></span>| 
| <span data-ttu-id="e04c8-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="e04c8-111">ContainsLine</span></span>| <span data-ttu-id="e04c8-112">Dosyada emin olmak için bir satır var.</span><span class="sxs-lookup"><span data-stu-id="e04c8-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="e04c8-113">Dosya yoksa, bu satırın dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="e04c8-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="e04c8-114">**ContainsLine** zorunludur, ancak boş bir dize olarak ayarlanabilir ('ContainsLine = ''') değil gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="e04c8-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>| 
| <span data-ttu-id="e04c8-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="e04c8-115">DoesNotContainPattern</span></span>| <span data-ttu-id="e04c8-116">Normal ifade deseni dosyasında bulunmamalıdır satırlar için.</span><span class="sxs-lookup"><span data-stu-id="e04c8-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="e04c8-117">Bu normal bir ifadeyle eşleşen dosyasında bulunan tüm satırlar için dosyadan satır kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e04c8-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>| 
| <span data-ttu-id="e04c8-118">dependsOn</span><span class="sxs-lookup"><span data-stu-id="e04c8-118">DependsOn</span></span> | <span data-ttu-id="e04c8-119">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="e04c8-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e04c8-120">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e04c8-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="e04c8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e04c8-121">Example</span></span>

<span data-ttu-id="e04c8-122">Bu örnek kullanılmasını gösterir **nxFileLine** yapılandırmak için kaynak `/etc/sudoers` dosyası, kullanıcı sağlanarak: monuser değil requiretty için yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="e04c8-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

