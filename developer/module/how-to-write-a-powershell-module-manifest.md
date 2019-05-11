---
title: Bir PowerShell modül bildirimi yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670288"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>PowerShell Modül Bildirimi Yazma

Bir kez, isteğe bağlı olarak bir modül bildirimi ekleyebilirsiniz, Windows PowerShell modülü yazdınız. Bir modül bildirimi modülle ilgili bilgileri dahil etmek için kullanabileceğiniz bir PowerShell komut dosyası var. Örneğin, yazar açıklayan, kullanıcı ortamının özelleştirmek için betikleri çalıştırma dosyaları (örneğin, iç içe geçmiş modülleri), modüldeki yük türü ve biçimlendirme dosyaları, sistem gereksinimleri tanımlayın ve modül aktarır üyeleri sınırlamak belirtin.

## <a name="creating-a-module-manifest"></a>Bir modül bildirimi oluşturma

A *modül bildirimini* bir modül içeriğini açıklayan ve modül nasıl işleneceğini belirleyen bir Windows PowerShell veri dosyası (.psd1). Bildirim dosyası anahtarları ve değerleri içeren bir karma tablo içeren bir metin dosyasıdır. Bir bildirim dosyası bir modül için modülü aynı adlandırma ve modül dizinini kökündeki yerleştirme bağlayın.

