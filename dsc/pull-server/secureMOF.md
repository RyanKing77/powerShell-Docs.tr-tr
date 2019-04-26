---
ms.date: 10/31/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MOF dosyasının güvenliğini sağlama
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079344"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="cd1bd-103">MOF dosyasının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="cd1bd-103">Securing the MOF File</span></span>

> <span data-ttu-id="cd1bd-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cd1bd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cd1bd-105">DSC, yerel Configuration Manager (LCM) istenen son durum burada uygulayan bir MOF dosyasında depolanan bilgileri uygulayarak sunucu düğümleri yapılandırılmasını yönetir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="cd1bd-106">Bu dosya yapılandırma ayrıntılarını içerdiği için güvenli kalmasını sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="cd1bd-107">Bu konu, hedef düğüm dosya şifrelenmiş sahip olmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="cd1bd-108">Düğümü kullanan uygulandığında sürüm 5.0 PowerShell ile başlayarak, tüm MOF dosyasının varsayılan olarak şifrelenmiş `Start-DSCConfiguration` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span>
<span data-ttu-id="cd1bd-109">Çekme Hizmeti protokolü kullanarak sertifikaları, hedef düğüm tarafından indirilen yapılandırmaları şifresi çözülür ve uygulanmadan önce sistem tarafından okunur emin olmak için yönetilmeyen bir çözümü uygularken bu makalede açıklanan işlemi gereklidir (örneğin, Windows Server'da kullanılabilir çekme hizmetini).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="cd1bd-110">Düğümleri kayıtlı [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) otomatik olarak sahip sertifikaların yüklü ve yönetim zahmetine ile hizmet tarafından yönetilen gerekli.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="cd1bd-111">Bu konu başlığı altında şifreleme için kullanılan sertifikaları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-111">This topic discusses certificates used for encryption.</span></span>
> <span data-ttu-id="cd1bd-112">Şifreleme için otomatik olarak imzalanan bir sertifika yeterlidir, özel anahtarı parola ve şifreleme her zaman tutulur çünkü güven belgenin anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
> <span data-ttu-id="cd1bd-113">Otomatik olarak imzalanan sertifikalar gereken *değil* kimlik doğrulama amaçlarıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
> <span data-ttu-id="cd1bd-114">Bir sertifika bir güvenilen sertifika yetkilisi (CA) öğesinden herhangi bir kimlik doğrulama amaçlarıyla kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd1bd-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cd1bd-115">Prerequisites</span></span>

<span data-ttu-id="cd1bd-116">Başarıyla bir DSC yapılandırması güvenliğini sağlamak için kullanılan kimlik bilgilerini şifrelemek için aşağıdakilere sahip olduğunuzdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="cd1bd-117">**Bazı araçlar, verme ve sertifikaları dağıtma**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="cd1bd-118">Bu konu ve alt örnekler Active Directory Sertifika yetkilisinin kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="cd1bd-119">Active Directory Sertifika Hizmetleri hakkında daha fazla bilgi için bkz. [Active Directory Sertifika Hizmetleri'ne Genel Bakış](https://technet.microsoft.com/library/hh831740.aspx) ve [Windows Server 2008'de Active Directory Sertifika Hizmetleri](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="cd1bd-120">**Hedef düğüm veya düğümler yönetici erişimi**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="cd1bd-121">**Her hedef düğüm kendi kişisel Store kaydedilen şifreleme özellikli bir sertifikası olan**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="cd1bd-122">Windows PowerShell'de depolama Cert: \LocalMachine\My yoludur.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="cd1bd-123">Bu konudaki örnekler (diğer sertifika şablonları ile birlikte) bulabilirsiniz "iş istasyonu kimlik doğrulaması" şablonu kullanma [varsayılan sertifika şablonlarını](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="cd1bd-124">Bu yapılandırma hedef düğümü dışında bir bilgisayarda çalışıyor olacak varsa **sertifikanın ortak anahtarını dışarı aktarmak**ve yapılandırmasından çalıştırılacağı bilgisayar alın.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="cd1bd-125">Yalnızca dışarı aktardığınızdan emin olun **genel** anahtar; özel anahtarı güvende tutun.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="cd1bd-126">Genel işlem</span><span class="sxs-lookup"><span data-stu-id="cd1bd-126">Overall process</span></span>

 1. <span data-ttu-id="cd1bd-127">Sertifikaları, anahtarları ve parmak izleri, sertifikanın bir kopyasını her hedef düğümü vardır ve parmak izi ve ortak anahtar yapılandırması bilgisayar olduğundan emin olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="cd1bd-128">Ortak anahtarın parmak izi ve yol içeren yapılandırma veri bloğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="cd1bd-129">Hedef düğüm için istediğiniz yapılandırmayı tanımlar ve hedef düğümleri üzerindeki şifre çözme yerel yapılandırma komut vermeye genel ayarlar bir yapılandırma betiği, sertifika parmak izi ile yapılandırma verilerin şifresini çözmek için Yöneticisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="cd1bd-130">Yerel Configuration Manager ayarlarını ve DSC yapılandırma başlatma Yapılandırması'nı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diyagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="cd1bd-132">Sertifika gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="cd1bd-132">Certificate Requirements</span></span>

<span data-ttu-id="cd1bd-133">Kimlik bilgilerinin şifrelenebilmesi uygulamak için bir ortak anahtar sertifikası kullanılabilir olmalıdır _hedef düğüm_ diğer bir deyişle **güvenilen** DSC yapılandırması yazmak için kullanılan bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="cd1bd-134">Bu ortak anahtar sertifikasını, DSC kimlik bilgilerinin şifrelenebilmesi için kullanılacak için belirli gereksinimler vardır:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="cd1bd-135">**Anahtar kullanımı**:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-135">**Key Usage**:</span></span>
   - <span data-ttu-id="cd1bd-136">İçermelidir: 'KeyEncipherment' ve 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="cd1bd-137">Gereken _değil_ içerir: 'Dijital imzası'.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="cd1bd-138">**Gelişmiş anahtar kullanımı**:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="cd1bd-139">İçermelidir: Belge Şifreleme (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="cd1bd-140">Gereken _değil_ içerir: İstemci kimlik doğrulaması (1.3.6.1.5.5.7.3.2) ve sunucu kimlik doğrulaması (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="cd1bd-141">Sertifikanın özel anahtarı kullanılabilir \* hedef Node_.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="cd1bd-142">**Sağlayıcısı** sertifika "Microsoft RSA SChannel Şifreleme Sağlayıcısı" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd1bd-143">Bir anahtar kullanımı 'Dijital imzası' ya da kimlik doğrulaması EKU'lar birini içeren ile bir sertifika kullanabilirsiniz, ancak bu daha kolay yanlış kullanılmış ve savunmasız saldırı olarak şifreleme anahtarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="cd1bd-144">Bu nedenle bu anahtar kullanımı ve EKU'larına atlar özellikle DSC kimlik bilgilerinin güvenliğini sağlama amacıyla oluşturulan bir sertifika kullanmak iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="cd1bd-145">Varolan bir sertifikayı üzerinde _hedef düğüm_ karşılaması için güvenli DSC kimlik bilgileri bu ölçütler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="cd1bd-146">Sertifika oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd1bd-146">Certificate creation</span></span>

<span data-ttu-id="cd1bd-147">Oluşturun ve gereken şifreleme sertifikasını (ortak-özel anahtar çifti) kullanmak için gerçekleştirebileceğiniz iki yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="cd1bd-148">Şirket oluşturma **hedef düğüm** ve yalnızca ortak anahtarını dışarı aktarma **geliştirme düğümü**</span><span class="sxs-lookup"><span data-stu-id="cd1bd-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="cd1bd-149">Şirket oluşturma **geliştirme düğümü** ve tüm anahtar çifti için dışarı aktarma **hedef düğüm**</span><span class="sxs-lookup"><span data-stu-id="cd1bd-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="cd1bd-150">Yöntem 1 MOF kimlik bilgileri şifresini çözmek için kullanılan özel anahtarı her zaman hedef düğümde kalacağından önerilir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="cd1bd-151">Hedef düğümde sertifika oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="cd1bd-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="cd1bd-152">Özel anahtarı üzerinde MOF şifresini çözmek için kullanılır çünkü gizli tutulması gereken **hedef düğüm** özel anahtar sertifikasını oluşturmak için bunu yapmanın en kolay yolu olan **hedef düğüm**ve kopyalama  **Ortak anahtar sertifikasını** DSC yapılandırma MOF dosyasına yazmak için kullanılan bilgisayarda.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="cd1bd-153">Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-153">The following example:</span></span>

1. <span data-ttu-id="cd1bd-154">bir sertifika oluşturur **hedef düğüm**</span><span class="sxs-lookup"><span data-stu-id="cd1bd-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="cd1bd-155">üzerinde ortak anahtar sertifikasını dışa aktarır **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="cd1bd-156">Ortak anahtar sertifikası olarak içeri aktarır **my** sertifika deposunda imzalanırsa **yazma düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="cd1bd-157">Hedef düğümde: oluşturma ve sertifikayı dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="cd1bd-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="cd1bd-158">Hedef düğüm: Windows Server 2016 ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="cd1bd-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="cd1bd-159">Bir kez dışarı aktarılan `DscPublicKey.cer` kopyalanması gereken **geliştirme düğümü**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="cd1bd-160">Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd1bd-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="cd1bd-161">Çünkü `New-SelfSignedCertificate` cmdlet'i üzerinde Windows işletim sistemleri Windows 10 ve Windows Server 2016 öncesinde desteklemez **türü** bu işletim sistemlerinde bu sertifikayı oluşturmak için alternatif bir yöntem parametresi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="cd1bd-162">Bu durumda kullanabileceğiniz `makecert.exe` veya `certutil.exe` sertifikayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
><span data-ttu-id="cd1bd-163">Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiği indirin](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifika oluşturmak için bunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="cd1bd-164">Bir kez dışarı aktarılan ```DscPublicKey.cer``` kopyalanması gereken **geliştirme düğümü**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="cd1bd-165">Yazma düğümde: cert'ın ortak anahtar içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="cd1bd-165">On the Authoring Node: import the cert’s public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="cd1bd-166">Yazma düğümde sertifika oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="cd1bd-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="cd1bd-167">Alternatif olarak, şifreleme sertifikası üzerinde oluşturulabilir **geliştirme düğümü**, dışarı aktarılan ile **özel anahtarı** bir PFX dosyasını ve ardından alındığı **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="cd1bd-168">DSC kimlik bilgisi şifreleme uygulama için geçerli bir yöntem budur _Nano sunucu_.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="cd1bd-169">PFX bir parolayla güvenli olsa da, güvenli aktarım sırasında tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="cd1bd-170">Aşağıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-170">The following example:</span></span>

1. <span data-ttu-id="cd1bd-171">bir sertifika oluşturur **yazma düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="cd1bd-172">özel anahtar dahil olmak üzere sertifikayı dışarı aktaran **yazma düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="cd1bd-173">özel anahtarı kaldırır **yazma düğüm**, ancak ortak anahtar sertifikası tutar **my** depolayın.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="cd1bd-174">özel anahtar sertifikasını, üzerinde My(Personal) sertifika deposuna aktarır. **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="cd1bd-175">Böylece tarafından güvenilecek, kök deposuna eklenmelidir **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="cd1bd-176">Yazma düğümde: oluşturma ve sertifikayı dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="cd1bd-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="cd1bd-177">Hedef düğüm: Windows Server 2016 ve Windows 10</span><span class="sxs-lookup"><span data-stu-id="cd1bd-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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

<span data-ttu-id="cd1bd-178">Bir kez dışarı aktarılan `DscPrivateKey.pfx` kopyalanması gereken **hedef düğüm**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="cd1bd-179">Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="cd1bd-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="cd1bd-180">Çünkü `New-SelfSignedCertificate` cmdlet'i üzerinde Windows işletim sistemleri Windows 10 ve Windows Server 2016 öncesinde desteklemez **türü** bu işletim sistemlerinde bu sertifikayı oluşturmak için alternatif bir yöntem parametresi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="cd1bd-181">Bu durumda kullanabileceğiniz `makecert.exe` veya `certutil.exe` sertifikayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
> <span data-ttu-id="cd1bd-182">Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiği indirin](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifika oluşturmak için bunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="cd1bd-183">Hedef düğümde: olarak güvenilen bir kök sertifikası'nın özel anahtarını içeri aktarın</span><span class="sxs-lookup"><span data-stu-id="cd1bd-183">On the Target Node: import the cert’s private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="cd1bd-184">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="cd1bd-184">Configuration data</span></span>

<span data-ttu-id="cd1bd-185">Hangi hedef düğümler olup olmadığına göre çalıştırmak veya kimlik bilgilerini şifreleme anlamına gelir ve diğer bilgileri şifrelenmez için yapılandırma veri bloğu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="cd1bd-186">Yapılandırma veri bloğu hakkında daha fazla bilgi için bkz. [ayırarak yapılandırma ve ortam verilerini](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="cd1bd-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="cd1bd-187">Kimlik bilgisi şifreleme için ilgili her düğüm için yapılandırılabilir öğeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="cd1bd-188">**NodeName** -kimlik bilgilerinin şifrelenebilmesi için yapılandırılan hedef düğümün adı.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="cd1bd-189">**PsDscAllowPlainTextPassword** - şifrelenmemiş kimlik bu düğümü için geçirilecek izin verilmediğini.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="cd1bd-190">Bu **önerilmez**.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-190">This is **not recommended**.</span></span>
- <span data-ttu-id="cd1bd-191">**Parmak izi** -şirket kimlik bilgilerini DSC yapılandırması şifresini çözmek için kullanılan sertifikanın parmak izini _hedef düğüm_.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="cd1bd-192">**Bu sertifika, hedef düğümde yerel makine sertifika deposunda bulunmalıdır.**</span><span class="sxs-lookup"><span data-stu-id="cd1bd-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="cd1bd-193">**CertificateFile** - sertifika dosyasını (ortak anahtarı içerir) için kimlik bilgilerini şifrelemek için kullanılmalıdır _hedef düğüm_.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="cd1bd-194">Bu olmalıdır bir DER kodlu ikili X.509 veya Base-64 kodlanmış X.509 biçimi sertifika dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="cd1bd-195">Bu örnek, adlandırılmış targetNode, yolunu (targetNode.cer adlı) ortak anahtar sertifika dosyası ve ortak anahtarın parmak izini üzerinde yapacak bir hedef düğümü belirten yapılandırma veri bloğu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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

## <a name="configuration-script"></a><span data-ttu-id="cd1bd-196">Yapılandırma betiği</span><span class="sxs-lookup"><span data-stu-id="cd1bd-196">Configuration script</span></span>

<span data-ttu-id="cd1bd-197">Yapılandırma betiği kendisi, `PsCredential` en kısa sürede için depolanan kimlik bilgileri sağlamak için parametre.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="cd1bd-198">Sağlanan örnek çalıştırdığınızda, DSC kimlik bilgilerinizi ister ve ardından yapılandırma veri bloğu içindeki hedef düğümle ilişkilendirilen CertificateFile kullanarak MOF dosyasını şifreleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="cd1bd-199">Bu kod örneği, bir kullanıcıya güvenli bir paylaşımından bir dosyayı kopyalar.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-199">This code example copies a file from a share that is secured to a user.</span></span>

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
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="cd1bd-200">Şifre çözme ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd1bd-200">Setting up decryption</span></span>

<span data-ttu-id="cd1bd-201">Önce [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) çalışabilir, sertifikanın parmak izi doğrulamak için CertificateID kaynak kullanarak yerel Configuration Manager her bir hedef düğümde hangi sertifikanın kimlik bilgilerinin şifresini çözmek için kullanılacağını söyleyin zorunda.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="cd1bd-202">Bu örnek işlevi (kullanmak istediğiniz tam sertifika bulabilirsiniz, özelleştirmek gerekebilir) uygun yerel sertifika bulacaksınız:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="cd1bd-203">Sertifikanın parmak izi tarafından tanımlanan yapılandırma betiğini değerini kullanmak için güncelleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="cd1bd-204">Bir yapılandırmayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cd1bd-204">Running the configuration</span></span>

<span data-ttu-id="cd1bd-205">Bu noktada, iki dosya çıkarır yapılandırması, çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="cd1bd-206">Bir \*. yerel makine deposunda depolanır ve parmak izi tarafından tanımlanan sertifikayı kullanan kimlik bilgilerinin şifresini çözmek için yerel Configuration Manager'ı yapılandıran oluşturduğunuzdan dosya.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="cd1bd-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) Geçerli \*. oluşturduğunuzdan dosya.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="cd1bd-208">Yapılandırmayı uygulayan bir MOF dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="cd1bd-209">Start-DscConfiguration yapılandırmasını uygular.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="cd1bd-210">Bu komutlar bu adımları yerine getirmiş olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="cd1bd-211">Bu örnekte, hedef düğüme DSC yapılandırması gönderir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="cd1bd-212">DSC yapılandırması varsa, bir DSC çekme sunucusuna kullanarak da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="cd1bd-213">Bkz: [DSC çekme istemcisi ayarlama](pullClient.md) DSC yapılandırmaları bir DSC çekme sunucusu kullanarak uygulama hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="cd1bd-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="cd1bd-214">Kimlik bilgisi şifreleme modülü örneği</span><span class="sxs-lookup"><span data-stu-id="cd1bd-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="cd1bd-215">Tüm adımları yanı sıra, dışa aktarır ve ortak anahtarları kopyalar bir yardımcı cmdlet'i içeren tam bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cd1bd-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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
