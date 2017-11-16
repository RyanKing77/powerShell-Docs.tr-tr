---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Yönetim için Windows PowerShell'i kullanma"
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a>Yönetim için Windows PowerShell'i kullanma
Windows PowerShell temel amacı daha iyi ve daha kolay yönetim sistemleri denetime etkileşimli olarak veya komut dosyasından sağlamaktadır. Bu bölüm, Windows sistemleri Windows PowerShell ile yönetme birçok belirli sorunları için aracılığıyla çözümlerini anlatılmaktadır. Biz komut dosyaları veya Windows PowerShell Kullanıcı Kılavuzu'nda hakkında açıklandı değildir ancak çözümler komut dosyaları veya işlev olarak daha sonra kullanılabilir. İşlevler sorunları çözmek için çözümün bir parçası olarak dahil örnekler göstereceğiz.

Çözüm açıklamaları belirli cmdlet'leri, genel Get-WmiObject cmdlet'i ve Windows ve .NET Framework altyapılar parçası olan bile dış araçları kullanarak çözümleri bir karışımını görürsünüz. Dış araçlar kullanımını uzun vadeli tasarım hedefi, Windows PowerShell'in bir parçasıdır. Sistem büyüdükçe bile kullanıcılar sürekli içinde kullanılabilir toolsets bunlar gereken her şeyi gerektirmeyen durumlarda karşılaşır. Tümleştirme çözümlerden her türlü olası alternatif senaryoyu desteklemek Windows PowerShell cmdlet uygulamaları başına foster bağımlılığını yerine çalışır.

