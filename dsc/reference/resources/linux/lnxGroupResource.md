---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxGroup kaynağı
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077872"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="eaa19-103">DSC için Linux nxGroup kaynağı</span><span class="sxs-lookup"><span data-stu-id="eaa19-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="eaa19-104">**NxGroup** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde yerel grupları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaa19-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="eaa19-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaa19-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="eaa19-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eaa19-106">Properties</span></span>

|  <span data-ttu-id="eaa19-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="eaa19-107">Property</span></span> |  <span data-ttu-id="eaa19-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaa19-108">Description</span></span> |
|---|---|
| <span data-ttu-id="eaa19-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="eaa19-109">GroupName</span></span>| <span data-ttu-id="eaa19-110">Belirli bir durumu emin olmak istediğiniz grubun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="eaa19-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="eaa19-111">Ensure</span></span>| <span data-ttu-id="eaa19-112">Grubun mevcut olup olmadığını denetleyin belirler.</span><span class="sxs-lookup"><span data-stu-id="eaa19-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="eaa19-113">"Var" grubu var. olmak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eaa19-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="eaa19-114">Kümesi "Yok" grubu sağlamak için mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="eaa19-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="eaa19-115">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-115">The default value is "Present".</span></span>|
| <span data-ttu-id="eaa19-116">Üyeler</span><span class="sxs-lookup"><span data-stu-id="eaa19-116">Members</span></span>| <span data-ttu-id="eaa19-117">Bir grup oluşturacak olan üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="eaa19-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="eaa19-118">MembersToInclude</span></span>| <span data-ttu-id="eaa19-119">Sağlamak istediğiniz kullanıcıları grubunun bir üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="eaa19-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="eaa19-120">MembersToExclude</span></span>| <span data-ttu-id="eaa19-121">Sağlamak istediğiniz kullanıcıları grup üyesi olmayan belirtir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="eaa19-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="eaa19-122">PreferredGroupID</span></span>| <span data-ttu-id="eaa19-123">Mümkünse, Grup Kimliği sağlanan değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eaa19-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="eaa19-124">Grup Kimliği şu anda kullanımda ise sonraki kullanılabilir grup kimliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eaa19-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="eaa19-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="eaa19-125">DependsOn</span></span> | <span data-ttu-id="eaa19-126">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaa19-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eaa19-127">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="eaa19-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="eaa19-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaa19-128">Example</span></span>

<span data-ttu-id="eaa19-129">Aşağıdaki örnek, kullanıcı 'monuser' var ve 'DBusers' grubunun bir üyesi olduğundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaa19-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```