---
title: Cmdlet diğer adları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849969"
---
# <a name="cmdlet-aliases"></a>Cmdlet Diğer Adları

Cmdlet diğer adlar, cmdlet kullanıcı deneyimini geliştirmek için kullanabilirsiniz. Sık kullanılan cmdlet'leri yazarak azaltmak ve görevleri tamamlamak için hızlı bir şekilde kolaylaştırmak için diğer adları ekleyebilirsiniz. Yerleşik diğer adlar, cmdlet'ler içerebilir veya kullanıcılar, kendi özel diğer adlar tanımlayabilir.

Örneğin, [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet'i sahip yerleşik `gcm` diğer adı. Diğer adlar, böylece kullanıcılar, yeni komutlarını öğrenmeniz gerekmez. diğer dillerde komut adları eklemek için de kullanabilirsiniz.

## <a name="alias-guidelines"></a>Diğer ad kuralları

Yerleşik diğer adlar için cmdlet'lerinizi oluşturduğunuzda aşağıdaki yönergeleri izleyin:

- Diğer adlar atamadan önce Windows PowerShell'i başlatın ve ardından çalıştırın [Get-diğer ad](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) zaten kullanılan diğer adlarını görmek için cmdlet.

- Cmdlet adı ve cmdlet adı isim başvuran bir diğer ad soneki fiili başvuran bir diğer ad ön eki ekleyin. Örneğin, diğer `Import-Module` cmdlet'tir "ipmo". Tüm fiiller ve diğer adlarını listesi için bkz: [Cmdlet fiilleri](./approved-verbs-for-windows-powershell-commands.md).

- Aynı diğer ad ön eki aynı fiili sahip cmdlet'leri içerir. Örneğin, adında "Get" fiili sahip tüm Windows PowerShell cmdlet'leri için diğer adlar, "g" ön ekini kullanın.

- Aynı isim sahip cmdlet'leri, aynı diğer ad soneki içerir. Örneğin, adında "Oturumu" isim sahip tüm Windows PowerShell cmdlet'leri için diğer adlar "sn" soneki kullanın.

- Diğer dillerde komutlar eşdeğerdir cmdlet'leri için komut adını kullanın.

- Genel olarak, diğer adlar olabildiğince kısa yapın. Diğer ad fiil için ayrı en az bir karakter ve isim için farklı bir karakter olduğundan emin olun. Diğer adı benzersiz hale getirmek için gerektiği şekilde daha fazla karakter ekleyin.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
