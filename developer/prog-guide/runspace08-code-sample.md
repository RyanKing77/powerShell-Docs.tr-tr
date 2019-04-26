---
title: Örnek kod RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081283"
---
# <a name="runspace08-code-sample"></a>RunSpace08 Kod Örneği

İşte kaynak kodunu Runspace08 örnek bölümünde açıklanan yönelik [bir konsol uygulaması, ekler parametreleri için bir komut oluşturma](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Bu örnek uygulama bir çalışma alanı oluşturur, bir işlem hattı oluşturur, ardışık iki komut ekler, iki parametre ikinci komuta ekler ve sonra işlem hattını yürütür. Ardışık düzenine eklenen komutlar `Get-Process` ve `Sort-Object` cmdlet'leri.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)