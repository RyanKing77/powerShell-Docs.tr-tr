---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Web erişim cmdlet'leri
ms.technology: powershell
ms.openlocfilehash: 6930fd6a08de69078576fb0d0fbabb04e05d0814
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="d9c62-103">Windows PowerShell Web Erişim Cmdlet’leri</span><span class="sxs-lookup"><span data-stu-id="d9c62-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="d9c62-104">Bu başvuru cmdlet açıklamaları ve sözdizimi için tüm Windows PowerShell® Web Access özgü cmdlet'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9c62-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="d9c62-105">Cmdlet başındaki fiil göre alfabetik sırada cmdlet'leri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9c62-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="d9c62-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d9c62-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="d9c62-107">Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.</span><span class="sxs-lookup"><span data-stu-id="d9c62-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="d9c62-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d9c62-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="d9c62-109">Windows PowerShell Web Erişimi yetkilendirme kuralları kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9c62-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="d9c62-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d9c62-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="d9c62-111">Windows PowerShell Web erişimi web uygulaması IIS'de yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d9c62-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="d9c62-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d9c62-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="d9c62-113">Windows PowerShell Web Erişimi'nden belirtilen bir yetkilendirme kuralını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9c62-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="d9c62-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="d9c62-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="d9c62-115">Belirli bir kullanıcının doğrulamak için yetkilendirme kuralları testleri bilgisayar, uç nokta erişim isteği yetkili olduğu.</span><span class="sxs-lookup"><span data-stu-id="d9c62-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="d9c62-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="d9c62-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="d9c62-117">Windows PowerShell web uygulamasını IIS'den kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d9c62-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="d9c62-118">**Not**:</span><span class="sxs-lookup"><span data-stu-id="d9c62-118">**Note**:</span></span>
>
><span data-ttu-id="d9c62-119">Kullanılabilir tüm cmdlet'leri listelemek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="d9c62-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="d9c62-120">`Get-Command –Module PowerShellWebAccess` cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9c62-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="d9c62-121">Hakkında daha fazla bilgi için ya da sözdizimini, cmdlet'lerinden herhangi birini kullanın: `Get-Help ` *&lt;cmdlet adı&gt;* nerede *&lt;cmdlet adı&gt;* araştırmak istediğiniz cmdlet'in adıdır.</span><span class="sxs-lookup"><span data-stu-id="d9c62-121">For more information about, or for the syntax of, any of the cmdlets, use: `Get-Help `*&lt;cmdlet name&gt;* where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="d9c62-122">Daha ayrıntılı bilgi için, aşağıdaki cmdlet'lerin herhangi birini çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d9c62-122">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="d9c62-123">`Get-Help `*&lt;Cmdlet adı&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="d9c62-123">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="d9c62-124">`Get-Help `*&lt;Cmdlet adı&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="d9c62-124">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="d9c62-125">`Get-Help `*&lt;Cmdlet adı&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="d9c62-125">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="d9c62-126">Daha Fazla Bilgi</span><span class="sxs-lookup"><span data-stu-id="d9c62-126">More Information</span></span>

<span data-ttu-id="d9c62-127">PowerShell Web erişimi hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="d9c62-127">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="d9c62-128">Yükleme ve Windows PowerShell Web erişimini kullanma</span><span class="sxs-lookup"><span data-stu-id="d9c62-128">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)