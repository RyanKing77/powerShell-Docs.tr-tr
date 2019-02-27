---
title: Cmdlet kod öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845265"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet Kodunda Öznitelikler

Windows PowerShell tarafından sağlanan ortak işlevselliği kullanmak için cmdlet kod içinde tanımlanan ortak özellikler ve sınıfların öznitelikleri ile donatılmış. Örneğin, aşağıdaki sınıf tanımını Microsoft .NET Framework sınıfında tanımlamak için Cmdlet özniteliğini kullanır **Get-Proc** cmdlet'i uygulanır. (Bu cmdlet, bu belgedeki bir örnek olarak kullanılır ve benzer `Get-Process` cmdlet'inin Windows PowerShell tarafından sağlanan.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Bu öznitelikler, geliştirdikleri cmdlet kod uygulamadan ayrı olduğundan meta veriler olarak kabul edilir. Çalışma zamanı Windows PowerShell cmdlet çalıştırıldığında, öznitelikleri algılar ve ardından her öznitelik için uygun eylemi gerçekleştirir.

Kendi sürümü bu öznitelikler tarafından sağlanan işlevselliği uygulamak isteyebilirsiniz ancak bu ortak işlevler iyi cmdlet'i tasarım kullanılır.

Cmdlet'lerinizi içinde bildirilebilir farklı öznitelikleri hakkında daha fazla bilgi için bkz. [öznitelik türlerini](./attribute-types.md).

## <a name="see-also"></a>Ayrıca bkz:

[Öznitelik türleri](./attribute-types.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
