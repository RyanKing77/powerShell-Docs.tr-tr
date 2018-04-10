---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: Kaydet-komut dosyası
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a>Kaydet-komut dosyası

Kaydet-komut dosyası cmdlet belirtilen bir konuma kaydederek komut dosyasını gözden geçirmenizi sağlar.

## <a name="description"></a>Açıklama

Kaydet-komut dosyası cmdlet'i belirtilen komut dosyası kaydeder.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Örnek komutlar

### <a name="example-1-save-a-script-from-a-repository"></a>Örnek 1: bir depodan bir komut dosyasını kaydetme
Bu komut komut yerel klasörde C:\ScriptSharingDemo Fabrikam-ClientScript GalleryINT depodan en son sürümünü kaydeder

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Örnek 2: yöneltme bulma komut dosyası cmdlet'inden tarafından bir komut dosyasının bir sürümünü kaydedin.

İlk komut Fabrikam ClientScript GalleryINT depodan 1.5 sürümünü bulur ve C:\ScriptSharingDemo klasörüne kaydeder

İkinci komut kaydedilmiş komut dosyası meta verileri doğrular.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Örnek 3: bir depodan bir komut dosyası bir ön sürümünü Kaydet
Bu komut komut yerel klasörde C:\ScriptSharingDemo Fabrikam-ClientScript GalleryINT depodan en son sürümünü kaydeder

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```