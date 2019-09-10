---
title: Windows PowerShell modülünü anlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848072"
---
# <a name="understanding-a-windows-powershell-module"></a>Windows PowerShell Modülünü Anlama

*Modül* , uygun bir birim (genellikle tek bir dizinde kaydedilir) olarak gruplandırılan Ilgili bir Windows PowerShell işlevleri kümesidir. Bir dizi ilgili betik dosyası, derleme ve ilgili kaynakları bir modül olarak tanımlayarak, kodunuzu daha kolay bir şekilde başvurabilir, yükleyebilir, kalıcı hale getirebilirsiniz ve daha kolay bir şekilde paylaşabilirsiniz.

Bir modülün ana amacı, Windows PowerShell kodunun modüle belirlenmesi (IE, yeniden kullanımı ve soyutlama) sağlamaktır. Örneğin, bir modül oluşturmanın en temel yolu, bir Windows PowerShell betiğini. psm1 dosyası olarak kaydetmeniz yeterlidir. Bunun yapılması, betikte bulunan işlevleri ve değişkenleri denetlemenizi (IE, genel veya özel hale getirme) sağlar. Betiği bir. psm1 dosyası olarak kaydetmek, belirli değişkenlerin kapsamını denetlemenize de olanak tanır. Son olarak, komut dosyanızı daha büyük çözümler için yapı taşları olarak düzenlemek, yüklemek ve kullanmak üzere [Install-Module](/powershell/module/PowershellGet/Install-Module) gibi cmdlet 'leri de kullanabilirsiniz.

## <a name="module-components-and-types"></a>Modül bileşenleri ve türleri

Modül dört temel bileşenden oluşur:

1. Kod dosyası bir sıralama-genellikle bir PowerShell betiği veya yönetilen bir cmdlet bütünleştirilmiş kodu.

2. Yukarıdaki kod dosyasına ek derlemeler, yardım dosyaları veya komut dosyaları gibi, başka her şeyi de gerektirebilir.

3. Yukarıdaki dosyaları açıklayan ve yazar ve sürüm bilgileri gibi meta verileri depolayan bir bildirim dosyası.

4. Yukarıdaki içeriğin tümünü içeren ve PowerShell 'in makul bir şekilde bulabileceği bir dizin.

   Bu bileşenlerden hiçbirinin kendilerine göre değil, gerçekten gerekli olduğunu unutmayın. Örneğin, bir modül Teknik olarak yalnızca bir. psm1 dosyasında depolanan bir betik olabilir. Genellikle kurumsal amaçlar için kullanılan bir bildirim dosyası olan hiçbir şey olmayan bir modüle da sahip olabilirsiniz. Ayrıca, dinamik olarak bir modülün oluşturduğu bir komut dosyası yazabilirsiniz ve bu nedenle, aslında içinde herhangi bir şeyi depolamak için bir dizine ihtiyaç kalmaz. Aşağıdaki bölümlerde, bir modülün farklı olası parçalarını karıştırarak ve eşleştirerek alabileceğiniz modül türleri açıklanır.

### <a name="script-modules"></a>Betik modülleri

Adından da anlaşılacağı gibi, bir *komut dosyası modülü* geçerli herhangi bir Windows PowerShell kodu içeren bir dosyadır (. psm1). Betik geliştiricileri ve Yöneticiler, üyeleri işlevleri, değişkenleri ve daha fazlasını içeren modüller oluşturmak için bu modül türünü kullanabilir. Bu noktada, bir komut dosyası modülü yalnızca farklı bir uzantıya sahip bir Windows PowerShell komut dosyası olur ve bu da yöneticilerin üzerinde içeri aktarma, dışarı aktarma ve yönetim işlevlerini kullanmasına olanak sağlar.

Ayrıca, modüldeki veri dosyaları, diğer bağımlı modüller veya çalışma zamanı betikleri gibi diğer kaynakları dahil etmek için bir bildirim dosyası kullanabilirsiniz. Bildirim dosyaları, yazma ve sürüm oluşturma bilgileri gibi meta verileri izlemek için de kullanışlıdır.

Son olarak, dinamik olarak oluşturulmayan diğer tüm modüller gibi bir betik modülünün, PowerShell 'in makul bir şekilde bulabildiği bir klasöre kaydedilmesi gerekir. Genellikle bu, PowerShell modülünün yoludur; Ancak gerekirse modülünüzün yüklendiği yeri açıkça tanımlayabilirsiniz. Daha fazla bilgi için bkz. [PowerShell betik modülü yazma](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>İkili modüller

