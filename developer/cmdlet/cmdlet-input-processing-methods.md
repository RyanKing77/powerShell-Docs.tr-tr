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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068496"
---
# <a name="cmdlet-input-processing-methods"></a>Cmdlet Giriş İşleme Yöntemleri

Cmdlet'leri bir veya daha fazla işleme işlerini yapmak için bu konuda açıklanan yöntemlerden giriş geçersiz kılması gerekir.
Bu yöntemler, ön işleme, giriş işleme ve sonrası işleme işlemlerini gerçekleştirmek cmdlet sağlar.
Bu yöntemleri Ayrıca, cmdlet işlemeyi durdur olanak tanır.
Bu yöntemleri kullanma hakkında daha ayrıntılı örnek için bkz [SelectStr öğretici](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Ön işleme işlemleri

Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) cmdlet tarafından işlenen daha sonra tüm kayıtlar için geçerli olan herhangi bir ön işleme işlemi eklemek için yöntemi.
PowerShell komut işlem hattı işlediğinde, PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.
PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).

Aşağıdaki kod, BeginProcessing yöntemi uygulanışı gösterilmektedir.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>İşleme giriş

Cmdlet'leri geçersiz kılma [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet'e gönderilen girişi işlemek için yöntemi.
PowerShell komut işlem hattı işlediğinde, PowerShell cmdlet tarafından işlenen her giriş kaydı için bu yöntemi çağırır.
PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).

Aşağıdaki kod, ProcessRecord yöntemi uygulanışı gösterilmektedir.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>İşlem Sonrası işlemleri

Cmdlet'leri geçersiz kılmalıdır [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet tarafından işlenen tüm kayıtlar için geçerli olan herhangi bir işlem sonrası işlemi eklemek için yöntemi.
Örneğin, nesne değişkenleri bittikten sonra temizleme cmdlet'inize olabilir işleme.

PowerShell komut işlem hattı işlediğinde, PowerShell Bu yöntem işlem hattındaki cmdlet'inin her örneği için bir kez çağırır.
Bununla birlikte, PowerShell çalışma zamanı EndProcessing yöntemi cmdlet midway kendi giriş işlemeden iptal edilirse veya herhangi bir bölümünü cmdlet'i bir sonlandırmalı hata oluşması durumunda çağırmayacaktır olduğunu unutmamak önemlidir.
Bu nedenle, nesne temizleme gerektiren bir cmdlet tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) desen, bir sonlandırıcı dahil olmak üzere çalışma zamanı, her iki EndProcessing çağırabilirsiniz ve [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri.
PowerShell komut ardışık düzeni nasıl çağırır hakkında daha fazla bilgi için bkz. [cmdlet'i işleme yaşam döngüsü](/previous-versions/ms714429(v=vs.85)).

Aşağıdaki kod, EndProcessing yöntemi uygulanışı gösterilmektedir.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr Öğreticisi](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
