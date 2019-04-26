---
title: Açıklama tabanlı Yardım işlevlerde yerleştirme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083204"
---
# <a name="placing-comment-based-help-in-functions"></a>İşlevlere Yorum Tabanlı Yardım Yerleştirme

Bu konuda, bir işlev için açıklama tabanlı Yardım yerleştirileceği yeri açıklanmaktadır. böylece `Get-Help` cmdlet'i açıklama tabanlı Yardım konusunu doğru işlevi ile ilişkilendirir.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Bir işlev için açıklama tabanlı Yardım yerleştirileceği yeri

- İşlev gövdesi başında.

- İşlev gövdesi sonunda.

- Önce `Function` anahtar sözcüğü. İşlev bir betik veya betik modülü olduğunda olamaz birden çok boş satırı açıklama tabanlı Yardım son satırının arasında ve `Function` anahtar sözcüğü. Aksi takdirde, `Get-Help` Yardım betiğiyle, işlev olmayan ile ilişkilendirir.

## <a name="examples-of-help-placement-in-a-function"></a>Bir işlevde Yardım yerleştirme örnekleri

 Aşağıdaki örnekler, her bir işlev için açıklama tabanlı Yardım üç yerleştirme seçeneklerini gösterir.

### <a name="help-at-the-beginning-of-a-function-body"></a>Bir işlev gövdesinin başında Yardım

 Aşağıdaki örnek, açıklama tabanlı bir işlev gövdesinin başında gösterir.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Bir işlev gövdesinin sonunda Yardım

 Aşağıdaki örnek, açıklama tabanlı bir işlev gövdesinin sonunda gösterir.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Önce Function anahtar Yardım

 Aşağıdaki örnekler gösterilmektedir function anahtar sözcüğünü önce satırda açıklama tabanlı.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```