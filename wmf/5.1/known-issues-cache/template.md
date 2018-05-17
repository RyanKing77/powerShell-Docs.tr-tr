---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Örnek şablon bilinen bir sorun veya sınırlaması raporu
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
>Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama girin

## <a name="example-erroneous-executionpolicy-errors"></a>Örnek: Hatalı ExecutionPolicy hataları ##
Windows 7, PowerShell modülleri ve DSC kaynakları kullanımı hakkında ExecutionPolicy bildirilen hataları neden olabilir.

### <a name="resolution"></a>Çözüm

Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:

```powershell
Set-ExecutionPolicy RemoteSigned
```
