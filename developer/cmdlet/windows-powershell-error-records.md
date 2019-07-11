---
title: Windows PowerShell hata kayıtları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735068"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell Hata Kayıtları

Cmdlet'leri geçmesi gerekir bir [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) sonlandıran ve sonlandırmayan hatalar için hata koşulu tanımlayan nesne.

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne, aşağıdaki bilgileri içerir:

- Hatayı açıklayan özel durum. Genellikle, bu cmdlet yakalandı ve bir hata kayıtta bir özel durumdur. Her hata kaydı, bir özel durum içermelidir.

Cmdlet'i bir özel durum yakalamak değil, bu yeni bir özel durum oluşturmak ve en iyi hata durumunu açıklayan özel durum sınıfı seçin. Ancak, üzerinden erişilebildiğinden, özel durum gerekmez [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) özelliği [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)nesne.

- Tanılama amacıyla ve Windows PowerShell komut dosyaları tarafından belirli hata işleyicilerini ile belirli hata durumlarını işlemek için kullanılabilir hedeflenen bir gösterge sağlar hata tanımlayıcı. Her hata kaydı hata tanımlayıcı içermelidir (hata tanımlayıcısı bakın).

- Tanılama amacıyla kullanılan genel bir gösterge sağlar hata kategorisi. Her hata kaydı hata kategorisi belirtmeniz gerekir (hata kategorisi bakın).

- İsteğe bağlı değiştirme hata iletisi ve önerilen eylemi (değiştirme hata iletisine bakın).

- İsteğe bağlı çağırma hatası oluşturdu cmdlet'i hakkında bilgi sağlar. Bu bilgiler, Windows PowerShell tarafından belirtilen (çağırma iletisinin bakın).

- Hata oluştuğu sırada işlenmekte olan hedef nesne. Bu giriş nesnesi olabilir veya cmdlet'inize işlemekte olan başka bir nesne olabilir. Örneğin, komut için `remove-item -recurse c:\somedirectory`, hata "c:\somedirectory\lockedfile" için bir FileInfo nesnesi örneği olabilir. Hedef nesne bilgileri isteğe bağlıdır.

## <a name="error-identifier"></a>Hata tanımlayıcı

Bir hata kaydı oluşturduğunuzda, cmdlet'inize içinde hata koşulu belirten bir tanımlayıcı belirtin. Windows PowerShell hedeflenen tanımlayıcı tam hata tanımlayıcısını oluşturmak için cmdlet adı ile birleştirir. Tam hata tanımlayıcı erişilebilir [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) özelliği [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)nesne. Hata tanımlayıcı tek başına kullanılabilir değil. Kullanılabilir yalnızca tam hata tanımlayıcısının parçası olarak.

Hata kaydı oluştururken hata tanımlayıcıları oluşturmak için aşağıdaki yönergeleri kullanın:

- Hata tanımlayıcı, bir hata koşulunu belirgin hale getirin. Tanılama amacıyla ve belirli hata koşulları belirli hata işleyicilerini ile işleyen bir komut dosyası için hata tanımlayıcıları hedefleyin. Bir kullanıcı hata ve kaynağı tanımlamak için hata tanımlayıcı kullanmanız mümkün olması gerekir. Yeni özel durum alt sınıflar, gerekli değildir. böylece, mevcut özel belirli hata koşulları için Raporlama hata tanımlayıcıları da etkinleştirin.

- Genel olarak, farklı hata tanımlayıcıları farklı kod yollarını atayın. Son kullanıcı, belirli tanımlayıcılardan fayda sağlar. Genellikle, çağrıları her kod yolu [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) veya [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) kendi tanımlayıcısı. Hata iletisi ve tersi için yeni bir şablon dize tanımlarken bir kural olarak, yeni bir tanımlayıcı tanımlayın. Hata iletisi, tanımlayıcı olarak kullanmayın.

- Belirli hata tanımlayıcısını kullanarak kod yayımladığınızda, bu tanımlayıcı, eksiksiz bir ürün için hatalarla semantiği yaşam döngüsü destek kurun. Bu orijinal içerikten anlamsal olarak farklı bir bağlamda yeniden kullanmayın. Bu hata semantiği değiştirirseniz, oluşturun ve yeni bir kimlik kullanın.

- Belirli hata tanımlayıcısı, genellikle yalnızca belirli bir CLR türü istisnalara kullanmalısınız. Özel durumun türünü veya hedef nesne türü değişirse, oluşturun ve yeni bir kimlik kullanın.

- Raporladığınız hatayı kısaca karşılık gelen hata tanımlayıcınızı metnini seçin. Standart .NET Framework adlandırma ve büyük/küçük harf kuralları kullanın. Boşluk veya noktalama işareti kullanmayın. Hata tanımlayıcıları yerelleştiriyor musunuz.

