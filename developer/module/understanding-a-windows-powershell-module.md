---
title: Bir Windows PowerShell modülü anlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851530"
---
# <a name="understanding-a-windows-powershell-module"></a>Windows PowerShell Modülünü Anlama

A *Modülü* (genellikle tek bir dizinde kaydedilir) uygun bir birim olarak birlikte gruplandırılmış ilgili Windows PowerShell işlevleri kümesidir. Bir dizi ilgili komut dosyaları, derlemeleri ve ilgili kaynakları bir modül olarak tanımlayarak, başvuru, yükleme, kalıcı hale getirmek ve kodunuzu, başka bir duruma göre çok daha kolay paylaşın.

Modül ana amacı, Windows PowerShell kodu (örneğin, yeniden ve soyutlama) uyumluluğuna izin vermektir. Örneğin, bir modül oluşturmanın en temel yolu yalnızca bir Windows PowerShell Betiği bir .psm1 dosyayı farklı kaydet sağlamaktır. Bunun yapılması kadar denetim (örneğin, genel veya özel) işlevler ve değişkenler betiğinde yer sağlar. Betik bir .psm1 dosyası olarak kaydederek de belirli değişkenlerin kapsam denetlemenizi sağlar. Son olarak da cmdlet'ler gibi kullanabilirsiniz [Install-Module](/powershell/module/PowershellGet/Install-Module) düzenlemek için yükleme ve kodunuzu daha büyük çözümler için yapı taşı olarak kullanın.

## <a name="module-components-and-types"></a>Modül bileşenleri ve türleri

Bir modül dört temel bileşenlerden oluşur:

1. Bazı kod dosyasının - genellikle bir PowerShell Betiği veya yönetilen cmdlet derleme sıralayın.

2. Yukarıdaki kod dosya olabilir herhangi ek derlemeler gibi dosyalar veya betikler yardımcı.

3. Yazar ve sürüm bilgileri gibi metadada depolar yanı sıra yukarıdaki dosyalarını açıklar bir bildirim dosyası...

4. Yukarıdaki içeriğin tümünü içerir ve bulunduğu bir dizin burada PowerShell makul bir şekilde bulabilir.

   Bu bileşenler, kendileri tarafından hiçbiri gerçekten gerekli olduğunu unutmayın. Örneğin, bir modül yalnızca bir .psm1 dosyasında depolanan bir betik teknik olabilir. Esas olarak kuruluş amacıyla kullanılan bir bildirim dosyası, ancak hiçbir şey bir modülü de olabilir. Ayrıca, dinamik olarak bir modül oluşturur ve bu nedenle gerçekten her şeyi depolamak için bir dizin gerekmiyor bir betik yazabilirsiniz. Aşağıdaki bölümlerde karıştırma ve modül olası farklı bölümlerini birlikte eşleşen alabilirsiniz modülleri türleri açıklanmaktadır.

### <a name="script-modules"></a>Betik modülleri

Adından da anlaşılacağı gibi bir *betik modülündeki* herhangi bir geçerli Windows PowerShell kodu içeren bir dosya (.psm1). Betik geliştiriciler ve Yöneticiler bu tür bir modül İşlevler, değişkenler ve diğer üyeleri dahil modüller oluşturmak için kullanabilirsiniz. Yaklaşımının temelindeki üzerinde içeri aktarma, dışarı aktarma ve yönetim işlevlerini kullanma olanağı sağlayan başka bir uzantı yalnızca Windows PowerShell betiğiyle bir betik modüldür.

Ayrıca, modülünüzde veri dosyaları, diğer bağımlı modülleri veya çalışma zamanı betikler gibi diğer kaynaklar dahil edilecek bildirim dosyası kullanabilirsiniz. Bildirim dosyaları izlemek için geliştirme ve sürüm bilgileri gibi meta veriler için kullanışlıdır.

