---
title: Bir bağımsız değişken sayısı doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067816"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="7b6fe-102">Bağımsız Değişken Sayısını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="7b6fe-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="7b6fe-103">Bu örnekte Windows PowerShell çalışma zamanı bir parametreyi kabul eden (sayı) bağımsız değişken sayısı denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir cmdlet çalıştırılmadan önce.</span><span class="sxs-lookup"><span data-stu-id="7b6fe-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="7b6fe-104">Bu doğrulama kuralı, ValidateCount öznitelik bildirerek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7b6fe-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="7b6fe-105">Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="7b6fe-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="7b6fe-106">Bir bağımsız değişken sayısı doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="7b6fe-106">To validate an argument count</span></span>

- <span data-ttu-id="7b6fe-107">Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b6fe-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="7b6fe-108">Bu örnekte parametre bir bağımsız değişken veya kadar üç bağımsız değişken kabul edeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b6fe-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="7b6fe-109">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7b6fe-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b6fe-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7b6fe-110">See Also</span></span>

[<span data-ttu-id="7b6fe-111">ValidateCount özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="7b6fe-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="7b6fe-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="7b6fe-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
