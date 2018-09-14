---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: fe2b71dcfa870ba3f92484ae3fd3c45b3107a1bc
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523088"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="96418-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="96418-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="96418-104">ÖZETİ</span><span class="sxs-lookup"><span data-stu-id="96418-104">SYNOPSIS</span></span>

<span data-ttu-id="96418-105">Yeni bir yetkilendirme kuralı için Windows PowerShell Web Erişimi yetkilendirme kuralı kümesi ekler.</span><span class="sxs-lookup"><span data-stu-id="96418-105">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="96418-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96418-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="96418-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="96418-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="96418-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="96418-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="96418-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="96418-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="96418-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="96418-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="96418-111">AÇIKLAMA</span><span class="sxs-lookup"><span data-stu-id="96418-111">DESCRIPTION</span></span>

<span data-ttu-id="96418-112">**Add-PswaAuthorizationRule** cmdlet'i Windows PowerShell(r) Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.</span><span class="sxs-lookup"><span data-stu-id="96418-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell(r) Web Access authorization rule set.</span></span>

<span data-ttu-id="96418-113">Kullanıcılar, bilgisayarlar ve bu kural için Windows PowerShell uç noktası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96418-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="96418-114">Kullanıcılar ve bilgisayarlar bireysel kullanıcı hesapları ve bilgisayar adlarını veya grup belirleyerek belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96418-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="96418-115">Bir Active Directory etki alanına katılmış bir bilgisayar için cmdlet kuralı oluşturmak için bilgisayarın güvenlik tanımlayıcısı (SID) kullanır.</span><span class="sxs-lookup"><span data-stu-id="96418-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span> <span data-ttu-id="96418-116">Bu sayede kısa bir ad, bir tam etki alanı adı (FQDN) veya bir IP adresi için kullanılacak **bilgisayar adı** alan oturum açma sayfasında.</span><span class="sxs-lookup"><span data-stu-id="96418-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="96418-117">Bir Active Directory etki alanına katılmamış bir bilgisayarda, cmdlet, yönetici tarafından sağlanan bilgisayar adını kullanarak kuralı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96418-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="96418-118">Son Kullanıcı başarıyla bu makineye bağlanmak için kuralda göründüğü gibi bilgisayar adı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96418-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="96418-119">Ardından ağ üzerinde aynı ada sahip birden çok bilgisayar varsa, kısa ad birden fazla bilgisayara çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96418-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="96418-120">Bir bağlantıyı kurarken bu için karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="96418-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="96418-121">Adlı çalışma grubu bilgisayarı için bir kuralı varsa, örneğin, "*Sunucu1*" adlı yeni bir bilgisayar *server1.contoso.com* katıldığından ağa yetkilendirme kurallarını kullanarak doğrulama başarılı olur ve Windows PowerShell Web erişimi çalışır adlı bilgisayara bir bağlantı kurmak "*Sunucu1*".</span><span class="sxs-lookup"><span data-stu-id="96418-121">For example, if a rule exists for the workgroup computer named "*Server1*" and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named "*Server1*".</span></span> <span data-ttu-id="96418-122">Bu bağlantı ile belirtilen bilgisayar kurulduktan garanti edilmez; çalışma grubu veya adlı etki alanı bilgisayarda denemesi yapılamadı "*Sunucu1*".</span><span class="sxs-lookup"><span data-stu-id="96418-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="96418-123">Belirsizliği azaltmak için hedef bilgisayar için mümkün olduğunca bir yetkilendirme kuralı oluşturmak FQDN kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="96418-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="96418-124">Birincil oturum açma kimlik bilgisi alternatif kimlik bilgilerini değil Windows PowerShell Web erişimi kullanıcı yetkilendirme kuralları değerlendirin (ikinci bir dizi kimlik bilgisi bulundu **isteğe bağlı bağlantı ayarları** bölümü oturum açma sayfası).</span><span class="sxs-lookup"><span data-stu-id="96418-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="96418-125">Bu örneği için örneğin 6'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="96418-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="96418-126">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96418-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="96418-127">-ComputerGroupName \<dize\></span><span class="sxs-lookup"><span data-stu-id="96418-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="96418-128">Active Directory etki alanı Hizmetleri (AD DS) veya yerel gruplar bu kural erişim veren bir bilgisayar grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-129">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-129">Aliases</span></span>                     | <span data-ttu-id="96418-130">yok</span><span class="sxs-lookup"><span data-stu-id="96418-130">none</span></span>                  |
| <span data-ttu-id="96418-131">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-131">Required?</span></span>                   | <span data-ttu-id="96418-132">TRUE</span><span class="sxs-lookup"><span data-stu-id="96418-132">true</span></span>                  |
| <span data-ttu-id="96418-133">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-133">Position?</span></span>                   | <span data-ttu-id="96418-134">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-134">named</span></span>                 |
| <span data-ttu-id="96418-135">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-135">Default Value</span></span>               | <span data-ttu-id="96418-136">yok</span><span class="sxs-lookup"><span data-stu-id="96418-136">none</span></span>                  |
| <span data-ttu-id="96418-137">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-137">Accept Pipeline Input?</span></span>      | <span data-ttu-id="96418-138">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-138">True (ByPropertyName)</span></span> |
| <span data-ttu-id="96418-139">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-139">Accept Wildcard Characters?</span></span> | <span data-ttu-id="96418-140">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-140">false</span></span>                 |

