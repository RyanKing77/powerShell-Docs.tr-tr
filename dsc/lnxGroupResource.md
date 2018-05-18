---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxGroup kaynak için
ms.openlocfilehash: 9651f3affc9b040a7ef8e7bf8d5ab4cebcca8128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="f932c-103">DSC Linux nxGroup kaynak için</span><span class="sxs-lookup"><span data-stu-id="f932c-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="f932c-104">**NxGroup** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümde yerel grupları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f932c-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f932c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f932c-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="f932c-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f932c-106">Properties</span></span>

|  <span data-ttu-id="f932c-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="f932c-107">Property</span></span> |  <span data-ttu-id="f932c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f932c-108">Description</span></span> |
|---|---|
| <span data-ttu-id="f932c-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="f932c-109">GroupName</span></span>| <span data-ttu-id="f932c-110">Belirli bir durumu sağlamak istediğiniz grubun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f932c-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f932c-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="f932c-111">Ensure</span></span>| <span data-ttu-id="f932c-112">Grubun var olup olmadığını denetlemek belirler.</span><span class="sxs-lookup"><span data-stu-id="f932c-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="f932c-113">Bu özelliği Grup mevcut emin olmak için "var" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f932c-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="f932c-114">"Mevcut için" grubu yok emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f932c-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="f932c-115">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f932c-115">The default value is "Present".</span></span>|
| <span data-ttu-id="f932c-116">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f932c-116">Members</span></span>| <span data-ttu-id="f932c-117">Grup form üyeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f932c-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="f932c-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="f932c-118">MembersToInclude</span></span>| <span data-ttu-id="f932c-119">Sağlamak istediğiniz kullanıcıları grubunun bir üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f932c-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="f932c-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="f932c-120">MembersToExclude</span></span>| <span data-ttu-id="f932c-121">Sağlamak istediğiniz kullanıcıları grubunun üyesi olmayan belirtir.</span><span class="sxs-lookup"><span data-stu-id="f932c-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="f932c-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="f932c-122">PreferredGroupID</span></span>| <span data-ttu-id="f932c-123">Grup Kimliği için sağlanan değer mümkünse ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f932c-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="f932c-124">Grup Kimliği şu anda kullanımda ise, bir sonraki kullanılabilir grup kimliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f932c-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="f932c-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f932c-125">DependsOn</span></span> | <span data-ttu-id="f932c-126">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="f932c-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f932c-127">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f932c-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="f932c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f932c-128">Example</span></span>

<span data-ttu-id="f932c-129">Aşağıdaki örnekte, kullanıcı "monuser" mevcut ve "DBusers" grubunun bir üyesi olduğundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="f932c-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```