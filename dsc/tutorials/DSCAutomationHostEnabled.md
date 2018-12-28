---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405691"
---
>Şunun için geçerlidir: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled kayıt defteri anahtarı

DSC kullandığı **DSCAutomationHostEnabled** kayıt defteri anahtarı altında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies** ilk önyükleme yukarı makinenin yapılandırmasını etkinleştirmek için.
DSCAutomationHostEnabled üç modunu destekler:

|  DSCAutomationHostEnabled değeri  |  Açıklama   |
|---|---|
0 | Makine önyüklemede yapılandırma devre dışı bırakın. |
1 | Makine önyüklemede yapılandırma etkinleştirin. |
2 | Yalnızca DSC ise, makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu. Bu varsayılan değerdir. |

## <a name="see-also"></a>Ayrıca bkz:

İlk önyüklemede yapılandırma çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz [DSC kullanarak ilk önyüklemede bir sanal makine yapılandırma](bootstrapDsc.md).