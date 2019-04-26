---
title: PowerShell Core’da WS-Management (WSMan) Uzaktan İletişimi
description: PowerShell core'da WSMan kullanarak uzaktan iletişim
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058888"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>PowerShell Core’da WS-Management (WSMan) Uzaktan İletişimi

## <a name="instructions-to-create-a-remoting-endpoint"></a>Bir uzak uç noktası oluşturmaya ilişkin yönergeler

Bir eklenti WinRM Windows PowerShell Core paketi içerir (`pwrshplugin.dll`) ve bir yükleme komut dosyası (`Install-PowerShellRemoting.ps1`) içinde `$PSHome`.
Bu dosyalar, uç nokta belirtildiğinde gelen PowerShell uzak bağlantıları kabul etmek üzere PowerShell etkinleştirin.

### <a name="motivation"></a>Motivasyon

PowerShell yüklemesi kullanarak uzak bilgisayarlarla PowerShell oturumları kurup `New-PSSession` ve `Enter-PSSession`.
Gelen PowerShell uzak bağlantıları kabul etmek üzere etkinleştirmek için kullanıcı bir WinRM uzaktan iletişim uç noktası oluşturmanız gerekir.
Bu kullanıcı WinRM uç nokta oluşturmak için Yükle-PowerShellRemoting.ps1 çalıştığı bir açık katılımı senaryodur.
Biz ek işlevsellik eklemek kadar yükleme komut dosyasını kısa vadeli bir çözüm olan `Enable-PSRemoting` aynı eylemi gerçekleştirmek için.
Daha fazla ayrıntı için lütfen sorun bakın [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Betik eylemleri

Komut dosyası

1. İçinde eklenti için bir dizin oluşturur. `$env:windir\System32\PowerShell`
1. Pwrshplugin.dll o konuma kopyalar.
1. Bir yapılandırma dosyası oluşturur
1. WinRM ile bu eklenti kayıtları

### <a name="registration"></a>Kayıt

Betik, bir yönetici düzeyinde PowerShell oturumu ve iki modda çalışan içinde yürütülmelidir.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Bunu kaydolacak PowerShell örneği tarafından yürütülen

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Başka bir PowerShell örneği, kaydolacak örneği adına yürüten

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Örneğin:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**NOT:** Uzak Kayıt betiği, tüm PSRP oturumlarına hemen komut dosyası çalıştırıldıktan sonra sona erecek şekilde WinRM, yeniden başlatılır. Uzak oturum sırasında çalıştırırsanız, bu bağlantı sonlandırılacak.

## <a name="how-to-connect-to-the-new-endpoint"></a>Yeni uç noktasına bağlanma

Yeni PowerShell uç noktası için bir PowerShell oturumu belirterek oluşturun `-ConfigurationName "some endpoint name"`. Yukarıdaki örnekte PowerShell örneğine bağlanmak için kullanın:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Unutmayın `New-PSSession` ve `Enter-PSSession` belirtmeyin çağrılarını `-ConfigurationName` varsayılan PowerShell uç noktası hedeflediğini `microsoft.powershell`.