---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268308"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="38e51-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="38e51-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="38e51-104">ÖZETİ</span><span class="sxs-lookup"><span data-stu-id="38e51-104">SYNOPSIS</span></span>

<span data-ttu-id="38e51-105">Windows PowerShell Web erişimi web uygulamasını IIS yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="38e51-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="38e51-106">SÖZ DİZİMİ</span><span class="sxs-lookup"><span data-stu-id="38e51-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="38e51-107">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="38e51-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="38e51-108">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="38e51-108">DESCRIPTION</span></span>

<span data-ttu-id="38e51-109">**Install-PswaWebApplication** cmdlet'i, Windows PowerShell Web erişimi web uygulaması yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="38e51-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="38e51-110">Web uygulaması yükler, bir web sitesi ile ilişkilendirir ve isteğe bağlı olarak bir test SSL sertifikası kullanarak oluşturur. Bu cmdlet **useTestCertificate** parametresi.</span><span class="sxs-lookup"><span data-stu-id="38e51-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="38e51-111">İçin güvenlik nedeniyle web yöneticilerinin üretim ortamları için bir test sertifikası kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="38e51-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="38e51-112">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="38e51-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="38e51-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="38e51-113">-UseTestCertificate</span></span>

<span data-ttu-id="38e51-114">Bir test sertifikası oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38e51-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="38e51-115">Bu parametre, bu cmdlet bir test sertifikası oluşturur ve HTTPS isteklerinde sertifikayı kullanmak için Windows PowerShell Web erişimi web uygulamasını yapılandırır, true olarak ayarlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="38e51-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="38e51-116">Bu parametre false olarak ayarlarsanız, hiçbir sertifika veya bağlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="38e51-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="38e51-117">Windows PowerShell Web erişimi için başka bir sertifika kullandıysanız, bu değeri false olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38e51-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="38e51-118">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="38e51-118">Aliases</span></span>                              | <span data-ttu-id="38e51-119">yok</span><span class="sxs-lookup"><span data-stu-id="38e51-119">none</span></span>                                 |
| <span data-ttu-id="38e51-120">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-120">Required?</span></span>                            | <span data-ttu-id="38e51-121">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-121">false</span></span>                                |
| <span data-ttu-id="38e51-122">Konumu?</span><span class="sxs-lookup"><span data-stu-id="38e51-122">Position?</span></span>                            | <span data-ttu-id="38e51-123">adlı</span><span class="sxs-lookup"><span data-stu-id="38e51-123">named</span></span>                                |
| <span data-ttu-id="38e51-124">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="38e51-124">Default Value</span></span>                        | <span data-ttu-id="38e51-125">TRUE</span><span class="sxs-lookup"><span data-stu-id="38e51-125">true</span></span>                                 |
| <span data-ttu-id="38e51-126">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="38e51-127">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-127">false</span></span>                                |
| <span data-ttu-id="38e51-128">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="38e51-129">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="38e51-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="38e51-130">-WebApplicationName</span></span>

<span data-ttu-id="38e51-131">Web uygulamanız için bir ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="38e51-131">Specifies the name for your web application.</span></span> <span data-ttu-id="38e51-132">Bu Windows PowerShell Web erişimi URL'si son parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38e51-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="38e51-133">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="38e51-133">Aliases</span></span>                              | <span data-ttu-id="38e51-134">yok</span><span class="sxs-lookup"><span data-stu-id="38e51-134">none</span></span>                                 |
| <span data-ttu-id="38e51-135">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-135">Required?</span></span>                            | <span data-ttu-id="38e51-136">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-136">false</span></span>                                |
| <span data-ttu-id="38e51-137">Konumu?</span><span class="sxs-lookup"><span data-stu-id="38e51-137">Position?</span></span>                            | <span data-ttu-id="38e51-138">1</span><span class="sxs-lookup"><span data-stu-id="38e51-138">1</span></span>                                    |
| <span data-ttu-id="38e51-139">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="38e51-139">Default Value</span></span>                        | <span data-ttu-id="38e51-140">pswa</span><span class="sxs-lookup"><span data-stu-id="38e51-140">pswa</span></span>                                 |
| <span data-ttu-id="38e51-141">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="38e51-142">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-142">false</span></span>                                |
| <span data-ttu-id="38e51-143">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="38e51-144">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="38e51-145">-WebSiteName</span><span class="sxs-lookup"><span data-stu-id="38e51-145">-WebSiteName</span></span>

