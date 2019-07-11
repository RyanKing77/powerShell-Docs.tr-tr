---
title: Windows PowerShell Programcı&#39;s Kılavuzu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734879"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell Programcı&#39;s Kılavuzu

Bu Programcı Kılavuzu geliştiriciler ve sistem yöneticileri için bir komut satırı yönetim ortamı sağlama konusunda ilgilendiğiniz hedef alır. Windows PowerShell, Windows PowerShell, işin çoğunu sizin için gerçekleştirmesini istemeniz verirken .NET nesnelerini kullanıma sunma yönetimi komutları oluşturmak basit bir yol sağlar.

Geleneksel komut geliştirme, bir parametre ayrıştırıcı, bir parametre bağlayıcı, filtreler ve her komutu tarafından kullanıma sunulan tüm işlevleri yazmak için gereklidir. Windows PowerShell komutları yazma kolaylaştırmak için aşağıdakileri sağlar:

- Bir güçlü Windows PowerShell çalışma zamanı (yürütme altyapısı) ile kendi Ayrıştırıcı ve komut parametreleri otomatik olarak bağlama için bir mekanizma.

- Biçimlendirme ve komut satırı Yorumlayıcı (CLI) kullanarak komutu sonuçları görüntülemek için yardımcı programlar.

- Depolanan verilere erişmek kolaylaştıran yüksek düzeyde (Windows PowerShell sağlayıcısı) aracılığıyla işlevsellik için destek.

  Az maliyetle zengin komut ya da yönetici tam bir komut satırı deneyimi sunacaktır komut kümesini bir .NET nesnesini temsil edebilir.

  Sonraki bölümde, koşulları ve Windows PowerShell temel kavramları kapsar. Bu kavramlar ve terimler geliştirme başlatmadan önce tanıyın.

## <a name="about-windows-powershell"></a>Windows PowerShell Hakkında

Windows PowerShell komutları kullanabileceğiniz çeşitli geliştirme tanımlar. Bu komutlar şunlardır: işlevleri, filtreler, betikleri, diğer adlar ve yürütülebilir dosyalar (uygulamalar). Bu kılavuzda ele alınan ana komut "cmdlet'i" adlı basit ve küçük bir komut türüdür. Windows PowerShell cmdlet'leri kümesi sağlar ve tam ortamınıza uyacak şekilde özelleştirme cmdlet'ini destekler. Komut zincirlerini kullanarak cmdlet'leri, çalıştığı gibi Windows PowerShell çalışma zamanı komutu tüm türleri işler.

Komutları ek olarak, Windows PowerShell cmdlet'leri kullanılabilir belirli kümesini oluşturan çeşitli özelleştirilebilir Windows PowerShell sağlayıcılarını destekler. Kabuğu Windows PowerShell tarafından sağlanan ana bilgisayar uygulaması (Windows PowerShell.exe) içinde çalışır, ancak bir özel konak uygulamasından özel gereksinimleri karşılamak için geliştirebilirsiniz eşit olarak erişilebilir. Daha fazla bilgi için [nasıl Windows PowerShell çalışır](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell Cmdlet'leri

Bir cmdlet Windows PowerShell ortamında kullanılan basit bir komuttur. Komut satırında sağlanan Otomasyon betikleri bağlamında bu cmdlet'ler Windows PowerShell çalışma zamanı çağırır ve Windows PowerShell çalışma zamanı de bunları programlı olarak Windows PowerShell API'leri aracılığıyla çağırır.