Son olarak, dinamik olarak oluşturulan değil, başka bir modül gibi bir betik modülü PowerShell makul bulabilecek bir klasörde kaydedilmesi gerekir. Genellikle, bu PowerShell modülünü yoludur; Ancak, gerekirse, açıkça modülünüzde yüklendiği tanımlayabilirsiniz. Daha fazla bilgi için [nasıl yazılacağını PowerShell betik modülündeki](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>İkili modülleri

A *ikili modül* gibi derlenmiş kodu içeren bir .NET Framework derlemesi (.dll) C#. Cmdlet geliştiriciler bu tür bir modülü cmdlet'leri, sağlayıcıları ve daha fazlasını paylaşmak için kullanabilirsiniz. (Mevcut eklentileri ikili modülleri olarak da kullanılabilir.) Bir betik modülüne karşılaştırıldığında, ikili bir modül daha hızlı veya özelliklerine cmdlet'leri oluşturmanıza olanak tanır (gibi çoklu iş parçacığı kullanımı) için Windows PowerShell betikleri kodda kolay değildir.

Betik modülleri ile modülünüzde kullanan ek kaynaklar açıklanır ve modülünüzde hakkındaki meta verileri izlemek için bir bildirim dosyası dahil edebilirsiniz. Benzer şekilde, bir klasörde bir PowerShell modülü yol boyunca büyük olasılıkla ikili modülünüzde yüklemelisiniz. Daha fazla bilgi için bkz. nasıl [ikili bir PowerShell modülü yazma](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Modüller listesi

A *bildirim Modülü* tüm bileşenlerini açıklamak için bir bildirim dosyası kullanır, ancak komut çekirdek derleme veya herhangi bir tür olmayan bir modüldür. (Resmi olarak, bir bildirim modül bırakır `ModuleToProcess` veya `RootModule` boş bildirimin öğesi.) Ancak, bir modülün bağımlı derlemeleri yüklemek veya otomatik olarak belirli ön işleme betikleri çalıştırma olanağı gibi diğer özellikleri kullanmaya devam edebilirsiniz. Bir bildirim modülü, iç içe geçmiş modülleri, derlemeler, türler veya biçimleri gibi diğer modüllerin kullanacağı kaynakları paketlemek için kullanışlı bir yol olarak da kullanabilirsiniz. Daha fazla bilgi için [bildirim PowerShell modülü yazma](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dinamik modüller

A *dinamik modül* bir modülün gelen yüklü değil veya bir dosyaya kaydedilebilir. Bunun yerine, bir komut dosyası tarafından dinamik olarak oluşturuldukları kullanarak [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet'i. Bu modül türü yüklenemedi veya kalıcı depolama alanına kaydedildi gerekmez isteğe bağlı bir modülü oluşturmak bir betik sağlar. Doğası, dinamik modül kısa süreli olması beklenir ve tarafından erişilemez `Get-Module` cmdlet'i. Benzer şekilde, genellikle modül bildirimleri gerekmez ya da bunların büyük olasılıkla kendi ilgili derlemeleri depolamak için kalıcı klasörleri gerekir.

## <a name="module-manifests"></a>Modül bildirimleri

A *modül bildirimini* bir karma tablo içeren bir .psd1 dosyasıdır. Anahtarlar ve değerler karma tablosundaki şunları yapın:

- Modül öznitelikleri ve içeriği açıklanmaktadır.

- Önkoşulları tanımlayın.

- Bileşenlerin nasıl işleneceğini belirler.

  Bildirimler, bir modül için gerekli değildir. Modülleri komut dosyalarına (.ps1) başvuran, biçimlendirme Modülü (.psm1), bildirim dosyası (.psd1) komut dosyalarını ve dosyaları (.ps1xml), cmdlet ve sağlayıcı derlemeleri (.dll), kaynak dosyaları, Yardım dosyaları, yerelleştirme dosyaları veya başka türde bir dosya veya kaynak yazın, Modülün bir parçası sağlanır. Uluslararası hale getirilmiş bir betik için modül klasöründe bir dizi ileti katalog dosyaları da içerir. Modül klasörü için bir bildirim dosyası eklerseniz, tek bir birim olarak birden çok dosya bildirim başvurarak başvurabilirsiniz.

  Bildirimi bilgi aşağıdaki kategorileri açıklanmaktadır:

- Modül, modül sürüm numarasını, yazarı ve açıklaması gibi hakkındaki meta verileri.

- Modülü Windows PowerShell sürümü, ortak dil çalışma zamanı (CLR) sürümünü ve gerekli modülleri içeri aktarmak için gerekli Önkoşullar.

- İşlenecek işleme yönergeleri, komut dosyaları, biçimleri ve türleri gibi.

- Dışarı aktarılacak modülü, diğer adlar, İşlevler, değişkenler ve cmdlet'leri dışarı aktarmak için gibi kısıtlamalar üyeleri üzerinde.

  Daha fazla bilgi için [bildirim PowerShell modülü yazma](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Depolama ve bir modülünü yükleme

Oluşturduktan sonra bir komut dosyası, ikili veya bildirim modülü, başkalarının da erişebilir, iş bir konuma kaydedebilirsiniz. Örneğin, burada Windows PowerShell yüklü değil veya bir kullanıcı klasöründe depolanan sistem klasörü modülünüzde depolanabilir.

Genel olarak bakıldığında, modülünüzde depolanan yollardan biri kullanılarak yüklediğiniz belirleyebilir `$ENV:PSModulePath` değişkeni. Bu yollardan kullanarak PowerShell otomatik olarak bulabilir ve bir kullanıcı kendi kodunda bir çağrı yaptığında, modülü, anlamına gelir. Modülünüzün başka bir yerde depolayın, modülünüzde konumunu bir parametre olarak geçirerek çağırdığınızda bilmeniz PowerShell açıkça sağlayabilirsiniz `Install-Module`.

Ne olursa olsun, klasör yolu olarak adlandırılır *temel* ' % s'Modülü (ModuleBase) ve betik adını, ikili veya bildirim modül dosyası aşağıdaki istisnalarla modülü klasör adı ile aynı olması gerekir:

- Tarafından oluşturulan dinamik modüller `New-Module` cmdlet'i adı kullanılarak `Name` cmdlet parametresi.

- Bütünleştirilmiş kod nesneleriyle aynı tarafından içeri aktarılan modülleri  **`Import-Module` -derleme** komutu aşağıdaki söz dizimini göre adlandırılır: `"dynamic_code_module_" + assembly.GetName()`.

  Daha fazla bilgi için [PowerShell modülünü yükleme](./installing-a-powershell-module.md) ve [PSModulePath yükleme yolunu değiştirmek](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Modülü cmdlet'lerini ve değişkenler

Aşağıdaki cmdlet'ler ve değişkenleri oluşturulmasını ve yönetimini modülleri için Windows PowerShell tarafından sağlanır.

[Yeni modül](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet'i Bu cmdlet oluşturur var. yeni bir dinamik modül yalnızca bellekte. Modül bir betik bloğundan oluşturulur ve dışarı aktarılan üyeleri, İşlevler ve değişkenler gibi oturumu hemen kullanılabilir ve oturum kapatılana kadar kullanılabilir durumda kalır.

[Yeni ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet'i Bu cmdlet yeni bir modül bildirimi (.psd1) dosyası oluşturur, değerleri doldurur ve bildirim dosyası için belirtilen yol kaydeder. Bu cmdlet, el ile doldurulacak bir modül bildirim şablonu oluşturmak için de kullanılabilir.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet'i Bu cmdlet bir veya daha fazla modülü geçerli oturuma ekler.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet'i Bu cmdlet, yapıldı veya geçerli oturuma aktarılabilir modülleri hakkında bilgi alır.

[Dışarı aktarma ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet'i Bu cmdlet belirtir (örneğin, cmdlet'leri, İşlevler, değişkenler ve diğer adları) betik Modülü (.psm1) veya dinamik modül kullanılarak oluşturulan dışarı modülü üyeleri `New-Module` cmdlet'i.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet'i Bu cmdlet modülleri geçerli oturumdan kaldırır.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet'i Bu cmdlet, bir modül bildirimi doğru bileşenleri bir modülün modül bildirim dosyası (.psd1) içinde listelenen dosyaların gerçekten belirtilen yolda mevcut olduğunu doğrulayarak açıklayan doğrular.

$PSScriptRoot betik modülündeki yürütülmekte olduğu dizin Bu değişken içeriyor. Bu modül yolu diğer kaynaklarına erişmek için kullanılacak komut dosyaları sağlar.

$env: PSModulePath bu ortam değişkeni, hangi Windows PowerShell modülleri depolanır dizinlerin bir listesini içerir. Windows PowerShell modülleri için Yardım konularını güncelleştiriliyor ve modüller otomatik olarak içeri bu değişkenin değerini kullanır.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)
