---
title: Events01 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229294"
---
# <a name="events01-sample"></a>Events01 Örneği

Bu örnek, kaydetmek kullanıcı tarafından başlatılan olaylara izin veren bir cmdlet oluşturma işlemi gösterilmektedir [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Bu cmdlet ile kullanıcıların altındaki belirli bir dizine bir dosya oluşturulduğunda yürütülecek bir eylem kaydedebilirsiniz.
Bu örnek türetildiği [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) temel sınıfı.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Visual Studio kullanarak örneği oluşturmak nasıl.

1. Windows PowerShell 2.0 yüklü SDK ile Events01 klasöre gidin.
   Varsayılan konum `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Çözüm (.sln) dosyasını simgesini çift tıklatın.
   Bu örnek projeyi Microsoft Visual Studio'da açılır.

3. İçinde **derleme** menüsünde **Çözümü Derle**.
   Kitaplık örneği için varsayılan olarak oluşturulacak `\bin` veya `\bin\debug` klasörleri.

### <a name="how-to-run-the-sample"></a>Örneği çalıştırma

1. Aşağıdaki modül klasörü oluşturun:

    `[user]/documents/windowspowershell/modules/events01`

2. Kitaplık dosyası örneği için modül klasöre kopyalayın.

3. Windows PowerShell’i başlatın.

4. Windows PowerShell'de cmdlet yüklemek için aşağıdaki komutu çalıştırın:

    ```powershell
    import-module events01
    ```

5. TEMP dizininde bir dosya oluşturulduğunda bir ileti yazar bir eylem kaydetmek için kayıt FileSystemEvent cmdlet'ini kullanın.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. TEMP dizini altında bir dosya oluşturun ve eylem yürütülmeden unutmayın (ileti görüntülenir).

Aşağıdaki adımları izleyerek sonuçları bir örnek çıktı budur.

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

Bu örnek, Windows PowerShell 2.0 gerektirir.

## <a name="demonstrates"></a>Gösteriler

Bu örnek aşağıdaki gösterir.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Bir cmdlet için etkinlik kaydı yazma

Cmdlet türetildiği [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) ortak parametreleri için destek sağlar sınıfını `Register-*Event` cmdlet'leri.
Öğesinden türetilen cmdlet'leri [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) yalnızca belirli parametrelerini tanımlayın ve yok saymak gereken `GetSourceObject` ve `GetSourceObjectEventName` soyut yöntemler.

## <a name="example"></a>Örnek

Bu örnek tarafından oluşturulan olaylar için kaydettirmek gösterilmektedir [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](writing-a-windows-powershell-cmdlet.md)