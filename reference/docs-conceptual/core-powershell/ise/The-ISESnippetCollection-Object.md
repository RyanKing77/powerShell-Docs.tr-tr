---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippetCollection Nesnesi
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection Nesnesi

**ISESnippetCollection** nesnesidir koleksiyonu **ISESnippet** nesneleri. İle ilişkili dosyaları koleksiyonu bir **PowerShellTab** nesne bu sınıfın bir üyesidir. Örnek **$psISE.CurrentPowerShellTab.Files** koleksiyonu.

## <a name="methods"></a>Yöntemler

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.

Yükleri bir. kullanıcı tanımlı parçacıkları içeren snippets.ps1xml dosyası. Parçacıkları oluşturmak için en kolay yolu, otomatik olarak bunları profili klasörünüzde depolar ve böylece Windows PowerShell ISE her başlattığınızda yüklenen yeni IseSnippet cmdlet'ini kullanmaktır.

**FilePathName** - dize yolun ve dosya adı için bir. parçacığı tanımları içeren snippets.ps1xml dosyası.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Ayrıca bkz:

- [The ISESnippetObject](The-ISESnippetObject.md)
- [Nesne modeli komut dosyası Windows PowerShell ISE amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)