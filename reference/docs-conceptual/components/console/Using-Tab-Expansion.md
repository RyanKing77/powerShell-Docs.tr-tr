---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Sekme Genişletmeyi Kullanma
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031015"
---
# <a name="using-tab-expansion"></a>Sekme Genişletmeyi Kullanma

Komut satırı Kabuk komut girişini hızlandırmak ve ipuçları sağlayan genellikle uzun dosyalarını veya komutları adlarını otomatik olarak tamamlamak için bir yol sağlar. PowerShell sayesinde dosya adları ve cmdlet adları tuşlarına basarak doldurun <kbd>sekmesini</kbd> anahtarı.

> [!NOTE]
> Sekme genişletmeyi iç işlev TabExpansion veya TabExpansion2 tarafından denetlenir. Bu işlev değiştirilmiş veya geçersiz olduğundan, bu tartışma için varsayılan PowerShell yapılandırması davranışını kılavuzudur.

Bir dosya adı veya yolu kullanılabilir seçeneklerden otomatik doldurma, tuşuna basın ve ad bölümünü yazın <kbd>sekmesini</kbd> anahtarı. PowerShell, bulduğu ilk eşleşmeyi adı otomatik olarak genişletilecektir. Tuşuna basarak <kbd>sekmesini</kbd> anahtar art arda geçiş tüm kullanılabilir seçenekleri.

Sekme genişletmeyi cmdlet adları, biraz farklıdır. Sekme genişletmeyi bir cmdlet adı kullanmak için ' % s'adı (Fiili) ve izleyen tire tüm ilk bölümünü yazın. Daha fazla kısmi bir eşleşme için bir ad doldurabilirsiniz. Örneğin, `get-co` ve tuşuna <kbd>sekmesini</kbd> anahtar, PowerShell otomatik olarak bu genişleyecek `Get-Command` cmdlet (, ayrıca standart formlarına büyük/küçük harf değiştiğine dikkat edin). Basarsanız <kbd>sekmesini</kbd> anahtar yeniden PowerShell Bu yalnızca diğer eşleşen cmdlet'i adla değiştirir `Get-Content`.

Sekme genişletmeyi aynı satırda tekrar tekrar kullanabilirsiniz. Sekme genişletmeyi adına gibi kullanabileceğiniz `Get-Content` cmdlet'ini girerek:

```
PS> Get-Con<Tab>
```

Bastığınızda <kbd>sekmesini</kbd> anahtar, komut genişletir:

```
PS> Get-Content
```

Sonra kısmen Active Kurulum günlük dosyası yolunu belirtin ve yeniden sekme genişletmeyi kullanma:

```
PS> Get-Content c:\windows\acts<Tab>
```

Bastığınızda <kbd>sekmesini</kbd> anahtar, komut genişletir:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Bir sekme genişletme işlemi sekmelerin her zaman bir sözcük tamamlama girişiminde yorumlanır sınırlamasıdır. Bir PowerShell konsolunda komut örnekleri kopyalayıp, örnek sekmeleri içermediğinden emin emin olun; aşması durumunda sonuçları tahmin edilemez ve istediğiniz neredeyse kesindir olmayacak.
