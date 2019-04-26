---
title: Cmdlet'i sınıf bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068649"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="97317-102">Cmdlet Sınıf Bildirimi</span><span class="sxs-lookup"><span data-stu-id="97317-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="97317-103">Microsoft .NET Framework sınıf belirterek bir cmdlet bildirilen **cmdlet'i** öznitelik olarak meta veri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97317-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="97317-104">( **Cmdlet'i** tüm cmdlet'ler için tek gereken özniteliği bir özniteliktir).</span><span class="sxs-lookup"><span data-stu-id="97317-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="97317-105">Belirttiğinizde **cmdlet'i** özniteliği, kullanıcı cmdlet'e tanımlayan fiil-isim çift belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="97317-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="97317-106">Ayrıca, cmdlet destekleyen Windows PowerShell işlevler açıklamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="97317-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="97317-107">Belirtmek için kullanılan bildirim sözdizimi hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="97317-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="97317-108">**Cmdlet'i** özniteliği tarafından tanımlanan [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="97317-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="97317-109">Bu sınıf özelliklerini öznitelik bildirdiğinizde, kullanılan bildirim parametrelere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="97317-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="97317-110">Adlar</span><span class="sxs-lookup"><span data-stu-id="97317-110">Nouns</span></span>

<span data-ttu-id="97317-111">Cmdlet isim cmdlet yapan kaynakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="97317-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="97317-112">İsim cmdlet'lerinizi diğer cmdlet'lerinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="97317-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="97317-113">İsimleri, cmdlet adları olmalıdır ve söz konusu olduğunda genel isimleri, özel, gibi *sunucu*, kaynağınızı benzer diğer kaynaklardan ayırır kısa bir önek eklemek idealdir.</span><span class="sxs-lookup"><span data-stu-id="97317-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="97317-114">Örneğin, bir isim öneki içeren bir cmdlet adı olan `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="97317-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="97317-115">Belirli bir isim daha genel bir fiil birleşimi cmdlet eylemi tarafından kolayca bulmak ve gereksiz cmdlet adı çoğaltma kaçınarak Bu cmdlet tarafından kaynağı tanımlamak kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="97317-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="97317-116">Cmdlet adları kullanılamaz, özel karakterler bir listesi için bkz. [gerekli geliştirme yönergeleri](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="97317-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="97317-117">Fiiller</span><span class="sxs-lookup"><span data-stu-id="97317-117">Verbs</span></span>

<span data-ttu-id="97317-118">Fiil belirttiğinizde, geliştirme yönergeleri Windows PowerShell tarafından sağlanan önceden tanımlanmış fiillerden biri kullanmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97317-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="97317-119">Bu önceden tanımlanmış fiillerden biri kullanarak yazdığınız cmdlet'leri ve Microsoft tarafından ve başkaları tarafından yazılan cmdlet'ler arasında tutarlılığı garanti eder.</span><span class="sxs-lookup"><span data-stu-id="97317-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="97317-120">Örneğin, "Al" fiili veri almak için cmdlet'leri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97317-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="97317-121">Fiiller yönergeleri hakkında daha fazla bilgi için bkz. [Cmdlet fiili adları](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="97317-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="97317-122">Cmdlet adları kullanılamaz, özel karakterler bir listesi için bkz. [gerekli geliştirme yönergeleri](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="97317-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="97317-123">Windows PowerShell işlevselliği destekleme</span><span class="sxs-lookup"><span data-stu-id="97317-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="97317-124">**Cmdlet'i** özniteliği de cmdlet'inize bazı Windows PowerShell tarafından sağlanan genel işlevlerini destekler belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="97317-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="97317-125">Bu, kullanıcı geri bildirim onayı (ShouldProcess özelliği desteği olarak adlandırılır) gibi ortak işlevselliği ve işlemler için desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="97317-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="97317-126">(İşlemler için destek Windows PowerShell 2. 0'de sunulmuştur).</span><span class="sxs-lookup"><span data-stu-id="97317-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="97317-127">Belirtmek için kullanılan bildirim sözdizimi hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="97317-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="97317-128">Cmdlet'i sınıf tanımı</span><span class="sxs-lookup"><span data-stu-id="97317-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="97317-129">Aşağıdaki kod, GetProc cmdlet'i sınıf tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="97317-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="97317-130">Bu Pascal casing kullanılır ve sınıf adını fiil ve isim cmdlet içerir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="97317-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="97317-131">Pascal büyük/küçük harf</span><span class="sxs-lookup"><span data-stu-id="97317-131">Pascal Casing</span></span>

<span data-ttu-id="97317-132">Cmdlet adı Pascal kullanarak büyük/küçük harf.</span><span class="sxs-lookup"><span data-stu-id="97317-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="97317-133">Örneğin, `Get-Item` ve `Get-ItemProperty` cmdlet'leri cmdlet'leri adlandırırken büyük küçük harf kullanımının doğru şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="97317-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="97317-134">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="97317-134">See Also</span></span>

[<span data-ttu-id="97317-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="97317-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="97317-136">CmdletAttribute bildirimi</span><span class="sxs-lookup"><span data-stu-id="97317-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="97317-137">Cmdlet fiili adları</span><span class="sxs-lookup"><span data-stu-id="97317-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="97317-138">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="97317-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="97317-139">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="97317-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
