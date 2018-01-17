---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsFeatureSet kaynağı"
ms.openlocfilehash: a2bb008852ccfdc04998a57d3e64e08bf05e6433
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="33d74-103">DSC WindowsFeatureSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="33d74-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="33d74-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33d74-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="33d74-105">**WindowsFeatureSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), roller ve özellikler eklenemez veya kaldırılamaz hedef düğümde emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d74-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="33d74-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsFeature kaynak](windowsfeatureResource.md) belirtilen her bir özelliğin `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="33d74-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="33d74-107">Çok sayıda Windows özelliği aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="33d74-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="33d74-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33d74-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="33d74-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="33d74-109">Properties</span></span>

|  <span data-ttu-id="33d74-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="33d74-110">Property</span></span>  |  <span data-ttu-id="33d74-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d74-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="33d74-112">Ad</span><span class="sxs-lookup"><span data-stu-id="33d74-112">Name</span></span>| <span data-ttu-id="33d74-113">Rolleri veya sağlamak istediğiniz özellikleri adlarını eklenir veya kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="33d74-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="33d74-114">Bu aynı sonucu verir **adı** özelliği [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet'ini ve rollerin veya özelliklerin görünen adı değil.</span><span class="sxs-lookup"><span data-stu-id="33d74-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>| 
| <span data-ttu-id="33d74-115">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="33d74-115">Credential</span></span>| <span data-ttu-id="33d74-116">Rolleri veya özellikleri eklemek veya kaldırmak için kullanılacak kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="33d74-116">The credentials to use to add or remove the roles or features.</span></span>| 
| <span data-ttu-id="33d74-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="33d74-117">Ensure</span></span>| <span data-ttu-id="33d74-118">Roller veya özellikler eklenip eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="33d74-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="33d74-119">Roller veya özellikler olduğundan emin olmak için eklenen, ayarlanmış roller veya özellikler kaldırıldığından, emin olmak için "var" Bu özelliği ayarlayın "Yok" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="33d74-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="33d74-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="33d74-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="33d74-121">Bu özelliği ayarlamak **$true** ile gerekli tüm alt özellikleri ile belirttiğiniz özellikleri içerecek şekilde **adı** özelliği.</span><span class="sxs-lookup"><span data-stu-id="33d74-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>| 
| <span data-ttu-id="33d74-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="33d74-122">LogPath</span></span>| <span data-ttu-id="33d74-123">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="33d74-123">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="33d74-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="33d74-124">DependsOn</span></span>| <span data-ttu-id="33d74-125">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="33d74-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="33d74-126">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="33d74-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="33d74-127">Kaynak</span><span class="sxs-lookup"><span data-stu-id="33d74-127">Source</span></span>| <span data-ttu-id="33d74-128">Gerekiyorsa, yükleme için kullanılacak kaynak dosyasının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="33d74-128">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="33d74-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="33d74-129">Example</span></span>

<span data-ttu-id="33d74-130">Aşağıdaki yapılandırma sağlar **Web sunucusu** (IIS) ve **SMTP sunucusu** özellikleri ve her, tüm alt özellikleri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="33d74-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```

