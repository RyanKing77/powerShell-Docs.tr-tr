---
title: Windows PowerShell02 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850361"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 Örneği

Bu örnek, bir çalışma alanı havuzunun çalışma alanlarını kullanarak zaman uyumsuz olarak komutları çalıştırmayı öğrenin gösterir. Örnek komutların bir listesini oluşturur ve gerektiğinde Windows PowerShell altyapısı havuzdan bir çalışma alanı açılırken komutları çalıştırır.

## <a name="requirements"></a>Gereksinimler

- Bu örnek, Windows PowerShell 2.0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir:

- Çalışma alanları aynı zamanda açık izin verilen minimum ve Maksimum sayıda RunspacePool nesne oluşturma.

- Komutların listesini oluşturuluyor.

- Komutlar zaman uyumsuz olarak çalışıyor.

- Çağırma [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) ücretsiz kaç çalışma alanlarını görmek için yöntemi.

- Komut çıktısı ile yakalama [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) yöntemi.

## <a name="example"></a>Örnek

Bu örnek nasıl açılacağını çalışma havuzun çalışma alanları ve komutlar bu çalışma alanlarında zaman uyumsuz olarak çalıştırmak nasıl gösterir.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell ana bilgisayar uygulaması yazma](./writing-a-windows-powershell-host-application.md)