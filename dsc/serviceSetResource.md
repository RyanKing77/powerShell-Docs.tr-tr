---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC ServiceSet kaynağı"
ms.openlocfilehash: 92fa4a442eb42e89195162b7831f1a96d40b84f5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="0f44a-103">DSC ServiceSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="0f44a-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="0f44a-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0f44a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="0f44a-105">**ServiceSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f44a-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="0f44a-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [hizmet kaynak](serviceResource.md) belirtilen her hizmet için `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f44a-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="0f44a-107">Bu kaynak Hizmetleri aynı duruma sayısını yapılandırmak istediğinizde kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f44a-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f44a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f44a-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="0f44a-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0f44a-109">Properties</span></span>

|  <span data-ttu-id="0f44a-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="0f44a-110">Property</span></span>  |  <span data-ttu-id="0f44a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f44a-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0f44a-112">Ad</span><span class="sxs-lookup"><span data-stu-id="0f44a-112">Name</span></span>| <span data-ttu-id="0f44a-113">Hizmet adlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-113">Indicates the service names.</span></span> <span data-ttu-id="0f44a-114">Bazen bu görünen adları farklı olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0f44a-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="0f44a-115">Hizmetleri ve bunların geçerli durumu ile bir liste alabilir [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="0f44a-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="0f44a-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="0f44a-116">StartupType</span></span>| <span data-ttu-id="0f44a-117">Hizmet başlangıç türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="0f44a-118">Bu özellik için izin verilen değerler: **otomatik**, **devre dışı**, ve **el ile**</span><span class="sxs-lookup"><span data-stu-id="0f44a-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="0f44a-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0f44a-119">BuiltInAccount</span></span>| <span data-ttu-id="0f44a-120">Hizmetler için kullanılacak oturum açma hesabını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="0f44a-121">Bu özellik için izin verilen değerler: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="0f44a-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="0f44a-122">Durum</span><span class="sxs-lookup"><span data-stu-id="0f44a-122">State</span></span>| <span data-ttu-id="0f44a-123">Hizmetler için sağlamak istediğiniz durumunu gösterir: **durduruldu** veya **çalıştıran**.</span><span class="sxs-lookup"><span data-stu-id="0f44a-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="0f44a-124">Emin olun</span><span class="sxs-lookup"><span data-stu-id="0f44a-124">Ensure</span></span>| <span data-ttu-id="0f44a-125">Hizmetleri sistemde var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="0f44a-126">Bu özelliği ayarlamak **etmeksizin** Hizmetleri mevcut emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="0f44a-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="0f44a-127">Ayar **mevcut** hedef Hizmetleri mevcut olduğunu (varsayılan değer) sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f44a-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="0f44a-128">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="0f44a-128">Credential</span></span>| <span data-ttu-id="0f44a-129">Hizmet kaynağı altında çalışacağı hesabın kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="0f44a-130">Bu özellik ve **BuiltinAccount** özelliği birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f44a-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="0f44a-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0f44a-131">DependsOn</span></span>| <span data-ttu-id="0f44a-132">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f44a-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0f44a-133">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise *ResourceName* ve türünü *ResourceType*, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0f44a-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="0f44a-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f44a-134">Example</span></span>

<span data-ttu-id="0f44a-135">Aşağıdaki yapılandırma "Windows Ses" ve "Uzak Masaüstü Hizmetleri" hizmetlerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="0f44a-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

