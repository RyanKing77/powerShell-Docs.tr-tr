---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: "pswaauthorizationrule Kaldır"
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="0ec34-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0ec34-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="0ec34-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="0ec34-104">SYNOPSIS</span></span>

<span data-ttu-id="0ec34-105">Windows PowerShell® Web Access'ten belirtilen bir yetkilendirme kuralını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ec34-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ec34-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="0ec34-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="0ec34-107">Id</span><span class="sxs-lookup"><span data-stu-id="0ec34-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="0ec34-108">Kural</span><span class="sxs-lookup"><span data-stu-id="0ec34-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="0ec34-109">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="0ec34-109">DESCRIPTION</span></span>

<span data-ttu-id="0ec34-110">Windows PowerShell Web Erişimi'nden belirtilen bir yetkilendirme kuralını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ec34-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="0ec34-111">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="0ec34-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="0ec34-112">-Force</span><span class="sxs-lookup"><span data-stu-id="0ec34-112">-Force</span></span>

<span data-ttu-id="0ec34-113">Cmdlet'i onay istemeden çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0ec34-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="0ec34-114">Varsayılan olarak cmdlet devam etmeden önce onay ister.</span><span class="sxs-lookup"><span data-stu-id="0ec34-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="0ec34-115">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="0ec34-115">Aliases</span></span>                              | <span data-ttu-id="0ec34-116">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-116">none</span></span>                                 |
| <span data-ttu-id="0ec34-117">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-117">Required?</span></span>                            | <span data-ttu-id="0ec34-118">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-118">false</span></span>                                |
| <span data-ttu-id="0ec34-119">Konumu?</span><span class="sxs-lookup"><span data-stu-id="0ec34-119">Position?</span></span>                            | <span data-ttu-id="0ec34-120">Adlı</span><span class="sxs-lookup"><span data-stu-id="0ec34-120">named</span></span>                                |
| <span data-ttu-id="0ec34-121">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="0ec34-121">Default Value</span></span>                        | <span data-ttu-id="0ec34-122">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-122">none</span></span>                                 |
| <span data-ttu-id="0ec34-123">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0ec34-124">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-124">false</span></span>                                |
| <span data-ttu-id="0ec34-125">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0ec34-126">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="0ec34-127">-ID &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0ec34-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="0ec34-128">Tanımlayıcılar (Kimlikler) kaldırmak için bir veya daha fazla kural belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ec34-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="0ec34-129">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="0ec34-129">Aliases</span></span>                              | <span data-ttu-id="0ec34-130">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-130">none</span></span>                                 |
| <span data-ttu-id="0ec34-131">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-131">Required?</span></span>                            | <span data-ttu-id="0ec34-132">TRUE</span><span class="sxs-lookup"><span data-stu-id="0ec34-132">true</span></span>                                 |
| <span data-ttu-id="0ec34-133">Konumu?</span><span class="sxs-lookup"><span data-stu-id="0ec34-133">Position?</span></span>                            | <span data-ttu-id="0ec34-134">2</span><span class="sxs-lookup"><span data-stu-id="0ec34-134">2</span></span>                                    |
| <span data-ttu-id="0ec34-135">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="0ec34-135">Default Value</span></span>                        | <span data-ttu-id="0ec34-136">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-136">none</span></span>                                 |
| <span data-ttu-id="0ec34-137">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0ec34-138">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0ec34-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0ec34-139">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0ec34-140">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="0ec34-141">-Kural &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0ec34-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="0ec34-142">Kaldırmak için kuralları belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ec34-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="0ec34-143">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="0ec34-143">Aliases</span></span>                              | <span data-ttu-id="0ec34-144">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-144">none</span></span>                                 |
| <span data-ttu-id="0ec34-145">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-145">Required?</span></span>                            | <span data-ttu-id="0ec34-146">TRUE</span><span class="sxs-lookup"><span data-stu-id="0ec34-146">true</span></span>                                 |
| <span data-ttu-id="0ec34-147">Konumu?</span><span class="sxs-lookup"><span data-stu-id="0ec34-147">Position?</span></span>                            | <span data-ttu-id="0ec34-148">2</span><span class="sxs-lookup"><span data-stu-id="0ec34-148">2</span></span>                                    |
| <span data-ttu-id="0ec34-149">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="0ec34-149">Default Value</span></span>                        | <span data-ttu-id="0ec34-150">yok</span><span class="sxs-lookup"><span data-stu-id="0ec34-150">none</span></span>                                 |
| <span data-ttu-id="0ec34-151">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0ec34-152">TRUE (ByValue)</span><span class="sxs-lookup"><span data-stu-id="0ec34-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="0ec34-153">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0ec34-154">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="0ec34-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0ec34-155">-Confirm</span></span>