Cmdlet'ler hakkında daha fazla bilgi için bkz. [yazma bir Windows PowerShell cmdlet'i](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell sağlayıcıları

Yönetim görevleri gerçekleştirdiği kullanıcı bir veri deposuna (örneğin, dosya sistemi, Windows kayıt defteri veya bir sertifika deposu) depolanan verileri incelemeniz gerekebilir. Bu işlemleri daha kolay hale getirmek için Windows PowerShell, Windows kayıt defteri gibi bir özel veri deposuna erişmek için kullanılan bir Windows PowerShell sağlayıcısı adlı bir modül tanımlar. Her bir sağlayıcı veri deposunda simetrik bir görünümünü kullanıcıya vermek, ilgili cmdlet'ler kümesi destekler.

Windows PowerShell, Windows PowerShell sağlayıcıları birkaç varsayılan sağlar. Örneğin, kayıt defteri sağlayıcısı, gezinti ve Windows kayıt defteri düzenlemesini destekler. Kayıt defteri anahtarlarını öğeleri olarak temsil edilir ve kayıt defteri değerleri, özellik olarak kabul edilir.

Kullanıcının erişmesi gereken bir veri deposu, kullanıma, kendi Windows PowerShell sağlayıcısı yazmak açıklandığı gibi ihtiyacınız olabilecek [oluşturma Windows PowerShell sağlayıcıları](./how-to-create-a-windows-powershell-provider.md). Daha fazla bilgi aboutWindows için PowerShell sağlayıcıları, bkz: [nasıl Windows PowerShell çalışır](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Ana bilgisayar uygulaması

Windows PowerShell kullanıcıyla etkileşim kurar ve bir konsol penceresi kullanarak Windows PowerShell çalışma zamanı uygulamasını barındıran bir konsol uygulamasıdır varsayılan konak uygulama powershell.exe içerir.

Nadiren özelleştirme karşın, kendi ana bilgisayar uygulaması Windows PowerShell için yazma gerekecektir. Varsayılan konak uygulama tarafından sağlanan arabirimi daha zengin bir GUI arabirimi için bir gereksinimi varsa, kendi uygulamanızın ihtiyaç duyabileceğiniz bir durumdur. Komut satırında, GUI dayandırırken özel bir uygulama da isteyebilirsiniz. Daha fazla bilgi için [bir Windows PowerShell ana bilgisayar uygulaması oluşturma işlemini](/powershell/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Windows PowerShell çalışma zamanı

Windows PowerShell çalışma zamanı komut işleme uygulayan bir yürütme altyapısıdır. Bu konak uygulama ve Windows PowerShell komutlarını ve sağlayıcılar arasında arabirim sağlayan sınıflar içerir. Windows PowerShell çalışma zamanı içinde kabuk ve komutları yürütmek işletimsel ortamı olan geçerli Windows PowerShell oturumu için bir çalışma nesnesi olarak uygulanır. İşlem ayrıntıları için bkz. [nasıl Windows PowerShell çalışır](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Windows PowerShell dil

Windows PowerShell dil komut dosyası işlevleri ve komutları çağrılacak mekanizmaları sağlar. Tam komut dosyası için Windows PowerShell ile Windows PowerShell dil başvurusu sevk bilgi.

### <a name="extended-type-system-ets"></a>Genişletilmiş tür sistemi (ETS)

Windows PowerShell, .NET gibi farklı nesneleri ve XML nesneleri çeşitli erişim sağlar. Sonuç olarak, tüm nesne türleri için ortak bir Özet sunmak için shell, genişletilmiş tür sistemi (ETS) kullanır. Çoğu ETS işlevselliği kullanıcıya şeffaf olan ancak betik ya da .NET Geliştirici aşağıdaki amaçlarla kullanır:

- Belirli nesne üyelerin bir alt kümesini görüntüleme. Windows PowerShell, belirli nesne türlerinden "uyumlu" bir görünümünü sağlar.

- Üye, varolan nesnelere ekleme.

- Erişim nesneleri serileştirilir.

- Yazma nesneleri özelleştirilmiş.

  ETS kullanarak esnek yeni "türler", oluşturabileceğiniz Windows PowerShell dili ile uyumludur. Bir .NET geliştiricisi olarak, bir nesne olmaması halinde belirlemek için Windows PowerShell dil komut dosyası, örneğin geçerli olduğundan aynı semantiği kullanarak nesnelerle çalışmayı mümkün `true`.

  Madde işaretleri ve Windows PowerShell nesnelerin nasıl kullandığı hakkında daha fazla bilgi için bkz. [Windows PowerShell nesnesi kavramları](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Windows PowerShell için programlama

Windows PowerShell komutları, sağlayıcıları ve .NET Framework kullanarak diğer program modüllerinin kendi kodunu tanımlar. Bu aracı çalıştırmak için bu kılavuzda sağlanan örnekleri bilinse de, Microsoft Visual Studio kullanımı için Windows PowerShell için özelleştirilmiş modülleri oluştururken sınırlandırılmıştır değil. Sınıf devralma ve öznitelikleri kullanılmasını desteklediği dilediğiniz .NET dilini kullanabilirsiniz. Bazı durumlarda, Windows PowerShell API'lerini, genel türler erişebilmesi için programlama dilini gerektirir.

## <a name="programmers-reference"></a>Programcı Başvurusu

Windows PowerShell için geliştirirken işinize yarayacak [Windows PowerShell SDK'sı](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Windows PowerShell kullanmaya başlama

Windows PowerShell Kabuk kullanmaya başlamak hakkında daha fazla bilgi için bkz. [Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Windows PowerShell ile birlikte gönderilir. Hızlı Başvuru üç kat belgesini de cmdlet'ini kullanmak için bir öncü olarak sağlanır.

## <a name="contents-of-this-guide"></a>Bu kılavuzun içeriği

|Konu|Tanım|
|-----------|----------------|
|[Bir Windows PowerShell sağlayıcısı oluşturma](./how-to-create-a-windows-powershell-provider.md)|Bu bölümde, bir Windows PowerShell için Windows PowerShell sağlayıcısını nasıl oluşturulduğu açıklanır.|
|[Bir Windows PowerShell ana bilgisayar uygulaması oluşturma](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|Bu bölümde, bir çalışma alanı işleyen bir ana bilgisayar uygulaması yazma ve kendi özel ana bilgisayar uygulayan bir ana bilgisayar uygulaması yazma açıklanmaktadır.|
|[Bir Windows PowerShell ek bileşeni oluşturma](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Bu bölümde, bir derlemede tüm cmdlet'leri ve sağlayıcıları kaydetmek için kullanılan bir ek bileşeni oluşturma ve bir özel ek bileşenini oluşturma açıklanmaktadır.|
|[Bir konsol Kabuk oluşturma](./how-to-create-a-console-shell.md)|Bu bölümde, Genişletilebilir değil bir konsol Kabuk oluşturmayı açıklar.|
|[Windows PowerShell kavramlarını](./windows-powershell-concepts.md)|Bu bölüm, Windows PowerShell bir geliştiricinin bakış açısından anlamanıza yardımcı olacak kavramsal bilgiler içerir.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
