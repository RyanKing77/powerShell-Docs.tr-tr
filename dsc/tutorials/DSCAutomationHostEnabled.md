---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076505"
---
>Şunun için geçerlidir: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled kayıt defteri anahtarı

DSC kullandığı **DSCAutomationHostEnabled** kayıt defteri anahtarı altında **hkey_local_machıne\software\microsoft\windows\currentversion\policies\system** makinenin başlangıç yapılandırmasını etkinleştirmek için önyükleme artırma.
**DSCAutomationHostEnabled** üç modunu destekler:

|  DSCAutomationHostEnabled değeri  |  Açıklama   |
|---|---|
0 | Makine önyüklemede yapılandırma devre dışı bırakın. |
1 | Makine önyüklemede yapılandırma etkinleştirin. |
2 | Yalnızca DSC ise, makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu. Varsayılan değer budur. |

## <a name="see-also"></a>Ayrıca bkz:

İlk önyüklemede yapılandırma çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz [DSC kullanarak ilk önyüklemede bir sanal makine yapılandırma](bootstrapDsc.md).
