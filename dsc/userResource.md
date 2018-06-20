---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kullanıcı kaynağı
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189661"
---
#<a name="dsc-user-resource"></a><span data-ttu-id="feebe-103">DSC kullanıcı kaynak #</span><span class="sxs-lookup"><span data-stu-id="feebe-103">DSC User Resource#</span></span>


><span data-ttu-id="feebe-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="feebe-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="feebe-105">__Kullanıcı__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan yerel kullanıcı hesaplarını yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="feebe-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="feebe-106">Sözdizimi ##</span><span class="sxs-lookup"><span data-stu-id="feebe-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="feebe-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="feebe-107">Properties</span></span>
|  <span data-ttu-id="feebe-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="feebe-108">Property</span></span>  |  <span data-ttu-id="feebe-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feebe-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="feebe-110">UserName</span><span class="sxs-lookup"><span data-stu-id="feebe-110">UserName</span></span>| <span data-ttu-id="feebe-111">Belirli bir durumu sağlamak istediğiniz hesap adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="feebe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feebe-112">Description</span></span>| <span data-ttu-id="feebe-113">Kullanıcı hesabı için kullanmak istediğiniz açıklamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="feebe-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="feebe-114">Devre Dışı</span><span class="sxs-lookup"><span data-stu-id="feebe-114">Disabled</span></span>| <span data-ttu-id="feebe-115">Hesabın etkin olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="feebe-116">Bu özelliği ayarlamak __$true__ bu hesap devre dışı ve ayarlamak olduğunu emin olmak için __$false__ için etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="feebe-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="feebe-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="feebe-117">Ensure</span></span>| <span data-ttu-id="feebe-118">Hesabının mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-118">Indicates if the account exists.</span></span> <span data-ttu-id="feebe-119">Bu hesabı var olduğundan emin olmak için "var" özelliğine ayarlayın ve "Mevcut için" hesap yok emin olmak için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="feebe-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="feebe-120">FullName</span><span class="sxs-lookup"><span data-stu-id="feebe-120">FullName</span></span>| <span data-ttu-id="feebe-121">Kullanıcı hesabı için kullanmak istediğiniz tam adı bir dizeyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="feebe-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="feebe-122">Parola</span><span class="sxs-lookup"><span data-stu-id="feebe-122">Password</span></span>| <span data-ttu-id="feebe-123">Bu hesap için kullanmak istediğiniz parolayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="feebe-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="feebe-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="feebe-125">Kullanıcının parolayı değiştirirseniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="feebe-126">Bu özelliği ayarlamak __$true__ kullanıcı olamaz parolasını değiştirmek ve ayarlamak emin olmak için __$false__ parola değiştirmeye izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="feebe-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="feebe-127">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="feebe-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="feebe-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="feebe-128">PasswordChangeRequired</span></span>| <span data-ttu-id="feebe-129">Kullanıcı bir sonraki oturum açmada parola değiştirmeli gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="feebe-130">Bu özelliği ayarlamak __$true__ kullanıcı parolasını değiştirmeniz gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="feebe-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="feebe-131">Varsayılan değer __$true__.</span><span class="sxs-lookup"><span data-stu-id="feebe-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="feebe-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="feebe-132">PasswordNeverExpires</span></span>| <span data-ttu-id="feebe-133">Parola sona erecek gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-133">Indicates if the password will expire.</span></span> <span data-ttu-id="feebe-134">Bu hesap süresiz için parola bu özelliği ayarlamak emin olmak için __$true__ve ayarlamak __$false__ parola süresi dolacak durumunda.</span><span class="sxs-lookup"><span data-stu-id="feebe-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="feebe-135">Varsayılan değer __$false__.</span><span class="sxs-lookup"><span data-stu-id="feebe-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="feebe-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="feebe-136">DependsOn</span></span> | <span data-ttu-id="feebe-137">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="feebe-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="feebe-138">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="feebe-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="feebe-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="feebe-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```