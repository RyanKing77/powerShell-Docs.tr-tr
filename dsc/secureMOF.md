---
ms.date: 10/31/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MOF dosyasının güvenliğini sağlama
ms.openlocfilehash: f17c95c951151c0c11057ac0bce172c4ec73c91d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893272"
---
# <a name="securing-the-mof-file"></a>MOF dosyasının güvenliğini sağlama

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC, yerel Configuration Manager (LCM) istenen son durum burada uygulayan bir MOF dosyasında depolanan bilgileri uygulayarak sunucu düğümleri yapılandırılmasını yönetir.
Bu dosya yapılandırma ayrıntılarını içerdiği için güvenli kalmasını sağlamak önemlidir.
Bu konu, hedef düğüm dosya şifrelenmiş sahip olmak açıklar.

Düğümü kullanan uygulandığında sürüm 5.0 PowerShell ile başlayarak, tüm MOF dosyasının varsayılan olarak şifrelenmiş `Start-DSCConfiguration` cmdlet'i.
Çekme Hizmeti protokolü kullanarak sertifikaları, hedef düğüm tarafından indirilen yapılandırmaları şifresi çözülür ve uygulanmadan önce sistem tarafından okunur emin olmak için yönetilmeyen bir çözümü uygularken bu makalede açıklanan işlemi gereklidir (örneğin, Windows Server'da kullanılabilir çekme hizmetini).
Düğümleri kayıtlı [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) otomatik olarak sahip sertifikaların yüklü ve yönetim zahmetine ile hizmet tarafından yönetilen gerekli.

> [!NOTE]
> Bu konu başlığı altında şifreleme için kullanılan sertifikaları açıklanır.
> Şifreleme için otomatik olarak imzalanan bir sertifika yeterlidir, özel anahtarı parola ve şifreleme her zaman tutulur çünkü güven belgenin anlamına gelmez.
> Otomatik olarak imzalanan sertifikalar gereken *değil* kimlik doğrulama amaçlarıyla kullanılabilir.
> Bir sertifika bir güvenilen sertifika yetkilisi (CA) öğesinden herhangi bir kimlik doğrulama amaçlarıyla kullanmanız gerekir.

## <a name="prerequisites"></a>Önkoşullar

Başarıyla bir DSC yapılandırması güvenliğini sağlamak için kullanılan kimlik bilgilerini şifrelemek için aşağıdakilere sahip olduğunuzdan emin olun:

- **Bazı araçlar, verme ve sertifikaları dağıtma**. Bu konu ve alt örnekler Active Directory Sertifika yetkilisinin kullandığınız varsayılır. Active Directory Sertifika Hizmetleri hakkında daha fazla bilgi için bkz. [Active Directory Sertifika Hizmetleri'ne Genel Bakış](https://technet.microsoft.com/library/hh831740.aspx) ve [Windows Server 2008'de Active Directory Sertifika Hizmetleri](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Hedef düğüm veya düğümler yönetici erişimi**.
- **Her hedef düğüm kendi kişisel Store kaydedilen şifreleme özellikli bir sertifikası olan**. Windows PowerShell'de depolama Cert: \LocalMachine\My yoludur. Bu konudaki örnekler (diğer sertifika şablonları ile birlikte) bulabilirsiniz "iş istasyonu kimlik doğrulaması" şablonu kullanma [varsayılan sertifika şablonlarını](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Bu yapılandırma hedef düğümü dışında bir bilgisayarda çalışıyor olacak varsa **sertifikanın ortak anahtarını dışarı aktarmak**ve yapılandırmasından çalıştırılacağı bilgisayar alın. Yalnızca dışarı aktardığınızdan emin olun **genel** anahtar; özel anahtarı güvende tutun.

## <a name="overall-process"></a>Genel işlem

 1. Sertifikaları, anahtarları ve parmak izleri, sertifikanın bir kopyasını her hedef düğümü vardır ve parmak izi ve ortak anahtar yapılandırması bilgisayar olduğundan emin olarak ayarlayın.
 2. Ortak anahtarın parmak izi ve yol içeren yapılandırma veri bloğu oluşturun.
 3. Hedef düğüm için istediğiniz yapılandırmayı tanımlar ve hedef düğümleri üzerindeki şifre çözme yerel yapılandırma komut vermeye genel ayarlar bir yapılandırma betiği, sertifika parmak izi ile yapılandırma verilerin şifresini çözmek için Yöneticisi oluşturun.
 4. Yerel Configuration Manager ayarlarını ve DSC yapılandırma başlatma Yapılandırması'nı çalıştırın.

![Diyagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Sertifika gereksinimleri

Kimlik bilgilerinin şifrelenebilmesi uygulamak için bir ortak anahtar sertifikası kullanılabilir olmalıdır _hedef düğüm_ diğer bir deyişle **güvenilen** DSC yapılandırması yazmak için kullanılan bilgisayar.
Bu ortak anahtar sertifikasını, DSC kimlik bilgilerinin şifrelenebilmesi için kullanılacak için belirli gereksinimler vardır:

1. **Anahtar kullanımı**:
   - İçermelidir: 'KeyEncipherment' ve 'DataEncipherment'.
   - Gereken _değil_ içeriyor: 'Dijital imzası'.
2. **Gelişmiş anahtar kullanımı**:
   - İçermelidir: belge şifreleme (1.3.6.1.4.1.311.80.1).
   - Gereken _değil_ içeriyor: istemci kimlik doğrulaması (1.3.6.1.5.5.7.3.2) ve sunucu kimlik doğrulaması (1.3.6.1.5.5.7.3.1).
3. Sertifikanın özel anahtarı kullanılabilir * hedef Node_.
4. **Sağlayıcısı** sertifika "Microsoft RSA SChannel Şifreleme Sağlayıcısı" olmalıdır.

> [!IMPORTANT]
> Bir anahtar kullanımı 'Dijital imzası' ya da kimlik doğrulaması EKU'lar birini içeren ile bir sertifika kullanabilirsiniz, ancak bu daha kolay yanlış kullanılmış ve savunmasız saldırı olarak şifreleme anahtarını etkinleştirir. Bu nedenle bu anahtar kullanımı ve EKU'larına atlar özellikle DSC kimlik bilgilerinin güvenliğini sağlama amacıyla oluşturulan bir sertifika kullanmak iyi bir uygulamadır.

Varolan bir sertifikayı üzerinde _hedef düğüm_ karşılaması için güvenli DSC kimlik bilgileri bu ölçütler kullanılabilir.

## <a name="certificate-creation"></a>Sertifika oluşturma

Oluşturun ve gereken şifreleme sertifikasını (ortak-özel anahtar çifti) kullanmak için gerçekleştirebileceğiniz iki yaklaşım vardır.

1. Şirket oluşturma **hedef düğüm** ve yalnızca ortak anahtarını dışarı aktarma **geliştirme düğümü**
2. Şirket oluşturma **geliştirme düğümü** ve tüm anahtar çifti için dışarı aktarma **hedef düğüm**

Yöntem 1 MOF kimlik bilgileri şifresini çözmek için kullanılan özel anahtarı her zaman hedef düğümde kalacağından önerilir.

### <a name="creating-the-certificate-on-the-target-node"></a>Hedef düğümde sertifika oluşturuluyor

Özel anahtarı üzerinde MOF şifresini çözmek için kullanılır çünkü gizli tutulması gereken **hedef düğüm** özel anahtar sertifikasını oluşturmak için bunu yapmanın en kolay yolu olan **hedef düğüm**ve kopyalama  **Ortak anahtar sertifikasını** DSC yapılandırma MOF dosyasına yazmak için kullanılan bilgisayarda.
Aşağıdaki örnekte:

1. bir sertifika oluşturur **hedef düğüm**
2. üzerinde ortak anahtar sertifikasını dışa aktarır **hedef düğüm**.
3. Ortak anahtar sertifikası olarak içeri aktarır **my** sertifika deposunda imzalanırsa **yazma düğüm**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>Hedef düğümde: oluşturma ve sertifikayı dışarı aktarma

> Hedef düğüm: Windows Server 2016 ve Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

Bir kez dışarı aktarılan `DscPublicKey.cer` kopyalanması gereken **geliştirme düğümü**.

> Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri
> [!WARNING]
> Çünkü `New-SelfSignedCertificate` cmdlet'i üzerinde Windows işletim sistemleri Windows 10 ve Windows Server 2016 öncesinde desteklemez **türü** bu işletim sistemlerinde bu sertifikayı oluşturmak için alternatif bir yöntem parametresi gereklidir.
>
> Bu durumda kullanabileceğiniz `makecert.exe` veya `certutil.exe` sertifikayı oluşturmak için.
>
>Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiği indirin](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifika oluşturmak için bunu kullanın:

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

Bir kez dışarı aktarılan ```DscPublicKey.cer``` kopyalanması gereken **geliştirme düğümü**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>Yazma düğümde: cert'ın ortak anahtar içeri aktarma

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Yazma düğümde sertifika oluşturuluyor

Alternatif olarak, şifreleme sertifikası üzerinde oluşturulabilir **geliştirme düğümü**, dışarı aktarılan ile **özel anahtarı** bir PFX dosyasını ve ardından alındığı **hedef düğüm**.
DSC kimlik bilgisi şifreleme uygulama için geçerli bir yöntem budur _Nano sunucu_.
PFX bir parolayla güvenli olsa da, güvenli aktarım sırasında tutulmalıdır.
Aşağıdaki örnekte:

1. bir sertifika oluşturur **yazma düğüm**.
2. özel anahtar dahil olmak üzere sertifikayı dışarı aktaran **yazma düğüm**.
3. özel anahtarı kaldırır **yazma düğüm**, ancak ortak anahtar sertifikası tutar **my** depolayın.
4. özel anahtar sertifikasını, üzerinde My(Personal) sertifika deposuna aktarır. **hedef düğüm**.
   - Böylece tarafından güvenilecek, kök deposuna eklenmelidir **hedef düğüm**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>Yazma düğümde: oluşturma ve sertifikayı dışarı aktarma

> Hedef düğüm: Windows Server 2016 ve Windows 10

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

Bir kez dışarı aktarılan `DscPrivateKey.pfx` kopyalanması gereken **hedef düğüm**.

> Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri
> [!WARNING]
> Çünkü `New-SelfSignedCertificate` cmdlet'i üzerinde Windows işletim sistemleri Windows 10 ve Windows Server 2016 öncesinde desteklemez **türü** bu işletim sistemlerinde bu sertifikayı oluşturmak için alternatif bir yöntem parametresi gereklidir.
>
> Bu durumda kullanabileceğiniz `makecert.exe` veya `certutil.exe` sertifikayı oluşturmak için.
>
> Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiği indirin](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifika oluşturmak için bunu kullanın:

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>Hedef düğümde: olarak güvenilen bir kök sertifikası'nın özel anahtarını içeri aktarın

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Yapılandırma verileri

Hangi hedef düğümler olup olmadığına göre çalıştırmak veya kimlik bilgilerini şifreleme anlamına gelir ve diğer bilgileri şifrelenmez için yapılandırma veri bloğu tanımlar. Yapılandırma veri bloğu hakkında daha fazla bilgi için bkz. [ayırarak yapılandırma ve ortam verilerini](configData.md).

Kimlik bilgisi şifreleme için ilgili her düğüm için yapılandırılabilir öğeler şunlardır:

- **NodeName** -kimlik bilgilerinin şifrelenebilmesi için yapılandırılan hedef düğümün adı.
- **PsDscAllowPlainTextPassword** - şifrelenmemiş kimlik bu düğümü için geçirilecek izin verilmediğini. Bu **önerilmez**.
- **Parmak izi** -şirket kimlik bilgilerini DSC yapılandırması şifresini çözmek için kullanılan sertifikanın parmak izini _hedef düğüm_. **Bu sertifika, hedef düğümde yerel makine sertifika deposunda bulunmalıdır.**
- **CertificateFile** - sertifika dosyasını (ortak anahtarı içerir) için kimlik bilgilerini şifrelemek için kullanılmalıdır _hedef düğüm_. Bu olmalıdır bir DER kodlu ikili X.509 veya Base-64 kodlanmış X.509 biçimi sertifika dosyası.

Bu örnek, adlandırılmış targetNode, yolunu (targetNode.cer adlı) ortak anahtar sertifika dosyası ve ortak anahtarın parmak izini üzerinde yapacak bir hedef düğümü belirten yapılandırma veri bloğu gösterir.

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

## <a name="configuration-script"></a>Yapılandırma betiği

Yapılandırma betiği kendisi, `PsCredential` en kısa sürede için depolanan kimlik bilgileri sağlamak için parametre. Sağlanan örnek çalıştırdığınızda, DSC kimlik bilgilerinizi ister ve ardından yapılandırma veri bloğu içindeki hedef düğümle ilişkilendirilen CertificateFile kullanarak MOF dosyasını şifreleyebilir. Bu kod örneği, bir kullanıcıya güvenli bir paylaşımından bir dosyayı kopyalar.

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

## <a name="setting-up-decryption"></a>Şifre çözme ayarlama

Önce [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) çalışabilir, sertifikanın parmak izi doğrulamak için CertificateID kaynak kullanarak yerel Configuration Manager her bir hedef düğümde hangi sertifikanın kimlik bilgilerinin şifresini çözmek için kullanılacağını söyleyin zorunda. Bu örnek işlevi (kullanmak istediğiniz tam sertifika bulabilirsiniz, özelleştirmek gerekebilir) uygun yerel sertifika bulacaksınız:

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

Sertifikanın parmak izi tarafından tanımlanan yapılandırma betiğini değerini kullanmak için güncelleştirilebilir:

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

## <a name="running-the-configuration"></a>Bir yapılandırmayı çalıştırma

Bu noktada, iki dosya çıkarır yapılandırması, çalıştırabilirsiniz:

- Bir *. yerel makine deposunda depolanır ve parmak izi tarafından tanımlanan sertifikayı kullanan kimlik bilgilerinin şifresini çözmek için yerel Configuration Manager'ı yapılandıran oluşturduğunuzdan dosya. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) Geçerli *. oluşturduğunuzdan dosya.
- Yapılandırmayı uygulayan bir MOF dosyası. Start-DscConfiguration yapılandırmasını uygular.

Bu komutlar bu adımları yerine getirmiş olacaksınız:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Bu örnekte, hedef düğüme DSC yapılandırması gönderir.
DSC yapılandırması varsa, bir DSC çekme sunucusuna kullanarak da uygulanabilir.

Bkz: [DSC çekme istemcisi ayarlama](pullClient.md) DSC yapılandırmaları bir DSC çekme sunucusu kullanarak uygulama hakkında daha fazla bilgi için.

## <a name="credential-encryption-module-example"></a>Kimlik bilgisi şifreleme modülü örneği

Tüm adımları yanı sıra, dışa aktarır ve ortak anahtarları kopyalar bir yardımcı cmdlet'i içeren tam bir örnek aşağıda verilmiştir:

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