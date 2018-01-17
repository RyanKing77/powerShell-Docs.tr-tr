---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell cmdlet'i
ms.date: 2016-12-12
title: pswaauthorizationrule Al
ms.technology: powershell
ms.openlocfilehash: 003195457660a18b9bbed065181b6d8c23835348
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>ÖZET

Windows PowerShell® Web Erişimi yetkilendirme kuralları kümesi döndürür.

## <a name="syntax"></a>Sözdizimi

### <a name="id"></a>Kimlik
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Ad
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>AÇIKLAMA

**Get-PswaAuthorizationRule** cmdlet'i Windows PowerShell® Web Erişimi yetkilendirme kuralları kümesi döndürür.
Ne **kimliği** parametresi ya da **RuleName** parametresi belirtilirse, sonra Bu cmdlet tüm kuralları listeler. **Kimliği** parametresi, sonuçlara filtre uygulamak için kullanılabilir.

## <a name="parameters"></a>PARAMETRELERİ

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Bu cmdlet alması gereken kuralların tanımlayıcılar (Kimlikler) belirtir. Hiçbir kimlikleri belirtilirse, bu cmdlet tüm yetkilendirme kurallarını döndürür.

|||  
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | yanlış                                |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue, ByPropertyName)       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;dize\[\]&gt;

Almak için yetkilendirme kuralları adlarını belirtir. Bu parametre, bu diziye dizelerde kuralı adları tam olarak eşleşen tüm kuralları döndürür.

|||  
|-|-|
| Diğer adlar                              | yok                                 |
| Gerekli mi?                            | TRUE                                 |
| Konumu?                            | 2                                    |
| Varsayılan Değer                        | yok                                 |
| Ardışık Düzen Girişi kabul edilsin mi?               | TRUE (ByValue, ByPropertyName)       |
| Joker Karakter Kabul Edilsin Mi?          | yanlış                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Bu cmdlet genel parametreleri destekler:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer ve - OutVariable.
Daha fazla bilgi için bkz: [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>GİRİŞLERİ

### <a name="int"></a>int\[\]

Bu cmdlet dizisi veya dize değerlerini bir dizi girdi olarak kabul eder.

### <a name="string"></a>Dize\[\]

Bu cmdlet dizisi veya dize değerlerini bir dizi girdi olarak kabul eder.

## <a name="outputs"></a>ÇIKIŞLARI

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Bu cmdlet bir PswaAuthorizationRule nesnesi çıktı olarak üretir.


## <a name="examples"></a>ÖRNEKLER

### <a name="example-1"></a>ÖRNEK 1

Bu örnekte tüm kurallar alır.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>ÖRNEK 2

Bu örnek Kimliğine sahip bir kural alır *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>Örnek 3 {#example-3 .subHeading}

Bu örnekte, nasıl cmdlet ardışık düzen arasında bir değer kabul gösterilmektedir.
Bu cmdlet, bir kural kimliği ve bir kural adı geçirilir.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>İlgili Konular

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
