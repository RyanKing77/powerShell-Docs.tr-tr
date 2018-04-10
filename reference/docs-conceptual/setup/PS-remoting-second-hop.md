---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell uzaktan iletişim içinde ikinci atlama yapma
ms.openlocfilehash: 893b4353c4244dc96c4b234bb4062b583a5cd36d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>PowerShell uzaktan iletişim içinde ikinci atlama yapma

"İkinci atlama sorun" aşağıdaki gibi bir durumla başvuruyor:

1. Oturum açmış _ServerA_.
2. Gelen _ServerA_, bağlanmak için Uzak PowerShell oturumu Başlat _SunucuB_.
3. Çalıştırdığınız bir komut _SunucuB_ , PowerShell uzaktan iletişimi oturum üzerindeki bir kaynağa erişim girişiminde _SunucuC ise_.
4. Kaynağa erişim _SunucuC ise_ engellendi, PowerShell uzak oturum oluşturmak için kullanılan kimlik bilgileri gelen değil geçirildiğinden _SunucuB_ için _SunucuC ise_.

Bu sorunu gidermek için birkaç yolu vardır. Bu konuda, birkaç ikinci atlama sorun en popüler çözümleri inceleyeceğiz.

## <a name="credssp"></a>CredSSP

Kullanabileceğiniz [kimlik bilgileri güvenlik desteği sağlayıcısı (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) kimlik doğrulaması için. CredSSP kimlik bilgileri uzak sunucuda önbelleğe alır (_SunucuB_), bunu kullanarak kimlik bilgisi hırsızlığı saldırıları kadar açar. Uzak bilgisayar tehlikede olsa saldırganın kullanıcının kimlik bilgilerine erişebilir. CredSSP hem istemci hem de sunucu bilgisayarlarda varsayılan olarak devre dışıdır. Yalnızca en güvenilir ortamlarında CredSSP etkinleştirmeniz gerekir. Örneğin, bir etki alanı yöneticisi etki alanı denetleyicisi yüksek oranda güvenilir olmadığı için bir etki alanı denetleyicisine bağlanma.

PowerShell uzaktan iletişim için CredSSP kullanırken, güvenlik sorunları hakkında daha fazla bilgi için bkz: [yanlışlıkla Sabotaj: CredSSP dikkat](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Kimlik bilgisi hırsızlığı saldırıları hakkında daha fazla bilgi için bkz: [Azaltıcı Pass--Hash (PtH) saldırılarını ve diğer kimlik bilgisi hırsızlığını](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Etkinleştirmek ve PowerShell uzaktan iletişim için CredSSP kullanma örneği için bkz: [ikinci atlama sorunu çözmek için CredSSP kullanarak](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Artıları

- Tüm sunucular için Windows Server 2008 veya sonraki sürümleriyle çalışır.

### <a name="cons"></a>Eksileri

- Güvenlik açıkları vardır.
- İstemci ve sunucu rollerinin yapılandırılmasını gerektirir.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos temsilcisi (kısıtlanmamış)

Ayrıca kullanabilir Kısıtlanmamış Kerberos yetkilendirmesi ikinci atlama yapma. Ancak, bu yöntem atanmış kimlik bilgileri kullanıldığı hiçbir denetim sağlar.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez. Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Hiçbir özel kodlama gerektirir.

### <a name="cons"></a>Eksileri

- İkinci atlama için WinRM desteklemez.
- Bir güvenlik açığı oluşturma, kimlik bilgilerinin kullanıldığı üzerinde hiçbir denetimi sağlar.

## <a name="kerberos-constrained-delegation"></a>Kısıtlı Kerberos temsilcisi seçme

Eski Kısıtlı temsilci (değil kaynak tabanlı), ikinci atlama yapmak için kullanabilirsiniz.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez. Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Hiçbir özel kodlama gerektirir

### <a name="cons"></a>Eksileri

- İkinci atlama için WinRM desteklemez.
- Uzak sunucuya Active Directory nesnesinde yapılandırılmış olması gerekir (_SunucuB_).
- Bir etki alanı sınırlıdır. Etki alanları veya ormanlar arası olamaz.
- Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerektirir.

## <a name="resource-based-kerberos-constrained-delegation"></a>Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme

Kaynak tabanlı Kerberos kısıtlı temsilcisi (Windows Server 2012'de sunulmuştur), kimlik bilgileri temsilcisi kaynakları bulunduğu sunucu nesnesinde yapılandırın.
Yukarıda açıklanan ikinci atlama senaryoda yapılandırdığınız _SunucuC ise_ belirtmek için burada kabul edeceği kimlik bilgileri temsilcisi.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi temsilci seçilemez. Daha fazla bilgi için bkz: [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Kimlik bilgileri depolanmaz.
- Görece kolay PowerShell cmdlet'leri--gerekli özel kodlama kullanılarak yapılandırılabilir.
- Özel etki alanı erişimi gereklidir.
- Etki alanları ve ormanlar arasında çalışır.
- PowerShell kodu.

### <a name="cons"></a>Eksileri

- Windows Server 2012 veya sonraki sürümünü gerektirir.
- İkinci atlama için WinRM desteklemez.
- Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerektirir.

### <a name="example"></a>Örnek

Kaynak yapılandırır örnek temel Kısıtlı temsilci PowerShell bakalım _SunucuC ise_ yetki verilen kimlik bilgilerinden izin vermek için bir _SunucuB_.
Bu örnek, tüm sunucular Windows Server 2012 veya sonraki sürümünü, çalıştığını varsayar ve hangi sunuculardan herhangi biri için her bir etki alanı en az bir Windows Server 2012 etki alanı denetleyicisi olduğunu ait.

Kısıtlanmış temsilci yapılandırmadan önce eklemelisiniz `RSAT-AD-PowerShell` Active Directory PowerShell modülünü yüklemek için özellik ve oturumunuza bu modülünü içeri aktarın:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Birkaç kullanılabilir cmdlet'leri şimdi sahip bir **PrincipalsAllowedToDelegateToAccount** parametre:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** parametre kümeleri Active Directory nesne özniteliği **msDS-AllowedToActOnBehalfOfOtherIdentity**, bir erişim denetimi listesi (ACL) içeren, hangi hesapların ilişkili hesabın kimlik bilgilerini temsil izniniz olan belirtir (örneğimizde, makine hesabını olacaktır _Server_).

Şimdi şimdi sunucuları temsil etmek amacıyla değişkenlerini ayarlamak:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (ve bu nedenle PowerShell uzaktan iletişimini) varsayılan olarak bilgisayar hesabı olarak çalışır. Bu bakarak bkz **StartName** özelliği `winrm` hizmeti:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

İçin _SunucuC ise_ PowerShell uzaktan iletişim oturumundan temsilci sağlamak için _SunucuB_, biz ayarlayarak erişim izni verecek **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ bilgisayar nesnesi _SunucuB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [Anahtar Dağıtım Merkezi (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) önbellekleri erişim denemesi (negatif önbelleğini) 15 dakika için reddedildi. Varsa _SunucuB_ önceden erişmeyi denedi _SunucuC ise_, üzerinde önbelleğini temizlemek gerekir _SunucuB_ göre aşağıdaki komutu çalıştırır:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Ayrıca bilgisayarı yeniden başlatın veya önbelleğini temizlemek için en az 15 dakika bekleyin.

Önbelleği temizledikten sonra koddan başarıyla çalıştırabilirsiniz _ServerA_ aracılığıyla _SunucuB_ için _SunucuC ise_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

Bu örnekte, `$using` değişkeni yapmak için kullanılan `$ServerC` değişkeni görünür _SunucuB_. Hakkında daha fazla bilgi için `$using` değişken, bkz: [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).

Kimlik bilgileri için temsilci seçme birden çok sunucu izin vermek için _SunucuC ise_, değerini **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ bir dizi:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Etki alanları arasında ikinci atlama yapmak istiyorsanız, tam etki alanı adı (FQDN) etki alanının etki alanı denetleyicisini kendisine eklemek _SunucuB_ ait:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Kimlik bilgileri SunucuC ise için temsilci seçme olanağı kaldırmak için değerini ayarlayın **PrincipalsAllowedToDelegateToAccount** parametresini _SunucuC ise_ için `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme hakkında bilgi

- [Kerberos kimlik doğrulamasındaki yenilikler nelerdir?](https://technet.microsoft.com/library/hh831747.aspx)
- [Windows Server 2012 hızları Kerberos sorunun nasıl kısıtlı temsilcisi, bölüm 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Windows Server 2012 hızları Kerberos sorunun nasıl kısıtlı temsilcisi, bölüm 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Anlama Kerberos Kısıtlanmış temsilci seçme için tümleşik Windows kimlik doğrulaması ile Azure Active Directory Uygulama proxy'si dağıtımları](http://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory şema öznitelikleri M2.210 özniteliği msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protokolü uzantıları: kullanıcı için hizmet ve kısıtlanmış temsil protokolü 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)
- [Kaynak tabanlı Kerberos Kısıtlı temsilci](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Kısıtlanmış temsilci PrincipalsAllowedToDelegateToAccount kullanarak olmadan uzaktan yönetim](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>Runas komutunu kullanarak PSSessionConfiguration

Bir oturum yapılandırması oluşturabilirsiniz _SunucuB_ ve kendi **RunAsCredential** parametresi.

İkinci atlama sorunu çözmek için PSSessionConfiguration ve Farklı Çalıştır'ı kullanma hakkında daha fazla bilgi için bkz: [çoklu atlamalı PowerShell uzaktan iletişim için başka bir çözüm](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Artıları

- WMF 3.0 veya daha sonra herhangi bir sunucu ile çalışır.

### <a name="cons"></a>Eksileri

- Yapılandırmasını gerektirir **PSSessionConfiguration** ve **RunAs** Ara her sunucuda (_SunucuB_).
- Bir etki alanı kullanırken parola bakım gerektiren **RunAs** hesabı

## <a name="just-enough-administration-jea"></a>Yeterli Yönetim (JEA)

JEA, yönetici bir PowerShell oturumunda çalıştırmak hangi komutları sınırlamanıza olanak sağlar. İkinci atlama sorunu çözmek için kullanılabilir.

JEA hakkında daha fazla bilgi için bkz: [yalnızca yeterince Yönetim](https://docs.microsoft.com/en-us/powershell/jea/overview).

### <a name="pros"></a>Artıları

- Sanal hesap kullanırken hiçbir parola Bakım.

### <a name="cons"></a>Eksileri

- WMF 5.0 veya sonrasını gerektirir.
- Her ara sunucusu üzerindeki yapılandırmayı gerektirir (_SunucuB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Invoke-Command betik bloğu içinde geçişi kimlik bilgileri

Kimlik bilgileri içinde geçirdiğiniz **ScriptBlock** yapılan bir çağrı parametresinin [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet'i.

### <a name="pros"></a>Artıları

- Özel sunucu yapılandırması gerektirmez.
- WMF 2.0 veya sonraki sürümünü çalıştıran herhangi bir sunucu üzerinde çalışır.

### <a name="cons"></a>Eksileri

- Garip kod teknik gerektirir.
- WMF 2.0 çalıştıran, bir uzak oturum için bağımsız değişkenleri geçirme farklı bir sözdizimi gerektirir.

### <a name="example"></a>Örnek

Aşağıdaki örnek, kimlik bilgileri geçirmek gösterilmiştir bir **Invoke-Command** betik bloğu:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Ayrıca bkz:

[PowerShell Uzaktan İletişim Güvenlik Konuları](WinRMSecurity.md)