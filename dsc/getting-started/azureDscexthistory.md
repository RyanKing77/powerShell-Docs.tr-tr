---
description: Azure Desired State Configuration ' nı (DSC) uzantısı sürüm geçmişi hakkında bilgi edinin.
ms.date: 06/21/2018
keywords: DSC, powershell, azure, uzantısı
title: Azure DSC uzantısı sürüm geçmişi
ms.openlocfilehash: 2c076e3beccc15e99af2327820916d7a4d28da68
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405865"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Azure Desired State Configuration uzantısı sürüm geçmişi

Azure Desired State Configuration (DSC) VM uzantısı, gerektiğinde geliştirmeleri ve Azure, Windows Server ve Windows PowerShell içeren Windows Management Framework (WMF) tarafından sunulan yeni özellikler destekleyecek şekilde güncelleştirilir.

Bu makalede destekler, açıklamalar ve yenilikleri veya değişiklikleri açıklamalar hangi ortamlarda DSC VM uzantısını Azure'nün her sürümü hakkında bilgi sağlar.

## <a name="latest-version"></a>En son sürümü

### <a name="version-276"></a>Sürüm 2.76

- **Yayın Tarihi:**
  - 9 Mayıs 2018 (Azure) | Haziran 21 2018'e (Azure Çin'de, Azure kamu)
- **İşletim sistemi desteği:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows istemci 7/8.1/10
  - Nano Sunucu
- **WMF desteği:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 güncelleştirme
  - WMF 4.0
- **Ortam:**
  - Azure
  - Azure Çin
  - Azure kamu
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - Uzantı meta verileri substatus ve diğer küçük hata düzeltmeleri için geliştirme.

## <a name="supported-versions"></a>Desteklenen sürümler

> [!WARNING]
> WMF 5.0 ortak imzalama sertifikalarını, Ağustos 2016'da süresi dolmuş Önizleme sürümleri 2.4 2.13 aracılığıyla kullanın.  Bu sorun hakkında daha fazla bilgi için bkz. [blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Sürüm 2,75

- **Yayın Tarihi:** 5 Mart 2018
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 8.1/7/10, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - TLS 1.2 son taşıma GitHub'ın sonra bir Azure Otomasyonu DSC Azure Marketi'nde kullanılabilir kendin YAP Resource Manager şablonlarını kullanarak VM eklenemiyor veya DSC uzantı Github'da barındırılan herhangi bir yapılandırma almak için kullanın. Uzantı dağıtma sırasında aşağıdakine benzer bir hata görürsünüz:

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - Yeni Uzantı sürümü, TLS 1.2 artık uygulanmaz. Uzantı için 2,75 autoupgraded olacağı uzantı AutoUpgradeMinorVersion zaten varsa dağıtımı sırasında Resource Manager şablonunda = true. El ile güncelleştirmeleri için belirtme `TypeHandlerVersion = 2.75` Resource Manager şablonunuzda.

### <a name="version-270---272"></a>Sürüm 2.70 2.72

- **Yayın Tarihi:** 13 Kasım 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 8.1/7/10, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - Düzeltmeleri ve portal kullanıcı Arabirimi aracılığıyla Azure Automation DSC, hem de Resource Manager şablonu kullanarak basitleştirir geliştirmeleri hata.  Daha fazla bilgi için [varsayılan yapılandırma betiğini](/azure/virtual-machines/extensions/dsc-overview) DSC uzantı belgelerinde.

### <a name="version-226"></a>Sürüm 2.26

- **Yayın Tarihi:** 9 Haziran 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 8.1/7/10, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - Telemetri geliştirmeleri.

### <a name="version-225"></a>Sürüm 2,25

- **Yayın Tarihi:** 2 Haziran 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 8.1/7/10, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - Çeşitli hata düzeltmeleri ve başka küçük geliştirmeler eklenmiştir.

### <a name="version-224"></a>Sürüm 2,24

- **Yayın Tarihi:** 13 Nisan 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - VM UUID & DSC aracı kimliği uzantı meta verileri kullanıma sunar. Başka küçük geliştirmeler eklenmiştir.

### <a name="version-223"></a>Sürüm 2.23

- **Yayın Tarihi:** 15 Mart 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - Çok sayıda hata düzeltmeleri ve diğer geliştirmesi eklendi.

### <a name="version-222"></a>Sürüm 2.22

- **Yayın Tarihi:** 8 Şubat 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano sunucu
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - DSC uzantısı WMF 5.1 desteği sunuyor.
  - Küçük iyileştirmeler eklenmiştir.

### <a name="version-221"></a>Sürüm 2.21

- **Yayın Tarihi:** 2 aralık 2016
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano sunucu
- **WMF desteği:** WMF 5.1 önizleme, WMF 5.0 RTM, WMF 4.0 güncelleştirme WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme). Nano sunucu için VM üzerinde DSC rolü yüklenir.
- **Yeni özellikler:**
  - DSC uzantısı şimdi Nano Sunucu'da kullanılabilir. Bu sürümü, öncelikli olarak uzantısı Nano Sunucu'da çalıştırmak için kod değişiklikleri içerir.
  - Küçük iyileştirmeler eklenmiştir.

### <a name="version-220"></a>Sürüm 2.20

