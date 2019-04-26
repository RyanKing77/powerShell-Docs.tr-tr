---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
description: Hedef düğüm üzerindeki yerel grupların yönetmek için bir mekanizma sağlar.
title: DSC GroupSet kaynağı
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077186"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="649ab-104">DSC GroupSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="649ab-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="649ab-105">Uygulama hedefi: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="649ab-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="649ab-106">**GroupSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC) hedef düğümde yerel grupları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="649ab-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="649ab-107">Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [kaynak grubunda](groupResource.md) belirtilen her grup için `GroupName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="649ab-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="649ab-108">Bu kaynak, ekleme ve/veya aynı birden fazla gruba üye listesini Kaldır, birden fazla grubunu kaldırın veya aynı listesiyle birden fazla Grup üyeleri eklemek istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ab-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="649ab-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="649ab-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="649ab-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="649ab-110">Properties</span></span>

|  <span data-ttu-id="649ab-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="649ab-111">Property</span></span>  |  <span data-ttu-id="649ab-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="649ab-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="649ab-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="649ab-113">GroupName</span></span>| <span data-ttu-id="649ab-114">Belirli bir durumu sağlamak istediğiniz grupların adları.</span><span class="sxs-lookup"><span data-stu-id="649ab-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="649ab-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="649ab-115">MembersToExclude</span></span>| <span data-ttu-id="649ab-116">Gruplar mevcut üyelikten üyeleri kaldırmak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ab-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="649ab-117">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="649ab-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="649ab-118">Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="649ab-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="649ab-119">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ab-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="649ab-120">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="649ab-120">Credential</span></span>| <span data-ttu-id="649ab-121">Uzak kaynaklara erişmek için gerekli kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="649ab-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="649ab-122">**Not**: Bu hesap, tüm yerel olmayan hesapları grubuna eklemek için Active Directory iznine sahip olmalıdır; Aksi takdirde bir hata meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="649ab-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="649ab-123">Emin olun</span><span class="sxs-lookup"><span data-stu-id="649ab-123">Ensure</span></span>| <span data-ttu-id="649ab-124">Gruplar mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="649ab-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="649ab-125">"Yok" grubu mevcut sağlamak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="649ab-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="649ab-126">"(Varsayılan değer) sunmak için" ayar grupları mevcut olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="649ab-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="649ab-127">Üyeler</span><span class="sxs-lookup"><span data-stu-id="649ab-127">Members</span></span>| <span data-ttu-id="649ab-128">Belirtilen üye ile geçerli grup üyeliğini değiştirmek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ab-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="649ab-129">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="649ab-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="649ab-130">Bir yapılandırmada bu özelliği ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği.</span><span class="sxs-lookup"><span data-stu-id="649ab-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="649ab-131">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ab-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="649ab-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="649ab-132">MembersToInclude</span></span>| <span data-ttu-id="649ab-133">Mevcut üyelik grubunun üyeleri eklemek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="649ab-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="649ab-134">Bu özelliğin değeri form dizeler dizisidir *etki alanı*\\*UserName*.</span><span class="sxs-lookup"><span data-stu-id="649ab-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="649ab-135">Bir yapılandırmada bu özelliği ayarlarsanız, kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="649ab-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="649ab-136">Bunun yapılması, bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649ab-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="649ab-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="649ab-137">DependsOn</span></span> | <span data-ttu-id="649ab-138">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="649ab-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="649ab-139">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için söz dizimi ' DependsOn "[= ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="649ab-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="649ab-140">Örnek 1: Kalmasını sağlama grup yok</span><span class="sxs-lookup"><span data-stu-id="649ab-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="649ab-141">Aşağıdaki örnek, "myGroup" ve "myOtherGroup" adlı iki grup mevcut olduğundan emin olun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="649ab-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="649ab-142">Bu örnekte, kolaylık olması için düz metin kimlik bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="649ab-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="649ab-143">Yapılandırma MOF dosyasının kimlik bilgilerini şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyasının güvenliğini sağlama](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="649ab-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
