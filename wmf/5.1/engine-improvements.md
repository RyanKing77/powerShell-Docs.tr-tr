---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 PowerShell altyapısı iyileştirmeleri
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687450"
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

> [!Note]
> Desteklenmeyen bazı senaryolar için başlatma ilgili bir değişiklik etkileyebilir.
> PowerShell artık, dosyaları okur `$pshome\*.ps1xml` --bu dosyaları bazı dosya önlemek için C# için olarak dönüştürüldü ve XML işlem yükünü CPU dosyaları.
> Dosya içeriğini değiştirirseniz V5, yalnızca V2 için herhangi bir etkisi olmaz şekilde dosyaları yan yana V2 desteklemek için hala mevcut.
> Bu dosyaların içeriğini değiştirme, desteklenen bir senaryo asla olup olmadığını unutmayın.

Başka bir görünür bir değişiklik, dışarı aktarılan komutlar ve diğer bilgileri sistemde yüklü modüller için PowerShell'i nasıl önbelleğe aldığını ' dir.
Daha önce bu önbellek dizinde depolanan `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
WMF 5.1, tek bir dosyayı bir önbellektir `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Bkz: [modül çözümleme önbellek](scenarios-features.md#module-analysis-cache) daha fazla ayrıntı için.