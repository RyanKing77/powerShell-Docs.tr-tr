---
title: Bir bağımsız değişken kümesi doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067731"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="15c8b-102">Bağımsız Değişken Kümesini Doğrulama</span><span class="sxs-lookup"><span data-stu-id="15c8b-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="15c8b-103">Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenini denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15c8b-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="15c8b-104">Bu doğrulama kuralı için parametre bağımsız değişken geçerli değerler sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15c8b-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="15c8b-105">Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="15c8b-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="15c8b-106">Bağımsız değişken doğrulamak için ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="15c8b-106">To validate an argument set</span></span>

- <span data-ttu-id="15c8b-107">Aşağıdaki kodda gösterildiği gibi ValidateSet öznitelik ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15c8b-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="15c8b-108">Bu örnek için üç olası değer kümesini belirtir `UserName` parametresi.</span><span class="sxs-lookup"><span data-stu-id="15c8b-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="15c8b-109">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="15c8b-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15c8b-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="15c8b-110">See Also</span></span>

[<span data-ttu-id="15c8b-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="15c8b-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="15c8b-112">ValidateSet özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="15c8b-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="15c8b-113">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="15c8b-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
