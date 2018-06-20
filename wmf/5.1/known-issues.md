---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1 bilinen sorunlar
ms.openlocfilehash: d53031bea978087c68fcb22989c7cd2e2cf2d9fa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219462"
---
# <a name="known-issues-in-wmf-51"></a>WMF 5.1 bilinen sorunlar #

> Not: Bu bilgiler değiştirilebilir olur.

## <a name="starting-powershell-shortcut-as-administrator"></a>Yönetici olarak PowerShell kısayol başlatma
WMF yükledikten sonra kısayol yönetici olarak PowerShell başlatmaya çalışırsanız, "Belirtilmeyen hata" iletisi alabilirsiniz.
Yönetici olmayan kısaca yeniden açın ve kısayol şimdi bile yönetici olarak çalışır.

## <a name="pester"></a>Pester
Bu sürümde Pester Nano Server kullanırken bilmeniz gereken iki sorunlar vardır:

* Testleri Pester karşı çalışan bazı hatalar tam CLR ve çekirdek CLR arasındaki farklar nedeniyle neden olabilir. Özellikle, doğrula yöntemini XmlDocument türünde kullanılamaz. NUnit Çıktı günlükleri şeması doğrulamaya altı testleri başarısız olduğu bilinmektedir.
* Kod kapsamı test başarısız şu anda çünkü *WindowsFeature* DSC kaynağı Nano Server yok. Ancak, bu hatalar genellikle zararsız olan ve güvenle yoksayılabilir.

## <a name="operation-validation"></a>İşlemi doğrulama

* Çalışma dışı Yardım URI nedeniyle Microsoft.PowerShell.Operation.Validation modülü için Update-Help başarısız

## <a name="dsc-after-uninstall-wmf"></a>DSC sonra WMF kaldırma
* WMF kaldırma DSC MOF belgeleri yapılandırma klasöründen silinmez. MOF belgeleri eski sistemlerinde kullanılabilir olmayan daha yeni özellikler içeriyorsa DSC düzgün çalışmaz. Bu durumda, aşağıdaki komut dosyasını yükseltilmiş PowerShell konsolundan DSC durumları temizlemek için çalıştırın.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a>JEA sanal hesaplar
JEA uç noktaları ve sanal hesaplar WMF 5.0 ile kullanmak üzere yapılandırılmış oturum yapılandırmaları WMF 5.1 sürümüne yükselttikten sonra sanal hesap kullanmak için yapılandırılmaz.
Bu, JEA oturumlarında çalışan komutlar olası kullanıcı yükseltilmiş ayrıcalıklar gerektiren komutlar çalışmasını engelleyen bir geçici yönetici hesabı yerine bağlanan kullanıcının kimliği altında çalışacağı anlamına gelir.
Sanal hesaplar geri yüklemek için kaydı ve sanal hesapları kullanan tüm oturum yapılandırmaları yeniden kaydetmeniz gerekir.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
