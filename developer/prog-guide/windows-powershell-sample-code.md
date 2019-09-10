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
ms.openlocfilehash: e9df44b17453e9f73f6eb388d9cbc8a69fce4ba2
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848003"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell Örnek Kod

Windows PowerShell® örnekleri Windows SDK üzerinden kullanılabilir. Bu bölüm Windows SDK örneklerde bulunan örnek kodu içerir.

> [!NOTE]
> Windows SDK yüklendiğinde, tüm Windows PowerShell örneklerinin kullanılabilir hale getirilme **örnekleri** dizini oluşturulur. Tipik bir yükleme dizini **C:\Program Files\Microsoft SDKs\Windows\v6.0**' dir.
> Windows PowerShell örnekleri dizinini bulmak için Windows PowerShell 'i başlatın ve **"CD Samples\SysMgmt\PowerShell"** yazın. Bu belgede, Windows PowerShell örnekleri dizinine  **\<> PowerShell örnekleri**denir.

## <a name="sample-code-listing"></a>Örnek kod listesi

|Örnek Kod|Açıklama|
|-----------------|-----------------|
|[AccessDbProviderSample01 kod örneği](./accessdbprovidersample01-code-sample.md)|Bu, [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[AccessDbProviderSample02 kod örneği](./accessdbprovidersample02-code-sample.md)|Bu, [Windows PowerShell sürücü sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[AccessDbProviderSample03 kod örneği](./accessdbprovidersample03-code-sample.md)|Bu, [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[AccessDbProviderSample04 kod örneği](./accessdbprovidersample04-code-sample.md)|Bu, [bir Windows PowerShell kapsayıcı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[AccessDbProviderSample05 kod örneği](./accessdbprovidersample05-code-sample.md)|Bu, [Windows PowerShell gezinti sağlayıcısı oluşturma](./creating-a-windows-powershell-navigation-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[AccessDbProviderSample06 kod örneği](./accessdbprovidersample06-code-sample.md)|Bu, [Windows PowerShell Içerik sağlayıcısı oluşturma](./creating-a-windows-powershell-content-provider.md)bölümünde açıklanan sağlayıcıdır.|
|[GetProc01 kod örnekleri](./getproc01-code-samples.md)|Bu, `Get-Process` [ilk cmdlet dosyanızı oluşturma](../cmdlet/creating-a-cmdlet-without-parameters.md)bölümünde açıklanan temel cmdlet örneğidir.|
|[GetProc02 kod örnekleri](./getproc02-code-samples.md)|Bu, [komut satırı girişini işleyen parametreler ekleme](../cmdlet/adding-parameters-that-process-command-line-input.md)bölümünde açıklanan cmdletörneğidir.`Get-Process`|
|[GetProc03 kod örnekleri](./getproc03-code-samples.md)|Bu, `Get-Process` [işlem hattı girişini işleyen parametreler ekleme](../cmdlet/adding-parameters-that-process-pipeline-input.md)bölümünde açıklanan cmdlet örneğidir.|
|[GetProc04 kod örnekleri](./getproc04-code-samples.md)|Bu, [cmdlet 'lerinize Sonlandırıcı olmayan hata raporlaması ekleme](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)bölümünde açıklanan cmdletörneğidir.`Get-Process`|
|[GetProc05 kod örnekleri](./getproc05-code-samples.md)|Bu `Get-Process` cmdlet, [cmdlet 'lerinize Sonlandırıcı olmayan hata raporlaması ekleme](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)bölümünde açıklanan cmdlet 'e benzer.|
|[StopProc01 kod örnekleri](./stopproc01-code-samples.md)|Bu, [sistemi değiştiren bir cmdlet oluşturma](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md)bölümünde açıklanan cmdletörneğidir.`Stop-Process`|
|[StopProcessSample04 kod örnekleri](./stopprocesssample04-code-samples.md)|Bu, [bir cmdlet 'e parametre kümeleri ekleme](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)bölümünde açıklanan cmdletörneğidir.`Stop-Process`|
|[Runspace01 kod örnekleri](./runspace01-code-samples.md)|Bunlar, [belirtilen komutu çalıştıran bir konsol uygulaması oluşturma](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)bölümünde açıklanan çalışma için kod örnekleridir.|
|[Runspace02 kod örnekleri](./runspace02-code-samples.md)|Bu örnek, `Get-Process` cmdlet 'i eşzamanlı olarak yürütmek için [System. Management. Automation. runspaceınvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) sınıfını kullanır.|
|[RunSpace03 kod örnekleri](./runspace03-code-samples.md)|Bunlar, "belirtilen betiği çalıştıran bir konsol uygulaması oluşturma" bölümünde açıklanan çalışma alanı için kod örnekleridir.|
|[RunSpace04 kod örnekleri](./runspace04-code-samples.md)|Bu, sonlandırma hatası üreten bir betiği yürütmek için [System. Management. Automation. Runspaceınvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) sınıfını kullanan bir çalışma alanı için bir kod örneğidir.|
|[RunSpace05 kod örneği](./runspace05-code-sample.md)|Bu, [RunspaceConfiguration kullanarak bir runspace yapılandırma](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)bölümünde açıklanan Runspace05 örneği için kaynak kodudur.|
|[RunSpace06 kod örneği](./runspace06-code-sample.md)|Bu, [bir Windows PowerShell ek bileşenini kullanarak bir runspace yapılandırma](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)bölümünde açıklanan Runspace06 örneği için kaynak kodudur.|
|[RunSpace07 kod örneği](./runspace07-code-sample.md)|Bu, bir işlem hattına [Komutlar ekleyen bir konsol uygulaması oluşturma](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)bölümünde açıklanan Runspace07 örneği için kaynak kodudur.|
|[RunSpace08 kod örneği](./runspace08-code-sample.md)|Bu, [bir komuta parametreler ekleyen bir konsol uygulaması oluşturma](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)bölümünde açıklanan Runspace08 örneği için kaynak kodudur.|
|[RunSpace09 kod örneği](./runspace09-code-sample.md)|Bu, işlem hattını [zaman uyumsuz olarak çağıran bir konsol uygulaması oluşturma](https://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)bölümünde açıklanan Runspace09 örneği için kaynak kodudur.|
|[RunSpace10 kod örneği](./runspace10-code-sample.md)|Bu, [System. Management. Automation. Runspaces. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) öğesine bir cmdlet ekleyen ve ardından runspace oluşturmak için değiştirilen yapılandırma bilgilerini kullanan Runspace10 örneği için kaynak kodudur.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK 'Sı](../windows-powershell-reference.md)