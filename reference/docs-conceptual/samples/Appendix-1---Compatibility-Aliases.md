---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ek 1 Uyumluluk Takma Adları
ms.assetid: 96ad921e-1a57-463e-8e60-424faf8b6ef8
ms.openlocfilehash: 113bbee1af185f98777df5767022d54accb69447
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406007"
---
# <a name="appendix-1---compatibility-aliases"></a>Ek 1 - uyumluluk takma adları

Windows PowerShell, Windows PowerShell'de tanıdık komut adlarını kullanmak UNIX ve Cmd kullanıcıların çeşitli geçiş diğer adları vardır. En sık kullanılan diğer adlar diğer adı ve varsa, standart Windows PowerShell diğer Windows PowerShell komutu ile birlikte, aşağıdaki tabloda gösterilmektedir.

Başka bir ad alanından içinde Windows PowerShell Get-diğer ad cmdlet'ini kullanarak işaret eden Windows PowerShell komutunu bulabilirsiniz. Örneğin **get-diğer ad cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD komut|UNIX komutu|PS Komut|PS Diğer adı|
|---------------|----------------|--------------|------------|
|**dizini**|**Ls**|**Get-Childıtem**|**gcı**|
|**CLS**|**Temizle**|**Clear-Host** (işlev)|**CLS**|
|**DEL, Sil, rmdir**|**RM**|**Remove öğesi**|**RI**|
|**Kopyalama**|**CP**|**Öğeyi Kopyala**|**CI**|
|**taşıma**|**MV**|**Öğe Taşı**|**mı**|
|**Yeniden adlandırma**|**MV**|**Öğeyi yeniden adlandır**|**rni**|
|**Türü**|**cat**|**Get-içerik**|**GC**|
|**CD**|**CD**|**Konum ayarlama**|**SL**|
|**MD**|**mkdir**|**Yeni öğe**|**nı**|
|**pushd**|**pushd**|**Anında iletme konumu**|**pushd**|
|**popd**|**popd**|**POP konumu**|**popd**|