Yalnızca bir tek .psm1 veya ikili derleme içeren basit modülleri için bir modül bildirimi isteğe bağlıdır. Ancak, kodunuzu düzenlemenize yardımcı olacak ve sürüm oluşturma bilgilerini korumak için yararlı oldukları gibi mümkün olduğunda, bir modül bildirimi kullanmanız önerilir. Ayrıca, bir modül bildirimi, genel derleme önbelleğinde yüklü bir derlemeyi vermek için gereklidir. Bir modül bildirimi de güncelleştirilebilir Yardımı özelliği destekleyen modüller için gereklidir. Diğer bir deyişle, güncelleştirilebilir Yardımı kullanan **HelpInfoUri** modülü için güncelleştirilmiş Yardım dosyalarının konumunu içeren Yardım bilgileri (HelpInfo XML) dosyasını bulmak için modül bildirimindeki anahtar. Güncelleştirilebilir Yardımı hakkında daha fazla bilgi için bkz: [güncelleştirilebilir Yardımı destekleme](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Oluşturma ve bir modül bildirimi kullanma

1. Bir modül bildirimi oluşturmak için birkaç seçeneğiniz vardır:

   1. Doğrudan gerekli en düşük miktarda bilgiyi ile karma tablo oluşturma ve modülünüzde aynı ada sahip bir .psd1 dosyaya kaydedin. Bunu yaptıktan sonra dosyayı açın ve uygun değerleri el ile ekleyin.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Veya, çağırma [yeni ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet'i, bir veya daha fazla varsayılan değerleri ile geçirilen parametre olarak. (Bu not yalnızca dosya adını, ancak bir bildirim oluşturmak için gereklidir.) Bu değerlerle açıkça belirtilen sağladığınız tüm bildirim ve uygun bir varsayılan değer içeren rest ile bir modül bildirimi oluşturur.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Son olarak, ayrıca bir boş .psd1 dosyası oluşturabilir ve bu konunun sonundaki şablon dosyaya kopyalayın ve ilgili değerleri doldurun. Yalnızca gerçek bir gereksinimi, dosyanın modülü aynı adlandırıldı emin olmak için bu durumda olacaktır.

2. Ek öğeler varsa dosyasındaki sahip olmasını istediğiniz bildirimi ekleyin.

   Genel olarak bakıldığında, bu büyük olasılıkla, Not Defteri gibi tercih ettiğiniz herhangi bir metin düzenleyicisinde gerçekleştirilir. Ancak bir gerçek komut dosyası veya geliştirme ortamında, PowerShell ISE gibi düzenlemek isteyebilirsiniz, böylece kod içeren bir betik dosyası teknik olarak budur. Yeniden bildirim dosyası tüm öğeleri hariç ModuleVersion numarası isteğe bağlı olduğunu unutmayın.

   Anahtarlar ve değerler sahip olabilir, modül bildiriminde açıklamaları için bkz. **modül bildirimi öğeleri** aşağıda. Parametre açıklamaları, ek bilgi için bkz. [yeni ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet'i.

3. İsteğe bağlı olarak, temel modül bildirim öğeleri tarafından kapsanmayan herhangi bir senaryoya modül bildirimine ek kod eklemeyi seçebilirsiniz.

   Güvenlik kaygıları nedeniyle, bir modül bildirim dosyasında yalnızca küçük bir kısmı kullanılabilir işlemleri PowerShell'i çalıştırın. Genellikle, kullanabileceğiniz **varsa** deyimi, aritmetik ve Karşılaştırma işleçleri ve temel PowerShell veri türleri.

4. Modül bildiriminizi oluşturulduktan sonra (bildirim yok içinde açıklanan tüm yollar düzeltmeniz onaylamak için) bir çağrı ile test edebilirsiniz [Test ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Modül bildiriminizi modülünüzde içeren dizine üst düzey içinde bulunduğundan emin olun.

   Bir sistemin modülünüzde kopyalayın ve bunu içeri PowerShell, modülü içeri aktarmak için modül bildirimini kullanır.

6. İsteğe bağlı olarak, doğrudan modülü bildiriminizi çağrısı ile test edebilirsiniz [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) tarafından bildirimi nokta kaynak belirleme.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Modül bildirim öğeleri

Aşağıdaki tabloda, modül bildiriminde olabilir öğeleri açıklar.

|Öğe|Varsayılan|Açıklama|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Türü: dize|' '|Bu bildirimi ile ilişkilendirilmiş modülü veya ikili modül betiği. PowerShell'in önceki sürümleri bu öğe, ModuleToProcess çağrılır.<br /><br /> Kök modülüyle ilgili olası türleri boş olabilir (hangi hale getirir bu bir **bildirim** Modülü), bir kod modülünün adı (Bu getiren .psm1 bir **betik** Modülü), veya bir ikili (.exe veya .dll, modül adı Bu getiren bir **ikili** Modülü). Bu öğe bir modül bildirimi (.psd1) veya bir betiği (.ps1) adını yerleştirme hataya neden olur.|
|Moduleversıon<br /><br /> Türü: dize|1.0|Bu modül sürüm numarası. Dize [System.Version] için dönüştüremedi olmalıdır. That is, '#.#.#.#.#'. `Import-Module` bulduğu ilk modülü yükler **$psModulePath** adla eşleşen ve en az olarak yüksek bir ModuleVersion sahip `-MinimumVersion` parametresi. Belirli bir sürümünü almak için kullanın`-RequiredVersion` parametresi, bunun yerine.<br /><br /> Örnek: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Türü: dize|Otomatik olarak oluşturulan GUID|Bu modül benzersiz şekilde tanımlamak için kullanılan kimliği. Bir modül GUID tarafından şu anda içeri aktarılamıyor unutmayın.<br /><br /> Örnek: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Yazar<br /><br /> Türü: dize|Yok|Bu modül yazar.<br /><br /> Örnek: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Türü: dize|Bilinmiyor|Şirket veya satıcı Bu modülün.<br /><br /> Örnek: `CompanyName = 'Fabrikam'`|
|Telif Hakkı<br /><br /> Türü: dize|(c) [currentYear] [Yazar]. Tüm hakları saklıdır.|Bu modül için telif hakkı bildirimi.<br /><br /> Örnek: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Açıklama<br /><br /> Türü: dize|' '|Bu modülü tarafından sağlanan işlevselliği açıklaması.<br /><br /> Örnek: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Türü: dize|' '|Bu modülü tarafından gerekli Windows PowerShell altyapısının en düşük sürüm. Geçerli geçerli değerler 1.0, 2.0, 3.0, 4.0 ve 5.0:.<br /><br /> Örnek: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Türü: dize|' '|Modül tarafından gerekli Windows PowerShell ana bilgisayar adını belirtir. Bu ad, Windows PowerShell tarafından sağlanır. Programda bir ana bilgisayar programı adını bulmak için şunu yazın: `$host.name` .<br /><br /> Örnek: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Türü: dize|' '|Bu modülü tarafından gerekli Windows PowerShell ana bilgisayar en düşük sürümü.<br /><br /> Örnek: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Türü: dize|' '|Microsoft .NET Framework'ün bu modülün gerekli en düşük sürümü.<br /><br /> Örnek: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Türü: dize|' '|Bu modülü tarafından gereken ortak dil çalışma zamanı (CLR) minimum sürümü.<br /><br /> Örnek: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Türü: dize|' '|Bu modülü tarafından gerekli İşlemci mimarisi (hiçbiri, X86, Amd64). Geçerli değerler x86, AMD64, IA64 işlemeyen (Bilinmeyen ya da belirtilmemiş).<br /><br /> Örnek: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Türü: [string []]|@()|Bu modül içeri aktarmadan önce genel ortam aktarılmalıdır modüller. Bu, bunlar zaten yüklü sürece listelenen tüm modülleri yükler. (Örneğin, bazı modüller zaten farklı bir modül tarafından yüklenmemiş olabilir.). Kullanarak yüklemek için belirli bir sürümünü belirtmek mümkündür `RequiredVersion` yerine `ModuleVersion`. Kullanırken `ModuleVersion` en az belirtilen sürümü ile kullanılabilir en yeni sürümü yükler.<br /><br /> Örnek: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Örnek: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Türü: [string []]|@()|Bu modülün içeri aktarılması önce yüklenmesi gereken bütünleştirilmiş kodları.<br /><br /> RequiredModules, zaten yüklü değilse RequiredAssemblies PowerShell yükleyecek unutmayın.|
|ScriptsToProcess<br /><br /> Türü: [string []]|@()|Modül içeri aktarıldığında, arayanın kavramak çalışan betik (.ps1) dosyaları. Bu durum veya iç içe geçmiş modülleri, başka bir modül oturum durumu için genel oturum olabilir. Yalnızca bir oturum açma betiği kullanması gerektiği gibi bir ortamı hazırlamak için bu betikleri kullanabilirsiniz.<br /><br /> Bu betikler bildiriminde listelenen modüllerinden birini yüklenmeden önce çalıştırılır.|
|TypesToProcess<br /><br /> Türü: [nesne []]|@()|Bu modülü içeri aktarılırken yüklenecek dosyaları (.ps1xml) yazın.|
|FormatsToProcess<br /><br /> Türü: [nesne []]|@()|Bu modülü içeri aktarılırken yüklenmesini (.ps1xml) dosya biçiminde.|
|NestedModules<br /><br /> Türü: [nesne []]|@()|İç içe geçmiş modüllerini RootModule/ModuleToProcess Belirtilen modül olarak içe aktarmak için modüller.<br /><br /> Bu öğe bir modül adı ekleme için arama benzer `Import-Module` alanından komut dosyası veya bütünleştirilmiş kod kodunuz içinde. İkisi arasındaki temel fark ne bildirim dosyasında burada yüklenmekte olan görmek daha kolay olmasıdır. Bir modül burada yüklenemezse, ayrıca, henüz modülünüzün gerçek yüklenmedi.<br /><br /> Diğer modüllerin ek olarak, burada betik (.ps1) dosyalarını yükleyebilir. Bu dosyalar, kök modül bağlamında çalıştırılır. (Bu kök modülünüzde betikte kaynağını nokta eşdeğerdir.)|
|FunctionsToExport<br /><br /> Tür: Dize|'*'|Modül (joker karakterlere izin) aktarır işlevleri, arayanın oturum durumu için belirtir. Varsayılan olarak, tüm işlevleri dışa aktarılır. Bu anahtar, bir modül tarafından dışa aktarılan işlevleri kısıtlamak için kullanabilirsiniz.<br /><br /> Arayanın oturum durumu, durum veya iç içe geçmiş modülleri, başka bir modül oturum durumu için genel oturum olabilir. FunctionsToExport anahtarı kullanarak bir modül zincirindeki işlevi kısıtlar sürece iç içe modül zinciri, iç içe geçmiş bir modülü tarafından verilen tüm işlevler için genel oturum durumuna dışarı aktarılır.<br /><br /> Bildirim işlevleri için diğer adlar da dışarı aktarır, bu anahtarı işlevleri, diğer adların listelendiği AliasesToExport anahtarı kaldırabilirsiniz, ancak bu anahtar, işlev diğer adları listesine eklenemiyor.|
|CmdletsToExport<br /><br /> Tür: Dize|'*'|Modül (joker karakterlere izin) aktarır cmdlet'ler belirtir. Varsayılan olarak, tüm cmdlet'leri dışarı aktarılır. Bu anahtar, bir modül tarafından dışarı aktarılan cmdlet'leri kısıtlamak için kullanabilirsiniz.<br /><br /> Arayanın oturum durumu, durum veya iç içe geçmiş modülleri, başka bir modül oturum durumu için genel oturum olabilir. İç içe modül zinciri, zincirdeki bir modül cmdlet CmdletsToExport anahtarı kullanarak kısıtlar sürece iç içe geçmiş bir modülü tarafından verilen tüm cmdlet'ler sonuçta genel oturum durumuna dışarı aktarılır.<br /><br /> Bildirim cmdlet'leri için diğer adlar da dışarı aktarır, bu anahtar, diğer adların listelendiği cmdlet'leri AliasesToExport anahtarı kaldırabilirsiniz, ancak bu anahtarı cmdlet diğer adları listesine eklenemiyor.|
|VariablesToExport<br /><br /> Tür: Dize|'*'|Arayanın oturum durumu için Modülü (joker karakterlere izin) aktarır değişkenleri belirtir. Varsayılan olarak, tüm değişkenleri dışarı aktarılır. Bu anahtar, bir modül tarafından dışarı aktarılan değişkenlerin kısıtlamak için kullanabilirsiniz.<br /><br /> Arayanın oturum durumu, durum veya iç içe geçmiş modülleri, başka bir modül oturum durumu için genel oturum olabilir. İç içe modül zinciri, iç içe geçmiş bir modülü tarafından verilen tüm değişkenleri VariablesToExport anahtarı kullanarak değişkeni zincirinde bir modül sınırlar sürece genel oturum durumuna aktarılır.<br /><br /> Bildirim değişkenleri için diğer adlar da dışarı aktarır, bu anahtar, diğer adlar listelenen değişkenleri AliasesToExport anahtarı kaldırabilirsiniz, ancak bu anahtar değişken diğer adları listesine eklenemiyor.|
|AliasesToExport<br /><br /> Tür: Dize|'*'|Modül (joker karakterlere izin) dışarı aktarır. diğer adlar için çağıranın oturum durumunu belirtir. Varsayılan olarak, tüm diğer adlar verilir. Bu anahtar, bir modül tarafından dışarı aktarılan diğer adları kısıtlamak için kullanabilirsiniz.<br /><br /> Arayanın oturum durumu, durum veya iç içe geçmiş modülleri, başka bir modül oturum durumu için genel oturum olabilir. İç içe modül zinciri, zincirdeki bir modül AliasesToExport anahtarı kullanarak diğer kısıtlar sürece iç içe geçmiş bir modülü tarafından verilen tüm diğer adları sonuçta genel oturum durumuna dışarı aktarılır.|
|ModuleList<br /><br /> Türü: [string []]|@()|Bu modül ile paketlenmiştir tüm modülleri belirtir. Bu modüller ModuleName ve GUID anahtarlarla adına (virgülle ayrılmış dizesi) veya bir karma tablosu olarak girilebilir. Karma tablo isteğe bağlı bir ModuleVersion anahtar da olabilir. ModuleList anahtarı, bir modül sayım davranacak şekilde tasarlanmıştır. Bu modüller otomatik olarak işlenmez.|
|FileList<br /><br /> Türü: [string []]|@()|Bu modül ile paketlenen tüm dosyaların listesi. Olarak ModuleList, FileList Envanter Listesi yardımcı olmaktır ve aksi takdirde işlenmedi.|
|PrivateData<br /><br /> Türü: [object]|' '|RootModule/ModuleToProcess anahtarı ile belirtilen kök modülüne geçilmesi gereken herhangi bir özel veri belirtir.|
|HelpInfoURI<br /><br /> Türü: dize|' '|Bu modül HelpInfo URI'si.|
|DefaultCommandPrefix<br /><br /> Türü: dize|' '|Komutlar için varsayılan ön ek, bu modülünden dışarı aktarılan. Önekini kullanarak varsayılan geçersiz kılma `Import-Module` -önek.|

## <a name="sample-module-manifest"></a>Örnek modül bildirimi

Aşağıdaki örnek modül bildirimi, modül bildiriminde anahtarları ve varsayılan değerleri gösterir. Bu örnek kullanılarak oluşturulmuş `New-ModuleManifest` cmdlet'inin Windows PowerShell 3.0. Birden çok modül oluştururken farklı modüller için değiştirilebilir bir bildirim şablonu oluşturmak için bu cmdlet'i kullanabilirsiniz.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