### <a name="-computername-string"></a><span data-ttu-id="96418-141">-ComputerName \<dize\></span><span class="sxs-lookup"><span data-stu-id="96418-141">-ComputerName \<String\></span></span>

<span data-ttu-id="96418-142">Bu kural erişim veren bilgisayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-143">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-143">Aliases</span></span>                     | <span data-ttu-id="96418-144">yok</span><span class="sxs-lookup"><span data-stu-id="96418-144">none</span></span>                  |
| <span data-ttu-id="96418-145">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-145">Required?</span></span>                   | <span data-ttu-id="96418-146">TRUE</span><span class="sxs-lookup"><span data-stu-id="96418-146">true</span></span>                  |
| <span data-ttu-id="96418-147">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-147">Position?</span></span>                   | <span data-ttu-id="96418-148">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-148">named</span></span>                 |
| <span data-ttu-id="96418-149">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-149">Default Value</span></span>               | <span data-ttu-id="96418-150">yok</span><span class="sxs-lookup"><span data-stu-id="96418-150">none</span></span>                  |
| <span data-ttu-id="96418-151">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-151">Accept Pipeline Input?</span></span>      | <span data-ttu-id="96418-152">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-152">True (ByPropertyName)</span></span> |
| <span data-ttu-id="96418-153">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-153">Accept Wildcard Characters?</span></span> | <span data-ttu-id="96418-154">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-154">false</span></span>                 |

### <a name="-configurationname-string"></a><span data-ttu-id="96418-155">-ConfigurationName \<dize\></span><span class="sxs-lookup"><span data-stu-id="96418-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="96418-156">Windows PowerShell oturumu yapılandırması, olarak da bilinen bu kural erişim veren çalışma adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-157">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-157">Aliases</span></span>                     | <span data-ttu-id="96418-158">yok</span><span class="sxs-lookup"><span data-stu-id="96418-158">none</span></span>                  |
| <span data-ttu-id="96418-159">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-159">Required?</span></span>                   | <span data-ttu-id="96418-160">TRUE</span><span class="sxs-lookup"><span data-stu-id="96418-160">true</span></span>                  |
| <span data-ttu-id="96418-161">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-161">Position?</span></span>                   | <span data-ttu-id="96418-162">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-162">named</span></span>                 |
| <span data-ttu-id="96418-163">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-163">Default Value</span></span>               | <span data-ttu-id="96418-164">yok</span><span class="sxs-lookup"><span data-stu-id="96418-164">none</span></span>                  |
| <span data-ttu-id="96418-165">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-165">Accept Pipeline Input?</span></span>      | <span data-ttu-id="96418-166">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-166">True (ByPropertyName)</span></span> |
| <span data-ttu-id="96418-167">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-167">Accept Wildcard Characters?</span></span> | <span data-ttu-id="96418-168">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-168">false</span></span>                 |

