---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISESnippetCollection nesnesi
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a>ISESnippetCollection nesnesi
  **ISESnippetCollection** nesnesidir koleksiyonu **ISESnippet** nesneleri. İle ilişkili dosyaları koleksiyonu bir **PowerShellTab** nesne bu sınıfın bir üyesidir. Örnek **$psISE.CurrentPowerShellTab.Files** koleksiyonu.

## <a name="methods"></a>Yöntemler

### <a name="load-filepathname-"></a>Yük\( FilePathName\)
  Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil. 

 Yükleri bir. kullanıcı tanımlı parçacıkları içeren snippets.ps1xml dosyası. Parçacıkları oluşturmak için en kolay yolu, otomatik olarak bunları profili klasörünüzde depolar ve böylece Windows PowerShell ISE her başlattığınızda yüklenen yeni IseSnippet cmdlet'ini kullanmaktır.

 **FilePathName** - dize yolun ve dosya adı için bir. parçacığı tanımları içeren snippets.ps1xml dosyası.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Ayrıca bkz:
- [ISESnippetObject](The-ISESnippetObject.md) 
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE nesne modeli hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)

  
