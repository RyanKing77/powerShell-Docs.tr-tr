---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: pswawebapplication kaldırma
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="97b2f-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="97b2f-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="97b2f-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="97b2f-104">SYNOPSIS</span></span>

<span data-ttu-id="97b2f-105">Windows PowerShell® web uygulamasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="97b2f-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="97b2f-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="97b2f-107">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="97b2f-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="97b2f-108">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="97b2f-108">DESCRIPTION</span></span>

<span data-ttu-id="97b2f-109">**Uninstall-PswaWebApplication** cmdlet'i Windows PowerShell web uygulamasını kaldırır ve IIS Web sitesi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="97b2f-110">Cmdlet, IIS veya Windows PowerShell'i çalıştırmak gerekli olduğundan yüklü diğer özellikler kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="97b2f-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="97b2f-111">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="97b2f-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="97b2f-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="97b2f-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="97b2f-113">Sınama sertifikaları tarafından oluşturulan gösterir **yükleme\_PswaWebApplication** cmdlet (ile **UseTestCertificate** parametresi) silinir.</span><span class="sxs-lookup"><span data-stu-id="97b2f-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="97b2f-114">Yalnızca sınama sertifikası tarafından oluşturulan aynı ada sahip **Install-PswaWebApplication** cmdlet kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="97b2f-115">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="97b2f-115">Aliases</span></span>                              | <span data-ttu-id="97b2f-116">yok</span><span class="sxs-lookup"><span data-stu-id="97b2f-116">none</span></span>                                 |
| <span data-ttu-id="97b2f-117">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-117">Required?</span></span>                            | <span data-ttu-id="97b2f-118">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-118">false</span></span>                                |
| <span data-ttu-id="97b2f-119">Konumu?</span><span class="sxs-lookup"><span data-stu-id="97b2f-119">Position?</span></span>                            | <span data-ttu-id="97b2f-120">Adlı</span><span class="sxs-lookup"><span data-stu-id="97b2f-120">named</span></span>                                |
| <span data-ttu-id="97b2f-121">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="97b2f-121">Default Value</span></span>                        | <span data-ttu-id="97b2f-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="97b2f-122">true</span></span>                                 |
| <span data-ttu-id="97b2f-123">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b2f-124">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-124">false</span></span>                                |
| <span data-ttu-id="97b2f-125">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b2f-126">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="97b2f-127">-WebApplicationName &lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="97b2f-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="97b2f-128">Kaldırmak için web uygulamasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97b2f-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="97b2f-129">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="97b2f-129">Aliases</span></span>                              | <span data-ttu-id="97b2f-130">yok</span><span class="sxs-lookup"><span data-stu-id="97b2f-130">none</span></span>                                 |
| <span data-ttu-id="97b2f-131">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-131">Required?</span></span>                            | <span data-ttu-id="97b2f-132">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-132">false</span></span>                                |
| <span data-ttu-id="97b2f-133">Konumu?</span><span class="sxs-lookup"><span data-stu-id="97b2f-133">Position?</span></span>                            | <span data-ttu-id="97b2f-134">1</span><span class="sxs-lookup"><span data-stu-id="97b2f-134">1</span></span>                                    |
| <span data-ttu-id="97b2f-135">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="97b2f-135">Default Value</span></span>                        | <span data-ttu-id="97b2f-136">pswa</span><span class="sxs-lookup"><span data-stu-id="97b2f-136">pswa</span></span>                                 |
| <span data-ttu-id="97b2f-137">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b2f-138">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-138">false</span></span>                                |
| <span data-ttu-id="97b2f-139">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b2f-140">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="97b2f-141">-WebSiteName &lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="97b2f-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="97b2f-142">Web uygulamasının yüklendiği web sitesi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="97b2f-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="97b2f-143">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="97b2f-143">Aliases</span></span>                              | <span data-ttu-id="97b2f-144">yok</span><span class="sxs-lookup"><span data-stu-id="97b2f-144">none</span></span>                                 |
| <span data-ttu-id="97b2f-145">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-145">Required?</span></span>                            | <span data-ttu-id="97b2f-146">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-146">false</span></span>                                |
| <span data-ttu-id="97b2f-147">Konumu?</span><span class="sxs-lookup"><span data-stu-id="97b2f-147">Position?</span></span>                            | <span data-ttu-id="97b2f-148">Adlı</span><span class="sxs-lookup"><span data-stu-id="97b2f-148">named</span></span>                                |
| <span data-ttu-id="97b2f-149">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="97b2f-149">Default Value</span></span>                        | <span data-ttu-id="97b2f-150">Varsayılan Web sitesi</span><span class="sxs-lookup"><span data-stu-id="97b2f-150">Default Web Site</span></span>                     |
| <span data-ttu-id="97b2f-151">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b2f-152">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-152">false</span></span>                                |
| <span data-ttu-id="97b2f-153">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b2f-154">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="97b2f-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="97b2f-155">-Confirm</span></span>

