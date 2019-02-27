---
title: Bir Windows PowerShell komut dosyası kullanarak bir iş akışı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844747"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Windows PowerShell Betiği Kullanarak İş Akışı Oluşturma

Bir Windows PowerShell komut dosyasını yazmayarak bir iş akışı oluşturabilirsiniz. Bir iş akışı oluşturmak için betik gövdesi önce iş akışı için bir ad tarafından izlenen iş akışı anahtar sözcüğünü kullanın. Örneğin:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

İş akışı, herhangi bir Windows PowerShell komutu olduğu aynı şekilde bulabilirsiniz.

## <a name="implementing-parallel-and-sequence"></a>Paralel ve sıralı uygulama

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) paralel etkinliklerin yürütülmesini destekler. Bu özellik bir Windows PowerShell komut dosyası uygulamak `parallel` anahtar sözcüğü bir betik bloğu önünde. Ayrıca `foreach -parallel` paralel nesnelerden oluşan bir koleksiyon üzerinden yineleme yapmak için yapı. Bir grup etkinlik paralel bloğu içinde sırayla yürütmek için betik bloğunda etkinlikleri grubu alın ve blok dizisi anahtar sözcüğü ile koyun.

## <a name="joining-computers-to-a-domain"></a>Bilgisayar bir etki alanına katma

Aşağıdaki betik, bir grup kullanıcı tarafından belirtilen bir bilgisayar etki alanı durumunu denetler, zaten birleştirilmemiş ve sonra durumu yeniden denetler bunları bir etki alanına katılan bir iş akışı oluşturur. Bu, açıklandığı bir XAML iş akışı betiği sürümüdür [Windows PowerShell etkinlikleriyle iş akışı oluşturma](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```