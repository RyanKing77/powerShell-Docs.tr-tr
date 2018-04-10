---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 89f0deaece27e2d207dfb820d4df80e427c9cb94
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="installation-instructions"></a>Yükleme yönergeleri

İşletim sistemi ve mimarisi için doğru paketini indirin:

| İşletim Sistemi       | Mimari | Paket adı              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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