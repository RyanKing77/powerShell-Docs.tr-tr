---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsFeature kaynağı"
ms.openlocfilehash: a3433577a122f6c7e31360e094a089f6ceef77c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="38b2a-103">DSC WindowsFeature kaynağı</span><span class="sxs-lookup"><span data-stu-id="38b2a-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="38b2a-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="38b2a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="38b2a-105">**WindowsFeature** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), roller ve özellikler eklenemez veya kaldırılamaz hedef düğümde emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="38b2a-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="38b2a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38b2a-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="38b2a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="38b2a-107">Properties</span></span>

|  <span data-ttu-id="38b2a-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="38b2a-108">Property</span></span>  |  <span data-ttu-id="38b2a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38b2a-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="38b2a-110">Ad</span><span class="sxs-lookup"><span data-stu-id="38b2a-110">Name</span></span>| <span data-ttu-id="38b2a-111">Sağlamak istediğiniz rol veya özellik adını eklenen veya kaldırılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="38b2a-112">Bu aynı sonucu verir __adı__ özelliğinden [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet'ini ve rol veya özellik görünen adı değil.</span><span class="sxs-lookup"><span data-stu-id="38b2a-112">This is the same as the __Name__ property from the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="38b2a-113">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="38b2a-113">Credential</span></span>| <span data-ttu-id="38b2a-114">Rol veya özellik eklemek veya kaldırmak için kullanılacak kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="38b2a-115">Emin olun</span><span class="sxs-lookup"><span data-stu-id="38b2a-115">Ensure</span></span>| <span data-ttu-id="38b2a-116">Rol veya özellik eklediyseniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="38b2a-117">Rol veya özellik olduğundan emin olmak için eklenen, ayarlanmış bu özelliğe rol veya özellik kaldırıldığını, emin olmak için "var" olarak ayarlayın "Yok" özelliği.</span><span class="sxs-lookup"><span data-stu-id="38b2a-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="38b2a-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="38b2a-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="38b2a-119">Bu özelliği ayarlamak __$true__ belirttiğiniz ile gerekli tüm alt özellikleri özellik durumuyla durumunu emin olmak için __adı__ özelliği.</span><span class="sxs-lookup"><span data-stu-id="38b2a-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="38b2a-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="38b2a-120">LogPath</span></span>| <span data-ttu-id="38b2a-121">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="38b2a-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="38b2a-122">DependsOn</span></span>| <span data-ttu-id="38b2a-123">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="38b2a-124">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="38b2a-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="38b2a-125">Kaynak</span><span class="sxs-lookup"><span data-stu-id="38b2a-125">Source</span></span>| <span data-ttu-id="38b2a-126">Gerekiyorsa, yükleme için kullanılacak kaynak dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38b2a-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="38b2a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="38b2a-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

