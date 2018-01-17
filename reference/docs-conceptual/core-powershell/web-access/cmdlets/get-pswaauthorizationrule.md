---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: pswaauthorizationrule Al
ms.technology: powershell
ms.openlocfilehash: 003195457660a18b9bbed065181b6d8c23835348
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="ff5a6-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ff5a6-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff5a6-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="ff5a6-104">SYNOPSIS</span></span>

<span data-ttu-id="ff5a6-105">Windows PowerShell® Web Erişimi yetkilendirme kuralları kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff5a6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff5a6-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="ff5a6-107">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ff5a6-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="ff5a6-108">Ad</span><span class="sxs-lookup"><span data-stu-id="ff5a6-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ff5a6-109">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="ff5a6-109">DESCRIPTION</span></span>

<span data-ttu-id="ff5a6-110">**Get-PswaAuthorizationRule** cmdlet'i Windows PowerShell® Web Erişimi yetkilendirme kuralları kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="ff5a6-111">Ne **kimliği** parametresi ya da **RuleName** parametresi belirtilirse, sonra Bu cmdlet tüm kuralları listeler.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="ff5a6-112">**Kimliği** parametresi, sonuçlara filtre uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="ff5a6-113">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="ff5a6-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="ff5a6-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ff5a6-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="ff5a6-115">Bu cmdlet alması gereken kuralların tanımlayıcılar (Kimlikler) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="ff5a6-116">Hiçbir kimlikleri belirtilirse, bu cmdlet tüm yetkilendirme kurallarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="ff5a6-117">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="ff5a6-117">Aliases</span></span>                              | <span data-ttu-id="ff5a6-118">yok</span><span class="sxs-lookup"><span data-stu-id="ff5a6-118">none</span></span>                                 |
| <span data-ttu-id="ff5a6-119">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-119">Required?</span></span>                            | <span data-ttu-id="ff5a6-120">yanlış</span><span class="sxs-lookup"><span data-stu-id="ff5a6-120">false</span></span>                                |
| <span data-ttu-id="ff5a6-121">Konumu?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-121">Position?</span></span>                            | <span data-ttu-id="ff5a6-122">2</span><span class="sxs-lookup"><span data-stu-id="ff5a6-122">2</span></span>                                    |
| <span data-ttu-id="ff5a6-123">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="ff5a6-123">Default Value</span></span>                        | <span data-ttu-id="ff5a6-124">yok</span><span class="sxs-lookup"><span data-stu-id="ff5a6-124">none</span></span>                                 |
| <span data-ttu-id="ff5a6-125">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ff5a6-126">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="ff5a6-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="ff5a6-127">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ff5a6-128">yanlış</span><span class="sxs-lookup"><span data-stu-id="ff5a6-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="ff5a6-129">-RuleName&lt;dize\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ff5a6-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="ff5a6-130">Almak için yetkilendirme kuralları adlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="ff5a6-131">Bu parametre, bu diziye dizelerde kuralı adları tam olarak eşleşen tüm kuralları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="ff5a6-132">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="ff5a6-132">Aliases</span></span>                              | <span data-ttu-id="ff5a6-133">yok</span><span class="sxs-lookup"><span data-stu-id="ff5a6-133">none</span></span>                                 |
| <span data-ttu-id="ff5a6-134">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-134">Required?</span></span>                            | <span data-ttu-id="ff5a6-135">TRUE</span><span class="sxs-lookup"><span data-stu-id="ff5a6-135">true</span></span>                                 |
| <span data-ttu-id="ff5a6-136">Konumu?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-136">Position?</span></span>                            | <span data-ttu-id="ff5a6-137">2</span><span class="sxs-lookup"><span data-stu-id="ff5a6-137">2</span></span>                                    |
| <span data-ttu-id="ff5a6-138">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="ff5a6-138">Default Value</span></span>                        | <span data-ttu-id="ff5a6-139">yok</span><span class="sxs-lookup"><span data-stu-id="ff5a6-139">none</span></span>                                 |
| <span data-ttu-id="ff5a6-140">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ff5a6-141">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="ff5a6-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="ff5a6-142">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="ff5a6-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ff5a6-143">yanlış</span><span class="sxs-lookup"><span data-stu-id="ff5a6-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ff5a6-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ff5a6-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ff5a6-145">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ff5a6-146">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ff5a6-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ff5a6-147">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="ff5a6-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="ff5a6-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="ff5a6-148">int\[\]</span></span>

<span data-ttu-id="ff5a6-149">Bu cmdlet dizisi veya dize değerlerini bir dizi girdi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="ff5a6-150">Dize\[\]</span><span class="sxs-lookup"><span data-stu-id="ff5a6-150">String\[\]</span></span>

<span data-ttu-id="ff5a6-151">Bu cmdlet dizisi veya dize değerlerini bir dizi girdi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="ff5a6-152">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="ff5a6-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ff5a6-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ff5a6-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ff5a6-154">Bu cmdlet bir PswaAuthorizationRule nesnesi çıktı olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="ff5a6-155">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="ff5a6-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ff5a6-156">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="ff5a6-156">EXAMPLE 1</span></span>

<span data-ttu-id="ff5a6-157">Bu örnekte tüm kurallar alır.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="ff5a6-158">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="ff5a6-158">EXAMPLE 2</span></span>

<span data-ttu-id="ff5a6-159">Bu örnek Kimliğine sahip bir kural alır *2*.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="ff5a6-160">Örnek 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="ff5a6-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="ff5a6-161">Bu örnekte, nasıl cmdlet ardışık düzen arasında bir değer kabul gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="ff5a6-162">Bu cmdlet, bir kural kimliği ve bir kural adı geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ff5a6-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="ff5a6-163">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="ff5a6-163">Related topics</span></span>

- [<span data-ttu-id="ff5a6-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ff5a6-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="ff5a6-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ff5a6-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="ff5a6-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ff5a6-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="ff5a6-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ff5a6-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
