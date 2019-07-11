---
title: Örnek kod RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734960"
---
# <a name="runspace05-code-sample"></a>RunSpace05 Kod Örneği

Açıklanan Runspace05 örnek kaynak kodu işte [kullanarak bir çalışma alanı RunspaceConfiguration yapılandırma](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). Bu örnek, çalışma alanı yapılandırma bilgileri oluşturmak, bir çalışma alanı oluşturma, tek bir komutla bir işlem hattı oluşturursunuz ve ardından işlem hattı yürütme işlemi gösterilmektedir. Yürütülen komut `Get-Process` cmdlet'i.

> [!NOTE]
> İndirebileceğiniz C# Windows Yazılım Geliştirme Seti için Windows Vista Microsoft ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace05.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)