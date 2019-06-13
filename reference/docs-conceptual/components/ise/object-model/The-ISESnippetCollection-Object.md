---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippetCollection Nesnesi
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030505"
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
