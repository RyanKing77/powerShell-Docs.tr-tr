---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Hizmet kaynağı
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688304"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="ea984-103">DSC Hizmet kaynağı</span><span class="sxs-lookup"><span data-stu-id="ea984-103">DSC Service Resource</span></span>

> <span data-ttu-id="ea984-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ea984-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="ea984-105">**Hizmet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), hedef düğümdeki hizmetleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea984-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea984-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea984-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ea984-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ea984-107">Properties</span></span>

|  <span data-ttu-id="ea984-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="ea984-108">Property</span></span>  |  <span data-ttu-id="ea984-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea984-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="ea984-110">Adı</span><span class="sxs-lookup"><span data-stu-id="ea984-110">Name</span></span>| <span data-ttu-id="ea984-111">Hizmet adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea984-111">Indicates the service name.</span></span> <span data-ttu-id="ea984-112">Bazen bu görünen addan farklı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ea984-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="ea984-113">Hizmetler ve Get-Service cmdlet'i ile bunların geçerli durumunu listesini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea984-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="ea984-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="ea984-114">BuiltInAccount</span></span>| <span data-ttu-id="ea984-115">Hizmet için kullanılacak oturum açma hesabı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="ea984-116">Bu özellik için izin verilen değerler şunlardır: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="ea984-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="ea984-117">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="ea984-117">Credential</span></span>| <span data-ttu-id="ea984-118">Hizmet, altında çalışacağı hesabın kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea984-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="ea984-119">Bu özellik ve __BuiltinAccount__ özelliği birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ea984-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="ea984-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ea984-120">DependsOn</span></span>| <span data-ttu-id="ea984-121">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ea984-122">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ea984-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ea984-123">Başlangıç türü</span><span class="sxs-lookup"><span data-stu-id="ea984-123">StartupType</span></span>| <span data-ttu-id="ea984-124">Hizmet başlangıç türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="ea984-125">Bu özellik için izin verilen değerler şunlardır: **Otomatik**, **devre dışı bırakılmış**, ve **el ile**</span><span class="sxs-lookup"><span data-stu-id="ea984-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="ea984-126">Durum</span><span class="sxs-lookup"><span data-stu-id="ea984-126">State</span></span>| <span data-ttu-id="ea984-127">Hizmet için sağlamak istediğiniz durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="ea984-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea984-128">Description</span></span> | <span data-ttu-id="ea984-129">Hedef hizmet açıklamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="ea984-130">Görünen Ad</span><span class="sxs-lookup"><span data-stu-id="ea984-130">DisplayName</span></span> | <span data-ttu-id="ea984-131">Hedef hizmet görünen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea984-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="ea984-132">Emin olun</span><span class="sxs-lookup"><span data-stu-id="ea984-132">Ensure</span></span> | <span data-ttu-id="ea984-133">Hedef hizmet sistemde var olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="ea984-134">Bu özellik kümesine **devamsızlık** hedef hizmet yok emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="ea984-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="ea984-135">Bu ayarın **mevcut** hedef hizmetinin var olduğunu (varsayılan değer) sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea984-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="ea984-136">Yol</span><span class="sxs-lookup"><span data-stu-id="ea984-136">Path</span></span> | <span data-ttu-id="ea984-137">Yeni bir hizmet için ikili dosya yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea984-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="ea984-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea984-138">Example</span></span>

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