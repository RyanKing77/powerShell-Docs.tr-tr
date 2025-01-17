---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1'de bilinen sorunlar
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856367"
---
# <a name="known-issues-in-wmf-51"></a>WMF 5.1'de bilinen sorunlar

## <a name="starting-powershell-shortcut-as-administrator"></a>Yönetici olarak PowerShell kısayolu başlatılıyor

WMF yükleme sırasında kısayol yönetici olarak PowerShell başlatmaya çalışırsanız, bir "Bilinmeyen hata" iletisi alabilirsiniz. Yönetici olmayan kısaca yeniden açın ve kısayol artık yönetici olarak da çalışır.

## <a name="pester"></a>Pester

Bu sürümde, Pester Nano Sunucu'da kullanırken bilmeniz gereken iki sorun vardır:

- Testleri Pester karşı çalışan bazı hataları tam CLR ve CORE CLR farklılıklardan dolayı neden olabilir. Özellikle, **doğrulama** yöntemi kullanılabilir değil **XmlDocument** türü. NUnit çıktı günlüklerini şemasını onaylamaya altı testleri başarısız olduğu bilinmektedir.
- Bir kod kapsamı test başarısız çünkü **WindowsFeature** Nano Server'da DSC kaynak mevcut değil. Ancak, bu hatalar genellikle zararsızdır ve güvenle yoksayılabilir.

## <a name="operation-validation"></a>İşlem doğrulama

- `Update-Help` çalışmayan Yardım URI nedeniyle Microsoft.PowerShell.Operation.Validation modülü başarısız

## <a name="dsc-after-uninstall-wmf"></a>DSC sonra WMF kaldırma

- WMF kaldırma DSC MOF belgeleri yapılandırma klasörden silmez. MOF belgeleri eski sistemlerde kullanılabilir olmayan yeni özellikler içeriyorsa DSC düzgün şekilde çalışmaz. Bu durumda, DSC durumları temizlemek için yükseltilmiş bir PowerShell konsolundan aşağıdaki betiği çalıştırın.

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>JEA sanal hesaplar

JEA uç noktaları ve WMF 5.0 ile sanal hesaplar kullanacak şekilde yapılandırılmış oturum yapılandırmaları WMF 5.1 sürümüne yükselttikten sonra sanal bir hesabı kullanacak şekilde yapılandırılmaz. Bu, JEA oturumlarında çalışan komutlar potansiyel olarak kullanıcı yükseltilmiş ayrıcalıklar gerektiren komutlar çalışmasını engelliyor. bir geçici yönetici hesabı yerine bağlanan kullanıcının kimliği altında çalışacağı anlamına gelir. Sanal hesaplar geri yüklemek için kaydını kaldırma ve sanal hesaplar kullanan herhangi bir oturum yapılandırmaları yeniden kaydetmeniz gerekir.

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