- **Yayın Tarihi:** 2 Ağustos 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.1 önizleme, WMF 5.0 RTM, WMF 4.0 güncelleştirme WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - İçin WMF 5.1 önizleme destekler. İlk kez yayımlandığında, bu sürümü isteğe bağlı bir yükseltme oldu ve Wmfversion belirtmek zorunda = ' 5.1PP' Resource Manager şablonlarındaki WMF 5.1 Preview sürümünü yükleyin. Wmfversion = 'latest' hala yükler [WMF 5.0 RTM'ye](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). WMF 5.1 önizleme hakkında daha fazla bilgi için bkz. [bu blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - İkincil diğer düzeltmeleri ve geliştirmeleri eklenmiştir.

### <a name="version--219"></a>Sürüm 2.19

- **Yayın Tarihi:** 3 Haziran 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme WMF 4.0
- **Ortam:** Azure, Azure Çin Azure kamu
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - DSC uzantısı Center'a Azure Çin'de sunulmuştur. Bu sürümü, öncelikli olarak uzantısını Azure Çin üzerinde çalıştırmak için düzeltmeler içerir.

### <a name="version-218"></a>Sürüm 2.18

- **Yayın Tarihi:** 3 Haziran 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Telemetri telemetri düzeltme indirme dosyasına (bilinen Azure DNS sorun) veya yükleme sırasında bir hata meydana geldiğinde engelleyici olmayan olun.
  - Burada uzantı yapılandırma işlenirken bir yeniden başlatma işleminden sonra durdurur aralıklı olarak ortaya çıkan sorunu düzeltin. Bu DSC uzantı 'durumuna geçiş aşamasında' kalmasına neden olmaktadır.
  - İkincil diğer düzeltmeleri ve geliştirmeleri eklenmiştir.

### <a name="version-217"></a>Sürüm 2.17

- **Yayın Tarihi:** 26 Nisan 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - İçin WMF 4.0 güncelleştirme destekler. WMF 4.0 güncelleştirme hakkında daha fazla bilgi için bkz. [bu blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - DSC uzantı yükleme sırasında oluşur ya da bir DSC Yapılandırması uygulanırken uzantısı sonrası hataları yeniden deneme mantığına yükleyin. Bu değişikliğin bir parçası olarak uzantı önceki bir yükleme başarısız olursa, yükleme işlemini yeniden deneyin veya daha önce için en fazla üç kez tamamlanma durumu (başarı/hata) ulaşana kadar veya yeni bir istek geliyorsa, başarısız olan bir DSC yapılandırması yeniden kabul edin. Uzantı geçersiz kullanıcı ayarları/kullanıcı girişi nedeniyle başarısız olursa, yeniden denemez. Bu durumda, uzantı ile yeni bir isteği yeniden çağrılmasını ve kullanıcı ayarları düzeltmek gerekir. Not: DSC uzantısı yeniden deneme işlemleri için Azure VM Aracısı bağlıdır. Azure VM Aracısı, başarı veya hata durumu ulaşana kadar son başarısız istek uzantısıyla çağırır.

### <a name="version-216"></a>Sürüm 2.16

- **Yayın Tarihi:** 21 Nisan 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Hata işleme ve diğer küçük hata düzeltmeleri geliştirme.
  - DSC uzantı ayarları yeni özelliği. AdvancedOptions ' ForcePullAndApply' eklenen DSC uzantısını etkinleştirmek için yenileme modunu (varsayılan anında iletme modu aksine) çekme olduğunda DSC yapılandırmaları kabul edin. Daha fazla bilgi için bkz [bu blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) DSC uzantı ayarları hakkında daha fazla bilgi edinmek için.

### <a name="version-215"></a>Sürüm 2.15

- **Yayın Tarihi:** 14 Mart 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Uzantı sürümü 2.14, WMF RTM'yi yüklemeden değişiklik dahil. Uzantısı için 2.13.2.0 2.14.0.0 sürümünden yükseltirken, fark edebilirsiniz DSC bazı cmdlet'lerin başarısız veya yapılandırmanızın bir hata ile başarısız oluyor: 'No örneği ile özellik değerlerini bulundu'. Daha fazla bilgi için [DSC sürüm notları](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). Bu sorunlara yönelik geçici çözümler 2,15 sürümünde eklenmiştir.
  - Ne yazık ki, sürüm 2.14 zaten yüklü ve yukarıdaki iki sorun biri ile çalışan, bu adımları el ile gerçekleştirmeniz gerekir.  Yükseltilmiş bir PowerShell oturumunda:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Sürüm 2.14

- **Yayın Tarihi:** 25 Şubat 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Notlar:** Bu sürüm, Windows Server 2016 Technical Preview'da dahil olarak DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - WMF RTM kullanır.
  - DSC uzantısı kalitesini iyileştirmek için veri koleksiyonunu etkinleştirir. Daha fazla bilgi için [blog](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Resource Manager şablonu uzantı için güncelleştirilmiş ayarları biçim sağlar. Daha fazla bilgi için [blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Hata düzeltmeleri ve diğer geliştirmeler.

## <a name="next-steps"></a>Sonraki adımlar

- PowerShell DSC hakkında daha fazla bilgi için Git [PowerShell Belge Merkezi](../overview/overview.md).
- İnceleme [DSC uzantısı için Resource Manager şablonu](/azure/virtual-machines/extensions/dsc-template).
- PowerShell DSC kullanarak yönetebilirsiniz. daha fazla işlevsellik ve daha fazla DSC kaynakları için Gözat [PowerShell Galerisi](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Yapılandırmalarına önemli parametreleri geçirme hakkında daha fazla ayrıntı için bkz [yönetin, DSC uzantısı işleyicisine ile güvenli kimlik bilgileri](/azure/virtual-machines/extensions/dsc-credentials).