---
title: Bir bağımsız değişkeni aralık doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067799"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="70b02-102">Bağımsız Değişken Aralığını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="70b02-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="70b02-103">Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenin minimum ve maksimum değerleri denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="70b02-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="70b02-104">Bu doğrulama kuralı, ValidateRange öznitelik bildirerek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70b02-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="70b02-105">Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="70b02-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="70b02-106">Bir bağımsız değişkeni aralık doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="70b02-106">To validate an argument range</span></span>

- <span data-ttu-id="70b02-107">Aşağıdaki kodda gösterildiği gibi ValidateRange öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="70b02-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="70b02-108">Bu örnek için 0 ile 5 bir dizi belirtir `InputData` parametresi.</span><span class="sxs-lookup"><span data-stu-id="70b02-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="70b02-109">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="70b02-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70b02-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="70b02-110">See Also</span></span>

[<span data-ttu-id="70b02-111">ValidateRange özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="70b02-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="70b02-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="70b02-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
