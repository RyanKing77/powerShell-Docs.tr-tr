---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "WMF 5.1 PowerShell altyapısı yenilikleri"
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a>PowerShell altyapısı geliştirmeleri

WMF 5.1, çekirdek PowerShell altyapısı aşağıdaki iyileştirmeleri uygulanmıştır:


## <a name="performance"></a>Performans ##

Performans bazı önemli alanlarında geliştirilmiştir:

- Başlatma
- ForEach-Object ve Where-Object gibi cmdlet öğelerini ardışık düzen yaklaşık % 50 daha hızlı'dir 

Bazı örnek iyileştirmeleri (sonuçlarınızı donanımınıza bağlı olarak değişebilir): 

| Senaryo | 5.0 süresi (ms) | 5.1 süresi (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell çalıştırma ilk hiç:`powershell -command "Unknown-Command"` | 30000 | 13000 |
| Yerleşik komutu analiz önbellek:`powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
> Bir değişiklik için başlatma ilgili bazı etkileyebilecek Not senaryoları desteklenmiyor. 
> PowerShell artık dosyaları okur `$pshome\*.ps1xml` --bu dosyaları bazı dosya önlemek için C# için olarak dönüştürülen ve XML işlem yükünü CPU dosyaları. 
Dosya içeriğini değiştirirseniz, bu V5, yalnızca V2 için herhangi bir etkisi kalmaması dosyaları yan yana destek V2 hala mevcut. 
Bu dosyaların içeriğini değiştirme, desteklenen bir senaryo asla olup olmadığını unutmayın.

Başka bir görünür PowerShell dışarı aktarılan komutlar ve diğer bilgileri bir sistemde yüklü modülleri için nasıl önbelleğe alınacağını değişikliktir. Bu önbellek dizinde depolanan daha önce `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. WMF 5.1, tek bir dosya önbelleğidir `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Bkz: [modülü analiz önbellek](scenarios-features.md#module-analysis-cache) daha fazla ayrıntı için.