- Dinamik olarak hata tanımlayıcıları tekrarlanabilir olmayan bir şekilde oluşturmaz. Örneğin, bir işlem kimliği gibi hata bilgisi içermeyen uygulamalardır Yalnızca bunlar aynı hata koşuluyla karşılaşıp diğer kullanıcılar tarafından görülen hatayla tanımlayıcıları karşılık geliyorsa, hata tanımlayıcıları yararlıdır.

## <a name="error-category"></a>Hata kategorisi

Bir hata kaydı oluşturduğunuzda, tarafından tanımlanan sabitlerinden birini kullanarak hatayı kategorisini belirtmek [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) sabit listesi. Windows PowerShell ayarladığınızda kullanıcılar, hata bilgilerini görüntülemek için hata kategorisi kullanır `$ErrorView` değişkenini `"CategoryView"`.

Kullanmaktan kaçının [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** sabit. Hataya neden olan işlem veya hata hakkında hiçbir bilgi varsa kategori kusursuz olsa bile hata ya da işlemi en iyi açıklayan kategoriyi seçin.

Windows PowerShell tarafından görüntülenen bilgiler kategori görünümünde dizesi olarak adlandırılır ve özelliklerinden oluşturulmuştur [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) sınıfı. (Bu sınıf, hata erişilir [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) özellik.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

Aşağıdaki listede görüntülenen bilgileri açıklanmaktadır:

- Kategori: Windows PowerShell tanımlı [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) sabit.

- TargetName: Varsayılan olarak, hata oluştuğunda nesnesinin adını cmdlet işliyordu. Veya başka bir cmdlet tanımlı bir dize.

- TargetType: Varsayılan olarak, hedef nesne türü. Veya başka bir cmdlet tanımlı bir dize.

- Etkinlik: Varsayılan olarak, hata kaydı oluşturan cmdlet adı. Veya, cmdlet tarafından tanımlanan herhangi bir dize.

- Neden: Varsayılan olarak, özel durum türü. Veya başka bir cmdlet tanımlı bir dize.

## <a name="replacement-error-message"></a>Değiştirme hata iletisi

Bir cmdlet için bir hata kaydı geliştirdiğinizde, varsayılan ileti metni varsayılan hata iletisi hatayı geldiği [System.Exception.Message](/dotnet/api/System.Exception.Message) özelliği. İleti metni yalnızca hata ayıklama amacıyla (.NET Framework yönergeleriyle göre) hazırlanmıştır salt okunur bir özellik budur. Değiştirir veya varsayılan ileti metni çoğaltan bir hata iletisi oluşturmanızı öneririz. İleti cmdlet'e daha kolay ve daha belirli olun.

Değiştirme yapılacak tarafından sağlanan bir [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) nesne. Windows PowerShell tarafından kullanılabilen ek yerelleştirme bilgisi sağladıkları için bu nesnenin şu oluşturuculardan birini kullanın.

- [Hata ayrıntıları (cmdlet'i, String, String, Object[])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): Şablon dizenizi cmdlet gerçekleştirilir aynı bütünleştirilmiş kodun kaynak dizesi ise veya şablon dizesini geçersiz kılma yoluyla yüklemek istiyorsanız bu bu oluşturucuyu kullanarak [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) yöntemi.

- [Hata ayrıntıları (derleme, dize, dize, Object[])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): Bu oluşturucu kullanın şablon dizesini başka bir derlemede ve bu geçersiz kılma yüklenmiyor [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Değiştirme yapılacak küçük bir fark dışında özel durum iletileri yazmak için .NET Framework tasarım ilkelerine uymalıdır. Geliştiriciler için özel durum iletileri yazılması yönergeleri durumu. Bu değişikliği iletileri için cmdlet'i kullanıcı yazılması gerekir.

Değiştirme hata iletisi önce eklenmelidir [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) veya [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) yöntemi çağrılır. Bir değiştirme iletisi eklemek için [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) hata kaydı özelliği. Bu özelliği ayarlandığında, Windows PowerShell görüntüler [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) özelliği yerine varsayılan ileti metni.

## <a name="recommended-action-information"></a>Önerilen eylem bilgileri

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) nesne de hata oluştuğunda, hangi eylemlerin önerilen hakkında bilgi sağlar.

## <a name="invocation-information"></a>Çağrı bilgileri

Bir cmdlet kullandığında [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) veya [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) bir hata kaydı, Windows PowerShell bildirmek için hata oluştuğunda çağrıldı komutu açıklayan bilgileri otomatik olarak ekler. Bu bilgileri tarafından sağlanan bir [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) komutu, kendisini komutu tarafından çağrıldı cmdlet adı içeren nesneyi ve ardışık düzen veya komut dosyası hakkında bilgi. Bu özellik salt okunurdur.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Windows PowerShell hata raporlama](./error-reporting-concepts.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
