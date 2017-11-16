---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSCAutomationHostEnabled kayıt defteri anahtarı"
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
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


