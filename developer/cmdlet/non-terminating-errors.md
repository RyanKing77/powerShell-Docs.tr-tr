---
title: Sonlandırıcı olmayan hatalar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067663"
---
# <a name="non-terminating-errors"></a>Sonlandırıcı Olmayan Hatalar

Bu konuda, sonlandırıcı olmayan hatalara bildirmek için kullanılan yöntem anlatılmaktadır. Ayrıca, cmdlet yöntemi çağırmak nasıl açıklar.

Sonlandırıcı olmayan bir hata oluştuğunda, cmdlet bu hatayı çağırarak bildirmelidir [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi. Cmdlet'i bir sonlandırıcı olmayan hata bildirdiğinde, cmdlet daha fazla gelen ve bu giriş nesnesi üzerinde çalışmaya devam edebilir işlem hattı nesneleri. Cmdlet çağırırsa [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi, cmdlet sonlandırmayan hataya neden olan koşul açıklayan bir hata kaydı yazabilirsiniz. Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).

Cmdlet'leri çağırabilir [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) gerektiğinde gelen yöntemleri işleme kendi girdideki. Ancak, cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) çağrılan iş parçacığından [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), veya [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) giriş işleme yöntemi. Çağırmayın [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) başka bir iş parçacığından. Bunun yerine, hataları tekrar ana iş parçacığı iletişim kurar.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell hata kaydı](./windows-powershell-error-records.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
