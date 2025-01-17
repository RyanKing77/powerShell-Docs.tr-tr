---
title: RunSpace03 (VB.NET) kod örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3611d66b-19da-4477-ac05-2e5e68312f51
caps.latest.revision: 6
ms.openlocfilehash: 0931fe7a606b09475084203eaf9fa263ea1cd5f8
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848007"
---
# <a name="runspace03-vbnet-code-sample"></a>RunSpace03 (VB.NET) Kod Örneği

Aşağıda, "belirtilen betiği çalıştıran bir konsol uygulaması oluşturma" bölümünde açıklanan konsol uygulaması için VB.NET kaynak kodu verilmiştir. Bu örnek, Betiğe geçirilen işlem adlarının listesi için işlem bilgilerini alan bir betiği yürütmek üzere [System. Management. Automation. Runspaceınvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) sınıfını kullanır. Giriş nesnelerinin bir betiğe nasıl geçirileceğini ve hata nesnelerinin yanı sıra çıkış nesnelerinin nasıl alınacağını gösterir.

> [!NOTE]
> Windows Vista ve Microsoft .NET Framework 3,0 çalışma zamanı bileşenleri için Windows yazılım geliştirme seti 'ni kullanarak bu örnek için VB.NET kaynak dosyasını (runspace03. vb) indirebilirsiniz. İndirme yönergeleri için bkz. [Windows PowerShell 'ı yükleme ve Windows PowerShell SDK 'Sını indirme](/powershell/developer/installing-the-windows-powershell-sdk).
> İndirilen kaynak dosyaları,  **\<PowerShell örnekleri >** dizininde bulunur.

## <a name="code-sample"></a>Kod örneği

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace03

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script that retrieves process information for the
        ''' list of process names passed into the script.
        ''' It shows how to pass input objects to a script and
        ''' how to retrieve error objects as well as the output objects.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that were generated
        '''    during the execution of that script.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of processes to look for
            Dim processNames() As String = {"lsass", "nosuchprocess", _
                "services", "nosuchprocess2"}

            ' The script to run to get these processes. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | get-process -name {$_}"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            Dim errors As System.Collections.IList = Nothing
            Dim result As PSObject
            For Each result In invoker.Invoke(script, processNames, errors)
                Console.WriteLine("{0,-20} {1}", _
                result.Members("ProcessName").Value, _
                result.Members("HandleCount").Value)
            Next result

            ' Now process any error records that were generated while
            ' running the script.
            Console.WriteLine(vbCrLf & _
                "The following non-terminating errors occurred:" & vbCrLf)
            If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                Dim err As PSObject
                For Each err In errors
                    System.Console.WriteLine("    error: {0}", err.ToString())
                Next err
            End If
            System.Console.WriteLine(vbCRLF & "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main

    End Class 'Runspace03

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace03.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace03.vb#L09-L83 "Runspace03.vb")] -->

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK 'Sı](../windows-powershell-reference.md)