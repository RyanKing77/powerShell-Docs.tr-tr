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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849010"
---
# <a name="how-to-validate-an-argument-count"></a>Bağımsız Değişken Sayısını Doğrulama

Bu örnekte Windows PowerShell çalışma zamanı bir parametreyi kabul eden (sayı) bağımsız değişken sayısı denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir cmdlet çalıştırılmadan önce. Bu doğrulama kuralı, ValidateCount öznitelik bildirerek ayarlayın.

> [!NOTE]
> Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).

## <a name="to-validate-an-argument-count"></a>Bir bağımsız değişken sayısı doğrulamak için

- Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin. Bu örnekte parametre bir bağımsız değişken veya kadar üç bağımsız değişken kabul edeceğini belirtir.

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

Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
