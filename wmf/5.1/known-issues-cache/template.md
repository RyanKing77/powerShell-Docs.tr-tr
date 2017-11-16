---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: "Örnek şablon bilinen bir sorun veya sınırlaması raporu"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
>Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama girin

## <a name="example-erroneous-executionpolicy-errors"></a>Örnek: Hatalı ExecutionPolicy hataları ##
Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.

### <a name="resolution"></a>Çözüm

Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:

```powershell
Set-ExecutionPolicy RemoteSigned
```