<span data-ttu-id="38e51-146">Bu Windows PowerShell Web erişimi web uygulamasını yüklemek için Web sunucusu (IIS) Web sitesinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38e51-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="38e51-147">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="38e51-147">Aliases</span></span>                              | <span data-ttu-id="38e51-148">yok</span><span class="sxs-lookup"><span data-stu-id="38e51-148">none</span></span>                                 |
| <span data-ttu-id="38e51-149">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-149">Required?</span></span>                            | <span data-ttu-id="38e51-150">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-150">false</span></span>                                |
| <span data-ttu-id="38e51-151">Konumu?</span><span class="sxs-lookup"><span data-stu-id="38e51-151">Position?</span></span>                            | <span data-ttu-id="38e51-152">adlı</span><span class="sxs-lookup"><span data-stu-id="38e51-152">named</span></span>                                |
| <span data-ttu-id="38e51-153">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="38e51-153">Default Value</span></span>                        | <span data-ttu-id="38e51-154">Varsayılan Web sitesi</span><span class="sxs-lookup"><span data-stu-id="38e51-154">Default Web Site</span></span>                     |
| <span data-ttu-id="38e51-155">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="38e51-156">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-156">false</span></span>                                |
| <span data-ttu-id="38e51-157">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="38e51-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="38e51-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="38e51-159">-Confirm</span></span>

<span data-ttu-id="38e51-160">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="38e51-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="38e51-161">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-161">Required?</span></span>                            | <span data-ttu-id="38e51-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-162">false</span></span>                                |
| <span data-ttu-id="38e51-163">Konumu?</span><span class="sxs-lookup"><span data-stu-id="38e51-163">Position?</span></span>                            | <span data-ttu-id="38e51-164">adlı</span><span class="sxs-lookup"><span data-stu-id="38e51-164">named</span></span>                                |
| <span data-ttu-id="38e51-165">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="38e51-165">Default Value</span></span>                        | <span data-ttu-id="38e51-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-166">false</span></span>                                |
| <span data-ttu-id="38e51-167">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="38e51-168">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-168">false</span></span>                                |
| <span data-ttu-id="38e51-169">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="38e51-170">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="38e51-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="38e51-171">-WhatIf</span></span>

<span data-ttu-id="38e51-172">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38e51-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="38e51-173">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="38e51-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="38e51-174">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-174">Required?</span></span>                            | <span data-ttu-id="38e51-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-175">false</span></span>                                |
| <span data-ttu-id="38e51-176">Konumu?</span><span class="sxs-lookup"><span data-stu-id="38e51-176">Position?</span></span>                            | <span data-ttu-id="38e51-177">adlı</span><span class="sxs-lookup"><span data-stu-id="38e51-177">named</span></span>                                |
| <span data-ttu-id="38e51-178">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="38e51-178">Default Value</span></span>                        | <span data-ttu-id="38e51-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-179">false</span></span>                                |
| <span data-ttu-id="38e51-180">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="38e51-181">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-181">false</span></span>                                |
| <span data-ttu-id="38e51-182">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="38e51-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="38e51-183">yanlış</span><span class="sxs-lookup"><span data-stu-id="38e51-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="38e51-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="38e51-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="38e51-185">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="38e51-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="38e51-186">Daha fazla bilgi için [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="38e51-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="38e51-187">GİRİŞ</span><span class="sxs-lookup"><span data-stu-id="38e51-187">INPUTS</span></span>

<span data-ttu-id="38e51-188">Bu cmdlet herhangi bir giriş alır.</span><span class="sxs-lookup"><span data-stu-id="38e51-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="38e51-189">ÇIKIŞLAR</span><span class="sxs-lookup"><span data-stu-id="38e51-189">OUTPUTS</span></span>

<span data-ttu-id="38e51-190">Bu cmdlet herhangi bir çıktı üretmez.</span><span class="sxs-lookup"><span data-stu-id="38e51-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="38e51-191">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="38e51-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="38e51-192">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="38e51-192">EXAMPLE 1</span></span>

<span data-ttu-id="38e51-193">Bu örnek için varsayılan değerleri kullanarak PSWA web uygulamasına yükler **WebApplicationName** (*pswa*) ve **WebSiteName** (*varsayılan Web sitesi* ) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="38e51-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="38e51-194">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="38e51-194">EXAMPLE 2</span></span>

<span data-ttu-id="38e51-195">Bu örnek, bir test sertifikası ve varsayılan değerleri kullanarak PSWA web uygulaması yükler. **WebApplicationName** ve **WebSiteName** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="38e51-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="38e51-196">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="38e51-196">Related topics</span></span>

- [<span data-ttu-id="38e51-197">Ekle-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="38e51-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="38e51-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="38e51-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="38e51-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="38e51-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="38e51-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="38e51-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)