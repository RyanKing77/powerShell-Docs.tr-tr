---
title: HelpInfo XML dosyasının nasıl oluşturulacağı | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844901"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>HelpInfo XML Dosyası Oluşturma

Bu bölümdeki konular, oluşturma ve bir "HelpInfo XML dosyası olarak" Windows PowerShell güncelleştirilebilir Yardımı özelliği için yaygın olarak bilinen bir Yardım bilgileri dosyası doldurmak açıklanmaktadır.

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML dosyasını genel bakış

Modül için güncelleştirilebilir Yardımı hakkında bilgi birincil kaynağı HelpInfo XML dosyasıdır. Bu modüller, desteklenen UI kültürü ve kullanıcının en yeni Yardım dosyaları olup olmadığını belirlemek için güncelleştirilebilir Yardımı'nı kullanan sürüm numaraları için Yardım dosyalarının konumunu içerir.

Birden çok UI kültürü için birden çok Yardım dosyası modül içerse bile her modülü yalnızca bir HelpInfo XML dosyası vardır. Modül yazarı HelpInfo XML dosyası oluşturur ve tarafından belirtilen Internet konumda yerleştirir **HelpInfoUri** modül bildirimindeki anahtar. Modül Yardım dosyaları güncelleştirilmiş ve karşıya yüklenen modül yazarı HelpInfo XML dosyasını güncelleştirir ve orijinal HelpInfo XML dosyasını yeni sürüm ile değiştirir.

HelpInfo XML dosyasını dikkatli bir şekilde korunur önemlidir. Güncelleştirilebilir Yardımı yeni dosyaları karşıya yükleme, ancak sürüm numaralarının artırılıp unutursanız, yeni dosyalar kullanıcıların bilgisayarlarına yüklemez. Güncelleştirilebilir Yardımı için yeni bir kullanıcı Arabirimi kültürünü Yardım dosyalarını eklemek ancak HelpInfo XML dosyasını güncelleştirin veya yoksa onu doğru konuma yerleştirmek, yeni dosyalar yüklemez.

## <a name="in-this-section"></a>Bu bölümde

Bu bölüm aşağıdaki konuları içerir.

- [HelpInfo XML Şeması](./helpinfo-xml-schema.md)

- [HelpInfo XML örnek dosya](./helpinfo-xml-sample-file.md)

- [Nasıl HelpInfo XML dosya adı](./how-to-name-a-helpinfo-xml-file.md)

- [HelpInfo XML sürüm numaraları ayarlama](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Ayrıca bkz:

[Güncelleştirilebilir Yardımı destekleme](./supporting-updatable-help.md)