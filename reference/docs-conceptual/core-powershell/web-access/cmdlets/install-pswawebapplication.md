---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: "pswawebapplication yükleyin"
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="cbd70-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="cbd70-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="cbd70-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="cbd70-104">SYNOPSIS</span></span>

<span data-ttu-id="cbd70-105">Windows PowerShell® Web Access web uygulaması IIS'de yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cbd70-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="cbd70-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="cbd70-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="cbd70-107">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="cbd70-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="cbd70-108">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="cbd70-108">DESCRIPTION</span></span>

<span data-ttu-id="cbd70-109">**Install-PswaWebApplication** cmdlet'i Windows PowerShell Web erişimi web uygulaması yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cbd70-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="cbd70-110">Bu cmdlet web uygulamasını yükler, bir web sitesi ile ilişkilendirir ve isteğe bağlı olarak bir SSL sertifikası kullanarak test oluşturur **useTestCertificate** parametresi.</span><span class="sxs-lookup"><span data-stu-id="cbd70-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="cbd70-111">Güvenlik nedeniyle web yöneticileri üretim ortamları için bir test sertifikası kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="cbd70-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="cbd70-112">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="cbd70-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="cbd70-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="cbd70-113">-UseTestCertificate</span></span>

<span data-ttu-id="cbd70-114">Bir test sertifikası oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd70-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="cbd70-115">Bu parametre, bu cmdlet bir test sertifikası oluşturur ve HTTPS isteklerinde sertifikayı kullanmak üzere Windows PowerShell Web erişimi web uygulaması yapılandırır true olarak ayarlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="cbd70-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="cbd70-116">Bu parametre false olarak ayarlanırsa, hiçbir sertifika veya bağlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cbd70-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="cbd70-117">Başka bir sertifika Windows PowerShell Web erişimi için kullanılıyorsa, bu değeri false olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cbd70-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="cbd70-118">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="cbd70-118">Aliases</span></span>                              | <span data-ttu-id="cbd70-119">yok</span><span class="sxs-lookup"><span data-stu-id="cbd70-119">none</span></span>                                 |
| <span data-ttu-id="cbd70-120">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-120">Required?</span></span>                            | <span data-ttu-id="cbd70-121">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-121">false</span></span>                                |
| <span data-ttu-id="cbd70-122">Konumu?</span><span class="sxs-lookup"><span data-stu-id="cbd70-122">Position?</span></span>                            | <span data-ttu-id="cbd70-123">Adlı</span><span class="sxs-lookup"><span data-stu-id="cbd70-123">named</span></span>                                |
| <span data-ttu-id="cbd70-124">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="cbd70-124">Default Value</span></span>                        | <span data-ttu-id="cbd70-125">TRUE</span><span class="sxs-lookup"><span data-stu-id="cbd70-125">true</span></span>                                 |
| <span data-ttu-id="cbd70-126">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cbd70-127">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-127">false</span></span>                                |
| <span data-ttu-id="cbd70-128">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cbd70-129">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="cbd70-130">-WebApplicationName&lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="cbd70-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="cbd70-131">Web uygulamanız için ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd70-131">Specifies the name for your web application.</span></span> <span data-ttu-id="cbd70-132">Bu Windows PowerShell Web erişim URL'si son parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cbd70-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="cbd70-133">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="cbd70-133">Aliases</span></span>                              | <span data-ttu-id="cbd70-134">yok</span><span class="sxs-lookup"><span data-stu-id="cbd70-134">none</span></span>                                 |
| <span data-ttu-id="cbd70-135">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-135">Required?</span></span>                            | <span data-ttu-id="cbd70-136">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-136">false</span></span>                                |
| <span data-ttu-id="cbd70-137">Konumu?</span><span class="sxs-lookup"><span data-stu-id="cbd70-137">Position?</span></span>                            | <span data-ttu-id="cbd70-138">1</span><span class="sxs-lookup"><span data-stu-id="cbd70-138">1</span></span>                                    |
| <span data-ttu-id="cbd70-139">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="cbd70-139">Default Value</span></span>                        | <span data-ttu-id="cbd70-140">pswa</span><span class="sxs-lookup"><span data-stu-id="cbd70-140">pswa</span></span>                                 |
| <span data-ttu-id="cbd70-141">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cbd70-142">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-142">false</span></span>                                |
| <span data-ttu-id="cbd70-143">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cbd70-144">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="cbd70-145">-WebSiteName&lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="cbd70-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="cbd70-146">Bu Windows PowerShell Web erişimi web uygulamasını yüklemek için Web sunucusu (IIS) Web sitesi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd70-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="cbd70-147">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="cbd70-147">Aliases</span></span>                              | <span data-ttu-id="cbd70-148">yok</span><span class="sxs-lookup"><span data-stu-id="cbd70-148">none</span></span>                                 |
| <span data-ttu-id="cbd70-149">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-149">Required?</span></span>                            | <span data-ttu-id="cbd70-150">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-150">false</span></span>                                |
| <span data-ttu-id="cbd70-151">Konumu?</span><span class="sxs-lookup"><span data-stu-id="cbd70-151">Position?</span></span>                            | <span data-ttu-id="cbd70-152">Adlı</span><span class="sxs-lookup"><span data-stu-id="cbd70-152">named</span></span>                                |
| <span data-ttu-id="cbd70-153">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="cbd70-153">Default Value</span></span>                        | <span data-ttu-id="cbd70-154">Varsayılan Web sitesi</span><span class="sxs-lookup"><span data-stu-id="cbd70-154">Default Web Site</span></span>                     |
| <span data-ttu-id="cbd70-155">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cbd70-156">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-156">false</span></span>                                |
| <span data-ttu-id="cbd70-157">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cbd70-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="cbd70-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cbd70-159">-Confirm</span></span>

