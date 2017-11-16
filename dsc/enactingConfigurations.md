---
ms.date: 2017-10-16
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yapılandırmaları ederek ilerlemesini kabul ederek"
ms.openlocfilehash: f9f8889439e43d540b50b68ef13e8e088b8cadd3
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2017
---
# <a name="enacting-configurations"></a>Yapılandırmaları ederek ilerlemesini kabul ederek

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell istenen durum yapılandırması (DSC) yapılandırmaları yürürlüğe iki yolu vardır: itme modu ve çekme modu.

## <a name="push-mode"></a>Anında iletme modu

![Anında iletme modu](images/pushModel.png "nasıl modu works bildirme")

Anında iletme modu başvuruyor etkin olarak çağırarak bir yapılandırma için bir hedef düğüm uygulama bir kullanıcıya [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i.

Oluşturma ve yapılandırma derleme sonra onu zorlama modunda çağırarak yürürlüğe [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, ayarı cmdlet'inin MOF yapılandırma bulunduğu yolu Path parametresi.
Örneğin, yapılandırma MOF adresindedir ise `C:\DSC\Configurations\localhost.mof`, aşağıdaki komut ile yerel makineye uygulanacak:`Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Not__: varsayılan olarak, DSC yapılandırma bir arka plan işi olarak çalıştırır. Yapılandırma etkileşimli olarak çalıştırmak için arama [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) ile __-bekleyin__ parametresi.

## <a name="pull-mode"></a>Çekme modu

![Çekme modu](images/pullModel.png "nasıl modu works isteme")

Çekme modunda, bir uzak çekme hizmetinden istenen durumu yapılandırmalarını almak için çekme istemcileri yapılandırılır.
Benzer şekilde, çekme hizmeti konak DSC hizmeti için ayarlanmış ve yapılandırmaları ve çekme istemciler tarafından gerekli kaynaklarla sağlanmış.
Her çekme istemcilerin düğümün yapılandırması üzerinde düzenli uyumluluk denetimi gerçekleştirir zamanlanmış bir olay vardır.
İlk kez olay tetiklendiğinde çekme istemci üzerindeki yerel Configuration Manager (LCM'yi) LCM'yi belirtilen yapılandırmasını almak için çekme hizmetine istekte bulunur.
Bu yapılandırma çekme hizmette varsa ve ilk doğrulama denetimlerini geçirir, yapılandırma, ardından tarafından LCM'yi yürütüldüğü çekme istemciye indirilir.

İstemci Yapılandırması tarafından belirtilen düzenli aralıklarla uyumlu olduğunu LCM'yi denetler **ConfigurationModeFrequencyMins** LCM'yi özelliği.
Tarafından belirtilen düzenli aralıklarla çekme hizmetinde güncelleştirilmiş yapılandırmaları için LCM'yi denetler **RefreshModeFrequency** LCM'yi özelliği.
LCM'yi yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](metaConfig.md).

Bir çekme hizmetini barındırmak için önerilen çözümdür DSC bulut hizmeti [Azure Otomasyonu](https://azure.microsoft.com/en-us/services/automation/).
Bu barındırılan grafik yönetim, raporlama ve merkezi yönetim çözümü sağlar.

Bir çekme hizmeti Windows Server'da ayarlama hakkında daha fazla bilgi için bkz: [DSC web çekme sunucusu kurma](pullServer.md).
Ancak, bu uygulama kısıtlı özelliklere sahiptir ve bazı "bunu kendiniz" tümleştirme gerektiriyor mu anlayın.

Aşağıdaki konularda, çekme hizmet ve istemcileri açıklanır:

- [Azure Otomasyonu DSC genel bakış](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Bir SMB çekme sunucusu kurma](pullServerSMB.md)
- [Bir çekme istemci yapılandırma](pullClientConfigID.md)
