---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190154"
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>ÖZET

Bir kural belirtilen kullanıcı, bilgisayar veya uç nokta için mevcut olup olmadığını doğrular.

## <a name="syntax"></a>SÖZDİZİMİ

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Test-PswaAuthorizationRule** cmdlet, bir kural belirtilen kullanıcı, bilgisayar veya uç nokta için mevcut olup olmadığını doğrular.
Bu cmdlet, belirli bir kullanıcı, bilgisayar veya uç nokta erişim isteği yetkili olduğunu doğrulamak için yetkilendirme kuralları, test etmek için de kullanılabilir.
Varsayılan olarak, bu cmdlet yetkilendirme dosyasında tüm kuralları değerlendirir.
Ancak, test etmek için kurallar kümesini belirtebilirsiniz.

Kimlik doğrulama hataları gidermek için bu cmdlet'i kullanabilirsiniz.

Bu cmdlet parametrelerini alanları Windows PowerShell® Web Access oturum açma sayfasında karşılık gelir.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;dize&gt;

Test etmek için bilgisayar adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;dize&gt;

Test etmek için Windows PowerShell oturum yapılandırmasını, uç nokta veya çalışma alanı olarak da bilinen adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | 3                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;URI&gt;

Bağlantıyı sınamak için URI belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Belirten bir **PSCredential** Windows PowerShell Web Erişimi yetkilendirme kuralları test etmek için kullanmak istediğiniz bir kullanıcı hesabı için nesnesi. Bu parametreyi eklemezseniz cmdlet şu anda oturum açmış kullanıcı hesabını kullanır. Alınacak bir **PSCredential** yetkilendirme kuralları uzaktan test, çalıştırmak için gerekli olan nesne, [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet'i.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Kural &lt;PswaAuthorizationRule\[\]&gt;

Test etmek için kurallar kümesini belirtir. Bu parametre belirtilmezse, bu cmdlet'i tüm yetkilendirme kurallarını karşı sınar.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue)                       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;dize&gt;

Test etmek için kullanıcı adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.
Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>GİRİŞLERİ

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Bu cmdlet PswaAuthorizationRule nesneleri içeren bir dizi girdi olarak kabul eder.

## <a name="outputs"></a>ÇIKIŞLARI

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Bu cmdlet PswaAuthorizationRule nesnelerinin bir dizisi çıktı olarak üretir.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu örnekte, kullanıcı izin veren tüm kuralları görüntülemek için tüm yetkilendirme kurallarını testleri *contoso\\mhanson* bilgisayara bağlanmak için *SUN2* ve bir Windows PowerShell oturumu kullanın adlı Yapılandırması *test*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>ÖRNEK 2

Hangi Yetkilendirme kurallarını denetlemek için tüm yetkilendirme kuralları geçerli kullanıcıya bu örnekte testleri *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>İlgili Konular

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)