---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 60abe525ca1bdcebca570f2ef3656f32dca3747f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="mof-documents-are-encrypted-by-default"></a>Varsayılan olarak şifrelenmiş MOF belgeleri

Yapılandırma belgeler hassas bilgiler içerir. DSC önceki sürümlerinde dağıtmak ve bir yapılandırma içinde kimlik bilgilerini güvenli hale getirmek için sertifikaları yönetmek için gerekli olmuştur. Çoğu için önemli yönetim yükü, bu ve bunu hala değildi ve güvenli, bazı yapılandırma bilgilerini bırakıldı yapmak için bile tüm iş ile sürdü. 

Artık söz konusu değildir çünkü **tüm yapılandırma MOF dosyalarından varsayılan olarak güvenlidir**. Hiçbir sertifika veya meta yapılandırma ayarları gereklidir. MOF kaydedildiğinde bir yapılandırma kurduğunda tarafından yerel Configuration Manager (LCM'yi) bir hedef düğümdeki diske şifrelenir. MOF dosyalarından kullanılarak şifrelenmiş [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Not:** yapılandırma komut dosyası tarafından oluşturulan MOF dosyalarından şifrelenmez.

**Örnek:** zorlama modunda şifrelemesi ![MOF şifreleme](../images/MOF_Encryption.jpg)

Parolaları şifrelemek için sertifika yöntemi zaten kullanıyorsanız, veya ek güvenlik için parolaları, gerekirse [sertifika tabanlı şifreleme varolan yöntemi](https://msdn.microsoft.com/powershell/dsc/securemof) çalışmaya devam eder. Sonuç tam olarak DPAPIs kullanılarak şifrelenmiş bir MOF belgenin ve ayrıca parolalara sahip içinde şifrelenmiş.

Bu şifreleme yalnızca yapılandırma MOF belgeleri (pending.mof, current.mof, previous.mof ve kısmi MOF dosyalarından) için geçerlidir. Büyük olasılıkla daha az gizli içerdikleri beri Meta yapılandırma MOF dosyalarından hala düz metin olarak kaydedilir.

