---
title: Güvenlik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849031"
---
# <a name="security-parameters"></a><span data-ttu-id="85885-102">Güvenlik Parametreleri</span><span class="sxs-lookup"><span data-stu-id="85885-102">Security Parameters</span></span>

<span data-ttu-id="85885-103">Aşağıdaki tabloda, sertifika anahtarı ve ayrıcalık bilgilerini belirtmek parametreleri gibi bir işlem için güvenlik bilgileri sağlamak için kullanılan parametreler için işlevselliği ve önerilen adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="85885-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

<span data-ttu-id="85885-104">ACL veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-104">ACL Data type: String</span></span>

<span data-ttu-id="85885-105">Koruma için bir katalog veya bir Tekdüzen Kaynak Tanımlayıcısı (URI) için erişim denetimi düzeyini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-105">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="85885-106">CertFile veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-106">CertFile Data type: String</span></span>

<span data-ttu-id="85885-107">Kullanıcı şunlardan birini içeren dosyanın adını belirtmek için bu parametreyi uygulayın:</span><span class="sxs-lookup"><span data-stu-id="85885-107">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span>

- <span data-ttu-id="85885-108">Bir Base64 veya Distinguished Encoding Rules (DER) kodlu x.509 sertifikası</span><span class="sxs-lookup"><span data-stu-id="85885-108">A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span>

- <span data-ttu-id="85885-109">En az bir sertifika ve anahtar içeren bir ortak anahtar şifreleme standartları (PKCS) #12 dosyası</span><span class="sxs-lookup"><span data-stu-id="85885-109">A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>

<span data-ttu-id="85885-110">CertIssuerName veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-110">CertIssuerName Data type: String</span></span>

<span data-ttu-id="85885-111">Bu parametre, kullanıcı bir sertifikayı verenin adını belirtebilir veya kullanıcı bir alt dizesi belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-111">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="85885-112">CertRequestFile veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-112">CertRequestFile Data type: String</span></span>

<span data-ttu-id="85885-113">Bir Base64 veya DER kodlu PKCS #10 sertifika isteğini içeren dosyanın adını belirlemek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-113">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>

<span data-ttu-id="85885-114">CertSerialNumber veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-114">CertSerialNumber Data type: String</span></span>

<span data-ttu-id="85885-115">Sertifika yetkilisi tarafından verilmiş bir seri numarası belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-115">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>

<span data-ttu-id="85885-116">Sertifikadeposukonumu veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-116">CertStoreLocation Data type: String</span></span>

<span data-ttu-id="85885-117">Kullanıcı sertifika depolama konumunu belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-117">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="85885-118">Genellikle bir dosya yolu konumdur.</span><span class="sxs-lookup"><span data-stu-id="85885-118">The location is typically a file path.</span></span>

<span data-ttu-id="85885-119">CertSubjectName veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-119">CertSubjectName Data type: String</span></span>

<span data-ttu-id="85885-120">Bu parametre, kullanıcı bir sertifikayı veren belirtebilir veya kullanıcı bir alt dizesi belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-120">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="85885-121">CertUsage veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-121">CertUsage Data type: String</span></span>

<span data-ttu-id="85885-122">Anahtar kullanımı veya Gelişmiş anahtar kullanımı belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-122">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="85885-123">Anahtar biraz, biraz, bir nesne tanımlayıcı (OID) maske olarak veya bir dizeyi temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="85885-123">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>

<span data-ttu-id="85885-124">Kimlik bilgisi veri türü: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="85885-124">Credential Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>

<span data-ttu-id="85885-125">Bu parametre, böylece cmdlet'i otomatik olarak bir kullanıcı adı veya parola girmesini ister uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-125">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="85885-126">Tam bir kimlik bilgisi doğrudan sağlanmazsa, her ikisi için de bir istem görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="85885-126">A prompt for both is displayed if a full credential is not supplied directly.</span></span>

<span data-ttu-id="85885-127">CSPAdı veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-127">CSPName Data type: String</span></span>

<span data-ttu-id="85885-128">Kullanıcı sertifika hizmeti sağlayıcısı (CSP) adını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-128">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>

<span data-ttu-id="85885-129">CSPType veri türü: Tamsayı</span><span class="sxs-lookup"><span data-stu-id="85885-129">CSPType Data type: Integer</span></span>

<span data-ttu-id="85885-130">Kullanıcı, CSP türünü belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-130">Implement this parameter so that the user can specify the type of CSP.</span></span>

<span data-ttu-id="85885-131">Grup veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-131">Group Data type: String</span></span>

