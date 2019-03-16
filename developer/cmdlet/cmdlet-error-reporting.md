---
title: Cmdlet'i hata raporlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057952"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet Hata Raporlama

Cmdlet'leri, farklı bağlı olarak hataları hataları olup olmadığını sonlandırma hataları veya olmak üzere sonlandırmasız hatalar bildirmeniz gerekir. Sonlandıran hata hemen sonlandırılması için işlem hattı neden olan hataları ya da işleme devam etmek için bir neden olduğunda gerçekleşen hataları oluşturur. Geçerli bir hata koşulu rapor bu hataları olmak üzere sonlandırmasız hatalar olan ancak cmdlet giriş nesneleri işlemek devam edebilirsiniz. Olmak üzere sonlandırmasız hatalar, kullanıcı genellikle sorununu bilgilendirilir, ancak cmdlet sonraki giriş nesnesi işlemeye devam eder.

## <a name="terminating-and-nonterminating-errors"></a>Sonlandıran hem de olmak üzere Sonlandırmasız hatalar

Aşağıdaki yönergeler, bir hata durumu hatası veya olmak üzere sonlandırmasız bir hata olup olmadığını belirlemek için kullanılabilir.

- Hata koşulu cmdlet'inize, daha fazla giriş tüm nesneler başarıyla işlenmesini önlemek mu? Bu durumda, bir sonlandırma hatası budur.

- Hata durumu, belirli bir giriş nesnesi veya bir alt giriş nesnelerin ilişkili mi? Bu, bu durumda, olmak üzere sonlandırmasız bir hatadır.

- Cmdlet gibi işleme giriş başka bir nesne üzerinde başarılı olabilir birden çok giriş nesneleri kabul ediyor mu? Bu, bu durumda, olmak üzere sonlandırmasız bir hatadır.

- Hatta belirli bir durum yalnızca tek bir giriş nesnesine geçerli olduğu durumlarda birden çok giriş nesne kabul edebilen cmdlet'leri ne sonlandırma ve olmak üzere sonlandırmasız hatalar arasında karar vermeniz gerekir.

- Cmdlet'leri herhangi bir sayıda giriş nesneleri alabilir ve bir sonlandırma özel durumuyla atamadan önce herhangi bir sayıda başarı veya hata nesneleri gönderin. Alınan giriş nesne sayısını ve gönderilen başarı ve hata nesne sayısı arasında bir ilişki yoktur.

- Yalnızca 0-1 nesneleri giriş ve yalnızca 0-1 oluşturmak kabul edebilen cmdlet'leri nesneler hataları sonlandıran hata olarak kabul et ve sonlandırıcı özel durumlar oluşturmaya çıktı.

## <a name="reporting-nonterminating-errors"></a>Raporlama olmak üzere Sonlandırmasız hatalar

Raporlama olmak üzere sonlandırmasız bir hata her zaman içinde cmdlet'in uygulaması yapılmalıdır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi veya [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi. Bu tür hataları çağırarak raporlanır [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) sırayla hata akışına bir hata kaydı gönderen yöntemi.

## <a name="reporting-terminating-errors"></a>Sonlandıran hata raporlama

Sonlandıran hata bildirilen özel durumları atma veya arayarak [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi. Cmdlet ayrıca catch ve özel durumlar gibi OutOfMemory yeniden harekete geçirerek, ancak bunlar Windows PowerShell çalışma zamanı bunları da yakalar özel durumlar yeniden harekete geçirileceğini gerekli değildir unutmayın.

Ayrıca, belirli sorunlar için kendi özel durumlarınızı durumunuza tanımlayın veya kendi hata kaydı kullanarak mevcut bir özel ek bilgi ekleyebilirsiniz.

## <a name="error-records"></a>Hata kaydı

Windows PowerShell kullanarak bir olmak üzere sonlandırmasız bir hata koşulu tanımlar [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesneleri. Her [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne, hata kategorisi bilgileri, isteğe bağlı bir hedef nesneyi ve hata durumu hakkında ayrıntılar sağlar.

### <a name="error-identifiers"></a>Hata tanımlayıcıları

Hata tanımlayıcı cmdlet içinde hata koşulu tanımlayan basit bir dizedir. Windows PowerShell Bu tanımlayıcıyı belirli hatalar için yanıt verirken hata veya günlük kaydı hataları, filtreleme, daha sonra kullanılabilir bir tam hata tanımlayıcısını oluşturmak için cmdlet'i tanımlayıcısı veya başka bir kullanıcıya özel etkinlikler ile birleştirir.

Aşağıdaki yönergeler, hata tanımlayıcıları belirtirken gelmelidir.

- Farklı, yüksek oranda ayrıntılı hata tanımlayıcıları farklı kod yollarını atayın. Çağıran her kod yolu [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) veya [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) kendi hata tanımlayıcısı olmalıdır.

- Hata tanımlayıcıları hem sonlandıran hem de olmak üzere sonlandırmasız hatalar için CLR özel durum türleri için benzersiz olmalıdır.

- Bir cmdlet veya Windows PowerShell sağlayıcısı sürümleri arasında hata tanımlayıcı semantiği değiştirmeyin. Hata tanımlayıcı semantiği kurulduktan sonra cmdlet'inize yaşam döngüsü boyunca sürekli kalması gerekir.

- Sondaki hataları için hata benzersiz tanımlayıcısı için belirli bir CLR özel durum türü kullanın. Özel durum türü değişirse, yeni bir hata tanımlayıcısı kullanın.

- Olmak üzere sonlandırmasız hatalar için belirli bir giriş nesnesi için bir özel hata tanımlayıcısı kullanın.

- Metin için raporlanan hata tersely karşılık gelen tanımlayıcısını seçin. Boşluk veya noktalama işareti kullanmayın.

- Tekrarlanabilir olmayan hata tanımlayıcıları oluşturmaz. Örneğin, bir işlem tanımlayıcısını içeren tanımlayıcılar oluşturmaz. Yalnızca bunlar aynı sorunu yaşayan başka kullanıcılar tarafından görülen tanımlayıcıları karşılık hata tanımlayıcıları yararlıdır.

### <a name="error-categories"></a>Hata kategorisi

Hata kategorileri, son kullanıcı hataları gruplandırmak için kullanılır. Windows PowerShell kategorilerine tanımlar ve cmdlet'lerini ve Windows PowerShell sağlayıcıları aralarında hata kaydı oluşturulurken seçmelisiniz.

Kullanılabilir hata kategorilerinin açıklaması için bkz. [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) sabit listesi. Genel olarak, NoError UndefinedError ve mümkün olduğunda genel hata kaçınmanız gerekir.

Kullanıcılar, bunlar ayarladığınızda, kategoriye göre hataları görüntüleyebilirsiniz "`$ErrorView`" için "CategoryView".

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell cmdlet'leri](./cmdlet-overview.md)

[Cmdlet çıkışı](./types-of-cmdlet-output.md)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
