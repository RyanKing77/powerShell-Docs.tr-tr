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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846161"
---
# <a name="how-to-validate-an-argument-pattern"></a>Bağımsız Değişken Desenini Doğrulama

Bu örnek, çalışma zamanı Windows PowerShell cmdlet çalıştırılmadan önce parametre bağımsız değişkenini karakteri desenini denetlemek için kullanabileceğiniz bir doğrulama kuralı belirtmek gösterilmektedir. Bu doğrulama kuralı, ValidatePattern öznitelik bildirerek ayarlayın.

> [!NOTE]
> Bu öznitelik tanımlayan sınıf hakkında daha fazla bilgi için bkz: [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).

## <a name="to-validate-an-argument-pattern"></a>Bir bağımsız değişken desen doğrulamak için

- Aşağıdaki kodda gösterildiği gibi doğrulama özniteliğini ekleyin. Bu örnekte, her sayı 0 ile 9 arasında bir değer olduğu dört basamak desenini belirtir.

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

Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md).

## <a name="see-also"></a>Ayrıca bkz:

[ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
