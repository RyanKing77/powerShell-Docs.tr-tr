---
title: Runspace04 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082691"
---
# <a name="runspace04-sample"></a><span data-ttu-id="3f6ed-102">Runspace04 Örneği</span><span class="sxs-lookup"><span data-stu-id="3f6ed-102">Runspace04 Sample</span></span>

<span data-ttu-id="3f6ed-103">Bu örnek nasıl kullanılacağını gösterir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) komutlarını çalıştırmak için sınıf ve komutlarını çalıştırırken oluşturulan catch Sonlandırıcı hataları.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="3f6ed-104">İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişkeni olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="3f6ed-105">Sonuç olarak, hiçbir nesne döndürülür ve bir sonlandırma hatası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f6ed-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f6ed-106">Requirements</span></span>

<span data-ttu-id="3f6ed-107">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3f6ed-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3f6ed-108">Demonstrates</span></span>

<span data-ttu-id="3f6ed-109">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3f6ed-110">Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3f6ed-111">İşlem hattı için komutlar ekleme [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="3f6ed-112">İşlem hattına parametre bağımsız değişkenlerini ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="3f6ed-113">Komutlar zaman uyumlu olarak çalıştırılıyor.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="3f6ed-114">Kullanarak [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) ayıklayın ve komutlar tarafından döndürülen nesne özellikleri görüntülemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="3f6ed-115">Alma ve komutları çalıştırma sırasında oluşturulan hata kaydı görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="3f6ed-116">Yakalama ve komutlar tarafından oluşturulan Sonlandırıcı özel durumlar görüntüleniyor.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="3f6ed-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f6ed-117">Example</span></span>

<span data-ttu-id="3f6ed-118">Bu örnekteki komutlar Windows PowerShell tarafından sağlanan varsayılan çalışma alanındaki zaman uyumlu olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="3f6ed-119">Komutu, geçerli olmayan bir parametre bağımsız değişkenini geçtiğinden son komut bir sonlandırma hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="3f6ed-120">Sonlandırma hatası yakalanan ve görüntülenen.</span><span class="sxs-lookup"><span data-stu-id="3f6ed-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3f6ed-121">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3f6ed-121">See Also</span></span>

[<span data-ttu-id="3f6ed-122">Bir Windows PowerShell ana bilgisayar uygulaması yazma</span><span class="sxs-lookup"><span data-stu-id="3f6ed-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)