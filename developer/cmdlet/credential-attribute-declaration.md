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
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851992"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="21aa6-102">Kimlik Bilgisi Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="21aa6-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="21aa6-103">Kimlik bilgisi türü parametrelerle kullanılabilecek isteğe bağlı bir öznitelik kimlik bilgisi özniteliktir [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir.</span><span class="sxs-lookup"><span data-stu-id="21aa6-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="21aa6-104">Bu öznitelik için bir parametre bildirimi eklendiğinde, Windows PowerShell bir dize girişi dönüştürür bir [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) nesne.</span><span class="sxs-lookup"><span data-stu-id="21aa6-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="21aa6-105">Örneğin, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet, Windows PowerShell oluşturmak için bu öznitelik kullanır [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet'i tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="21aa6-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>
<span data-ttu-id="21aa6-106">Kimlik bilgisi türü parametrelerle kullanılabilecek isteğe bağlı bir öznitelik kimlik bilgisi özniteliktir [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir.</span><span class="sxs-lookup"><span data-stu-id="21aa6-106">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="21aa6-107">Bu öznitelik için bir parametre bildirimi eklendiğinde, Windows PowerShell bir dize girişi dönüştürür bir [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) nesne.</span><span class="sxs-lookup"><span data-stu-id="21aa6-107">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="21aa6-108">Örneğin, [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet, Windows PowerShell oluşturmak için bu öznitelik kullanır [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) cmdlet'i tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="21aa6-108">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="21aa6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21aa6-109">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="21aa6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21aa6-110">Remarks</span></span>

- <span data-ttu-id="21aa6-111">Bu öznitelik türünde bir parametre tarafından genellikle kullanılan [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) böylece bir dize da bağımsız değişken olarak parametresine geçilebilir.</span><span class="sxs-lookup"><span data-stu-id="21aa6-111">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="21aa6-112">Olduğunda bir [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) nesne parametresi için geçirilen, Windows PowerShell hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="21aa6-112">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="21aa6-113">Oluştururken [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) nesnesi, Windows PowerShell, kullanıcıya uygun yönergeleri görüntülemek için geçerli ana bilgisayar kullanır.</span><span class="sxs-lookup"><span data-stu-id="21aa6-113">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="21aa6-114">Örneğin, bu öznitelik kullanıldığında varsayılan ana bilgisayar için bir kullanıcı adı ve parola istemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="21aa6-114">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="21aa6-115">Ancak, özel bir ana bilgisayar kullanılıyorsa farklı bir komut istemi tanımlayan sonra Bu istem görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21aa6-115">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="21aa6-116">Bu öznitelik ile parametre özniteliği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21aa6-116">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="21aa6-117">Bu özniteliği hakkında daha fazla bilgi için bkz. [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="21aa6-117">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="21aa6-118">Kimlik bilgisi özniteliği tarafından tanımlanan [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21aa6-118">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="21aa6-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="21aa6-119">See Also</span></span>

[<span data-ttu-id="21aa6-120">Parametre diğer adları</span><span class="sxs-lookup"><span data-stu-id="21aa6-120">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="21aa6-121">Parametre özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="21aa6-121">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="21aa6-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="21aa6-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
