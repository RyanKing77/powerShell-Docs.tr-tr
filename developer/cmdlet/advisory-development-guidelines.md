---
title: Danışmanlık geliştirme yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854879"
---
# <a name="advisory-development-guidelines"></a>Tavsiye Niteliğinde Geliştirme Yönergeleri

Bu bölümde, iyi geliştirme ve kullanıcı deneyimleri sağlamak için dikkate almanız yönergeler açıklanmaktadır. Bazen uygulanabilir ve bazen olabilir değil.

## <a name="design-guidelines"></a>Tasarım yönergeleri

Cmdlet'leri tasarlarken aşağıdaki yönergeleri dikkate alınmalıdır. Durumunuza bir tasarım kılavuzu bulduğunuzda, benzer yönergeleri için kod yönergelere bakmak emin olun.

### <a name="support-an-inputobject-parameter-ad01"></a>Bir Inputobject parametresi (AD01) desteği

Windows PowerShell Microsoft .NET Framework nesneleri ile doğrudan çalıştığından, bir .NET Framework nesnesi genellikle tam olarak eşleşen kullanıcı türü gerekiyor belirli bir işlemi gerçekleştirip kullanılabilir. `InputObject` Böyle bir nesnenin giriş olarak alan bir parametre için standart adıdır. Örneğin, örnek **Stop-Proc** cmdlet'inde [StopProc öğretici](./stopproc-tutorial.md) tanımlayan bir `InputObject` ardışık düzendeki girişi destekleyen işlem türünde parametre. Kullanıcı işlem nesneleri kümesini almak, durdurmak için tam nesneleri seçmek için bunları yönetmek ve bunlara geçirmek **Stop-Proc** doğrudan cmdlet'i.

### <a name="support-the-force-parameter-ad02"></a>Force parametresini (AD02) desteği

Bazen, kullanıcının istenen işlemi gerçekleştirmemizi korumak bir cmdlet gerekir. Böyle bir cmdlet desteklemelidir bir `Force` kullanıcının işlemi gerçekleştirmek için izni olup olmadığını, korumayı geçersiz kılmak izin vermek için parametre.

Örneğin, [Kaldır öğesini](/powershell/module/microsoft.powershell.management/remove-item) cmdlet, salt okunur bir dosya normalde kaldırmaz. Ancak, bu cmdlet destekleyen bir `Force` parametresi için bir kullanıcı bir salt okunur dosya kaldırılmasını zorlayabilirsiniz. Kullanıcı salt okunur özniteliğini değiştirmek için izne zaten sahip ve kullanıcı dosyayı kaldırır, kullanım `Force` parametresi işlemi basitleştirir. Ancak, kullanıcının dosyayı silme iznine sahip değilse `Force` parametresi etkisizdir.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Windows PowerShell (AD03) üzerinden kimlik bilgilerini işleme

