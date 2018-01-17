---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: "pswaauthorizationrule Kaldır"
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="bab0a-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bab0a-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="bab0a-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="bab0a-104">SYNOPSIS</span></span>

<span data-ttu-id="bab0a-105">Windows PowerShell® Web Access'ten belirtilen bir yetkilendirme kuralını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bab0a-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="bab0a-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="bab0a-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="bab0a-107">Id</span><span class="sxs-lookup"><span data-stu-id="bab0a-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="bab0a-108">Kural</span><span class="sxs-lookup"><span data-stu-id="bab0a-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="bab0a-109">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="bab0a-109">DESCRIPTION</span></span>

<span data-ttu-id="bab0a-110">Windows PowerShell Web Erişimi'nden belirtilen bir yetkilendirme kuralını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bab0a-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="bab0a-111">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="bab0a-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="bab0a-112">-Force</span><span class="sxs-lookup"><span data-stu-id="bab0a-112">-Force</span></span>

<span data-ttu-id="bab0a-113">Cmdlet'i onay istemeden çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="bab0a-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="bab0a-114">Varsayılan olarak cmdlet devam etmeden önce onay ister.</span><span class="sxs-lookup"><span data-stu-id="bab0a-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="bab0a-115">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="bab0a-115">Aliases</span></span>                              | <span data-ttu-id="bab0a-116">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-116">none</span></span>                                 |
| <span data-ttu-id="bab0a-117">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-117">Required?</span></span>                            | <span data-ttu-id="bab0a-118">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-118">false</span></span>                                |
| <span data-ttu-id="bab0a-119">Konumu?</span><span class="sxs-lookup"><span data-stu-id="bab0a-119">Position?</span></span>                            | <span data-ttu-id="bab0a-120">Adlı</span><span class="sxs-lookup"><span data-stu-id="bab0a-120">named</span></span>                                |
| <span data-ttu-id="bab0a-121">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="bab0a-121">Default Value</span></span>                        | <span data-ttu-id="bab0a-122">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-122">none</span></span>                                 |
| <span data-ttu-id="bab0a-123">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bab0a-124">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-124">false</span></span>                                |
| <span data-ttu-id="bab0a-125">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bab0a-126">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="bab0a-127">-ID &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="bab0a-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="bab0a-128">Tanımlayıcılar (Kimlikler) kaldırmak için bir veya daha fazla kural belirtir.</span><span class="sxs-lookup"><span data-stu-id="bab0a-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="bab0a-129">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="bab0a-129">Aliases</span></span>                              | <span data-ttu-id="bab0a-130">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-130">none</span></span>                                 |
| <span data-ttu-id="bab0a-131">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-131">Required?</span></span>                            | <span data-ttu-id="bab0a-132">TRUE</span><span class="sxs-lookup"><span data-stu-id="bab0a-132">true</span></span>                                 |
| <span data-ttu-id="bab0a-133">Konumu?</span><span class="sxs-lookup"><span data-stu-id="bab0a-133">Position?</span></span>                            | <span data-ttu-id="bab0a-134">2</span><span class="sxs-lookup"><span data-stu-id="bab0a-134">2</span></span>                                    |
| <span data-ttu-id="bab0a-135">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="bab0a-135">Default Value</span></span>                        | <span data-ttu-id="bab0a-136">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-136">none</span></span>                                 |
| <span data-ttu-id="bab0a-137">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bab0a-138">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bab0a-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="bab0a-139">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bab0a-140">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="bab0a-141">-Kural &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="bab0a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="bab0a-142">Kaldırmak için kuralları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bab0a-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="bab0a-143">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="bab0a-143">Aliases</span></span>                              | <span data-ttu-id="bab0a-144">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-144">none</span></span>                                 |
| <span data-ttu-id="bab0a-145">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-145">Required?</span></span>                            | <span data-ttu-id="bab0a-146">TRUE</span><span class="sxs-lookup"><span data-stu-id="bab0a-146">true</span></span>                                 |
| <span data-ttu-id="bab0a-147">Konumu?</span><span class="sxs-lookup"><span data-stu-id="bab0a-147">Position?</span></span>                            | <span data-ttu-id="bab0a-148">2</span><span class="sxs-lookup"><span data-stu-id="bab0a-148">2</span></span>                                    |
| <span data-ttu-id="bab0a-149">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="bab0a-149">Default Value</span></span>                        | <span data-ttu-id="bab0a-150">yok</span><span class="sxs-lookup"><span data-stu-id="bab0a-150">none</span></span>                                 |
| <span data-ttu-id="bab0a-151">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bab0a-152">TRUE (ByValue)</span><span class="sxs-lookup"><span data-stu-id="bab0a-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="bab0a-153">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bab0a-154">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="bab0a-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bab0a-155">-Confirm</span></span>

