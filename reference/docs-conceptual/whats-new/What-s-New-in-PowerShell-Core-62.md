---
title: PowerShell Core 6.2 yenilikler nelerdir?
description: Yeni özellikler ve PowerShell Core 6.2 yayımlanan değişiklikleri
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750039"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2 yenilikler nelerdir?

Seçimi önemli yeni özellikler ve PowerShell Core 6.2 ' sunulan değişiklikler bazıları aşağıdadır.

Ayrıca **ton** boyunca "daha hızlı ve daha kararlı (Ayrıca, birçok ve çok sayıda hata düzeltmesi) PowerShell olun bence olarak"!
Değişikliklerin tam listesi için kullanıma sunduğumuz [github'da changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Ve bazı adları diyoruz sırasında kullandığınız için teşekkür ederiz [tüm topluluğa katkıda bulunanlar](https://github.com/PowerShell/PowerShell/graphs/contributors) yapılması bu sürümde mümkün.

## <a name="engine-updates-and-fixes"></a>Altyapı güncelleştirmeleri ve düzeltmeleri

- PowerShell uzaktan iletişimini etkinleştirme/devre dışı cmdlet'i uyarı iletilerini ekleyin ([#9203][])
- Düzeltme `FormatTable` uzak seri durumundan çıkarma regresyon ([#9116][])
- Görev-tabanlı güncelleştirme `async` API'lerini doğrudan bir görev nesnesi döndürmek için PowerShell eklendi ([#9079][])
- 5 ekleyin `InvokeAsync` aşırı yüklemeler ve `StopAsync` için `PowerShell` türü ([#8056][]) (teşekkürler @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Genel Cmdlet güncelleştirmeleri ve düzeltmeleri

- Etkinleştirme `SecureString` cmdlet'leri için Windows olmayan düz metin depolayarak ([#9199][])
- Geçersiz ileti Ekle `Send-MailMessage` ([#9178][])
- Düzeltme `Restart-Computer` üzerinde çalışılacak `localhost` WinRM olmadığında mevcut ([#9160][])
- Olun `Start-Job` PowerShell barındırıldığında sonlandırma hatası throw ([#9128][])
- İçin güncelleştirme sürüm `PowerShell.Native` ve testleri barındırma ([#8983][])

## <a name="breaking-changes"></a>Hataya Neden Olan Değişiklikler

Windows PowerShell ile tutarlı olmasını Write-Output içinde - NoEnumerate davranışı düzeltmek ([#9069][]) (teşekkürler @vexx32!)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
