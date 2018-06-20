---
ms.date: 10/31/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MOF dosyası güvenliğini sağlama
ms.openlocfilehash: d6f213e497838192ca6ce8d537cc291ee3811e79
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190205"
---
# <a name="securing-the-mof-file"></a>MOF dosyası güvenliğini sağlama

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC yapılandırma sunucusu düğümlerinin burada yerel Configuration Manager (LCM'yi) istenen son durum uygulayan bir MOF dosyasında depolanan bilgileri uygulayarak yönetir.
Bu dosya yapılandırma ayrıntılarını içerdiğinden, güvenli tutmak önemlidir.
Bu konuda, hedef düğüm dosya şifrelenmiş sahip olmak açıklar.

Düğüm kullanmaya uygulandığında sürüm 5.0 PowerShell ile başlayarak, tüm MOF dosyası varsayılan olarak şifrelenmiş **başlangıç DSCConfiguration** cmdlet'i.
Bu makalede açıklanan işlemi yalnızca Sertifikalar, hedef düğüm tarafından indirilen yapılandırmaları şifresi çözülür ve uygulanmadan önce sistem tarafından okunur emin olmak için yönetilmeyen çekme hizmet protokolünü kullanarak bir çözüm uygulama gereklidir (örneğin, çekme hizmeti Windows Server'da kullanılabilir).
Düğümleri kayıtlı için [Azure Otomasyonu DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) otomatik olarak sahip sertifikaları yüklü ve hiçbir yönetim yükü ile hizmet yöneten gerekli.

>**Not:** şifreleme için kullanılan sertifikaları bu konuda ele alınmıştır.
>Şifreleme için otomatik olarak imzalanan bir sertifika yeterlidir, özel anahtarı her zaman gizli anahtar ve şifreleme tutulduğundan belgenin güven anlamına gelmez.
>Otomatik olarak imzalanan sertifikalar gereken *değil* kimlik doğrulama amacıyla kullanılabilir.
>Tüm kimlik doğrulama amacıyla bir sertifika bir güvenilen sertifika yetkilisi (CA) gelen kullanmanız gerekir.

## <a name="prerequisites"></a>Önkoşullar

Başarıyla bir DSC yapılandırma güvenliğini sağlamak için kullanılan kimlik bilgilerini şifrelemek için aşağıdakilere sahip olduğunuzdan emin olun:

* **Bazı şekillerini vermek ve sertifikaları dağıtma**. Bu konu ve onun örnekler Active Directory Sertifika yetkilisi kullandığınız varsayılır. Active Directory Sertifika Hizmetleri hakkında daha fazla bilgi için bkz: [Active Directory Sertifika Hizmetleri'ne Genel Bakış](https://technet.microsoft.com/library/hh831740.aspx) ve [Windows Server 2008'de Active Directory Sertifika Hizmetleri](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Hedef düğüm veya düğümler yönetim erişimi**.
* **Her hedef düğüm, Kişisel depolama kaydedilmiş şifreleme özellikli bir sertifikaya sahip**. Windows PowerShell'de depolama Cert: \LocalMachine\My yoludur. Bu konudaki örnekler adresindeki (yanı sıra diğer sertifika şablonlarını) bulabilirsiniz "iş istasyonu kimlik doğrulaması" şablonu kullanmak [varsayılan sertifika şablonları](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Bu yapılandırma hedef düğüm dışında bir bilgisayarda çalıştıracaksanız **sertifikanın ortak anahtarını dışarı aktarmak**ve yapılandırmasından çalışacağı bilgisayarda alın. Yalnızca dışarı emin olun **ortak** özel anahtarı güvenli tutmaya; anahtarı.

## <a name="overall-process"></a>Genel işlem

 1. Sertifikalar, anahtarları ve parmak izleri, sertifikanın kopyasını her hedef düğüme sahiptir ve ortak anahtar ve parmak izi yapılandırma bilgisayarın olduğundan emin olarak ayarlayın.
 2. Parmak izi ortak anahtar ve yolunu içeren bir yapılandırma veri bloğu oluşturun.
 3. Hedef düğüm için istenen yapılandırmanızı tanımlar ve yerel yapılandırma komut verme hedef düğümleri şifre çözme ayarlar bir yapılandırma komut dosyası sertifika ve kendi parmak izini kullanarak yapılandırma verilerin şifresini çözmek için Yöneticisi oluşturun.
 4. Yerel Configuration Manager ayarlar ve DSC yapılandırması başlangıç yapılandırması çalıştırın.

![Diyagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Sertifika gereksinimleri

Kimlik bilgisi şifreleme kabul etmek için bir ortak anahtar sertifikası kullanılabilir olmalıdır _hedef düğüm_ diğer bir deyişle **güvenilen** DSC yapılandırması yazmak için kullanılan bilgisayar tarafından.
Bu ortak anahtar sertifikası için bu DSC kimlik bilgisi şifreleme için kullanılacak belirli gereksinimlere sahiptir:
 1. **Anahtar kullanımı**:
   - İçermelidir: 'KeyEncipherment' ve 'DataEncipherment'.
   - Gereken _değil_ içeriyor: 'Dijital imza'.
 2. **Gelişmiş anahtar kullanımı**:
   - İçermelidir: belge şifreleme (1.3.6.1.4.1.311.80.1).
   - Gereken _değil_ içerir: istemci kimlik doğrulaması (1.3.6.1.5.5.7.3.2) ve sunucu kimlik doğrulaması (1.3.6.1.5.5.7.3.1).
 3. Sertifikanın özel anahtarı kullanılabilir * hedef Node_.
 4. **Sağlayıcı** sertifika "Microsoft RSA SChannel Şifreleme Sağlayıcısı" olmalıdır.

>**Önerilen en iyi yöntem:** anahtar kullanımı 'Dijital imza' ya da kimlik doğrulama EKU'lar birini içeren ile bir sertifika kullanabilirsiniz, ancak bu yanlış kullanılmış ve karşı savunmasız saldırı şifreleme anahtarının daha kolay olanak tanır. Bu nedenle bu anahtar kullanımı ve EKU atlar özellikle DSC kimlik bilgilerini korumak amacıyla oluşturulan bir sertifika kullanmak en iyi bir uygulamadır.

Varolan bir sertifikayı üzerinde _hedef düğüm_ karşılaması için güvenli DSC kimlik bilgileri bu ölçütler kullanılabilir.

## <a name="certificate-creation"></a>Sertifika oluşturma

Gerekli şifreleme sertifikası (genel-özel anahtar çifti) oluşturmak için uygulayabileceğiniz iki yaklaşım vardır.

1. Üzerinde oluşturulduğu **hedef düğüm** ve yalnızca ortak anahtarını dışarı aktarma **yazma düğümü**
2. Üzerinde oluşturulduğu **yazma düğümü** ve tüm anahtar çifti verme **hedef düğüm**

Yöntem 1 MOF kimlik bilgilerini şifrelemek için kullanılan özel anahtarı her zaman hedef düğümde kalır nedeniyle önerilir.


### <a name="creating-the-certificate-on-the-target-node"></a>Hedef düğümde sertifika oluşturma

Özel anahtarı üzerinde MOF şifresini çözmek için kullanılır çünkü gizli tutulması gereken **hedef düğüm** özel anahtar sertifikasını oluşturmak için bunu yapmanın en kolay yolu olan **hedef düğüm**ve kopyalama  **Ortak anahtar sertifikası** DSC yapılandırması bir MOF dosyasına yazmak için kullanılan bilgisayara.
Aşağıdaki örnek:
 1. bir sertifika oluşturur **hedef düğüm**
 2. üzerinde ortak anahtar sertifikası dışarı aktarmaları **hedef düğüm**.
 3. Ortak anahtar sertifikası içine alır **my** sertifika deposunda **yazma düğümü**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>Hedef düğümde bulunan: oluşturma ve sertifika verme
>Hedef düğüm: Windows Server 2016 ve Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Bir kez dışarı ```DscPublicKey.cer``` kopyalanması gerekir **yazma düğümü**.

>Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri

Üzerinde Windows işletim sistemlerinin Windows 10 ve Windows Server 2016 önce yeni SelfSignedCertificate cmdlet desteklemez çünkü **türü** parametresi, bu sertifika oluşturma alternatif bir yöntem bunları gereklidir işletim sistemleri.
Bu durumda kullanabileceğiniz ```makecert.exe``` veya ```certutil.exe``` bir sertifika oluşturmak için.

Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiğini indir](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifikayı oluşturmak için kullanın:
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
Bir kez dışarı ```DscPublicKey.cer``` kopyalanması gerekir **yazma düğümü**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>Yazma düğümde: sertifika ait ortak anahtarı alma
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Geliştirme düğümde sertifika oluşturma
Alternatif olarak, şifreleme sertifikası üzerinde oluşturulabilir **yazma düğümü**, dışarı aktarılan ile **özel anahtarı** bir PFX dosyası ve ardından alındığı **hedef düğüm**.
Bu, DSC kimlik bilgisi şifreleme uygulama için geçerli yöntemdir _Nano Server_.
PFX güvenli bir parola ile olsa da, güvenli aktarım sırasında tutulmalıdır.
Aşağıdaki örnek:
 1. bir sertifika oluşturur **yazma düğümü**.
 2. özel anahtar dahil olmak üzere sertifika dışa aktarır **yazma düğümü**.
 3. özel anahtardan kaldırır **yazma düğümü**, ancak ortak anahtar sertifikası tutar **my** depolar.
 4. özel anahtar sertifikasını, üzerinde My(Personal) sertifika deposuna aktarır **hedef düğüm**.
   - Böylece tarafından güvenilecek, kök deposuna eklenmelidir **hedef düğüm**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>Yazma düğümde: oluşturma ve sertifika verme
>Hedef düğüm: Windows Server 2016 ve Windows 10

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
Bir kez dışarı ```DscPrivateKey.pfx``` kopyalanması gerekir **hedef düğüm**.

>Hedef düğüm: Windows Server 2012 R2/Windows 8.1 ve önceki sürümleri

Üzerinde Windows işletim sistemlerinin Windows 10 ve Windows Server 2016 önce yeni SelfSignedCertificate cmdlet desteklemez çünkü **türü** parametresi, bu sertifika oluşturma alternatif bir yöntem bunları gereklidir işletim sistemleri.
Bu durumda kullanabileceğiniz ```makecert.exe``` veya ```certutil.exe``` bir sertifika oluşturmak için.

Alternatif bir yöntem [Microsoft Script Center yeni SelfSignedCertificateEx.ps1 betiğini indir](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) ve bunun yerine sertifikayı oluşturmak için kullanın:
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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>Hedef düğümde bulunan: olarak güvenilir bir kök sertifikası'nın özel anahtar alma
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Yapılandırma verileri

Yapılandırma veri bloğu hangi hedef düğümleri olup olmadığına göre çalıştırmak veya kimlik bilgileri, şifreleme anlamına gelir ve diğer bilgileri şifrelenmez tanımlar. Yapılandırma veri bloğu hakkında daha fazla bilgi için bkz: [ayırarak yapılandırma ve ortam verilerini](configData.md).

Kimlik bilgisi şifreleme için ilgili her düğüm için yapılandırılmış olan öğeler şunlardır:
* **NodeName** -kimlik bilgilerinin şifrelenebilmesi yapılandırılmış hedef düğümün adı.
* **PsDscAllowPlainTextPassword** - şifrelenmemiş kimlik bilgileri bu düğüme geçirilmesi izin verilmeyeceğini. Bu **önerilmez**.
* **Parmak izi** -üzerinde DSC Yapılandırması'ndaki kimlik bilgilerini şifrelemek için kullanılan sertifikanın parmak izini _hedef düğüm_. **Bu sertifika, hedef düğümde bulunan yerel makine sertifika deposunda bulunmalıdır.**
* **CertificateFile** - (yalnızca ortak anahtarı içeren) sertifika dosyası için kimlik bilgilerini şifrelemek için kullanılacak _hedef düğüm_. Bu da olmalıdır bir DER ile kodlanmış ikili X.509 veya Base-64 kodlanmış X.509 biçimi sertifika dosyası.

Bu örnek, görev yapması için bir hedef düğümü adlandırılmış targetNode, ortak anahtar sertifika dosyasından (targetNode.cer adlı) ve ortak anahtar parmak izini yolunu belirtir. bir yapılandırma veri bloğu gösterir.

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


## <a name="configuration-script"></a>Yapılandırma komut dosyası

Yapılandırma betiği içinde kendisi, `PsCredential` en kısa sürede için depolanan kimlik bilgileri sağlamak için parametre. Sağlanan örnek çalıştırdığınızda, DSC kimlik bilgilerini ister ve yapılandırma veri bloğundaki hedef düğümle ilişkili CertificateFile kullanarak MOF dosyasını şifrelemek. Bu kod örneği bir dosyayı güvenli bir paylaşımdan bir kullanıcıya kopyalar.

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

## <a name="setting-up-decryption"></a>Şifre çözme ayarlama

Önce [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) çalışabilir, sertifikanın parmak izi doğrulamak için CertificateID kaynak kullanarak kimlik bilgileri şifresini çözmek için kullanılacak hangi sertifikanın her bir hedef düğümde yerel Configuration Manager söyleyin zorunda. Bu örnek işlevi (kullanmak istediğiniz tam sertifika bulacaksınız şekilde özelleştirmek için olabilir) uygun yerel sertifika bulacaksınız:

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

Kendi parmak izi tarafından tanımlanan sertifikayla değeri kullanmak için yapılandırma komut dosyası güncelleştirilebilir:

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

## <a name="running-the-configuration"></a>Yapılandırmasını çalıştırma

Bu noktada, iki dosya çıkış yapılandırma çalıştırabilirsiniz:

 * Bir *. yerel Configuration Manager'ın yerel makine deposunda depolanır ve kendi parmak izi tarafından tanımlanan sertifikayı kullanarak kimlik bilgilerini şifresini yapılandırır meta.mof dosya. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) Geçerli *. meta.mof dosya.
 * Gerçekte yapılandırma uygulanır bir MOF dosyası. Başlangıç DscConfiguration yapılandırmasını uygular.

Bu komutlar, bu adımları yapabiliriz:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Bu örnek DSC yapılandırması hedef düğüme gönderdiğiniz.
DSC yapılandırması da varsa bir DSC çekme sunucusuna kullanılarak uygulanabilir.

Bkz: [bir DSC çekme istemcisi kurarken](pullClient.md) DSC yapılandırmaları bir DSC çekme sunucusu kullanarak uygulama hakkında daha fazla bilgi için.

## <a name="credential-encryption-module-example"></a>Kimlik bilgisi şifreleme modülü örneği

Tüm adımları yanı sıra dışa aktarır ve ortak anahtarları kopyalar bir yardımcı cmdlet'i içeren tam bir örnek aşağıda verilmiştir:

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
