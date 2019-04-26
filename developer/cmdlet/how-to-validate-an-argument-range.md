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
# <a name="how-to-validate-an-argument-range"></a>Bağımsız Değişken Aralığını Doğrulama

Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenin minimum ve maksimum değerleri denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir. Bu doğrulama kuralı, ValidateRange öznitelik bildirerek ayarlayın.

> [!NOTE]
> Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).

### <a name="to-validate-an-argument-range"></a>Bir bağımsız değişkeni aralık doğrulamak için

- Aşağıdaki kodda gösterildiği gibi ValidateRange öznitelik ekleyin. Bu örnek için 0 ile 5 bir dizi belirtir `InputData` parametresi.

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

Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
