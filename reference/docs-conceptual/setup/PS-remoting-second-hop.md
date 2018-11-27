---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: PowerShell uzaktan iletişim'de ikinci atlamayı yapma
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320712"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>PowerShell uzaktan iletişim'de ikinci atlamayı yapma

"İkinci atlama sorun" aşağıdaki gibi bir durumla ifade eder:

1. Oturum açtığınız _ServerA_.
2. Gelen _ServerA_, bağlanmak için Uzak PowerShell oturumu Başlat _SunucuB_.
3. Bir komutu çalıştırdığınız _SunucuB_ , PowerShell uzaktan iletişimini oturum üzerinde bir kaynağa erişmeye çalışır. _SunucuC ise_.
4. Şirket kaynağına erişim _SunucuC ise_ reddedildi, PowerShell uzaktan iletişimini oturumu oluşturmak için kullanılan kimlik bilgilerini gelen geçirilen değil çünkü _SunucuB_ için _SunucuC ise_.

Bu sorunu çözmek için birkaç yolu vardır. Bu konuda, ikinci atlama sorun en popüler çözümleri birkaçı şu konuları inceleyeceğiz.

## <a name="credssp"></a>CredSSP

Kullanabileceğiniz [kimlik bilgileri güvenlik desteği sağlayıcısı (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) kimlik doğrulaması için. CredSSP kimlik bilgilerini uzak sunucuda önbelleğe alır (_SunucuB_), onu kullanarak kimlik bilgisi hırsızlığı saldırılarını kadar açılmasını sağlayın. Uzak bilgisayarın tehlikede olursa saldırganın kullanıcının kimlik bilgilerine erişebilir. CredSSP hem istemci hem de sunucu bilgisayarlarda varsayılan olarak devre dışıdır. Yalnızca en çok güvenilen ortamlarda CredSSP etkinleştirmeniz gerekir. Örneğin, bir etki alanı yöneticisi etki alanı denetleyicisi yüksek oranda güvenilir olmadığı için bir etki alanı denetleyicisine bağlanma.

PowerShell uzaktan iletişimi için CredSSP kullanırken, güvenlik sorunları hakkında daha fazla bilgi için bkz. [yanlışlıkla Sabotaj: CredSSP Sıralamaların](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Kimlik bilgisi hırsızlığı saldırılarını hakkında daha fazla bilgi için bkz: [Azaltıcı Pass--Hash (PtH) saldırılarını ve diğer kimlik bilgisi Hırsızlıklarını](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Etkinleştirmek ve PowerShell uzaktan iletişimi için CredSSP kullanma örneği için bkz: [ikinci atlama sorunu çözmek için CredSSP kullanarak](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Artıları

- Tüm sunucular için Windows Server 2008 veya daha sonra çalışır.

### <a name="cons"></a>Eksileri

- Güvenlik açıkları vardır.
- İstemci ve sunucu rollerini yapılandırılmasını gerektirir.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos temsilcisi seçme (sınırlandırılmamış)

Ayrıca kullanabilir Kısıtlanmamış Kerberos yetkilendirmesi ikinci atlamayı yapma. Ancak, bu yöntem, temsilci seçilen kimlik bilgilerinin kullanıldığı bir denetim yok sağlar.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez. Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Özel kodlama gerektirir.

### <a name="cons"></a>Eksileri

- İkinci atlama için WinRM desteklemez.
- Bir güvenlik açığı oluşturarak, kimlik bilgilerinin kullanıldığı hiçbir denetim sağlar.

## <a name="kerberos-constrained-delegation"></a>Kısıtlı Kerberos temsilcisi seçme

İkinci atlamayı yapma, eski Kısıtlı temsilci (değil kaynak tabanlı) kullanabilirsiniz.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez. Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Özel kodlama gerektirir

### <a name="cons"></a>Eksileri

- İkinci atlama için WinRM desteklemez.
- Uzak sunucuya Active Directory nesne üzerinde yapılandırılmış olması gerekir (_SunucuB_).
- Bir etki alanı ile sınırlıdır. Etki alanları veya ormanlar arası olamaz.
- Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.

## <a name="resource-based-kerberos-constrained-delegation"></a>Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme

Kaynak tabanlı Kerberos kısıtlı temsilcisi (Windows Server 2012'de sunulmuştur), kaynakların nerede sunucu nesnesinde kimlik bilgileri temsilcisi yapılandırın.
Yukarıda açıklanan ikinci atlama senaryoda yapılandırdığınız _SunucuC ise_ belirtmek için burada kabul edeceği kimlik bilgileri temsilcisi.

>**Not:** olan Active Directory hesaplarını **Hesap duyarlıdır ve devredilemez** özellik kümesi için temsilci olarak seçilemez. Daha fazla bilgi için [güvenlik odak: 'Hesap duyarlıdır ve devredilemez' ayrıcalıklı hesaplar için analiz](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) ve [Kerberos kimlik doğrulaması araçları ve ayarları](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Artıları

- Kimlik bilgileri depolanmaz.
- PowerShell cmdlet'leri--özel kodlama gerekmeden kullanarak yapılandırmak daha kolay.
- Özel etki alanı erişimi gereklidir.
- Etki alanları ve ormanlar arasında çalışır.
- PowerShell kodu.

### <a name="cons"></a>Eksileri

- Windows Server 2012 veya sonraki sürümünü gerektirir.
- İkinci atlama için WinRM desteklemez.
- Nesneleri ve hizmet asıl adları (SPN) güncelleştirmek için hakları gerekir.

### <a name="example"></a>Örnek

Kaynak yapılandıran örnek üzerinde kısıtlı temsilci tabanlı bir PowerShell göz atalım _SunucuC ise_ temsilci seçilen kimlik bilgilerinden izin vermek için bir _SunucuB_.
Bu örnek, tüm sunucular Windows Server 2012 veya sonraki sürümünü, çalıştığını varsayar ve hangi sunuculardan herhangi biri için her bir etki alanı en az bir Windows Server 2012 etki alanı denetleyicisi olduğunu ait.

Kısıtlanmış temsilciyi yapılandırmak önce eklemelisiniz `RSAT-AD-PowerShell` Active Directory PowerShell modülü yüklemek için özellik ve daha sonra oturumunuz bu modülü içeri aktarın:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Birkaç kullanılabilir cmdlet'lerin artık sahip bir **PrincipalsAllowedToDelegateToAccount** parametresi:

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

**PrincipalsAllowedToDelegateToAccount** parametre ayarlar Active Directory nesne özniteliği **msDS-AllowedToActOnBehalfOfOtherIdentity**, erişim denetimi listesi (ACL) içeriyor, hangi hesapların ilişkili hesabı kimlik bilgilerini temsil izniniz belirtir (Bizim örneğimizde, makine hesabını olacaktır _sunucu_).

Artık sunucuları temsil etmek için kullanacağız değişkenleri ayarlayalım:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (ve bu nedenle PowerShell uzaktan iletişimini) varsayılan olarak bilgisayar hesabı olarak çalışır. Bu bakarak görebilirsiniz **StartName** özelliği `winrm` hizmeti:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

İçin _SunucuC ise_ PowerShell uzaktan iletişimini oturumundan temsilci izni _SunucuB_, biz ayarlayarak erişim izni verir **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için bilgisayar nesnesine göre _SunucuB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [Anahtar Dağıtım Merkezi (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) önbellekler 15 dakika boyunca erişim denemesi (negatif önbellek) reddedildi. Varsa _SunucuB_ daha önce erişmeyi denedi _SunucuC ise_, üzerinde önbelleği temizlemek ihtiyacınız olacak _SunucuB_ aşağıdaki komutunu çağırarak:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Ayrıca bilgisayarı yeniden başlatın veya önbelleği temizlemek için en az 15 dakika bekleyin.

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

Bu örnekte, `$using` değişkeni sağlamak için kullanılan `$ServerC` değişken görünür _SunucuB_. Hakkında daha fazla bilgi için `$using` değişken, bkz: [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Kimlik bilgileri için temsilci seçmek birden çok sunucu izin vermek için _SunucuC ise_, değerini **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ bir dizi:

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

Etki alanları arasında ikinci atlama yapmak istiyorsanız, tam etki alanı adı (FQDN) etki alanının etki alanı denetleyicisini kendisine ekleme _SunucuB_ aittir:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Temsilci SunucuC ise kimlik özelliği kaldırmak için değerini ayarlamak **PrincipalsAllowedToDelegateToAccount** parametresi _SunucuC ise_ için `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Kaynak tabanlı kısıtlı Kerberos temsilcisi seçme hakkında bilgi

- [Kerberos kimlik doğrulamasındaki yenilikler](https://technet.microsoft.com/library/hh831747.aspx)
- [Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Nasıl Windows Server 2012 hızları kolaylaştırın, Kerberos kısıtlı temsilcisi, bölüm 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Anlama Kerberos kısıtlı temsilcisi tümleşik Windows kimlik doğrulaması ile Azure Active Directory Uygulama Ara sunucusu dağıtımları için](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory şema öznitelikleri M2.210 özniteliği msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protokolü uzantıları: kullanıcı için hizmet ve kısıtlanmış temsil protokolü 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Kaynak tabanlı Kerberos kısıtlı temsil](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Kısıtlanmış temsilci kullanarak PrincipalsAllowedToDelegateToAccount olmadan uzaktan yönetim](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>Farklı Çalıştır'ı kullanarak PSSessionConfiguration

Bir oturum yapılandırması oluşturabilirsiniz _SunucuB_ ve kendi **RunAsCredential** parametresi.

İkinci atlama sorunu çözmek için PSSessionConfiguration ve Farklı Çalıştır'ı kullanma hakkında daha fazla bilgi için bkz: [çoklu atlamalı PowerShell uzaktan iletişim için başka bir çözüm](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Artıları

- Herhangi bir sunucu WMF 3.0 veya üstü ile çalışır.

### <a name="cons"></a>Eksileri

- Yapılandırılmasını gerektirir **PSSessionConfiguration** ve **RunAs** Ara her sunucuda (_SunucuB_).
- Bir etki alanı kullanırken parola bakıma gerek duyacağını **RunAs** hesabı

## <a name="just-enough-administration-jea"></a>Yeterli Yönetim (JEA)

JEA, yönetici bir PowerShell oturumunda çalıştırmak hangi komutları sınırlamanıza olanak tanır. İkinci atlama sorunu çözmek için kullanılabilir.

JEA hakkında daha fazla bilgi için bkz. [yeterli yönetim](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Artıları

- Sanal bir hesap kullanırken hiçbir parola Bakım.

### <a name="cons"></a>Eksileri

- WMF 5.0 veya sonraki sürümünü gerektirir.
- Her bir ara sunucu yapılandırma gerektirir (_SunucuB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Invoke-Command betik bloğunun Pass kimlik bilgileri

Kimlik bilgileri içine geçirebilirsiniz **ScriptBlock** çağrısına parametre [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet'i.

### <a name="pros"></a>Artıları

- Özel sunucu yapılandırması gerektirmez.
- WMF 2.0 veya sonraki sürümünü çalıştıran herhangi bir sunucu üzerinde çalışır.

### <a name="cons"></a>Eksileri

- Garip kod teknik gerektirir.
- WMF 2.0 çalıştırılıyorsa, uzak oturumu bağımsız değişkenleri geçirmek için farklı bir sözdizimi gerektirir.

### <a name="example"></a>Örnek

Aşağıdaki örnek, kimlik bilgilerini geçirmek nasıl gösterir bir **Invoke-Command** betik bloğu:

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