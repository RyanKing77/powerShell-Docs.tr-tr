---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Yönetim için Windows PowerShell’i Kullanma
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954339"
---
# <a name="using-windows-powershell-for-administration"></a>Yönetim için Windows PowerShell’i Kullanma
Windows PowerShell temel amacı daha iyi ve daha kolay yönetim sistemleri denetime etkileşimli olarak veya komut dosyasından sağlamaktadır. Bu bölüm, Windows sistemleri Windows PowerShell ile yönetme birçok belirli sorunları için aracılığıyla çözümlerini anlatılmaktadır. Biz komut dosyaları veya Windows PowerShell Kullanıcı Kılavuzu'nda hakkında açıklandı değildir ancak çözümler komut dosyaları veya işlev olarak daha sonra kullanılabilir. İşlevler sorunları çözmek için çözümün bir parçası olarak dahil örnekler göstereceğiz.

Çözüm açıklamaları belirli cmdlet'leri, genel Get-WmiObject cmdlet'i ve Windows ve .NET Framework altyapılar parçası olan bile dış araçları kullanarak çözümleri bir karışımını görürsünüz. Dış araçlar kullanımını uzun vadeli tasarım hedefi, Windows PowerShell'in bir parçasıdır. Sistem büyüdükçe bile kullanıcılar sürekli içinde kullanılabilir toolsets bunlar gereken her şeyi gerektirmeyen durumlarda karşılaşır. Tümleştirme çözümlerden her türlü olası alternatif senaryoyu desteklemek Windows PowerShell cmdlet uygulamaları başına foster bağımlılığını yerine çalışır.