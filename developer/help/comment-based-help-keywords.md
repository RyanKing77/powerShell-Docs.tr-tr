---
title: Açıklama tabanlı Yardım anahtar sözcükleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301525"
---
# <a name="comment-based-help-keywords"></a>Yorum Tabanlı Yardım Anahtar Kelimeleri

Bu konu, listeler ve açıklama tabanlı Yardım anahtar kelimeleri açıklar.

## <a name="keywords-in-comment-based-help"></a>Açıklama tabanlı Yardım anahtar sözcükleri

Geçerli açıklama tabanlı Yardım anahtar sözcükleri aşağıda verilmiştir. Bunlar, genellikle birlikte bunların kullanım amacını Yardım konusunun göründükleri sırayla listelenir. Bu anahtar sözcükler, açıklama tabanlı Yardım herhangi bir sırada görünebilir ve büyük küçük harfe duyarlı değildir.

Unutmayın `.ExternalHelp` anahtar sözcüğü diğer tüm açıklama tabanlı Yardım anahtar göre önceliklidir. Zaman `.ExternalHelp` var, [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet'i bile anahtar değeri ile eşleşen bir Yardım dosyası bulamadığında açıklama tabanlı Yardım görüntülemez.

`.Synopsis` İşlev veya komut dosyasını kısa bir açıklaması. Bu anahtar sözcüğü her konuda yalnızca bir kez kullanılabilir.

`.Description` İşlev veya betiği ayrıntılı bir açıklaması. Bu anahtar sözcüğü her konuda yalnızca bir kez kullanılabilir.

`.Parameter` *\<Parametre-adı >* parametre açıklaması. Dahil edebilirsiniz bir `.Parameter` anahtar sözcüğü her bir parametreye işlev veya betiği.

`.Parameter` Anahtar sözcük, açıklama bloğu herhangi bir sırada ancak hangi parametreleri görünen sırada görünebilir `Param` bildirimi veya işlevin bildiriminin parametreleri Yardım konusundaki görüntülenme sırasını belirler. Yardım konusundaki parametrelerinin sırasını değiştirmek için parametrelerin sırasını değiştirme `Param` bildirimi veya işlevin bildirimi.

Parametre açıklaması bir açıklama girerek belirtebilirsiniz `Param` deyiminden hemen önce parametre değişken adı. Her ikisi de kullanırsanız, bir `Param` deyimi açıklama ve `.Parameter` anahtar sözcüğü, ilişkili açıklama `.Parameter` anahtar sözcüğü kullanılır ve `Param` deyimi açıklama göz ardı edilir.

`.Example` İşlev veya betiği, ardından isteğe bağlı olarak örnek çıktı ve bir açıklama kullanan bir örnek komutu. Bu anahtar sözcüğü her örnek için yineleyin.

`.Inputs` Microsoft .NET Framework türleri işlev veya betiği ayrıştırılabilir nesne. Giriş nesnelerin bir açıklama da ekleyebilirsiniz.

`.Outputs` .NET Framework türü nesnelerin cmdlet döndürür. Döndürülen nesnelerin bir açıklama da ekleyebilirsiniz.

`.Notes` İşlev veya betiği hakkında ek bilgi.

`.Link` İlgili konu adı. Bu anahtar sözcük, ilgili her konuda için yineleyin. Bu içerik Yardım konusunun ilgili bağlantılar bölümünde görüntülenir.

`.Link` Anahtar sözcüğü içeriği de Tekdüzen Kaynak Tanımlayıcısı (URI) için aynı Yardım konusunun çevrimiçi sürümünü içerir. Kullandığınız çevrimiçi sürümünü açar `Online` Get-Help parametresi. URI, "http" veya "https" ile başlamalıdır.

`.Component` Teknoloji veya işlev veya betiği kullanan veya ilişkili özellik. Get-Help komutunu içerdiğinde, bu içerik görünür `Component` Get-Help parametresi.

`.Role` Kullanıcı rolü için Yardım konusu. Get-Help komutunu içerdiğinde, bu içerik görünür `Role` Get-Help parametresi.

`.Functionality` Kullanım amacı, işlev. Get-Help komutunu içerdiğinde, bu içerik görünür `Functionality` Get-Help parametresi.

`.ForwardHelpTargetName` `<Command-Name>` Belirtilen komut için Yardım konusuna yeniden yönlendirir. Kullanıcılar bir işlev, betik, cmdlet'i veya sağlayıcısı için Yardım konularını da dahil olmak üzere tüm Yardım konusunu yeniden yönlendirebilirsiniz.

`.ForwardHelpCategory` `<Category>` Öğenin Yardım kategorisi içinde ForwardHelpTargetName belirtir. Diğer ad, Cmdlet, HelpFile, işlevi, sağlayıcı, genel, SSS, sözlük, ScriptCommand, ExternalScript, filtre veya tüm değerler geçerlidir. Bu anahtar sözcüğü, komutları aynı ada sahip olduğunuzda, çakışmaları önlemek için kullanın.

`.RemoteHelpRunspace` `<PSSession-variable>` Yardım konusu içeren bir oturum belirtir. PSSession içeren bir değişkeni girin. Bu anahtar sözcük tarafından kullanılan `Export-PSSession` verilen komutlar için Yardım konuları bulmak için cmdlet'i.

`.ExternalHelp` `<XML Help File>` Yolunu ve/veya betik veya işlevdeki bir XML tabanlı Yardım dosyasının adını belirtir.

`.ExternalHelp` Anahtar sözcüğü söyler [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet'ini bir XML tabanlı dosyasında betik veya işlevi için Yardım alın. **. ExternalHelp** anahtar sözcüğü, bir XML tabanlı Yardım dosyası için bir betik veya işlevdeki kullanılırken gereklidir. Bu olmadan, `Get-Help` işlev veya komut dosyası için bir Yardım dosyası bulmaz.

`.ExternalHelp` Anahtar sözcüğü diğer tüm açıklama tabanlı Yardım anahtar göre önceliklidir. Zaman `.ExternalHelp` var, [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet'i bile anahtar değeri ile eşleşen bir Yardım dosyası bulamadığında açıklama tabanlı Yardım görüntülemez.

İşlev değerini bir betik modülü tarafından aktarılan zaman `.ExternalHelp` bir yol belirtmeden dosya adı olmalıdır. `Get-Help` bir yerel ayara özgü alt modül dizinini dosyasını arar. Dosya adı için gereksinim yoktur, ancak aşağıdaki dosya adı biçimi kullanmak için en iyi uygulamadır: `<ScriptModule>.psm1-help.xml`.

İşlev bir modülle ilişkili olmadığı durumlarda, bir yol ve dosya adı değerine dahil **. ExternalHelp** anahtar sözcüğü. UI kültüre özgü alt dizinleri belirtilen XML dosyasının yolu içeriyorsa, `Get-Help` uygun geri dönüş standartları kurulan için dil olarak işlev ve betik adını içeren bir XML dosyası için alt dizinleri öz yinelemeli olarak arar Windows, yalnızca olmadığı için tüm XML tabanlı Yardım konularını yapar.

Cmdlet Yardım XML tabanlı Yardım dosyası biçimi hakkında daha fazla bilgi için bkz. [yazma Windows PowerShell cmdlet'i Yardımı](./writing-help-for-windows-powershell-cmdlets.md).