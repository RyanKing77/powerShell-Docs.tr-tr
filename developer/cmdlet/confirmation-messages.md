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
# <a name="confirmation-messages"></a>Onay İletileri

Bağlı türevleri görüntülenebilen farklı onay mesajları işte [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) çağrılan yöntemlere.

> [!IMPORTANT]
> İstek onayları gösteren örnek kod için bkz [okundu nasıl](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Kaynak belirtme

Çağırarak değiştirilmek üzere olan kaynağı belirtebileceğiniz [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty Fullname =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) yöntemi. Bu durumda, kullanarak kaynak sağlamanız `target` yöntemi ve işlem parametresi, Windows PowerShell tarafından eklenir. Aşağıdaki iletiyi "MyResource" metin etkilediği kaynaktır ve çağrıyı yapan komutun adını işlemdir.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Kullanıcı seçerse **Evet** veya **Tümüne Evet** onayı (gösterildiği gibi aşağıdaki örnekte), bir çağrı isteği [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yapıldığında, görüntülenecek bir ikinci onay iletisi neden olur.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Kaynak ve işlem belirtme

Değiştirilmek üzere olan kaynağı ve komutunu çağırarak gerçekleştirmek üzere işlem belirtebilirsiniz [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty Fullname =](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) yöntemi. Bu durumda, kullanarak kaynak sağlamanız `target` parametresi ve kullanarak işlemi `target` parametresi. Aşağıdaki ileti içinde "MyResource" metin etkilediği kaynak ve gerçekleştirilecek işlemi "MyAction" şeklindedir.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Kullanıcı seçerse **Evet** veya **Tümüne Evet** çağrısı önceki iletiye [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yapıldığında, hangi neden bir Görüntülenecek ikinci onay iletisi.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
