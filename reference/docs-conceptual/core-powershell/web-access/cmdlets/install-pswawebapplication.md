---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: "pswawebapplication yükleyin"
ms.technology: powershell
ms.openlocfilehash: ce4d01fbe8a83924e7023d792c68c903a32e07d4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="1453e-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="1453e-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="1453e-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="1453e-104">SYNOPSIS</span></span>

<span data-ttu-id="1453e-105">Windows PowerShell® Web Access web uygulaması IIS'de yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1453e-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="1453e-106">SÖZDİZİMİ</span><span class="sxs-lookup"><span data-stu-id="1453e-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="1453e-107">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="1453e-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="1453e-108">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="1453e-108">DESCRIPTION</span></span>

<span data-ttu-id="1453e-109">**Install-PswaWebApplication** cmdlet'i Windows PowerShell Web erişimi web uygulaması yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1453e-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="1453e-110">Bu cmdlet web uygulamasını yükler, bir web sitesi ile ilişkilendirir ve isteğe bağlı olarak bir SSL sertifikası kullanarak test oluşturur **useTestCertificate** parametresi.</span><span class="sxs-lookup"><span data-stu-id="1453e-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="1453e-111">Güvenlik nedeniyle web yöneticileri üretim ortamları için bir test sertifikası kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="1453e-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="1453e-112">PARAMETRELERİ</span><span class="sxs-lookup"><span data-stu-id="1453e-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="1453e-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="1453e-113">-UseTestCertificate</span></span>

<span data-ttu-id="1453e-114">Bir test sertifikası oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1453e-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="1453e-115">Bu parametre, bu cmdlet bir test sertifikası oluşturur ve HTTPS isteklerinde sertifikayı kullanmak üzere Windows PowerShell Web erişimi web uygulaması yapılandırır true olarak ayarlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="1453e-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="1453e-116">Bu parametre false olarak ayarlanırsa, hiçbir sertifika veya bağlama oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1453e-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="1453e-117">Başka bir sertifika Windows PowerShell Web erişimi için kullanılıyorsa, bu değeri false olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1453e-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="1453e-118">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="1453e-118">Aliases</span></span>                              | <span data-ttu-id="1453e-119">yok</span><span class="sxs-lookup"><span data-stu-id="1453e-119">none</span></span>                                 |
| <span data-ttu-id="1453e-120">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-120">Required?</span></span>                            | <span data-ttu-id="1453e-121">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-121">false</span></span>                                |
| <span data-ttu-id="1453e-122">Konumu?</span><span class="sxs-lookup"><span data-stu-id="1453e-122">Position?</span></span>                            | <span data-ttu-id="1453e-123">Adlı</span><span class="sxs-lookup"><span data-stu-id="1453e-123">named</span></span>                                |
| <span data-ttu-id="1453e-124">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="1453e-124">Default Value</span></span>                        | <span data-ttu-id="1453e-125">TRUE</span><span class="sxs-lookup"><span data-stu-id="1453e-125">true</span></span>                                 |
| <span data-ttu-id="1453e-126">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1453e-127">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-127">false</span></span>                                |
| <span data-ttu-id="1453e-128">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1453e-129">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="1453e-130">-WebApplicationName&lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="1453e-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="1453e-131">Web uygulamanız için ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="1453e-131">Specifies the name for your web application.</span></span> <span data-ttu-id="1453e-132">Bu Windows PowerShell Web erişim URL'si son parçası olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1453e-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="1453e-133">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="1453e-133">Aliases</span></span>                              | <span data-ttu-id="1453e-134">yok</span><span class="sxs-lookup"><span data-stu-id="1453e-134">none</span></span>                                 |
| <span data-ttu-id="1453e-135">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-135">Required?</span></span>                            | <span data-ttu-id="1453e-136">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-136">false</span></span>                                |
| <span data-ttu-id="1453e-137">Konumu?</span><span class="sxs-lookup"><span data-stu-id="1453e-137">Position?</span></span>                            | <span data-ttu-id="1453e-138">1</span><span class="sxs-lookup"><span data-stu-id="1453e-138">1</span></span>                                    |
| <span data-ttu-id="1453e-139">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="1453e-139">Default Value</span></span>                        | <span data-ttu-id="1453e-140">pswa</span><span class="sxs-lookup"><span data-stu-id="1453e-140">pswa</span></span>                                 |
| <span data-ttu-id="1453e-141">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1453e-142">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-142">false</span></span>                                |
| <span data-ttu-id="1453e-143">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1453e-144">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="1453e-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="1453e-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="1453e-146">Bu Windows PowerShell Web erişimi web uygulamasını yüklemek için Web sunucusu (IIS) Web sitesi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1453e-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="1453e-147">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="1453e-147">Aliases</span></span>                              | <span data-ttu-id="1453e-148">yok</span><span class="sxs-lookup"><span data-stu-id="1453e-148">none</span></span>                                 |
| <span data-ttu-id="1453e-149">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-149">Required?</span></span>                            | <span data-ttu-id="1453e-150">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-150">false</span></span>                                |
| <span data-ttu-id="1453e-151">Konumu?</span><span class="sxs-lookup"><span data-stu-id="1453e-151">Position?</span></span>                            | <span data-ttu-id="1453e-152">Adlı</span><span class="sxs-lookup"><span data-stu-id="1453e-152">named</span></span>                                |
| <span data-ttu-id="1453e-153">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="1453e-153">Default Value</span></span>                        | <span data-ttu-id="1453e-154">Varsayılan Web sitesi</span><span class="sxs-lookup"><span data-stu-id="1453e-154">Default Web Site</span></span>                     |
| <span data-ttu-id="1453e-155">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1453e-156">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-156">false</span></span>                                |
| <span data-ttu-id="1453e-157">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1453e-158">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="1453e-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1453e-159">-Confirm</span></span>

