---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>ÖZET

Windows PowerShell® Web Access web uygulaması IIS'de yapılandırır.

## <a name="syntax"></a>SÖZDİZİMİ

### <a name="default"></a>Varsayılan
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Install-PswaWebApplication** cmdlet'i Windows PowerShell Web erişimi web uygulaması yapılandırır. Bu cmdlet web uygulamasını yükler, bir web sitesi ile ilişkilendirir ve isteğe bağlı olarak bir SSL sertifikası kullanarak test oluşturur **useTestCertificate** parametresi. Güvenlik nedeniyle web yöneticileri üretim ortamları için bir test sertifikası kullanmamalısınız.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-usetestcertificate"></a>-UseTestCertificate

Bir test sertifikası oluşturulduğunu belirtir. Bu parametre, bu cmdlet bir test sertifikası oluşturur ve HTTPS isteklerinde sertifikayı kullanmak üzere Windows PowerShell Web erişimi web uygulaması yapılandırır true olarak ayarlanmışsa. Bu parametre false olarak ayarlanırsa, hiçbir sertifika veya bağlama oluşturulur. Başka bir sertifika Windows PowerShell Web erişimi için kullanılıyorsa, bu değeri false olarak ayarlayın.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | TRUE                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;dize&gt;

Web uygulamanız için ad belirtir. Bu Windows PowerShell Web erişim URL'si son parçası olarak görüntülenir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | pswa                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;dize&gt;

Bu Windows PowerShell Web erişimi web uygulamasını yüklemek için Web sunucusu (IIS) Web sitesi adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | Varsayılan Web sitesi                     |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-confirm"></a>-Confirm

Cmdlet'i çalıştırmadan önce sizden onay ister.

|||
|-|-|
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yanlış                                |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-whatif"></a>-WhatIf

Cmdlet çalıştırılıyorsa ne olacağını gösterir.
Cmdlet çalıştırılmaz.

|||
|-|-|
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yanlış                                |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.
Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>GİRİŞLERİ

Bu cmdlet herhangi bir giriş alır.

## <a name="outputs"></a>ÇIKIŞLARI

Bu cmdlet herhangi bir çıktı oluşturmaz.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu örnek için varsayılan değerleri kullanarak PSWA web uygulamasına yükler **WebApplicationName** (*pswa*) ve **WebSiteName** (*varsayılan Web sitesi* ) parametreleri.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>ÖRNEK 2

Bu örnek, bir test sertifikası ve varsayılan değerleri kullanarak PSWA web uygulamasını yükler. **WebApplicationName** ve **WebSiteName** parametreleri.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>İlgili Konular

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)