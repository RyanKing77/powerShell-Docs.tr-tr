---
title: Yardım dosyalarını nasıl güncelleştireceğinizi | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082326"
---
# <a name="how-to-update-help-files"></a>Yardım Dosyalarını Güncelleştirme

Bu konu, güncelleştirilebilir Yardımı'nı destekleyen bir modül için Yardım dosyalarını nasıl güncelleştireceğinizi açıklar.

## <a name="updating-help-files"></a>Yardım dosyaları güncelleştiriliyor

Yardım dosyaları, hataları düzeltme, bir kavramı açıklığa kavuşturan, sık sorulan soru yanıtlama, yeni dosyaları ekleme veya yeni ve daha iyi örnekleri ekleme gibi güncelleştirmek için birçok neden vardır.

Yardım dosyasını güncelleştirmek için:

1. Dosyaları değiştirin.

2. Dosyalar diğer UI kültürü çevir.

3. Tüm Yardım dosyaları (yeni, değiştirilmiş ve değişmeden) için her UI kültürü modülünde toplayın.

4. Dosyaları XML şemasına karşı doğrulayın.

5. CAB dosyaları her UI kültürü için yeniden oluşturun.

6. HelpInfo XML dosyasında sürüm numaralarının her UI kültürü için CAB dosyasının artırın.

7. Değeri tarafından belirtilen konuma yeni CAB dosyaları karşıya yükleme **HelpContentUri** HelpInfo XML dosyasında öğe. Eski CAB dosyaları, CAB dosyaları yeni değiştirin.

8. Tarafından belirtilen konuma güncelleştirilmiş HelpInfo XML dosyasını karşıya yükleme **HelpInfoUri** modül bildirimindeki anahtar. Eski HelpInfo XML dosyası yeni dosya ile değiştirin.