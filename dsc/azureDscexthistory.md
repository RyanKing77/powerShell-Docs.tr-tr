---
description: İstenen durum Yapılandırması'nı (DSC) uzantısı'nda Azure sürüm geçmişi hakkında bilgi edinin.
ms.date: 03/14/2018
ms.topic: conceptual
keywords: DSC, powershell, azure, uzantısı
title: Azure DSC uzantısı sürüm geçmişi
author: DCtheGeek
ms.author: dacoulte
ms.openlocfilehash: a183137dde302811874bd5466c35bccebca5d128
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Azure istenen durum yapılandırması uzantısı sürüm geçmişi

Azure istenen durum yapılandırması (DSC) VM uzantısı gerektiği geliştirmeleri ve Azure, Windows Server ve Windows PowerShell içeren Windows Management Framework (WMF) tarafından sunulan yeni özellikler desteklemek üzere güncelleştirilmiştir.

Bu makalede destekler, açıklamalar ve yeni özellikleri ve değişiklikleri açıklamalar için hangi ortamları Azure DSC VM uzantısı, her sürümü hakkında bilgi sağlar.

## <a name="latest-versions"></a>En son sürümleri

### <a name="version-275"></a>Sürüm 2,75

- **Yayın Tarihi:**
  - 5 Mart 2018
- **İşletim sistemi desteği:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Windows İstemcisi 8.1/7/10
  - Nano Sunucu
- **WMF desteği:**
  - WMF 5.1
  - WMF 5.0 RTM
  - WMF 4.0 güncelleştirme
  - WMF 4.0
- **Ortamı:**
  - Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - TLS 1.2 için GitHub'ın en son taşıma sonra yerleşik bir VM üzerinde Azure Marketi kullanılabilir Dıy Resource Manager şablonları kullanarak Azure Otomasyonu DSC olamaz veya DSC uzantısı GitHub üzerinde barındırılan config almak için kullanın. Uzantı dağıtma sırasında aşağıdakine benzer bir hata görürsünüz:

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

  - Yeni Uzantı sürümde TLS 1.2 şimdi zorlanır. Uzantı 2,75 autoupgraded alırsınız AutoUpgradeMinorVersion zaten sahipse, uzantı dağıtırken Resource Manager şablonunda = true. El ile güncelleştirmeleri için belirtme `TypeHandlerVersion = 2.75` için Resource Manager şablonunda.

### <a name="version-219"></a>Sürüm 2.19

- **Yayın Tarihi:**
  - 3 Haziran 2016
- **İşletim sistemi desteği:**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
- **WMF desteği:**
  - WMF 5.0 RTM
  - WMF 4.0 güncelleştirme
  - WMF 4.0
- **Ortamı:**
  - Azure
  - Azure Çin
  - Azure kamu
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - DSC uzantı şimdi üzerinde Azure Çin'e dahil edilmiş. Bu sürüm öncelikle uzantısı Azure Çin üzerinde çalıştırmak için düzeltmeler içerir.

## <a name="supported-versions"></a>Desteklenen sürümleri

> [!WARNING]
> WMF 5.0 Genel Ağustos 2016'da, imzalama sertifikası süresi Önizleme sürümleri 2.13 aracılığıyla 2.4 kullanın.  Bu sorun hakkında daha fazla bilgi için bkz: [blog gönderisi](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-270---272"></a>Sürüm 2.70 2.72

- **Yayın Tarihi:** 13 Kasım 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 7/8.1/10, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - Düzeltmeleri & UI Portalı aracılığıyla Azure Otomasyonu DSC, hem de Resource Manager şablonu kullanarak basitleştirir geliştirmeleri hata.  Daha fazla bilgi için bkz: [varsayılan yapılandırma komut dosyası](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script) DSC uzantısı belgelerinde.

### <a name="version-226"></a>Sürüm 2.26

- **Yayın Tarihi:** 9 Haziran 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 7/8.1/10, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - Telemetri geliştirmeler.

### <a name="version-225"></a>Sürüm 2,25

- **Yayın Tarihi:** 2 Haziran 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows istemci 7/8.1/10, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - Çeşitli hata düzeltmeleri ve diğer ikincil geliştirmeler eklendi.

### <a name="version-224"></a>Sürüm 2,24

- **Yayın Tarihi:** 13 Nisan 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - VM UUID & DSC Aracısı kimliği uzantısı meta veri kullanıma sunar. İkincil diğer geliştirmeler eklendi.

### <a name="version-223"></a>Sürüm 2.23

- **Yayın Tarihi:** 15 Mart 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - Çok sayıda hata düzeltmeleri ve diğer geliştirmeler eklendi.

### <a name="version-222"></a>Sürüm 2.22

- **Yayın Tarihi:** 8 Şubat 2017
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF desteği:** WMF 5.1, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - DSC uzantı WMF 5.1 desteği artık sahiptir.
  - İkincil diğer geliştirmeler eklendi.

### <a name="version-221"></a>Sürüm 2.21

- **Yayın Tarihi:** 2 aralık 2016
- **İşletim sistemi desteği:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **WMF desteği:** WMF 5.1 önizleme, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016'da yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme). Nano Server için VM DSC rolü yüklenir.
- **Yeni özellikler:**
  - DSC uzantısı artık Nano Server üzerinde kullanılabilir. Bu sürüm, öncelikle uzantısı Nano sunucuda çalıştırmak için kod değişiklikleri içerir.
  - İkincil diğer geliştirmeler eklendi.

### <a name="version-220"></a>Sürüm 2.20

