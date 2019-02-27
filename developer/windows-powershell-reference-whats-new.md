---
title: Windows PowerShell başvuru - yenilikler nelerdir?
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848597"
---
# <a name="whats-new"></a>Yenilikler

Windows PowerShell 2.0 kullanmak için cmdlet'leri ve sağlayıcıları uygulamaları barındırmak yazarken aşağıdaki yeni özellikleri sağlar.

## <a name="modules"></a>Modüller

Şimdi, paketleyebilir ve Windows PowerShell çözümleri modüllerini kullanarak dağıtabilirsiniz. Modüller bölüme izin, düzenlemek ve Windows PowerShell kodunuzu müstakil, yeniden kullanılabilir birimler halinde soyut. Bir Windows PowerShell modülü yazma modüller hakkında daha fazla bilgi için bkz.

## <a name="the-powershell-class"></a>PowerShell sınıfı

PowerShell sınıf için program aracılığıyla komutları çalıştırma konak uygulamalar adlandırılır, uygulamaları oluşturmak için daha basit bir çözüm sağlar. Bu sınıf, komutların bir işlem hattı oluşturma, komutları çalıştırmak için kullanılan çalışma belirlemek ve komutlar zaman uyumlu veya zaman uyumsuz olarak çağırma belirtin sağlar.

## <a name="the-runspacepool-class"></a>RunspacePool sınıfı

Çalışma alanı havuzları birden çok çalışma alanları tek bir çağrı kullanılarak oluşturmanıza imkan tanır. CreateRunspacePool yöntemi, aynı ana bilgisayar, ilk oturum durumu ve bağlantı bilgileri gibi aynı özelliklere sahip çalışma alanları oluşturmak için kullanılan çeşitli aşırı yükler sağlar.

## <a name="the-initialsessionstate-class"></a>InitialSessionState sınıfı

InitialSessionState sınıfı, bir çalışma alanı açıldığında kullanılan bir oturum durumu yapılandırmasını oluşturmanıza olanak sağlar. Özel yapılandırma, mshshort tarafından sağlanan komutları içeren bir varsayılan yapılandırması ve komutlarının kısıtlanır oturumunu yeteneklerine göre yapılandırmasını oluşturabilirsiniz.

## <a name="remote-runspaces"></a>Uzak çalışma alanları

Uzak makinede komutları çalıştırabilir ve sonuçlarını yerel olarak toplamak olanak tanıyan uzak bilgisayarlarda açılabilir çalışma alanları artık oluşturabilirsiniz. Bir uzak çalışma alanı oluşturmak için çalışma alanı oluştururken, uzak bağlantı bilgilerini belirtmeniz gerekir. CreateRunspace ve CreateRunspacePool örnekler için bkz. Bağlantı bilgilerini RunspaceConnectionInfo sınıfı tarafından tanımlanır.

## <a name="private-runspace-elements"></a>Özel çalışma öğeleri

Artık, genel veya özel öğeleri olan çalışma alanları oluşturabilirsiniz. Bu öğeleri çalışma alanı için kullanılabilir, ancak kullanıcılar için uygun olmayan çalışma alanları oluşturmanızı sağlar. Hangi çalışma öğelerinin özel hale getirilebilir bulmak için ConstrainedSessionStateEntry sınıfına bakın.

## <a name="runspace-threading-modes-and-apartment-state"></a>Çalışma modları ve Grup durumu iş parçacığı oluşturma

Artık, bir çalışma alanında komutlarını çalıştırırken kullanılan iş parçacıklarını nasıl oluşturulduğunu ve belirtebilirsiniz. System.Management.Automation.Runspaces.Runspace.ThreadOptions ve System.Management.Automation.Runspaces.RunspacePool.ThreadOptions özelliklere bakın.

Artık, bir çalışma alanında komutlarını çalıştırmak için kullanılan iş parçacıklarının Grup durumu alabilirsiniz. System.Management.Automation.Runspaces.Runspace.ApartmentState ve System.Management.Automation.Runspaces.RunspacePool.ApartmentState özelliklere bakın.

## <a name="transaction-cmdlets"></a>İşlem cmdlet'leri

Artık, bir işlem içinde kullanılabilen cmdlet'leri de oluşturabilirsiniz. Bir işlemde bir cmdlet'i kullanıldığında eylemlerini geçicidir ve bunlar kabul edilecek veya Windows PowerShell tarafından sağlanan işlem cmdlet'leri tarafından reddedildi.

İşlemler hakkında daha fazla bilgi için bkz. nasıl destek işlemler yapılır.

## <a name="transaction-provider"></a>İşlem sağlayıcısı

Artık, bir işlem içinde kullanılabilir bir sağlayıcı oluşturabilirsiniz. Benzer şekilde bir işlemde bir sağlayıcı kullanıldığında, cmdlet, eylemlerini geçici ve bunlar kabul edilecek veya Windows PowerShell tarafından sağlanan işlem cmdlet'leri tarafından reddedildi.

İşlem bir sağlayıcı sınıfı içinde desteği belirtme hakkında daha fazla bilgi için System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities özelliğine bakın.

## <a name="job-cmdlets"></a>İş cmdlet'leri

Artık bir iş olarak kendi eylemi gerçekleştirebilir cmdlet'leri de yazabilirsiniz. Bu işleri, geçerli oturum etkileşim olmadan arka planda çalıştırılır. Windows PowerShell işleri nasıl desteklediği hakkında daha fazla bilgi için arka plan işleri bakın.

## <a name="cmdlet-output-types"></a>Cmdlet çıktı türleri

Artık, OutputType özniteliğini cmdlet'lerinizi yazarken bildirerek, cmdlet tarafından döndürülen .NET Framework türleri de belirtebilirsiniz. Bu, başkalarının hangi nesnelerin türünü cmdlet'inin OutputType özelliğine bakılarak cmdlet'i tarafından döndürülür belirlemek izin verir.

## <a name="event-support"></a>Olay destek

Ekleme ve olayları kullanma cmdlet'ler artık yazabilirsiniz. PSEvent sınıfına bakın.

## <a name="proxy-commands"></a>Proxy komutları

Artık başka bir komut çalıştırmak için kullanılan proxy komutları yazabilirsiniz. Bir ara sunucu komutu, kullanıcıya hangi işlevleri kaynak cmdlet kullanılabilir denetlemenize olanak tanır. Örneğin, kaynak komutu tarafından sağlanan bir parametre kaldırır bir ara sunucu komutu oluşturabilirsiniz. ProxyCommand sınıfına bakın.

## <a name="multiple-choice-prompts"></a>Birden çok seçim istemleri

Artık birden çok seçim kullanıcı komut istemlerini sağlayan uygulamalar yazabilirsiniz. IHostUISupportsMultipleChoiceSelection arabirimi bakın

## <a name="interactive-sessions"></a>Etkileşimli oturumları

Şimdi başlatabilir ve uzak bir bilgisayarda etkileşimli bir oturum durdurabilirsiniz uygulamalar yazabilirsiniz.
IHostSupportsInteractiveSession arabirimi konusuna bakın.

## <a name="custom-cmdlet-help-for-providers"></a>Özel Cmdlet yardımına sağlayıcıları

Artık sağlayıcısı cmdlet'leri için özelleştirilmiş Yardım konuları da oluşturabilirsiniz. Özel cmdlet'i Yardım konularını, cmdlet cmdlet'e sağlayıcısı ekler dinamik parametreleri de dahil olmak üzere sağlayıcı yolu ve belge özelliklere, nasıl çalıştığını açıklayabilir.
