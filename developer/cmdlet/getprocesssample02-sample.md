---
title: GetProcessSample02 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849514"
---
# <a name="getprocesssample02-sample"></a>GetProcessSample02 Örneği

Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet yazma işlemi gösterilmektedir. Sağladığı bir `Name` alınacak işlemleri belirtmek için kullanılan parametre. Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak nasıl.

1. Windows PowerShell 2.0 yüklü SDK ile GetProcessSample02 klasöre gidin. C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02 varsayılan konumdur.

2. Çözüm (.sln) dosyasını simgesini çift tıklatın. Bu örnek projeyi Visual Studio'da açılır.

3. İçinde **derleme** menüsünde **Çözümü Derle**.

    Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.

### <a name="how-to-run-the-sample"></a>Örneği çalıştırma

1. Aşağıdaki modül klasörü oluşturun:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Örnek derleme modülü klasöre kopyalayın.

3. Windows PowerShell’i başlatın.

4. Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:

    `import-module getprossessample02`

5. Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:

    `get-proc`

## <a name="requirements"></a>Gereksinimler

Bu örnek, Windows PowerShell 2.0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir.

- Cmdlet özniteliğini kullanarak cmdlet'i sınıf bildirme.

- Parametre özniteliği kullanarak bir cmdlet parametresi bildirme.

- Parametre konumu belirtme.

- Giriş parametresi için bir doğrulama özniteliği bildirme.

## <a name="example"></a>Örnek

Bu örnek, Get-Proc cmdlet'inin içeren bir uygulama gösterir. bir `Name` parametresi.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
