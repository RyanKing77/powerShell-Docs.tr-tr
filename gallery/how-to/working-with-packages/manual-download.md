---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, PowerShell, psgallery
title: Elle Paket İndirme
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215449"
---
# <a name="manual-package-download"></a>Elle Paket İndirme

PowerShell Galerisi, PowerShellGet cmdlet 'leri kullanılmadan doğrudan Web sitesinden bir paketin indirilmesini destekler. Herhangi bir paketi, bir NuGet paketi (`.nupkg`) dosyası olarak indirebilir ve ardından bir iç depoya kopyalayabilirsiniz.

> [!NOTE]
> El ile paket `Install-Module` indirme **, cmdlet** 'in yerini alacak şekilde tasarlanmamıştır.
> Paketin indirilmesi modül veya betiği yüklemez. Bağımlılıklar, indirilen NuGet paketine dahil edilmez. Aşağıdaki yönergeler yalnızca başvuru amaçları için verilmiştir.

## <a name="using-manual-download-to-acquire-a-package"></a>Paket almak için el ile indirme kullanma

Her sayfada, burada gösterildiği gibi el Ile Indirme bağlantısı bulunur:

![El ile Indir](../../Images/packagedisplaypagewithpseditions.png)

El ile indirmek için **Ham nupkg dosyasını indir**' e tıklayın. Paketin bir kopyası, tarayıcınızla `<name>.<version>.nupkg`ilgili indirme klasörüne kopyalanır.

NuGet paketi, paketin içeriğiyle ilgili bilgiler içeren ek dosyalar içeren bir ZIP arşividir. Internet Explorer gibi bazı tarayıcılar `.nupkg` dosya uzantısını ile `.zip`otomatik olarak değiştirir. Paketi genişletmek için, gerekirse `.nupkg` dosyayı olarak `.zip`yeniden adlandırın ve ardından içeriği yerel bir klasöre ayıklayın.

NuGet paket dosyası orijinal paketlenmiş kodun parçası olmayan aşağıdaki **NuGet 'e özgü öğeleri** içerir:

- Adlı `_rels` bir klasör, bağımlılıkları listeleyen `.rels` bir dosya içerir
- Adlı `package` bir klasör, NuGet 'e özgü verileri içerir
- Adlı `[Content_Types].xml` bir dosya-PowerShellGet gibi uzantıların NuGet ile nasıl çalıştığını açıklar
- Adlı `<name>.nuspec` bir dosya, meta verilerin toplu içeriğini içerir

## <a name="installing-powershell-modules-from-a-nuget-package"></a>NuGet paketinden PowerShell modülleri yükleme

> [!NOTE]
> Bu yönergeler **,** çalıştırmaya `Install-Module`aynı sonucu vermez. Bu yönergeler en düşük gereksinimleri karşılar. Bunların yerini alacak `Install-Module`şekilde tasarlanmamıştır.
> Tarafından `Install-Module` gerçekleştirilen bazı adımlar dahil değildir.

En kolay yaklaşım, NuGet 'e özgü öğeleri klasöründen kaldırmalıdır. Öğeleri kaldırmak, paket yazarı tarafından oluşturulan PowerShell kodundan çıkar.
NuGet 'e özgü öğelerin listesi için bkz. [paket edinmek için el ile Indirme kullanma](#using-manual-download-to-acquire-a-package).

Adımlar aşağıdaki gibidir:

1. NuGet paketinin içeriğini yerel bir klasöre ayıklayın.
2. NuGet 'e özgü öğeleri klasörden silin.
3. Klasörü yeniden adlandırın. Varsayılan klasör adı genellikle `<name>.<version>`olur. Modül bir ön sürüm `-prerelease` sürümü olarak etiketlenmişse, bu sürüm dahil olabilir. Klasörü yalnızca modül adıyla yeniden adlandırın. Örneğin, `azurerm.storage.5.0.4-preview` olur `azurerm.storage`.
4. Klasörünü içindeki `$env:PSModulePath value`klasörlerden birine kopyalayın. `$env:PSModulePath`, PowerShell 'in modülleri arayacağı bir noktalı virgülle ayrılmış yol kümesidir.

> [!IMPORTANT]
> El ile indirme, modülün gerektirdiği hiçbir bağımlılığı içermez. Pakette bağımlılıklar varsa, Bu modülün düzgün çalışması için sistemde yüklü olmaları gerekir. PowerShell Galerisi, paket için gereken tüm bağımlılıkları gösterir.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>NuGet paketinden PowerShell betikleri yükleme

> [!NOTE]
> Bu yönergeler **,** çalıştırmaya `Install-Script`aynı sonucu vermez. Bu yönergeler en düşük gereksinimleri karşılar. Bunların yerini alacak `Install-Script`şekilde tasarlanmamıştır.

En kolay yaklaşım, NuGet paketini ayıklamanın ardından betiği doğrudan kullanmaktır.

Adımlar aşağıdaki gibidir:

1. NuGet paketinin içeriğini ayıklayın.
2. Klasördeki `.PS1` dosya doğrudan bu konumdan kullanılabilir.
3. Klasördeki NuGet 'e özgü öğeleri silebilirsiniz.

NuGet 'e özgü öğelerin listesi için bkz. [paket edinmek için el ile Indirme kullanma](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> El ile indirme, modülün gerektirdiği hiçbir bağımlılığı içermez. Pakette bağımlılıklar varsa, Bu modülün düzgün çalışması için sistemde yüklü olmaları gerekir. PowerShell Galerisi, paket için gereken tüm bağımlılıkları gösterir.
