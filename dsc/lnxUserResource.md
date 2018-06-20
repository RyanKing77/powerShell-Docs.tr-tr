---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxUser kaynak için
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218935"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="1b42e-103">DSC Linux nxUser kaynak için</span><span class="sxs-lookup"><span data-stu-id="1b42e-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="1b42e-104">**NxUser** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümde yerel kullanıcıları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b42e-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b42e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b42e-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="1b42e-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b42e-106">Properties</span></span>

|  <span data-ttu-id="1b42e-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="1b42e-107">Property</span></span> |  <span data-ttu-id="1b42e-108">Belirli bir durumu sağlamak istediğiniz hesap adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="1b42e-109">UserName</span><span class="sxs-lookup"><span data-stu-id="1b42e-109">UserName</span></span>| <span data-ttu-id="1b42e-110">Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="1b42e-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="1b42e-111">Ensure</span></span>| <span data-ttu-id="1b42e-112">Hesap var olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-112">Specifies whether the account exists.</span></span> <span data-ttu-id="1b42e-113">Bu hesabı var olduğundan emin olmak için "var" özelliğine ayarlayın ve "Mevcut için" hesap yok emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1b42e-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="1b42e-114">FullName</span><span class="sxs-lookup"><span data-stu-id="1b42e-114">FullName</span></span>| <span data-ttu-id="1b42e-115">Kullanıcı hesabı için kullanılacak tam adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="1b42e-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="1b42e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b42e-116">Description</span></span>| <span data-ttu-id="1b42e-117">Kullanıcı hesabı açıklaması.</span><span class="sxs-lookup"><span data-stu-id="1b42e-117">The description for the user account.</span></span>|
| <span data-ttu-id="1b42e-118">Parola</span><span class="sxs-lookup"><span data-stu-id="1b42e-118">Password</span></span>| <span data-ttu-id="1b42e-119">Linux bilgisayar için uygun biçimde kullanıcılar parola karması.</span><span class="sxs-lookup"><span data-stu-id="1b42e-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="1b42e-120">Genellikle, bir güvenlik SHA-256 ve SHA-512 karma budur.</span><span class="sxs-lookup"><span data-stu-id="1b42e-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="1b42e-121">Debian ve Ubuntu Linux üzerinde bu değer mkpasswd komutuyla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="1b42e-122">Python'un Crypt kitaplığının crypt yöntemi diğer Linux distro'lar için karma değeri üretmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b42e-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="1b42e-123">Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="1b42e-123">Disabled</span></span>| <span data-ttu-id="1b42e-124">Hesabın etkin olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="1b42e-125">Bu özelliği ayarlamak **$true** bu hesap devre dışı ve ayarlamak olduğunu emin olmak için **$false** için etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1b42e-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="1b42e-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="1b42e-126">PasswordChangeRequired</span></span>| <span data-ttu-id="1b42e-127">Kullanıcı parolalarını değiştirip değiştiremeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="1b42e-128">Bu özelliği ayarlamak **$true** kullanıcı olamaz parolasını değiştirmek ve ayarlamak emin olmak için **$false** parola değiştirmeye izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="1b42e-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="1b42e-129">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="1b42e-129">The default value is **$false**.</span></span> <span data-ttu-id="1b42e-130">Bu özellik, yalnızca kullanıcı hesabını daha önce yoktu ve oluşturuldu değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="1b42e-131">GirişDizini</span><span class="sxs-lookup"><span data-stu-id="1b42e-131">HomeDirectory</span></span>| <span data-ttu-id="1b42e-132">Kullanıcı için giriş dizini.</span><span class="sxs-lookup"><span data-stu-id="1b42e-132">The home directory for the user.</span></span>|
| <span data-ttu-id="1b42e-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="1b42e-133">GroupID</span></span>| <span data-ttu-id="1b42e-134">Kullanıcının birincil grup kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b42e-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="1b42e-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1b42e-135">DependsOn</span></span> | <span data-ttu-id="1b42e-136">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b42e-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b42e-137">Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğunda Kimliğini ilk "ResourceName" ve "ResourceType" türü ise, bu özelliği kullanan sözdizimi ise `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1b42e-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="1b42e-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b42e-138">Example</span></span>

<span data-ttu-id="1b42e-139">Aşağıdaki örnekte, kullanıcı "monuser" mevcut ve "DBusers" grubunun bir üyesi olduğundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b42e-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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