---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: WinRMSecurity
ms.openlocfilehash: e390a84b6f7a1932afdad84c7b09ce7da2ec5370
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-remoting-security-considerations"></a>PowerShell uzaktan iletişim güvenlik konuları

PowerShell uzaktan iletişimi, Windows sistemleri yönetmek için önerilen yoldur. PowerShell uzaktan iletişimi, Windows Server 2012 R2'de varsayılan olarak etkindir. Bu belge PowerShell uzaktan iletişimini kullanırken, güvenlik sorunlarının, öneriler ve en iyi yöntemler ele alınmaktadır.

## <a name="what-is-powershell-remoting"></a>PowerShell uzaktan iletişimi nedir?

PowerShell uzaktan iletişimi kullandığından [Windows Uzaktan Yönetim (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), Microsoft uyarlamasını olduğu [Yönetim (WS-Management) için Web Hizmetleri](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) kullanıcıların PowerShell çalıştırmasına izin vermek için protokol komutları uzak bilgisayarlarda. PowerShell uzaktan iletişim sırasında kullanma hakkında daha fazla bilgi bulabilirsiniz [çalıştıran uzak komutları](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell uzaktan iletişimini kullanma ile aynı değil **ComputerName** çalıştırmak için temel protokolü olarak uzak yordam çağrısı (RPC) kullanan bir uzak bilgisayarda bir cmdlet parametresi.

## <a name="powershell-remoting-default-settings"></a>PowerShell uzaktan iletişim varsayılan ayarları

PowerShell uzaktan iletişimi (ve WinRM) aşağıdaki bağlantı noktalarını dinlemek:

- HTTP: 5985
- HTTPS: 5986

Varsayılan olarak, PowerShell uzaktan iletişim bağlantıları yalnızca Administrators grubunun üyeleri sağlar. Oturumlar, böylece tüm işletim sistemi erişim denetimleri bireysel kullanıcılara uygulanan ve grupları bunları PowerShell uzaktan iletişimi bağlıyken uygulanmaya devam kullanıcının bağlamında başlatılır.

Özel ağlarda PowerShell uzaktan iletişim için varsayılan Windows Güvenlik duvarı kuralı tüm bağlantıları kabul eder. Genel ağlarda, varsayılan Windows Güvenlik duvarı kuralı aynı alt ağda yalnızca gelen PowerShell uzaktan iletişim bağlantıları sağlar. Ortak ağ üzerindeki tüm bağlantılar için PowerShell uzaktan iletişimi'ni açın, kural açıkça değiştirmeniz gerekir.

>**Uyarı:** ortak ağlara için güvenlik duvarı kuralı bilgisayarı dış bağlantı kötü amaçlı saldırılara karşı korumak için tasarlanmıştır. Bu kural kaldırırken dikkatli olun.

## <a name="process-isolation"></a>İşlem yalıtımı

PowerShell uzaktan iletişimi kullandığından [Windows Uzaktan Yönetim (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) bilgisayarlar arasındaki iletişim.
WinRM Network Service hesabının altında bir hizmet olarak çalışır ve ana bilgisayar PowerShell örnekleri için kullanıcı hesapları olarak çalışan yalıtılmış işlemler olarak çoğaltılır. Bir kullanıcı olarak çalışan PowerShell örneği PowerShell örneği başka bir kullanıcı olarak çalışan bir işlemi hiçbir erişebilir.

## <a name="event-logs-generated-by-powershell-remoting"></a>PowerShell uzaktan iletişimi tarafından oluşturulan olay günlükleri

FireEye olay günlüklerini ve PowerShell uzaktan iletişim oturumları, adresinde tarafından oluşturulan diğer güvenlik kanıt iyi özetini sağlanan [PowerShell saldırılarının araştırılması](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Şifreleme ve aktarım protokolleri

PowerShell uzaktan iletişim bağlantı iki perspektiften güvenlik düşünmek faydalıdır: ilk kimlik doğrulaması ve devam eden iletişimleri.

Kullanılan Aktarım Protokolü bağımsız olarak (HTTP veya HTTPS), PowerShell uzaktan iletişim ilk kimlik doğrulamasından sonra tüm iletişimi her zaman bir oturum başına AES 256 simetrik anahtarla şifreler.

### <a name="initial-authentication"></a>İlk kimlik doğrulaması

Kimlik doğrulama - sunucu ve ideal - istemci sunucuya istemcinin kimliğini doğrular.

Bir istemci bilgisayar adını kullanarak bir etki alanı sunucusuna bağlandığında (örn: server01, veya server01.contoso.com), varsayılan kimlik doğrulama protokolüdür [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos yeniden kullanılabilir kimlik bilgisi herhangi bir tür göndermeden kullanıcı kimliği ve sunucu kimliğini garanti eder.

İstemci IP adresini kullanarak bir etki alanı sunucusuna bağlanarak veya bir çalışma grubu sunucusuna bağlanır, Kerberos kimlik doğrulaması mümkün değil. PowerShell uzaktan iletişimi dayanan bu durumda, [NTLM kimlik doğrulama protokolü](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). NTLM kimlik doğrulama protokolü, herhangi bir tür delegable kimlik bilgisi göndermeden kullanıcı kimliğini garanti eder. Kullanıcı kimliğini kanıtlamak için NTLM protokolü istemci ve sunucu bir oturum anahtarı kullanıcının parolayı hiç parola değişimi olmadan işlem gerektirir. Kullanıcının parolayı biliyor ve sunucu için oturum anahtarı hesaplar etki alanı denetleyicisi ile iletişim kurar şekilde sunucunun kullanıcı parolasının genellikle bilmez.

NTLM protokolü ancak, sunucu kimliğini garanti etmez. Protokollerle kimlik doğrulaması için NTLM kullanan tüm gibi bir etki alanına katılmış bilgisayarın makine hesabına erişim izni olan bir saldırgan etki alanı denetleyicisi bir NTLM oturum anahtarı işlem ve böylece sunucu özelliklerini çağıramadı.

NTLM tabanlı kimlik doğrulaması varsayılan olarak devre dışıdır, ancak hedef sunucuda yapılandırma ya da SSL veya istemcide WinRM TrustedHosts ayarını yapılandırarak izin verilir.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>NTLM tabanlı bağlantılarını sırasında sunucu kimliğini doğrulamak için SSL sertifikalarını kullanma

NTLM kimlik doğrulama protokolü (yalnızca zaten, parolanızı bilir) hedef sunucunun kimliğini garanti edemez olduğundan, hedef sunucular PowerShell uzaktan iletişim için SSL kullanacak şekilde yapılandırabilirsiniz. (Ayrıca istemcinin güvendiği bir sertifika yetkilisi tarafından verilen değilse) hedef sunucuya bir SSL sertifikası atama kullanıcı kimliği ve sunucu kimliğini garanti eder, NTLM tabanlı kimlik doğrulamasını etkinleştirir.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>NTLM tabanlı sunucu kimlik hataları yoksayma

NTLM bağlantıları için bir sunucuya bir SSL sertifikası dağıtma uyuşmazlığa ise, WinRM ile sunucu ekleyerek elde edilen kimlik hataları gözardı **TrustedHosts** listesi. Lütfen bir sunucu adı TrustedHosts listesine ekleme deyimi ana bilgisayarlarının kendilerini güvenilirliği hakkında herhangi bir biçimde düşünülmemelidir olduğunu not - NTLM kimlik doğrulama protokolü ana bilgisayara aslında bağlanan garanti edemez gibi olduğunuz bağlanmak planlayan.
Bunun yerine, sunucunun kimliğini doğrulayamadı tarafından oluşturulan hata gizlemek istediğiniz ana bilgisayarların listesini TrustedHosts ayarı göz önünde bulundurmalısınız.


### <a name="ongoing-communication"></a>Devam eden iletişimleri

İlk kimlik doğrulaması tamamlandıktan sonra [PowerShell uzaktan iletişim protokolü](https://msdn.microsoft.com/en-us/library/dd357801.aspx) tüm devam eden iletişimleri oturum başına AES 256 simetrik anahtarla şifreler.


## <a name="making-the-second-hop"></a>İkinci atlama yapma

Varsayılan olarak, PowerShell uzaktan iletişimi (varsa) Kerberos veya NTLM kimlik doğrulaması için kullanır. Bu protokollerin her ikisi de, uzak makineye kimlik bilgileri gönderilmeden kimlik doğrulaması.
Bu, kimlik doğrulaması için en güvenli yoldur ancak uzak makineye kullanıcının kimlik bilgilerine sahip olmadığından diğer bilgisayarlar ve hizmetler kullanıcı adınıza erişemez.
Bu "ikinci atlama sorun" bilinir.

Bu sorunu önlemek için birkaç yolu vardır. Bu yöntemler ve açıklamaları uzmanları avantajlarını ve dezavantajlarını her için bkz: [ikinci atlama PowerShell uzaktan iletişimi yapma](PS-remoting-second-hop.md).