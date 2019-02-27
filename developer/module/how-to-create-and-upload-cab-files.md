---
title: Oluşturma ve CAB dosyaları karşıya yükle | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848667"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB Dosyaları Oluşturma ve Karşıya Yükleme

Bu konu, güncelleştirilebilir Yardımı CAB dosyaları oluşturmak ve bunları güncelleştirilebilir Yardımı cmdlet'leri bunları nereden konumuna yükleme işlemini açıklar.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Oluşturma ve güncelleştirilebilir Yardımı CAB dosyaları karşıya yükleme

Bir modülün birden çok dil ve kültür için yeni veya güncelleştirilmiş Yardım dosyaları sunmak için güncelleştirilebilir Yardımı özelliğini kullanabilirsiniz. Bir modül için güncelleştirilebilir Yardımı bir paketi tek HelpInfo XML dosyasından oluşur ve bir veya daha fazla dolap (. CAB) dosyası. CAB dosyası her bir kullanıcı Arabirimi kültürünü modülünde Yardım dosyalarını içerir. Güncelleştirilebilir Yardımı için CAB dosyası oluşturmak için aşağıdaki yordamı kullanın.

1. UI kültürü tarafından modül için Yardım dosyalarını düzenleyin. Her güncelleştirilebilir Yardımı CAB dosyası, bir kullanıcı Arabirimi kültürünü bir modülde Yardım dosyaları içerir. CAB dosyaları modülü her biri için farklı bir kullanıcı Arabirimi kültürünü için birden çok Yardım teslim edebilirsiniz.

2. Doğrulama güncelleştirilebilir Yardımı için izin verilen dosya türleri yalnızca şunlardır ve bunları bir Yardım dosyası şemayla doğrulanamadı dosyaları yardımcı olur. Varsa `Update-Help` cmdlet'i geçersiz veya izin verilen bir tür değil bir dosyayı karşılaştığında, geçersiz dosya yüklemez ve CAB dosyaları yüklemeyi durdurur. İzin verilen dosya türlerinin bir listesi için bkz. [dosyası izin verilen güncelleştirilebilir Yardımı CAB dosyasındaki türleri](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Yardım dosyaları dijital olarak imzala. Dijital imzalar, gerekli değildir. ancak bunlar bir en iyi uygulamalardan biridir.

4. Tüm dosyaları kullanıcı arabiriminde bir modül için kültür, yalnızca yeni olan dosyaları veya değişmiş olan Yardım içerir. CAB dosyası eksik, kullanıcılar ilk kez Yardım dosyalarını yükleyin ya da her güncelleştirme indirme sahip olmaz tüm modül Yardım dosyaları.

5. MakeCab.exe gibi dolap dosyaları oluşturan bir yardımcı programını kullanın. Windows PowerShell, CAB dosyaları oluşturma cmdlet'leri içermez.

6. CAB dosyası adı. Daha fazla bilgi için [güncelleştirilebilir bir Yardım CAB dosyası adına nasıl](./how-to-name-an-updatable-help-cab-file.md).

7. Tarafından belirtilen konuma modülü için CAB dosyaları karşıya yükleme **HelpContentUri** modülü için HelpInfo XML dosyasında öğe. Ardından tarafından belirtilen konuma HelpInfo XML dosyasını karşıya **HelpInfoUri** modül bildirim anahtar. **HelpContentUri** ve **HelpInfoUri** aynı konuma işaret edebilir.

> [!CAUTION]
> Değerini **HelpInfoUri** anahtarı ve **HelpContentUri** öğesi "http" veya "https" ile başlamalıdır. Değer bir Internet konumu belirtmeniz gerekir ve bir dosya adı içermemelidir.