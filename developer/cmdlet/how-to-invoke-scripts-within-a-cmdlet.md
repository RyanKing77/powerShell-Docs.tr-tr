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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="a82ca-102">Cmdlet’teki Betikleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="a82ca-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="a82ca-103">Bu örnek, bir cmdlet için sağlanan bir betik çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a82ca-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="a82ca-104">Komut dosyası, cmdlet tarafından yürütülür ve sonuçları cmdlet'e koleksiyonu olarak döndürülür [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a82ca-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="a82ca-105">Bir betik bloğu çağırmak için</span><span class="sxs-lookup"><span data-stu-id="a82ca-105">To invoke a script block</span></span>

1. <span data-ttu-id="a82ca-106">Komut, bir komut dosyası bloğu cmdlet'e sağlanmadı doğrular.</span><span class="sxs-lookup"><span data-stu-id="a82ca-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="a82ca-107">Bir betik bloğu sağlandıysa, betik bloğunun kendi gereken parametrelerle komutu çağırır.</span><span class="sxs-lookup"><span data-stu-id="a82ca-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="a82ca-108">Ardından, betiği döndürülen toplulukta yinelenen [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) nesneleri ve gerekli işlemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="a82ca-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a82ca-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a82ca-109">See Also</span></span>

[<span data-ttu-id="a82ca-110">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="a82ca-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)