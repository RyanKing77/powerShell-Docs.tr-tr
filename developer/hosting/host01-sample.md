---
title: Host01 örnek | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fca30b1-13fe-48a2-b0dd-979c161177a6
caps.latest.revision: 14
ms.openlocfilehash: 9a4b7c842c6222fa2e9f1c14f37f45d7a5158107
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082853"
---
# <a name="host01-sample"></a><span data-ttu-id="39026-102">Host01 Örneği</span><span class="sxs-lookup"><span data-stu-id="39026-102">Host01 Sample</span></span>

<span data-ttu-id="39026-103">Bu örnek, özel bir ana bilgisayar kullanan bir konak uygulamanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39026-103">This sample shows how to implement a host application that uses a custom host.</span></span> <span data-ttu-id="39026-104">Özel ana bilgisayarı kullanan bu örnekte bir çalışma alanı oluşturulur ve ardından [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) API "çıkış" çağıran bir betik çalıştırmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="39026-104">In this sample a runspace is created that uses the custom host, and then the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) API is used to run a script that calls "exit."</span></span> <span data-ttu-id="39026-105">Konak uygulama betiği çıktısına arar ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="39026-105">The host application then looks at the output of the script and prints out the results.</span></span>

 <span data-ttu-id="39026-106">Bu örnek, Windows PowerShell tarafından sağlanan varsayılan kullanıcı Arabirimi özellikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="39026-106">This sample uses the default UI features provided by Windows PowerShell.</span></span> <span data-ttu-id="39026-107">Özel bir ana bilgisayar, kullanıcı Arabirimi özelliklerini uygulama hakkında daha fazla bilgi için bkz. [Host02 örnek](./host02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="39026-107">For more information about implementing the UI features of a custom host, see [Host02 Sample](./host02-sample.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="39026-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39026-108">Requirements</span></span>

 <span data-ttu-id="39026-109">Bu örnek, Windows PowerShell 2.0 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="39026-109">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="39026-110">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="39026-110">Demonstrates</span></span>

- <span data-ttu-id="39026-111">Oluşturduğunuz özel konak sınıf türetilir [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="39026-111">Creating a custom host class that derives from the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span>

- <span data-ttu-id="39026-112">Bir çalışma alanı oluşturma, özel ana bilgisayar sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="39026-112">Creating a runspace that uses the custom host class.</span></span>

- <span data-ttu-id="39026-113">Oluşturma bir [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) çıkış çağıran bir betik çalıştıran bir nesne.</span><span class="sxs-lookup"><span data-stu-id="39026-113">Creating a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell) object that runs a script that calls exit.</span></span>

- <span data-ttu-id="39026-114">Doğru çıkış kodu çıkış işleminde kullanılan doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="39026-114">Verifying that the correct exit code was used in the exit process.</span></span>

## <a name="example"></a><span data-ttu-id="39026-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="39026-115">Example</span></span>

 <span data-ttu-id="39026-116">Aşağıdaki kod, basit bir özel konak arabirimini kullanan ana bilgisayar uygulamasına uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39026-116">The following code shows an implementation of a host application that uses a simple custom host interface.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{

    using System;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using PowerShell = System.Management.Automation.PowerShell;

    /// <summary>
    /// This class contains the Main entry point for this host application.
    /// </summary>
    internal class Host01
    {

        /// <summary>
        /// Indicator to tell the host application that it should exit.
        /// </summary>
        private bool shouldExit;

        /// <summary>
        /// The exit code that the host application will use to exit.
        /// </summary>
        private int exitCode;

        /// <summary>
        /// Gets or sets a value indicating whether the
        /// host application should exit.
        /// </summary>
        public bool ShouldExit
        {
            get { return this.shouldExit; }
            set { this.shouldExit = value; }
        }

        /// <summary>
        /// Gets or sets the PSHost implementation that is
        /// used to tell the host application what code to use
        /// when exiting.
        /// </summary>
        public int ExitCode
        {
            get { return this.exitCode; }
            set { this.exitCode = value; }
        }

        /// <summary>
        /// This sample uses a PowerShell object to run
        /// a script that calls exit. The host application looks at
        /// this and prints out the result.
        /// </summary>
        /// <param name="args">Parameter not used.</param>
        private static void Main(string[] args)
        {
            // Create an instance of this host application class so that
            // the Windows PowerShell engine will have access to the
            // ShouldExit and ExitCode parameters.
            Host01 me = new Host01();

            // Create the host instance to use.
            MyHost myHost = new MyHost(me);

            // Create a runspace that uses the host object and run the
            // script using a PowerShell object.
            using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(myHost))
            {
                // Open the runspace.
                myRunSpace.Open();

                // Create a PowerShell object to run the script.
                using (PowerShell powershell = PowerShell.Create())
                {
                    powershell.Runspace = myRunSpace;

                    // Create the pipeline and run the script
                    // "exit (2+2)".
                    string script = "exit (2+2)";
                    powershell.AddScript(script);
                    powershell.Invoke(script);
                }

                // Check the flags and see if they were set propertly.
                Console.WriteLine(
                    "ShouldExit={0} (should be True); ExitCode={1} (should be 4)",
                    me.ShouldExit,
                    me.ExitCode);

                // close the runspace to free resources.
                myRunSpace.Close();
            }

            Console.WriteLine("Hit any key to exit...");
            Console.ReadKey();
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="39026-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="39026-117">Example</span></span>

 <span data-ttu-id="39026-118">Aşağıdaki kod uygulamasıdır [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) bu konak uygulama tarafından kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="39026-118">The following code is the implementation of the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class that is used by this host application.</span></span> <span data-ttu-id="39026-119">Uygulanmaz bu öğeleri bir özel durum veya hiçbir şey döndürmeyen.</span><span class="sxs-lookup"><span data-stu-id="39026-119">Those elements that are not implemented throw an exception or return nothing.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Host
{
    using System;
    using System.Globalization;
    using System.Management.Automation.Host;

    /// <summary>
    /// This is a sample implementation of the PSHost abstract class for
    /// console applications. Not all members are implemented. Those that
    /// are not implemented throw a NotImplementedException exception or
    /// return nothing.
    /// </summary>
    internal class MyHost : PSHost
    {
        /// <summary>
        /// A reference to the PSHost implementation.
        /// </summary>
        private Host01 program;

        /// <summary>
        /// The culture information of the thread that created
        /// this object.
        /// </summary>
        private CultureInfo originalCultureInfo =
            System.Threading.Thread.CurrentThread.CurrentCulture;

        /// <summary>
        /// The UI culture information of the thread that created
        /// this object.
        /// </summary>
        private CultureInfo originalUICultureInfo =
            System.Threading.Thread.CurrentThread.CurrentUICulture;

        /// <summary>
        /// The identifier of this PSHost implementation.
        /// </summary>
        private Guid myId = Guid.NewGuid();

        /// <summary>
        /// Initializes a new instance of the MyHost class. Keep
        /// a reference to the host application object so that it
        /// can be informed of when to exit.
        /// </summary>
        /// <param name="program">
        /// A reference to the host application object.
        /// </param>
        public MyHost(Host01 program)
        {
            this.program = program;
        }

        /// <summary>
        /// Return the culture information to use. This implementation
        /// returns a snapshot of the culture information of the thread
        /// that created this object.
        /// </summary>
        public override System.Globalization.CultureInfo CurrentCulture
        {
            get { return this.originalCultureInfo; }
        }

        /// <summary>
        /// Return the UI culture information to use. This implementation
        /// returns a snapshot of the UI culture information of the thread
        /// that created this object.
        /// </summary>
        public override System.Globalization.CultureInfo CurrentUICulture
        {
            get { return this.originalUICultureInfo; }
        }

        /// <summary>
        /// This implementation always returns the GUID allocated at
        /// instantiation time.
        /// </summary>
        public override Guid InstanceId
        {
            get { return this.myId; }
        }

        /// <summary>
        /// Return a string that contains the name of the host implementation.
        /// Keep in mind that this string may be used by script writers to
        /// identify when your host is being used.
        /// </summary>
        public override string Name
        {
            get { return "MySampleConsoleHostImplementation"; }
        }

        /// <summary>
        /// This sample does not implement a PSHostUserInterface component so
        /// this property simply returns null.
        /// </summary>
        public override PSHostUserInterface UI
        {
            get { return null; }
        }

        /// <summary>
        /// Return the version object for this application. Typically this
        /// should match the version resource in the application.
        /// </summary>
        public override Version Version
        {
            get { return new Version(1, 0, 0, 0); }
        }

        /// <summary>
        /// Not implemented by this example class. The call fails with
        /// a NotImplementedException exception.
        /// </summary>
        public override void EnterNestedPrompt()
        {
            throw new NotImplementedException(
                "The method or operation is not implemented.");
        }

        /// <summary>
        /// Not implemented by this example class. The call fails
        /// with a NotImplementedException exception.
        /// </summary>
        public override void ExitNestedPrompt()
        {
            throw new NotImplementedException(
                "The method or operation is not implemented.");
        }

        /// <summary>
        /// This API is called before an external application process is
        /// started. Typically it is used to save state so the parent can
        /// restore state that has been modified by a child process (after
        /// the child exits). In this example, this functionality is not
        /// needed so the method returns nothing.
        /// </summary>
        public override void NotifyBeginApplication()
        {
            return;
        }

        /// <summary>
        /// This API is called after an external application process finishes.
        /// Typically it is used to restore state that a child process may
        /// have altered. In this example, this functionality is not
        /// needed so the method returns nothing.
        /// </summary>
        public override void NotifyEndApplication()
        {
           return;
        }

        /// <summary>
        /// Indicate to the host application that exit has
        /// been requested. Pass the exit code that the host
        /// application should use when exiting the process.
        /// </summary>
        /// <param name="exitCode">The exit code to use.</param>
        public override void SetShouldExit(int exitCode)
        {
            this.program.ShouldExit = true;
            this.program.ExitCode = exitCode;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="39026-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="39026-120">See Also</span></span>