<span data-ttu-id="cbd70-160">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="cbd70-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="cbd70-161">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-161">Required?</span></span>                            | <span data-ttu-id="cbd70-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-162">false</span></span>                                |
| <span data-ttu-id="cbd70-163">Konumu?</span><span class="sxs-lookup"><span data-stu-id="cbd70-163">Position?</span></span>                            | <span data-ttu-id="cbd70-164">Adlı</span><span class="sxs-lookup"><span data-stu-id="cbd70-164">named</span></span>                                |
| <span data-ttu-id="cbd70-165">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="cbd70-165">Default Value</span></span>                        | <span data-ttu-id="cbd70-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-166">false</span></span>                                |
| <span data-ttu-id="cbd70-167">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cbd70-168">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-168">false</span></span>                                |
| <span data-ttu-id="cbd70-169">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cbd70-170">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="cbd70-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cbd70-171">-WhatIf</span></span>

<span data-ttu-id="cbd70-172">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbd70-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cbd70-173">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="cbd70-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="cbd70-174">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-174">Required?</span></span>                            | <span data-ttu-id="cbd70-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-175">false</span></span>                                |
| <span data-ttu-id="cbd70-176">Konumu?</span><span class="sxs-lookup"><span data-stu-id="cbd70-176">Position?</span></span>                            | <span data-ttu-id="cbd70-177">Adlı</span><span class="sxs-lookup"><span data-stu-id="cbd70-177">named</span></span>                                |
| <span data-ttu-id="cbd70-178">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="cbd70-178">Default Value</span></span>                        | <span data-ttu-id="cbd70-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-179">false</span></span>                                |
| <span data-ttu-id="cbd70-180">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="cbd70-181">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-181">false</span></span>                                |
| <span data-ttu-id="cbd70-182">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="cbd70-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="cbd70-183">yanlış</span><span class="sxs-lookup"><span data-stu-id="cbd70-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="cbd70-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="cbd70-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="cbd70-185">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="cbd70-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="cbd70-186">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cbd70-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="cbd70-187">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="cbd70-187">INPUTS</span></span>

<span data-ttu-id="cbd70-188">Bu cmdlet herhangi bir giriş alır.</span><span class="sxs-lookup"><span data-stu-id="cbd70-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="cbd70-189">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="cbd70-189">OUTPUTS</span></span>

<span data-ttu-id="cbd70-190">Bu cmdlet herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="cbd70-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="cbd70-191">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="cbd70-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="cbd70-192">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="cbd70-192">EXAMPLE 1</span></span>

<span data-ttu-id="cbd70-193">Bu örnek için varsayılan değerleri kullanarak PSWA web uygulamasına yükler **WebApplicationName** (*pswa*) ve **WebSiteName** (*varsayılan Web sitesi* ) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="cbd70-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="cbd70-194">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="cbd70-194">EXAMPLE 2</span></span>

<span data-ttu-id="cbd70-195">Bu örnek, bir test sertifikası ve varsayılan değerleri kullanarak PSWA web uygulamasını yükler. **WebApplicationName** ve **WebSiteName** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="cbd70-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="cbd70-196">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="cbd70-196">Related topics</span></span>

- [<span data-ttu-id="cbd70-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cbd70-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="cbd70-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cbd70-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="cbd70-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cbd70-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="cbd70-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="cbd70-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
