---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Nesne ardışık düzen"
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a>Nesne ardışık düzen
Ardışık Düzen kanal bağlı kesimleri bir dizi gibi davranır. Ardışık Düzen taşıma öğeleri her segment geçirin. Windows PowerShell'de bir ardışık düzen oluşturmak için dikey çizgi işleci birlikte komutları Bağlan "|". Her komutun çıktısı, sonraki komut için giriş olarak kullanılır.

Ardışık Düzen tartışmaya açık bir şekilde komut satırı arabirimlerinden kullanılan en değerli kavramıdır. Düzgün bir şekilde kullanılan, ardışık düzen yalnızca karmaşık komutları girerek çabaları azaltmak, ancak komutlarda iş akışını görmeyi kolaylaştırır. Bir ilgili yararlı ardışık düzen her bir öğede ayrı olarak çalıştırmak için bunları sıfır, bir ya da çok sayıda öğe ardışık düzeninde olmasına göre değiştirmek sahip olmadığını özelliğidir. Ayrıca, her (bir ardışık düzen öğesi olarak adlandırılır) bir ardışık düzende komutu genellikle çıktısını ardışık düzen tarafından-öğe sonraki komuta geçirir. Bu genellikle karmaşık komutların kaynak talebi azaltır ve çıktı hemen alma başlamanızı sağlar.

Bu bölümde, biz nasıl en popüler Kabukları ardışık düzen Windows PowerShell komut zinciri farklı açıklar ve sonra Denetim ardışık düzeni çıkış yardımcı olmak ve ardışık düzen nasıl çalıştığını görmek için kullanabileceğiniz bazı temel Araçlar gösterin.

