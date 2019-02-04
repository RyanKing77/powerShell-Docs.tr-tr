---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxUser kaynağı
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686015"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="c48e2-103">DSC için Linux nxUser kaynağı</span><span class="sxs-lookup"><span data-stu-id="c48e2-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="c48e2-104">**NxUser** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde yerel kullanıcıları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c48e2-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c48e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c48e2-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c48e2-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c48e2-106">Properties</span></span>

|  <span data-ttu-id="c48e2-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="c48e2-107">Property</span></span> |  <span data-ttu-id="c48e2-108">Belirli bir durumu sağlamak istediğiniz hesap adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="c48e2-109">UserName</span><span class="sxs-lookup"><span data-stu-id="c48e2-109">UserName</span></span>| <span data-ttu-id="c48e2-110">Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c48e2-111">Emin olun</span><span class="sxs-lookup"><span data-stu-id="c48e2-111">Ensure</span></span>| <span data-ttu-id="c48e2-112">Hesap mevcut olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-112">Specifies whether the account exists.</span></span> <span data-ttu-id="c48e2-113">Bu hesabı var olduğundan emin olmak için "var" özelliğini ayarlayın ve "Eksik için" hesabı yok emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c48e2-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="c48e2-114">Tam adı</span><span class="sxs-lookup"><span data-stu-id="c48e2-114">FullName</span></span>| <span data-ttu-id="c48e2-115">Kullanıcı hesabı için kullanılacak tam adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c48e2-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="c48e2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c48e2-116">Description</span></span>| <span data-ttu-id="c48e2-117">Kullanıcı hesabı için açıklama.</span><span class="sxs-lookup"><span data-stu-id="c48e2-117">The description for the user account.</span></span>|
| <span data-ttu-id="c48e2-118">Parola</span><span class="sxs-lookup"><span data-stu-id="c48e2-118">Password</span></span>| <span data-ttu-id="c48e2-119">Linux bilgisayar için uygun biçimde kullanıcılar parola karması.</span><span class="sxs-lookup"><span data-stu-id="c48e2-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="c48e2-120">Genellikle, bir salted SHA-256 veya SHA-512 karma budur.</span><span class="sxs-lookup"><span data-stu-id="c48e2-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="c48e2-121">Bu değer, Debian ve Ubuntu Linux üzerinde mkpasswd komutu ile oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="c48e2-122">Diğer Linux dağıtımları için crypt yöntemi Python'un Crypt Kitaplığı'nın karmasını oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="c48e2-123">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="c48e2-123">Disabled</span></span>| <span data-ttu-id="c48e2-124">Hesabın etkin olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="c48e2-125">Bu özellik kümesine **$true** bu hesabı devre dışı ayarlamanız gerektiğini ve emin olmak için **$false** etkinleştirildiğinden emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="c48e2-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="c48e2-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c48e2-126">PasswordChangeRequired</span></span>| <span data-ttu-id="c48e2-127">Kullanıcının parola değiştirip değiştiremeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="c48e2-128">Bu özellik kümesine **$true** kullanıcı olamaz parolasını değiştirmek, ayarlayın sağlamak ve **$false** parolayı değiştirmek izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="c48e2-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="c48e2-129">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="c48e2-129">The default value is **$false**.</span></span> <span data-ttu-id="c48e2-130">Bu özellik yalnızca kullanıcı hesabını daha önce yok ve oluşturulan değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="c48e2-131">GirişDizini</span><span class="sxs-lookup"><span data-stu-id="c48e2-131">HomeDirectory</span></span>| <span data-ttu-id="c48e2-132">Kullanıcı için giriş dizini.</span><span class="sxs-lookup"><span data-stu-id="c48e2-132">The home directory for the user.</span></span>|
| <span data-ttu-id="c48e2-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="c48e2-133">GroupID</span></span>| <span data-ttu-id="c48e2-134">Kullanıcının birincil grup kimliği.</span><span class="sxs-lookup"><span data-stu-id="c48e2-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="c48e2-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c48e2-135">DependsOn</span></span> | <span data-ttu-id="c48e2-136">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c48e2-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c48e2-137">Örneğin, çalıştırmak istediğiniz kaynak yapılandırma komut dosyası bloğu Kimliğini ilk "ResourceName" ve "ResourceType" kendi türü ise, bu özelliği kullanmaya ilişkin sözdizimini ise `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c48e2-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c48e2-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="c48e2-138">Example</span></span>

<span data-ttu-id="c48e2-139">Aşağıdaki örnek, "monuser" kullanıcı var ve "DBusers" grubunun bir üyesi olduğundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="c48e2-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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