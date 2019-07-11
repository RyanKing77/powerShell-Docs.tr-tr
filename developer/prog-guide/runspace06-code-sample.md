---
title: Örnek kod RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734940"
---
# <a name="runspace06-code-sample"></a>RunSpace06 Kod Örneği

İşte kaynak kodunu Runspace06 örnek bölümünde açıklanan yönelik [bir Windows PowerShell ek bileşenini kullanarak bir çalışma alanı yapılandırma](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Bu örnek uygulama, bir Windows PowerShell, ardından bir işlem hattını tek bir komutla çalıştırmak için kullanılan eklentisinde, temel bir çalışma alanı oluşturur. Bunu yapmak için uygulama çalışma alanı yapılandırma bilgileri oluşturur, bir çalışma alanı oluşturur, tek bir komutla bir işlem hattı oluşturur ve sonra işlem hattını yürütür.

> [!NOTE]
> İndirebileceğiniz C# Windows Vista için Windows Yazılım Geliştirme Seti ve Microsoft .NET Framework 3.0 çalışma zamanı bileşenlerini kullanarak kaynak dosyası (runspace06.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)