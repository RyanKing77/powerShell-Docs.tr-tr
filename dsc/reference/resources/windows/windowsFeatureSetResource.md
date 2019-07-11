---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsFeatureSet kaynağı
ms.openlocfilehash: 8a64168d9ad0d6a6c40eb0398cc734fa93a247dc
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726781"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="d632c-103">DSC WindowsFeatureSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="d632c-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="d632c-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d632c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d632c-105">**WindowsFeatureSet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), roller ve Özellikler eklenen veya kaldırılan bir hedef düğümde emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d632c-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="d632c-106">Bu kaynak bir [bileşik kaynak](../../../resources/authoringResourceComposite.md) çağrılarının [WindowsFeature kaynağı](windowsfeatureResource.md) belirtilen her bir özellik `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="d632c-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="d632c-107">Bu kaynak, çok sayıda Windows özelliği aynı duruma yapılandırmak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="d632c-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="d632c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d632c-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d632c-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d632c-109">Properties</span></span>

|  <span data-ttu-id="d632c-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="d632c-110">Property</span></span>  |  <span data-ttu-id="d632c-111">Description</span><span class="sxs-lookup"><span data-stu-id="d632c-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="d632c-112">Adı</span><span class="sxs-lookup"><span data-stu-id="d632c-112">Name</span></span>| <span data-ttu-id="d632c-113">Rolleri veya özellikleri sağlamak istediğiniz adlarını eklendiğinde veya kaldırıldığında.</span><span class="sxs-lookup"><span data-stu-id="d632c-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="d632c-114">Bu, aynı **adı** özelliği [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet'ini ve rollerin veya özelliklerin görünen adı değil.</span><span class="sxs-lookup"><span data-stu-id="d632c-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="d632c-115">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="d632c-115">Credential</span></span>| <span data-ttu-id="d632c-116">Rolleri veya özellikleri eklemek veya kaldırmak için kullanılacak kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="d632c-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="d632c-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="d632c-117">Ensure</span></span>| <span data-ttu-id="d632c-118">Roller veya özellikler eklenip eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d632c-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="d632c-119">Rolleri veya özellikleri olmasını sağlamak için ek olarak ayarlayın "Var" rollerin veya özelliklerin kaldırıldığını, emin olmak için bu özelliği ayarlayın özelliğini "Yok".</span><span class="sxs-lookup"><span data-stu-id="d632c-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="d632c-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="d632c-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="d632c-121">Bu özellik kümesine **$true** ile belirttiğiniz özellikleri ile gerekli tüm alt özellikleri içerecek şekilde **adı** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d632c-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="d632c-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="d632c-122">LogPath</span></span>| <span data-ttu-id="d632c-123">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="d632c-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="d632c-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="d632c-124">DependsOn</span></span>| <span data-ttu-id="d632c-125">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d632c-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d632c-126">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d632c-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d632c-127">Source</span><span class="sxs-lookup"><span data-stu-id="d632c-127">Source</span></span>| <span data-ttu-id="d632c-128">Gerekirse yüklenmesi için kullanılacak kaynak dosyasının konumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d632c-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="d632c-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d632c-129">Example</span></span>

<span data-ttu-id="d632c-130">Aşağıdaki yapılandırma, sağlar **Web-Server** (IIS) ve **SMTP sunucusu** özellikleri ve her, tüm alt özellikleri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d632c-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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
