---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Group kaynağı
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054977"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="2f84f-103">DSC Group kaynağı</span><span class="sxs-lookup"><span data-stu-id="2f84f-103">DSC Group Resource</span></span>

> <span data-ttu-id="2f84f-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2f84f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2f84f-105">Group kaynağı, Windows PowerShell Desired State Configuration (DSC), hedef düğümde yerel grupları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f84f-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f84f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f84f-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="2f84f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f84f-107">Properties</span></span>

|  <span data-ttu-id="2f84f-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="2f84f-108">Property</span></span>  |  <span data-ttu-id="2f84f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f84f-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="2f84f-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="2f84f-110">GroupName</span></span>| <span data-ttu-id="2f84f-111">Belirli bir durumu emin olmak istediğiniz grubun adı.</span><span class="sxs-lookup"><span data-stu-id="2f84f-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2f84f-112">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="2f84f-112">Credential</span></span>| <span data-ttu-id="2f84f-113">Uzak kaynaklara erişmek için gerekli kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="2f84f-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="2f84f-114">**Not**: Bu hesap, tüm yerel olmayan hesapları grubuna eklemek için Active Directory iznine sahip olmalıdır; Aksi takdirde, yapılandırmasını hedef düğümde yürütülürken bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="2f84f-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="2f84f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f84f-115">Description</span></span>| <span data-ttu-id="2f84f-116">Grup açıklaması.</span><span class="sxs-lookup"><span data-stu-id="2f84f-116">The description of the group.</span></span>|
| <span data-ttu-id="2f84f-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="2f84f-117">Ensure</span></span>| <span data-ttu-id="2f84f-118">Grubun var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f84f-118">Indicates if the group exists.</span></span> <span data-ttu-id="2f84f-119">"Yok" grubu yok sağlamak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f84f-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="2f84f-120">"(Varsayılan değer) sunmak için" ayarı, grubun var olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f84f-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="2f84f-121">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2f84f-121">Members</span></span>| <span data-ttu-id="2f84f-122">Belirtilen üye ile geçerli grup üyeliğini değiştirmek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f84f-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="2f84f-123">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="2f84f-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f84f-124">Bir yapılandırmada bu özelliği ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği.</span><span class="sxs-lookup"><span data-stu-id="2f84f-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="2f84f-125">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f84f-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="2f84f-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="2f84f-126">MembersToExclude</span></span>| <span data-ttu-id="2f84f-127">Grubun mevcut üyelikten üyeleri kaldırmak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f84f-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="2f84f-128">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="2f84f-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f84f-129">Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="2f84f-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2f84f-130">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f84f-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="2f84f-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="2f84f-131">MembersToInclude</span></span>| <span data-ttu-id="2f84f-132">Mevcut üyelik grubunun üyeleri eklemek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2f84f-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="2f84f-133">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="2f84f-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f84f-134">Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="2f84f-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2f84f-135">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f84f-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="2f84f-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="2f84f-136">DependsOn</span></span> | <span data-ttu-id="2f84f-137">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f84f-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2f84f-138">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="2f84f-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="2f84f-139">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="2f84f-139">Example 1</span></span>

<span data-ttu-id="2f84f-140">Aşağıdaki örnek, "Testgrubu" adlı bir grup mevcut olduğundan emin olmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f84f-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="2f84f-141">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="2f84f-141">Example 2</span></span>

<span data-ttu-id="2f84f-142">Aşağıdaki örnek, bir Active Directory kullanıcısı nerede zaten bir PSCredential yerel yönetici hesabı için kullandığınız birden çok makine Laboratuvar yapının bir parçası olarak yerel administrators grubuna eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f84f-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span>
<span data-ttu-id="2f84f-143">Bu da etki alanı yönetici hesabı (etki alanı yükseltme sonrasında) kullanıldıkça, ardından bu mevcut PSCredential etki alanında kolay bir kimlik bilgisi ile dönüştürmek ihtiyacımız var.</span><span class="sxs-lookup"><span data-stu-id="2f84f-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="2f84f-144">Ardından yerel Yöneticiler grubuna üye sunucusunda bir etki alanı kullanıcısı ekleyebiliriz.</span><span class="sxs-lookup"><span data-stu-id="2f84f-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="2f84f-145">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="2f84f-145">Example 3</span></span>

<span data-ttu-id="2f84f-146">Aşağıdaki örnek, yerel bir grup TigerTeamAdmins emin olmak gösterilmektedir, sunucuda bir özel etki alanı hesabı Contoso\JerryG TigerTeamSource.Contoso.Com içermiyor.</span><span class="sxs-lookup"><span data-stu-id="2f84f-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```