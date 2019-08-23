---
title: Gerekli geliştirme yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: e68e43a91f9139e8d3dc636b5740121515aab2e6
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986669"
---
# <a name="required-development-guidelines"></a>Gerekli Geliştirme Yönergeleri

Cmdlet 'lerinizi yazdığınızda aşağıdaki yönergelerin izlenmesi gerekir. Cmdlet kodunuzu yazmak için cmdlet 'leri ve yönergeleri tasarlamaya yönelik yönergelere ayrılırlar. Bu yönergeleri izlemeden, cmdlet 'larınız başarısız olabilir ve cmdlet 'lerinizi kullandıklarında kullanıcılarınız kötü bir deneyimle karşılaşabilir.

## <a name="in-this-topic"></a>Bu konuda

### <a name="design-guidelines"></a>Tasarım yönergeleri

- [Yalnızca onaylanan fiiller kullan (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet adları: Kullanılamayacak karakterler (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Kullanılamayan parametre adları (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Destek onayı Istekleri (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Etkileşimli oturumlar için destek zorla parametresi (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Belge çıkış nesneleri (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Kod yönergeleri

- [Cmdlet 'ten veya PSCmdlet sınıflarından türet (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Cmdlet özniteliğini belirtin (RC02)](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Bir giriş Işleme yöntemini geçersiz kılma (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [OutputType özniteliğini belirtin (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Çıkış nesnelerine yönelik tutamaçları tutma (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Tanıtıcı hataları robustly (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Cmdlet 'lerinizi dağıtmak için bir Windows PowerShell modülü kullanma (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Tasarım yönergeleri

Cmdlet 'lerinizi ve diğer cmdlet 'leri kullanma arasında tutarlı bir kullanıcı deneyimi sağlamak için cmdlet 'ler tasarlarken aşağıdaki yönergelerin izlenmesi gerekir. Durumunuza uygun bir tasarım kılavuzu bulduğunuzda, benzer yönergeler için kod yönergelerine baktığınızdan emin olun.

### <a name="use-only-approved-verbs-rd01"></a>Yalnızca onaylanan fiiller kullan (RD01)

Cmdlet özniteliğinde belirtilen fiil, Windows PowerShell tarafından sunulan tanınan fiil kümesinden gelmelidir. Yasaklanmış eşanlamlıdan biri olmamalıdır. Cmdlet fiillerini belirtmek için aşağıdaki numaralandırmalar tarafından tanımlanan sabit dizeleri kullanın:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Onaylanan fiil adları hakkında daha fazla bilgi için bkz. [cmdlet fiilleri](./approved-verbs-for-windows-powershell-commands.md).

Kullanıcılar, keşfedilebilir ve beklenen cmdlet adları kümesine sahip olmalıdır. Kullanıcının bir cmdlet 'in ne yaptığını ve sistemin yeteneklerini kolayca bulmasını sağlamak için uygun fiili kullanın. Örneğin, aşağıdaki komut satırı komutu, sistem üzerindeki adları "Başlat" ile başlayan tüm komutların bir listesini alır: `get-command start-*`. Cmdlet 'lerinizi diğer cmdlet 'lerden ayırt etmek için cmdlet 'lerinizin içindeki isimleri kullanın. Ad, işlemin gerçekleştirileceği kaynağı gösterir. İşlemin kendisi, fiil tarafından temsil edilir.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet adları: Kullanılamayacak karakterler (RD02)

Cmdlet 'leri adlandırma sırasında, aşağıdaki özel karakterlerden birini kullanmayın.

|Karakter|Adı|
|---------------|----------|
|#|numara işareti|
|,|virgülle|
|()|ayraçlar|
|{}|küme ayraçları|
|[]|köşeli|
|&|işaretinden|
|-|kısa çizgi **notunun:**  Kısa çizgi, fiil ' dan ayırmak için kullanılabilir, ancak ad içinde veya fiil içinde kullanılamaz.|
|/|eğik çizgi işareti|
|\\| ters eğik çizgi|
|$|dolar işareti|
|^|kar|
|;|noktalı virgülle|
|:|üste|
|"|Çift tırnak işareti|
|'|tek tırnak işareti|
|<>|açılı ayraçlar|
|&#124;|dikey çubuk|
|?|soru işareti|
|@|oturum açma|
|`|geri değer (aksan işareti)|
|*|koyun|
|%|yüzde işareti|
|+|artı işareti|
|=|eşittir işareti|
|~|eşit|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Kullanılamayan parametre adları (RD03)

Windows PowerShell, tüm cmdlet 'ler için parametreler ve belirli durumlarda eklenen ek parametreler için ortak bir parametre kümesi sağlar. Kendi cmdlet 'lerinizi tasarlarken aşağıdaki adları kullanamazsınız: Onaylayın, hata ayıklayın, ErrorAction, ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, whatIf, UseTransaction ve verbose. Bu parametreler hakkında daha fazla bilgi için bkz. [ortak parametre adları](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Destek onayı Istekleri (RD04)

Sistemi değiştiren bir işlem gerçekleştiren cmdlet 'ler için, onay istemek için [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metodunu çağırmalıdır ve özel durumlarda, [şunu çağırır System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi. ( [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemi yalnızca [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi çağrıldıktan sonra çağrılmalıdır.)

Bu çağrıları yapmak için cmdlet cmdlet özniteliğinin `SupportsShouldProcess` anahtar sözcüğünü ayarlayarak doğrulama isteklerini desteklediğini belirtmelidir. Bu özniteliği ayarlama hakkında daha fazla bilgi için bkz. [cmdlet öznitelik bildirimi](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Cmdlet sınıfının cmdlet özniteliği, cmdlet 'in [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemine yapılan çağrıları desteklediğini gösteriyorsa ve cmdlet 'e [çağrıyı yapamazsa, System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi, Kullanıcı sistemi beklenmedik şekilde değiştirebilir.

Herhangi bir sistem değişikliği için [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemini kullanın. Bir Kullanıcı tercihi ve `WhatIf` parametresi [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemini denetler. Buna karşılık, [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) çağrısı, tehlikeli olabilecek değişiklikler için ek bir denetim gerçekleştirir. Bu yöntem herhangi bir Kullanıcı tercihi veya `WhatIf` parametresi tarafından denetlenmez. Cmdlet 'leriniz [System. Management. Automation. cmdlet. shouldcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metodunu çağırırsa, bu iki yönteme yapılan çağrıları `Force` atlayan ve işlemle devam eden bir parametreye sahip olmalıdır. Bu, cmdlet 'inin etkileşimli olmayan betiklerin ve ana bilgisayarlarda kullanılmasına izin verdiğinden önemlidir.

Cmdlet 'larınız bu çağrıları destekliyorsa, Kullanıcı eylemin gerçekten gerçekleştirilip gerçekleştirilmeyeceğini tespit edebilir. Örneğin, [stop-Process](/powershell/module/microsoft.powershell.management/stop-process) cmdlet 'ı, System, Winlogon ve Spoolsv işlemleri de dahil olmak üzere kritik işlemler kümesini durdurmadan önce [System. Management. Automation. cmdlet. shouldcontinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) yöntemini çağırır.

Bu yöntemleri destekleme hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Etkileşimli oturumlar için destek zorla parametresi (RD05)

Cmdlet 'leriniz etkileşimli olarak kullanılıyorsa, her zaman, komut istemleri veya giriş satırları okuma gibi etkileşimli eylemleri geçersiz kılmak için bir zorla parametresi sağlayın. Bu, cmdlet 'inin etkileşimli olmayan betiklerin ve ana bilgisayarlarda kullanılmasına izin verdiğinden önemlidir. Aşağıdaki yöntemler etkileşimli bir ana bilgisayar tarafından uygulanabilir.

- [System. Management. Automation. Host. Pshostuserınterface. Prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. Host. Pshostuserınterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. Host. Pshostuserınterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. Host. Pshostuserınterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. Host. Pshostuserınterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Belge çıkış nesneleri (RD06)

Windows PowerShell, ardışık düzene yazılan nesneleri kullanır. Kullanıcıların her bir cmdlet tarafından döndürülen nesnelerden yararlanması için, döndürülen nesneleri belgeleyerek, döndürülen nesnelerin üyelerinin ne için kullanıldığını belgemalısınız.

## <a name="code-guidelines"></a>Kod yönergeleri

Cmdlet kodu yazılırken aşağıdaki yönergelerin izlenmesi gerekir. Durumunuza uygun bir kod Kılavuzu bulduğunuzda, benzer yönergeler için tasarım yönergelerine baktığınızdan emin olun.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Cmdlet 'ten veya PSCmdlet sınıflarından türet (RC01)

Bir cmdlet 'in [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) veya [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfından türetmeniz gerekir. [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfından türetilen cmdlet 'Ler Windows PowerShell çalışma zamanına bağlı değildir. Bunlar, doğrudan Microsoft .NET Framework dilinden çağrılabilir. [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfından türetilen cmdlet 'Ler Windows PowerShell çalışma zamanına bağlıdır. Bu nedenle, bir runspace içinde yürütülür.

Uyguladığınız tüm cmdlet sınıfları ortak sınıf olmalıdır. Bu cmdlet sınıfları hakkında daha fazla bilgi için bkz. [cmdlet 'e genel bakış](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>Cmdlet özniteliğini belirtin (RC02)

Bir cmdlet 'in Windows PowerShell tarafından tanınması için, .NET Framework sınıfı cmdlet özniteliğiyle birlikte tasarlanmalıdır. Bu öznitelik, cmdlet 'in aşağıdaki özelliklerini belirtir.

- Cmdlet 'ini tanımlayan fiil ve-isim çifti.

- Birden çok parametre kümesi belirtildiğinde kullanılan varsayılan parametre kümesi. Varsayılan parametre kümesi, Windows PowerShell 'in hangi parametre kümesini kullanacağını belirleyen yeterli bilgileri olmadığında kullanılır.

- Cmdlet 'in [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemine çağrıları destekleyip desteklemediğini gösterir. Bu yöntem, cmdlet sistemde değişiklik yapmadan önce kullanıcıya bir onay iletisi görüntüler. Onay isteklerinin nasıl yapılacağı hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

- Onay iletisiyle ilişkili eylemin etki düzeyini (veya önem derecesini) belirtin. Çoğu durumda, varsayılan orta değer kullanılmalıdır. Etki düzeyinin kullanıcıya görüntülenen onay isteklerini nasıl etkilediği hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

Cmdlet özniteliğini bildirme hakkında daha fazla bilgi için bkz. [Cmdtatattribute declaration](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Bir giriş Işleme yöntemini geçersiz kılma (RC03)

Cmdlet 'inin Windows PowerShell ortamına katılması için aşağıdaki *giriş işleme yöntemlerinden*en az birini geçersiz kılması gerekir.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) bu yöntem bir kez adlandırılır ve ön işleme işlevselliği sağlamak için kullanılır.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) bu yöntemin birden çok kez çağrılması ve kayıt kayıt işlevlerini sağlamak için kullanılır.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) bu yöntem bir kez çağrılır ve işlem sonrası işlevselliği sağlamak için kullanılır.

### <a name="specify-the-outputtype-attribute-rc04"></a>OutputType özniteliğini belirtin (RC04)

OutputType özniteliği (Windows PowerShell 2,0 ' de tanıtılan) cmdlet 'inin işlem hattına döndürdüğü .NET Framework türünü belirtir. Cmdlet 'lerinizin çıkış türünü belirterek, cmdlet 'i tarafından döndürülen nesneleri diğer cmdlet 'ler tarafından daha fazla bulunabilir hale getirin. Cmdlet sınıfını Bu öznitelikle dekorasyon hakkında daha fazla bilgi için bkz. [OutputType öznitelik bildirimi](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Çıkış nesnelerine yönelik tutamaçları tutma (RC05)

Cmdlet 'leriniz [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemine geçirilen nesneler için herhangi bir tutamacı saklamamalıdır. Bu nesneler, ardışık düzendeki bir sonraki cmdlet 'e geçirilir veya bir komut dosyası tarafından kullanılır. Nesneler için tutamaçları koruuyorsanız, iki varlık her bir nesneye sahip olur ve bu da hatalara neden olur.

### <a name="handle-errors-robustly-rc06"></a>Tanıtıcı hataları robustly (RC06)

Yönetim ortamı, yönettiğinizde sisteminizde önemli değişiklikleri algılar ve yapar. Bu nedenle, cmdlet 'lerin hataları doğru bir şekilde işlemesi çok önemlidir. Hata kayıtları hakkında daha fazla bilgi için bkz. [Windows PowerShell hata raporlama](./error-reporting-concepts.md).

- Bir hata, bir cmdlet 'in daha fazla kayıt işlemeye devam etmesini engelliyorsa, bu bir sonlandırma hatasıdır. Cmdlet 'i bir [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesnesine başvuran [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodunu çağırmalıdır. Bir özel durum cmdlet tarafından yakalanmadığında, Windows PowerShell çalışma zamanının kendisi daha az bilgi içeren bir sonlandırma hatası oluşturur.

- İşlem hattından gelen bir sonraki kayıt üzerinde (örneğin, farklı bir işlem tarafından oluşturulan bir kayıt) işlemi durdurmayan Sonlandırıcı olmayan bir hata için, cmdlet 'in, [](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) bir [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesnesine başvurur. Sonlandırıcı olmayan bir hata örneği, belirli bir işlem duramazsa oluşan hatadır. [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yönteminin çağrılması, kullanıcının istenen eylemleri sürekli olarak gerçekleştirmesini ve başarısız olan belirli eylemlerin bilgilerini korumasını sağlar. Cmdlet 'lerinizin her kaydı mümkün olduğunca bağımsız olarak işlemesi gerekir.

- [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ve [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemlerinin başvurduğu [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesnesi bir Core için özel durum. Kullanılacak özel durumu belirlerken .NET Framework tasarım kılavuzunu izleyin. Hata anlam, mevcut bir özel durumla anlam içeriyorsa, bu özel durumu kullanın veya bu özel durumdan türetirsiniz. Aksi takdirde, doğrudan [System. Exception](/dotnet/api/System.Exception) türünden yeni bir özel durum veya özel durum hiyerarşisi türetirsiniz.

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) nesnesi ayrıca Kullanıcı için hataları gruplandıran bir hata kategorisi gerektirir. Kullanıcı, `$ErrorView` Shell değişkeninin değerini categoryview olarak ayarlayarak kategoriye göre hataları görüntüleyebilir. Olası kategoriler [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) numaralandırması tarafından tanımlanır.

- Bir cmdlet yeni bir iş parçacığı oluşturursa ve bu iş parçacığında çalışan kod işlenmeyen bir özel durum oluşturursa, Windows PowerShell hatayı yakalamaz ve işlemi sonlandırır.

- Bir nesnenin yıkıcısında işlenmeyen bir özel duruma neden olan kodu varsa, Windows PowerShell hatayı yakalamaz ve işlemi sonlandırır. Bu ayrıca bir nesne işlenmeyen bir özel duruma neden olan Dispose yöntemlerini çağırırsa meydana gelir.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Cmdlet 'lerinizi dağıtmak için bir Windows PowerShell modülü kullanma (RC07)

Cmdlet 'lerinizi paketleyip dağıtmak için bir Windows PowerShell modülü oluşturun. Windows PowerShell 2,0 ' de modül desteği eklenmiştir. Cmdlet sınıflarınızı içeren derlemeleri doğrudan ikili modül dosyaları olarak kullanabilirsiniz (cmdlet 'lerinizi test ederken bu çok yararlı olur) veya cmdlet derlemelerine başvuran bir modül bildirimi oluşturabilirsiniz. (Ayrıca, modüller kullanılırken var olan ek bileşen derlemeleri ekleyebilirsiniz.) Modüller hakkında daha fazla bilgi için bkz. [Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Ayrıca bkz:

[Güçlü teşvik geliştirme yönergeleri](./strongly-encouraged-development-guidelines.md)

[Danışmanlık geliştirme yönergeleri](./advisory-development-guidelines.md)

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)
