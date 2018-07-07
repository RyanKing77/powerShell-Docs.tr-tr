---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxFileLine kaynağı
ms.openlocfilehash: f2a989dd3a6746948e09ba94e279c02be8ebe2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893306"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="19a81-103">DSC için Linux nxFileLine kaynağı</span><span class="sxs-lookup"><span data-stu-id="19a81-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="19a81-104">**NxFileLine** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde bir yapılandırma dosyası içindeki satırların yönetmek üzere bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="19a81-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="19a81-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19a81-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="19a81-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="19a81-106">Properties</span></span>

|  <span data-ttu-id="19a81-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="19a81-107">Property</span></span> |  <span data-ttu-id="19a81-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19a81-108">Description</span></span> |
|---|---|
| <span data-ttu-id="19a81-109">Dosya yolu</span><span class="sxs-lookup"><span data-stu-id="19a81-109">FilePath</span></span>| <span data-ttu-id="19a81-110">Hedef düğümde bulunan satırları yönetmek için dosyanın tam yolu.</span><span class="sxs-lookup"><span data-stu-id="19a81-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="19a81-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="19a81-111">ContainsLine</span></span>| <span data-ttu-id="19a81-112">Dosyada emin olmak için bir satır var.</span><span class="sxs-lookup"><span data-stu-id="19a81-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="19a81-113">Dosyasında yoksa, bu satırı dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="19a81-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="19a81-114">**ContainsLine** zorunludur, ancak boş bir dize olarak ayarlanabilir (`ContainsLine = ""`) durumunda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="19a81-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span>|
| <span data-ttu-id="19a81-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="19a81-115">DoesNotContainPattern</span></span>| <span data-ttu-id="19a81-116">Dosyasında bulunmamalıdır satırlar için normal ifade deseni.</span><span class="sxs-lookup"><span data-stu-id="19a81-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="19a81-117">Bu normal bir ifadeyle eşleşen dosyasında bulunan tüm satırlar için satırın dosyasından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="19a81-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="19a81-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="19a81-118">DependsOn</span></span> | <span data-ttu-id="19a81-119">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19a81-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="19a81-120">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="19a81-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="19a81-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="19a81-121">Example</span></span>

<span data-ttu-id="19a81-122">Kullanarak bu örnek gösterir **nxFileLine** yapılandırmak için kaynak `/etc/sudoers` kullanıcı sağlanarak dosyası: monuser değil requiretty için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="19a81-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```