---
title: GetProc02 (C#) örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 740e8d60b71654b82020d16b2964165f3ee1e600
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851229"
---
# <a name="getproc02-c-sample-code"></a>GetProc02 (C#) Örnek Kod

Aşağıdaki kod uygulamasını gösterir. bir `Get-Process` komut satırı girişi kabul eden cmdlet'i. Bu uygulama tanımlar dikkat edin bir `Name` parametresi komut satırı girişi ve izin vermek için kullandığı [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) çıkışın gösterdiği gibi yöntemi mekanizması, çıkış göndermek için işlem hattına nesneleri.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)