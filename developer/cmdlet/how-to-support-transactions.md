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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067867"
---
# <a name="how-to-support-transactions"></a>İşlemleri Destekleme

Bu örnek, bir cmdlet için işlemler için destek ekleme temel kod öğeleri gösterir.

> [!IMPORTANT]
> Windows PowerShell işlemleri nasıl işlediği hakkında daha fazla bilgi için bkz. [hakkında işlem][about_Transactions].

## <a name="to-support-transactions"></a>İşlemleri desteklemek için

1. Cmdlet öznitelik bildirdiğinizde, cmdlet işlemleri destekler belirtin.
   Windows PowerShell cmdlet işlemleri desteklediğinde ekler `UseTransaction` çalıştırıldığında cmdlet'e parametre.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Bir yöntem işleme giriş içinde ekleme bir `if` blok bir işlem olup olmadığını belirlemek için.
   Varsa `if` deyimi çözümler için `true`, bu deyimi içinde eylemleri geçerli işleminin bağlamında gerçekleştirilebilir.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
