---
ms.topic: reference
keywords: PowerShell cmdlet'i
ms.date: 12/12/2016
title: Kaldırma-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a>Kaldırma-PswaWebApplication

## <a name="synopsis"></a>ÖZET

Windows PowerShell® web uygulamasını kaldırır.

## <a name="syntax"></a>SÖZDİZİMİ

### <a name="default"></a>Varsayılan
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Uninstall-PswaWebApplication** cmdlet'i Windows PowerShell web uygulamasını kaldırır ve IIS Web sitesi kaldırır. Cmdlet, IIS veya Windows PowerShell'i çalıştırmak gerekli olduğundan yüklü diğer özellikler kaldırılmaz.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Sınama sertifikaları tarafından oluşturulan gösterir **yükleme\_PswaWebApplication** cmdlet (ile **UseTestCertificate** parametresi) silinir.
Yalnızca sınama sertifikası tarafından oluşturulan aynı ada sahip **Install-PswaWebApplication** cmdlet kaldırılır.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | TRUE                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;dize&gt;

Kaldırmak için web uygulamasının adını belirtir.

|||
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | 1                                    |
| Varsayılan Değer                        | pswa                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;dize&gt;

Web uygulamasının yüklendiği web sitesi adını belirtir.

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

Bu cmdlet, hiçbir çıkış döndürür.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu komut için Windows PowerShell Web uygulamasını kaldırır.
Varsayılan değerleri kullanarak yüklediyseniz, Windows PowerShell Web uygulamasını kaldırmak için bu cmdlet'i kullanabilirsiniz.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>ÖRNEK 2

Bu komut için Windows PowerShell Web uygulamasını kaldırır ve uygulama ile ilişkili test sertifikasını siler.
Varsayılan değerleri kullanarak yüklediyseniz ve bir test sertifikası oluşturulan Windows PowerShell Web uygulamasını kaldırmak için bu cmdlet'i kullanabilirsiniz.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>Örnek 3 {#example-3 .subHeading}

Yükleme sırasında bir özel Web sitesi ve uygulama belirtildiğinde bu komut için Windows PowerShell Web uygulamasını kaldırır.
Adlı Web sitesini komut kaldırır *Sitem* ve adlı uygulama *TestApplication* ve uygulama ile ilişkili test sertifikalar da silinip silinmediğini belirtir.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>İlgili Konular

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)