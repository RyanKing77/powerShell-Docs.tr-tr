---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094237"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>ÖZETİ

Yeni bir yetkilendirme kuralı için Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesi ekler.

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

**Add-PswaAuthorizationRule** cmdlet'i yeni bir yetkilendirme kuralı için Windows PowerShell® Web Erişimi yetkilendirme kuralı kümesi ekler.

Kullanıcılar, bilgisayarlar ve bu kural için Windows PowerShell uç noktası belirtmeniz gerekir. Kullanıcılar ve bilgisayarlar bireysel kullanıcı hesapları ve bilgisayar adlarını veya grup belirleyerek belirtebilirsiniz.

Bir Active Directory etki alanına katılmış bir bilgisayar için cmdlet kuralı oluşturmak için bilgisayarın güvenlik tanımlayıcısı (SID) kullanır.
Bu sayede kısa bir ad, bir tam etki alanı adı (FQDN) veya bir IP adresi için kullanılacak **bilgisayar adı** alan oturum açma sayfasında.

Bir Active Directory etki alanına katılmamış bir bilgisayarda, cmdlet, yönetici tarafından sağlanan bilgisayar adını kullanarak kuralı oluşturur. Son Kullanıcı başarıyla bu makineye bağlanmak için kuralda göründüğü gibi bilgisayar adı sağlamanız gerekir.

Ardından ağ üzerinde aynı ada sahip birden çok bilgisayar varsa, kısa ad birden fazla bilgisayara çözebilirsiniz. Bir bağlantıyı kurarken bu için karışıklığa neden olabilir. Adlı çalışma grubu bilgisayarı için bir kuralı varsa, örneğin, "*Sunucu1*" adlı yeni bir bilgisayar *server1.contoso.com* katıldığından ağa yetkilendirme kurallarını kullanarak doğrulama başarılı olur ve Windows PowerShell Web erişimi çalışır adlı bilgisayara bir bağlantı kurmak "*Sunucu1*". Bu bağlantı ile belirtilen bilgisayar kurulduktan garanti edilmez; çalışma grubu veya adlı etki alanı bilgisayarda denemesi yapılamadı "*Sunucu1*". Belirsizliği azaltmak için hedef bilgisayar için mümkün olduğunca bir yetkilendirme kuralı oluşturmak FQDN kullanmanız önerilir.

Birincil oturum açma kimlik bilgisi alternatif kimlik bilgilerini değil Windows PowerShell Web erişimi kullanıcı yetkilendirme kuralları değerlendirin (ikinci bir dizi kimlik bilgisi bulundu **isteğe bağlı bağlantı ayarları** bölümü oturum açma sayfası). Bu örneği için örneğin 6'ya bakın.

## <a name="parameters"></a>Parametreler

### <a name="-computergroupname-string"></a>-ComputerGroupName \<dize\>

Active Directory etki alanı Hizmetleri (AD DS) veya yerel gruplar bu kural erişim veren bir bilgisayar grubunun adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-computername-string"></a>-ComputerName \<dize\>

Bu kural erişim veren bilgisayar adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-configurationname-string"></a>-ConfigurationName \<dize\>

Windows PowerShell oturumu yapılandırması, olarak da bilinen bu kural erişim veren çalışma adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Belirtir bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kuralları değiştirmek için kullanmak istediğiniz bir kullanıcı hesabı için nesne. Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır. Alınacak bir **PSCredential** uzaktan yetkilendirme kuralları eklemek, çalıştırmak için gerekli olan nesne [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet'i.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-force"></a>-Force

Komutu kullanıcı onayı istemeden çalışmaya zorlar. \
Ayrıca, bir basit veya kısa bir bilgisayar adı (örneğin, bir etki alanı adı değil veya tam değil bir addır) girdiğinizde, ayrıca onaylamanızı ister. Böylece bir bilgisayar yalnızca bilgisayar bir çalışma grubunda ise eklemek için basit bir ad kullanabilirsiniz güvenlik nedenleriyle, onay istenir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-rulename-string"></a>-RuleName \<dize\>

Bu kuralın kolay adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<dize\[\]\>

AD DS veya yerel gruplar bu kural erişim veren bir veya daha fazla kullanıcı grubu adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByPropertyName)                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-username-string"></a>-UserName \<dize\[\]\>

