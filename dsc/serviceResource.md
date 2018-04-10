---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Hizmet kaynağı
ms.openlocfilehash: 59d7c0c7147bf28b92d64a25c0d67c277e0bb210
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-service-resource"></a><span data-ttu-id="33368-103">DSC Hizmet kaynağı</span><span class="sxs-lookup"><span data-stu-id="33368-103">DSC Service Resource</span></span>

> <span data-ttu-id="33368-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33368-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="33368-105">**Hizmet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), hedef düğümde bulunan hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="33368-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="33368-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33368-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="33368-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="33368-107">Properties</span></span>

|  <span data-ttu-id="33368-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="33368-108">Property</span></span>  |  <span data-ttu-id="33368-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33368-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="33368-110">Ad</span><span class="sxs-lookup"><span data-stu-id="33368-110">Name</span></span>| <span data-ttu-id="33368-111">Hizmet adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-111">Indicates the service name.</span></span> <span data-ttu-id="33368-112">Bazen bu görünen adından farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="33368-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="33368-113">Hizmetler ve bunların geçerli durumu Get-Service cmdlet ile listesini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33368-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="33368-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="33368-114">BuiltInAccount</span></span>| <span data-ttu-id="33368-115">Hizmet için oturum açma hesabı belirtir.</span><span class="sxs-lookup"><span data-stu-id="33368-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="33368-116">Bu özellik için izin verilen değerler: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="33368-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="33368-117">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="33368-117">Credential</span></span>| <span data-ttu-id="33368-118">Hizmet, altında çalışacağı hesabın kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="33368-119">Bu özellik ve __BuiltinAccount__ özelliği birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33368-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="33368-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="33368-120">DependsOn</span></span>| <span data-ttu-id="33368-121">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="33368-122">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="33368-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="33368-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="33368-123">StartupType</span></span>| <span data-ttu-id="33368-124">Hizmet başlangıç türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="33368-125">Bu özellik için izin verilen değerler: **otomatik**, **devre dışı**, ve **el ile**</span><span class="sxs-lookup"><span data-stu-id="33368-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="33368-126">Durum</span><span class="sxs-lookup"><span data-stu-id="33368-126">State</span></span>| <span data-ttu-id="33368-127">Hizmet için sağlamak istediğiniz durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="33368-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33368-128">Description</span></span> | <span data-ttu-id="33368-129">Hedef hizmet açıklaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="33368-130">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="33368-130">DisplayName</span></span> | <span data-ttu-id="33368-131">Hedef hizmet görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33368-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="33368-132">Emin olun</span><span class="sxs-lookup"><span data-stu-id="33368-132">Ensure</span></span> | <span data-ttu-id="33368-133">Hedef hizmet sistemde var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="33368-134">Bu özelliği ayarlamak **etmeksizin** hedef hizmet yok emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="33368-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="33368-135">Ayar **mevcut** hedef hizmetinin var olduğunu (varsayılan değer) sağlar.</span><span class="sxs-lookup"><span data-stu-id="33368-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="33368-136">Yol</span><span class="sxs-lookup"><span data-stu-id="33368-136">Path</span></span> | <span data-ttu-id="33368-137">Yeni bir hizmet için ikili dosya yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="33368-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="33368-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="33368-138">Example</span></span>

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