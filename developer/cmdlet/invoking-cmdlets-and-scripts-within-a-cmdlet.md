---
title: Cmdlet'leri ve komut dosyalarını içinde bir Cmdlet yürütmesini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846245"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Bir Cmdlet’te Cmdlet ve Betikleri Çağırma

Bir cmdlet diğer cmdlet'ler ve işleme yöntemi cmdlet'inin girdideki betiklerin çağırabilirsiniz. Bu, yeniden kod yazmak zorunda kalmadan, cmdlet'e mevcut cmdlet'leri ve betikleri işlevselliğini eklemenizi sağlar.

## <a name="the-invoke-method"></a>Invoke yöntemi

Var olan bir cmdlet'i çağırarak tüm cmdlet'ler çağırabilirsiniz [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) yönteminden yöntemi gibi işleme giriş içinde [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), diğer bir deyişle cmdlet'i tarafından geçersiz kılındı. Ancak, doğrudan öğesinden türetilen cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı. Türetilen bir cmdlet çağrılamıyor [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı.

[System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) yöntemi aşağıdaki çeşitler sahiptir.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Bu cmdlet nesnesini başlatır ve "T" türü nesnelerinin bir koleksiyonunu döndürür.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Bu cmdlet nesnesini başlatır ve kesin türü belirtilmiş emumerator döndürür. Bu değişken, nesneleri koleksiyonda özel işlemler gerçekleştirmek için kullanılacak kullanıcı sağlar.

## <a name="examples"></a>Örnekler

|Örnek|Açıklama|
|-------------|-----------------|
|[Bir Cmdlet cmdlet'lerin çağırma](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Bu örnekte, başka bir cmdlet içinde cmdlet'inden çağrılacak gösterilmektedir.|
|[Bir Cmdlet içinde betikleri çağırma](./how-to-invoke-scripts-within-a-cmdlet.md)|Bu örnek cmdlet'in içinde başka bir cmdlet için sağlanan bir betik çağırmak nasıl gösterir.|

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
