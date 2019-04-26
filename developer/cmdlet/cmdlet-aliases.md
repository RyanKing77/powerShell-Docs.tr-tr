---
title: Cmdlet diğer adları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068734"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="ae42f-102">Cmdlet Diğer Adları</span><span class="sxs-lookup"><span data-stu-id="ae42f-102">Cmdlet Aliases</span></span>

<span data-ttu-id="ae42f-103">Cmdlet diğer adlar, cmdlet kullanıcı deneyimini geliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae42f-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="ae42f-104">Sık kullanılan cmdlet'leri yazarak azaltmak ve görevleri tamamlamak için hızlı bir şekilde kolaylaştırmak için diğer adları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae42f-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="ae42f-105">Yerleşik diğer adlar, cmdlet'ler içerebilir veya kullanıcılar, kendi özel diğer adlar tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ae42f-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="ae42f-106">Örneğin, [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet'i sahip yerleşik `gcm` diğer adı.</span><span class="sxs-lookup"><span data-stu-id="ae42f-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="ae42f-107">Diğer adlar, böylece kullanıcılar, yeni komutlarını öğrenmeniz gerekmez. diğer dillerde komut adları eklemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae42f-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="ae42f-108">Diğer ad kuralları</span><span class="sxs-lookup"><span data-stu-id="ae42f-108">Alias Guidelines</span></span>

<span data-ttu-id="ae42f-109">Yerleşik diğer adlar için cmdlet'lerinizi oluşturduğunuzda aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="ae42f-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="ae42f-110">Diğer adlar atamadan önce Windows PowerShell'i başlatın ve ardından çalıştırın [Get-diğer ad](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) zaten kullanılan diğer adlarını görmek için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae42f-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="ae42f-111">Cmdlet adı ve cmdlet adı isim başvuran bir diğer ad soneki fiili başvuran bir diğer ad ön eki ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae42f-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="ae42f-112">Örneğin, diğer `Import-Module` cmdlet'tir "ipmo".</span><span class="sxs-lookup"><span data-stu-id="ae42f-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="ae42f-113">Tüm fiiller ve diğer adlarını listesi için bkz: [Cmdlet fiilleri](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ae42f-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="ae42f-114">Aynı diğer ad ön eki aynı fiili sahip cmdlet'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="ae42f-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="ae42f-115">Örneğin, adında "Get" fiili sahip tüm Windows PowerShell cmdlet'leri için diğer adlar, "g" ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae42f-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="ae42f-116">Aynı isim sahip cmdlet'leri, aynı diğer ad soneki içerir.</span><span class="sxs-lookup"><span data-stu-id="ae42f-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="ae42f-117">Örneğin, adında "Oturumu" isim sahip tüm Windows PowerShell cmdlet'leri için diğer adlar "sn" soneki kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae42f-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="ae42f-118">Diğer dillerde komutlar eşdeğerdir cmdlet'leri için komut adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae42f-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="ae42f-119">Genel olarak, diğer adlar olabildiğince kısa yapın.</span><span class="sxs-lookup"><span data-stu-id="ae42f-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="ae42f-120">Diğer ad fiil için ayrı en az bir karakter ve isim için farklı bir karakter olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ae42f-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="ae42f-121">Diğer adı benzersiz hale getirmek için gerektiği şekilde daha fazla karakter ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae42f-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae42f-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ae42f-122">See Also</span></span>

[<span data-ttu-id="ae42f-123">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="ae42f-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
