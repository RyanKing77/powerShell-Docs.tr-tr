---
title: Görüntülenen verileri biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065674"
---
# <a name="formatting-displayed-data"></a>Görüntülenen Verileri Biçimlendirme

Tek tek veri noktalarının listesi, tablo veya geniş görünüm nasıl görüntüleneceğini belirtebilirsiniz. Kullanabileceğiniz `FormatString` görünümünüzü veya öğelerin tanımlarken öğesi kullanabilir `ScriptBlock` çağrılacak öğesi `FormatString` veri çubuğunda yöntemi.

## <a name="using-the-formatstring-element"></a>FormatString öğesini kullanarak

Değer aşağıdaki örnekte, `TotalProcessorTime` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne FormatString öğesi kullanılarak biçimlendirildiğinde. `TotalProcessorTime` Özelliği

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



