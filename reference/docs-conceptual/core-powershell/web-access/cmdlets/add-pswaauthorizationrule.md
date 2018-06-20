---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190392"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>ÖZET

Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.

## <a name="syntax"></a>Sözdizimi

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Add-PswaAuthorizationRule** cmdlet, Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesine yeni bir yetkilendirme kuralı ekler.

Kullanıcılar, bilgisayarlar ve bu kural için Windows PowerShell uç noktaları belirtmeniz gerekir. Kullanıcılar ve bilgisayarlar bireysel kullanıcı hesapları ve bilgisayar adları ya da grupları belirterek belirtebilirsiniz.

Bir Active Directory etki alanına katılmış bir bilgisayar için cmdlet kuralı oluşturmak için bilgisayar güvenlik tanımlayıcısı (SID) kullanır.
Bu sayede kısa bir ad, bir tam etki alanı adı (FQDN) veya bir IP adresi için kullanılacak **bilgisayar adı** oturum açma sayfasında alan.

Bir Active Directory etki alanına katılmamış bir bilgisayar için cmdlet yönetici tarafından sağlanan bilgisayar adını kullanarak kural oluşturur. Son kullanıcı başarılı bir şekilde bu makineye bağlanmak için kuralda göründüğü gibi bilgisayar adı sağlamanız gerekir.

Ağ üzerinde aynı ada sahip birden çok bilgisayar varsa, kısa adı birden fazla bilgisayara çözebilirsiniz. Bu bağlantı kurarken belirsizlik için yol açabilir. Adlı çalışma grubu bilgisayarı için bir kuralı varsa, örneğin, "*Sunucu1*" adlı yeni bir bilgisayar *server1.contoso.com* katılmışsa ağa yetkilendirme kurallarını kullanarak doğrulama başarılı olur ve Windows PowerShell Web erişimi çalışır adlı bilgisayara bir bağlantı kurmak "*Sunucu1*". Bu belirtilen çalışma grubu bilgisayarı ile bağlantı kurulur kesin değildir; çalışma grubu veya adlı etki alanı bilgisayarda denemesi yapılamadı "*Sunucu1*". Belirsizliği azaltmak için hedef bilgisayar için mümkün olduğunca bir yetkilendirme kuralı oluşturmak FQDN kullanmanız önerilir.

Birincil oturum açma kimlik bilgileri Windows PowerShell Web erişimi kullanıcılarının olmayan alternatif kimlik bilgileri yetkilendirme kuralları değerlendirin (ikinci kimlik bilgileri kümesi bulunan **isteğe bağlı bağlantı ayarlarını** bölümü oturum açma sayfası). Bu örneği için örnek 6'ya bakın.

## <a name="parameters"></a>Parametreler

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

Active Directory etki alanı Hizmetleri (AD DS) veya yerel gruplar için bu kural erişimine izin verdiği bir bilgisayar grubunun adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;dize&gt;

Bu kural erişim verdiği bilgisayar adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;dize&gt;