### <a name="-credential--pscredential"></a><span data-ttu-id="96418-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="96418-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="96418-170">Belirtir bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kuralları değiştirmek için kullanmak istediğiniz bir kullanıcı hesabı için nesne.</span><span class="sxs-lookup"><span data-stu-id="96418-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="96418-171">Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır.</span><span class="sxs-lookup"><span data-stu-id="96418-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="96418-172">Alınacak bir **PSCredential** uzaktan yetkilendirme kuralları eklemek, çalıştırmak için gerekli olan nesne [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="96418-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-173">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-173">Aliases</span></span>                     | <span data-ttu-id="96418-174">yok</span><span class="sxs-lookup"><span data-stu-id="96418-174">none</span></span>  |
| <span data-ttu-id="96418-175">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-175">Required?</span></span>                   | <span data-ttu-id="96418-176">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-176">false</span></span> |
| <span data-ttu-id="96418-177">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-177">Position?</span></span>                   | <span data-ttu-id="96418-178">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-178">named</span></span> |
| <span data-ttu-id="96418-179">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-179">Default Value</span></span>               | <span data-ttu-id="96418-180">yok</span><span class="sxs-lookup"><span data-stu-id="96418-180">none</span></span>  |
| <span data-ttu-id="96418-181">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-181">Accept Pipeline Input?</span></span>      | <span data-ttu-id="96418-182">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-182">false</span></span> |
| <span data-ttu-id="96418-183">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-183">Accept Wildcard Characters?</span></span> | <span data-ttu-id="96418-184">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-184">false</span></span> |

### <a name="-force"></a><span data-ttu-id="96418-185">-Force</span><span class="sxs-lookup"><span data-stu-id="96418-185">-Force</span></span>

<span data-ttu-id="96418-186">Komutu, kullanıcı onayı istemeden çalışmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="96418-186">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="96418-187">Ayrıca, bir basit veya kısa bir bilgisayar adı (örneğin, bir etki alanı adı değil veya tam değil bir addır) girdiğinizde, ayrıca onaylamanızı ister.</span><span class="sxs-lookup"><span data-stu-id="96418-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="96418-188">Böylece bir bilgisayar yalnızca bilgisayar bir çalışma grubunda ise eklemek için basit bir ad kullanabilirsiniz güvenlik nedenleriyle, onay istenir.</span><span class="sxs-lookup"><span data-stu-id="96418-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-189">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-189">Aliases</span></span>                              | <span data-ttu-id="96418-190">yok</span><span class="sxs-lookup"><span data-stu-id="96418-190">none</span></span>                                 |
| <span data-ttu-id="96418-191">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-191">Required?</span></span>                            | <span data-ttu-id="96418-192">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-192">false</span></span>                                |
| <span data-ttu-id="96418-193">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-193">Position?</span></span>                            | <span data-ttu-id="96418-194">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-194">named</span></span>                                |
| <span data-ttu-id="96418-195">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-195">Default Value</span></span>                        | <span data-ttu-id="96418-196">yok</span><span class="sxs-lookup"><span data-stu-id="96418-196">none</span></span>                                 |
| <span data-ttu-id="96418-197">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="96418-198">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-198">false</span></span>                                |
| <span data-ttu-id="96418-199">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="96418-200">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="96418-201">-RuleName \<dize\></span><span class="sxs-lookup"><span data-stu-id="96418-201">-RuleName \<String\></span></span>