Bir cmdlet tanımlamalıdır bir `Credential` kimlik bilgilerini temsil etmek için parametre. Bu parametre türü olmalıdır [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) ve bir kimlik bilgisi özniteliği bildirimi kullanılarak tanımlanmalıdır. Bu destek, otomatik olarak tam bir kimlik bilgisi doğrudan sağlanamadığında kullanıcının kullanıcı adı, parola veya her ikisi için de ister. Kimlik bilgisi özniteliği hakkında daha fazla bilgi için bkz. [kimlik bilgisi öznitelik bildiriminin](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Kodlama parametreler (AD04) desteği

Cmdlet'inize okur ya da metin ya da bir dosya sistemi dosyasından okuma veya yazma gibi bir ikili biçimindeki Yazar cmdlet'inize nasıl metin ikili biçimde kodlandı belirten kodlama parametresi sahip olması gerekir.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Sınama cmdlet'lerini bir Boole değeri (AD05) döndürmelidir

Testleri kendi kaynaklara karşı gerçekleştirdiğiniz cmdlet'leri döndürmelidir bir [System.Boolean](/dotnet/api/System.Boolean) koşullu ifadelerde kullanılabilir olacak şekilde işlem hattının yazın.

## <a name="code-guidelines"></a>Kod kuralları

Cmdlet'i kodu yazarken aşağıdaki kılavuzları dikkate alınmalıdır. Durumunuza bir kılavuz bulduğunuzda, benzer yönergeleri için tasarım kılavuzlarına bakın emin olun.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Cmdlet'i sınıf adlandırma kuralları (AC01) izleyin

Aşağıdaki standart adlandırma kuralları cmdlet'lerinizi keşfedilmesini kolaylaştırın ve cmdlet'leri tam olarak ne anlama kullanıcı Yardımı. Bu yöntem Windows PowerShell cmdlet'leri genel türleri olduğundan kullanarak diğer geliştiriciler için özellikle önemlidir.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Bir Cmdlet doğru Namespace tanımlayın

Ekler bir .NET Framework ad alanında normalde bir cmdlet için bir sınıf tanımlama ". Komutları"cmdlet'in çalıştığı bir ürünü temsil ad alanı. Örneğin, Windows PowerShell ile dahil edilen cmdlet'ler içinde tanımlı `Microsoft.PowerShell.Commands` ad alanı.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Cmdlet adı ile eşleşmesi için bu cmdlet'i sınıfı adı

Bir cmdlet uygulayan .NET Framework sınıf adı, sınıf adını "*\<fiil >**\<isim >**\<komut >*" değiştirinburada *\<Fiil >* ve  *\<isim >* fiil ve isim cmdlet adı için kullanılan, yer tutucular. Örneğin, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i adlı bir sınıf tarafından uygulanan `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Herhangi bir işlem hattı giriş (AC02) BeginProcessing yöntemi geçersiz kılarsanız

İçinde cmdlet'inize ardışık düzendeki girişi kabul etmiyor, işleme uygulanmalıdır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi. Bu yöntem cmdlet'leri sırayı da korumak Windows PowerShell kullanımına izin verir. İşlem hattının kalan cmdlet'leri, işleme başlamak için bir fırsat geçmeden önce işlem hattındaki ilk cmdlet her zaman nesnelerini döndürür.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Durdurma istekleri işlemek için (AC03) StopProcessing yöntemi geçersiz kılın

Geçersiz kılma [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) yöntemi cmdlet'inize durdurma sinyali işleyebilmeniz. Bazı cmdlet'ler, işlemin tamamlanması uzun sürebilir ve cmdlet RPC çağrıları uzun süre çalışan iş parçacığında zaman engeller gibi Windows PowerShell çalışma zamanı yapılan çağrılar arasında geçirmek uzun sağlarlar. Bu çağrı yapmak cmdlet'leri içerir [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi, [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi ve diğer geri bildirim Bu mekanizmalar tamamlanması uzun zaman alabilir. Bu durumda, kullanıcı için bu cmdlet'leri bir durdurma sinyali göndermek gerekebilir.

### <a name="implement-the-idisposable-interface-ac04"></a>(AC04) IDisposable arayüzünü uygular

Cmdlet'inize tarafından (işlem hattı için yazılmış) kaldırıldıklarından olmayan nesneler varsa [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi, ek bir nesneyi elden cmdlet'inize gerektirebilir. Örneğin, bir dosya tanıtıcısı cmdlet'inize açar, kendi [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi ve tutamacı açılmaya tarafından kullanılmak üzere tutar [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi, bu tutamacı sahip işlem sonunda kapatılmalıdır.

Windows PowerShell çalışma zamanı her zaman arama [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi. Örneğin, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi değil cmdlet midway bu işlemi iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir, çağrılabilir. Bu nedenle, nesne temizleme gerektiren bir cmdlet için .NET Framework sınıf tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) Sonlandırıcı dahil olmak üzere Windows PowerShell çalışma zamanı, her ikisi de çağırabilirsiniz arabirimi deseni [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ve [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Serileştirme uyumlu parametre türleri (AC05) kullanın

Cmdlet'inize uzak bilgisayarlarda çalışmasını desteklemek için istemci bilgisayarda kolayca serileştirilmiş ve ardından sunucu bilgisayarda rehydrated türlerini kullanın. İzleme, serileştirme dostu türleridir.

İlkel türler:

- Bayt, SByte, ondalık, tek, Double, Int16, Int32, Int64, UInt16, Uınt32 ve UInt64.

- Boolean, Guid, bayt [], TimeSpan, DateTime, URI ve sürüm.

- Char, String, XmlDocument.

Yerleşik rehydratable türleri:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IP adresi, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Diğer türleri:

- SecureString

- Kapsayıcılar (listeler ve yukarıdaki türü sözlükleri)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Hassas verileri (AC06) SecureString kullanın

Hassas verileri her zaman işlerken kullanmak [System.Security.Securestring](/dotnet/api/System.Security.SecureString) veri türü. Bu işlem hattı giriş parametreleri yanı sıra işlem hattının hassas verileri döndüren içerebilir.

## <a name="see-also"></a>Ayrıca bkz:

[Gerekli geliştirme yönergeleri](./required-development-guidelines.md)

[Önemle önerilir geliştirme yönergeleri](./strongly-encouraged-development-guidelines.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
