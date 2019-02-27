---
title: Cmdlet çıktı türleri | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845363"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet çıktı türleri

PowerShell cmdlet'leri tarafından çıktı üretmek için çağrılabilir çeşitli yöntemler sağlar. Bu yöntemler, belirli bir işlemi çıktılarını başarı veri akışı veya hata veri akışı gibi bir özel veri akışı yazmak için kullanın. Bu makalede, çıkış onları oluşturmak için kullanılan yöntemleri ve türleri açıklanmaktadır.

## <a name="types-of-output"></a>Çıktı türleri

### <a name="success-output"></a>Başarı çıktısı

Cmdlet'leri, ardışık düzende sonraki komutu tarafından işlenen bir nesne döndürerek başarı bildirebilirsiniz. Cmdlet başarıyla eylemi gerçekleştirdikten sonra cmdlet'i çağırır [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi. Bu yöntem yerine çağırmanızı öneririz [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) veya [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) yöntemleri.

Sağlayabilirsiniz bir **PassThru** nesneler genellikle döndürmeyen cmdlet'leri için parametre geçin.
Zaman **PassThru** komut satırında anahtar parametresi belirtilirse, cmdlet nesneyi döndürmek üzere sorulur. Bir örneği olan bir cmdlet'i bir **PassThru** parametresi bkz [Ekle-geçmiş](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Hata çıktısı

Cmdlet'leri hatalar bildirebilir. Cmdlet, sonlandırmalı bir hata oluştuğunda, özel durum oluşturur. Sonlandırıcı olmayan bir hata oluştuğunda cmdlet'i çağırır [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) bir hata kaydı hatası veri akışına göndermek üzere yöntemi. Hata raporlama hakkında daha fazla bilgi için bkz. [hata raporlama kavramları](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Ayrıntılı çıkış

Cmdlet'leri sağlayabilir yararlı bilgiler için cmdlet doğru kayıtları çağırarak işlerken [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) yöntemi. Yöntem nasıl eylemi İlerliyor ayrıntılı iletileri oluşturur.

Varsayılan olarak, ayrıntılı iletiler görüntülenmez. Belirtebileceğiniz **ayrıntılı** bu iletileri görüntülemek için cmdlet çalıştırıldığında parametresi. **Ayrıntılı** tüm cmdlet'ler için kullanılabilen ortak bir parametredir.

### <a name="progress-output"></a>İlerleme durumunu çıktı

Cmdlet'i, bir dizini yinelemeli olarak kopyalama gibi tamamlanması uzun süren görevler gerçekleştirirken cmdlet'leri için ilerleme durumu bilgileri sağlar. Cmdlet ilerleme bilgisini görüntülemek için çağırdığı [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) yöntemi.

### <a name="debug-output"></a>Hata ayıklama çıkışı

Cmdlet kod sorunlarını giderirken yararlıdır hata ayıklama iletileri cmdlet'leri sağlar. Hata ayıklama bilgileri cmdlet görüntülenecek çağırır [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) yöntemi.

Varsayılan olarak, hata ayıklama iletileri görüntülenmez. Belirtebileceğiniz **hata ayıklama** bu iletileri görüntülemek için cmdlet çalıştırıldığında parametresi. **Hata ayıklama** tüm cmdlet'ler için kullanılabilen ortak bir parametredir.

### <a name="warning-output"></a>Uyarı çıkış

Cmdlet'leri çağırarak uyarı iletilerini görüntüleyebilir [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) yöntemi.

Varsayılan olarak, uyarı iletileri görüntülenir. Kullanarak uyarı iletilerini ancak yapılandırabilirsiniz `$WarningPreference` kullanarak veya değişken **ayrıntılı** ve **hata ayıklama** cmdlet çağrıldığında parametreleri.

## <a name="displaying-output"></a>Çıktıyı görüntüleme

Tüm yazma yöntem çağrıları için içerik görünen belirli çalışma zamanı değişkenleri tarafından belirlenir. Özel durum [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi. Bu değişkenler kullanarak doğru yerde çağrısı kodunuzda yazma ve uygun olduğunda veya çıkış görüntülenmesi gerekiyorsa endişe olmayan hale getirebilirsiniz.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Bir ana bilgisayar uygulaması çıkış işlevselliğini erişme

Ayrıca, bir ana bilgisayar uygulaması çıkış işlevselliğini PowerShell çalışma zamanı doğrudan erişmek için bir cmdlet tasarlayabilirsiniz. Konak yerine PowerShell tarafından sağlanan API'leri kullanarak [System.Console](/dotnet/api/System.Console) veya [System.Windows.Forms](/dotnet/api/System.Windows.Forms) cmdlet'inize konakları çeşitli ile çalışmasını sağlar. Örneğin: **powershell.exe** konsol konağına **powershell_ise.exe** grafik konak, PowerShell uzaktan iletişimini konak ve üçüncü taraf konakları.

## <a name="see-also"></a>Ayrıca bkz.

[Hata Raporlama kavramları](./error-reporting-concepts.md)

[Cmdlet'i genel bakış](./cmdlet-overview.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)