---
title: İşlemleri desteklemek nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847596"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="4de4d-102">İşlemleri Destekleme</span><span class="sxs-lookup"><span data-stu-id="4de4d-102">How to Support Transactions</span></span>

<span data-ttu-id="4de4d-103">Bu örnek, bir cmdlet için işlemler için destek ekleme temel kod öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="4de4d-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4de4d-104">Windows PowerShell işlemleri nasıl işlediği hakkında daha fazla bilgi için bkz. [hakkında işlem][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="4de4d-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="4de4d-105">İşlemleri desteklemek için</span><span class="sxs-lookup"><span data-stu-id="4de4d-105">To support transactions</span></span>

1. <span data-ttu-id="4de4d-106">Cmdlet öznitelik bildirdiğinizde, cmdlet işlemleri destekler belirtin.</span><span class="sxs-lookup"><span data-stu-id="4de4d-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="4de4d-107">Windows PowerShell cmdlet işlemleri desteklediğinde ekler `UseTransaction` çalıştırıldığında cmdlet'e parametre.</span><span class="sxs-lookup"><span data-stu-id="4de4d-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="4de4d-108">Bir yöntem işleme giriş içinde ekleme bir `if` blok bir işlem olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="4de4d-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="4de4d-109">Varsa `if` deyimi çözümler için `true`, bu deyimi içinde eylemleri geçerli işleminin bağlamında gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4de4d-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="4de4d-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4de4d-110">See Also</span></span>

[<span data-ttu-id="4de4d-111">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="4de4d-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
