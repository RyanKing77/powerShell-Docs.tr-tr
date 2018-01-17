---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC Linux nxSshAuthorizedKeys kaynak için"
ms.openlocfilehash: f48ecec39ffe24cee99ca08ad9d050b36c5e04bf
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="dfab9-103">DSC Linux nxSshAuthorizedKeys kaynak için</span><span class="sxs-lookup"><span data-stu-id="dfab9-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="dfab9-104">**NxAuthorizedKeys** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), yönetmek için bir mekanizma ssh yetkili belirli bir kullanıcı için anahtarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfab9-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfab9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfab9-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="dfab9-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dfab9-106">Properties</span></span>

|  <span data-ttu-id="dfab9-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="dfab9-107">Property</span></span> |  <span data-ttu-id="dfab9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfab9-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="dfab9-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="dfab9-109">KeyComment</span></span>| <span data-ttu-id="dfab9-110">Anahtar için benzersiz bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="dfab9-110">A unique comment for the key.</span></span> <span data-ttu-id="dfab9-111">Bu anahtarları benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfab9-111">This is used to uniquely identify keys.</span></span>| 
| <span data-ttu-id="dfab9-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="dfab9-112">Ensure</span></span>| <span data-ttu-id="dfab9-113">Anahtar tanımlı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfab9-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="dfab9-114">Bu özelliği anahtarı kullanıcının yetkili anahtarları dosyasında yok emin olmak için "yok" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dfab9-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="dfab9-115">Anahtar kullanıcının yetkili anahtar dosyasında tanımlanan emin olmak için "var" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dfab9-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>| 
| <span data-ttu-id="dfab9-116">Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="dfab9-116">Username</span></span>| <span data-ttu-id="dfab9-117">SSH yönetmek için kullanıcı adı için anahtarları yetkili.</span><span class="sxs-lookup"><span data-stu-id="dfab9-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="dfab9-118">Tanımlı değil, varsayılan kullanıcı "Kök" olur.</span><span class="sxs-lookup"><span data-stu-id="dfab9-118">If not defined, the default user is "root".</span></span>| 
| <span data-ttu-id="dfab9-119">üzerine gelin</span><span class="sxs-lookup"><span data-stu-id="dfab9-119">Key</span></span>| <span data-ttu-id="dfab9-120">Anahtar içerikleri.</span><span class="sxs-lookup"><span data-stu-id="dfab9-120">The contents of the key.</span></span> <span data-ttu-id="dfab9-121">Bu gereklidir **olun** "Var" ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dfab9-121">This is required if **Ensure** is set to "Present".</span></span>| 
| <span data-ttu-id="dfab9-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="dfab9-122">DependsOn</span></span> | <span data-ttu-id="dfab9-123">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfab9-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dfab9-124">Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="dfab9-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="dfab9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfab9-125">Example</span></span>

<span data-ttu-id="dfab9-126">Aşağıdaki örnek, ssh yetkili ortak tanımlar "monuser" kullanıcı için anahtar.</span><span class="sxs-lookup"><span data-stu-id="dfab9-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```

