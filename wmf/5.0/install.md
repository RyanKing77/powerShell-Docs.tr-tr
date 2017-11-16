---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
ms.openlocfilehash: 668a5b20add58ff5e23f35d6cebddc39c64ce926
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="installation-instructions"></a>Yükleme yönergeleri

İşletim sistemi ve mimarisi için doğru paketini indirin:

| İşletim Sistemi       | Mimari | Paket adı              | 
|------------------------|--------------|---------------------------| 
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2 KB3134758 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) | 
| Windows Server 2012    | x64      | [W2K12 KB3134759 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) | 
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2 KB3134760 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2 KB3134758 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1 KB3134758 x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2 KB3134760 x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7 KB3134760 x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Windows Gezgini (veya Windows Server 2012 R2 ve Windows 8.1 dosya Gezgini'nde) WMF 5.0 yüklemek için:**

1. MSU dosyasının yüklediğiniz klasöre gidin.

2. Çalıştırmak için MSU çift tıklayın.

**WMF 5.0 komut isteminden yüklemek için:** 

1. Bilgisayarınızın mimarisi için doğru paket indirdikten sonra yükseltilmiş kullanıcı haklarıyla (yönetici olarak çalıştır) bir komut istemi penceresi açın. Üzerinde Sunucu Çekirdeği yükleme seçenekleri Windows Server 2012 R2 veya Windows Server 2012 veya Windows Server 2008 R2 SP1, varsayılan olarak yükseltilmiş kullanıcı haklarıyla bir komut istemi açar.

2. Dizinleri içine varsa indirilen veya WMF 5.0 yükleme paketini kopyaladığınız klasöre gidin.

3. Aşağıdaki komutlardan birini çalıştırın:
    - Windows Server 2012 R2 veya Windows 8.1 x64 çalıştıran bilgisayarlarda çalıştırmak **Win8.1AndW2K12R2 KB3134758 x64.msu quiet**.
    - Windows Server 2012 çalıştıran bilgisayarlarda çalıştırmak **W2K12 KB3134759 x64.msu quiet**.
    - X 64 Windows Server 2008 R2 SP1 veya Windows 7 SP1 çalıştıran bilgisayarlarda çalıştırmak **Win7AndW2K8R2 KB3134760 x64.msu quiet**.
    - Windows 8.1 x86 çalıştıran bilgisayarlarda çalıştırmak **Win8.1 KB3134758 x86.msu quiet**.
    - X 86 Windows 7 SP1 çalıştıran bilgisayarlarda çalıştırmak **Win7 KB3134760 x86.msu quiet**.

**Windows Server 2008 SP1 ve Windows 7 SP1 için ek yükleme notları:**

Aşağıdaki önkoşulların karşılandığından emin olun:
- En son hizmet paketine yüklenir.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) yüklenir

*WinRM bağımlılık:* Windows PowerShell istenen durum yapılandırması (DSC) üzerinde WinRM bağlıdır. WinRM Windows Server 2008 R2 ve Windows 7 varsayılan olarak etkin değildir. WinRM, etkinleştirmek için bir Windows PowerShell oturumunda çalıştırın, yükseltilmiş **Set-WSManQuickConfig**.


