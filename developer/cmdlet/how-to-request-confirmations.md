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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058836"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="efe85-102">Onay İsteme</span><span class="sxs-lookup"><span data-stu-id="efe85-102">How to Request Confirmations</span></span>

<span data-ttu-id="efe85-103">Bu örnek nasıl çağrılacağını gösterir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) onaylarını gelen istek için yöntem Kullanıcı önce bir eylem yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="efe85-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efe85-104">Windows PowerShell bu isteklerin nasıl işlediği hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="efe85-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="efe85-105">Onay isteme</span><span class="sxs-lookup"><span data-stu-id="efe85-105">To request confirmation</span></span>

1. <span data-ttu-id="efe85-106">Emin `SupportsShouldProcess` cmdlet'i öznitelik parametresinin ayarlandığında `true`.</span><span class="sxs-lookup"><span data-stu-id="efe85-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="efe85-107">(İşlevler için bir parametre CmdletBinding özniteliği budur.)</span><span class="sxs-lookup"><span data-stu-id="efe85-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="efe85-108">Ekleme bir `Force` cmdlet'inize parametresi, böylece kullanıcı onayı isteğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efe85-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="efe85-109">Ekleme bir `if` dönüş değerini kullanan deyimi [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) belirlemek için yöntemi [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="efe85-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="efe85-110">İkinci bir ekleme `if` dönüş değerini kullanan deyimi [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi ve değerini `Force` işlemi gerekip gerekmediğini belirlemek için parametre gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="efe85-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="efe85-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="efe85-111">Example</span></span>

<span data-ttu-id="efe85-112">Aşağıdaki kod örneğinde, [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemleri geçersiz kılma içinde adlandırılır ' ın [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efe85-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="efe85-113">Ancak, bu yöntemler diğer girişini işleme yöntemlerini de çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efe85-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="efe85-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="efe85-114">See Also</span></span>

[<span data-ttu-id="efe85-115">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="efe85-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
