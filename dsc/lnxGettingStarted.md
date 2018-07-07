---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Linux için Desired State Configuration (DSC) ile çalışmaya başlama
ms.openlocfilehash: d5a4a17fbcffbbbd6df3dd902dbd104769b7d17e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893605"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Linux için Desired State Configuration (DSC) ile çalışmaya başlama

Bu konuda, Linux için PowerShell Desired State Configuration (DSC) ile çalışmaya başlamak açıklanmaktadır. DSC hakkında genel bilgi için bkz: [Windows PowerShell Desired State Configuration ile'çalışmaya başlama](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Desteklenen Linux işlemi sistemi sürümleri

Aşağıdaki Linux işletim sistemi sürümleri için DSC Linux için desteklenir.

- CentOS 5, 6 ve 7 (x86/x64)
- Debian GNU/Linux 6, 7 ve 8 (x86/x64)
- Oracle Linux 5, 6 ve 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 ve 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 ve 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS ve 16.04 LTS (x86/x64)

Aşağıdaki tabloda, Linux için DSC için gerekli Paket bağımlılıklarını açıklar.

|  Gerekli paket |  Açıklama |  En düşük sürüm |
|---|---|---|
| glibc| GNU Kitaplığı| 2... 4 – 31.30|
| Python| Python| 2.4-3.4|
| omiserver| Açık Yönetim Altyapısı| 1.0.8.1|
| openssl| OpenSSL kitaplıkları| 0.9.8 veya 1.0|
| ctypes| Python CTypes kitaplığı| Python sürümü ile eşleşmelidir|
| libcurl| cURL, http istemci kitaplığı| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Linux için DSC yükleme

Yüklemelisiniz [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) Linux için DSC yüklemeden önce.

### <a name="installing-omi"></a>OMI yükleme

Sürüm 1.0.8.1 Open Management Infrastructure (OMI) CIM sunucusu Linux gerektirir Desired State Configuration veya üzeri. OMI açık grubundan indirilebilir: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

OMI yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) için uygun olan paketi yükleyin. RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur. DEB paketleri, Debian GNU/Linux ve Ubuntu Server için uygundur. Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun olsa da yüklü olan bilgisayarlar için uygundur.

> [!NOTE]
> Yüklü olan bir OpenSSL sürümü belirlemek için komutu çalıştırmak `openssl version`.

OMI, bir CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>DSC yükleme

Linux için DSC indirilebilir [burada](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

DSC yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) için uygun olan paketi yükleyin. RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur. DEB paketleri, Debian GNU/Linux ve Ubuntu Server için uygundur. Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun olsa da yüklü olan bilgisayarlar için uygundur.

> [!NOTE]
> Yüklü olan bir OpenSSL sürümü belirlemek için komut openssl sürümü çalıştırın.

DSC, bir CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Linux için DSC kullanma

Aşağıdaki bölümlerde, oluşturma ve Linux bilgisayarlarda DSC yapılandırmaları açıklanmaktadır.

### <a name="creating-a-configuration-mof-document"></a>Yapılandırma MOF belgesi oluşturma

Windows PowerShell yapılandırma anahtar sözcüğü, tıpkı Windows bilgisayarlar için Linux bilgisayarlar için bir yapılandırma oluşturmak için kullanılır. Aşağıdaki adımlar, Windows PowerShell kullanarak bir Linux bilgisayar için bir yapılandırma belgesi oluşturulmasını açıklar.

1. Nx modülünü içeri aktarın. Nx Windows PowerShell modülünü şeması için yerleşik kaynaklar için DSC Linux için içerir ve yerel bilgisayarınıza yüklenmeli ve yapılandırmada içeri aktarıldı.

   - Nx modülünü yüklemek için nx modülü dizini ya da kopyalama `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` veya `$PSHOME\Modules`. Nx modülü DSC Linux yükleme paketinin (MSI) dahildir. Yapılandırmanızda nx modülü içeri aktarmak için kullanın `Import-DSCResource` komutu:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Bir yapılandırma tanımlama ve yapılandırma belgesi oluşturun:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Yapılandırma Linux bilgisayar anında iletme

