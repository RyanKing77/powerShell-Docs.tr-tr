---
title: Cmdlet hata raporlama | Microsoft Docs
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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986321"
---
# <a name="cmdlet-error-reporting"></a>Cmdlet hata bildirimi

Cmdlet 'ler hataların hataları sonlandırıp sonlandırmayacağı veya sonlandırmasız hatalar olmasına bağlı olarak hataları farklı şekilde raporlemelidir. Hataları sonlandırma, işlem hattının hemen sonlandırılmasını veya işleme devam etmek için bir neden olmadığında oluşan hataları ortaya çıkarabilir. Sonlandırıcı olmayan hatalar, geçerli bir hata koşulunu rapor eden hatalardır, ancak cmdlet giriş nesnelerini işlemeye devam edebilir. Sonlandırıcı olmayan hatalar ile kullanıcıya genellikle sorun bildirilir, ancak cmdlet bir sonraki giriş nesnesini işlemeye devam eder.

## <a name="terminating-and-nonterminating-errors"></a>Sonlandırma ve Sonlandırıcı olmayan hatalar

Bir hata koşulunun Sonlandırıcı hatası mu yoksa Sonlandırıcı olmayan bir hata mu olduğunu anlamak için aşağıdaki kılavuzlar kullanılabilir.

- Hata koşulu, cmdlet 'inin daha fazla giriş nesnesini başarıyla işlemesini engelliyor mu? Bu durumda, bu bir sonlandırma hatasıdır.

- Hata durumu, belirli bir giriş nesnesi veya giriş nesneleri alt kümesiyle ilgili mi? Bu durumda, bu Sonlandırıcı olmayan bir hatadır.

- Cmdlet birden çok giriş nesnesini kabul ediyor, ancak başka bir giriş nesnesinde işleme başarılı olabilir mi? Bu durumda, bu Sonlandırıcı olmayan bir hatadır.

- Birden çok giriş nesnesini kabul edebilecek cmdlet 'ler, belirli bir durum yalnızca tek bir giriş nesnesi için geçerli olduğunda bile Sonlandırıcı ve Sonlandırıcı olmayan hatalar arasında karar almalıdır.

- Cmdlet 'leri, bir sonlandırma özel durumu oluşturmadan önce herhangi bir sayıda giriş nesnesini alabilir ve herhangi bir sayıda başarılı veya hata nesnesi gönderebilir. Alınan girdi nesnelerinin sayısı ve gönderilen başarı ve hata nesnelerinin sayısı arasında hiçbir ilişki yoktur.

- Yalnızca 0-1 giriş nesnesini kabul edebilecek ve yalnızca 0-1 çıkış nesnesi oluşturan cmdlet 'ler hataları sonlandırma hataları olarak değerlendirilir ve sonlandırma özel durumları oluşturur.

## <a name="reporting-nonterminating-errors"></a>Sonlandırıcı olmayan hataları raporlama

Sonlandırıcı olmayan bir hatanın raporlanması her zaman cmdlet 'inin [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi, [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi veya [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi. Bu tür hatalar, sırasıyla hata akışına bir hata kaydı Gönderen [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi çağırarak raporlanır.

## <a name="reporting-terminating-errors"></a>Raporlama hatalarını bildirme

Hataları sonlandırma, özel durumlar oluşturarak veya [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi çağırarak bildirilir. Cmdlet 'lerin Ayrıca **OutOfMemory**gibi özel durumları yakalayabilir ve yeniden oluşturduklarında, PowerShell çalışma zamanı bunları da yakalayabileceği için bunların özel durumları yeniden oluşturması gerekli değildir.

Ayrıca, durumunuza özgü sorunlar için kendi özel durumlarınızı tanımlayabilir veya hata kaydını kullanarak mevcut bir özel duruma ek bilgiler ekleyebilirsiniz.

## <a name="error-records"></a>Hata kayıtları

PowerShell, [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesneleriyle birlikte Sonlandırıcı olmayan bir hata koşulu tanımlar. Her bir nesne hata kategorisi bilgileri, isteğe bağlı bir hedef nesnesi ve hata durumu hakkında ayrıntılar sağlar.

### <a name="error-identifiers"></a>Hata tanımlayıcıları

Hata tanımlayıcısı cmdlet içinde hata koşulunu tanımlayan basit bir dizedir.
PowerShell bu tanımlayıcıyı, daha sonra hata akışları veya günlüğe kaydetme hatalarını filtrelerken, belirli hatalara yanıt vermediğinde veya kullanıcıya özgü diğer etkinliklerle birlikte kullanılabilecek tam bir hata tanımlayıcısı oluşturmak için bir cmdlet tanımlayıcısı ile birleştirir.

Aşağıdaki yönergelerin hata tanımlayıcıları belirtildiğinde izlenmesi gerekir:

- Farklı kod yollarına farklı, yüksek oranda özel, hata tanımlayıcıları atayın. [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) veya [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ' i çağıran her kod yolunun kendi hata tanımlayıcısına sahip olması gerekir.

- Hata tanımlayıcıları hem Sonlandırıcı hem de Sonlandırıcı olmayan hatalar için ortak dil çalışma zamanı (CLR) özel durum türleri için benzersiz olmalıdır.

- Cmdlet veya PowerShell sağlayıcınızın sürümleri arasındaki bir hata tanımlayıcısının semantiğini değiştirmeyin. Bir hata tanımlayıcısının semantiği oluşturulduktan sonra, cmdlet 'inin yaşam döngüsü boyunca sabit kalmalıdır.

- Hataları sonlandırmak için, belirli bir CLR özel durum türü için benzersiz bir hata tanımlayıcısı kullanın. Özel durum türü değişirse, yeni bir hata tanımlayıcısı kullanın.

- Sonlandırıcı olmayan hatalar için belirli bir giriş nesnesi için belirli bir hata tanımlayıcısı kullanın.

- Bildirilen hataya karşılık gelen tanımlayıcı için metin seçin. Boşluk veya noktalama işareti kullanmayın.

- Tekrarlanmamış hata tanımlayıcıları oluşturmamayın. Örneğin, bir işlem tanımlayıcısı içeren tanımlayıcılar oluşturmayın. Hata tanımlayıcıları yalnızca aynı sorunu yaşayan diğer kullanıcılar tarafından görülen tanımlayıcılara karşılık geliyorsa yararlıdır.

### <a name="error-categories"></a>Hata kategorileri

Hata kategorileri Kullanıcı için hataları gruplandırmak için kullanılır. PowerShell bu kategorileri ve cmdlet 'leri tanımlar ve PowerShell sağlayıcılarının hata kaydını oluştururken aralarında seçim yapmanız gerekir.

Kullanılabilir hata kategorilerinin bir açıklaması için bkz. [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) sabit listesi. Genel olarak, mümkün olduğunda **NOERROR**, **UndefinedError**ve **genericerror** kullanmaktan kaçının.

Kullanıcılar kategorili `$ErrorView` **Görünüm**olarak ayarlandığında, kategoriye göre hataları görüntüleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

[Cmdlet 'e genel bakış](./cmdlet-overview.md)

[Cmdlet çıkış türleri](./types-of-cmdlet-output.md)

[Windows PowerShell Başvurusu](../windows-powershell-reference.md)
