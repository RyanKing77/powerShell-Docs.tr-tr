---
title: Cmdlet yöntemleri işleme giriş | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794952"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet Giriş İşleme Yöntemleri

Cmdlet'leri bir veya daha fazla işleme işlerini yapmak için bu konuda açıklanan yöntemlerden giriş geçersiz kılması gerekir. Bu yöntemler, ön işleme işlemleri, giriş işleme ve sonrası işleme gerçekleştirmek cmdlet sağlar. Bu yöntemleri Ayrıca, cmdlet işlemeyi durdur olanak tanır.

## <a name="pre-processing-tasks"></a>Ön işleme görevleri

Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) cmdlet tarafından işlenen daha sonra tüm kayıtlar için geçerli olan herhangi bir ön işleme işlemi eklemek için yöntemi. Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır. Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) yöntemi.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md). Bu öğreticide **seçin Str** cmdlet'ini kullanır [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) kayıtları işleme giriş aramak için kullanılan normal ifade oluşturmak için yöntemi.

## <a name="input-processing-tasks"></a>Giriş işleme görevleri

Cmdlet'leri geçersiz kılma [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) cmdlet'e gönderilen girişi işlemek için yöntemi. Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell cmdlet tarafından işlenen her giriş kaydı için bu yöntemi çağırır. Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>İşlem Sonrası görevler

Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) cmdlet tarafından işlenen tüm kayıtlar için geçerli olan herhangi bir işlem sonrası işlemi eklemek için yöntemi. Örneğin, nesne değişkenleri bittikten sonra temizleme cmdlet'inize olabilir işleme.

Windows PowerShell komut işlem hattı işlediğinde, Windows PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır. Ancak, Windows PowerShell çalışma zamanı olmayan çağrı unutmamak gerekir [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) yöntemi cmdlet midway, giriş işleme üzerinden iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir. Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) desen, bir sonlandırıcı dahil olmak üzere çalışma zamanı, her ikisi de çağırabilirsiniz [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) ve [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri. Nasıl Windows PowerShell komut işlem hattını çağıran hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

Aşağıdaki kod uygulanışı gösterilmektedir [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Nasıl kullanılacağı hakkında daha ayrıntılı bir örnek için [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty Fullname =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) yöntemi bkz [SelectStr öğretici](./selectstr-tutorial.md).

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty tam adı =](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty tam adı =](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty tam adı =](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
