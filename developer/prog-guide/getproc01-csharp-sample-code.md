---
title: GetProc01 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430086"
---
# <a name="getproc01-c-sample-code"></a>GetProc01 (C#) Örnek Kod

Aşağıdaki kod GetProc01 örnek cmdlet uygulamasını gösterir. Cmdlet için alma işlemi asıl işi bırakarak basitleştirilmiştir fark [System.Diagnostics.Process.Getprocesses*](/dotnet/api/System.Diagnostics.Process.GetProcesses) yöntemi.

> [!NOTE]
> İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu Get-Proc cmdlet için kaynak dosyası (getproc01.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)