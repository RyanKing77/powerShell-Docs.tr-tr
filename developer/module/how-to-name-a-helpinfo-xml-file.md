---
title: Nasıl HelpInfo XML dosya adı | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082405"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML Dosyasını Adlandırma

Bu konu, genellikle HelpInfo XML dosyası olarak bilinen güncelleştirilebilir Yardımı bilgi dosyaları, gerekli ad biçimini açıklar.

## <a name="how-to-name-a-helpinfo-xml-file"></a>HelpInfo XML Dosyasını Adlandırma

HelpInfo XML dosyası aşağıdaki biçimde bir adı olmalıdır.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Öğe adı aşağıdaki gibidir.

ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.

ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.

Örneğin, modül adı "TestModule" ise ve ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 modülü için HelpInfo XML dosyasının adı olacaktır:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`