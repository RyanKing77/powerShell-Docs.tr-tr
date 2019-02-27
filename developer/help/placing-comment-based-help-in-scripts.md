---
title: Açıklama tabanlı Yardım betiklerde yerleştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850151"
---
# <a name="placing-comment-based-help-in-scripts"></a>Betiklere Yorum Tabanlı Yardım Yerleştirme

Bu konuda, bir komut dosyası için açıklama tabanlı Yardım yerleştirileceği yeri açıklanmaktadır. böylece `Get-Help` cmdlet'i, açıklama tabanlı Yardım konusuna değildir komut dosyasında olabilir herhangi işlevleri ve komut dosyaları ile ilişkilendirir.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Bir komut dosyası için açıklama tabanlı Yardım yerleştirileceği yeri

- Komut dosyasının başında. Betik Yardım betikte yalnızca açıklama ve boş satırları tarafından öncesinde.

- Betiğin sonunda.

  Listedeki ilk öğe (sonra Yardımı) betik gövdesi bir işlev bildirimi ise, işlev bildirimi ile Yardım komut dosyasının sonuna arasındaki en az iki boş satırlar olmalıdır. Aksi takdirde, Yardım işlevi değildir komut için Yardım için Yardım'ı olacak şekilde yorumlanır.

## <a name="examples-of-help-placement-in-a-script"></a>Bir komut dosyası yerleşimden Yardım örnekleri

 Aşağıdaki örnekler, her bir komut dosyası için açıklama tabanlı Yardım yerleştirme seçeneklerini gösterir.

### <a name="help-at-the-beginning-of-a-script"></a>Bir komut dosyasının başında Yardım

 Aşağıdaki örnek, açıklama tabanlı bir komut dosyasının başında gösterir.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Bir betik sonunda Yardım

 Aşağıdaki örnek, açıklama tabanlı bir komut dosyası sonunda gösterir.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```