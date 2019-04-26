---
title: Kimlik bilgisi öznitelik bildiriminin | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068327"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="0e0f7-102">Kimlik Bilgisi Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="0e0f7-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="0e0f7-103">Kimlik bilgisi türü parametrelerle kullanılabilecek isteğe bağlı bir öznitelik kimlik bilgisi özniteliktir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="0e0f7-104">Bu öznitelik için bir parametre bildirimi eklendiğinde, Windows PowerShell bir dize girişi dönüştürür bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="0e0f7-105">Örneğin, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet, Windows PowerShell oluşturmak için bu öznitelik kullanır [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet'i tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e0f7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e0f7-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="0e0f7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e0f7-107">Remarks</span></span>

- <span data-ttu-id="0e0f7-108">Bu öznitelik türünde bir parametre tarafından genellikle kullanılan [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="0e0f7-109">Olduğunda bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne parametresi için geçirilen, Windows PowerShell hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="0e0f7-110">Oluştururken [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesnesi, Windows PowerShell, kullanıcıya uygun yönergeleri görüntülemek için geçerli ana bilgisayar kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="0e0f7-111">Örneğin, bu öznitelik kullanıldığında varsayılan ana bilgisayar için bir kullanıcı adı ve parola istemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="0e0f7-112">Ancak, özel bir ana bilgisayar kullanılıyorsa farklı bir komut istemi tanımlayan sonra Bu istem görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="0e0f7-113">Bu öznitelik ile parametre özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="0e0f7-114">Bu özniteliği hakkında daha fazla bilgi için bkz. [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0e0f7-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="0e0f7-115">Kimlik bilgisi özniteliği tarafından tanımlanan [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e0f7-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e0f7-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="0e0f7-116">See Also</span></span>

[<span data-ttu-id="0e0f7-117">Parametre diğer adları</span><span class="sxs-lookup"><span data-stu-id="0e0f7-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="0e0f7-118">Parametre özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="0e0f7-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="0e0f7-119">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="0e0f7-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
