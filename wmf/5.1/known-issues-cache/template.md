---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: bilinen bir sorun veya sınırlama writeup örnek şablonu
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055556"
---
 >Not: önerilen açıklayıcı bir başlık ve kısa bir açıklama sağlayın.

## <a name="example-erroneous-executionpolicy-errors"></a>Örnek: Hatalı ExecutionPolicy hataları
Windows 7'de PowerShell modülleri ve DSC kaynakları ExecutionPolicy hakkında rapor edilen hata neden olabilir.

### <a name="resolution"></a>Çözüm

Çözmek için ayarlayın **ExecutionPolicy** için **RemoteSigned** (yönetici olarak çalıştır) yükseltilmiş bir PowerShell oturumunda aşağıdaki komutu çalıştırarak:

```powershell
Set-ExecutionPolicy RemoteSigned
```
