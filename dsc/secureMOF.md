---
ms.date: 10/31/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MOF dosyası güvenliğini sağlama
ms.openlocfilehash: 80ef37ef1bdcb0a8b0ad343b4eab99f1bc66e116
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="550b1-103">MOF dosyası güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="550b1-103">Securing the MOF File</span></span>

><span data-ttu-id="550b1-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="550b1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="550b1-105">DSC yapılandırma sunucusu düğümlerinin burada yerel Configuration Manager (LCM'yi) istenen son durum uygulayan bir MOF dosyasında depolanan bilgileri uygulayarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="550b1-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="550b1-106">Bu dosya yapılandırma ayrıntılarını içerdiğinden, güvenli tutmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="550b1-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="550b1-107">Bu konuda, hedef düğüm dosya şifrelenmiş sahip olmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="550b1-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="550b1-108">Düğüm kullanmaya uygulandığında sürüm 5.0 PowerShell ile başlayarak, tüm MOF dosyası varsayılan olarak şifrelenmiş **başlangıç DSCConfiguration** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="550b1-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the **Start-DSCConfiguration** cmdlet.</span></span>
<span data-ttu-id="550b1-109">Bu makalede açıklanan işlemi yalnızca Sertifikalar, hedef düğüm tarafından indirilen yapılandırmaları şifresi çözülür ve uygulanmadan önce sistem tarafından okunur emin olmak için yönetilmeyen çekme hizmet protokolünü kullanarak bir çözüm uygulama gereklidir (örneğin, çekme hizmeti Windows Server'da kullanılabilir).</span><span class="sxs-lookup"><span data-stu-id="550b1-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="550b1-110">Düğümleri kayıtlı için [Azure Otomasyonu DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) otomatik olarak sahip sertifikaları yüklü ve hiçbir yönetim yükü ile hizmet yöneten gerekli.</span><span class="sxs-lookup"><span data-stu-id="550b1-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

><span data-ttu-id="550b1-111">**Not:** şifreleme için kullanılan sertifikaları bu konuda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="550b1-111">**Note:** This topic discusses certificates used for encryption.</span></span>
><span data-ttu-id="550b1-112">Şifreleme için otomatik olarak imzalanan bir sertifika yeterlidir, özel anahtarı her zaman gizli anahtar ve şifreleme tutulduğundan belgenin güven anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="550b1-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
><span data-ttu-id="550b1-113">Otomatik olarak imzalanan sertifikalar gereken *değil* kimlik doğrulama amacıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="550b1-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
><span data-ttu-id="550b1-114">Tüm kimlik doğrulama amacıyla bir sertifika bir güvenilen sertifika yetkilisi (CA) gelen kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="550b1-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="550b1-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="550b1-115">Prerequisites</span></span>

<span data-ttu-id="550b1-116">Başarıyla bir DSC yapılandırma güvenliğini sağlamak için kullanılan kimlik bilgilerini şifrelemek için aşağıdakilere sahip olduğunuzdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="550b1-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="550b1-117">**Bazı şekillerini vermek ve sertifikaları dağıtma**.</span><span class="sxs-lookup"><span data-stu-id="550b1-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="550b1-118">Bu konu ve onun örnekler Active Directory Sertifika yetkilisi kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="550b1-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="550b1-119">Active Directory Sertifika Hizmetleri hakkında daha fazla bilgi için bkz: [Active Directory Sertifika Hizmetleri'ne Genel Bakış](https://technet.microsoft.com/library/hh831740.aspx) ve [Windows Server 2008'de Active Directory Sertifika Hizmetleri](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="550b1-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="550b1-120">**Hedef düğüm veya düğümler yönetim erişimi**.</span><span class="sxs-lookup"><span data-stu-id="550b1-120">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="550b1-121">**Her hedef düğüm, Kişisel depolama kaydedilmiş şifreleme özellikli bir sertifikaya sahip**.</span><span class="sxs-lookup"><span data-stu-id="550b1-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="550b1-122">Windows PowerShell'de depolama Cert: \LocalMachine\My yoludur.</span><span class="sxs-lookup"><span data-stu-id="550b1-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="550b1-123">Bu konudaki örnekler adresindeki (yanı sıra diğer sertifika şablonlarını) bulabilirsiniz "iş istasyonu kimlik doğrulaması" şablonu kullanmak [varsayılan sertifika şablonları](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="550b1-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="550b1-124">Bu yapılandırma hedef düğüm dışında bir bilgisayarda çalıştıracaksanız **sertifikanın ortak anahtarını dışarı aktarmak**ve yapılandırmasından çalışacağı bilgisayarda alın.</span><span class="sxs-lookup"><span data-stu-id="550b1-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="550b1-125">Yalnızca dışarı emin olun **ortak** özel anahtarı güvenli tutmaya; anahtarı.</span><span class="sxs-lookup"><span data-stu-id="550b1-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="550b1-126">Genel işlem</span><span class="sxs-lookup"><span data-stu-id="550b1-126">Overall process</span></span>

 1. <span data-ttu-id="550b1-127">Sertifikalar, anahtarları ve parmak izleri, sertifikanın kopyasını her hedef düğüme sahiptir ve ortak anahtar ve parmak izi yapılandırma bilgisayarın olduğundan emin olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="550b1-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="550b1-128">Parmak izi ortak anahtar ve yolunu içeren bir yapılandırma veri bloğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="550b1-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="550b1-129">Hedef düğüm için istenen yapılandırmanızı tanımlar ve yerel yapılandırma komut verme hedef düğümleri şifre çözme ayarlar bir yapılandırma komut dosyası sertifika ve kendi parmak izini kullanarak yapılandırma verilerin şifresini çözmek için Yöneticisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="550b1-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="550b1-130">Yerel Configuration Manager ayarlar ve DSC yapılandırması başlangıç yapılandırması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="550b1-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diyagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="550b1-132">Sertifika gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="550b1-132">Certificate Requirements</span></span>

<span data-ttu-id="550b1-133">Kimlik bilgisi şifreleme kabul etmek için bir ortak anahtar sertifikası kullanılabilir olmalıdır _hedef düğüm_ diğer bir deyişle **güvenilen** DSC yapılandırması yazmak için kullanılan bilgisayar tarafından.</span><span class="sxs-lookup"><span data-stu-id="550b1-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="550b1-134">Bu ortak anahtar sertifikası için bu DSC kimlik bilgisi şifreleme için kullanılacak belirli gereksinimlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="550b1-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="550b1-135">**Anahtar kullanımı**:</span><span class="sxs-lookup"><span data-stu-id="550b1-135">**Key Usage**:</span></span>
   - <span data-ttu-id="550b1-136">İçermelidir: 'KeyEncipherment' ve 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="550b1-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="550b1-137">Gereken _değil_ içeriyor: 'Dijital imza'.</span><span class="sxs-lookup"><span data-stu-id="550b1-137">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="550b1-138">**Gelişmiş anahtar kullanımı**:</span><span class="sxs-lookup"><span data-stu-id="550b1-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="550b1-139">İçermelidir: belge şifreleme (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="550b1-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="550b1-140">Gereken _değil_ içerir: istemci kimlik doğrulaması (1.3.6.1.5.5.7.3.2) ve sunucu kimlik doğrulaması (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="550b1-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="550b1-141">Sertifikanın özel anahtarı kullanılabilir \* hedef Node_.</span><span class="sxs-lookup"><span data-stu-id="550b1-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
 4. <span data-ttu-id="550b1-142">**Sağlayıcı** sertifika "Microsoft RSA SChannel Şifreleme Sağlayıcısı" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="550b1-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

><span data-ttu-id="550b1-143">**Önerilen en iyi yöntem:** anahtar kullanımı 'Dijital imza' ya da kimlik doğrulama EKU'lar birini içeren ile bir sertifika kullanabilirsiniz, ancak bu yanlış kullanılmış ve karşı savunmasız saldırı şifreleme anahtarının daha kolay olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="550b1-143">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="550b1-144">Bu nedenle bu anahtar kullanımı ve EKU atlar özellikle DSC kimlik bilgilerini korumak amacıyla oluşturulan bir sertifika kullanmak en iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="550b1-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="550b1-145">Varolan bir sertifikayı üzerinde _hedef düğüm_ karşılaması için güvenli DSC kimlik bilgileri bu ölçütler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="550b1-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="550b1-146">Sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="550b1-146">Certificate creation</span></span>

<span data-ttu-id="550b1-147">Gerekli şifreleme sertifikası (genel-özel anahtar çifti) oluşturmak için uygulayabileceğiniz iki yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="550b1-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="550b1-148">Üzerinde oluşturulduğu **hedef düğüm** ve yalnızca ortak anahtarını dışarı aktarma **yazma düğümü**</span><span class="sxs-lookup"><span data-stu-id="550b1-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="550b1-149">Üzerinde oluşturulduğu **yazma düğümü** ve tüm anahtar çifti verme **hedef düğüm**</span><span class="sxs-lookup"><span data-stu-id="550b1-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="550b1-150">Yöntem 1 MOF kimlik bilgilerini şifrelemek için kullanılan özel anahtarı her zaman hedef düğümde kalır nedeniyle önerilir.</span><span class="sxs-lookup"><span data-stu-id="550b1-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="550b1-151">Hedef düğümde sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="550b1-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="550b1-152">Özel anahtarı üzerinde MOF şifresini çözmek için kullanılır çünkü gizli tutulması gereken **hedef düğüm** özel anahtar sertifikasını oluşturmak için bunu yapmanın en kolay yolu olan **hedef düğüm**ve kopyalama  **Ortak anahtar sertifikası** DSC yapılandırması bir MOF dosyasına yazmak için kullanılan bilgisayara.</span><span class="sxs-lookup"><span data-stu-id="550b1-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="550b1-153">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="550b1-153">The following example:</span></span>
 1. <span data-ttu-id="550b1-154">bir sertifika oluşturur **hedef düğüm**</span><span class="sxs-lookup"><span data-stu-id="550b1-154">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="550b1-155">üzerinde ortak anahtar sertifikası dışarı aktarmaları **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="550b1-155">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="550b1-156">Ortak anahtar sertifikası içine alır **my** sertifika deposunda **yazma düğümü**.</span><span class="sxs-lookup"><span data-stu-id="550b1-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="550b1-157">Hedef düğümde bulunan: oluşturma ve sertifika verme</span><span class="sxs-lookup"><span data-stu-id="550b1-157">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="550b1-158">Hedef düğüm: Windows Server 2016 ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="550b1-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="550b1-159">Bir kez dışarı ```DscPublicKey.cer``` kopyalanması gerekir **yazma düğümü**.</span><span class="sxs-lookup"><span data-stu-id="550b1-159">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="550b1-160">Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="550b1-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="550b1-161">Üzerinde Windows işletim sistemlerinin Windows 10 ve Windows Server 2016 önce yeni SelfSignedCertificate cmdlet desteklemez çünkü **türü** parametresi, bu sertifika oluşturma alternatif bir yöntem bunları gereklidir işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="550b1-161">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="550b1-162">Bu durumda kullanabileceğiniz ```makecert.exe``` veya ```certutil.exe``` bir sertifika oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="550b1-162">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="550b1-163">Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiğini indir](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifikayı oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="550b1-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="550b1-164">Bir kez dışarı ```DscPublicKey.cer``` kopyalanması gerekir **yazma düğümü**.</span><span class="sxs-lookup"><span data-stu-id="550b1-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="550b1-165">Yazma düğümde: sertifika ait ortak anahtarı alma</span><span class="sxs-lookup"><span data-stu-id="550b1-165">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="550b1-166">Geliştirme düğümde sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="550b1-166">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="550b1-167">Alternatif olarak, şifreleme sertifikası üzerinde oluşturulabilir **yazma düğümü**, dışarı aktarılan ile **özel anahtarı** bir PFX dosyası ve ardından alındığı **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="550b1-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="550b1-168">Bu, DSC kimlik bilgisi şifreleme uygulama için geçerli yöntemdir _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="550b1-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="550b1-169">PFX güvenli bir parola ile olsa da, güvenli aktarım sırasında tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="550b1-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="550b1-170">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="550b1-170">The following example:</span></span>
 1. <span data-ttu-id="550b1-171">bir sertifika oluşturur **yazma düğümü**.</span><span class="sxs-lookup"><span data-stu-id="550b1-171">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="550b1-172">özel anahtar dahil olmak üzere sertifika dışa aktarır **yazma düğümü**.</span><span class="sxs-lookup"><span data-stu-id="550b1-172">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="550b1-173">özel anahtardan kaldırır **yazma düğümü**, ancak ortak anahtar sertifikası tutar **my** depolar.</span><span class="sxs-lookup"><span data-stu-id="550b1-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="550b1-174">özel anahtar sertifikasını, üzerinde kök sertifika deposuna aktarır **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="550b1-174">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="550b1-175">Böylece tarafından güvenilecek, kök deposuna eklenmelidir **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="550b1-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="550b1-176">Yazma düğümde: oluşturma ve sertifika verme</span><span class="sxs-lookup"><span data-stu-id="550b1-176">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="550b1-177">Hedef düğüm: Windows Server 2016 ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="550b1-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```
<span data-ttu-id="550b1-178">Bir kez dışarı ```DscPrivateKey.pfx``` kopyalanması gerekir **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="550b1-178">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="550b1-179">Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="550b1-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="550b1-180">Üzerinde Windows işletim sistemlerinin Windows 10 ve Windows Server 2016 önce yeni SelfSignedCertificate cmdlet desteklemez çünkü **türü** parametresi, bu sertifika oluşturma alternatif bir yöntem bunları gereklidir işletim sistemleri.</span><span class="sxs-lookup"><span data-stu-id="550b1-180">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="550b1-181">Bu durumda kullanabileceğiniz ```makecert.exe``` veya ```certutil.exe``` bir sertifika oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="550b1-181">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="550b1-182">Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiğini indir](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifikayı oluşturmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="550b1-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="550b1-183">Hedef düğümde bulunan: olarak güvenilir bir kök sertifikası'nın özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="550b1-183">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="550b1-184">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="550b1-184">Configuration data</span></span>

<span data-ttu-id="550b1-185">Yapılandırma veri bloğu hangi hedef düğümleri olup olmadığına göre çalıştırmak veya kimlik bilgileri, şifreleme anlamına gelir ve diğer bilgileri şifrelenmez tanımlar.</span><span class="sxs-lookup"><span data-stu-id="550b1-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="550b1-186">Yapılandırma veri bloğu hakkında daha fazla bilgi için bkz: [ayırarak yapılandırma ve ortam verilerini](configData.md).</span><span class="sxs-lookup"><span data-stu-id="550b1-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="550b1-187">Kimlik bilgisi şifreleme için ilgili her düğüm için yapılandırılmış olan öğeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="550b1-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="550b1-188">**NodeName** -kimlik bilgilerinin şifrelenebilmesi yapılandırılmış hedef düğümün adı.</span><span class="sxs-lookup"><span data-stu-id="550b1-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="550b1-189">**PsDscAllowPlainTextPassword** - şifrelenmemiş kimlik bilgileri bu düğüme geçirilmesi izin verilmeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="550b1-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="550b1-190">Bu **önerilmez**.</span><span class="sxs-lookup"><span data-stu-id="550b1-190">This is **not recommended**.</span></span>
* <span data-ttu-id="550b1-191">**Parmak izi** -üzerinde DSC Yapılandırması'ndaki kimlik bilgilerini şifrelemek için kullanılan sertifikanın parmak izini _hedef düğüm_.</span><span class="sxs-lookup"><span data-stu-id="550b1-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="550b1-192">**Bu sertifika, hedef düğümde bulunan yerel makine sertifika deposunda bulunmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="550b1-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="550b1-193">**CertificateFile** - (yalnızca ortak anahtarı içeren) sertifika dosyası için kimlik bilgilerini şifrelemek için kullanılacak _hedef düğüm_.</span><span class="sxs-lookup"><span data-stu-id="550b1-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="550b1-194">Bu da olmalıdır bir DER ile kodlanmış ikili X.509 veya Base-64 kodlanmış X.509 biçimi sertifika dosyası.</span><span class="sxs-lookup"><span data-stu-id="550b1-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="550b1-195">Bu örnek, görev yapması için bir hedef düğümü adlandırılmış targetNode, ortak anahtar sertifika dosyasından (targetNode.cer adlı) ve ortak anahtar parmak izini yolunu belirtir. bir yapılandırma veri bloğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="550b1-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```


## <a name="configuration-script"></a><span data-ttu-id="550b1-196">Yapılandırma komut dosyası</span><span class="sxs-lookup"><span data-stu-id="550b1-196">Configuration script</span></span>

<span data-ttu-id="550b1-197">Yapılandırma betiği içinde kendisi, `PsCredential` en kısa sürede için depolanan kimlik bilgileri sağlamak için parametre.</span><span class="sxs-lookup"><span data-stu-id="550b1-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="550b1-198">Sağlanan örnek çalıştırdığınızda, DSC kimlik bilgilerini ister ve yapılandırma veri bloğundaki hedef düğümle ilişkili CertificateFile kullanarak MOF dosyasını şifrelemek.</span><span class="sxs-lookup"><span data-stu-id="550b1-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="550b1-199">Bu kod örneği bir dosyayı güvenli bir paylaşımdan bir kullanıcıya kopyalar.</span><span class="sxs-lookup"><span data-stu-id="550b1-199">This code example copies a file from a share that is secured to a user.</span></span>

```
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="550b1-200">Şifre çözme ayarlama</span><span class="sxs-lookup"><span data-stu-id="550b1-200">Setting up decryption</span></span>

<span data-ttu-id="550b1-201">Önce [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) çalışabilir, sertifikanın parmak izi doğrulamak için CertificateID kaynak kullanarak kimlik bilgileri şifresini çözmek için kullanılacak hangi sertifikanın her bir hedef düğümde yerel Configuration Manager söyleyin zorunda.</span><span class="sxs-lookup"><span data-stu-id="550b1-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="550b1-202">Bu örnek işlevi (kullanmak istediğiniz tam sertifika bulacaksınız şekilde özelleştirmek için olabilir) uygun yerel sertifika bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="550b1-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="550b1-203">Kendi parmak izi tarafından tanımlanan sertifikayla değeri kullanmak için yapılandırma komut dosyası güncelleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="550b1-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="550b1-204">Yapılandırmasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="550b1-204">Running the configuration</span></span>

<span data-ttu-id="550b1-205">Bu noktada, iki dosya çıkış yapılandırma çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="550b1-205">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="550b1-206">Bir \*. yerel Configuration Manager'ın yerel makine deposunda depolanır ve kendi parmak izi tarafından tanımlanan sertifikayı kullanarak kimlik bilgilerini şifresini yapılandırır meta.mof dosya.</span><span class="sxs-lookup"><span data-stu-id="550b1-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="550b1-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) Geçerli \*. meta.mof dosya.</span><span class="sxs-lookup"><span data-stu-id="550b1-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
 * <span data-ttu-id="550b1-208">Gerçekte yapılandırma uygulanır bir MOF dosyası.</span><span class="sxs-lookup"><span data-stu-id="550b1-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="550b1-209">Başlangıç DscConfiguration yapılandırmasını uygular.</span><span class="sxs-lookup"><span data-stu-id="550b1-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="550b1-210">Bu komutlar, bu adımları yapabiliriz:</span><span class="sxs-lookup"><span data-stu-id="550b1-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="550b1-211">Bu örnek DSC yapılandırması hedef düğüme gönderdiğiniz.</span><span class="sxs-lookup"><span data-stu-id="550b1-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="550b1-212">DSC yapılandırması da varsa bir DSC çekme sunucusuna kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="550b1-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="550b1-213">Bkz: [bir DSC çekme istemcisi kurarken](pullClient.md) DSC yapılandırmaları bir DSC çekme sunucusu kullanarak uygulama hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="550b1-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="550b1-214">Kimlik bilgisi şifreleme modülü örneği</span><span class="sxs-lookup"><span data-stu-id="550b1-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="550b1-215">Tüm adımları yanı sıra dışa aktarır ve ortak anahtarları kopyalar bir yardımcı cmdlet'i içeren tam bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="550b1-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```