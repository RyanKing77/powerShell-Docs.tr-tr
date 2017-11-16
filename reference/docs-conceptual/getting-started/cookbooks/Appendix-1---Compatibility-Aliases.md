---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Ek 1 uyumluluk diğer adlar"
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: d789139ef80d4208b56e0b2930f04f824a00537d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="appendix-1---compatibility-aliases"></a>Ek 1 - uyumluluk diğer adlar
Windows PowerShell UNIX ve Cmd kullanıcıların Windows PowerShell'de tanıdık komut adları kullanmasına izin birkaç geçiş diğer adları var. En yaygın diğer adlar diğer adı ve varsa, standart bir Windows PowerShell diğer arkasındaki Windows PowerShell komutunu yanı sıra, aşağıdaki tabloda gösterilmektedir.

Herhangi bir diğer adla gelen Windows PowerShell içinde Get-diğer cmdlet'ini kullanarak işaret Windows PowerShell komutunu bulabilirsiniz. Örneğin, **get-diğer adı cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD komutu|UNIX komutu|PS Komutu|PS Diğer adı|
|---------------|----------------|--------------|------------|
|**dir**|**ls**|**Get-Childıtem**|**gcı**|
|**CLS**|**Temizle**|**Clear-Host** (işlev)|**CLS**|
|**DEL, silme, rmdir**|**RM**|**Remove öğesi**|**RI**|
|**kopyalama**|**CP**|**Öğeyi Kopyala**|**CI**|
|**taşıma**|**MV**|**Taşıma öğesi**|**mı**|
|**Yeniden Adlandır**|**MV**|**Öğe yeniden adlandırılamadı**|**rni**|
|**türü**|**Kat**|**Get-içerik**|**GC**|
|**CD**|**CD**|**Konum ayarlama**|**SL**|
|**MD**|**mkdir**|**Yeni öğe**|**nı**|
|**pushd**|**pushd**|**Anında iletme konumu**|**pushd**|
|**popd**|**popd**|**POP konumu**|**popd**|

