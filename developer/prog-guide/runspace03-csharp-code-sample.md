---
title: RunSpace03 (C#) kod örneği | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848034"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) Kod Örneği

"Belirli bir C# betiği çalıştıran bir konsol uygulaması oluşturma" bölümünde açıklanan konsol uygulaması için kaynak kodu aşağıda verilmiştir. Bu örnek, komut dosyasına geçirilen işlem adlarının listesini kullanarak işlem bilgilerini alan bir betiği yürütmek için [System. Management. Automation. Runspaceınvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) sınıfını kullanır. Giriş nesnelerinin bir betiğe nasıl geçirileceğini ve hata nesnelerinin yanı sıra çıkış nesnelerinin nasıl alınacağını gösterir.

> [!NOTE]
> Windows Vista için Microsoft C# Windows yazılım geliştirme seti ve Microsoft .NET Framework 3,0 çalışma zamanı bileşenleri kullanarak bu örnek için kaynak dosyasını (runspace03.cs) indirebilirsiniz. İndirme yönergeleri için bkz. [Windows PowerShell 'ı yükleme ve Windows PowerShell SDK 'Sını indirme](/powershell/developer/installing-the-windows-powershell-sdk).
> İndirilen kaynak dosyaları,  **\<PowerShell örnekleri >** dizininde bulunur.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK 'Sı](../windows-powershell-reference.md)