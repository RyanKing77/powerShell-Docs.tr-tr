---
title: GetProcessSample04 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068037"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 Örneği

Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet uygulamak gösterilmektedir. Bir işlem alınırken bir hata oluşması halinde olmak üzere sonlandırmasız bir hata oluşturur. Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak nasıl.

1. Windows PowerShell 2.0 yüklü SDK ile GetProcessSample04 klasöre gidin. C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04 varsayılan konumdur.

2. Çözüm (.sln) dosyasını simgesini çift tıklatın. Bu örnek projeyi Visual Studio'da açılır.

3. İçinde **derleme** menüsünde **Çözümü Derle**.

    Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.

### <a name="how-to-run-the-sample"></a>Örneği çalıştırma

1. Aşağıdaki modül klasörü oluşturun:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Örnek derleme modülü klasöre kopyalayın.

3. Windows PowerShell’i başlatın.

4. Windows PowerShell içinde derlemesini yüklemek için aşağıdaki komutu çalıştırın:

    `Import-module getprossessample04`

5. Cmdlet'i çalıştırmak için aşağıdaki komutu çalıştırın:

    `get-proc`

## <a name="requirements"></a>Gereksinimler

Bu örnek, Windows PowerShell 2.0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir.

- Cmdlet özniteliğini kullanarak cmdlet'i sınıf bildirme.

- Parametre özniteliği kullanarak bir cmdlet parametresi bildirme.

- Parametre konumu belirtme.

- Parametresi ardışık düzen tarafından giriş alan belirtilmesi. Giriş bir nesne veya bir parametre adı ile aynı özellik adı olan bir nesnenin bir özellik değerinden alınabilir.

- Giriş parametresi için bir doğrulama özniteliği bildirme.

- Olmak üzere sonlandırmasız bir hata ve hata akışına bir hata iletisi yazmak.

## <a name="example"></a>Örnek

Bu örnek, bir cmdlet'i olmak üzere sonlandırmasız hatalar işleme ve hata iletileri hata akışa Yazar oluşturma işlemi gösterilmektedir.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
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
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
