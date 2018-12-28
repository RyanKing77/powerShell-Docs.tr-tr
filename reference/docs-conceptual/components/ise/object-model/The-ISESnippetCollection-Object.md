---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippetCollection Nesnesi
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406012"
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection Nesnesi

**Isesnippetcollection** nesnedir koleksiyonu **ISESnippet** nesneleri. İle ilişkili dosyaları koleksiyonu bir **PowerShellTab** nesne bu sınıfın bir üyesidir. Bir örnek **$psISE.CurrentPowerShellTab.Files** koleksiyonu.

## <a name="methods"></a>Yöntemler

### <a name="load-filepathname-"></a>Yük\( FilePathName \)

Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.

Yükleri bir. kullanıcı tarafından tanımlanan kod parçacıkları içeren snippets.ps1xml dosyası. Kod parçacıkları oluşturmak için en kolay yolu, bunları otomatik olarak profil klasörünüzde depolar ve böylece, Windows PowerShell ISE her başlattığınızda yüklenen yeni IseSnippet cmdlet'ini kullanmaktır.

**FilePathName** - dize yolun ve dosya adı için bir. kod parçacığı tanımları içeren snippets.ps1xml dosyası.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Ayrıca bkz:

- [Isesnippet nesnesi](The-ISESnippetObject.md)
- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)