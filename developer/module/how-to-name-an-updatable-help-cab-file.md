---
title: Nasıl bir güncelleştirilebilir Yardımı CAB dosyası adı | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082371"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma

Bu konu, güncelleştirilebilir Yardımı dolap gerekli ad biçimini açıklar (. CAB) dosyası.

## <a name="how-to-name-an-updatable-help-cab-file"></a>Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma

Güncelleştirilebilir bir dolap (. CAB) dosyası aşağıdaki biçimde bir adı olmalıdır.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Öğe adı aşağıdaki gibidir.

ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.

ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.

Yardım dosyaları CAB dosyasındaki UICulture UI kültür. Bu değer bir değerle eşleşmelidir **UICulture** modülü için HelpInfo XML dosyasındaki öğeleri.

Örneğin, modül adı "TestModule" ise, ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, ve UI kültürü "en-US" ise, CAB dosyasının adı olacaktır:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`