<span data-ttu-id="85885-132">Bu parametre, kullanıcı için erişim ilkeleri koleksiyonunu belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-132">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="85885-133">Daha fazla bilgi için açıklamasına bakın `Principal` parametresi.</span><span class="sxs-lookup"><span data-stu-id="85885-133">For more information, see the description of the `Principal` parameter.</span></span>

<span data-ttu-id="85885-134">KeyAlgorithm veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-134">KeyAlgorithm Data type: String</span></span>

<span data-ttu-id="85885-135">Kullanıcı güvenlik için kullanılacak anahtar oluşturma algoritmasını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-135">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>

<span data-ttu-id="85885-136">AnahtarKapsayıcıAdı veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-136">KeyContainerName Data type: String</span></span>

<span data-ttu-id="85885-137">Kullanıcı anahtar kapsayıcısı adını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-137">Implement this parameter so that the user can specify the name of the key container.</span></span>

<span data-ttu-id="85885-138">KeyLength veri türü: Tamsayı</span><span class="sxs-lookup"><span data-stu-id="85885-138">KeyLength Data type: Integer</span></span>

<span data-ttu-id="85885-139">Bu parametre, kullanıcının anahtar uzunluğunu bit cinsinden belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-139">Implement this parameter so that the user can specify the length of the key in bits.</span></span>

<span data-ttu-id="85885-140">İşlem veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-140">Operation Data type: String</span></span>

<span data-ttu-id="85885-141">Bu parametre, kullanıcı korumalı bir nesne üzerinde gerçekleştirilecek bir eylem belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-141">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>

<span data-ttu-id="85885-142">Asıl veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-142">Principal Data type: String</span></span>

<span data-ttu-id="85885-143">Kullanıcı erişimi için benzersiz bir tanımlanabilen varlık belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-143">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>

<span data-ttu-id="85885-144">Ayrıcalık veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-144">Privilege Data type: String</span></span>

<span data-ttu-id="85885-145">Bu parametre, kullanıcının bir cmdlet, belirli bir varlık için bir işlem gerçekleştirmesine gerek sağ belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-145">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>

<span data-ttu-id="85885-146">Ayrıcalıkları veri türü: Ayrıcalıkları dizisi</span><span class="sxs-lookup"><span data-stu-id="85885-146">Privileges Data type: Array of privileges</span></span>

<span data-ttu-id="85885-147">Bu parametre, kullanıcının bir cmdlet, belirli bir giriş için kendi işlemi gerçekleştirmek için gereken hakları belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-147">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>

<span data-ttu-id="85885-148">Rol veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-148">Role Data type: String</span></span>

<span data-ttu-id="85885-149">Bu parametre, kullanıcının bir varlık tarafından gerçekleştirilen işlemlerin bir dizi belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-149">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>

<span data-ttu-id="85885-150">SaveCred veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="85885-150">SaveCred Data type: SwitchParameter</span></span>

<span data-ttu-id="85885-151">Bu parametre, böylece parametresi belirtildiğinde kullanıcı tarafından daha önce kaydedilen kimlik bilgileri kullanılacak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-151">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>

<span data-ttu-id="85885-152">Kapsam veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-152">Scope Data type: String</span></span>

<span data-ttu-id="85885-153">Bu parametre, kullanıcının cmdlet'i için korunan nesnelerin grubunu belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-153">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>

<span data-ttu-id="85885-154">SID veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="85885-154">SID Data type: String</span></span>

<span data-ttu-id="85885-155">Bu parametre, kullanıcı sorumlu temsil eden benzersiz bir tanımlayıcı belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-155">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>

<span data-ttu-id="85885-156">Güvenilen. veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="85885-156">Trusted Data type: SwitchParameter</span></span>

<span data-ttu-id="85885-157">Bu parametre, böylece parametresi belirtildiğinde güven düzeyleri desteklenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-157">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>

<span data-ttu-id="85885-158">TrustLevel veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="85885-158">TrustLevel Data type: Keyword</span></span>

<span data-ttu-id="85885-159">Kullanıcı desteklenen güven düzeyini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85885-159">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="85885-160">Örneğin, internet, intranet ve fulltrust olası değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="85885-160">For example, possible values include internet, intranet, and fulltrust.</span></span>

## <a name="see-also"></a><span data-ttu-id="85885-161">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="85885-161">See Also</span></span>

[<span data-ttu-id="85885-162">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="85885-162">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="85885-163">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="85885-163">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="85885-164">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="85885-164">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
