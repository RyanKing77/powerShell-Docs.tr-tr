---
title: 'Güncelleştirilebilir Yardım Yazma: Adım adım | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082133"
---
# <a name="updatable-help-authoring-step-by-step"></a>Güncelleştirilebilir Yardım Yazma: Adım Adım

Bu belgeler güncelleştirilebilir Yardımı yazma işleminde adımları listelenir.

## <a name="authoring-updatable-help-step-by-step"></a>Güncelleştirilebilir Yardımı yazma: Adım Adım

Güncelleştirilebilir Yardımı, son kullanıcılar için tasarlanmıştır ancak modül yazarları Ayrıca önemli avantajlar sağlar ve içerik ekleme olanağı dahil olmak üzere Yardım yazıcıları, hataları düzeltin, birden çok UI kültürde sunun ve uzun sonra kullanıcı yorumları ve istekleri, yanıt Modül sevk edildi. Bu konu nasıl paketini açıklar ve karşıya yükleme Yardım dosyaları ve böylece kullanıcılar indirebilir ve bunları kullanarak yükleyin [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri.

Aşağıdaki adımlar, güncelleştirilebilir Yardımı destekleme sürecine genel bir bakış sağlar.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>1. Adım: Yardım dosyalarınız için bir Internet sitesini Bul

Güncelleştirilebilir Yardımı oluşturmanın ilk adımı, modülün Yardım dosyaları için bir Internet konum bulmaktır. Aslında, iki farklı konuma kullanabilirsiniz. Modülün Yardım bilgi dosyası (HelpInfo XML - aşağıda açıklanmıştır), bir Internet konumu ve başka bir Internet konumda Yardım içeriği CAB dosyalarını tutabilirsiniz. Tüm Yardım içerik CAB dosyaları bir modül için aynı konumda olmalıdır. Farklı modüller için Yardım içeriği CAB dosyalarını aynı konuma yerleştirebilirsiniz.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>2. Adım: Modül bildiriminizi HelpInfoURI anahtar ekleme

Ekleme bir **HelpInfoURI** , modül bildirimine anahtar. Modülünüzün HelpInfo XML bilgi dosyasının konumu Tekdüzen Kaynak Tanımlayıcısı (URI) anahtar değeridir. Güvenlik için adres "http" veya "https" ile başlamalıdır. URI bir Internet konumu belirtmeniz gerekir, ancak HelpInfo XML dosya adı içermemesi gerekir.

Örneğin:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>3. Adım: HelpInfo XML dosyası oluşturun

Yardım dosyaları ve sürüm numaralarını, desteklenen her UI kültürü modülünde en yeni Yardım dosyaları, Internet konumunu URI HelpInfo XML bilgi dosyası içerir. Her bir Windows PowerShell modülü bir HelpInfo XML dosyası vardır. Yardım dosyaları güncelleştirdikten sonra düzenleme veya HelpInfo XML dosyasını değiştirin; başka bir eklemeyin. Daha fazla bilgi için [HelpInfo XML dosyasının nasıl oluşturulacağı](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>4. adım: Yardım dosyaları oturum

Dijital imzalar gerekli değildir, ancak dosyaları paylaştığı her iyi öneri oldukları.

### <a name="step-5-create-cab-files"></a>5. adım: CAB dosyaları oluşturma

Oluşturulacak MakeCab.exe gibi dolap (.cab) dosya oluşturur aracını bir. Modülünüzün Yardım dosyaları içeren CAB dosyası. Yardım dosyaları için ayrı bir CAB dosyası içinde her desteklenen UI kültürü oluşturun. Daha fazla bilgi için [hazırlama güncelleştirilebilir Yardımı CAB dosyaları nasıl](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>6. adım: Dosyalarınızı karşıya yükleyin

Yeni veya güncelleştirilmiş Yardım dosyaları yayımlamak için CAB dosyaları tarafından belirtilen Internet konuma karşıya yükleme **HelpContentUri** HelpInfo XML dosyasında öğe. Ardından, değeri tarafından belirtilen Internet konuma HelpInfo XML dosyasını karşıya **HelpInfoUri** modül bildirimindeki anahtar.
