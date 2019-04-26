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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="786bc-102">Cmdlet’teki Betikleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="786bc-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="786bc-103">Bu örnek, bir cmdlet için sağlanan bir betik çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="786bc-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="786bc-104">Komut dosyası, cmdlet tarafından yürütülür ve sonuçları cmdlet'e koleksiyonu olarak döndürülür [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="786bc-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="786bc-105">Bir betik bloğu çağırmak için</span><span class="sxs-lookup"><span data-stu-id="786bc-105">To invoke a script block</span></span>

1. <span data-ttu-id="786bc-106">Komut, bir komut dosyası bloğu cmdlet'e sağlanmadı doğrular.</span><span class="sxs-lookup"><span data-stu-id="786bc-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="786bc-107">Bir betik bloğu sağlandıysa, betik bloğunun kendi gereken parametrelerle komutu çağırır.</span><span class="sxs-lookup"><span data-stu-id="786bc-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="786bc-108">Ardından, betiği döndürülen toplulukta yinelenen [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) nesneleri ve gerekli işlemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="786bc-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="786bc-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="786bc-109">See Also</span></span>

[<span data-ttu-id="786bc-110">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="786bc-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
