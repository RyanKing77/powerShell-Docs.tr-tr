---
title: Runspace01 (C#) kod örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: ab067485d70523a16493eb57170615ab300eaa98
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735046"
---
# <a name="runspace01-c-code-sample"></a>Runspace01 (C#) Kod Örneği

İşte kod örnekleri için bir çalışma açıklanan [belirtilen bir komutu bir konsol uygulaması, çalışır oluşturma](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Bunu yapmak için uygulama bir çalışma alanı çağırır ve ardından bir komut çalıştırır. (Unutmayın. Bu uygulama çalışma alanı yapılandırma bilgileri belirtmiyor veya açıkça bir işlem hattı oluşturur). Çağrılan komut `Get-Process` cmdlet'i.

> [!NOTE]
> İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu çalışma alanı için kaynak dosyası (runspace01.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)