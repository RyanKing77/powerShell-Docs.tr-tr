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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846105"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="9ca1f-102">Görüntülenen Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="9ca1f-102">Formatting Displayed Data</span></span>

<span data-ttu-id="9ca1f-103">Tek tek veri noktalarının listesi, tablo veya geniş görünüm nasıl görüntüleneceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ca1f-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="9ca1f-104">Kullanabileceğiniz `FormatString` görünümünüzü veya öğelerin tanımlarken öğesi kullanabilir `ScriptBlock` çağrılacak öğesi `FormatString` veri çubuğunda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ca1f-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="9ca1f-105">FormatString öğesini kullanarak</span><span class="sxs-lookup"><span data-stu-id="9ca1f-105">Using the FormatString Element</span></span>

<span data-ttu-id="9ca1f-106">Değer aşağıdaki örnekte, `TotalProcessorTime` özelliği [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne FormatString öğesi kullanılarak biçimlendirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="9ca1f-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="9ca1f-107">`TotalProcessorTime` Özelliği</span><span class="sxs-lookup"><span data-stu-id="9ca1f-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```


