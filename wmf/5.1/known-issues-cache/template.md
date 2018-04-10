---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Örnek şablon bilinen bir sorun veya sınırlaması raporu
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
>Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama girin

## <a name="example-erroneous-executionpolicy-errors"></a>Örnek: Hatalı ExecutionPolicy hataları ##
Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.

### <a name="resolution"></a>Çözüm

Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:

```powershell
Set-ExecutionPolicy RemoteSigned
```