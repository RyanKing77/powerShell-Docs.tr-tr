---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Bilgi Akışı
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856388"
---
# <a name="information-stream"></a>Bilgi Akışı

PowerShell 5.0 ekler yeni yapılandırılmış **bilgi** bir betik ile bunun konağı arasında yapılandırılmış veri iletmek için akış. `Write-Host` Ayrıca, çıkışını yaymak için güncelleştirilmiştir **bilgi** artık yakalamak veya reddedebileceğiniz, sessiz akış. Yeni `Write-Information` cmdlet ile kullanılan **Informationvariable** ve **Informationaction** ortak parametreleri, daha fazla esneklik ve özellik sağlar.

Aşağıdaki işlev yararlanan yeni cmdlet'leri kullanan **bilgi** akış.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

Aşağıdaki örnekler, bu işlevi çalıştırma sonuçları gösterir.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

`$r` Değişkeni betik değişkeninde işlem bilgileri yakalanan `$p`.

```powershell
$r.Id
4008
```

Farklı `Write-Host` cmdlet'ini kullanarak **Informationvariable** parametresinin `Write-Information` bir değişken çıktısında yakalamanıza olanak sağlar. Kullanarak **etiketi**, gönderilen ileti için farklı bir kanal oluşturabilirsiniz **bilgi** akış.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Bir iletiyi gönderdiğinizde **bilgi** stream bu iletiyi bir etikete sahip konak uygulamasında görüntülenmez ancak etiket adı kullanılarak alınabilir. Örneğin:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```