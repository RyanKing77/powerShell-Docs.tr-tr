---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSCAutomationHostEnabled kayıt defteri anahtarı"
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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


