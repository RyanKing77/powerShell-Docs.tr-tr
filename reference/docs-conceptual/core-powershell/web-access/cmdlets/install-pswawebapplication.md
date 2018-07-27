---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268308"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>ÖZETİ

Windows PowerShell Web erişimi web uygulamasını IIS yapılandırır.

## <a name="syntax"></a>SÖZ DİZİMİ

### <a name="default"></a>Varsayılan
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Install-PswaWebApplication** cmdlet'i, Windows PowerShell Web erişimi web uygulaması yapılandırır.
Web uygulaması yükler, bir web sitesi ile ilişkilendirir ve isteğe bağlı olarak bir test SSL sertifikası kullanarak oluşturur. Bu cmdlet **useTestCertificate** parametresi. İçin güvenlik nedeniyle web yöneticilerinin üretim ortamları için bir test sertifikası kullanmamalısınız.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-usetestcertificate"></a>-UseTestCertificate

Bir test sertifikası oluşturulduğunu belirtir. Bu parametre, bu cmdlet bir test sertifikası oluşturur ve HTTPS isteklerinde sertifikayı kullanmak için Windows PowerShell Web erişimi web uygulamasını yapılandırır, true olarak ayarlanmışsa. Bu parametre false olarak ayarlarsanız, hiçbir sertifika veya bağlama oluşturulur. Windows PowerShell Web erişimi için başka bir sertifika kullandıysanız, bu değeri false olarak ayarlayın.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | TRUE                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Web uygulamanız için bir ad belirtir. Bu Windows PowerShell Web erişimi URL'si son parçası olarak görüntülenir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | pswa                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-websitename"></a>-WebSiteName

Bu Windows PowerShell Web erişimi web uygulamasını yüklemek için Web sunucusu (IIS) Web sitesinin adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | Varsayılan Web sitesi                     |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-confirm"></a>-Confirm

Cmdlet'i çalıştırmadan önce sizden onay ister.

|||
|-|-|
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yanlış                                |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-whatif"></a>-WhatIf

Cmdlet çalıştırılıyorsa ne olacağını gösterir.
Cmdlet çalıştırılmaz.

|||
|-|-|
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | adlı                                |
| Varsayılan Değer                        | yanlış                                |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable. Daha fazla bilgi için [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>GİRİŞ

Bu cmdlet herhangi bir giriş alır.

## <a name="outputs"></a>ÇIKIŞLAR

Bu cmdlet herhangi bir çıktı üretmez.

## <a name="examples"></a>ÖRNEKLERİ

### <a name="example-1"></a>ÖRNEK 1

Bu örnek için varsayılan değerleri kullanarak PSWA web uygulamasına yükler **WebApplicationName** (*pswa*) ve **WebSiteName** (*varsayılan Web sitesi* ) parametreleri.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>ÖRNEK 2

Bu örnek, bir test sertifikası ve varsayılan değerleri kullanarak PSWA web uygulaması yükler. **WebApplicationName** ve **WebSiteName** parametreleri.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>İlgili Konular

- [Ekle-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)