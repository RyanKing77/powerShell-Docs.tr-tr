---
title: Cmdlet parametrelerini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845307"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="1b39e-102">Cmdlet Parametreleri</span><span class="sxs-lookup"><span data-stu-id="1b39e-102">Cmdlet Parameters</span></span>

<span data-ttu-id="1b39e-103">Cmdlet parametreleri, giriş kabul etmek bir cmdlet sağlayan bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b39e-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="1b39e-104">Komut satırından doğrudan ya da işlem hattında, bağımsız değişkenler cmdlet'e geçirilen nesnelerinden bir giriş parametreleri kabul eder (olarak da bilinen *değerleri*) bu parametrelerinin cmdlet'in kabul eder, giriş belirtebilirsiniz nasıl cmdlet eylemlerini ve cmdlet döndürür işlem hattının verileri gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b39e-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1b39e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1b39e-105">In This Section</span></span>

<span data-ttu-id="1b39e-106">[Parametre olarak özellikleri bildirme](./declaring-properties-as-parameters.md) anlamanız gerekir bir cmdlet parametreleri bildirmek önce temel bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b39e-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="1b39e-107">[Cmdlet'i parametre türleri](./types-of-cmdlet-parameters.md) cmdlet'leri bildirebilirsiniz parametreleri farklı türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b39e-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="1b39e-108">[Cmdlet parametresi adı ve işlevsellik yönergeleri](./standard-cmdlet-parameter-names-and-types.md) önerilen veri türü ve standart parametreler işlevselliğini Discuses adları.</span><span class="sxs-lookup"><span data-stu-id="1b39e-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="1b39e-109">[Parametre diğer adlarına](./parameter-aliases.md) parametrelerini tanımlayabilirsiniz diğer adlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1b39e-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="1b39e-110">[Genel parametre adları](./common-parameter-names.md) bu konuda, Windows PowerShell cmdlet'lerinde ekler parametreler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b39e-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="1b39e-111">[Cmdlet parametresi ayarlar](./cmdlet-parameter-sets.md) nasıl parametre kümeleri farklı senaryolar için farklı eylemler gerçekleştiren tek bir cmdlet yazmanıza olanak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1b39e-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="1b39e-112">[Cmdlet dinamik parametreleri](./cmdlet-dynamic-parameters.md) özel koşullar altında kullanıcının parametreleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1b39e-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="1b39e-113">[Cmdlet parametreleri joker karakterleri destekleme](./supporting-wildcard-characters-in-cmdlet-parameters.md) bir kaynak grubu üzerinde çalıştırılacak bir cmdlet tasarlarken desteklemek için joker karakter açıklar.</span><span class="sxs-lookup"><span data-stu-id="1b39e-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="1b39e-114">[Parametre girişi doğrulama](./validating-parameter-input.md) nasıl Windows PowerShell cmdlet parametreleri için geçirilen bağımsız değişkenler doğrular açıklar.</span><span class="sxs-lookup"><span data-stu-id="1b39e-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="1b39e-115">[Giriş filtre parametrelerini](./input-filter-parameters.md) Discusses `Filter`, `Include`, ve `Exclude` cmdlet etkiler giriş nesne kümesini filtrelemek parametreleri.</span><span class="sxs-lookup"><span data-stu-id="1b39e-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1b39e-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1b39e-116">Related Sections</span></span>

[<span data-ttu-id="1b39e-117">Parametre girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="1b39e-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="1b39e-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="1b39e-118">See Also</span></span>

[<span data-ttu-id="1b39e-119">Parametre özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="1b39e-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="1b39e-120">Windows PowerShell cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="1b39e-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
