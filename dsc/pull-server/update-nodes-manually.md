---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Bir çekme sunucusundan düğüm güncelleştirme
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405670"
---
# <a name="update-nodes-from-a-pull-server"></a>Bir çekme sunucusundan düğüm güncelleştirme

Aşağıdaki bölümler, zaten bir çekme sunucusu ayarladığınızı varsayalım. Çekme sunucunuzu ayarlamadıysanız, aşağıdaki kılavuzları kullanabilirsiniz:

- [Bir DSC SMB çekme sunucusu ayarlama](pullServerSmb.md)
- [Bir DSC HTTP çekme sunucusu ayarlama](pullServer.md)

Her hedef düğüm yapılandırmaları, kaynaklar, indirin ve bile durumunu raporlamak için yapılandırılabilir. Bu makale indirilmesi ve kaynakları otomatik olarak indirmek için istemcileri yapılandırın kullanabilmesi için kaynakları karşıya yükleme işlemini gösterir. Düğümün aldığında atanmış bir yapılandırma yoluyla **çekme** veya **anında iletme** (v5) otomatik olarak karşıdan yüklerken LCM içinde belirtilen konumdan yapılandırma için gerekli tüm kaynakları.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Update-DSCConfiguration cmdlet'i kullanarak

PowerShell 5. 0'den itibaren [güncelleştirme-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet'ini çekme Sunucusu'ndan alana LCM içinde yapılandırılmış yapılandırmasını güncelleştirmek için bir düğüm zorlar.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Invoke-CIMMethod kullanma

PowerShell 4. 0'da, yine de el ile yapılandırma kullanılarak güncelleştirilecek çekme istemci zorlayabilirsiniz [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). Aşağıdaki örnek, bir CIM oturumu belirtilen kimlik bilgilerini oluşturur, uygun CIM yöntemini çağırır ve oturumunu kaldırır.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Ayrıca bkz:

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
