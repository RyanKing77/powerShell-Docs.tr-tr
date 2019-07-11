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
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734920"
---
# <a name="runspace08-code-sample"></a>RunSpace08 Kod Örneği

İşte kaynak kodunu Runspace08 örnek bölümünde açıklanan yönelik [bir konsol uygulaması, ekler parametreleri için bir komut oluşturma](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Bu örnek uygulama bir çalışma alanı oluşturur, bir işlem hattı oluşturur, ardışık iki komut ekler, iki parametre ikinci komuta ekler ve sonra işlem hattını yürütür. Ardışık düzenine eklenen komutlar `Get-Process` ve `Sort-Object` cmdlet'leri.

## <a name="code-sample"></a>Kod örneği

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)