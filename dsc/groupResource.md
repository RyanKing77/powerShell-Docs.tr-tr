---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC grubu kaynağı"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="e4745-103">DSC grubu kaynağı</span><span class="sxs-lookup"><span data-stu-id="e4745-103">DSC Group Resource</span></span>

> <span data-ttu-id="e4745-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4745-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4745-105">Grup kaynağına, Windows PowerShell istenen durum yapılandırması (DSC) hedef düğümde bulunan yerel grupları yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4745-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4745-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4745-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="e4745-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e4745-107">Properties</span></span>

|  <span data-ttu-id="e4745-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="e4745-108">Property</span></span>  |  <span data-ttu-id="e4745-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4745-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="e4745-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="e4745-110">GroupName</span></span>| <span data-ttu-id="e4745-111">Belirli bir durumu sağlamak istediğiniz grubunun adı.</span><span class="sxs-lookup"><span data-stu-id="e4745-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="e4745-112">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="e4745-112">Credential</span></span>| <span data-ttu-id="e4745-113">Uzak kaynaklara erişmek için gerekli kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e4745-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="e4745-114">**Not**: Bu hesabın tüm yerel olmayan hesapları grubuna eklemek için uygun Active Directory izinleri olması gerekir; aksi halde, yapılandırmasını hedef düğümde çalıştırıldığında bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="e4745-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="e4745-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4745-115">Description</span></span>| <span data-ttu-id="e4745-116">Grubun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e4745-116">The description of the group.</span></span>| 
| <span data-ttu-id="e4745-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="e4745-117">Ensure</span></span>| <span data-ttu-id="e4745-118">Grubun var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4745-118">Indicates if the group exists.</span></span> <span data-ttu-id="e4745-119">Bu özelliği grubu yok emin olmak için "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e4745-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="e4745-120">"(Varsayılan değer) sunmak için" olarak ayarlanması, grubun var olduğundan sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4745-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="e4745-121">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e4745-121">Members</span></span>| <span data-ttu-id="e4745-122">Belirtilen üyeleriyle geçerli grup üyeliğini değiştirmek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4745-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="e4745-123">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="e4745-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4745-124">Bu özellik bir yapılandırmada ayarlarsanız, ya da kullanmayın **MembersToExclude** veya **MembersToInclude** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4745-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="e4745-125">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4745-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="e4745-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="e4745-126">MembersToExclude</span></span>| <span data-ttu-id="e4745-127">Grup varolan üyeliğinden üyeleri kaldırmak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4745-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="e4745-128">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="e4745-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4745-129">Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4745-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e4745-130">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4745-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="e4745-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="e4745-131">MembersToInclude</span></span>| <span data-ttu-id="e4745-132">Grubun var olan üyeliğini üye eklemek için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4745-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="e4745-133">Biçiminde bir dize dizisi bu özellik değeri *etki alanı*\\*kullanıcıadı*.</span><span class="sxs-lookup"><span data-stu-id="e4745-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e4745-134">Bu özellik bir yapılandırmada ayarlarsanız kullanmayın **üyeleri** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4745-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e4745-135">Bunun yapılması bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4745-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="e4745-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="e4745-136">DependsOn</span></span> | <span data-ttu-id="e4745-137">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4745-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e4745-138">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi ' DependsOn = "[ ResourceType] KaynakAdı"''.</span><span class="sxs-lookup"><span data-stu-id="e4745-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="e4745-139">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="e4745-139">Example 1</span></span>

<span data-ttu-id="e4745-140">Aşağıdaki örnekte, "TestGroup" adlı bir grup mevcut olduğundan emin olmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4745-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="e4745-141">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="e4745-141">Example 2</span></span>
<span data-ttu-id="e4745-142">Aşağıdaki örnek, bir Active Directory kullanıcı zaten bir PSCredential yerel yönetici hesabı için kullandığınız birden çok makine Laboratuvar yapının parçası olarak yerel administrators grubuna eklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4745-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="e4745-143">Bu ayrıca etki alanı yönetici hesabını (etki alanı yükseltme sonrasında) kullanıldıkça biz sonra bu varolan PSCredential bize üye sunucuda yerel Yöneticiler grubunun bir etki alanı kullanıcısı eklemek etkinleştirmek için bir etki alanı kolay kimlik dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4745-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="e4745-144">Örnek 3</span><span class="sxs-lookup"><span data-stu-id="e4745-144">Example 3</span></span>
<span data-ttu-id="e4745-145">Aşağıdaki örnek, yerel bir grup TigerTeamAdmins emin olmak gösterilmektedir, sunucu üzerinde belirli etki alanı hesabı, Contoso\JerryG TigerTeamSource.Contoso.Com içermiyor.</span><span class="sxs-lookup"><span data-stu-id="e4745-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

