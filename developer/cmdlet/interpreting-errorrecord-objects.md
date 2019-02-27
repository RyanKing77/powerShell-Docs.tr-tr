---
title: ErrorRecord nesneleri yorumlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: d77e4daf25bfcd5e76c184f6dbdb619368627bfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847673"
---
# <a name="interpreting-errorrecord-objects"></a>ErrorRecord Nesnelerini Yorumlama

Çoğu durumda bir [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesnesi bir komutu veya betiği tarafından oluşturulan bir sonlandırıcı olmayan hata temsil eder. Hataları sonlandıran belirtebilirsiniz ek bilgiler bir ErrorRecord içinde [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) arabirimi.

Betiğinizi veya bir konak gerekir yorumlar komut veya betik yürütme sırasında gerçekleşen belirli hataları işlemek için bir hata işleyicisi yazmak istiyorsanız [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) belirlemek için nesne yoksa, kullanmak istediğiniz hata sınıfını temsil eder.

Sonlandırıcı olmayan hata bir cmdlet bir sonlandırma karşılaştığında veya hata durumunu açıklayan bir hata kaydı oluşturmanız gerekir. Ana bilgisayar uygulaması, bu hata kayıtları araştırmak ve gerçekleştirmek istediğiniz eylemi hata riskini azaltır. Konak uygulama kayıt işlemi başarısız oldu, ancak devam edebilir olmak üzere sonlandırmasız hatalar için hata kaydı ayrıca araştırmanız gerekir ve durdurmak ardışık düzen nedeniyle sonlandırılıyor hataları için hata kaydı araştırmanız gerekir.

> [!NOTE]
> Sonlandıran hata için cmdlet'i çağırır [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi. Sonlandırıcı olmayan hatalar için cmdlet'i çağırır [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi.

## <a name="error-record-design"></a>Hata kayıt tasarım

Hata kaydı birleşik bilgileri her bir hata kaydı benzersiz olmasını sağlarken durumlar kullanılabilir olmayan ek hata bilgileri sağlamak için tasarlanmıştır. Bu benzersizlik hata kaydı farklı bölümlerini hata durumunu belirleyebilir ve konak ilgilenmek zorunda incelemek ana bilgisayar uygulaması sağlar.

## <a name="interpreting-error-records"></a>Hata kaydı yorumlama

Hatayı belirlemek için hata kaydı çeşitli parçaları gözden geçirebilirsiniz. Bu bölümleri şunlardır:

- Hata kategorisi

- Hata özel durumu

- Tam hata tanımlayıcı (FQID)

- Diğer bilgiler

### <a name="the-error-category"></a>Hata kategorisi

Hata Kayıt hata kategorisi tarafından sağlanan önceden tanımlanmış sabitleri biridir [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) sabit listesi. Bu bilgiler aracılığıyla kullanılabilir [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) özelliği [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne.

Cmdlet CloseError, OpenError InvalidType, okuma hatası ve WriteError kategoriler ve diğer hata kategorisi belirtebilirsiniz. Konak uygulama hata kategorisi hata grupları yakalamak için kullanabilirsiniz.

### <a name="the-exception"></a>Özel durum

Hata kaydında bulunan özel durum cmdlet tarafından sağlanır ve erişilebilir [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) özelliği [ System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne.

Ana bilgisayar uygulamaları kullanabilir `is` özel durumu belirli bir sınıfın veya türetilmiş bir sınıfın olduğunu belirlemek için anahtar sözcüğü. Aşağıdaki örnekte gösterildiği gibi özel durum türü, bir daldaki iyidir.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Bu şekilde türetilmiş sınıfları yakalayın. Ancak, özel durum seri durumdan çıkarıldıysa sorunları vardır.

### <a name="the-fqid"></a>FQID

FQID hatayı belirlemek için kullanabileceğiniz en belirgin bilgilerdir. Bu cmdlet tarafından tanımlanan bir tanımlayıcı, cmdlet sınıfı ile bildirilen hata kaynağı adını içeren bir dizedir. Genel olarak, bir hata kaydı Windows olay günlüğüne bir olay kaydı benzerdir. Olay kaydının sınıfı tanımlayan bir aşağıdaki demet FQID benzerdir: (*günlük adı*, *kaynak*, *öğesini belirten Olay No.*).

Tek bir dize olarak denetlenecek FQID tasarlanmıştır. Konak uygulama tarafından ayrıştırılması hata tanımlayıcı tasarlanmıştır ancak çalışmaları mevcut. Aşağıdaki örnek biçimlendirilmiş tam hata tanımlayıcısıdır.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Önceki örnekte, ilk belirteç, ardından cmdlet'i sınıf adı hata tanımlayıcısıdır. Hata tanımlayıcı, tek bir belirteç veya tanımlayıcısının denetimi dallara ayırmaya izin veren bir noktayla ayrılmış tanımlayıcı olabilir. Boşluk veya noktalama hatası tanımlayıcıda kullanmayın. Virgül kullanmamak özellikle önemlidir; virgül tarafından Windows PowerShell tanımlayıcısı ve cmdlet sınıf adını ayırmak için kullanılır.

### <a name="other-information"></a>Diğer Bilgiler

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne hatanın gerçekleştiği ortamı tanımlayan bilgileri de sağlayabilirsiniz. Bu bilgiler hata ayrıntıları, çağrı bilgileri ve hatanın oluştuğu sırada işlenmekte olan hedef nesne gibi öğeleri içerir. Bu bilgiler ana bilgisayar uygulamasına yararlı olabilir, ancak genellikle hata tanımlamak için kullanılmaz. Bu bilgiler aşağıdaki özellikleri aracılığıyla kullanılabilir:

[System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.Errorrecord.Invocationinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.Errorrecord.Targetobject*](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Sonlandırıcı olmayan hata raporlama, cmdlet'e ekleme](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell hata raporlama](./error-reporting-concepts.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
