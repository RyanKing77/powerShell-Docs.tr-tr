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
# <a name="information-stream"></a><span data-ttu-id="071ae-103">Bilgi Akışı</span><span class="sxs-lookup"><span data-stu-id="071ae-103">Information Stream</span></span>

<span data-ttu-id="071ae-104">PowerShell 5.0 ekler yeni yapılandırılmış **bilgi** bir betik ile bunun konağı arasında yapılandırılmış veri iletmek için akış.</span><span class="sxs-lookup"><span data-stu-id="071ae-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="071ae-105">`Write-Host` Ayrıca, çıkışını yaymak için güncelleştirilmiştir **bilgi** artık yakalamak veya reddedebileceğiniz, sessiz akış.</span><span class="sxs-lookup"><span data-stu-id="071ae-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="071ae-106">Yeni `Write-Information` cmdlet ile kullanılan **Informationvariable** ve **Informationaction** ortak parametreleri, daha fazla esneklik ve özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="071ae-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="071ae-107">Aşağıdaki işlev yararlanan yeni cmdlet'leri kullanan **bilgi** akış.</span><span class="sxs-lookup"><span data-stu-id="071ae-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="071ae-108">Aşağıdaki örnekler, bu işlevi çalıştırma sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="071ae-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="071ae-109">`$r` Değişkeni betik değişkeninde işlem bilgileri yakalanan `$p`.</span><span class="sxs-lookup"><span data-stu-id="071ae-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="071ae-110">Farklı `Write-Host` cmdlet'ini kullanarak **Informationvariable** parametresinin `Write-Information` bir değişken çıktısında yakalamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="071ae-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="071ae-111">Kullanarak **etiketi**, gönderilen ileti için farklı bir kanal oluşturabilirsiniz **bilgi** akış.</span><span class="sxs-lookup"><span data-stu-id="071ae-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="071ae-112">Bir iletiyi gönderdiğinizde **bilgi** stream bu iletiyi bir etikete sahip konak uygulamasında görüntülenmez ancak etiket adı kullanılarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="071ae-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="071ae-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="071ae-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```