<span data-ttu-id="1453e-160">Cmdlet'i çalıştırmadan önce sizden onay ister.</span><span class="sxs-lookup"><span data-stu-id="1453e-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="1453e-161">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-161">Required?</span></span>                            | <span data-ttu-id="1453e-162">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-162">false</span></span>                                |
| <span data-ttu-id="1453e-163">Konumu?</span><span class="sxs-lookup"><span data-stu-id="1453e-163">Position?</span></span>                            | <span data-ttu-id="1453e-164">Adlı</span><span class="sxs-lookup"><span data-stu-id="1453e-164">named</span></span>                                |
| <span data-ttu-id="1453e-165">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="1453e-165">Default Value</span></span>                        | <span data-ttu-id="1453e-166">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-166">false</span></span>                                |
| <span data-ttu-id="1453e-167">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1453e-168">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-168">false</span></span>                                |
| <span data-ttu-id="1453e-169">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1453e-170">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="1453e-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1453e-171">-WhatIf</span></span>

<span data-ttu-id="1453e-172">Cmdlet çalıştırılıyorsa ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1453e-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1453e-173">Cmdlet çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="1453e-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="1453e-174">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-174">Required?</span></span>                            | <span data-ttu-id="1453e-175">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-175">false</span></span>                                |
| <span data-ttu-id="1453e-176">Konumu?</span><span class="sxs-lookup"><span data-stu-id="1453e-176">Position?</span></span>                            | <span data-ttu-id="1453e-177">Adlı</span><span class="sxs-lookup"><span data-stu-id="1453e-177">named</span></span>                                |
| <span data-ttu-id="1453e-178">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="1453e-178">Default Value</span></span>                        | <span data-ttu-id="1453e-179">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-179">false</span></span>                                |
| <span data-ttu-id="1453e-180">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="1453e-181">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-181">false</span></span>                                |
| <span data-ttu-id="1453e-182">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="1453e-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="1453e-183">yanlış</span><span class="sxs-lookup"><span data-stu-id="1453e-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="1453e-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1453e-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="1453e-185">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="1453e-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="1453e-186">Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1453e-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="1453e-187">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="1453e-187">INPUTS</span></span>

<span data-ttu-id="1453e-188">Bu cmdlet herhangi bir giriş alır.</span><span class="sxs-lookup"><span data-stu-id="1453e-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="1453e-189">ÇIKIŞLARI</span><span class="sxs-lookup"><span data-stu-id="1453e-189">OUTPUTS</span></span>

<span data-ttu-id="1453e-190">Bu cmdlet herhangi bir çıktı oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="1453e-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="1453e-191">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="1453e-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="1453e-192">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="1453e-192">EXAMPLE 1</span></span>

<span data-ttu-id="1453e-193">Bu örnek için varsayılan değerleri kullanarak PSWA web uygulamasına yükler **WebApplicationName** (*pswa*) ve **WebSiteName** (*varsayılan Web sitesi* ) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="1453e-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="1453e-194">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="1453e-194">EXAMPLE 2</span></span>

<span data-ttu-id="1453e-195">Bu örnek, bir test sertifikası ve varsayılan değerleri kullanarak PSWA web uygulamasını yükler. **WebApplicationName** ve **WebSiteName** parametreleri.</span><span class="sxs-lookup"><span data-stu-id="1453e-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="1453e-196">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="1453e-196">Related topics</span></span>

- [<span data-ttu-id="1453e-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1453e-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="1453e-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1453e-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="1453e-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1453e-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="1453e-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="1453e-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
