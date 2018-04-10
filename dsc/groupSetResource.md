---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
description: Hedef düğümde bulunan yerel grupları yönetmek için bir mekanizma sağlar.
title: DSC GroupSet kaynağı
ms.openlocfilehash: 4f8fc21806fdb4eb06e0d915d5b6ca229357a210
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="28956-104">DSC GroupSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="28956-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="28956-105">İçin geçerlidir: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="28956-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="28956-106">**GroupSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), yerel gruplar hedef düğümde bulunan yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="28956-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="28956-107">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [kaynak grubunda](groupResource.md) belirtilen her grup için `GroupName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="28956-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="28956-108">Bu kaynak ekleme ve/veya birden fazla gruba üye aynı listesi kaldırmak, birden fazla grubu kaldırmak veya üyeleri aynı listesiyle birden fazla grubu ekleme yapmak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="28956-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="28956-109">Sözdizimi ##</span><span class="sxs-lookup"><span data-stu-id="28956-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="28956-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="28956-110">Properties</span></span>

|  <span data-ttu-id="28956-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="28956-111">Property</span></span>  |  <span data-ttu-id="28956-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28956-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="28956-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="28956-113">GroupName</span></span>| <span data-ttu-id="28956-114">Belirli bir durumu sağlamak istediğiniz grupların adları.</span><span class="sxs-lookup"><span data-stu-id="28956-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="28956-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="28956-115">MembersToExclude</span></span>| <span data-ttu-id="28956-116">Gruplar mevcut üyeliğinden üyeleri kaldırmak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="28956-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="28956-117">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="28956-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="28956-118">Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="28956-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="28956-119">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28956-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="28956-120">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="28956-120">Credential</span></span>| <span data-ttu-id="28956-121">Uzak kaynaklara erişmek için gerekli kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="28956-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="28956-122">**Not**: Bu hesap tüm yerel olmayan hesapları grubuna eklemek için uygun Active Directory izinleri olması gerekir; aksi takdirde bir hata ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="28956-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="28956-123">Emin olun</span><span class="sxs-lookup"><span data-stu-id="28956-123">Ensure</span></span>| <span data-ttu-id="28956-124">Gruplar mevcut olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28956-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="28956-125">Bu özelliği grubu mevcut emin olmak için "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="28956-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="28956-126">"(Varsayılan değer) sunmak için" olarak ayarlanması grupların bulunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="28956-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="28956-127">Üyeler</span><span class="sxs-lookup"><span data-stu-id="28956-127">Members</span></span>| <span data-ttu-id="28956-128">Belirtilen üyeleriyle geçerli grup üyeliğini değiştirmek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="28956-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="28956-129">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="28956-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="28956-130">Bu özellik bir yapılandırmada ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği.</span><span class="sxs-lookup"><span data-stu-id="28956-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="28956-131">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28956-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="28956-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="28956-132">MembersToInclude</span></span>| <span data-ttu-id="28956-133">Grubun var olan üyeliğini üye eklemek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="28956-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="28956-134">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="28956-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="28956-135">Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="28956-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="28956-136">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28956-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="28956-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="28956-137">DependsOn</span></span> | <span data-ttu-id="28956-138">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="28956-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="28956-139">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="28956-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="28956-140">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="28956-140">Example 1</span></span>

<span data-ttu-id="28956-141">Aşağıdaki örnekte, "myGroup" ve "myOtherGroup" adlı iki grup mevcut olduğundan emin olun gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28956-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

><span data-ttu-id="28956-142">**Not:** Bu örnek düz metin kimlik bilgileri kolaylık sağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="28956-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="28956-143">Yapılandırma MOF dosyasındaki kimlik bilgilerini şifrelemek hakkında daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="28956-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>