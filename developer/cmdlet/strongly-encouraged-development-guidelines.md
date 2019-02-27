---
title: Kesinlikle, geliştirme yönergeleri teşvik | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 2bf2447eba07b74f8cc14c9820fc1c1774370b2f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845419"
---
# <a name="strongly-encouraged-development-guidelines"></a>Özellikle Önerilen Geliştirme Yönergeleri

Bu bölümde cmdlet'lerinizi yazdığınızda izlemeniz gereken yönergeleri açıklar. Cmdlet'leri ve cmdlet kodunuzu yazma yönergeleri tasarlama yönergeleri ile ayrılır. Bu yönergeleri her senaryo için geçerli olmadığını fark edebilirsiniz. Cmdlet'lerinizi kullandıklarında ancak, uygulamak ve aşağıdaki yönergeleri izleyin değil, kullanıcılarınızın kötü bir deneyime olabilir.

## <a name="design-guidelines"></a>Tasarım yönergeleri

- [Cmdlet adı (SD01) için belirli bir isim kullanın](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Baş harfleri büyük Cmdlet adları için (SD02) kullanın](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Parametre tasarımı yönergeleri (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [(SD04) kullanıcıya geri bildirim sağlayın](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Bir Cmdlet Yardım dosyası (SD05) oluşturun](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Kod kuralları

- [Kodlama parametreleri (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [İyi tanımlanmış bir ardışık düzen giriş (SC02) desteği](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Tek kayıtları (SC03) işlem hattı yazma](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Cmdlet'leri büyük küçük harf duyarsız olun ve harf korumalıdır (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Tasarım yönergeleri

Cmdlet'lerinizi ve diğer cmdlet'leri kullanarak arasında tutarlı bir kullanıcı deneyimi sağlamak için cmdlet'leri tasarlarken aşağıdaki yönergeleri takip edilmelidir. Durumunuza bir tasarım kılavuzu bulduğunuzda, benzer yönergeleri için kod yönergelere bakmak emin olun.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Cmdlet adı (SD01) için belirli bir isim kullanın

İsimleri, cmdlet adlandırmada kullanılır cmdlet'lerinizi keşfedebilmesi için belirli olması gerekir. Ürün adının kısaltılmış bir sürümü ile "server" gibi genel adlarla önek. Örneğin, bir isim Microsoft SQL Server örneğini çalıştıran bir sunucuya başvuruyorsa, "SQLServer" gibi bir isim kullanın. Belirli isimleri birleşimi ve onaylanmış fiiller kısa bir listesi, hızlı bir şekilde keşfedip cmdlet adları arasında çoğaltma kaçınarak işlevselliği tahmin kullanıcı etkinleştirin.

Kullanıcı deneyimini iyileştirmek için bir cmdlet adı için seçtiğiniz isim tekil olmalıdır. Örneğin, adı kullanmak `Get-Process` yerine **Get işlemleri**. Tüm cmdlet adları için bu kural, bir cmdlet birden fazla öğe hareket oluştuğu sırada izlemek idealdir.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Baş harfleri büyük Cmdlet adları için (SD02) kullanın

Baş harfleri büyük parametre adları için kullanın. Diğer bir deyişle, fiil ve isim içinde kullanılan tüm koşulları ilk harfini büyük harfe Dönüştür. Örneğin, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Parametre tasarımı yönergeleri (SD03)

Bir cmdlet çalışması gereken verileri almak parametreleri gereksinimlerine ve parametreleri, işlem özelliklerini belirlemek için kullanılan bilgileri belirtir. Örneğin, bir cmdlet olabilir bir `Name` veri işlem hattı ve cmdlet alan parametresi olabilir bir `Force` cmdlet bu işlemi gerçekleştirmek için zorlanabilir belirtmek için parametre. Bir cmdlet tanımlayabilirsiniz parametreleri sayısı sınırı yoktur.

#### <a name="use-standard-parameter-names"></a>Standart parametre adları kullanma

Böylece kullanıcı, belirli bir parametre ne anlama geldiğini hızlıca belirleyebilir cmdlet'inize standart parametre adları kullanmanız gerekir. Daha belirli bir ada gerekiyorsa, standart parametre adı kullanın ve ardından diğer ad olarak daha belirgin bir ad belirtin. Örneğin, `Get-Service` cmdlet'inin genel bir ada sahip bir parametre vardır (`Name`) ve daha belirgin bir diğer ad (`ServiceName`). Her iki terim bir parametreyi belirtmek için kullanılabilir.

Parametre adları ve veri türleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre adı ve işlevsellik yönergeleri](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Tekil parametre adları kullanma

Tek bir öğe değeri olan parametreler için çoğul adlar kullanmaktan kaçının. Bu dizileri ele parametreler içeren veya kullanıcı, bir dizi veya yalnızca bir öğe listesini sağlayabilir çünkü listeler.

Çoğul parametre adları, yalnızca parametrenin değeri her zaman birden çok öğe değeri olduğu Böyle durumlarda kullanılmalıdır. Bu gibi durumlarda, birden çok öğe sağlanır ve birden çok öğe belirtilmezse kullanıcıya cmdlet bir uyarı görüntülenmelidir cmdlet doğrulamanız gerekir.

#### <a name="use-pascal-case-for-parameter-names"></a>Parametre adları için baş harfleri büyük kullanın

Baş harfleri büyük parametre adları için kullanın. Diğer bir deyişle, adının ilk harfi dahil olmak üzere, bir parametre adı içindeki her bir sözcüğün ilk harfini büyük harfe Dönüştür. Örneğin, parametre adı `ErrorAction` doğru büyük/küçük harf kullanır. Aşağıdaki parametre adları yanlış büyük/küçük harf kullanın:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Seçenekler listesini alan parametreleri

Bir parametre değeri bir dizi seçenek seçilebilir oluşturmanın iki yolu vardır.

- Bir numaralandırma türü tanımlamak (veya var olan bir numaralandırma türü), geçerli değerleri belirtir. Ardından, numaralandırma türü bir parametre türü oluşturmak için kullanın.

- Ekleme **ValidateSet** özniteliği için parametre bildirimi. Bu özniteliği hakkında daha fazla bilgi için bkz. [ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Standart türler için parametreleri kullanın.

Diğer cmdlet'leriyle tutarlılık sağlamak için mümkün olduğunda ever standart türler için parametreleri kullanın. Farklı parametresi için kullanılan türleri hakkında daha fazla bilgi için bkz. [standart Cmdlet parametre adları ve türleri](./standard-cmdlet-parameter-names-and-types.md). Bu konuda, adlarını ve grupları "etkinlik parametreleri" gibi standart parametreler için .NET Framework türlerini açıklayan çeşitli konulara bağlantılar sağlar.

#### <a name="use-strongly-typed-net-framework-types"></a>Türü kesin belirlenmiş bir .NET Framework türleri kullanın

Parametreleri daha iyi parametre doğrulaması sağlamak için .NET Framework türleri'olarak tanımlanmamalıdır. Örneğin, bir değere bir değerler kümesinden kısıtlanmıştır parametreleri bir numaralandırma türü tanımlanmalıdır. Bir Tekdüzen Kaynak Tanımlayıcısı (URI) değeri desteklemek için parametre olarak tanımlayan bir [System.Uri](/dotnet/api/System.Uri) türü. Temel dize parametreleri tüm serbest biçimli metin özellikleri kaçının.

#### <a name="use-consistent-parameter-types"></a>Uyumlu parametre türleri kullanın

Her zaman aynı parametrenin birden çok cmdlet tarafından kullanıldığında, aynı parametre türü kullanın.  Örneğin, varsa `Process` parametresi bir [System.Int16](/dotnet/api/System.Int16) bir cmdlet için yazıp haline getirmez `Process` parametre başka bir cmdlet için bir [System.Uint16](/dotnet/api/System.UInt16) türü.

#### <a name="parameters-that-take-true-and-false"></a>Alan doğru parametreleri ve False

Parametreniz yalnızca sürerse `true` ve `false`, parametre türü olarak tanımlamanız [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter). Bir anahtar parametresi olarak işlenir `true` ne zaman, belirtilen bir komutu. Bir komut parametresi dahil edilmemişse, Windows PowerShell parametre değerini düşünür `false`. Boole parametreleri tanımlamaz.

Parametreniz 3 değerleri arasında ayırt etmek gerekiyorsa: $true, $false ve "belirsiz", ardından boş değer türünde bir parametre tanımlayın\<bool >.  Cmdlet'i bir nesnenin bir Boolean özelliği değiştirebilirsiniz 3 gereksinimi, "belirsiz" değeri genellikle meydana gelir. Bu durumda "belirsiz" özelliğinin geçerli değeri değiştirilmemesi anlamına gelir.

#### <a name="support-arrays-for-parameters"></a>Dizi parametreleri için destek

Genellikle, kullanıcıların birden çok bağımsız değişkeni aynı işlemi gerçekleştirmeniz gerekir. Bu kullanıcılar, bir cmdlet, böylece kullanıcı, bağımsız değişkenleri parametre olarak bir Windows PowerShell değişken içine geçirebilirsiniz giriş parametresi olarak bir dizi kabul etmelidir. Örneğin, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet dizisi almak için işlemlerin adlarını belirlemek için dizeleri kullanır.
Genellikle, kullanıcıların birden çok bağımsız değişkeni aynı işlemi gerçekleştirmeniz gerekir. Bu kullanıcılar, bir cmdlet, böylece kullanıcı, bağımsız değişkenleri parametre olarak bir Windows PowerShell değişken içine geçirebilirsiniz giriş parametresi olarak bir dizi kabul etmelidir. Örneğin, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet dizisi almak için işlemlerin adlarını belirlemek için dizeleri kullanır.

#### <a name="support-the-passthru-parameter"></a>PassThru parametresini destekler

Varsayılan olarak, birçok cmdlet değiştiren sistem gibi [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet'i, nesneler için "havuzlarını" görür ve bir sonuç yok. Bu cmdlet uygulamalıdır `PassThru` nesneyi döndürmek için cmdlet'i zorlamak için parametre. Zaman `PassThru` parametresi belirtildiğinde, cmdlet çağrısı kullanarak bir nesne döndürür. [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi. Örneğin, aşağıdaki komut, hesaplama işlemi durdurur ve sonuçta elde edilen işlem ardışık düzene geçirir.

```powershell
Stop-Process calc -passthru
```

Çoğu durumda, Ekle, küme ve yeni cmdlet'leri desteklemelidir bir `PassThru` parametresi.

#### <a name="support-parameter-sets"></a>Destek parametre kümeleri

Bir cmdlet, tek amaçlı gerçekleştirmek üzere tasarlanmıştır. Ancak, sık işlemi ya da işlem hedefi tanımlamak için birden fazla yolu yoktur. Örneğin, bir işlemin adını, tanımlayıcısını veya bir işlem nesnesi tarafından tanımlanmış olabilir. Cmdlet'i tüm makul hedeflerine temsillerini desteklemelidir. Normalde, cmdlet (parametre kümeleri adlandırılır) ve birlikte çalışması parametreleri kümelerini belirterek bu gereksinimi karşılar. Tek bir parametre, parametre kümeleri herhangi bir sayıda ait olabilir. Parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).

Parametre kümeleri belirttiğinizde, yalnızca bir parametresi ValueFromPipeline kümesine ayarlayın. Bildirme hakkında daha fazla bilgi için **parametre** özniteliği için bkz: [ParameterAttribute bildirimi](./parameter-attribute-declaration.md).

Parametre kümeleri kullanıldığında varsayılan parametre kümesi tarafından tanımlanan **cmdlet'i** özniteliği. Varsayılan parametre kümesi, etkileşimli bir Windows PowerShell oturumunda kullanılacak en olası parametre içermelidir. Bildirme hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [CmdletAttribute bildirimi](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>(SD04) kullanıcıya geri bildirim sağlayın

Kılavuzları, bu bölümde kullanıcıya geri bildirim sağlamak için kullanın. Bu geri bildirim sisteminizde gerçekleşen dikkat etmeniz ve daha iyi yönetim karar verir.

Çıkış her çağrıdan nasıl ele alınacağını belirtmek bir kullanıcı Windows PowerShell çalışma zamanı sağlar `Write` tercih değişkeni ayarlayarak yöntemi. Kullanıcı, sistem bilgileri ve başka bir eylemde bulunmadan önce kullanıcı sistemi sorgulama olmadığını belirleyen bir değişken görüntülemesi gerekip gerekmediğini belirleyen bir değişken dahil olmak üzere çeşitli tercih değişkenleri ayarlayabilirsiniz.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>WriteWarning WriteVerbose ve WriteDebug yöntemleri destekler

Bir cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) cmdlet istenmeyen bir sonuç olabilir bir işlem gerçekleştirmek üzere olduğunda yöntemi. Örneğin, bir cmdlet cmdlet hakkında bir salt okunur dosyanın üzerine ise bu yöntemi çağırmanız gerekir.

Bir cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) kullanıcı bazı ayrıntılı cmdlet yaptığı gerektirdiğinde yöntemi. Örneğin, cmdlet yazar, cmdlet yaptığı hakkında daha fazla bilgi gerektiren senaryolar vardır görünüyorsa bir cmdlet bu bilgileri çağırmanız gerekir.

Cmdlet çağırmalıdır [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi bir geliştirici ya da ürün destek mühendisi ne cmdlet'i işlemi bozdu anlamanız gerekir. Çağrılacak cmdlet'i için ise gerekli değildir [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi çağıran koddaki [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi olduğundan `Debug` parametre iki bilgi sunar.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress uzun süren işlemler için destek

Cmdlet'i işlemlerini tamamlamak için uzun bir zaman ve arka planda çalıştırılamaz Süren düzenli çağrılar aracılığıyla raporlama ilerleme desteklemelidir [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) yöntemi.

#### <a name="use-the-host-interfaces"></a>Konak arabirimleri kullanır.

Bazen, bir cmdlet yerine bir kullanıcıyla doğrudan kullanarak çeşitli yazma veya yöntemler tarafından desteklenen gerektiğini iletişim kurması [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı. Bu durumda, cmdlet türetilmesi [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) kullanın ve sınıf [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) özelliği. Bu özellik, farklı düzeylerde PromptForChoice istemi ve WriteLine/ReadLine türleri dahil olmak üzere, iletişim türünü destekler. En fazla belirli bir düzeye okuma ve yazma bireysel anahtarları ve arabelleklerinin dağıtılacak şekilde de sağlar.

Bir cmdlet bir grafik kullanıcı arabirimi (GUI) oluşturmak için özel olarak tasarlanmıştır, bu konak kullanarak atlamanızı değil [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) özelliği. GUI oluşturmak için tasarlanmış bir cmdlet örneğidir [çıkış GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet'i.

> [!NOTE]
> Cmdlet'leri kullanmamanız [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Bir Cmdlet Yardım dosyası (SD05) oluşturun

Cmdlet'ini her derleme için cmdlet'i hakkında bilgi içeren bir Help.xml dosyası oluşturun. Bu bilgiler, cmdlet'i, cmdlet'in parametreleri açıklamalarını ve cmdlet kullanım örneklerini açıklamasını içerir.

## <a name="code-guidelines"></a>Kod kuralları

Aşağıdaki yönergeler, cmdlet'lerinizi ve diğer cmdlet'leri kullanarak arasında tutarlı bir kullanıcı deneyimi sağlamak için cmdlet'leri kodlama yaparken gelmelidir. Durumunuza bir kod kılavuz bulduğunuzda, benzer yönergeleri için tasarım kılavuzlarına bakın emin olun.

### <a name="coding-parameters-sc01"></a>Kodlama parametreleri (SC01)

Ortak bir özellik ile belirtilmiş cmdlet'i sınıf bildirerek parametresini tanımlama **parametre** özniteliği. Statik üyeler türetilmiş .NET Framework sınıf cmdlet'i için olmasını parametrelere sahip değildir. Bildirme hakkında daha fazla bilgi için **parametre** özniteliği için bkz: [parametre özniteliği bildirimi](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Windows PowerShell yolları desteği

Windows PowerShell, ad alanlarına erişim normalleştirme mekanizması yoludur. Cmdlet'inde bir parametre için bir Windows PowerShell yol atadığınızda, kullanıcının özel bir "belirli bir yol için bir kısayol görevi gören sürücüsü" tanımlayabilirsiniz. Bir kullanıcı bu tür bir sürücü belirlediğinde, kayıt defterinde veriler gibi depolanan verileri tutarlı bir şekilde kullanılabilir.

Bir dosya veya bir veri kaynağını belirtmek için kullanıcıyı cmdlet'inize izin veriyorsa, türünde bir parametre tanımlamalıdır [System.String](/dotnet/api/System.String). Birden fazla sürücü destekleniyorsa, bir dizi türü olmalıdır. Parametre adı olması gereken `Path`, bir diğer adını ile `PSPath`. Ayrıca, `Path` parametresi joker karakteri desteklemelidir. Joker karakterler için gereken destek, tanımlayan bir `LiteralPath` parametresi.

Bir dosya cmdlet okur veya yazar verileri varsa, cmdlet, Windows PowerShell yolu giriş kabul etmelidir ve cmdlet'ini kullanmanız gerekir [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) Windows çevrilecek özelliği Dosya sistemi tanıdığı yolları uygulamasına PowerShell yolları. Belirli mekanizmaları, aşağıdaki yöntemler şunlardır:

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Cmdlet okuyan veya yazan verilerin yalnızca olup olmadığını sağlayıcı içerik bilgileri dosyası, cmdlet dizeler kümesi kullanmanız gerekir (`Content` üye) okuma ve yazma için. Bu bilgiler elde edilir [System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) özelliği. Bu mekanizmalar, diğer veri depolarına okuma ve yazma veri katılacak şekilde izin verir.

#### <a name="support-wildcard-characters"></a>Joker karakter desteği

Bir cmdlet mümkünse joker karakteri desteklemelidir. (Özellikle bir parametre bir nesneden bir nesneler kümesini tanımlamak için bir dize alır) joker karakterleri desteği bir cmdlet pek çok yerde meydana gelir. Örneğin, örnek **Stop-Proc** cmdlet'inden [StopProc öğretici](./stopproc-tutorial.md) tanımlayan bir `Name` işlem adları temsil eden dizeleri işlemek için parametre. Kullanıcı işlemleri, durdurmak için kolayca belirtmek için bu parametre joker karakterlerini destekler.

Destek için joker karakterler kullanılabilir, bir cmdlet işlemi genellikle bir dizi oluşturur. Bazen, bir kullanıcı aynı anda yalnızca tek bir öğe kullanabilir olduğundan, bir dizi desteklemek için anlamlı yapmaz. Örneğin, [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet'i kullanıcı, tek bir konuma ayarlamak için bir dizi desteklemek ihtiyacı yoktur. Bu örnekte, cmdlet hala joker karakterleri destekler, ancak tek bir konuma çözümleme zorlar.

Joker karakter düzenleri hakkında daha fazla bilgi için bkz: [Cmdlet parametreleri joker karakterleri destekleme](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Nesneleri tanımlama

Bu bölüm, cmdlet'leri ve varolan nesneleri genişletmek için nesnelerini tanımlama yönergeleri içerir.

##### <a name="define-standard-members"></a>Standart üyeleri tanımlama

Bir nesne türü özel Types.ps1xml dosyasında (şablon olarak kullanmak Windows PowerShell Types.ps1xml dosyası) genişletmek için standart üyeleri tanımlar. Standart üyeleri PSStandardMembers ada sahip bir düğüm tarafından tanımlanır. Bu tanımları, diğer cmdlet'ler ve Windows PowerShell çalışma zamanı, nesne ile tutarlı bir şekilde çalışması için izin verir.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Parametre olarak kullanılacak ObjectMembers tanımlayın

Bir nesne bir cmdlet için tasarlıyorsanız, üyelerini doğrudan bu cmdlet'ler parametreler için harita emin olun. Bu eşleme nesnesi işlem hattına kolayca gönderilmesine ve bir cmdlet'ten diğerine geçirilmesi sağlar.

Cmdlet'ler tarafından döndürülen önceden var olan .NET Framework nesnelerini sık betik geliştiricisi veya kullanıcısı tarafından gereken bazı önemli ya da uygun üyeler eksik. Bu eksik üyeleri görüntülemek için ve böylece nesneyi ardışık düzene doğru şekilde geçirilebilir doğru üye adları oluşturmak için özellikle önemli olabilir. Gerekli üyeleri bu belge için özel bir Types.ps1xml dosyası oluşturun. Bu dosya oluşturduğunuzda, aşağıdaki adlandırma kuralını öneririz: *< Your_Product_Name >*. Types.ps1xml.

Örneğin, ekleyebilirsiniz bir `Mode` komut dosyası özelliğini [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) daha net bir dosyanın özniteliklerini görüntülemek için yazın. Ayrıca, ekleyebilirsiniz bir `Count` diğer ad özelliğine [System.Array](/dotnet/api/System.Array) türü, özellik adı tutarlı kullanılmasına izin verin (yerine `Length`).

##### <a name="implement-the-icomparable-interface"></a>IComparable arabirimini uygulama

Uygulama bir [System.IComparable](/dotnet/api/System.IComparable) tüm çıkış nesnelerini arabirimi. Bu, çeşitli sıralama ve analiz cmdlet'lerinde kolayca yöneltilen için çıkış nesneleri sağlar.

##### <a name="update-display-information"></a>Güncelleştirme bilgilerini görüntüle

Bir nesne için görüntüleme beklenen sonuçları sağlamıyorsa, bir özel Oluştur  *\<YourProductName >*. Bu nesne için Format.ps1xml dosyası.

### <a name="support-well-defined-pipeline-input-sc02"></a>İyi tanımlanmış bir ardışık düzen giriş (SC02) desteği

#### <a name="implement-for-the-middle-of-a-pipeline"></a>İçin bir işlem hattı ortasına Uygula

Uygulayan bir işlem hattının ortasından çağrılacak varsayılarak bir cmdlet (diğer bir deyişle, diğer cmdlet'ler kendi giriş oluşturmak veya çıktısını kullanan). Örneğin, varsayabilir `Get-Process` cmdlet'i, veri oluşturduğundan kullanıldığında yalnızca bir işlem hattındaki ilk cmdlet olarak. Bu cmdlet bir işlem hattı ortasını için tasarlandığından, ancak bu cmdlet'i önceki cmdlet'leri veya veri almak için işlemleri belirtmek için işlem hattında sağlar.

#### <a name="support-input-from-the-pipeline"></a>İşlem hattı desteği girişten

Her parametre bir cmdlet için ayarlamak, ardışık düzendeki girişi destekleyen en az bir parametre içerir. Veri ve nesneleri doğru parametre kümesine göndermek ve sonuçları doğrudan bir cmdlet'e göndermeye alınacak kullanıcının ardışık giriş için destek sağlar.

Bir parametreyi, ardışık düzendeki girişi kabul eden **parametre** özniteliği içeren `ValueFromPipeline` anahtar sözcüğü, `ValueFromPipelineByPropertyName` anahtar sözcüğü özniteliği veya bildiriminden iki anahtar. Parametreleri bir parametrede hiçbiri destek ayarlarsanız `ValueFromPipeline` veya `ValueFromPipelineByPropertyName` anahtar sözcükler, cmdlet olamaz atayamayacağına yerleştirilebilir sonra başka bir cmdlet olduğundan herhangi bir işlem hattı girişi göz ardı eder.

#### <a name="support-the-processrecord-method"></a>ProcessRecord yöntemi

Yukarıdaki cmdlet işlem hattındaki tüm kayıtların kabul etmek için cmdlet uygulamalıdır [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi. Windows PowerShell Bu yöntem, birden çok kez kez cmdlet'inize için gönderilen her kayıt için çağırır.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Tek kayıtları (SC03) işlem hattı yazma

Bir cmdlet nesneleri geri döndüğünde, cmdlet nesneleri yazmalısınız böylece, oluşturulan hemen. Cmdlet bunları bunları birleşik bir diziye arabellek için tutmak zorunda değildir. Cmdlet'ler nesneler giriş olarak alır, ardından işlemek, görüntüleme veya işleme ve gecikme olmadan çıkış nesneleri görüntülemek mümkün olacaktır. Çıktı üretir bir cmdlet'i nesneleri teker teker çağırmalıdır [System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi. (Örneğin, temel alınan API çıkış nesnelerinin bir dizisi döndürüldüğünden) toplu olarak çıkış nesnelerini oluşturan bir cmdlet çağırmalıdır [System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject) , ikinci parametresinin bir yöntemle için `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Cmdlet'leri büyük küçük harf duyarsız olun ve harf korumalıdır (SC04)

Varsayılan olarak, Windows PowerShell kendisini büyük/küçük harf duyarlıdır. Ancak, önceden var olan sistemlerle oluşturulmasıyla ilgili olduğu için Windows PowerShell işlemi ve uyumluluk kolaylaştırmak için harfleri doğru yazdığınızdan. Diğer bir deyişle, bir karakterin büyük harf sağlanırsa, Windows PowerShell, büyük harflerle tutar. İyi çalışması sistemler için bu kurala uymayan bir cmdlet gerekir. Mümkünse, büyük küçük harf duyarlı bir şekilde çalışması. Ancak, daha sonra bir komut veya işlem hattı oluşan cmdlet'leri için özgün durum koruma gerekir.

## <a name="see-also"></a>Ayrıca bkz:

[Gerekli geliştirme yönergeleri](./required-development-guidelines.md)

[Danışmanlık geliştirme yönergeleri](./advisory-development-guidelines.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
