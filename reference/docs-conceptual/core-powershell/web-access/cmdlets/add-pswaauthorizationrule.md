---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: pswaauthorizationrule Ekle
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 71954fc115daee4c05662d11baa2bc6a0a417896
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="15579-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="15579-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="15579-104">ÖZET</span><span class="sxs-lookup"><span data-stu-id="15579-104">SYNOPSIS</span></span>

<span data-ttu-id="15579-105">Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.</span><span class="sxs-lookup"><span data-stu-id="15579-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="15579-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15579-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="15579-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="15579-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="15579-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="15579-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="15579-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="15579-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="15579-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="15579-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="15579-111">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="15579-111">DESCRIPTION</span></span>

<span data-ttu-id="15579-112">**Add-PswaAuthorizationRule** cmdlet, Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.</span><span class="sxs-lookup"><span data-stu-id="15579-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="15579-113">Kullanıcılar, bilgisayarlar ve bu kural için Windows PowerShell uç noktaları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15579-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="15579-114">Kullanıcılar ve bilgisayarlar bireysel kullanıcı hesapları ve bilgisayar adları ya da grupları belirterek belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15579-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="15579-115">Bir Active Directory etki alanına katılmış bir bilgisayar için cmdlet kuralı oluşturmak için bilgisayar güvenlik tanımlayıcısı (SID) kullanır.</span><span class="sxs-lookup"><span data-stu-id="15579-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="15579-116">Bu sayede kısa bir ad, bir tam etki alanı adı (FQDN) veya bir IP adresi için kullanılacak **bilgisayar adı** oturum açma sayfasında alan.</span><span class="sxs-lookup"><span data-stu-id="15579-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="15579-117">Bir Active Directory etki alanına katılmamış bir bilgisayar için cmdlet yönetici tarafından sağlanan bilgisayar adını kullanarak kural oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15579-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="15579-118">Son kullanıcı başarılı bir şekilde bu makineye bağlanmak için kuralda göründüğü gibi bilgisayar adı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15579-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="15579-119">Ağ üzerinde aynı ada sahip birden çok bilgisayar varsa, kısa adı birden fazla bilgisayara çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15579-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="15579-120">Bu bağlantı kurarken belirsizlik için yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="15579-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="15579-121">Adlı çalışma grubu bilgisayarı için bir kuralı varsa, örneğin, "*Sunucu1*" adlı yeni bir bilgisayar *server1.contoso.com* katılmışsa ağa yetkilendirme kurallarını kullanarak doğrulama başarılı olur ve Windows PowerShell Web erişimi çalışır adlı bilgisayara bir bağlantı kurmak "*Sunucu1*".</span><span class="sxs-lookup"><span data-stu-id="15579-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="15579-122">Bu belirtilen çalışma grubu bilgisayarı ile bağlantı kurulur kesin değildir; çalışma grubu veya adlı etki alanı bilgisayarda denemesi yapılamadı "*Sunucu1*".</span><span class="sxs-lookup"><span data-stu-id="15579-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="15579-123">Belirsizliği azaltmak için hedef bilgisayar için mümkün olduğunca bir yetkilendirme kuralı oluşturmak FQDN kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="15579-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="15579-124">Birincil oturum açma kimlik bilgileri Windows PowerShell Web erişimi kullanıcılarının olmayan alternatif kimlik bilgileri yetkilendirme kuralları değerlendirin (ikinci kimlik bilgileri kümesi bulunan **isteğe bağlı bağlantı ayarlarını** bölümü oturum açma sayfası).</span><span class="sxs-lookup"><span data-stu-id="15579-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="15579-125">Bu örneği için örnek 6'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="15579-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="15579-126">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15579-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="15579-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="15579-128">Active Directory etki alanı Hizmetleri (AD DS) veya yerel gruplar için bu kural erişimine izin verdiği bir bilgisayar grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-129">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-129">Aliases</span></span>                              | <span data-ttu-id="15579-130">yok</span><span class="sxs-lookup"><span data-stu-id="15579-130">none</span></span>                                 |
| <span data-ttu-id="15579-131">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-131">Required?</span></span>                            | <span data-ttu-id="15579-132">TRUE</span><span class="sxs-lookup"><span data-stu-id="15579-132">true</span></span>                                 |
| <span data-ttu-id="15579-133">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-133">Position?</span></span>                            | <span data-ttu-id="15579-134">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-134">named</span></span>                                |
| <span data-ttu-id="15579-135">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-135">Default Value</span></span>                        | <span data-ttu-id="15579-136">yok</span><span class="sxs-lookup"><span data-stu-id="15579-136">none</span></span>                                 |
| <span data-ttu-id="15579-137">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-138">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15579-139">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-140">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="15579-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="15579-142">Bu kural erişim verdiği bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-143">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-143">Aliases</span></span>                              | <span data-ttu-id="15579-144">yok</span><span class="sxs-lookup"><span data-stu-id="15579-144">none</span></span>                                 |
| <span data-ttu-id="15579-145">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-145">Required?</span></span>                            | <span data-ttu-id="15579-146">TRUE</span><span class="sxs-lookup"><span data-stu-id="15579-146">true</span></span>                                 |
| <span data-ttu-id="15579-147">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-147">Position?</span></span>                            | <span data-ttu-id="15579-148">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-148">named</span></span>                                |
| <span data-ttu-id="15579-149">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-149">Default Value</span></span>                        | <span data-ttu-id="15579-150">yok</span><span class="sxs-lookup"><span data-stu-id="15579-150">none</span></span>                                 |
| <span data-ttu-id="15579-151">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-152">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15579-153">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-154">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="15579-155">-ConfigurationName&lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="15579-156">Windows PowerShell oturumu configuration olarak da bilinen bu kural erişim verdiği çalışma alanının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-157">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-157">Aliases</span></span>                              | <span data-ttu-id="15579-158">yok</span><span class="sxs-lookup"><span data-stu-id="15579-158">none</span></span>                                 |
| <span data-ttu-id="15579-159">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-159">Required?</span></span>                            | <span data-ttu-id="15579-160">TRUE</span><span class="sxs-lookup"><span data-stu-id="15579-160">true</span></span>                                 |
| <span data-ttu-id="15579-161">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-161">Position?</span></span>                            | <span data-ttu-id="15579-162">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-162">named</span></span>                                |
| <span data-ttu-id="15579-163">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-163">Default Value</span></span>                        | <span data-ttu-id="15579-164">yok</span><span class="sxs-lookup"><span data-stu-id="15579-164">none</span></span>                                 |
| <span data-ttu-id="15579-165">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-166">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15579-167">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-168">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="15579-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="15579-170">Belirten bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kurallarını değiştirmek için kullanmak istediğiniz bir kullanıcı hesabı için nesnesi.</span><span class="sxs-lookup"><span data-stu-id="15579-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="15579-171">Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır.</span><span class="sxs-lookup"><span data-stu-id="15579-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="15579-172">Alınacak bir **PSCredential** uzaktan yetkilendirme kuralları eklemek için çalıştırmak için gerekli olan nesne, [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="15579-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-173">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-173">Aliases</span></span>                              | <span data-ttu-id="15579-174">yok</span><span class="sxs-lookup"><span data-stu-id="15579-174">none</span></span>                                 |
| <span data-ttu-id="15579-175">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-175">Required?</span></span>                            | <span data-ttu-id="15579-176">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-176">false</span></span>                                |
| <span data-ttu-id="15579-177">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-177">Position?</span></span>                            | <span data-ttu-id="15579-178">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-178">named</span></span>                                |
| <span data-ttu-id="15579-179">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-179">Default Value</span></span>                        | <span data-ttu-id="15579-180">yok</span><span class="sxs-lookup"><span data-stu-id="15579-180">none</span></span>                                 |
| <span data-ttu-id="15579-181">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-182">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-182">false</span></span>                                |
| <span data-ttu-id="15579-183">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-184">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="15579-185">-Force</span><span class="sxs-lookup"><span data-stu-id="15579-185">-Force</span></span>

<span data-ttu-id="15579-186">Komutu için kullanıcı onayı istemeden çalışmaya zorlar. \\</span><span class="sxs-lookup"><span data-stu-id="15579-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="15579-187">Ayrıca, bir basit veya kısa bir bilgisayar adı (örneğin, bir etki alanı adı değil veya tam değil adı) girdiğinizde de onaylamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="15579-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="15579-188">Böylece yalnızca bilgisayar bir çalışma grubunda ise bir bilgisayar eklemek için basit bir ad kullanabilirsiniz onay güvenlik nedenleriyle istendi.</span><span class="sxs-lookup"><span data-stu-id="15579-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-189">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-189">Aliases</span></span>                              | <span data-ttu-id="15579-190">yok</span><span class="sxs-lookup"><span data-stu-id="15579-190">none</span></span>                                 |
| <span data-ttu-id="15579-191">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-191">Required?</span></span>                            | <span data-ttu-id="15579-192">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-192">false</span></span>                                |
| <span data-ttu-id="15579-193">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-193">Position?</span></span>                            | <span data-ttu-id="15579-194">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-194">named</span></span>                                |
| <span data-ttu-id="15579-195">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-195">Default Value</span></span>                        | <span data-ttu-id="15579-196">yok</span><span class="sxs-lookup"><span data-stu-id="15579-196">none</span></span>                                 |
| <span data-ttu-id="15579-197">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-198">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-198">false</span></span>                                |
| <span data-ttu-id="15579-199">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-200">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="15579-201">-RuleName&lt;dize&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="15579-202">Bu kural için kolay adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-203">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-203">Aliases</span></span>                              | <span data-ttu-id="15579-204">yok</span><span class="sxs-lookup"><span data-stu-id="15579-204">none</span></span>                                 |
| <span data-ttu-id="15579-205">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-205">Required?</span></span>                            | <span data-ttu-id="15579-206">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-206">false</span></span>                                |
| <span data-ttu-id="15579-207">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-207">Position?</span></span>                            | <span data-ttu-id="15579-208">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-208">named</span></span>                                |
| <span data-ttu-id="15579-209">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-209">Default Value</span></span>                        | <span data-ttu-id="15579-210">yok</span><span class="sxs-lookup"><span data-stu-id="15579-210">none</span></span>                                 |
| <span data-ttu-id="15579-211">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-212">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15579-213">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-214">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="15579-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="15579-216">AD DS veya bu kural erişim verdiği yerel gruplar bir veya daha fazla kullanıcı grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-217">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-217">Aliases</span></span>                              | <span data-ttu-id="15579-218">yok</span><span class="sxs-lookup"><span data-stu-id="15579-218">none</span></span>                                 |
| <span data-ttu-id="15579-219">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-219">Required?</span></span>                            | <span data-ttu-id="15579-220">TRUE</span><span class="sxs-lookup"><span data-stu-id="15579-220">true</span></span>                                 |
| <span data-ttu-id="15579-221">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-221">Position?</span></span>                            | <span data-ttu-id="15579-222">Adlı</span><span class="sxs-lookup"><span data-stu-id="15579-222">named</span></span>                                |
| <span data-ttu-id="15579-223">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-223">Default Value</span></span>                        | <span data-ttu-id="15579-224">yok</span><span class="sxs-lookup"><span data-stu-id="15579-224">none</span></span>                                 |
| <span data-ttu-id="15579-225">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-226">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="15579-227">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-228">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="15579-229">-UserName&lt;dize\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="15579-230">Bu kural erişim verdiği bir veya daha fazla kullanıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="15579-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="15579-231">Kullanıcı adı, ağ geçidi bilgisayarında veya AD DS'de bir kullanıcı bir yerel kullanıcı hesabı olabilir.</span><span class="sxs-lookup"><span data-stu-id="15579-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="15579-232">Biçim `domain\user` veya `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="15579-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="15579-233">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="15579-233">Aliases</span></span>                              | <span data-ttu-id="15579-234">yok</span><span class="sxs-lookup"><span data-stu-id="15579-234">none</span></span>                                 |
| <span data-ttu-id="15579-235">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="15579-235">Required?</span></span>                            | <span data-ttu-id="15579-236">TRUE</span><span class="sxs-lookup"><span data-stu-id="15579-236">true</span></span>                                 |
| <span data-ttu-id="15579-237">Konumu?</span><span class="sxs-lookup"><span data-stu-id="15579-237">Position?</span></span>                            | <span data-ttu-id="15579-238">1</span><span class="sxs-lookup"><span data-stu-id="15579-238">1</span></span>                                    |
| <span data-ttu-id="15579-239">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="15579-239">Default Value</span></span>                        | <span data-ttu-id="15579-240">yok</span><span class="sxs-lookup"><span data-stu-id="15579-240">none</span></span>                                 |
| <span data-ttu-id="15579-241">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="15579-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="15579-242">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="15579-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="15579-243">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="15579-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="15579-244">yanlış</span><span class="sxs-lookup"><span data-stu-id="15579-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="15579-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="15579-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="15579-246">Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="15579-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="15579-247">Daha fazla bilgi için bkz: [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="15579-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="15579-248">GİRİŞLERİ</span><span class="sxs-lookup"><span data-stu-id="15579-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="15579-249">Dize</span><span class="sxs-lookup"><span data-stu-id="15579-249">String</span></span>

<span data-ttu-id="15579-250">Bu cmdlet bir dize veya dize dizisi giriş olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="15579-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="15579-251">Dize\[\]</span><span class="sxs-lookup"><span data-stu-id="15579-251">String\[\]</span></span>

<span data-ttu-id="15579-252">Bu cmdlet bir dize veya dize dizisi giriş olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="15579-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="15579-253">Çıkışlar</span><span class="sxs-lookup"><span data-stu-id="15579-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="15579-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="15579-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="15579-255">Bu cmdlet döndürür ve bir yetkilendirme kuralı nesne.</span><span class="sxs-lookup"><span data-stu-id="15579-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="15579-256">ÖRNEKLER</span><span class="sxs-lookup"><span data-stu-id="15579-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="15579-257">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="15579-257">EXAMPLE 1</span></span>

<span data-ttu-id="15579-258">Bu örnekte oturum yapılandırma erişim verir *PSWAEndpoint*, bir çalışma alanı, kısıtlanmış *SUN2* kullanıcılar için *SMAdmins* grup. \\</span><span class="sxs-lookup"><span data-stu-id="15579-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="15579-259">**Not**: bilgisayar adı bir tam etki alanı adı (FQDN) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15579-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="15579-260">Yöneticiler, sınırlı bir oturum yapılandırması veya sınırlı bir cmdlet'ler ve son kullanıcıların çalıştırabileceği görevleri aralığıdır çalışma tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="15579-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="15579-261">Sınırlı bir çalışma alanı tanımlanması, kullanıcıların izin verilen Windows PowerShell® çalışma alanında, böylece daha güvenli bir bağlantı sunulmamaktadır diğer bilgisayarlara erişmesini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="15579-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="15579-262">Oturum yapılandırmaları hakkında daha fazla bilgi için bkz: [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) veya [yükleme ve kullanım Windows PowerShell Web erişimi](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="15579-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="15579-263">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="15579-263">EXAMPLE 2</span></span>

<span data-ttu-id="15579-264">Bu örnek varsayılan Windows PowerShell oturum yapılandırması, erişim veren `Microsoft.PowerShell`, *SUN2* contoso adlı kullanıcılar kullanıcılar için\\Kullanıcı1, contoso\\user2 ve contoso\\KULLANICI3.</span><span class="sxs-lookup"><span data-stu-id="15579-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="15579-265">Bu cmdlet, üç kurallar (kişi başına 1) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15579-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="15579-266">ÖRNEK 3</span><span class="sxs-lookup"><span data-stu-id="15579-266">EXAMPLE 3</span></span>

<span data-ttu-id="15579-267">Bu örnekte, kullanıcı adı değerleri ardışık düzeni aracılığıyla giriş göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="15579-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="15579-268">ÖRNEK 4</span><span class="sxs-lookup"><span data-stu-id="15579-268">EXAMPLE 4</span></span>

<span data-ttu-id="15579-269">Bu örnekte gösterilmiştir tüm parametreleri özellik adı ardışık düzen değerlerinden ele nasıl.</span><span class="sxs-lookup"><span data-stu-id="15579-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="15579-270">ÖRNEK 5</span><span class="sxs-lookup"><span data-stu-id="15579-270">EXAMPLE 5</span></span>

<span data-ttu-id="15579-271">Bu örnek adlı yerel kullanıcı izin verme kuralı ekler *PswaServer\\ChrisLocal* adlı sunucuya erişimi *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="15579-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="15579-272">Bu örnekte, ağ geçidi bir çalışma grubunda ve hedef bilgisayar bir etki alanında olduğu yerde bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15579-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="15579-273">Yetkilendirme kural, ağ geçidinde yerel kullanıcılar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="15579-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="15579-274">Windows PowerShell Web erişimi oturum açma sayfasında, kimliğini başarıyla doğrulamak için kullanıcı kimlik bilgilerini ikinci bir set sağlamalısınız **isteğe bağlı bağlantı ayarlarını** alanı.</span><span class="sxs-lookup"><span data-stu-id="15579-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="15579-275">Ağ Geçidi sunucusu, hedef bilgisayardaki adlı bir sunucusu kullanıcının kimliğini doğrulamak için ek kimlik bilgileri kümesini kullanır. *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="15579-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="15579-276">ÖRNEK 6</span><span class="sxs-lookup"><span data-stu-id="15579-276">EXAMPLE 6</span></span>

<span data-ttu-id="15579-277">Bu örnekte tüm kullanıcıların tüm bilgisayarlarda tüm uç noktaları erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="15579-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="15579-278">Bu temelde yetkilendirme kuralları devre dışı bırakır. \\</span><span class="sxs-lookup"><span data-stu-id="15579-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="15579-279">**Not**: kullanımı `*` joker karakter güvenlik açısından duyarlı dağıtımları için önerilmez ve yalnızca test ortamları için kabul veya güvenlik nerede gevşetilebilir dağıtımlarında kullanılan.</span><span class="sxs-lookup"><span data-stu-id="15579-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="15579-280">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="15579-280">See Also</span></span>

- <span data-ttu-id="15579-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="15579-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="15579-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="15579-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="15579-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="15579-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="15579-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="15579-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="15579-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="15579-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="15579-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="15579-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="15579-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="15579-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
