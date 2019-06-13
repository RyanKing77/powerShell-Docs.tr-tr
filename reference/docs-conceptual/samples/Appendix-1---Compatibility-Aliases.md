---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ek 1 Uyumluluk Takma Adları
ms.openlocfilehash: 553b9f01d6b5e3f4e04f1a75c25979b54dc205da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030334"
---
# <a name="appendix-1---compatibility-aliases"></a>Ek 1 - uyumluluk takma adları

Windows PowerShell, Windows PowerShell'de tanıdık komut adlarını kullanmak UNIX ve Cmd kullanıcıların çeşitli geçiş diğer adları vardır. En sık kullanılan diğer adlar diğer adı ve varsa, standart Windows PowerShell diğer Windows PowerShell komutu ile birlikte, aşağıdaki tabloda gösterilmektedir.

Başka bir ad alanından içinde Windows PowerShell Get-diğer ad cmdlet'ini kullanarak işaret eden Windows PowerShell komutunu bulabilirsiniz. Örneğin **get-diğer ad cls**.

```
CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

|CMD komut|UNIX komutu|PS Command|PS Diğer adı|
|---------------|----------------|--------------|------------|
|**dizini**|**Ls**|**Get-Childıtem**|**gci**|
|**CLS**|**Temizle**|**Clear-Host** (işlev)|**CLS**|
|**DEL, Sil, rmdir**|**RM**|**Remove öğesi**|**RI**|
|**kopyalama**|**CP**|**Öğeyi Kopyala**|**ci**|
|**Taşıma**|**mv**|**Öğe Taşı**|**mı**|
|**Yeniden adlandırma**|**mv**|**Öğeyi yeniden adlandır**|**rni**|
|**type**|**Cat**|**Get-Content**|**GC**|
|**cd**|**cd**|**Konum ayarlama**|**sl**|
|**MD**|**mkdir**|**Yeni öğe**|**nı**|
|**pushd**|**pushd**|**Anında iletme konumu**|**pushd**|
|**popd**|**popd**|**POP konumu**|**popd**|
