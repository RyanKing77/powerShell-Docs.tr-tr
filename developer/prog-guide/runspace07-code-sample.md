---
title: Örnek kod RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 232b282e366c9fad167686337696ef2ccd8b30d8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734950"
---
# <a name="runspace07-code-sample"></a>RunSpace07 Kod Örneği

İşte kaynak kodunu Runspace07 örnek bölümünde açıklanan yönelik [bir konsol uygulaması olduğunu ekler komutları bir işlem hattı oluşturma](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Bu örnek uygulama bir çalışma alanı oluşturur, bir işlem hattı oluşturur, iki komutu ardışık düzene ekler ve sonra işlem hattını yürütür. Ardışık düzenine eklenen komutlar `Get-Process` ve `Measure-Object` cmdlet'leri.

> [!NOTE]
> İndirebileceğiniz C# Microsoft .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak kaynak dosyası (runspace07.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)