<span data-ttu-id="bab0a-156">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="bab0a-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="bab0a-157">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-157">Required?</span></span>                            | <span data-ttu-id="bab0a-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-158">false</span></span>                                |
| <span data-ttu-id="bab0a-159">Konumu?</span><span class="sxs-lookup"><span data-stu-id="bab0a-159">Position?</span></span>                            | <span data-ttu-id="bab0a-160">Adlı</span><span class="sxs-lookup"><span data-stu-id="bab0a-160">named</span></span>                                |
| <span data-ttu-id="bab0a-161">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="bab0a-161">Default Value</span></span>                        | <span data-ttu-id="bab0a-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-162">false</span></span>                                |
| <span data-ttu-id="bab0a-163">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bab0a-164">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-164">false</span></span>                                |
| <span data-ttu-id="bab0a-165">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bab0a-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="bab0a-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bab0a-167">-WhatIf</span></span>

<span data-ttu-id="bab0a-168">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bab0a-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bab0a-169">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="bab0a-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="bab0a-170">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-170">Required?</span></span>                            | <span data-ttu-id="bab0a-171">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-171">false</span></span>                                |
| <span data-ttu-id="bab0a-172">Konumu?</span><span class="sxs-lookup"><span data-stu-id="bab0a-172">Position?</span></span>                            | <span data-ttu-id="bab0a-173">Adlı</span><span class="sxs-lookup"><span data-stu-id="bab0a-173">named</span></span>                                |
| <span data-ttu-id="bab0a-174">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="bab0a-174">Default Value</span></span>                        | <span data-ttu-id="bab0a-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-175">false</span></span>                                |
| <span data-ttu-id="bab0a-176">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bab0a-177">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-177">false</span></span>                                |
| <span data-ttu-id="bab0a-178">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="bab0a-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bab0a-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="bab0a-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="bab0a-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="bab0a-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="bab0a-181">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="bab0a-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="bab0a-182">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bab0a-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="bab0a-183">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="bab0a-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="bab0a-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="bab0a-184">int\[\]</span></span>

<span data-ttu-id="bab0a-185">Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="bab0a-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="bab0a-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="bab0a-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="bab0a-187">Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="bab0a-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="bab0a-188">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="bab0a-188">OUTPUTS</span></span>

<span data-ttu-id="bab0a-189">Bu cmdlet herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="bab0a-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="bab0a-190">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="bab0a-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="bab0a-191">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="bab0a-191">EXAMPLE 1</span></span>

<span data-ttu-id="bab0a-192">Bu örnek Kimliğine sahip yetkilendirme kuralını kaldırır *2*.</span><span class="sxs-lookup"><span data-stu-id="bab0a-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="bab0a-193">Örnek 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="bab0a-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="bab0a-194">Bu örnekte, tüm yetkilendirme kurallarını kaldırır ve ayrıca kullanıcı tarafından onay gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bab0a-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="bab0a-195">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="bab0a-195">Related topics</span></span>

- [<span data-ttu-id="bab0a-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bab0a-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="bab0a-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bab0a-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="bab0a-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="bab0a-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="bab0a-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bab0a-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
