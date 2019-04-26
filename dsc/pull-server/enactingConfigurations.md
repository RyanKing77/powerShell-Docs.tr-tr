---
ms.date: 10/16/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmaları Kabul Etme
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079957"
---
# <a name="enacting-configurations"></a>Yapılandırmaları Kabul Etme

>Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell Desired State Configuration (DSC) yapılandırmaları uygulamak için iki yolu vardır: anında iletme modu ve çekme modu.

## <a name="push-mode"></a>Anında iletme modu

![Anında iletme modu](../images/pushModel.png "modu works nasıl anında iletme")

Anında iletme modu başvuran bir yapılandırma çağırarak hedef düğüme etkin bir şekilde uygulama bir kullanıcıya [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'i.

Oluşturma ve yapılandırma derleme sonra bunu gönderim modunda çağırarak geçireceğini [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet'ini ayarlama - Path parametresini cmdlet yapılandırma MOF bulunduğu yolu.
Örneğin, ' % s'yapılandırması MOF adresindedir ise `C:\DSC\Configurations\localhost.mof`, aşağıdaki komutla yerel makineye uygulanacak: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Not__: Varsayılan olarak, DSC yapılandırma bir arka plan işi olarak çalıştırır. Yapılandırma etkileşimli olarak çalıştırmak için çağrı [Başlat-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) ile __-bekleyin__ parametresi.

## <a name="pull-mode"></a>Çekme modu

![Çekme modu](../images/pullModel.png "nasıl modu works çekme")

Çekme modu, uzak çekme hizmetinden istenen durum yapılandırmaları almak için çekme istemcileri yapılandırılır.
Benzer şekilde, çekme hizmetini DSC konak Hizmeti'ne ayarlanmış ve çekme istemciler tarafından gerekli kaynakları ve yapılandırmaları ile sağlandı.
Her bir tanıtım istemcisinde bir düğüm yapılandırmasını düzenli uyumluluk denetimi yapar zamanlanmış bir olayı vardır.
İlk kez olayı tetiklendiğinde, tanıtım istemcisinde yerel Configuration Manager (LCM) LCM içinde belirtilen yapılandırmasını almak için çekme hizmetine bir istek gönderir.
Bu yapılandırma çekme hizmetini üzerinde var olduğundan ve ilk doğrulama denetimlerini geçirir, yapılandırmanın ardından LCM göre yürütüldüğü çekme istemcisi yüklenir.

İstemci Yapılandırması tarafından belirtilen düzenli aralıklarla uyumlu olduğunu LCM denetler **ConfigurationModeFrequencyMins** LCM özelliğidir.
LCM denetler çekme hizmetini güncelleştirilmiş yapılandırmalar tarafından belirtilen düzenli aralıklarla **RefreshModeFrequency** LCM özelliğidir.
LCM yapılandırma hakkında daha fazla bilgi için bkz: [yerel Configuration Manager Yapılandırma](../managing-nodes/metaConfig.md).

Bir çekme hizmetini barındıran için önerilen çözümdür DSC bulut hizmeti [Azure Otomasyonu](https://azure.microsoft.com/services/automation/).
Bu barındırılan grafik yönetimi, raporlama ve merkezi yönetim çözümü sağlar.

Windows Server'da bir çekme hizmetini ayarlama hakkında daha fazla bilgi için bkz. [bir DSC web çekme sunucusu ayarlama](pullServer.md).
Ancak, bu uygulamayla sınırlı özelliklere ve bazı "bunu kendiniz" tümleştirme gerektiriyor mu anlayın.

Aşağıdaki konularda, çekme hizmetini ve istemcilerin açıklanır:

- [Azure Automation DSC genel bakış](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Bir SMB çekme sunucusu ayarlama](pullServerSMB.md)
- [Çekme istemcisi yapılandırma](pullClientConfigID.md)