<span data-ttu-id="97b2f-156">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="97b2f-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="97b2f-157">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-157">Required?</span></span>                            | <span data-ttu-id="97b2f-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-158">false</span></span>                                |
| <span data-ttu-id="97b2f-159">Konumu?</span><span class="sxs-lookup"><span data-stu-id="97b2f-159">Position?</span></span>                            | <span data-ttu-id="97b2f-160">Adlı</span><span class="sxs-lookup"><span data-stu-id="97b2f-160">named</span></span>                                |
| <span data-ttu-id="97b2f-161">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="97b2f-161">Default Value</span></span>                        | <span data-ttu-id="97b2f-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-162">false</span></span>                                |
| <span data-ttu-id="97b2f-163">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b2f-164">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-164">false</span></span>                                |
| <span data-ttu-id="97b2f-165">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b2f-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="97b2f-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="97b2f-167">-WhatIf</span></span>

<span data-ttu-id="97b2f-168">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97b2f-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="97b2f-169">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="97b2f-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="97b2f-170">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-170">Required?</span></span>                            | <span data-ttu-id="97b2f-171">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-171">false</span></span>                                |
| <span data-ttu-id="97b2f-172">Konumu?</span><span class="sxs-lookup"><span data-stu-id="97b2f-172">Position?</span></span>                            | <span data-ttu-id="97b2f-173">Adlı</span><span class="sxs-lookup"><span data-stu-id="97b2f-173">named</span></span>                                |
| <span data-ttu-id="97b2f-174">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="97b2f-174">Default Value</span></span>                        | <span data-ttu-id="97b2f-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-175">false</span></span>                                |
| <span data-ttu-id="97b2f-176">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="97b2f-177">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-177">false</span></span>                                |
| <span data-ttu-id="97b2f-178">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="97b2f-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="97b2f-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="97b2f-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="97b2f-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="97b2f-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="97b2f-181">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="97b2f-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="97b2f-182">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="97b2f-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="97b2f-183">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="97b2f-183">INPUTS</span></span>

<span data-ttu-id="97b2f-184">Bu cmdlet herhangi bir giriş alır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="97b2f-185">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="97b2f-185">OUTPUTS</span></span>

<span data-ttu-id="97b2f-186">Bu cmdlet, hiçbir çıkış döndürür.</span><span class="sxs-lookup"><span data-stu-id="97b2f-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="97b2f-187">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="97b2f-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="97b2f-188">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="97b2f-188">EXAMPLE 1</span></span>

<span data-ttu-id="97b2f-189">Bu komut için Windows PowerShell Web uygulamasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="97b2f-190">Varsayılan değerleri kullanarak yüklediyseniz, Windows PowerShell Web uygulamasını kaldırmak için bu cmdlet'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97b2f-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="97b2f-191">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="97b2f-191">EXAMPLE 2</span></span>

<span data-ttu-id="97b2f-192">Bu komut için Windows PowerShell Web uygulamasını kaldırır ve uygulama ile ilişkili test sertifikasını siler.</span><span class="sxs-lookup"><span data-stu-id="97b2f-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="97b2f-193">Varsayılan değerleri kullanarak yüklediyseniz ve bir test sertifikası oluşturulan Windows PowerShell Web uygulamasını kaldırmak için bu cmdlet'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97b2f-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="97b2f-194">Örnek 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="97b2f-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="97b2f-195">Yükleme sırasında bir özel Web sitesi ve uygulama belirtildiğinde bu komut için Windows PowerShell Web uygulamasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97b2f-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="97b2f-196">Adlı Web sitesini komut kaldırır *Sitem* ve adlı uygulama *TestApplication* ve uygulama ile ilişkili test sertifikalar da silinip silinmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="97b2f-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="97b2f-197">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="97b2f-197">Related topics</span></span>

- [<span data-ttu-id="97b2f-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b2f-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="97b2f-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b2f-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="97b2f-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="97b2f-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="97b2f-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b2f-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="97b2f-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="97b2f-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)