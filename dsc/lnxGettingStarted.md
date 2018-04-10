---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Linux için istenen durum yapılandırması (DSC) ile çalışmaya başlama
ms.openlocfilehash: b2f35ebe84dfd9f68ca07e7630534be59f8a1aa3
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Linux için istenen durum yapılandırması (DSC) ile çalışmaya başlama

Bu konuda Linux için PowerShell istenen durum yapılandırması (DSC) ile çalışmaya başlamak açıklanmaktadır. DSC hakkında genel bilgi için bkz: [Windows PowerShell istenen durum yapılandırması ile çalışmaya başlama](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Desteklenen Linux işlemi sistemi sürümleri

Aşağıdaki Linux işletim sistemi sürümleri için DSC Linux için desteklenir.
- CentOS 5, 6 ve 7 (x86/x64)
- Debian GNU/Linux 6, 7 ve 8 (x86/x64)
- Oracle Linux 5, 6 ve 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 ve 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 ve 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS ve 16.04 LTS (x86/x64)

Aşağıdaki tabloda, Linux için DSC için gerekli paket bağımlılıkları açıklar.

|  Gerekli paket |  Açıklama |  En düşük sürüm |
|---|---|---|
| glibc| GNU Kitaplığı| 2…4 – 31.30|
| Python| Python| 2.4 – 3.4|
| omiserver| Açık Yönetim Altyapısı| 1.0.8.1|
| Openssl| OpenSSL kitaplıkları| 0.9.8 veya 1.0|
| ctypes| Python CTypes kitaplığı| Python sürümü aynı olmalıdır|
| libcurl| cURL http istemci kitaplığı| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Linux için DSC yükleme

Yüklemelisiniz [açık Yönetim Altyapısı (OMI)](https://github.com/Microsoft/omi) Linux için DSC yüklemeden önce.

### <a name="installing-omi"></a>OMI yükleme

İstenen durum yapılandırması sürümü 1.0.8.1 açık Yönetim Altyapısı (OMI) CIM sunucusu Linux gerektirir veya sonraki bir sürümü. OMI açık grubundan indirilebilir: [açık Yönetim Altyapısı (OMI)](https://github.com/Microsoft/omi).

OMI yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) uygun paketini yükleyin. RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur. DEB paketleri Debian GNU/Linux ve Ubuntu Server için uygundur. Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun durumdayken yüklü olan bilgisayarlar için uygundur.

> **Not**: yüklü olan bir OpenSSL sürümü belirlemek için komutu çalıştırmak `openssl version`.

OMI CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>DSC yükleme

Linux için DSC indirilebilir [burada](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).

DSC yüklemek için Linux sistemine (.rpm veya .deb) ve OpenSSL sürümü (ssl_098 veya ssl_100) ve mimari (x64/x86) uygun paketini yükleyin. RPM paketleri, CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server ve Oracle Linux için uygundur. DEB paketleri Debian GNU/Linux ve Ubuntu Server için uygundur. Ssl_098 paketleri OpenSSL 0.9.8 ssl_100 paketleri OpenSSL 1.0 yüklü bilgisayarlar için uygun durumdayken yüklü olan bilgisayarlar için uygundur.

> **Not**: yüklü olan bir OpenSSL sürümü belirlemek için komut openssl sürümü çalıştırın.

DSC CentOS 7 x64 sisteme yüklemek için aşağıdaki komutu çalıştırın.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Linux için DSC kullanma

Aşağıdaki bölümlerde, oluşturma ve Linux bilgisayarlarda DSC yapılandırmaları çalıştırma açıklanmaktadır.

### <a name="creating-a-configuration-mof-document"></a>Bir yapılandırma MOF belge oluşturma

Windows PowerShell yapılandırması anahtar sözcüğü, Windows bilgisayarları için olduğu gibi Linux bilgisayarlar için bir yapılandırma oluşturmak için kullanılır. Aşağıdaki adımlar, Windows PowerShell kullanarak bir Linux bilgisayar için bir yapılandırma belge oluşturulmasını açıklar.

1. Nx modülünü içeri aktarın. Nx Windows PowerShell modülü yerleşik kaynaklar için şema DSC için Linux için içerir ve yerel bilgisayarınıza yüklenmeli ve yapılandırmada içeri aktarıldı.

    -Nx modülünü yüklemek için nx modülü dizini ya da kopyalama `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` veya `$PSHOME\Modules`. Nx modülü DSC Linux yükleme paketinin (MSI) dahil edilir. Yapılandırmanızda nx modülü içeri aktarmak için kullanın __alma DSCResource__ komutu:

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. Yapılandırma belge oluşturmak ve bir yapılandırma tanımlayın:

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a>Linux bilgisayara yapılandırma bildirme

Yapılandırma belgeleri (MOF dosyaları) gönderilen Linux kullanarak bilgisayar [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i. Bu cmdlet ile birlikte kullanmak için [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), veya [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'leri, uzaktan Linux bilgisayara bir CIMSession kullanmanız gerekir. [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet CIMSession Linux bilgisayara oluşturmak için kullanılır.

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

> **Not**:
* "Gönderme" modu için kullanıcı kimlik bilgileri Linux bilgisayardaki kök kullanıcı olmalıdır.
* Linux, New-CimSession – UseSSL parametresi $true olarak ayarlanmış kullanılmalıdır yalnızca SSL/TLS bağlantılarını DSC için desteklenir.
* (DSC için) OMI tarafından kullanılan SSL sertifikasını dosyasında belirtilen: `/opt/omi/etc/omiserver.conf` özelliklere sahip: pemfile ve keyfile.
Bu sertifika çalıştırmakta olduğunuz Windows bilgisayar tarafından güvenilir değilse [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet'ini, sertifika doğrulama CIMSession seçeneklerle yoksay seçebilirsiniz: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

DSC yapılandırması Linux düğüme göndermek için aşağıdaki komutu çalıştırın.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Bir çekme sunucu yapılandırmasıyla Dağıt

Yapılandırmaları bir çekme sunucusuyla Linux bilgisayara gibi Windows bilgisayarları için dağıtılabilir. Bir çekme sunucusuna kullanma ile ilgili yönergeler için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](pullServer.md). Ek bilgi ve Linux bilgisayarları bir çekme sunucusuyla kullanmaya ilişkin sınırlamalar, sürüm notları Linux için istenen durum yapılandırması için bkz.

### <a name="working-with-configurations-locally"></a>Yerel olarak yapılandırmaları ile çalışma

Linux için DSC yapılandırma yerel Linux bilgisayardan çalışmak için komut dosyalarını içerir. Bu komut dosyalarını bulun `/opt/microsoft/dsc/Scripts` ve şunları içerir:
* GetDscConfiguration.py

 Bilgisayara uygulanan geçerli yapılandırmasını döndürür. Windows PowerShell cmdlet Get-DscConfiguration cmdlet'i benzer.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Bilgisayara uygulanan geçerli meta yapılandırmasını döndürür. Cmdlet benzer [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet'i.

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Özel bir DSC kaynağı modülünü yükler. Modül paylaşılan nesne kitaplığını içeren bir .zip dosyası ve şema MOF dosyaları yolunu gerektirir.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Özel bir DSC kaynağı modülü kaldırır. Kaldırılacak modülün adı gerektirir.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py

 Bir yapılandırma MOF dosyası bilgisayara uygulanır. Benzer şekilde [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i. Yapılandırmayı uygulamak için MOF yolu gerektirir.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Bir Meta yapılandırma MOF dosyası bilgisayara uygulanır. Benzer şekilde [kümesi DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet'i. Uygulanacak Meta yapılandırma MOF yolu gerektirir.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell istenen durum yapılandırması Linux günlük dosyaları için

Aşağıdaki günlük dosyalarına DSC için Linux iletiler için oluşturulur.

|Günlük dosyası|Dizin|Açıklama|
|---|---|---|
|omiserver.log|/var/OPT/omi/log|OMI CIM sunucusu işlemi için ilgili iletileri.|
|dsc.log|/var/OPT/omi/log|Yerel Configuration Manager (LCM'yi) ve DSC kaynak işlemlerinin işlemi için ilgili iletileri.|