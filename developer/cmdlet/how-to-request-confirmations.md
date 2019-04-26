---
title: Onayları nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067850"
---
# <a name="how-to-request-confirmations"></a>Onay İsteme

Bu örnek nasıl çağrılacağını gösterir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) onaylarını gelen istek için yöntem Kullanıcı önce bir eylem yapılmaz.

> [!IMPORTANT]
> Windows PowerShell bu isteklerin nasıl işlediği hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Onay isteme

1. Emin `SupportsShouldProcess` cmdlet'i öznitelik parametresinin ayarlandığında `true`. (İşlevler için bir parametre CmdletBinding özniteliği budur.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Ekleme bir `Force` cmdlet'inize parametresi, böylece kullanıcı onayı isteğini geçersiz kılabilirsiniz.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Ekleme bir `if` dönüş değerini kullanan deyimi [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) belirlemek için yöntemi [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi çağrılır.

4. İkinci bir ekleme `if` dönüş değerini kullanan deyimi [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi ve değerini `Force` işlemi gerekip gerekmediğini belirlemek için parametre gerçekleştirdi.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemleri geçersiz kılma içinde adlandırılır ' ın [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi. Ancak, bu yöntemler diğer girişini işleme yöntemlerini de çağırabilirsiniz.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
