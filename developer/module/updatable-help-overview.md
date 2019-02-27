---
title: Güncelleştirilebilir Yardımı genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847491"
---
# <a name="updatable-help-overview"></a>Güncelleştirilebilir Yardıma Genel Bakış

Bu belge, tasarım ve Windows PowerShell güncelleştirilebilir Yardımı özelliğinin işlemi temel bir giriş sağlar. Modül yazarları ve başkaları tarafından Windows PowerShell Yardımı, kullanıcılara sunmak için tasarlanmıştır.

## <a name="introduction"></a>Giriş

Windows PowerShell Yardımı Windows PowerShell deneyimi ayrılmaz bir parçasıdır. Windows PowerShell modülleri gibi Yardım konuları sürekli olarak güncelleştirilen ve yazarlar ve Windows PowerShell kullanıcıları Topluluğu Katkı tarafından geliştirildi.

*Güncelleştirilebilir Yardımı* özelliği, Windows PowerShell 3.0 sürümünde sunulan, kullanıcıların Yardım konuları en yeni sürümleri komut isteminde, yerleşik Windows PowerShell komutları için bile yeni modüller indirmeden olmasını sağlar veya Windows Update çalışıyor. Güncelleştirilebilir Yardımı, Internet'ten en yeni Yardım konuları sürümlerini indirin ve kullanıcının yerel bilgisayarda doğru dizinlerdeki yükleyin cmdlet'leri sağlayarak basit hale getirir. Güvenlik duvarının arkasındaki kullanıcılar bile, yeni cmdlet'ler, bir iç dosya paylaşımından güncelleştirilmiş Yardım almak için kullanabilirsiniz.

Güncelleştirilebilir Yardımı tam olarak tüm Windows PowerShell modülleri Windows® 8 ve Windows Server® 2012 tarafından desteklenen ve özellikleri Windows PowerShell modülü yazarları için kullanılabilir. Güncelleştirilebilir Yardımı yalnızca XML tabanlı Yardım dosyalarını destekler. Açıklama tabanlı Yardım desteklemez.

Güncelleştirilebilir Yardımı aşağıdaki özellikleri içerir.

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kullanıcıların en yeni Yardım sahip olup olmadığını belirleyen cmdlet, dosyaları bir modül için ve, aksi takdirde, Internet'ten en yeni Yardım dosyalarını indirir, bunları ayıklar ve bunları doğru modül dizinlerde yükler kullanıcının bilgisayarına. Kullanıcılar [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet'i yeni yüklediğiniz Yardım konuları hemen görüntüleyin. Windows PowerShell yeniden başlatmanız gerekmez.

- [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) en yeni Yardım indirir cmdlet'i, dosyaları Internet'ten ve bunları bir dosya sistemi dizine kaydeder. Kullanıcılar `Update-Help` cmdlet Yardım dosyalarını dosya sistemi dizinden almak ve paketini açın ve kullanıcının bilgisayarında modülü dizinlerdeki yükleyin. `Save-Help` Cmdlet'i, sınırlı kullanıcılar ya da Internet erişimi yok ve Internet erişimi sınırlamak için tercih ettiğiniz kuruluşlar için tasarlanmıştır.

- **Bir modül için yardımcı**. Bir modül için Yardım dosyaları yönetilir ve kullanıcıların kullandıkları modüller için Yardım dosyalarının tümünü sınıflandırıp bir birim olarak teslim. Güncelleştirilebilir Yardımı, modüller, Windows PowerShell ek bileşenleri için değil yalnızca için desteklenir.

- **Sürüm desteği**. Güncelleştirilebilir Yardımı standart dört konumu (N1. kullanır. N2. N3. Sürüm numaraları N4). Güncelleştirilebilir Yardımı, kullanıcının bilgisayarında bulunan sürüm numarasını Yardım dosyaları Yardım dosyalarını indirir (veya `Save-Help` dizin) Yardım dosyalarını Internet konumda sürüm numarasını düşüktür.

- **Çok dil desteği**. Güncelleştirilebilir Yardımı içinde birden çok UI kültürü modülü Yardım dosyalarını destekler. Güncelleştirilebilir Yardımı dosya adlarında "en-US" ve "ja-JP" gibi standart dil kodlarını ve `Update-Help` ve `Save-Help` cmdlet'leri Yardım dosyaları dile özgü alt modül dizinini, yerleştirin.

- **Otomatik olarak oluşturulmuş Yardım**. [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'i temel Yardım için Yardım dosyalarına sahip olmayan komutları görüntüler. Otomatik olarak oluşturulmuş Yardım komut sözdizimini ve diğer adlar ve çevrimiçi Yardım ve güncelleştirilebilir Yardımı kullanımıyla ilgili yönergeleri içerir.

- **Gelişmiş çevrimiçi Yardım**. Kolay erişim çevrimiçi Yardım için Yardım dosyaları artık gerektirmez. **Çevrimiçi** parametresinin `Get-Help` cmdlet'i şimdi değerinden bir çevrimiçi Yardım konusu URL'sini alır **HelpUri** özelliği bir Yardım dosyasında da çevrimiçi Yardım URL'si bulamazsanız, herhangi bir komutu. Doldurabilirsiniz **HelpUri** özelliği ekleyerek bir **HelpUri** özniteliğini kullanarak veya cmdlet, İşlevler ve CIM komutları koda **. Bağlantı** açıklama tabanlı Yardım iş akışları ve betikler yönergesinde.

  Bizim Yardım dosyaları güncelleştirilebilir hale getirmek için Windows PowerShell modülleri Windows 8 ve Windows Server vnext'te Yardım dosyaları ile gelmeyen. Kullanıcılar, Yardım dosyaları yüklemek ve güncelleştirmek için güncelleştirilebilir Yardımı'ni kullanabilirsiniz. Diğer modüllerin yazarları modüllerde Yardım dosyalarını ekleyebilir veya bunları çıkarın. Güncelleştirilebilir Yardımı için destek, isteğe bağlı ancak önerilen değerdir.
