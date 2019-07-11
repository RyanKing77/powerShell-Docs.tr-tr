---
title: Windows PowerShell örnek kodu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 4154aeb22b5dde7806f3af133559d471e82bb981
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733782"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell Örnek Kod

Windows PowerShell® örnekler Windows SDK aracılığıyla kullanılabilir. Bu bölüm, Windows SDK'sı örnekleri yer alan örnek kod içerir.

> [!NOTE]
> Windows SDK'sı yüklü olduğunda, bir **örnekleri** dizin oluşturuldu, tüm Windows PowerShell örnekleri kullanılabilir hale gelir. Normal Yükleme dizini **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Windows PowerShell ve türü **"cd Samples\SysMgmt\PowerShell"** Windows PowerShell örnekleri dizini bulunamadı. Bu belgede, Windows PowerShell örnekleri directory olarak adlandırılır  **\<PowerShell örnekleri >** .

## <a name="sample-code-listing"></a>Örnek kod listesi

|Örnek Kod|Açıklama|
|-----------------|-----------------|
|[AccessDbProviderSample01 kod örneği](./accessdbprovidersample01-code-sample.md)|Bu açıklanan sağlayıcıdır [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md).|
|[AccessDbProviderSample02 kod örneği](./accessdbprovidersample02-code-sample.md)|Bu açıklanan sağlayıcıdır [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).|
|[AccessDbProviderSample03 kod örneği](./accessdbprovidersample03-code-sample.md)|Bu açıklanan sağlayıcıdır [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).|
|[AccessDbProviderSample04 kod örneği](./accessdbprovidersample04-code-sample.md)|Bu açıklanan sağlayıcıdır [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).|
|[AccessDbProviderSample05 kod örneği](./accessdbprovidersample05-code-sample.md)|Bu açıklanan sağlayıcıdır [bir Windows PowerShell Gezinti sağlayıcı oluşturma](./creating-a-windows-powershell-navigation-provider.md).|
|[AccessDbProviderSample06 kod örneği](./accessdbprovidersample06-code-sample.md)|Bu açıklanan sağlayıcıdır [Windows PowerShell içerik sağlayıcısı oluşturma](./creating-a-windows-powershell-content-provider.md).|
|[GetProc01 kod örnekleri](./getproc01-code-samples.md)|Bu, temel `Get-Process` cmdlet örnek açıklanan [oluşturma bilgisayarınızı ilk Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md).|
|[GetProc02 kod örnekleri](./getproc02-code-samples.md)|Bu `Get-Process` cmdlet örnek açıklanan [parametreler, işlem komut satırı girişi ekleme](../cmdlet/adding-parameters-that-process-command-line-input.md).|
|[GetProc03 kod örnekleri](./getproc03-code-samples.md)|Bu `Get-Process` cmdlet örnek açıklanan [söz konusu işlem ardışık düzen giriş parametreleri ekleme](../cmdlet/adding-parameters-that-process-pipeline-input.md).|
|[GetProc04 kod örnekleri](./getproc04-code-samples.md)|Bu `Get-Process` cmdlet örnek açıklanan [bilgisayarınızı cmdlet'e olmak üzere Sonlandırmasız hata raporlama ekleme](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[GetProc05 kod örnekleri](./getproc05-code-samples.md)|Bu `Get-Process` açıklanan cmdlet'e cmdlet'i benzer [bilgisayarınızı cmdlet'e olmak üzere Sonlandırmasız hata raporlama ekleme](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).|
|[StopProc01 kod örnekleri](./stopproc01-code-samples.md)|Bu `Stop-Process` cmdlet örnek açıklanan [sistemi oluşturma, Cmdlet değiştirir](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).|
|[StopProcessSample04 kod örnekleri](./stopprocesssample04-code-samples.md)|Bu `Stop-Process` cmdlet örnek açıklanan [bir cmdlet'e parametre kümeleri ekleme](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).|
|[Runspace01 kod örnekleri](./runspace01-code-samples.md)|Çalışma alanı açıklanan için kod örnekleri bunlar [belirtilen bir komutu bir konsol uygulaması, çalışır oluşturma](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).|
|[Runspace02 kod örnekleri](./runspace02-code-samples.md)|Bu örnekte [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) yürütmek için sınıf `Get-Process` cmdlet'i zaman uyumlu olarak.|
|[RunSpace03 kod örnekleri](./runspace03-code-samples.md)|Çalışma alanı açıklanan için kod örnekleri bunlar [konsol uygulaması, çalıştırmalar belirtilen kod oluşturma](fd).|
|[RunSpace04 kod örnekleri](./runspace04-code-samples.md)|Bu kullanan bir çalışma alanı için bir kod örneği buradaki [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) bir sonlandırma hatası oluşturur bir betik yürütmek için sınıf.|
|[RunSpace05 kod örneği](./runspace05-code-sample.md)|Kaynak kodu Runspace05 örnek bölümünde açıklanan yönelik budur [kullanarak bir çalışma alanı RunspaceConfiguration yapılandırma](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).|
|[RunSpace06 kod örneği](./runspace06-code-sample.md)|Kaynak kodu Runspace06 örnek bölümünde açıklanan yönelik budur [bir Windows PowerShell ek bileşenini kullanarak bir çalışma alanı yapılandırma](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).|
|[RunSpace07 kod örneği](./runspace07-code-sample.md)|Kaynak kodu Runspace07 örnek bölümünde açıklanan yönelik budur [bir konsol uygulaması olduğunu ekler komutları bir işlem hattı oluşturma](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).|
|[RunSpace08 kod örneği](./runspace08-code-sample.md)|Kaynak kodu Runspace08 örnek bölümünde açıklanan yönelik budur [bir konsol uygulaması, ekler parametreleri için bir komut oluşturma](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).|
|[RunSpace09 kod örneği](./runspace09-code-sample.md)|Kaynak kodu Runspace09 örnek bölümünde açıklanan yönelik budur [bir işlem hattı zaman uyumsuz olarak çağırır bir konsol uygulaması oluşturma](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).|
|[RunSpace10 kod örneği](./runspace10-code-sample.md)|Bu cmdlet'e ekler Runspace10 örneği için kaynak kodu, [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ve sonra çalışma alanı oluşturmak için değiştirilmiş yapılandırma bilgilerini kullanır.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)