---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: "Kaydet-komut dosyası"
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2017
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

[Kaydet-komut dosyası](http://go.microsoft.com/fwlink/?LinkId=619786)

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

