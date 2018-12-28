---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405767"
---
# <a name="powershell-remoting-security-considerations"></a>PowerShell uzaktan iletişim güvenlik konuları

PowerShell uzaktan iletişimini Windows sistemleri yönetmek için önerilen yoldur. PowerShell uzaktan iletişimini, Windows Server 2012 R2'de varsayılan olarak etkindir. Bu belge, PowerShell uzaktan iletişimini kullanırken güvenlikle ilgili öneriler ve en iyi uygulamaları kapsar.

## <a name="what-is-powershell-remoting"></a>PowerShell uzaktan iletişimini nedir?

PowerShell uzaktan iletişimi kullandığından [Windows Uzaktan Yönetim (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), Microsoft uygulaması olduğu [Yönetim (WS-Management) için Web Hizmetleri](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) PowerShell'i çalıştırmak üzere kullanıcıların Protokolü komutları uzak bilgisayarlarda. PowerShell uzaktan iletişimini kullanma hakkında daha fazla bilgi bulabilirsiniz [çalıştıran uzak komutları](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell uzaktan iletişimini kullanarak aynı değil **ComputerName** çalıştırmak için uzak yordam çağrısı (RPC), temel alınan protokolü olarak kullanan bir uzak bilgisayarda bir cmdlet parametresi.

## <a name="powershell-remoting-default-settings"></a>PowerShell uzaktan iletişimi varsayılan ayarları

PowerShell uzaktan iletişimini (ve WinRM) aşağıdaki bağlantı noktalarında dinlemek:

- HTTP: 5985'tir
- HTTPS: 5986

Varsayılan olarak PowerShell uzaktan iletişimini bağlantıları yalnızca Administrators grubunun üyeleri sağlar. Oturumlarının tüm işletim sistemi erişim denetimleri bireysel kullanıcılara uygulanan ve gruplar varken üzerinden PowerShell uzaktan iletişimi için uygulamaya devam etmek için kullanıcının bağlamında başlatılabilir.

Özel ağlarda PowerShell uzaktan iletişim için varsayılan Windows Güvenlik duvarı kuralı tüm bağlantıları kabul eder. Genel ağlarda, varsayılan Windows Güvenlik duvarı kuralı aynı alt ağda yalnızca PowerShell uzaktan iletişimini bağlantılar sağlar. Bu kural, ortak bir ağdaki tüm bağlantılar için PowerShell uzaktan iletişimi'ni açmak için açıkça değiştirmek zorunda.

>**Uyarı:** Ortak ağlar için güvenlik duvarı kuralı, bilgisayarı kötü amaçlı olabilecek dış bağlantı saldırılara karşı korumak için tasarlanmıştır. Bu kural silerken dikkatli olun.

## <a name="process-isolation"></a>İşlem yalıtım

PowerShell uzaktan iletişimi kullandığından [Windows Uzaktan Yönetim (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) bilgisayarlar arasındaki iletişim için.
WinRM Network Service hesabının altında bir hizmet olarak çalışır ve kullanıcı hesabı olarak konak PowerShell örneklerine çalışan yalıtılmış işlemlerde olarak çoğaltılır. Bir kullanıcı olarak çalışan PowerShell örneğini erişim PowerShell örneğini başka bir kullanıcı olarak çalışan bir işleme yok.

## <a name="event-logs-generated-by-powershell-remoting"></a>PowerShell uzaktan iletişim tarafından oluşturulan olay günlükleri

Olay günlüklerini ve PowerShell uzaktan iletişimini oturumları, kullanılabilir tarafından oluşturulan diğer güvenlik kanıt iyi bir özetini FireEye sağlanan [PowerShell saldırıları araştırma](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Şifreleme ve aktarım protokolleri

PowerShell uzaktan iletişim bağlantı iki perspektiften güvenliğini düşünmek faydalıdır: ilk kimlik doğrulaması ve sürekli iletişim.

Kullanılan Aktarım Protokolü bağımsız olarak (HTTP veya HTTPS), PowerShell uzaktan iletişimini ilk kimlik doğrulamasından sonra tüm iletişimin her zaman bir oturum başına AES-256'yı simetrik anahtarla şifreler.

### <a name="initial-authentication"></a>İlk kimlik doğrulaması

Kimlik doğrulama - server ve ideal - istemcinin sunucuya istemcinin kimliğini doğrular.

Bir istemci bilgisayar adını kullanarak bir etki alanı sunucusuna bağlandığında (örn: server01, veya server01.contoso.com'nun), varsayılan kimlik doğrulama protokolüdür [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos her türlü yeniden kullanılabilir kimlik bilgisinin göndermeden kullanıcı kimliği ve sunucu kimliğini garanti eder.

İstemci IP adresini kullanarak bir etki alanı sunucusuna bağlanır veya bir çalışma grubu sunucusuna bağlanır, Kerberos kimlik doğrulaması mümkün değildir. PowerShell uzaktan iletişimini dayanan bu durumda, [NTLM kimlik doğrulama protokolü](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). NTLM kimlik doğrulama protokolü, temsilci seçme desteği sunulan kimlik bilgisi her türlü göndermeden kullanıcı kimliğini garanti eder. Kullanıcı kimliğini kanıtlamak için NTLM protokolü, istemci ve sunucu bir kullanıcının parolasını oturum anahtarı parola değişimi olmadan sürekli işlem gerektirir. Kullanıcının parolasını biliyor ve sunucunun oturum açma anahtarı hesaplar etki alanı denetleyicisi ile iletişim kurabilmesi sunucunun kullanıcının parolasını genellikle bilmez.

NTLM protokolü ancak sunucu kimliğini garanti etmez. Protokollerle NTLM kimlik doğrulaması için kullandığınız tüm gibi bir etki alanına katılmış bilgisayarın makine hesabı için erişimi olan bir saldırgan, etki alanı denetleyicisine bir NTLM oturum anahtarı işlem ve böylece sunucu özelliklerini çağırabilirsiniz.

NTLM tabanlı kimlik doğrulaması varsayılan olarak devre dışıdır, ancak hedef sunucuda yapılandırma ya da SSL veya istemcide WinRM TrustedHosts ayarını yapılandırarak izin verilebilir.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>NTLM tabanlı bağlantılar sırasında sunucu kimliğini doğrulamak için SSL sertifikalarının kullanımı

NTLM kimlik doğrulama protokolü (yalnızca zaten, parolanızı bilir) hedef sunucunun kimliğini garanti edemez olduğundan, hedef sunuculara PowerShell uzaktan iletişim için SSL kullanacak şekilde yapılandırabilirsiniz. Bir SSL sertifikası (Ayrıca istemcinin güvendiği bir sertifika yetkilisi tarafından verilen değilse) hedef sunucuya atama kullanıcı kimliği ve sunucu kimliğini garanti eder, NTLM tabanlı kimlik doğrulamasını etkinleştirir.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>NTLM tabanlı sunucu kimlik hataları yoksayma

Bir sunucu için NTLM bağlantılar için SSL sertifikası dağıtma blokunu ise, WinRM ile sunucu ekleyerek elde edilen kimlik hataları gizlemek **TrustedHosts** listesi. TrustedHosts listesine bir sunucu adı ekleme konakları güvenilirliğini deyimi herhangi bir biçimde değerlendirilmemelidir olduğunu lütfen unutmayın - NTLM kimlik doğrulama protokolü, ana hatta bağlandığınız garanti edemez gibi olduğunuz bağlanmak planlıyorsunuz.
Bunun yerine, sunucunun kimliği doğrulanamıyor tarafından oluşturulan hata gizlemek istediğiniz konakların listesini TrustedHosts ayarı düşünmelisiniz.


### <a name="ongoing-communication"></a>Devam eden iletişimleri

İlk kimlik doğrulaması tamamlandıktan sonra [PowerShell uzaktan iletişim protokolü](https://msdn.microsoft.com/library/dd357801.aspx) tüm devam eden iletişimleri oturum başına AES-256'yı simetrik anahtarla şifreler.


## <a name="making-the-second-hop"></a>İkinci atlamayı yapma

Varsayılan olarak PowerShell uzaktan iletişimini (varsa) Kerberos veya NTLM kimlik doğrulaması için kullanır. Bu protokollerin her ikisi de, uzak makineye kimlik bilgileri gönderilmeden kimlik doğrulaması.
Kimlik doğrulaması için en güvenli yolu budur ancak kullanıcının kimlik bilgilerini uzak makineye sahip olmadığından, diğer bilgisayarların ve hizmetlerin kullanıcı adınıza erişemez.
Bu, "ikinci atlama sorun" bilinir.

Bu sorunu önlemek için birkaç yolu vardır. Bu yöntemleri ve açıklamaları olumlu ve olumsuz her için bkz [PowerShell uzaktan iletişim'de ikinci atlamayı yapma](PS-remoting-second-hop.md).