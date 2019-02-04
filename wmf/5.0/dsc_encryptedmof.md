---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688437"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Varsayılan olarak MOF belgeler şifrelenir

Yapılandırma belgelerini, hassas bilgiler içerir. DSC önceki sürümlerinde dağıtmak ve yapılandırması içindeki kimlik bilgilerini güvenli hale getirmek için sertifikaları yönetmek için gerekli olmuştur. Çoğu için bile tüm işleri ile değildi ve güvenli, bazı yapılandırma bilgilerini kalan dosyalar hala bunu sürdü ve bu önemli yönetim yüklerini şeklindeydi.

Artık durumu değildir çünkü **tüm yapılandırma MOF'lar varsayılan olarak güvenlidir**. Hiçbir sertifika veya meta-yapılandırma ayarları gereklidir. MOF kaydedildiğinde bir yapılandırma için istediğiniz zaman tarafından yerel Configuration Manager (LCM) hedef düğümde diske şifrelenir. Kullanarak şifreli MOF'lar [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Not:** Bir yapılandırma betiği tarafından oluşturulan MOF'lar şifrelenmez.

**Örnek:** Şifreleme gönderme modunda ![MOF şifreleme](../images/MOF_Encryption.jpg)

Parolaları şifrelemek için sertifika yöntemi zaten kullanıyorsanız, veya ek güvenlik için parolaları, gerekiyorsa [sertifika tabanlı şifreleme varolan bir yöntem](https://msdn.microsoft.com/powershell/dsc/securemof) çalışmaya devam eder. Sonuç DPAPIs kullanarak tam olarak şifrelendiğinden bir MOF belgesi olabilir ve ayrıca parola mı içinde şifreli.

Bu şifreleme, yalnızca (pending.mof, current.mof, previous.mof ve kısmi MOF'lar) yapılandırma MOF belgeler için de geçerlidir. Daha büyük bir olasılıkla gizli dizileri içerdikleri beri Meta-yapılandırma MOF'lar hala düz metin olarak kaydedilir.
