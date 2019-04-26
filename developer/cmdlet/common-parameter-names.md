---
title: Genel parametre adları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068448"
---
# <a name="common-parameter-names"></a>Yaygın Parametre Adları

Bu konuda açıklanan parametreler olarak ifade edilir *ortak parametreleri*. Bunlar, cmdlet'leri için Windows PowerShell çalışma zamanı tarafından eklenir ve cmdlet tarafından bildirilemez.

> [!NOTE]
> Bu parametreleri sağlayıcısı cmdlet'leri ve ile donatılmış işlevleri için de eklenir `CmdletBinding` özniteliği.

## <a name="general-common-parameters"></a>Genel ortak Parametreler

Aşağıdaki parametreleri, tüm cmdlet'ler için eklenir ve cmdlet'i her çalıştırıldığında erişilebilir. Bu parametreleri tarafından tanımlanan [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) sınıfı.

### <a name="debug-alias-db"></a>Hata ayıklama (diğer ad: db)

Veri türü: SwitchParameter

Bu parametre, programcı düzeyinde hata ayıklama iletileri olup olmadığını belirtir. komut satırında görüntülenebilir. Bu iletiler cmdlet'inin bir işlemde sorun gidermek için tasarlanmıştır ve yapılan çağrılar tarafından oluşturulan [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi. Hata ayıklama iletileri yerelleştirilmiş gerekmez.

### <a name="erroraction-alias-ea"></a>ErrorAction (diğer ad: ea)

Veri türü: Sabit listesi

Bu parametre, bir hata oluştuğunda ne zaman gerçekleştirileceğini belirtir. Bu parametre için olası değerler tarafından tanımlanan [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) sabit listesi.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (diğer ad: ev)

Veri türü: Dize

Bu parametre, bir hata oluştuğunda nesneleri yerleştirileceği değişkeni belirtir. Bu değişkeni eklemek için kullanın +*varname* değişkeni ayarlama ve temizleme yerine.

### <a name="outvariable-alias-ov"></a>OutVariable (diğer ad: ov)

Veri türü: Dize

Bu parametre hangi yerleştirmek tüm nesneleri cmdlet tarafından oluşturulan çıktı değişkeni belirtir. Bu değişkeni eklemek için kullanın +*varname* değişkeni ayarlama ve temizleme yerine.

### <a name="outbuffer-alias-ob"></a>OutBuffer (diğer ad: ob)

Veri türü: Int32

Bu parametre, işlem hattını herhangi bir nesne geçirilmeden önce çıkış arabelleğinin depolamak için nesne sayısını tanımlar. Varsayılan olarak, nesneleri, işlem hattını hemen geçirilir.

### <a name="verbose-alias-vb"></a>Ayrıntılı (diğer ad: vb)

Veri türü: SwitchParameter

Bu parametre, cmdlet komut satırında görüntülenen açıklayıcı iletiler yazıp yazmayacağını belirtir. Bu iletiler, kullanıcıya ek Yardım sağlamak için tasarlanmıştır ve yapılan çağrılar tarafından oluşturulan [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi.

### <a name="warningaction-alias-wa"></a>WarningAction (diğer ad: wa)

Veri türü: Sabit listesi

Bu parametre, cmdlet bir uyarı iletisi Yazar olduğunda ne zaman gerçekleştirileceğini belirtir. Bu parametre için olası değerler tarafından tanımlanan [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) sabit listesi.

### <a name="warningvariable-alias-wv"></a>WarningVariable (diğer ad: wv)

Veri türü: Dize

Bu parametre, uyarı iletilerini kaydedilebilir değişkeni belirtir. Bu değişkeni eklemek için kullanın +*varname* değişkeni ayarlama ve temizleme yerine.

## <a name="risk-mitigation-parameters"></a>Risk azaltma parametreleri

Aşağıdaki parametreleri cmdlet'leri, bunlar kendi eylemi gerçekleştirmeden önce onay istekleri eklenir. Onay istekleri hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md). Bu parametreleri tarafından tanımlanan [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) sınıfı.

### <a name="confirm-alias-cf"></a>Onaylayın (diğer ad: cf)

Veri türü: SwitchParameter

Bu parametre, cmdlet kullanıcı devam etmek istediğinizden emin olup olmadığını soran bir istem görüntülenip görüntülenmeyeceğini belirtir.

### <a name="whatif-alias-wi"></a>WhatIf (diğer ad: wi)

Veri türü: SwitchParameter

Bu parametre, cmdlet gerçekte herhangi bir işlem yapmadan cmdlet'ini çalıştırarak etkilerini açıklayan bir ileti yazıp yazmayacağını belirtir.

## <a name="transaction-parameters"></a>İşlem parametreleri

Şu parametre işlemleri destekleyen cmdlet'ler eklendi. Bu parametreleri tarafından tanımlanan [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) sınıfı.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (diğer ad: usetx)

Veri türü: SwitchParameter

Bu parametre, eylemi gerçekleştirmek için geçerli işlem cmdlet'ini kullanıp kullanmayacağını belirtir.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