- **Yayın Tarihi:** 2 Ağustos 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.1 önizleme, WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - WMF için 5.1 önizleme destekler. İlk kez yayımlandığında, bu sürüm isteğe bağlı yükseltme oldu ve Wmfversion belirtmek zorunda kalındı = ' 5.1PP' Resource Manager şablonlarındaki WMF 5.1 Preview sürümünü yükleyin. Wmfversion 'Son' hala yükler = [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). WMF 5.1 önizleme hakkında daha fazla bilgi için bkz: [bu blog]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Diğer düzeltmeleri ikincil ve geliştirmeleri eklenmiştir.

### <a name="version--219"></a>Sürüm 2.19

- **Yayın Tarihi:** 3 Haziran 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure, Azure Çin'de Azure kamu
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - DSC uzantı edildi Azure Çin için sunulmuştur. Bu sürüm öncelikle uzantısı Azure Çin üzerinde çalıştırmak için düzeltmeler içerir.

### <a name="version-218"></a>Sürüm 2.18

- **Yayın Tarihi:** 3 Haziran 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Telemetri telemetri düzeltme indirme (bilinen Azure DNS sorun) veya yükleme sırasında bir hata oluştuğunda engellemeyen olun.
  - Burada uzantı bir yeniden başlatma işleminden sonra yapılandırma işlenirken durdurur için aralıklı sorunu düzeltin. Bu DSC uzantısı 'durumuna geçiş içinde' kalmasına neden olmaktadır.
  - Diğer düzeltmeleri ikincil ve geliştirmeleri eklenmiştir.

### <a name="version-217"></a>Sürüm 2.17

- **Yayın Tarihi:** 26 Nisan 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0 güncelleştirme, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - İçin WMF 4.0 güncelleştirme destekler. WMF 4.0 güncelleştirme hakkında daha fazla bilgi için bkz: [bu blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - DSC uzantı yükleme sırasında ortaya veya DSC Yapılandırması uygulanırken uzantısı post hataları yeniden deneme mantığına yükleyin. Bu değişikliğin bir parçası olarak uzantısı önceki bir yükleme başarısız olursa yüklemeyi yeniden deneyin veya daha önce için en fazla üç kez tamamlanma durumu (başarı/hata) ulaşana kadar veya yeni bir istek geliyorsa başarısız oldu bir DSC yapılandırma yeniden yürürlüğe. Uzantı geçersiz kullanıcı ayarları/kullanıcı girişi nedeniyle başarısız olursa, onu yeniden denemez. Bu durumda, yeni bir istekle yeniden çağrılan ve kullanıcı ayarlarını düzeltmek uzantı gerekir. Not: DSC uzantısı yeniden deneme işlemleri için Azure VM Aracısı bağımlıdır. Başarı veya hata durumu ulaşana kadar azure VM Aracısı son başarısız istek uzantısıyla çağırır.

### <a name="version-216"></a>Sürüm 2.16

- **Yayın Tarihi:** 21 Nisan 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Geliştirme hata işleme ve küçük diğer hata düzeltmeleri.
  - DSC uzantı ayarları yeni özelliği. DSC uzantısı etkinleştirmek için AdvancedOptions ' ForcePullAndApply' eklenen yenileme modu (varsayılan itme modu aksine) çekme olduğunda DSC yapılandırmaları yürürlüğe. Daha fazla bilgi için lütfen [bu blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) DSC uzantı ayarları hakkında daha fazla bilgi almak için.

### <a name="version-215"></a>Sürüm 2.15

- **Yayın Tarihi:** 14 Mart 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - Uzantı sürümü 2.14'da, WMF RTM yüklemek için değişiklikler dahil. 2.13.2.0 için 2.14.0.0 uzantısı sürümden yükseltirken, fark edebilirsiniz bazı DSC cmdlet'leri başarısız veya yapılandırmanızı bir hata ile başarısız – ' No örneği ile özellik değerleri bulundu'. Daha fazla bilgi için bkz: [DSC sürüm notları](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). Bu sorunlara yönelik geçici çözümler 2,15 sürümünde eklenmiştir.
  - Ne yazık ki, sürüm 2.14 zaten yüklediyseniz ve yukarıdaki iki sorunları birine çalıştırıyorsanız, bu adımları el ile yapmanız gerekir.  Yükseltilmiş bir PowerShell oturumunda:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Sürüm 2.14

- **Yayın Tarihi:** 25 Şubat 2016
- **İşletim sistemi desteği:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **WMF desteği:** WMF 5.0 RTM, WMF 4.0
- **Ortam:** Azure
- **Açıklamalar:** bu sürümü Windows Server 2016 Technical Preview içinde yer alan DSC kullanır; diğer Windows işletim sistemleri için yükler [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (yeniden başlatma gerektirir WMF yükleme).
- **Yeni özellikler:**
  - WMF RTM kullanır.
  - DSC uzantı kalitesini artırmak için veri toplamayı etkinleştirir. Daha fazla bilgi için bkz: [blog](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Resource Manager şablonu uzantı için güncelleştirilmiş ayarları biçimi sağlar. Daha fazla bilgi için bkz: [blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Hata düzeltmeleri ve diğer geliştirmeler.

## <a name="next-steps"></a>Sonraki adımlar

- PowerShell DSC hakkında daha fazla bilgi için Git [PowerShell Belge Merkezi](overview.md).
- İncelemek [Resource Manager şablonu DSC uzantısı](/azure/virtual-machines/windows/extensions-dsc-template).
- PowerShell DSC kullanarak yönetebilmeniz için daha fazla işlevsellik ve daha fazla DSC kaynakları Gözat [PowerShell Galerisi](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Yapılandırmaları hassas parametreleri geçirme hakkında daha fazla bilgi için bkz [yönetmek DSC uzantısı işleyici ile güvenli kimlik bilgileri](/azure/virtual-machines/windows/extensions-dsc-credentials).