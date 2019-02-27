---
title: Yükleme ve biçimlendirme verileri dışarı aktarma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 08c64d4094d8ba6c551b454887331666f0694f11
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850053"
---
# <a name="loading-and-exporting-formatting-data"></a>Biçimlendirme Verilerini Yükleme ve Dışarı Aktarma

Biçimlendirme dosyanızı oluşturduktan sonra dosyalarınızı geçerli oturuma yükleyerek oturumun biçim verilerini güncelleştirmeniz gerekir. (Windows PowerShell tarafından sağlanan biçimlendirme dosyaları geçerli oturum açıldığında, kayıtlı olan eklentileri tarafından yüklenir.) Geçerli oturumun biçim verilerini güncelleştirildikten sonra Windows PowerShell yüklü biçimlendirme dosyalarında tanımlanan görünümleri ile ilişkili .NET nesneleri görüntülemek için bu verileri kullanır. Geçerli oturuma yükleyebilir biçimlendirme dosyaları sayısı sınırı yoktur. Biçimlendirme veri güncelleştirmeye ek olarak, bir biçimlendirme dosyasına geri geçerli oturumda biçim verilerini verebilirsiniz.

## <a name="loading-format-data"></a>Biçim veri yükleme

Biçimlendirme dosyaları geçerli oturuma aşağıdaki yöntemler kullanılarak yüklenebilir:

- Komut satırından geçerli oturuma biçimlendirme dosyayı içeri aktarabilirsiniz. Kullanım [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) aşağıdaki yordamda açıklandığı gibi cmdlet'i.
- Komut satırından geçerli oturuma biçimlendirme dosyayı içeri aktarabilirsiniz. Kullanım [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) aşağıdaki yordamda açıklandığı gibi cmdlet'i.

- Biçimlendirme dosyanızı başvuran bir modül bildirimi oluşturabilirsiniz. Modülleri, dağıtım dosyaları biçimlendirme paketlemenize olanak sağlar. Kullanım [yeni ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) bildirimi oluşturmak için cmdlet'i ve [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet modülü geçerli oturuma yüklenemedi. Modüller hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).
- Biçimlendirme dosyanızı başvuran bir modül bildirimi oluşturabilirsiniz. Modülleri, dağıtım dosyaları biçimlendirme paketlemenize olanak sağlar. Kullanım [yeni ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) bildirimi oluşturmak için cmdlet'i ve [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet modülü geçerli oturuma yüklenemedi. Modüller hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

- Biçimlendirme dosyanızı başvuran bir ek bileşenini oluşturabilirsiniz. Kullanım [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) biçimlendirme dosyalarınızı başvurmak için. Dağıtım için paket Cmdlet'lerine, modüller ve ilişkili bir biçimlendirme ve türleri dosyaları kullanmak için özellikle önerilir. Modüller hakkında daha fazla bilgi için bkz: [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

- Komutları bir program aracılığıyla çağırdığınız, komutları çalıştırdığı ilk oturum durumunu çalışma alanı için bir biçimlendirme dosya giriş ekleyebilirsiniz. Biçimlendirme dosyası eklemek için kullanılan .NET türü hakkında daha fazla bilgi için bkz: [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty Fullname =](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) sınıfı.

Biçimlendirme bir dosya yüklendiğinde, Windows PowerShell, komut satırında nesneleri görüntülenirken kullanılacak görüntülemek belirlemek için kullandığı bir iç listesine eklenir. Listenin başına biçimlendirme dosyanızın önüne ekleyin veya listenin sonuna ekleyin. Burada biçimlendirme dosyanızı bu listeye eklenen bilerek biçimlendirme dosyasında tanımlanan, nasıl bir Windows PowerShell core cmdlet'i tarafından döndürülen bir nesnedir değiştirmek istediğinizde gibi mevcut bir görünüme sahip bir nesne için bir görünüm tanımlayan yüklüyorsanız önemlidir  görüntülenir. Yalnızca görünüm için bir nesne tanımlayan bir biçimlendirme dosyası yüklüyorsanız, daha önce açıklanan yöntemlerden herhangi birini kullanabilirsiniz.  Başka bir görünüm için bir nesne tanımlayan bir biçimlendirme dosyası yüklüyorsanız kullanmalısınız [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'i ve listenin başına dosyanızın önüne ekleyin.
Biçimlendirme bir dosya yüklendiğinde, Windows PowerShell, komut satırında nesneleri görüntülenirken kullanılacak görüntülemek belirlemek için kullandığı bir iç listesine eklenir. Listenin başına biçimlendirme dosyanızın önüne ekleyin veya listenin sonuna ekleyin. Burada biçimlendirme dosyanızı bu listeye eklenen bilerek biçimlendirme dosyasında tanımlanan, nasıl bir Windows PowerShell core cmdlet'i tarafından döndürülen bir nesnedir değiştirmek istediğinizde gibi mevcut bir görünüme sahip bir nesne için bir görünüm tanımlayan yüklüyorsanız önemlidir  görüntülenir. Yalnızca görünüm için bir nesne tanımlayan bir biçimlendirme dosyası yüklüyorsanız, daha önce açıklanan yöntemlerden herhangi birini kullanabilirsiniz.  Başka bir görünüm için bir nesne tanımlayan bir biçimlendirme dosyası yüklüyorsanız kullanmalısınız [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'i ve listenin başına dosyanızın önüne ekleyin.

## <a name="storing-your-formatting-file"></a>Biçimlendirme, dosya depolama

Biçimlendirme, dosyaları diskte depolandığı için gereksinimi yoktur. Ancak, aşağıdaki klasörde depolamaya kesinlikle önerilir: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>İçeri aktarma FormatData kullanarak bir biçim dosyası yükleniyor

1. Biçimlendirme dosyanıza disk Store.

2. Çalıştırma [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'i aşağıdaki komutlardan birini kullanarak.
2. Çalıştırma [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'i aşağıdaki komutlardan birini kullanarak.

   Dosya listesi önüne sizin biçimlendirme eklemek için bu komutu kullanın. Bir nesne nasıl görüntüleneceğini değiştiriyorsanız bu komutu kullanın.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Dosya listesinin sonuna sizin biçimlendirme eklemek için bu komutu kullanın.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Kullanarak bir dosya eklendiğinde [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'ini kaldıramazsınız dosya listeden oturumu açıkken. Biçimlendirme dosyayı listeden kaldırmak için oturumu kapatmanız gerekir.
   Kullanarak bir dosya eklendiğinde [güncelleştirme FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet'ini kaldıramazsınız dosya listeden oturumu açıkken. Biçimlendirme dosyayı listeden kaldırmak için oturumu kapatmanız gerekir.

## <a name="exporting-format-data"></a>Biçim verilerini dışarı aktarma

Gövde bölümünü buraya ekleyin.
