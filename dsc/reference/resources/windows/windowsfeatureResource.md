---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsFeature kaynağı
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048708"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="12957-103">DSC WindowsFeature kaynağı</span><span class="sxs-lookup"><span data-stu-id="12957-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="12957-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="12957-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="12957-105">**WindowsFeature** kaynak olarak Windows PowerShell Desired State Configuration (DSC), roller ve Özellikler eklenen veya kaldırılan bir hedef düğümde emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="12957-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="12957-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12957-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="12957-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="12957-107">Properties</span></span>

|  <span data-ttu-id="12957-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="12957-108">Property</span></span>  |  <span data-ttu-id="12957-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12957-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="12957-110">Ad</span><span class="sxs-lookup"><span data-stu-id="12957-110">Name</span></span>| <span data-ttu-id="12957-111">Sağlamak istediğiniz rol veya özellik adını eklendiğinde veya kaldırıldığında gösterir.</span><span class="sxs-lookup"><span data-stu-id="12957-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="12957-112">Bu, aynı __adı__ özelliğinden [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet'ini ve rol veya özellik görünen adı değil.</span><span class="sxs-lookup"><span data-stu-id="12957-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="12957-113">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="12957-113">Credential</span></span>| <span data-ttu-id="12957-114">Rol veya özellik eklemek veya kaldırmak için kullanılacak kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12957-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="12957-115">Emin olun</span><span class="sxs-lookup"><span data-stu-id="12957-115">Ensure</span></span>| <span data-ttu-id="12957-116">Rol veya özelliğin eklenip eklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="12957-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="12957-117">Rol veya özellik olduğundan emin olmak için ek olarak ayarlayın "Var" rol veya özellik kaldırıldığını, emin olmak için bu özelliği ayarlayın "Yok" özelliği.</span><span class="sxs-lookup"><span data-stu-id="12957-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="12957-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="12957-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="12957-119">Bu özellik kümesine __$true__ belirttiğiniz ile gerekli tüm alt özellik durumuyla durumunu emin olmak için __adı__ özelliği.</span><span class="sxs-lookup"><span data-stu-id="12957-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="12957-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="12957-120">LogPath</span></span>| <span data-ttu-id="12957-121">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="12957-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="12957-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="12957-122">DependsOn</span></span>| <span data-ttu-id="12957-123">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12957-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="12957-124">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="12957-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="12957-125">Kaynak</span><span class="sxs-lookup"><span data-stu-id="12957-125">Source</span></span>| <span data-ttu-id="12957-126">Gerekirse yüklenmesi için kullanılacak kaynak dosyasının konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="12957-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="12957-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="12957-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```