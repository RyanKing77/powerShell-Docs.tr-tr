---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: "pswaauthorizationrule Kaldır"
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>ÖZET

Windows PowerShell® Web Access'ten belirtilen bir yetkilendirme kuralını kaldırır.

## <a name="syntax"></a>SÖZDİZİMİ

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Kural
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

Windows PowerShell Web Erişimi'nden belirtilen bir yetkilendirme kuralını kaldırır.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-force"></a>-Force

Cmdlet'i onay istemeden çalıştırır. Varsayılan olarak cmdlet devam etmeden önce onay ister.

|||  
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | Adlı                                |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | yanlış                                |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-id-ltint32gt"></a>-ID &lt;Int32\[\]&gt;

Tanımlayıcılar (Kimlikler) kaldırmak için bir veya daha fazla kural belirtir.

|||  
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue, ByPropertyName)       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Kural &lt;PswaAuthorizationRule\[\]&gt;

Kaldırmak için kuralları belirtir.

|||  
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue)                       |
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

Cmdlet çalıştırılıyorsa ne olacağını gösterir. Cmdlet çalıştırılmaz.

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

### <a name="int"></a>int\[\]

Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Bu cmdlet dizisi veya bir dizi PswaAuthorizationRule nesneleri kabul eder.

## <a name="outputs"></a>ÇIKIŞLARI

Bu cmdlet herhangi bir çıktı oluşturmaz.

## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu örnek Kimliğine sahip yetkilendirme kuralını kaldırır *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>Örnek 2 {#example-2 .subHeading}

Bu örnekte, tüm yetkilendirme kurallarını kaldırır ve ayrıca kullanıcı tarafından onay gerektirir.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>İlgili Konular

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
