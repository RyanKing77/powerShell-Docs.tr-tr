---
title: Bir bağımsız değişken desen doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067782"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="048b9-102">Bağımsız Değişken Desenini Doğrulama</span><span class="sxs-lookup"><span data-stu-id="048b9-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="048b9-103">Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenini karakteri desenini denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="048b9-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="048b9-104">Bu doğrulama kuralı, ValidatePattern öznitelik bildirerek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="048b9-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="048b9-105">Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="048b9-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="048b9-106">Bir bağımsız değişken desen doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="048b9-106">To validate an argument pattern</span></span>

- <span data-ttu-id="048b9-107">Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="048b9-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="048b9-108">Bu örnekte, her sayı 0 ile 9 arasında bir değer olduğu dört basamak desenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="048b9-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="048b9-109">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="048b9-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="048b9-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="048b9-110">See Also</span></span>

[<span data-ttu-id="048b9-111">ValidatePattern özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="048b9-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="048b9-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="048b9-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
