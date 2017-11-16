---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: Test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="4ba46-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ba46-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4ba46-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="4ba46-104">SYNOPSIS</span></span>

<span data-ttu-id="4ba46-105">Bir kural belirtilen kullanıcı, bilgisayar veya uç nokta için mevcut olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="4ba46-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ba46-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="4ba46-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="4ba46-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4ba46-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="4ba46-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="4ba46-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4ba46-109">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="4ba46-109">DESCRIPTION</span></span>

<span data-ttu-id="4ba46-110">**Test-PswaAuthorizationRule** cmdlet, bir kural belirtilen kullanıcı, bilgisayar veya uç nokta için mevcut olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="4ba46-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="4ba46-111">Bu cmdlet, belirli bir kullanıcı, bilgisayar veya uç nokta erişim isteği yetkili olduğunu doğrulamak için yetkilendirme kuralları, test etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="4ba46-112">Varsayılan olarak, bu cmdlet yetkilendirme dosyasında tüm kuralları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="4ba46-113">Ancak, test etmek için kurallar kümesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba46-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="4ba46-114">Kimlik doğrulama hataları gidermek için bu cmdlet'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba46-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="4ba46-115">Bu cmdlet parametrelerini alanları Windows PowerShell® Web Access oturum açma sayfasında karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="4ba46-116">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="4ba46-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="4ba46-117">-ComputerName &lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="4ba46-118">Test etmek için bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-119">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-119">Aliases</span></span>                              | <span data-ttu-id="4ba46-120">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-120">none</span></span>                                 |
| <span data-ttu-id="4ba46-121">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-121">Required?</span></span>                            | <span data-ttu-id="4ba46-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="4ba46-122">true</span></span>                                 |
| <span data-ttu-id="4ba46-123">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-123">Position?</span></span>                            | <span data-ttu-id="4ba46-124">2</span><span class="sxs-lookup"><span data-stu-id="4ba46-124">2</span></span>                                    |
| <span data-ttu-id="4ba46-125">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-125">Default Value</span></span>                        | <span data-ttu-id="4ba46-126">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-126">none</span></span>                                 |
| <span data-ttu-id="4ba46-127">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-128">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-128">false</span></span>                                |
| <span data-ttu-id="4ba46-129">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-130">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="4ba46-131">-ConfigurationName &lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="4ba46-132">Test etmek için Windows PowerShell oturum yapılandırmasını, uç nokta veya çalışma alanı olarak da bilinen adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-133">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-133">Aliases</span></span>                              | <span data-ttu-id="4ba46-134">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-134">none</span></span>                                 |
| <span data-ttu-id="4ba46-135">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-135">Required?</span></span>                            | <span data-ttu-id="4ba46-136">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-136">false</span></span>                                |
| <span data-ttu-id="4ba46-137">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-137">Position?</span></span>                            | <span data-ttu-id="4ba46-138">3</span><span class="sxs-lookup"><span data-stu-id="4ba46-138">3</span></span>                                    |
| <span data-ttu-id="4ba46-139">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-139">Default Value</span></span>                        | <span data-ttu-id="4ba46-140">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-140">none</span></span>                                 |
| <span data-ttu-id="4ba46-141">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-142">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-142">false</span></span>                                |
| <span data-ttu-id="4ba46-143">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-144">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="4ba46-145">-ConnectionUri &lt;URI&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="4ba46-146">Bağlantıyı sınamak için URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-147">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-147">Aliases</span></span>                              | <span data-ttu-id="4ba46-148">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-148">none</span></span>                                 |
| <span data-ttu-id="4ba46-149">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-149">Required?</span></span>                            | <span data-ttu-id="4ba46-150">TRUE</span><span class="sxs-lookup"><span data-stu-id="4ba46-150">true</span></span>                                 |
| <span data-ttu-id="4ba46-151">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-151">Position?</span></span>                            | <span data-ttu-id="4ba46-152">2</span><span class="sxs-lookup"><span data-stu-id="4ba46-152">2</span></span>                                    |
| <span data-ttu-id="4ba46-153">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-153">Default Value</span></span>                        | <span data-ttu-id="4ba46-154">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-154">none</span></span>                                 |
| <span data-ttu-id="4ba46-155">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-156">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-156">false</span></span>                                |
| <span data-ttu-id="4ba46-157">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="4ba46-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="4ba46-160">Belirten bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kuralları test etmek için kullanmak istediğiniz bir kullanıcı hesabı için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4ba46-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="4ba46-161">Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ba46-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="4ba46-162">Alınacak bir **PSCredential** yetkilendirme kuralları uzaktan test, çalıştırmak için gerekli olan nesne, [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4ba46-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-163">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-163">Aliases</span></span>                              | <span data-ttu-id="4ba46-164">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-164">none</span></span>                                 |
| <span data-ttu-id="4ba46-165">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-165">Required?</span></span>                            | <span data-ttu-id="4ba46-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-166">false</span></span>                                |
| <span data-ttu-id="4ba46-167">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-167">Position?</span></span>                            | <span data-ttu-id="4ba46-168">Adlı</span><span class="sxs-lookup"><span data-stu-id="4ba46-168">named</span></span>                                |
| <span data-ttu-id="4ba46-169">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-169">Default Value</span></span>                        | <span data-ttu-id="4ba46-170">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-170">none</span></span>                                 |
| <span data-ttu-id="4ba46-171">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-172">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-172">false</span></span>                                |
| <span data-ttu-id="4ba46-173">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-174">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="4ba46-175">-Kural &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="4ba46-176">Test etmek için kurallar kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="4ba46-177">Bu parametre belirtilmezse, bu cmdlet'i tüm yetkilendirme kurallarını karşı sınar.</span><span class="sxs-lookup"><span data-stu-id="4ba46-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-178">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-178">Aliases</span></span>                              | <span data-ttu-id="4ba46-179">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-179">none</span></span>                                 |
| <span data-ttu-id="4ba46-180">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-180">Required?</span></span>                            | <span data-ttu-id="4ba46-181">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-181">false</span></span>                                |
| <span data-ttu-id="4ba46-182">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-182">Position?</span></span>                            | <span data-ttu-id="4ba46-183">Adlı</span><span class="sxs-lookup"><span data-stu-id="4ba46-183">named</span></span>                                |
| <span data-ttu-id="4ba46-184">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-184">Default Value</span></span>                        | <span data-ttu-id="4ba46-185">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-185">none</span></span>                                 |
| <span data-ttu-id="4ba46-186">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-187">TRUE (ByValue)</span><span class="sxs-lookup"><span data-stu-id="4ba46-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="4ba46-188">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-189">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="4ba46-190">-UserName &lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="4ba46-191">Test etmek için kullanıcı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ba46-192">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="4ba46-192">Aliases</span></span>                              | <span data-ttu-id="4ba46-193">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-193">none</span></span>                                 |
| <span data-ttu-id="4ba46-194">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-194">Required?</span></span>                            | <span data-ttu-id="4ba46-195">TRUE</span><span class="sxs-lookup"><span data-stu-id="4ba46-195">true</span></span>                                 |
| <span data-ttu-id="4ba46-196">Konumu?</span><span class="sxs-lookup"><span data-stu-id="4ba46-196">Position?</span></span>                            | <span data-ttu-id="4ba46-197">1</span><span class="sxs-lookup"><span data-stu-id="4ba46-197">1</span></span>                                    |
| <span data-ttu-id="4ba46-198">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="4ba46-198">Default Value</span></span>                        | <span data-ttu-id="4ba46-199">yok</span><span class="sxs-lookup"><span data-stu-id="4ba46-199">none</span></span>                                 |
| <span data-ttu-id="4ba46-200">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ba46-201">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-201">false</span></span>                                |
| <span data-ttu-id="4ba46-202">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="4ba46-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ba46-203">yanlış</span><span class="sxs-lookup"><span data-stu-id="4ba46-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4ba46-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4ba46-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4ba46-205">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4ba46-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4ba46-206">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ba46-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4ba46-207">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="4ba46-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4ba46-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4ba46-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4ba46-209">Bu cmdlet PswaAuthorizationRule nesneleri içeren bir dizi girdi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba46-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4ba46-210">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="4ba46-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4ba46-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4ba46-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4ba46-212">Bu cmdlet PswaAuthorizationRule nesnelerinin bir dizisi çıktı olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="4ba46-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="4ba46-213">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="4ba46-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4ba46-214">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="4ba46-214">EXAMPLE 1</span></span>

<span data-ttu-id="4ba46-215">Bu örnekte, kullanıcı izin veren tüm kuralları görüntülemek için tüm yetkilendirme kurallarını testleri *contoso\\mhanson* bilgisayara bağlanmak için *SUN2* ve bir Windows PowerShell oturumu kullanın adlı Yapılandırması *test*.</span><span class="sxs-lookup"><span data-stu-id="4ba46-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="4ba46-216">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="4ba46-216">EXAMPLE 2</span></span>

<span data-ttu-id="4ba46-217">Hangi Yetkilendirme kurallarını denetlemek için tüm yetkilendirme kuralları geçerli kullanıcıya bu örnekte testleri *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="4ba46-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="4ba46-218">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="4ba46-218">Related topics</span></span>

- [<span data-ttu-id="4ba46-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ba46-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4ba46-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ba46-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="4ba46-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4ba46-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="4ba46-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ba46-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
