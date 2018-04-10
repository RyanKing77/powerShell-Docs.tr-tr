---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ek 1 Uyumluluk Takma Adları
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
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
|**dir**|**Ls**|**Get-ChildItem**|**gci**|
|**cls**|**Temizle**|**Clear-Host** (işlev)|**cls**|
|**del, erase, rmdir**|**rm**|**Remove-Item**|**ri**|
|**Kopyalama**|**cp**|**Öğeyi Kopyala**|**ci**|
|**move**|**mv**|**Move-Item**|**mi**|
|**Yeniden Adlandır**|**mv**|**Öğe yeniden adlandırılamadı**|**rni**|
|**Türü**|**cat**|**Get-Content**|**gc**|
|**cd**|**cd**|**Konum ayarlama**|**sl**|
|**md**|**mkdir**|**Yeni öğe**|**ni**|
|**pushd**|**pushd**|**Anında iletme konumu**|**pushd**|
|**popd**|**popd**|**POP konumu**|**popd**|