Bu kural erişim veren bir veya daha fazla kullanıcı belirtir. Kullanıcı adı, ağ geçidi bilgisayarınıza veya AD DS'de bir kullanıcı bir yerel kullanıcı hesabı olabilir.
Biçim `domain\user` veya `computer\user`.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue, ByPropertyName)       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.
Daha fazla bilgi için [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>GİRİŞ

### <a name="string"></a>Dize

Bu cmdlet bir dize veya dizeler dizisi girdi olarak kabul eder.

### <a name="string"></a>Dize\[\]

Bu cmdlet bir dize veya dizeler dizisi girdi olarak kabul eder.

## <a name="outputs"></a>Çıkışlar

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Bu cmdlet döndürür bir yetkilendirme kuralı nesnesine.

## <a name="examples"></a>ÖRNEKLERİ

### <a name="example-1"></a>ÖRNEK 1

Bu örnekte oturum yapılandırması erişimi verir _PSWAEndpoint_, sınırlı çalışma alanı _SUN2_ kullanıcılar için _SMAdmins_ grubu.

> [!NOTE]
> Bilgisayar adı tam etki alanı adı (FQDN) olmalıdır. Yöneticiler, sınırlı bir oturum yapılandırması veya sınırlı bir cmdlet'ler ve son kullanıcıların görevleri aralığıdır çalışma alanı tanımlayın. Sınırlı bir çalışma alanı tanımlanması, kullanıcıların izin verilen Windows PowerShell® çalışma alanında, bu nedenle daha güvenli bir bağlantı sunulmamaktadır diğer bilgisayarlara erişmesini engelleyebilir. Oturum yapılandırmaları hakkında daha fazla bilgi için bkz. [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) veya [yükleme ve kullanım Windows PowerShell Web erişimi](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>ÖRNEK 2

Bu örnek, varsayılan Windows PowerShell oturum yapılandırması erişimi verir `Microsoft.PowerShell`, *SUN2* adlı kullanıcıları kullanıcılar için `contoso\user1`, `contoso\user2`, ve `contoso\user3`. Bu cmdlet, üç kuralları (kişi başına 1) oluşturur.

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>ÖRNEK 3

Bu örnekte, işlem hattı aracılığıyla kullanıcı adı değerleri giriş gösterilmektedir.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>ÖRNEK 4

Bu örnekte nasıl tüm parametreler özellik adına göre işlem hattından değerleri alın.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>ÖRNEK 5

Bu örnek adlı yerel kullanıcı izin verecek bir kural ekler `PswaServer\ChrisLocal` adlı sunucuda erişim **srv1.contoso.com**.

Bu örnekte, burada bir çalışma grubundaki ağ geçididir ve hedef bilgisayar bir etki alanında bir senaryo gösterilmektedir. Yetkilendirme kuralı Gateway'de yerel kullanıcılar için geçerlidir. Windows PowerShell Web erişimi oturum açma sayfasında, kimliğini başarıyla doğrulamak için kullanıcı kimlik bilgilerini ikinci bir set sağlamalıdır **isteğe bağlı bağlantı ayarları** alan. Ağ Geçidi sunucusu, kullanıcı hedef bilgisayarda adlı bir sunucu kimlik doğrulaması için ek kimlik bilgileri kümesini kullanır. *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>ÖRNEK 6

Bu örnekte, tüm kullanıcıların tüm bilgisayarlarda tüm uç noktalara erişimi verir.
Bu temelde, yetkilendirme kuralları devre dışı bırakır.

> [!NOTE]
> Kullanım `*` joker karakter güvenlik açısından duyarlı dağıtımları için önerilmez ve yalnızca test ortamları için kabul veya güvenlik burada gevşetilebilir dağıtımda kullanılan.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Ayrıca bkz:

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Üye Ekle](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[Yeni nesne](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)