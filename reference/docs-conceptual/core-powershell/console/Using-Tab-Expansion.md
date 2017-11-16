---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Sekme genişletme kullanma"
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a>Sekme genişletme kullanma
Komut satırı Kabukları komut girişini hızlandırmak ve sağlama genellikle uzun dosyalarını veya komutları adlarını otomatik olarak tamamlamak için bir yol sağlar. Windows PowerShell tuşlarına basarak dosya adlarını ve cmdlet adları doldurmanıza olanak sağlar **sekmesini** anahtarı.

> [!NOTE]
> Sekme genişletme iç işlev TabExpansion veya TabExpansion2 tarafından denetlenir. Bu işlev değiştirilmiş veya geçersiz olduğundan, bu tartışma varsayılan PowerShell yapılandırması davranışını Kılavuzu kalır.

Bir dosya adı veya yolu kullanılabilir seçeneklerden otomatik olarak doldurun, kısmını basın ve adını yazın **sekmesini** anahtarı. PowerShell, bulduğu ilk eşleşmeye adı otomatik olarak genişletilir. Tuşuna basarak **sekmesini** anahtar art arda geçiş tüm kullanılabilir seçenekleri.

Cmdlet adları sekmesini genişlemesi biraz farklıdır. Bir cmdlet adı sekmesini genişletme kullanmak için (fiil) adı ve izleyen tire tüm ilk bölümünü yazın. Daha fazla kısmi eşleşme için ad doldurabilirsiniz. Örneğin, **get-co** ve tuşuna basın **sekmesini** anahtar, PowerShell otomatik olarak bu genişletecek **Get-Command** cmdlet (bildirim, ayrıca durum değiştirir harfini standart formlarına). Basarsanız **sekmesini** anahtar yeniden PowerShell Bu yalnızca diğer eşleşen cmdlet adla değiştirir **Get-Content**.

Sekme genişletme aynı çizgi üzerinde tekrar tekrar kullanabilirsiniz. Örneğin, adına sekmesini genişletme kullanabilirsiniz **Get-Content** girerek cmdlet:

```
PS> Get-Con<Tab>
```

Bastığınızda **sekmesini** için anahtar, komut genişletir:

```
PS> Get-Content
```

Daha sonra kısmen Active Kurulum günlük dosyası yolunu belirtin ve yeniden sekmesini genişletme kullanın:

```
PS> Get-Content c:\windows\acts<Tab>
```

Bastığınızda **sekmesini** için anahtar, komut genişletir:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Bir sekme genişletme işlemi sekmelerin her zaman tam bir sözcük girişimleri yorumlanır kısıtlamasıdır. Bir PowerShell konsolunda komut örnekleri kopyalayıp, örnek sekmeleri içermiyor emin olun; varsa, sonuçlar öngörülemez olacaktır ve istediğiniz neredeyse kesinlikle olmaz.

