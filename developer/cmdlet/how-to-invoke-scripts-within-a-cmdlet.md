---
title: Komut dosyalarını bir Cmdlet içinde çağırmak nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846700"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Cmdlet’teki Betikleri Çağırma

Bu örnek, bir cmdlet için sağlanan bir betik çağırma gösterilmektedir. Komut dosyası, cmdlet tarafından yürütülür ve sonuçları cmdlet'e koleksiyonu olarak döndürülür [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) nesneleri.

## <a name="to-invoke-a-script-block"></a>Bir betik bloğu çağırmak için

1. Komut, bir komut dosyası bloğu cmdlet'e sağlanmadı doğrular. Bir betik bloğu sağlandıysa, betik bloğunun kendi gereken parametrelerle komutu çağırır.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Ardından, betiği döndürülen toplulukta yinelenen [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) nesneleri ve gerekli işlemleri gerçekleştirin.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
