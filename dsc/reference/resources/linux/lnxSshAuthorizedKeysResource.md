---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxSshAuthorizedKeys kaynağı
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687807"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="95483-103">DSC için Linux nxSshAuthorizedKeys kaynağı</span><span class="sxs-lookup"><span data-stu-id="95483-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="95483-104">**NxAuthorizedKeys** kaynak içinde PowerShell Desired State Configuration (DSC), yönetmek için bir mekanizma ssh yetkili belirli bir kullanıcı için anahtarlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="95483-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="95483-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95483-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="95483-106">Özellikler</span><span class="sxs-lookup"><span data-stu-id="95483-106">Properties</span></span>

|  <span data-ttu-id="95483-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="95483-107">Property</span></span> |  <span data-ttu-id="95483-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95483-108">Description</span></span> |
|---|---|
| <span data-ttu-id="95483-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="95483-109">KeyComment</span></span>| <span data-ttu-id="95483-110">Anahtar için benzersiz bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="95483-110">A unique comment for the key.</span></span> <span data-ttu-id="95483-111">Bu, anahtarlar benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95483-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="95483-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="95483-112">Ensure</span></span>| <span data-ttu-id="95483-113">Anahtar tanımlı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="95483-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="95483-114">"Yok" anahtar kullanıcının yetkili anahtarlar dosyasına yok sağlamak için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95483-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="95483-115">Anahtar kullanıcının yetkili anahtar dosyasında tanımlanan emin olmak için "var" ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="95483-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="95483-116">Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="95483-116">Username</span></span>| <span data-ttu-id="95483-117">Anahtarlar için SSH yönetmek için kullanıcı adı yetkili.</span><span class="sxs-lookup"><span data-stu-id="95483-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="95483-118">Tanımlı değilse, varsayılan "Kök" kullanıcıdır.</span><span class="sxs-lookup"><span data-stu-id="95483-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="95483-119">üzerine gelin</span><span class="sxs-lookup"><span data-stu-id="95483-119">Key</span></span>| <span data-ttu-id="95483-120">Anahtar içeriğini.</span><span class="sxs-lookup"><span data-stu-id="95483-120">The contents of the key.</span></span> <span data-ttu-id="95483-121">Bu gereklidir **olun** "Var" için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="95483-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="95483-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="95483-122">DependsOn</span></span> | <span data-ttu-id="95483-123">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="95483-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="95483-124">Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="95483-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="95483-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="95483-125">Example</span></span>

<span data-ttu-id="95483-126">Aşağıdaki örnek, bir ortak ssh yetkili tanımlar "monuser" kullanıcı anahtarı.</span><span class="sxs-lookup"><span data-stu-id="95483-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

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