*İkili modül* , gibi derlenmiş kod içeren bir .NET Framework derlemesidir (. dll) C#. Cmdlet geliştiricileri cmdlet 'leri, sağlayıcıları ve daha fazlasını paylaşmak için bu modül türünü kullanabilir. (Mevcut ek bileşenler, ikili modüller olarak da kullanılabilir.) Bir komut dosyası modülüyle karşılaştırıldığında, ikili bir modül daha hızlı bir şekilde veya Windows PowerShell betiklerine kodun kolay olmayan özelliklerini (çoklu iş parçacığı gibi) kullanmanıza olanak tanır.

Betik modüllerinde olduğu gibi, modülünüzün kullandığı ek kaynakları ve modülünüz hakkındaki meta verileri izlemek için bir bildirim dosyası ekleyebilirsiniz. Benzer şekilde, ikili modülünüzü PowerShell modülü yolu üzerinde bir yere yüklemelisiniz. Daha fazla bilgi için bkz. [PowerShell Ikili modülü nasıl yazılır](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Bildirim modülleri

*Bildirim modülü* , tüm bileşenlerini anlatmak için bir bildirim dosyası kullanan bir modüldür, ancak herhangi bir çekirdek derleme veya betik sıralaması yoktur. (Resmi olarak, bildirim modülü bildirimin `ModuleToProcess` veya `RootModule` öğesinin öğesini boş bırakır.) Ancak, bağımlı derlemeleri yükleme veya belirli ön işleme betiklerini otomatik olarak çalıştırma gibi bir modülün diğer özelliklerini kullanmaya devam edebilirsiniz. Bildirim modülünü, iç içe geçmiş modüller, derlemeler, türler veya biçimler gibi diğer modüllerin kullanacağı kaynakları paketlemek için kullanışlı bir yol olarak da kullanabilirsiniz. Daha fazla bilgi için bkz. [PowerShell modülü bildirimi yazma](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dinamik modüller

*Dinamik modül* bir dosya üzerinden yüklenmeyen veya ' a kaydedilmiş bir modüldür. Bunun yerine, [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet 'i kullanılarak bir komut dosyası tarafından dinamik olarak oluşturulur. Bu tür bir modül, bir betiğin, istek üzerine yüklenmesi veya kalıcı depolamaya kaydedilmesi gerekmeyen bir modül oluşturmasını sağlar. Doğası gereği, dinamik bir modülün kısa süreli olması amaçlanmıştır ve bu nedenle `Get-Module` cmdlet 'i tarafından erişilemez. Benzer şekilde, genellikle modül bildirimlerine gerek kalmaz veya ilgili derlemelerini depolamak için büyük olasılıkla kalıcı klasörlere ihtiyacı yoktur.

## <a name="module-manifests"></a>Modül bildirimleri

*Modül bildirimi* , karma tablo içeren bir. psd1 dosyasıdır. Karma tablodaki anahtarlar ve değerler aşağıdaki işlemleri yapar:

- Modülün içeriğini ve özniteliklerini açıkla.

- Önkoşulları tanımlayın.

- Bileşenlerin nasıl işlendiğini belirleme.

  Bir modül için bildirimler gerekli değildir. Modüller betik dosyaları (. ps1), komut dosyası modül dosyaları (. psm1), bildirim dosyaları (. psd1), biçimlendirme ve tür dosyaları (. ps1xml), cmdlet ve sağlayıcı derlemeleri (. dll), kaynak dosyaları, yardım dosyaları, yerelleştirme dosyaları veya diğer herhangi bir dosya veya kaynak türü için başvuru yapabilir. , modülün bir parçası olarak paketlenmiştir. Uluslararası bir komut dosyası için modül klasörü, bir dizi ileti kataloğu dosyası da içerir. Modül klasörüne bir bildirim dosyası eklerseniz, bildirime başvurarak birden çok dosyaya tek bir birim olarak başvurabilirsiniz.

  Bildirim, aşağıdaki bilgi kategorilerini açıklar:

- Modülle ilgili modül Sürüm numarası, yazar ve açıklama gibi meta veriler.

- Modülün içeri aktarılması için Windows PowerShell sürümü, ortak dil çalışma zamanı (CLR) sürümü ve gerekli modüller gibi Önkoşullar gereklidir.

- İşlenecek betikler, biçimler ve türler gibi işleme yönergeleri.

- Dışarı aktarılacak modül üyeleri, diğer adlar, işlevler, değişkenler ve verilecek cmdlet 'ler gibi kısıtlamalar.

  Daha fazla bilgi için bkz. [PowerShell modülü bildirimi yazma](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Modül depolama ve yükleme

Bir betik, ikili veya bildirim modülünü oluşturduktan sonra, işinizi başkalarının erişebileceği bir konuma kaydedebilirsiniz. Örneğin, modülünüzün Windows PowerShell 'in yüklü olduğu sistem klasöründe depolanması veya bir kullanıcı klasöründe depolanması olabilir.

Genel anlamda, `$ENV:PSModulePath` değişkende depolanan yollardan birini kullanarak modülünüzü nereye yükleyeceğini belirleyebilirsiniz. Bu yollardan birini kullanmak, bir Kullanıcı kendi kodunda bir çağrı yaptığında, PowerShell 'in modülünüzü otomatik olarak bulabileceği ve yükleyebileceği anlamına gelir. Modülünüzü başka bir yerde depoluorsanýz, ' ı çağırdığınızda `Install-Module`modülün konumunu bir parametre olarak geçirerek PowerShell 'e açıkça izin verebilirsiniz.

Ne olursa olsun, klasörün yolu modülün (ModuleBase) *temeli* olarak adlandırılır ve betik, ikili ya da bildirim modülü dosyasının adı modül klasörü adı ile aynı olmalıdır ve aşağıdaki özel durumlarla aynı olmalıdır:

- `New-Module` Cmdlet 'i tarafından oluşturulan Dinamik modüller, cmdlet 'in `Name` parametresi kullanılarak adlandırılabilir.

- `"dynamic_code_module_" + assembly.GetName()`  **`Import-Module` -Assembly** komutuna göre derleme nesnelerinden içeri aktarılan modüller aşağıdaki sözdizimine göre adlandırılır:.

  Daha fazla bilgi için bkz. [PowerShell modülünü yükleme](./installing-a-powershell-module.md) ve [PSModulePath yükleme yolunu değiştirme](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Modül cmdlet 'Leri ve değişkenleri

Aşağıdaki cmdlet 'ler ve değişkenler, modüllerin oluşturulması ve yönetilmesi için Windows PowerShell tarafından sağlanır.

[New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet 'i bu cmdlet yalnızca bellekte bulunan yeni bir dinamik modül oluşturur. Modül bir betik bloğundan oluşturulur ve işlevleri ve değişkenleri gibi, bu üye, oturumda hemen kullanılabilir ve oturum kapatılana kadar kullanılabilir kalır.

[New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 'i bu cmdlet yeni bir modül bildirim (. psd1) dosyası oluşturur, değerlerini doldurur ve bildirim dosyasını belirtilen yola kaydeder. Bu cmdlet, el ile doldurulabilecek bir modül bildirim şablonu oluşturmak için de kullanılabilir.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 'i bu cmdlet geçerli oturuma bir veya daha fazla modül ekler.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 'i bu cmdlet, geçerli oturuma aktarılabilecek olan veya olmayan modüller hakkında bilgi alır.

[Export-modülemeclienttarget](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet 'i bu cmdlet, bir betik modülü (. psm1) dosyasından veya `New-Module` cmdlet kullanılarak oluşturulan dinamik bir modülden dışarı aktarılmış modül üyelerini (cmdlet, işlevler, değişkenler ve diğer adlar gibi) belirtir.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet 'i bu cmdlet geçerli oturumdan modülleri kaldırır.

[Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet 'i bu cmdlet, modül bildirim dosyasında (. psd1) listelenen dosyaların gerçekten belirtilen yollarda mevcut olduğunu doğrulayarak bir modül bildiriminin bir modülün bileşenlerini doğru şekilde açıkladığını doğrular.

$PSScriptRoot bu değişken, komut dosyası modülünün yürütüldüğü dizini içerir. Betiklerin diğer kaynaklara erişmek için modül yolunu kullanmasına olanak sağlar.

$env:P SModulePath bu ortam değişkeni, Windows PowerShell modüllerinin depolandığı dizinlerin bir listesini içerir. Windows PowerShell, modülleri otomatik olarak içeri aktarırken ve modüller için yardım konularını güncelleştirirken bu değişkenin değerini kullanır.

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