<span data-ttu-id="0ec34-156">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="0ec34-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="0ec34-157">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-157">Required?</span></span>                            | <span data-ttu-id="0ec34-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-158">false</span></span>                                |
| <span data-ttu-id="0ec34-159">Konumu?</span><span class="sxs-lookup"><span data-stu-id="0ec34-159">Position?</span></span>                            | <span data-ttu-id="0ec34-160">Adlı</span><span class="sxs-lookup"><span data-stu-id="0ec34-160">named</span></span>                                |
| <span data-ttu-id="0ec34-161">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="0ec34-161">Default Value</span></span>                        | <span data-ttu-id="0ec34-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-162">false</span></span>                                |
| <span data-ttu-id="0ec34-163">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0ec34-164">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-164">false</span></span>                                |
| <span data-ttu-id="0ec34-165">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0ec34-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="0ec34-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0ec34-167">-WhatIf</span></span>

<span data-ttu-id="0ec34-168">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ec34-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0ec34-169">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="0ec34-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="0ec34-170">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-170">Required?</span></span>                            | <span data-ttu-id="0ec34-171">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-171">false</span></span>                                |
| <span data-ttu-id="0ec34-172">Konumu?</span><span class="sxs-lookup"><span data-stu-id="0ec34-172">Position?</span></span>                            | <span data-ttu-id="0ec34-173">Adlı</span><span class="sxs-lookup"><span data-stu-id="0ec34-173">named</span></span>                                |
| <span data-ttu-id="0ec34-174">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="0ec34-174">Default Value</span></span>                        | <span data-ttu-id="0ec34-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-175">false</span></span>                                |
| <span data-ttu-id="0ec34-176">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0ec34-177">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-177">false</span></span>                                |
| <span data-ttu-id="0ec34-178">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="0ec34-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0ec34-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="0ec34-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="0ec34-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="0ec34-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="0ec34-181">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="0ec34-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="0ec34-182">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0ec34-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="0ec34-183">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="0ec34-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="0ec34-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="0ec34-184">int\[\]</span></span>

<span data-ttu-id="0ec34-185">Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0ec34-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="0ec34-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="0ec34-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="0ec34-187">Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0ec34-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="0ec34-188">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="0ec34-188">OUTPUTS</span></span>

<span data-ttu-id="0ec34-189">Bu cmdlet herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0ec34-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="0ec34-190">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="0ec34-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="0ec34-191">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="0ec34-191">EXAMPLE 1</span></span>

<span data-ttu-id="0ec34-192">Bu örnek Kimliğine sahip yetkilendirme kuralını kaldırır *2*.</span><span class="sxs-lookup"><span data-stu-id="0ec34-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="0ec34-193">Örnek 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="0ec34-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="0ec34-194">Bu örnekte, tüm yetkilendirme kurallarını kaldırır ve ayrıca kullanıcı tarafından onay gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0ec34-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="0ec34-195">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="0ec34-195">Related topics</span></span>

- [<span data-ttu-id="0ec34-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0ec34-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="0ec34-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0ec34-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="0ec34-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="0ec34-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="0ec34-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0ec34-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
