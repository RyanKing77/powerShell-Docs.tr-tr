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
# <a name="events01-sample"></a><span data-ttu-id="e6c35-102">Events01 Örneği</span><span class="sxs-lookup"><span data-stu-id="e6c35-102">Events01 Sample</span></span>

<span data-ttu-id="e6c35-103">Bu örnek, kaydetmek kullanıcı tarafından başlatılan olaylara izin veren bir cmdlet oluşturma işlemi gösterilmektedir [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="e6c35-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="e6c35-104">Bu cmdlet ile kullanıcıların altındaki belirli bir dizine bir dosya oluşturulduğunda yürütülecek bir eylem kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6c35-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="e6c35-105">Bu örnek türetildiği [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e6c35-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="e6c35-106">Visual Studio kullanarak örneği oluşturmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="e6c35-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="e6c35-107">Windows PowerShell 2.0 yüklü SDK ile Events01 klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="e6c35-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="e6c35-108">Varsayılan konum `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="e6c35-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="e6c35-109">Çözüm (.sln) dosyasını simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e6c35-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="e6c35-110">Bu örnek projeyi Microsoft Visual Studio'da açılır.</span><span class="sxs-lookup"><span data-stu-id="e6c35-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="e6c35-111">İçinde **derleme** menüsünde **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="e6c35-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="e6c35-112">Kitaplık örneği için varsayılan olarak oluşturulacak `\bin` veya `\bin\debug` klasörleri.</span><span class="sxs-lookup"><span data-stu-id="e6c35-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="e6c35-113">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e6c35-113">How to run the sample</span></span>

1. <span data-ttu-id="e6c35-114">Aşağıdaki modül klasörü oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e6c35-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="e6c35-115">Kitaplık dosyası örneği için modül klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e6c35-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="e6c35-116">Windows PowerShell’i başlatın.</span><span class="sxs-lookup"><span data-stu-id="e6c35-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="e6c35-117">Windows PowerShell'de cmdlet yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e6c35-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="e6c35-118">TEMP dizininde bir dosya oluşturulduğunda bir ileti yazar bir eylem kaydetmek için kayıt FileSystemEvent cmdlet'ini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6c35-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="e6c35-119">TEMP dizini altında bir dosya oluşturun ve eylem yürütülmeden unutmayın (ileti görüntülenir).</span><span class="sxs-lookup"><span data-stu-id="e6c35-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="e6c35-120">Aşağıdaki adımları izleyerek sonuçları bir örnek çıktı budur.</span><span class="sxs-lookup"><span data-stu-id="e6c35-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="e6c35-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6c35-121">Requirements</span></span>

<span data-ttu-id="e6c35-122">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e6c35-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e6c35-123">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e6c35-123">Demonstrates</span></span>

<span data-ttu-id="e6c35-124">Bu örnek aşağıdaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6c35-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="e6c35-125">Bir cmdlet için etkinlik kaydı yazma</span><span class="sxs-lookup"><span data-stu-id="e6c35-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="e6c35-126">Cmdlet türetildiği [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) ortak parametreleri için destek sağlar sınıfını `Register-*Event` cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="e6c35-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="e6c35-127">Öğesinden türetilen cmdlet'leri [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) yalnızca belirli parametrelerini tanımlayın ve yok saymak gereken `GetSourceObject` ve `GetSourceObjectEventName` soyut yöntemler.</span><span class="sxs-lookup"><span data-stu-id="e6c35-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="e6c35-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6c35-128">Example</span></span>

<span data-ttu-id="e6c35-129">Bu örnek tarafından oluşturulan olaylar için kaydettirmek gösterilmektedir [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="e6c35-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e6c35-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e6c35-130">See Also</span></span>

[<span data-ttu-id="e6c35-131">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="e6c35-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)