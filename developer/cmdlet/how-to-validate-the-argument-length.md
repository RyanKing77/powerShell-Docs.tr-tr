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
# <a name="how-to-validate-the-argument-length"></a>Bağımsız Değişken Uzunluğunu Doğrulama

Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenin (uzunluk) karakter sayısını denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir. Bu doğrulama kuralı, ValidateLength öznitelik bildirerek ayarlayın.

> [!NOTE]
> Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).

## <a name="to-validate-the-argument-length"></a>Bağımsız değişken uzunluğu doğrulamak için

- Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin. Bu örnek, bağımsız değişkenin uzunluğu 0 ile 10 karakter uzunlukta olması gerektiğini belirtir.

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

Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
