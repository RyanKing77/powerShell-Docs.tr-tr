---
title: Geçersiz kılma yöntemleri işleme giriş | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056405"
---
# <a name="how-to-override-input-processing-methods"></a>Giriş İşleme Yöntemlerini Geçersiz Kılma

Bu örnekler, bir cmdlet yöntemlerinde işleme giriş üzerine gösterilmektedir. Bu yöntemleri aşağıdaki işlemleri gerçekleştirmek için kullanılır:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi, cmdlet tarafından işlenen tüm nesneleri için geçerli olan tek seferlik başlatma işlemlerini gerçekleştirmek için kullanılır. Windows PowerShell çalışma zamanı bu yöntemi yalnızca bir defa çağırır.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi cmdlet'e geçirilen nesneleri işlemek için kullanılır. Windows PowerShell çalışma zamanı, cmdlet'e geçirilen her nesne için bu yöntemi çağırır.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi, tek seferlik post işlemleri gerçekleştirmek için kullanılır. Windows PowerShell çalışma zamanı bu yöntemi yalnızca bir defa çağırır.

## <a name="to-override-the-beginprocessing-method"></a>BeginProcessing yöntemi geçersiz kılmak için

- Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi.

Aşağıdaki sınıftan bir örnek ileti yazdırır. Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>ProcessRecord yöntemi geçersiz kılmak için

- Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.

Aşağıdaki sınıftan bir örnek ileti yazdırır. Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>EndProcessing yöntemi geçersiz kılmak için

- Korumalı bir geçersiz kılma bildirmek [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.

Aşağıdaki sınıftan bir örnek yazdırır. Bu sınıf kullanmak için fiil ve isim cmdlet'i özniteliğinde, yeni fiil ve isim yansıtmak için sınıfın adını değiştirmek ve ihtiyaç duyduğunuz işlevsellik için geçersiz kılmasını eklersiniz [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
