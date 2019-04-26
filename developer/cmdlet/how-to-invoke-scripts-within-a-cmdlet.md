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
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067884"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Cmdlet’teki Betikleri Çağırma

Bu örnek, bir cmdlet için sağlanan bir betik çağırma gösterilmektedir. Komut dosyası, cmdlet tarafından yürütülür ve sonuçları cmdlet'e koleksiyonu olarak döndürülür [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) nesneleri.

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

2. Ardından, betiği döndürülen toplulukta yinelenen [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) nesneleri ve gerekli işlemleri gerçekleştirin.

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
