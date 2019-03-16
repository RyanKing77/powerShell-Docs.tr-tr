---
title: Geliştirme Kılavuzu gerekli | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056524"
---
# <a name="required-development-guidelines"></a>Gerekli Geliştirme Yönergeleri

Cmdlet'lerinizi yazarken aşağıdaki kılavuzları gelmelidir. Cmdlet'leri ve cmdlet kodunuzu yazma yönergeleri tasarlama yönergeleri ile ayrılır. Aşağıdaki yönergeleri izleyin değil, cmdlet'lerinizi başarısız olabilir ve cmdlet'lerinizi kullandıklarında, kullanıcılarınızın kötü bir deneyime sahip olabilir.

## <a name="in-this-topic"></a>Bu konudaki

### <a name="design-guidelines"></a>Tasarım yönergeleri

- [Kullanım fiiller (RD01) yalnızca onaylanmış](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet adları: Kullanılamaz karakterleri (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Kullanılamaz parametre adları (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Onay istekleri (RD04) desteği](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Etkileşimli oturumları (RD05) için Force parametresini destekler](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Belge çıkış nesnelerini (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Kod kuralları

- [Cmdlet'ini veya PSCmdlet sınıflardan (RC01) türetilir.](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Cmdlet öznitelik (RC02) belirtin](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [İşleme yöntemi (RC03) girdi geçersiz kıl](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [OutputType özniteliğini (RC04) belirtin](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Çıkış nesnelerini (RC05) tanıtıcıları korumuyor.](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Na hatalarını işleme (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Bir Windows PowerShell modülü Cmdlet'lerinizi (RC07) dağıtım yapma](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Tasarım yönergeleri

Cmdlet'lerinizi ve diğer cmdlet'leri kullanarak arasında tutarlı bir kullanıcı deneyimi sağlamak için cmdlet'leri tasarlarken aşağıdaki yönergeleri gelmelidir. Durumunuza bir tasarım kılavuzu bulduğunuzda, benzer yönergeleri için kod yönergelere bakmak emin olun.

### <a name="use-only-approved-verbs-rd01"></a>Kullanım fiiller (RD01) yalnızca onaylanmış

Cmdlet özniteliğinde belirtilen eylem fiilleri sağlanan Windows PowerShell tarafından tanınan kümesi gelmelidir. Yasaklanmış eş anlamlılar birini olmamalıdır. Aşağıdaki numaralandırmalar cmdlet fiilleri tarafından tanımlanan sabit dizeleri kullanın:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Onaylanmış bir fiil adları hakkında daha fazla bilgi için bkz. [Cmdlet fiilleri](./approved-verbs-for-windows-powershell-commands.md).

Kullanıcıların, bir dizi bulunabilir ve beklenen cmdlet adları gerekir. Kullanıcı bir cmdlet yapar ve sistem özelliklerini kolayca bulmak için bir hızlı değerlendirme yapabilmeleri için uygun bir fiil kullanın. Örneğin, aşağıdaki komut, adları "Başlangıç" ile başlayan sistem üzerindeki tüm komutların bir listesini alır: `get-command start-*`. Adlar, cmdlet'lerinde cmdlet'lerinizi diğer cmdlet'lerinden ayırt etmek için kullanın. İsim işlemi gerçekleştirilir kaynak gösterir. İşlem, fiili temsil edilir.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet adları: Kullanılamaz karakterleri (RD02)

Cmdlet adı, şu özel karakterlerden hiçbirini kullanmayın.

|Karakter|Adı|
|---------------|----------|
|#|sayı işareti|
|, |Virgül|
|()|Parantez|
|{}|Küme ayraçları|
|[]|köşeli ayraç|
|&|ve işareti|
|-|tire **Not:**  Fiili isim gelen ayırmak için tire kullanılabilir, ancak fiil veya isim içinde kullanılamaz.|
|/|eğik çizgi işareti|
|\|Ters eğik çizgi|
|$|Dolar işareti|
|^|Giriş işaretini|
|;|Noktalı virgül|
|:|İki nokta üst üste|
|"|Çift tırnak işareti|
|'|Tek tırnak işareti|
|<>|açılı ayraçlar|
|&#124;|dikey çubuk|
|?|Soru işareti|
|@|oturum sırasında|
|' | yedekleme değer çizgisi (kesme işareti)|
|*|Yıldız işareti|
|%|Yüzde işareti|
|+|Artı işareti|
|=|Eşittir işareti|
|~|Tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Kullanılamaz parametre adları (RD03)

Windows PowerShell bir dizi ortak bir parametre tüm cmdlet'ler için yanı sıra belirli durumlarda eklenen ek parametreler sunar. Kendi cmdlet'leri tasarlarken aşağıdaki adlarını kullanamazsınız: Onaylayın, hata ayıklama, ErrorAction ErrorVariable, OutBuffer OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction ve ayrıntılı. Bu parametreler hakkında daha fazla bilgi için bkz. [genel parametre adları](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Onay istekleri (RD04) desteği

Sistem değiştiren bir işlemi gerçekleştirmek için cmdlet'leri, bunlar çağırmalıdır [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) onay isteği ve özel durumlarda çağırmak için yöntem [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi. ( [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yalnızca sonra çağrılabilir [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi çağrılır.)

Cmdlet'i ayarlayarak doğrulama isteklerini desteklediğini belirtmeniz gerekir, bu çağrı yapmak için `SupportsShouldProcess` cmdlet'i özniteliğinin anahtar sözcüğü. Bu öznitelik ayarlama hakkında daha fazla bilgi için bkz. [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Cmdlet'i sınıf cmdlet'i öznitelik cmdlet çağrıları desteklediğini gösteriyorsa [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi ve cmdlet başarısız çağrı yapmak [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi, kullanıcının sistem beklenmedik bir şekilde değiştirebilir.

Kullanım [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) tüm sistem değiştirilmesi için yöntemi. Kullanıcı tercihi ve `WhatIf` parametre denetimi [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi. Buna karşılık, [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) çağrısı için potansiyel olarak tehlikeli olabilecek değişiklikleri ek bir denetim gerçekleştirir. Bu yöntem herhangi bir kullanıcı tercihi tarafından denetlenen veya `WhatIf` parametresi. Cmdlet'inize çağırırsa [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi içermelidir bir `Force` parametresi, bu iki yöntem çağrıları atlar ve işleme devam eder. Etkileşimli olmayan betikleri ve konaklar kullanılacak cmdlet'inize izin verdiğinden, bu önemlidir.

Bu çağrılar cmdlet'lerinizi destekliyorsa, kullanıcı eylemi gerçekten gerçekleştirilmesi gerekip gerekmediğini belirleyebilirsiniz. Örneğin, [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet'i çağrıları [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Winlogon, sistemi dahil olmak üzere kritik işlemler kümesini durdurulmadan önce yöntemi ve Spoolsv işlemleri.

Bu yöntemler destekleme hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Etkileşimli oturumları (RD05) için Force parametresini destekler

Cmdlet'i etkileşimli olarak kullanılıyorsa, her zaman komut istemlerini veya giriş satır okuma gibi etkileşimli eylemleri geçersiz kılmak için Force parametresini belirtin). Etkileşimli olmayan betikleri ve konaklar kullanılacak cmdlet'inize izin verdiğinden, bu önemlidir. Aşağıdaki yöntemlerden etkileşimli bir ana bilgisayar tarafından uygulanabilir.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Belge çıkış nesnelerini (RD06)

Windows PowerShell işlem hattına yazılır nesneleri kullanır. Kullanıcıların her cmdlet'i tarafından döndürülen nesneleri yararlanmak sırasıyla, döndürülen nesneleri belgelemeniz gerekir ve döndürülen nesnelere üyeleri için kullanılır belgeleyin gerekir.

## <a name="code-guidelines"></a>Kod kuralları

Cmdlet kodu yazarken aşağıdaki yönergeleri gelmelidir. Durumunuza bir kod kılavuz bulduğunuzda, benzer yönergeleri için tasarım kılavuzlarına bakın emin olun.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Cmdlet'ini veya PSCmdlet sınıflardan (RC01) türetilir.

Bir cmdlet tarafından türetilmelidir [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) veya [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı. Öğesinden türetilen cmdlet'leri [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı Windows PowerShell çalışma zamanına bağlı değildir. Tüm Microsoft .NET Framework dilinden doğrudan çağrılabilir. Öğesinden türetilen cmdlet'leri [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı Windows PowerShell çalışma zamanına bağlıdır. Bu nedenle, bir çalışma alanı içinde yürütün.

Uygulamanız tüm cmdlet sınıfları, ortak sınıfların olması gerekir. Bu cmdlet sınıfları hakkında daha fazla bilgi için bkz. [cmdlet'i genel bakış](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Cmdlet öznitelik (RC02) belirtin

Windows PowerShell tarafından kabul edilecek bir cmdlet için .NET Framework sınıfı cmdlet'i özniteliği ile donatılmış olmalıdır. Bu öznitelik, cmdlet aşağıdaki özellikleri belirtir.

- Cmdlet tanımlayan fiil-isim çifti.

- Birden fazla parametre kümesine belirtildiğinde, kullanılan varsayılan parametre kümesi. Varsayılan parametre kümesi, Windows PowerShell kullanmak için hangi parametre kümesi olduğunu belirlemede yeterli bilgi olmadığında kullanılır.

- Cmdlet çağrıları destekleyip desteklemediğini belirten [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi. Bu yöntem, cmdlet, sistemde bir değişiklik yaparsa önce kullanıcıya bir onay iletisi görüntüler. Onay istekleri nasıl yapılacağını hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

- Onay iletisi ile ilişkili eylemi etki düzeyine (veya önem derecesi) belirtin. Çoğu durumda, Orta, varsayılan değer kullanılmalıdır. Etki düzeyi kullanıcıya görüntülenen onay istekleri nasıl etkilediği hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

Cmdlet öznitelik bildirmek hakkında daha fazla bilgi için bkz. [CmdletAttribute bildirimi](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>İşleme yöntemi (RC03) girdi geçersiz kıl

Bu cmdlet Windows PowerShell ortamında katılmak aşağıdakilerden en az birini kılmalı *giriş işleme yöntemleri*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) bu yöntem bir kez çağrılır ve ön işleme işlevleri sağlamak için kullanılır.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) bu yöntem, birden çok kez çağrılır ve kayıt kayıt işlevleri sağlamak için kullanılır.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) bu yöntem bir kez çağrılır ve işlem sonrası işlevselliği sağlamak için kullanılır.

### <a name="specify-the-outputtype-attribute-rc04"></a>OutputType özniteliğini (RC04) belirtin

İşlem hattına cmdlet'inize veren .NET Framework türü (Windows PowerShell 2. 0 ' sunulmuştur) OutputType özniteliğini belirtir. Cmdlet'lerinizi çıktı türünü belirterek diğer cmdlet'ler tarafından daha bulunabilir, cmdlet'i tarafından döndürülen nesne olun. Bu öznitelik cmdlet'i sınıfıyla dekorasyon hakkında daha fazla bilgi için bkz. [OutputType özniteliğini bildirimi](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Çıkış nesnelerini (RC05) tanıtıcıları korumuyor.

Cmdlet'inize tanıtıcıları geçirilen nesnelere korurlar değil [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi. Bu nesneler, ardışık düzende sonraki cmdlet'ine geçirilir ya da bunlar bir komut dosyası tarafından kullanılır. Nesneleri tanıtıcıları tutuyorsanız, iki varlık hataya neden her nesne hakimi olursunuz.

### <a name="handle-errors-robustly-rc06"></a>Na hatalarını işleme (RC06)

Bir yönetim ortamı kendiliğinden algılar ve yönetmekte olduğunuz sisteme önemli bir değişiklik yapar. Bu nedenle, cmdlet'leri hataları doğru bir şekilde işlemek önemlidir. Hata kaydı hakkında daha fazla bilgi için bkz: [Windows PowerShell, hata raporlama](./error-reporting-concepts.md).

- Hata bir cmdlet kayıt işlemeye devam etmesini engelleyen bir sonlandırmalı hata olur. Cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) başvuran yöntemi bir [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne. Cmdlet tarafından bir özel durum yakalandı, Windows PowerShell çalışma zamanının kendisi daha az bilgi içeren bir sonlandırma hatası oluşturur.

- Cmdlet işlem hattı (farklı bir işlem tarafından üretilen Örneğin, bir kaydı için) gelen kayıt işlemi sonraki durdurmaz Sonlandırıcı olmayan bir hata için çağırmalıdır [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) başvuran yöntemi bir [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne. Bir sonlandırıcı olmayan hata örneği durdurmak belirli bir işlem başarısız olursa oluşan hatadır. Çağırma [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi, kullanıcının istenen eylemleri tutarlı bir şekilde çalışmasına ve başarısız olan belirli eylemler için bilgileri korumak için sağlar. Cmdlet'inize her bir kayıt olarak bağımsız olarak işlemelidir.

- [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) tarafından başvurulan nesne [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ve [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemleri bir özel durum özellikleri temel alınarak gerektirir. Kullanılacak özel durum belirlerken, .NET Framework tasarım yönergeleri izleyin. Hata anlamsal olarak var olan bir özel durum ile aynı ise, o özel durumu kullanın veya bu özel durumdan türetilen. Aksi takdirde, yeni özel durum ya da doğrudan özel durum hiyerarşisi türetilen [System.Exception](/dotnet/api/System.Exception) türü.

Bir [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesne aynı zamanda hataları kullanıcı grupları bir hata kategorisi gerektirir. Değerini ayarlayarak kategoriye göre hataları görüntüleyebileceği `$ErrorView` CategoryView Kabuk değişkeni. Kategori tarafından tanımlanan [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) sabit listesi.

- Bir cmdlet yeni bir iş parçacığı oluşturur ve bu iş parçacığındaki çalıştırılan kod işlenmemiş bir özel durum oluşturursa, Windows PowerShell hata yakalayamaz ve işlemini sonlandırır.

- Bir nesne kodu işlenmeyen bir özel durum neden olur, yok Edicisi varsa, Windows PowerShell hata yakalayamaz ve işlemini sonlandırır. Bir nesne neden işlenmeyen bir özel durum atma yöntemleri çağırırsa de gerçekleşir.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Bir Windows PowerShell modülü Cmdlet'lerinizi (RC07) dağıtım yapma

Paket ve cmdlet'lerinizi dağıtmak için bir Windows PowerShell modülünü oluşturun. Modüller için destek Windows PowerShell 2.0 sürümünde kullanıma sunulmuştur. Bu cmdlet'lerinizi test ederken faydalı dosyalarını (,) doğrudan ikili modül, cmdlet sınıflar içeren derlemeler kullanabilirsiniz veya cmdlet'i derlemelere başvuran bir modül bildirimi oluşturabilirsiniz. (Ayrıca ek bileşenini varolan derlemeleri modülleri kullanırken ekleyebilirsiniz.) Modüller hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Ayrıca bkz:

[Önemle önerilir geliştirme yönergeleri](./strongly-encouraged-development-guidelines.md)

[Danışmanlık geliştirme yönergeleri](./advisory-development-guidelines.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
