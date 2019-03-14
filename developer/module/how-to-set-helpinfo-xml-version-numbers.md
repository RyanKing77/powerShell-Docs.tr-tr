---
title: HelpInfo XML sürüm numaraları ayarlama | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794357"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML Sürüm Numaralarını Ayarlama

Bu konu başlığında, ayarlayın ve genellikle bir "HelpInfo XML dosyası." olarak bilinen bir güncelleştirilebilir bilgi dosyasında sürüm numaralarının artırmak açıklanmaktadır

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo XML Sürüm Numaralarını Ayarlama

Sürüm numaraları HelpInfo XML dosyasında, güncelleştirilebilir Yardımı çalışması için kritik öneme sahiptir. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet'leri, yalnızca uzak HelpInfo XML dosyasındaki bir UI kültürü için sürüm numarası bu UI kültürü için sürüm numarasından daha büyük olduğunda yeni Yardım dosyalarını indirme Yerel HelpInfo XML veya yerel HelpInfo XML dosyası yok.

Tanımlanan 4 bölümde sürüm numarasını HelpInfo XML dosyasını kullanan **System.Version** Microsoft .NET Framework sınıfı. Biçim `N1.N2.N3.N4`. Modül yazarları tarafından verilen düzeni numaralandırma herhangi bir sürümünü kullanabilir **System.Version** sınıfı. Güncelleştirilebilir Yardımı gerektirir yalnızca sürüm numarası için kullanıcı Arabirimi kültürünü artışı CAB dosyası bu UI kültürü için yeni bir sürümü tarafından belirtilen konuma yüklendiğinde **HelpContentURI** HelpInfo XML dosyasında öğe.

Aşağıdaki örnek, Almanca (de-DE) UI kültür için sürüm 2.15.0.10 olduğunda HelpInfo XML dosyasının öğeleri gösterir.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

UI kültürü için sürüm numarası, bu UI kültürü için CAB dosyası sürümü yansıtır. Sürüm numarası, tüm CAB dosyası için geçerlidir. CAB dosyası içinde farklı dosyalar farklı sürüm numaralarını ayarlanamaz. Her UI kültürü için sürüm numarası bağımsız olarak değerlendirilir ve modülün desteklediği diğer UI kültürü için sürüm numaraları için ilgili olmayan.