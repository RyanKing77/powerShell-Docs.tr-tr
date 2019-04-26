---
title: GetProcessSample01 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068071"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 Örneği

Bu örnek, yerel bilgisayardaki işlemleri alır bir cmdlet uygulamak gösterilmektedir. Bu cmdlet, Basitleştirilmiş bir sürümüdür `Get-Process` Windows PowerShell 2.0 tarafından sağlanan cmdlet'i.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak nasıl.

1. Windows PowerShell 2.0 yüklü SDK ile GetProcessSample01 klasöre gidin. C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01 varsayılan konumdur.

2. Çözüm (.sln) dosyasını simgesini çift tıklatın. Bu örnek projeyi Microsoft Visual Studio'da açılır.

3. İçinde **derleme** menüsünde **Çözümü Derle**.

  Kitaplık için örneği varsayılan \bin veya \bin\debug'dır klasörleri oluşturulur.

### <a name="how-to-run-the-sample"></a>Örneği çalıştırma

1. Bir Komut İstemi penceresi açın.

2. Örnek .dll dosyasını içeren dizine gidin.

3. InstallUtil "GetProcessSample01.dll" çalıştırın.

4. Windows PowerShell’i başlatın.

5. Shell ek bileşenini eklemek için aşağıdaki komutu çalıştırın.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Cmdlet'i çalıştırmak için aşağıdaki komutu girin. `get-proc`

   `get-proc`

   Aşağıdaki adımları sonuçları bir örnek çıktı budur.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Gereksinimler

Bu örnek, Windows PowerShell 1.0 veya üstü gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir.

- Temel örnek bir cmdlet oluşturuluyor.

- Cmdlet'i bir sınıf Cmdlet özniteliği kullanılarak tanımlama.

- Windows PowerShell 1.0 ve Windows PowerShell 2.0 ile çalışan bir ek bileşenini oluşturuluyor. Bunlar Windows PowerShell 2.0 gerektirir böylece sonraki örnekleri modülleri ek bileşenler yerine kullanın.

## <a name="example"></a>Örnek

Bu örnek, basit bir cmdlet ve ek bileşenini nasıl oluşturulacağını gösterir.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)