<span data-ttu-id="96418-202">Bu kuralın kolay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-203">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-203">Aliases</span></span>                              | <span data-ttu-id="96418-204">yok</span><span class="sxs-lookup"><span data-stu-id="96418-204">none</span></span>                                 |
| <span data-ttu-id="96418-205">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-205">Required?</span></span>                            | <span data-ttu-id="96418-206">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-206">false</span></span>                                |
| <span data-ttu-id="96418-207">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-207">Position?</span></span>                            | <span data-ttu-id="96418-208">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-208">named</span></span>                                |
| <span data-ttu-id="96418-209">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-209">Default Value</span></span>                        | <span data-ttu-id="96418-210">yok</span><span class="sxs-lookup"><span data-stu-id="96418-210">none</span></span>                                 |
| <span data-ttu-id="96418-211">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="96418-212">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="96418-213">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="96418-214">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="96418-215">-UserGroupName \<dize\[\]\></span><span class="sxs-lookup"><span data-stu-id="96418-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="96418-216">AD DS veya yerel gruplar bu kural erişim veren bir veya daha fazla kullanıcı grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-217">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-217">Aliases</span></span>                              | <span data-ttu-id="96418-218">yok</span><span class="sxs-lookup"><span data-stu-id="96418-218">none</span></span>                                 |
| <span data-ttu-id="96418-219">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-219">Required?</span></span>                            | <span data-ttu-id="96418-220">TRUE</span><span class="sxs-lookup"><span data-stu-id="96418-220">true</span></span>                                 |
| <span data-ttu-id="96418-221">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-221">Position?</span></span>                            | <span data-ttu-id="96418-222">adlı</span><span class="sxs-lookup"><span data-stu-id="96418-222">named</span></span>                                |
| <span data-ttu-id="96418-223">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-223">Default Value</span></span>                        | <span data-ttu-id="96418-224">yok</span><span class="sxs-lookup"><span data-stu-id="96418-224">none</span></span>                                 |
| <span data-ttu-id="96418-225">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="96418-226">TRUE (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="96418-227">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="96418-228">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="96418-229">-UserName \<dize\[\]\></span><span class="sxs-lookup"><span data-stu-id="96418-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="96418-230">Bu kural erişim veren bir veya daha fazla kullanıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="96418-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="96418-231">Kullanıcı adı, ağ geçidi bilgisayarınıza veya AD DS'de bir kullanıcı bir yerel kullanıcı hesabı olabilir.</span><span class="sxs-lookup"><span data-stu-id="96418-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span> <span data-ttu-id="96418-232">Biçim `domain\user` veya `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="96418-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="96418-233">Diğer adlar</span><span class="sxs-lookup"><span data-stu-id="96418-233">Aliases</span></span>                              | <span data-ttu-id="96418-234">yok</span><span class="sxs-lookup"><span data-stu-id="96418-234">none</span></span>                                 |
| <span data-ttu-id="96418-235">Gerekli mi?</span><span class="sxs-lookup"><span data-stu-id="96418-235">Required?</span></span>                            | <span data-ttu-id="96418-236">TRUE</span><span class="sxs-lookup"><span data-stu-id="96418-236">true</span></span>                                 |
| <span data-ttu-id="96418-237">Konumu?</span><span class="sxs-lookup"><span data-stu-id="96418-237">Position?</span></span>                            | <span data-ttu-id="96418-238">1</span><span class="sxs-lookup"><span data-stu-id="96418-238">1</span></span>                                    |
| <span data-ttu-id="96418-239">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="96418-239">Default Value</span></span>                        | <span data-ttu-id="96418-240">yok</span><span class="sxs-lookup"><span data-stu-id="96418-240">none</span></span>                                 |
| <span data-ttu-id="96418-241">Ardışık Düzen Girişi kabul edilsin mi?</span><span class="sxs-lookup"><span data-stu-id="96418-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="96418-242">TRUE (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="96418-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="96418-243">Joker Karakter Kabul Edilsin Mi?</span><span class="sxs-lookup"><span data-stu-id="96418-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="96418-244">yanlış</span><span class="sxs-lookup"><span data-stu-id="96418-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="96418-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="96418-245">\<CommonParameters\></span></span>

<span data-ttu-id="96418-246">Bu cmdlet, ortak parametreleri destekler:</span><span class="sxs-lookup"><span data-stu-id="96418-246">This cmdlet supports the common parameters:</span></span>

<span data-ttu-id="96418-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer ve -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="96418-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="96418-248">Daha fazla bilgi için [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="96418-248">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="96418-249">GİRİŞ</span><span class="sxs-lookup"><span data-stu-id="96418-249">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="96418-250">Dize</span><span class="sxs-lookup"><span data-stu-id="96418-250">String</span></span>

<span data-ttu-id="96418-251">Bu cmdlet bir dize veya dizeler dizisi girdi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="96418-251">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="96418-252">dize\[\]</span><span class="sxs-lookup"><span data-stu-id="96418-252">String\[\]</span></span>

<span data-ttu-id="96418-253">Bu cmdlet bir dize veya dizeler dizisi girdi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="96418-253">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="96418-254">Çıkışlar</span><span class="sxs-lookup"><span data-stu-id="96418-254">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="96418-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="96418-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="96418-256">Bu cmdlet döndürür bir yetkilendirme kuralı nesnesine.</span><span class="sxs-lookup"><span data-stu-id="96418-256">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="96418-257">ÖRNEKLERİ</span><span class="sxs-lookup"><span data-stu-id="96418-257">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="96418-258">ÖRNEK 1</span><span class="sxs-lookup"><span data-stu-id="96418-258">EXAMPLE 1</span></span>

<span data-ttu-id="96418-259">Bu örnekte oturum yapılandırması erişimi verir _PSWAEndpoint_, sınırlı çalışma alanı _SUN2_ kullanıcılar için _SMAdmins_ grubu.</span><span class="sxs-lookup"><span data-stu-id="96418-259">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="96418-260">Bilgisayar adı tam etki alanı adı (FQDN) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96418-260">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="96418-261">Yöneticiler, sınırlı bir oturum yapılandırması veya sınırlı bir cmdlet'ler ve son kullanıcıların görevleri aralığıdır çalışma alanı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="96418-261">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="96418-262">Sınırlı bir çalışma alanı tanımlanması, kullanıcıların izin verilen Windows PowerShell(r) çalışma alanında, bu nedenle daha güvenli bir bağlantı sunulmamaktadır diğer bilgisayarlara erişmesini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="96418-262">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell(r) runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="96418-263">Oturum yapılandırmaları hakkında daha fazla bilgi için bkz. [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) veya [yükleme ve kullanım Windows PowerShell Web erişimi](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="96418-263">For more information on session configurations, see [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) or [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="96418-264">ÖRNEK 2</span><span class="sxs-lookup"><span data-stu-id="96418-264">EXAMPLE 2</span></span>

<span data-ttu-id="96418-265">Bu örnek, varsayılan Windows PowerShell oturum yapılandırması erişimi verir `Microsoft.PowerShell`, *SUN2* adlı kullanıcıları kullanıcılar için `contoso\user1`, `contoso\user2`, ve `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="96418-265">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="96418-266">Bu cmdlet, üç kuralları (kişi başına 1) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96418-266">This cmdlet creates three rules (1 per person).</span></span>

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="96418-267">ÖRNEK 3</span><span class="sxs-lookup"><span data-stu-id="96418-267">EXAMPLE 3</span></span>

<span data-ttu-id="96418-268">Bu örnekte, işlem hattı aracılığıyla kullanıcı adı değerleri giriş gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="96418-268">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="96418-269">ÖRNEK 4</span><span class="sxs-lookup"><span data-stu-id="96418-269">EXAMPLE 4</span></span>

<span data-ttu-id="96418-270">Bu örnekte nasıl tüm parametreler özellik adına göre işlem hattından değerleri alın.</span><span class="sxs-lookup"><span data-stu-id="96418-270">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="96418-271">ÖRNEK 5</span><span class="sxs-lookup"><span data-stu-id="96418-271">EXAMPLE 5</span></span>

<span data-ttu-id="96418-272">Bu örnek adlı yerel kullanıcı izin verecek bir kural ekler `PswaServer\ChrisLocal` adlı sunucuda erişim **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="96418-272">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="96418-273">Bu örnekte, burada bir çalışma grubundaki ağ geçididir ve hedef bilgisayar bir etki alanında bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="96418-273">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="96418-274">Yetkilendirme kuralı Gateway'de yerel kullanıcılar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="96418-274">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="96418-275">Windows PowerShell Web erişimi oturum açma sayfasında, kimliğini başarıyla doğrulamak için kullanıcı kimlik bilgilerini ikinci bir set sağlamalıdır **isteğe bağlı bağlantı ayarları** alan.</span><span class="sxs-lookup"><span data-stu-id="96418-275">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="96418-276">Ağ Geçidi sunucusu, kullanıcı hedef bilgisayarda adlı bir sunucu kimlik doğrulaması için ek kimlik bilgileri kümesini kullanır. *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="96418-276">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="96418-277">ÖRNEK 6</span><span class="sxs-lookup"><span data-stu-id="96418-277">EXAMPLE 6</span></span>

<span data-ttu-id="96418-278">Bu örnekte, tüm kullanıcıların tüm bilgisayarlarda tüm uç noktalara erişimi verir.</span><span class="sxs-lookup"><span data-stu-id="96418-278">This example allows all users access to all endpoints on all computers.</span></span> <span data-ttu-id="96418-279">Bu temelde, yetkilendirme kuralları devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="96418-279">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="96418-280">Kullanım `*` joker karakter güvenlik açısından duyarlı dağıtımları için önerilmez ve yalnızca test ortamları için kabul veya güvenlik burada gevşetilebilir dağıtımda kullanılan.</span><span class="sxs-lookup"><span data-stu-id="96418-280">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="96418-281">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="96418-281">See Also</span></span>

<span data-ttu-id="96418-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="96418-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="96418-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="96418-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="96418-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="96418-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="96418-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="96418-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="96418-286">Üye Ekle</span><span class="sxs-lookup"><span data-stu-id="96418-286">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="96418-287">Yeni nesne</span><span class="sxs-lookup"><span data-stu-id="96418-287">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="96418-288">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="96418-288">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
