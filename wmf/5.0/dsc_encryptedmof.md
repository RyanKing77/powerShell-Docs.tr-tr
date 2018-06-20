---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4c2a3fb15b108f1a8e9fd271a620bcb1cb8c77ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222345"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Varsayılan olarak şifrelenmiş MOF belgeleri

Yapılandırma belgeler hassas bilgiler içerir. DSC önceki sürümlerinde dağıtmak ve bir yapılandırma içinde kimlik bilgilerini güvenli hale getirmek için sertifikaları yönetmek için gerekli olmuştur. Çoğu için önemli yönetim yükü, bu ve bunu hala değildi ve güvenli, bazı yapılandırma bilgilerini bırakıldı yapmak için bile tüm iş ile sürdü.

Artık söz konusu değildir çünkü **tüm yapılandırma MOF dosyalarından varsayılan olarak güvenlidir**. Hiçbir sertifika veya meta yapılandırma ayarları gereklidir. MOF kaydedildiğinde bir yapılandırma kurduğunda tarafından yerel Configuration Manager (LCM'yi) bir hedef düğümdeki diske şifrelenir. MOF dosyalarından kullanılarak şifrelenmiş [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Not:** yapılandırma komut dosyası tarafından oluşturulan MOF dosyalarından şifrelenmez.

**Örnek:** zorlama modunda şifrelemesi ![MOF şifreleme](../images/MOF_Encryption.jpg)

Parolaları şifrelemek için sertifika yöntemi zaten kullanıyorsanız, veya ek güvenlik için parolaları, gerekirse [sertifika tabanlı şifreleme varolan yöntemi](https://msdn.microsoft.com/powershell/dsc/securemof) çalışmaya devam eder. Sonuç tam olarak DPAPIs kullanılarak şifrelenmiş bir MOF belgenin ve ayrıca parolalara sahip içinde şifrelenmiş.

Bu şifreleme yalnızca yapılandırma MOF belgeleri (pending.mof, current.mof, previous.mof ve kısmi MOF dosyalarından) için geçerlidir. Büyük olasılıkla daha az gizli içerdikleri beri Meta yapılandırma MOF dosyalarından hala düz metin olarak kaydedilir.
