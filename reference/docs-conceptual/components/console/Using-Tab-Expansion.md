---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Sekme Genişletmeyi Kullanma
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406048"
---
# <a name="using-tab-expansion"></a>Sekme Genişletmeyi Kullanma

Komut satırı Kabuk komut girişini hızlandırmak ve sağlama genellikle uzun dosyalarını veya komutları adlarını otomatik olarak tamamlamak için bir yol sağlar. Windows PowerShell sayesinde dosya adları ve cmdlet adları tuşlarına basarak doldurun **sekmesini** anahtarı.

> [!NOTE]
> Sekme genişletmeyi iç işlev TabExpansion veya TabExpansion2 tarafından denetlenir. Bu işlev değiştirilmiş veya geçersiz olduğundan, bu tartışma için varsayılan PowerShell yapılandırması davranışını kılavuzudur.

Bir dosya adı veya yolu kullanılabilir seçeneklerden otomatik doldurma, tuşuna basın ve ad bölümünü yazın **sekmesini** anahtarı. PowerShell, bulduğu ilk eşleşmeyi adı otomatik olarak genişletilecektir. Tuşuna basarak **sekmesini** anahtar art arda geçiş tüm kullanılabilir seçenekleri.

Sekme genişletmeyi cmdlet adları, biraz farklıdır. Sekme genişletmeyi bir cmdlet adı kullanmak için ' % s'adı (Fiili) ve izleyen tire tüm ilk bölümünü yazın. Daha fazla kısmi bir eşleşme için bir ad doldurabilirsiniz. Örneğin, **get-co** ve tuşuna **sekmesini** anahtar, PowerShell otomatik olarak bu genişleyecek **Get-Command** cmdlet (bildirim, ayrıca durum değiştirir harfini standart formlarına). Basarsanız **sekmesini** anahtar yeniden PowerShell Bu yalnızca diğer eşleşen cmdlet'i adla değiştirir **Get-Content**.

Sekme genişletmeyi aynı satırda tekrar tekrar kullanabilirsiniz. Sekme genişletmeyi adına gibi kullanabileceğiniz **Get-Content** cmdlet'ini girerek:

```
PS> Get-Con<Tab>
```

Bastığınızda **sekmesini** anahtar, komut genişletir:

```
PS> Get-Content
```

Sonra kısmen Active Kurulum günlük dosyası yolunu belirtin ve yeniden sekme genişletmeyi kullanma:

```
PS> Get-Content c:\windows\acts<Tab>
```

Bastığınızda **sekmesini** anahtar, komut genişletir:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Bir sekme genişletme işlemi sekmelerin her zaman bir sözcük tamamlama girişiminde yorumlanır sınırlamasıdır. Bir PowerShell konsolunda komut örnekleri kopyalayıp, örnek sekmeleri içermediğinden emin emin olun; aşması durumunda sonuçları tahmin edilemez ve istediğiniz neredeyse kesindir olmayacak.