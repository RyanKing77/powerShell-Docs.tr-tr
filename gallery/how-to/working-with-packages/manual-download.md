---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery
title: Elle Paket İndirme
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687702"
---
# <a name="manual-package-download"></a>Elle Paket İndirme

Powershell Galerisi PowerShellGet cmdlet'leri kullanmadan, doğrudan Web sitesinden bir paket indiriliyor destekler. Herhangi bir paket, ardından bir iç deposuna kopyalayabilirsiniz NuGet paketini (.nupkg) dosyası olarak indirebilirsiniz.

> [!NOTE]
> El ile paket **değil** Install-Module cmdlet'i bir ardılı olarak yöneliktir.
> Paket indiriliyor modül veya komut dosyası yüklemez. NuGet paketinin indirilen bağımlılıklar dahil edilmez. Aşağıdaki yönergeler, yalnızca başvuru amacıyla verilmiştir.

## <a name="using-manual-download-to-acquire-a-package"></a>Bir paket almak için el ile yükleme kullanma

Her sayfanın bağlantısını el ile indirmek için burada gösterildiği gibi sahiptir:

![El ile yükleme](../../Images/packagedisplaypagewithpseditions.png)

El ile yüklemek için tıklayın **ham nupkg dosya indirme**. Paketinin bir kopyasını kopyalar indirme klasörü için tarayıcınızı adıyla `<name>.<version>.nupkg`.

Ek dosyaları paket içeriği hakkında bilgi içeren bir ZIP arşivi NuGet paketidir. Internet Explorer gibi bazı tarayıcılar otomatik değiştirme `.nupkg` dosya uzantısıyla `.zip`. Paket genişletmek için yeniden adlandırma `.nupkg` dosyasını `.zip`, gerekli, içeriği yerel bir klasöre ayıklayın.

NuGet paket dosyası, özgün paketli kod parçası olmayan aşağıdaki NuGet özgü öğeleri içerir:

- Adlı bir klasör `_rels` -içeren bir `.rels` bağımlılıkları listeler dosyası
- Adlı bir klasör `package` -NuGet özgü verileri içerir
- Adlı bir dosya `[Content_Types].xml` -PowerShellGet gibi uzantısı NuGet ile nasıl çalıştığı açıklanır
- Adlı bir dosya `<name>.nuspec` -meta verilerin toplu içerir

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Bir NuGet paketinden PowerShell modüllerini yükleme

> [!NOTE]
> Bu yönergeler **yok** çalışan aynı sonucu verir `Install-Module`. Bu yönergeler, en düşük gereksinimleri karşılamak. Bir ardılı olarak amaçlanmamıştır `Install-Module`. Tarafından gerçekleştirilen bazı adımlar `Install-Module` dahil edilmez.

En kolay yaklaşım, NuGet özgü öğeleri klasöründen kaldırmaktır. Bu paketi yazarı tarafından oluşturulan PowerShell kodu bırakır. Adımlar şunlardır:

1. Yerel bir klasöre NuGet paketinin içeriğini ayıklayın.
2. NuGet özgü öğeleri klasöründen silin.
3. Klasörünü yeniden adlandırın. Varsayılan klasör adı genellikle olan `<name>.<version>`. Sürüm içerebilir "-yayın öncesi" modül yayım öncesi bir sürümü etiketlenmiş olması durumunda. Klasörü yeniden adlandırmak için yalnızca modül adı. Örneğin, "azurerm.storage.5.0.4-preview", "azurerm.storage" haline gelir.
4. Klasörlerinde birine klasörünü kopyalayın `$env:PSModulePath value`. `$env:PSModulePath` PowerShell modülleri için görünmelidir yollarının noktalı virgülle ayrılmış kümesidir.

> [!IMPORTANT]
> El ile yükleme modülü tarafından gerekli herhangi bir bağımlılığın içermez. Paket bağımlılıkları varsa, sistemde düzgün çalışması için bu modülü yüklenmelidir. PowerShell Galerisi, paket için gerekli tüm bağımlılıkları gösterir.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>PowerShell betiklerini bir NuGet paketi yükleniyor

> [!NOTE]
> Bu yönergeler **yok** çalışan aynı sonucu verir `Install-Script`. Bu yönergeler, en düşük gereksinimleri karşılamak. Bir ardılı olarak amaçlanmamıştır `Install-Script`.

Kolay ayıklama NuGet paketini ve ardından betiği doğrudan bir yaklaşımdır. Adımlar şunlardır:

1. NuGet paketinin içeriğini ayıklayın.
2. `.PS1` Klasöründeki dosyasını bu konumdan doğrudan kullanılabilir.
3. NuGet özgü öğeleri klasörü silebilir.

> [!IMPORTANT]
> El ile yükleme modülü tarafından gerekli herhangi bir bağımlılığın içermez. Paket bağımlılıkları varsa, sistemde düzgün çalışması için bu modülü yüklenmelidir. PowerShell Galerisi, paket için gerekli tüm bağımlılıkları gösterir.
