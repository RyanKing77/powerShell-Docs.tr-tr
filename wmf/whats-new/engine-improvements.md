---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 PowerShell altyapısı iyileştirmeleri
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856185"
---
# <a name="powershell-engine-improvements"></a>PowerShell altyapısı iyileştirmeleri

WMF 5.1 aşağıdaki çekirdek PowerShell altyapısı iyileştirmeleri uygulanmıştır:

## <a name="performance"></a>Performans

Bazı önemli alanda performans geliştirilmiştir:

- Başlatma
- Gibi cmdlet'leri için ardışık düzen `ForEach-Object` ve `Where-Object` yaklaşık % 50 daha hızlıdır

Bazı örnek iyileştirmeleri (sonuçlarınızı donanımınıza bağlı olarak farklılık gösterebilir):

| Senaryo | 5.0 süresi (ms) | 5.1 süresi (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| PowerShell'i çalıştırmak ilk hiç olmadığı kadar: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Yerleşik komut analiz önbellek: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!NOTE]
> Desteklenmeyen bazı senaryolar için başlatma ilgili bir değişiklik etkileyebilir. PowerShell artık, dosyaları okur `$pshome\*.ps1xml` --bu dosyaları dönüştürülmüştür C# bazı dosya ve XML dosyalarını işleme CPU ek yükünü önlemek için. Dosya içeriğini değiştirirseniz V5, yalnızca V2 için herhangi bir etkisi olmaz şekilde dosyaları yan yana V2 desteklemek için hala mevcut. Bu dosyaların içeriğini değiştirme, desteklenen bir senaryo asla olup olmadığını unutmayın.

Başka bir görünür bir değişiklik, dışarı aktarılan komutlar ve diğer bilgileri sistemde yüklü modüller için PowerShell'i nasıl önbelleğe aldığını ' dir. Daha önce bu önbellek dizinde depolanan `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. WMF 5.1, tek bir dosyayı bir önbellektir `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Bkz: [modül çözümleme önbellek](release-notes.md#module-analysis-cache) daha fazla ayrıntı için.