Windows PowerShell oturumu configuration olarak da bilinen bu kural erişim verdiği çalışma alanının adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Belirten bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kurallarını değiştirmek için kullanmak istediğiniz bir kullanıcı hesabı için nesnesi. Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır. Alınacak bir **PSCredential** uzaktan yetkilendirme kuralları eklemek için çalıştırmak için gerekli olan nesne, [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet'i.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-force"></a>-Force

Komutu için kullanıcı onayı istemeden çalışmaya zorlar. \
Ayrıca, bir basit veya kısa bir bilgisayar adı (örneğin, bir etki alanı adı değil veya tam değil adı) girdiğinizde de onaylamanızı ister. Böylece yalnızca bilgisayar bir çalışma grubunda ise bir bilgisayar eklemek için basit bir ad kullanabilirsiniz onay güvenlik nedenleriyle istendi.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;dize&gt;

Bu kural için kolay adı belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;dize\[\]&gt;

AD DS veya bu kural erişim verdiği yerel gruplar bir veya daha fazla kullanıcı grubu adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;dize\[\]&gt;

Bu kural erişim verdiği bir veya daha fazla kullanıcı belirtir. Kullanıcı adı, ağ geçidi bilgisayarında veya AD DS'de bir kullanıcı bir yerel kullanıcı hesabı olabilir.
Biçim `domain\user` veya `computer\user`.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue, ByPropertyName)       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.
Daha fazla bilgi için bkz: [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>GİRİŞLERİ

### <a name="string"></a>Dize

Bu cmdlet bir dize veya dize dizisi giriş olarak kabul eder.

### <a name="string"></a>Dize\[\]

Bu cmdlet bir dize veya dize dizisi giriş olarak kabul eder.

## <a name="outputs"></a>Çıkışlar

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Bu cmdlet döndürür ve bir yetkilendirme kuralı nesne.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu örnekte oturum yapılandırma erişim verir *PSWAEndpoint*, bir çalışma alanı, kısıtlanmış *SUN2* kullanıcılar için *SMAdmins* grup. \
**Not**: bilgisayar adı bir tam etki alanı adı (FQDN) olmalıdır. Yöneticiler, sınırlı bir oturum yapılandırması veya sınırlı bir cmdlet'ler ve son kullanıcıların çalıştırabileceği görevleri aralığıdır çalışma tanımlayın. Sınırlı bir çalışma alanı tanımlanması, kullanıcıların izin verilen Windows PowerShell® çalışma alanında, böylece daha güvenli bir bağlantı sunulmamaktadır diğer bilgisayarlara erişmesini engelleyebilir. Oturum yapılandırmaları hakkında daha fazla bilgi için bkz: [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) veya [yükleme ve kullanım Windows PowerShell Web erişimi](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>ÖRNEK 2

Bu örnek varsayılan Windows PowerShell oturum yapılandırması, erişim veren `Microsoft.PowerShell`, *SUN2* contoso adlı kullanıcılar kullanıcılar için\\Kullanıcı1, contoso\\user2 ve contoso\\KULLANICI3. Bu cmdlet, üç kurallar (kişi başına 1) oluşturur.

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>ÖRNEK 3

Bu örnekte, kullanıcı adı değerleri ardışık düzeni aracılığıyla giriş göstermektedir.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>ÖRNEK 4

Bu örnekte gösterilmiştir tüm parametreleri özellik adı ardışık düzen değerlerinden ele nasıl.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>ÖRNEK 5

Bu örnek adlı yerel kullanıcı izin verme kuralı ekler *PswaServer\\ChrisLocal* adlı sunucuya erişimi *srv1.contoso.com*.

Bu örnekte, ağ geçidi bir çalışma grubunda ve hedef bilgisayar bir etki alanında olduğu yerde bir senaryo gösterilmektedir. Yetkilendirme kural, ağ geçidinde yerel kullanıcılar için geçerlidir. Windows PowerShell Web erişimi oturum açma sayfasında, kimliğini başarıyla doğrulamak için kullanıcı kimlik bilgilerini ikinci bir set sağlamalısınız **isteğe bağlı bağlantı ayarlarını** alanı. Ağ Geçidi sunucusu, hedef bilgisayardaki adlı bir sunucusu kullanıcının kimliğini doğrulamak için ek kimlik bilgileri kümesini kullanır. *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>ÖRNEK 6

Bu örnekte tüm kullanıcıların tüm bilgisayarlarda tüm uç noktaları erişmesini sağlar.
Bu temelde yetkilendirme kuralları devre dışı bırakır. \
**Not**: kullanımı `*` joker karakter güvenlik açısından duyarlı dağıtımları için önerilmez ve yalnızca test ortamları için kabul veya güvenlik nerede gevşetilebilir dağıtımlarında kullanılan.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Ayrıca bkz:

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Üye Ekle](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [Yeni nesne](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)