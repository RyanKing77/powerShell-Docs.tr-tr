---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Registry kaynağı
ms.openlocfilehash: b77710d7a6fc599949e78c17af309ad88a1a0872
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093594"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="99247-103">DSC Registry kaynağı</span><span class="sxs-lookup"><span data-stu-id="99247-103">DSC Registry Resource</span></span>

> <span data-ttu-id="99247-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="99247-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="99247-105">**Kayıt defteri** kaynak olarak Windows PowerShell Desired State Configuration (DSC), kayıt defteri anahtarlarını ve değerlerini bir hedef düğümde yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="99247-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="99247-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99247-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="99247-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="99247-107">Properties</span></span>

|  <span data-ttu-id="99247-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="99247-108">Property</span></span>  |  <span data-ttu-id="99247-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99247-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="99247-110">üzerine gelin</span><span class="sxs-lookup"><span data-stu-id="99247-110">Key</span></span>| <span data-ttu-id="99247-111">Belirli bir durumu sağlamak istediğiniz kayıt defteri anahtarının yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="99247-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="99247-112">Bu yol, hive içermelidir.</span><span class="sxs-lookup"><span data-stu-id="99247-112">This path must include the hive.</span></span>|
| <span data-ttu-id="99247-113">değer adı</span><span class="sxs-lookup"><span data-stu-id="99247-113">ValueName</span></span>| <span data-ttu-id="99247-114">Kayıt defteri değerinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99247-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="99247-115">Bir kayıt defteri anahtarı ekleyip için ValueType veya ValueData belirtmeden bu özellik boş bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="99247-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="99247-116">Bir kayıt defteri anahtarının varsayılan değeri kaldırın ya da değiştirmek için ValueType veya ValueData belirtirken de bu özellik boş bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="99247-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="99247-117">Emin olun</span><span class="sxs-lookup"><span data-stu-id="99247-117">Ensure</span></span>| <span data-ttu-id="99247-118">Anahtar ve değer olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99247-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="99247-119">"Var" Bu özelliği ayarlamak emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="99247-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="99247-120">Nesneler yok emin olmak için "Yok" özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99247-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="99247-121">"Var" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="99247-121">The default value is "Present".</span></span>|
| <span data-ttu-id="99247-122">Force</span><span class="sxs-lookup"><span data-stu-id="99247-122">Force</span></span>| <span data-ttu-id="99247-123">Belirtilen kayıt defteri anahtarı varsa **zorla** yeni değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="99247-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="99247-124">Alt anahtarlar içeren bir kayıt defteri anahtarının silinmesi, bu olması gereken **$true**</span><span class="sxs-lookup"><span data-stu-id="99247-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="99247-125">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="99247-125">Hex</span></span>| <span data-ttu-id="99247-126">Onaltılık biçimde belirtilecektir verileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="99247-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="99247-127">Belirtilmişse DWORD/QWORD değer verisini onaltılık biçimde sunulur.</span><span class="sxs-lookup"><span data-stu-id="99247-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="99247-128">Diğer türleri için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="99247-128">Not valid for other types.</span></span> <span data-ttu-id="99247-129">Varsayılan değer **$false**.</span><span class="sxs-lookup"><span data-stu-id="99247-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="99247-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99247-130">DependsOn</span></span>| <span data-ttu-id="99247-131">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="99247-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="99247-132">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="99247-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="99247-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="99247-133">ValueData</span></span>| <span data-ttu-id="99247-134">Kayıt defteri değeri için veriler.</span><span class="sxs-lookup"><span data-stu-id="99247-134">The data for the registry value.</span></span>|
| <span data-ttu-id="99247-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="99247-135">ValueType</span></span>| <span data-ttu-id="99247-136">Değer türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="99247-136">Indicates the type of the value.</span></span> <span data-ttu-id="99247-137">Desteklenen türler: dize (REG_SZ), ikili dosya (ikili REG), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), çok dizeli (REG_MULTI_SZ), Genişletilebilir dize (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="99247-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="99247-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="99247-138">Example</span></span>

<span data-ttu-id="99247-139">Bu örnekte "ExampleKey" adlı bir anahtar mevcut olmasını sağlar **HKEY\_yerel\_makine** hive.</span><span class="sxs-lookup"><span data-stu-id="99247-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="99247-140">Bir kayıt defteri ayarı değiştirerek **HKEY\_geçerli\_kullanıcı** hive gerektirir yapılandırma sistemi olarak değil, kullanıcı kimlik bilgileriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="99247-140">Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="99247-141">Kullanabileceğiniz **PsDscRunAsCredential** özelliği yapılandırması için kullanıcı kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="99247-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="99247-142">Bir örnek için bkz. [DSC çalıştıran kullanıcı kimlik bilgileriyle](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="99247-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>