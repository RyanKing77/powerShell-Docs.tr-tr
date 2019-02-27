---
title: Açıklama tabanlı Yardım sözdizimi | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846497"
---
# <a name="syntax-of-comment-based-help"></a>Yorum Tabanlı Yardım Söz Dizimi

Bu bölümde, açıklama tabanlı Yardım söz dizimini açıklar.

## <a name="syntax-diagram"></a>Söz dizimi diyagramı

 Açıklama tabanlı Yardım için sözdizimi aşağıdaki gibidir:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Söz dizimi açıklaması

 Açıklama tabanlı Yardım açıklamaları dizisi olarak yazılır. Açıklama simgesini (#) açıklamaları önce her bir satır yazın ya da kullanabilirsiniz "\<#" ve "#>" açıklama bloğu oluşturmak için semboller. Açıklama bloğu içinde tüm satırları açıklamalar olarak yorumlanır.

 Açıklama tabanlı Yardım her bölüm bir anahtar tarafından tanımlanır ve her anahtar sözcüğün bir nokta (.) tarafından öncesinde. Anahtar sözcükler, herhangi bir sırada görünebilir. Anahtar adları büyük küçük harfe duyarlı değildir.

 Açıklama bloğu, en az bir Yardım anahtar sözcüğü içermesi gerekir. Bazı anahtar sözcükler gibi örnek, aynı açıklama bloğunda birden çok kez görünebilir. Her anahtar sözcüğü için Yardım içeriği satırda anahtar sözcüğü sonra başlar ve birden fazla satırı kapsayabilir.

 Tüm satırları açıklama tabanlı Yardım konusunun bitişik olması gerekir. Yardım konusunun bir parçası olmayan bir yorum açıklama tabanlı Yardım konusunun izleyen son Yardım olmayan yorum satırını açıklama tabanlı Yardım başlangıcı arasındaki en az bir boş satır olmalıdır.

 Örneğin, aşağıdaki açıklama tabanlı Yardım konusu içerir. Açıklama anahtar sözcüğü ve bir işlev veya betiği açıklamasını kendi değeri.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```