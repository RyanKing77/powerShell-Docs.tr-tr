---
title: GetProc Eğitmeni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851334"
---
# <a name="getproc-tutorial"></a>GetProc Öğreticisi

Bu bölüm, bunun için bir Get-Proc cmdlet oluşturma çok benzer bir öğretici sağlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sağlanan tarafından Windows PowerShell cmdlet'i. Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.

## <a name="topics-in-this-tutorial"></a>Bu öğreticide konuları

Bu öğreticide konular, önceki konu başlığında açıklanan üzerinde ne oluşturmaya her konu ile ardışık olarak okunacak şekilde tasarlanmıştır.

[Parametresiz bir cmdlet'i oluşturma](./creating-a-cmdlet-without-parameters.md) Bu bölümde parametre kullanmadan bir yerel bilgisayardan bilgilerini alır ve sonra bilgi işlem hattına yazan bir cmdlet'i oluşturmayı açıklar.

[Bu işlem komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md) Bu bölümde, cmdlet cmdlet'e geçirilen açık nesneler göre giriş işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar. Açıklanan uygulama burada kendi adına göre işlemler alır ve ardından işlem hattının bilgi yazar.

[Bu işlem ardışık giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md) Bu bölümde, cmdlet ardışık düzende geçirilen nesneleri işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar. Açıklanan uygulama cmdlet burada işlemleri cmdlet'e geçirilen nesneleri temel alır ve ardından işlem hattının bilgi yazar.

[Bilgisayarınızı cmdlet'e ekleme olmak üzere Sonlandırmasız hata raporlama](./adding-non-terminating-error-reporting-to-your-cmdlet.md) Bu bölümde, bir cmdlet için olmak üzere sonlandırmasız rapor eklemeyi açıklar. Burada açıklanan uygulama girişi işlerken oluşur ve bir hata kaydı hatası akışa Yazar olmak üzere sonlandırmasız hatalar algılar.

## <a name="see-also"></a>Ayrıca bkz:

[Parametresiz bir cmdlet'i oluşturma](./creating-a-cmdlet-without-parameters.md)

[Komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md)

[İşlem ardışık düzen giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md)

[Cmdlet'inize için olmak üzere Sonlandırmasız rapor ekleme](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
