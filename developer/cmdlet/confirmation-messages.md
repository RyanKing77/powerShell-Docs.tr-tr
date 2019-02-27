---
title: Onay mesajları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850606"
---
# <a name="confirmation-messages"></a><span data-ttu-id="6022e-102">Onay İletileri</span><span class="sxs-lookup"><span data-stu-id="6022e-102">Confirmation Messages</span></span>

<span data-ttu-id="6022e-103">Bağlı türevleri görüntülenebilen farklı onay mesajları işte [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) çağrılan yöntemlere.</span><span class="sxs-lookup"><span data-stu-id="6022e-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6022e-104">İstek onayları gösteren örnek kod için bkz [okundu nasıl](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="6022e-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="6022e-105">Kaynak belirtme</span><span class="sxs-lookup"><span data-stu-id="6022e-105">Specifying the Resource</span></span>

<span data-ttu-id="6022e-106">Çağırarak değiştirilmek üzere olan kaynağı belirtebileceğiniz [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty Fullname =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6022e-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="6022e-107">Bu durumda, kullanarak kaynak sağlamanız `target` yöntemi ve işlem parametresi, Windows PowerShell tarafından eklenir.</span><span class="sxs-lookup"><span data-stu-id="6022e-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="6022e-108">Aşağıdaki iletiyi "MyResource" metin etkilediği kaynaktır ve çağrıyı yapan komutun adını işlemdir.</span><span class="sxs-lookup"><span data-stu-id="6022e-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6022e-109">Kullanıcı seçerse **Evet** veya **Tümüne Evet** onayı (gösterildiği gibi aşağıdaki örnekte), bir çağrı isteği [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yapıldığında, görüntülenecek bir ikinci onay iletisi neden olur.</span><span class="sxs-lookup"><span data-stu-id="6022e-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="6022e-110">Kaynak ve işlem belirtme</span><span class="sxs-lookup"><span data-stu-id="6022e-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="6022e-111">Değiştirilmek üzere olan kaynağı ve komutunu çağırarak gerçekleştirmek üzere işlem belirtebilirsiniz [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty Fullname =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6022e-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="6022e-112">Bu durumda, kullanarak kaynak sağlamanız `target` parametresi ve kullanarak işlemi `target` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6022e-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="6022e-113">Aşağıdaki ileti içinde "MyResource" metin etkilediği kaynak ve gerçekleştirilecek işlemi "MyAction" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="6022e-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6022e-114">Kullanıcı seçerse **Evet** veya **Tümüne Evet** çağrısı önceki iletiye [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yapıldığında, hangi neden bir Görüntülenecek ikinci onay iletisi.</span><span class="sxs-lookup"><span data-stu-id="6022e-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="6022e-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6022e-115">See Also</span></span>

[<span data-ttu-id="6022e-116">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="6022e-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