Yapılandırma belgelerini (MOF dosyaları) gönderilen Linux bilgisayar kullanarak [Başlat-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet'i. Bu cmdlet ile birlikte kullanmak için [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), veya [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet'leri, uzaktan Linux bilgisayara bir CIMSession kullanmanız gerekir. [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'i bir CIMSession Linux bilgisayarda oluşturmak için kullanılır.

Aşağıdaki kod bir CIMSession DSC için Linux için oluşturulacağını gösterir.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> [!NOTE]
> "Gönderme" modu için kullanıcı kimlik bilgilerini Linux bilgisayarında kök kullanıcı olması gerekir.
> Yalnızca SSL/TLS bağlantılarını DSC için Linux için desteklenen `New-CimSession` $true olarak ayarlayın: UseSSL parametresi ile birlikte kullanılmalıdır.
> (DSC için) OMI tarafından kullanılan SSL sertifikasını dosyasında belirtilen: `/opt/omi/etc/omiserver.conf` özelliklere sahip: pemfile ve keyfile.
> Bu sertifika, çalıştırmakta olduğunuz Windows bilgisayar tarafından güvenilir değilse [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'i üzerinde tercih edebilirsiniz sertifika doğrulama CIMSession seçeneklerle yoksay: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

DSC yapılandırması Linux düğüme göndermek için aşağıdaki komutu çalıştırın.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Bir çekme sunucusu yapılandırmasıyla dağıtın

Yapılandırmaları bir çekme sunucusu ile bir Linux bilgisayar gibi Windows bilgisayarlar için dağıtılabilir. Bir çekme sunucusu kullanma ile ilgili yönergeler için bkz [Windows PowerShell Desired State Configuration çekme sunucuları](pullServer.md). Ek bilgi ve Linux bilgisayarları bir çekme sunucusu kullanmaya ilişkin sınırlamalar için sürüm notları için Linux Desired State Configuration ' için bkz.

### <a name="working-with-configurations-locally"></a>Yerel olarak yapılandırmaları ile çalışma

Linux için DSC yapılandırması yerel Linux bilgisayardan çalışmak için komut dosyalarını içerir. Olan bu betikler bulun `/opt/microsoft/dsc/Scripts` ve şunları içerir:

- GetDscConfiguration.py

Bilgisayara uygulanan geçerli yapılandırmasını döndürür. Windows PowerShell cmdlet'i için benzer `Get-DscConfiguration` cmdlet'i.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Bilgisayara uygulanan geçerli meta yapılandırmasını döndürür. Cmdlet'e benzer [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet'i.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Özel bir DSC kaynağı modülünü yükler. Modül paylaşılan nesne kitaplığı içeren bir .zip dosyası ve şema MOF dosya yolunu gerektirir.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Özel bir DSC kaynak modülü kaldırır. Kaldırmak için modülünün adı gerektirir.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Yapılandırma MOF dosyasının bilgisayara uygulanır. Benzer şekilde [Başlat-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet'i. ' % S'yapılandırması uygulamak için MOF yolu gerektirir.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Bir Meta yapılandırma MOF dosyasının bilgisayara uygulanır. Benzer şekilde [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet'i. Uygulanacak Meta yapılandırma MOF yolu gerektirir.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Linux günlük dosyaları için PowerShell Desired State Configuration

Aşağıdaki günlük dosyaları için DSC Linux iletileri üretilir.

|Günlük dosyası|Dizin|Açıklama|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|OMI CIM sunucusu işlemi için ilgili iletiler.|
|**DSC.log**|`/var/opt/omi/log`|Yerel Configuration Manager'ı (LCM) ve DSC kaynak işlemleri çalışması için ilgili iletiler.|