---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Hizmet kaynağı"
ms.openlocfilehash: a549530edc19496a68c036fecbd18b0072cc6d74
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-service-resource"></a><span data-ttu-id="a101e-103">DSC Hizmet kaynağı</span><span class="sxs-lookup"><span data-stu-id="a101e-103">DSC Service Resource</span></span>

> <span data-ttu-id="a101e-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a101e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="a101e-105">**Hizmet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a101e-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a101e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a101e-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="a101e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a101e-107">Properties</span></span>

|  <span data-ttu-id="a101e-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="a101e-108">Property</span></span>  |  <span data-ttu-id="a101e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a101e-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a101e-110">Ad</span><span class="sxs-lookup"><span data-stu-id="a101e-110">Name</span></span>| <span data-ttu-id="a101e-111">Hizmet adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-111">Indicates the service name.</span></span> <span data-ttu-id="a101e-112">Bazen bu görünen adından farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a101e-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="a101e-113">Hizmetler ve bunların geçerli durumu Get-Service cmdlet ile listesini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a101e-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>| 
| <span data-ttu-id="a101e-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="a101e-114">BuiltInAccount</span></span>| <span data-ttu-id="a101e-115">Hizmet için oturum açma hesabı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a101e-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="a101e-116">Bu özellik için izin verilen değerler: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="a101e-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="a101e-117">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="a101e-117">Credential</span></span>| <span data-ttu-id="a101e-118">Hizmet, altında çalışacağı hesabın kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="a101e-119">Bu özellik ve __BuiltinAccount__ özelliği birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a101e-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>| 
| <span data-ttu-id="a101e-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a101e-120">DependsOn</span></span>| <span data-ttu-id="a101e-121">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a101e-122">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a101e-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="a101e-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="a101e-123">StartupType</span></span>| <span data-ttu-id="a101e-124">Hizmet başlangıç türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="a101e-125">Bu özellik için izin verilen değerler: **otomatik**, **devre dışı**, ve **el ile**</span><span class="sxs-lookup"><span data-stu-id="a101e-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>| 
| <span data-ttu-id="a101e-126">Durum</span><span class="sxs-lookup"><span data-stu-id="a101e-126">State</span></span>| <span data-ttu-id="a101e-127">Hizmet için sağlamak istediğiniz durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-127">Indicates the state you want to ensure for the service.</span></span>| 
| <span data-ttu-id="a101e-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a101e-128">Description</span></span> | <span data-ttu-id="a101e-129">Hedef hizmet açıklaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-129">Indicates the description of the target service.</span></span>| 
| <span data-ttu-id="a101e-130">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="a101e-130">DisplayName</span></span> | <span data-ttu-id="a101e-131">Hedef hizmet görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a101e-131">Indicates the display name of the target service.</span></span>| 
| <span data-ttu-id="a101e-132">Emin olun</span><span class="sxs-lookup"><span data-stu-id="a101e-132">Ensure</span></span> | <span data-ttu-id="a101e-133">Hedef hizmet sistemde var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="a101e-134">Bu özelliği ayarlamak **etmeksizin** hedef hizmet yok emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="a101e-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="a101e-135">Ayar **mevcut** hedef hizmetinin var olduğunu (varsayılan değer) sağlar.</span><span class="sxs-lookup"><span data-stu-id="a101e-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="a101e-136">Yol</span><span class="sxs-lookup"><span data-stu-id="a101e-136">Path</span></span> | <span data-ttu-id="a101e-137">Yeni bir hizmet için ikili dosya yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a101e-137">Indicates the path to the binary file for a new service.</span></span>| 

## <a name="example"></a><span data-ttu-id="a101e-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="a101e-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

