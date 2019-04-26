---
title: Bağımsız değişken uzunluğu doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067729"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="303e4-102">Bağımsız Değişken Uzunluğunu Doğrulama</span><span class="sxs-lookup"><span data-stu-id="303e4-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="303e4-103">Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenin (uzunluk) karakter sayısını denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="303e4-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="303e4-104">Bu doğrulama kuralı, ValidateLength öznitelik bildirerek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="303e4-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="303e4-105">Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="303e4-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="303e4-106">Bağımsız değişken uzunluğu doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="303e4-106">To validate the argument length</span></span>

- <span data-ttu-id="303e4-107">Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="303e4-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="303e4-108">Bu örnek, bağımsız değişkenin uzunluğu 0 ile 10 karakter uzunlukta olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="303e4-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="303e4-109">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="303e4-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="303e4-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="303e4-110">See Also</span></span>

[<span data-ttu-id="303e4-111">ValidateLength özniteliği bildirimi</span><span class="sxs-lookup"><span data-stu-id="303e4-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="303e4-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="303e4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
