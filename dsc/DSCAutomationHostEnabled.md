---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
>Uygulandığı öğe: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled kayıt defteri anahtarı

DSC kullanır **DSCAutomationHostEnabled** kayıt defteri anahtarında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies** ilk önyükleme yukarı yerindeki makinede yapılandırmasını etkinleştirmek için.
DSCAutomationHostEnabled üç modlarını destekler:

|  DSCAutomationHostEnabled değeri  |  Açıklama   |
|---|---|
0 | Makine önyükleme yukarı yapılandırma devre dışı bırakın. |
1 | Makine önyükleme yukarı yapılandırma etkinleştirin. |
2 | Yalnızca DSC ise makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu. Bu varsayılan değerdir. |

## <a name="see-also"></a>Ayrıca bkz:

İlk önyükleme yukarı yapılandırmaları çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz: [DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma](bootstrapDsc.md).