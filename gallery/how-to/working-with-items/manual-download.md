---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeri, powershell, psgallery
title: El ile paket indirme
ms.openlocfilehash: 7d228ccea9b840e4850d03a7a2e3e1c71e11d95e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523398"
---
# <a name="manual-package-download"></a>El ile paket indirme

Powershell Galerisi PowerShellGet cmdlet'leri kullanmadan, doğrudan Web sitesinden bir paket indiriliyor destekler. Paket, daha sonra kolayca iç bir depoya kopyalanabilir bir NuGet paketi (.nupkg) dosyası olarak indirilir.

> [!NOTE]
> El ile paket **değil** Install-Module cmdlet'i bir ardılı olarak yöneliktir.
> Paket indiriliyor modül veya komut dosyası yüklemez. NuGet paketinin indirilen bağımlılıklar dahil edilmez. Aşağıdaki yönergeler, yalnızca başvuru amacıyla verilmiştir.

## <a name="using-manual-download-to-acquire-a-package"></a>Bir paket almak için el ile yükleme kullanma

Her sayfanın bağlantısını el ile indirmek için burada gösterildiği gibi sahiptir:

![El ile yükleme](../../Images/Manual_Item_Download.PNG)

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
4. Klasör için PSModulePath kopyalayın.

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
