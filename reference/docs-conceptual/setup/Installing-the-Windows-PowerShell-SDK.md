---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell SDK’sını Yükleme
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953574"
---
# <a name="installing-the-windows-powershell-sdk"></a>Windows PowerShell SDK’sını Yükleme

Aşağıdaki konuda farklı Windows sürümleri üzerinde PowerShell SDK'yı yüklemeyi açıklar.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 yükleme Windows 8 ve Windows Server 2012 için SDK'sı

Windows PowerShell 3.0, Windows 8 ve Windows Server 2012 ile otomatik olarak yüklenir.
Ayrıca, indirin ve Windows 8 SDK'sı bir parçası olarak Windows PowerShell 3.0 için başvuru bütünleştirilmiş yükleyin.
Bu derlemeler cmdlet'leri, sağlayıcıları ve ana bilgisayar programlar için Windows PowerShell 3.0 yazmanızı sağlar.
Windows 8 için Windows SDK yüklediğinizde, Windows PowerShell derlemeleri başvuru derleme klasöründe \Program dosyaları (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0 otomatik olarak yüklenir.
Daha fazla bilgi için bkz: [Windows 8 SDK yükleme sitesini](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Windows PowerShell kod örnekleri Geliştirme Merkezi de kullanılabilir.
Daha fazla bilgi için masaüstü kod örnek sayfasına bakın [Geliştirme Merkezi sitesi](http://code.msdn.microsoft.com/windowsdesktop/).

Ayrıca, Windows PowerShell 3.0 geriye dönük olarak uyumludur Windows PowerShell 2.0 SDK ile birlikte, kod örnekleri sayısını içerir.
Windows PowerShell 2.0 SDK'sını indirin hakkında daha fazla bilgi için aşağıya bakın.
(2.0 kod örnekleri Windows 8 ve Windows PowerShell 3.0 ile uyumlu olsa da, bir Windows 8 platformda Windows PowerShell 2.0 yükleme yapamayacağınızı unutmayın.)

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 yükleme Windows 7 ve Windows Server 2008 R2 için SDK'sı

Windows 7 ve Windows Server 2008 R2'in otomatik olarak PowerShell 2.0 yüklü.
Ayrıca, bu sistemlerinde PowerShell 3.0 yükleyebilirsiniz.
(Daha fazla bilgi için bkz: [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).).
Yukarıda açıklandığı gibi Windows 7 ve Windows Server 2008 R2'de Windows 8 SDK'sı yükleyebilirsiniz.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows PowerShell 2.0 yükleme için Windows 7, Vista, XP, Server 2003 ve Server 2008 SDK'sı

Windows PowerShell 2.0 SDK'sı cmdlet'leri, sağlayıcılarının ve barındırma uygulamaları yazmak için gereken başvuru derlemeleri sağlar ve kod yazmaya başladığınızda, başlangıç noktası olarak kullanılabilecek C# örnek kodu sağlıyor.

Bu SDK yüklemek için bkz: [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Başvuru derlemeleri

Başvuru derlemeleri varsayılan olarak aşağıdaki konuma yüklenir: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Not**: Windows PowerShell 2.0 derlemeleri karşı derlenmiş kod Windows PowerShell 1.0 yüklemelerde yüklenemiyor.
>Ancak, Windows PowerShell 1.0 derlemeleri karşı derlenmiş kod Windows PowerShell 2.0 yüklemelerde yüklenebilir.

## <a name="samples"></a>Örnekler

Kod örnekleri, varsayılan olarak şu konumda yüklenir: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Aşağıdaki bölümlerde her örnek yaptığı, kısa bir açıklama sağlayın.

## <a name="cmdlet-samples"></a>Cmdlet örnekleri
**GetProcessSample01**

Yerel bilgisayardaki tüm işlemler alır basit bir cmdlet yazma gösterilmektedir.

**GetProcessSample02**

Cmdlet parametreleri eklemek gösterilmiştir.
Cmdlet, bir veya daha fazla işlem adlarını alır ve eşleşen işlemleri döndürür.

**GetProcessSample03**

Ardışık Düzen girişten kabul parametreleri eklemek gösterilmiştir.

**GetProcessSample04**

Nonterminating hataların nasıl işleneceğini gösterir.

**GetProcessSample05**

Belirtilen işlemlerin listesini görüntülemek nasıl gösterir.

**SelectObject**

Nasıl yalnızca belirli nesneleri seçmek için bir filtre yazılacağını gösterir.

**SelectString**

Belirtilen desen dosyalarını arayın gösterilmektedir.

**StopProcessSample01**

Nasıl uygulandığını gösterir bir *PassThru* parametre ve yapılan çağrılar tarafından kullanıcı geri bildirim istemek nasıl [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) ve [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) yöntemleri.
Kullanıcıları belirtmek *PassThru* istediğinizde bir nesne döndürmek için cmdlet zorlamak parametre

**StopProcessSample02**

Belirli bir işlemi durdurmak gösterilmiştir.

**StopProcessSample03**

Parametreler için diğer adlar bildirmeyi ve joker karakterleri destekleme gösterir.

**StopProcessSample04**

Parametre kümeleri bildirme gösterilmektedir cmdlet giriş ve kullanmak üzere ayarlanmış varsayılan parametre belirtme alan nesne.

## <a name="remoting-samples"></a>Remoting örnekleri

**RemoteRunspace01**

Uzak bağlantı kurmak için kullanılan bir uzak çalışma alanı oluşturulacağını gösterir.

**RemoteRunspacePool01**

Bir uzak çalışma alanı havuzu oluşturma ve bu havuzu kullanarak birden çok komutları aynı anda çalışmasına nasıl gösterir.

**Serialization01**

Varolan bir .NET sınıfı arayın ve bu sınıfın seçili ortak özellikleri bilgilerinden serileştirme/seri durumdan çıkarma arasında korunur emin olmak gösterilmiştir.

**Serialization02**

Varolan bir .NET sınıfı arayın ve bilgileri sınıfının ortak özelliklerini kullanılabilir olmadığında bu sınıfın örneği bilgilerinden serileştirme/seri durumdan çıkarma arasında korunur emin olmak gösterilmiştir.

**Serialization03**

Varolan bir .NET sınıfı arayın ve örnekleri, bu sınıfın ve türetilmiş sınıflarının (dinamik .NET nesnelerini rehydrated) serisi olduğundan emin olun gösterilmektedir.

## <a name="event-samples"></a>Olay örnekleri

**Event01**

ObjectEventRegistrationBase türetme tarafından olay kaydı için bir cmdlet'i oluşturulacağını gösterir.

**Event02**

Gösterir nasıl uzak bilgisayarlarda oluşturulan Windows PowerShell olaylarını bildirimlerini almak üzere nasıl gösterir.
Aracılığıyla kullanıma sunulan PSEventReceived olayı kullanan [çalışma](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) sınıfı.

## <a name="hosting-application-samples"></a>Barındırma uygulama örnekleri

**Runspace01**

Nasıl kullanılacağını gösterir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) çalıştırmak için sınıf [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet zaman uyumlu olarak.
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet'i döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) nesneleri yerel bilgisayarda çalışan her işlem için.

**Runspace02**

Nasıl kullanılacağını gösterir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) çalıştırmak için sınıf [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) ve [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlet'leri zaman uyumlu olarak.
[Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet'i döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) nesneleri her işlem yerel bilgisayarda çalışan ve temel nesneleri Sort-Object sıralar kendi [kimliği](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) özelliği.
Sonuçları aşağıdaki komutlardan birini kullanarak görüntüleyen bir [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) denetim.

**Runspace03**

Nasıl kullanılacağını gösterir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) eşzamanlı olarak bir komut dosyasını çalıştırmak için sınıf ve sonlandırıcı olmayan hataların nasıl işleneceğini.
Komut dosyası işlemi adlarının bir listesini alır ve bu işlemleri alır.
Komut dosyası çalıştırılırken oluşturulan Sonlandırıcı olmayan hatalar dahil olmak üzere komut dosyası sonuçlarını konsol penceresinde görüntülenir.

**Runspace04**

Nasıl kullanılacağını gösterir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) komutlarını çalıştırmak için sınıf ve komutlarını çalıştırırken oluşturulan catch sonlandırma hataları nasıl.
İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişken geçirildi.
Sonuç olarak, hiçbir nesne döndürmedi ve bir sonlandırma hatası oluşturulur.

**Runspace05**

Bir ek bileşenine ekleme gösterilmektedir bir [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) çalışma açıldığında cmdlet ek bileşenini, böylece kullanılabilir nesne.
Ek bir Get-Proc cmdlet sağlar (tarafından tanımlanan [GetProcessSample01 örnek](https://technet.microsoft.com/library/ff602028.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) nesnesi.

**Runspace06**

Bir modüle eklemeyi gösterir bir [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) çalışma açıldığında modülü yüklenir böylece nesne.
Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](https://technet.microsoft.com/library/ff602027.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) nesnesi.

**Runspace07**

Bir çalışma alanı oluşturun ve ardından kullanarak iki cmdlet'leri zaman uyumlu olarak çalıştırmak için bu çalışma alanı kullanın gösterilmektedir bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) nesnesi.

**Runspace08**

Komutlar ve bağımsız değişkenler ardışık düzenine nasıl ekleneceğini gösterir bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) nesne ve komutları eşzamanlı olarak çalıştırma.

**Runspace09**

Bir komut dosyası ardışık düzenine eklemek gösterilmektedir bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) nesnesi ve komut dosyalarını zaman uyumsuz olarak çalıştırma.
Olaylar, komut çıktısı işlemek için kullanılır.

**Runspace10**

Varsayılan ilk oturum durumu oluşturmayı gösteren bir cmdlet ile ekleme [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), ilk oturum durumu kullanan bir çalışma alanı oluşturma ve kullanarak komutu çalıştırmak nasıl bir [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)nesnesi.

**Runspace11**

Nasıl kullanılacağını gösterir [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) var olan bir cmdlet'i çağırır, ancak kullanılabilir parametreleri kümesini sınırlayan bir proxy komutu oluşturmak için sınıfı.
Proxy komutu daha sonra kısıtlı bir çalışma alanı oluşturmak için kullanılan bir ilk oturum durumu eklenir.
Bu kullanıcının yalnızca proxy komutu aracılığıyla cmdlet işlevselliğini erişebileceği anlamına gelir.

**PowerShell01**

Kullanarak bir kısıtlanmış çalışma alanı oluşturmayı gösteren bir [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) nesnesi.

**PowerShell02**

Bir çalışma alanı havuzu birden çok komutları aynı anda çalıştırmak için nasıl kullanılacağını gösterir.

## <a name="host-samples"></a>Ana bilgisayar örnekleri

**Host01**

Özel bir ana bilgisayar kullanan bir ana bilgisayar uygulaması uygulamak gösterilmiştir.
Özel ana bilgisayar kullanan bir çalışma alanı oluşturulur bu örnekteki ve ardından [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API "Çık" çağıran bir komut dosyası çalıştırmak için kullanılır.
Ana bilgisayar uygulamasını komut dosyasının çıktıyı arar ve sonuçları yazdırır.

**Host02**

Windows PowerShell çalışma zamanı özel konak uygulaması birlikte kullanan bir ana bilgisayar uygulamasının nasıl yazılacağını gösterir.
Konak uygulama ana bilgisayar kültür Almanca, çalışır ayarlar [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet'i ve yazarken sonuçları görüntüler bkz bunları pwrsh.exe ve geçerli veri ve saat sonra yazdırır Almanca kullanarak.

**Host03**

Komut satırından komutları okuyan, komutları çalıştırır ve sonuçları konsola görüntüler bir etkileşimli konsol tabanlı ana bilgisayar uygulamasının nasıl oluşturulacağını gösterir.

**Host04**

Komut satırından komutları okuyan, komutları çalıştırır ve sonuçları konsola görüntüler bir etkileşimli konsol tabanlı ana bilgisayar uygulamasının nasıl oluşturulacağını gösterir.
Bu ana bilgisayar uygulaması, ayrıca birden çok seçenek belirtmesini izin görüntüleme istemleri destekler.

**Host05**

Komut satırından komutları okuyan, komutları çalıştırır ve sonuçları konsola görüntüler bir etkileşimli konsol tabanlı ana bilgisayar uygulamasının nasıl oluşturulacağını gösterir.
Ayrıca bu ana bilgisayar uygulaması kullanarak uzak bilgisayarlara çağrıları destekler [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) ve [çıkış-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlet'leri.

**Host06**

Komut satırından komutları okuyan, komutları çalıştırır ve sonuçları konsola görüntüler bir etkileşimli konsol tabanlı ana bilgisayar uygulamasının nasıl oluşturulacağını gösterir.
Ayrıca, bu örnek kullanıcı tarafından girilen metin rengini belirtmek için belirteç Oluşturucu API'lerini kullanır.

## <a name="provider-samples"></a>Sağlayıcısı örnekleri

**AccessDBProviderSample01**

Doğrudan türeyen bir sağlayıcı sınıf bildirme gösterilmektedir [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) sınıfı.
Burada yalnızca bütünlük açısından dahil edilmiştir.

**AccessDBProviderSample02**

Üzerine gösterilmektedir [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) ve [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) yeni PSDrive ve Kaldır-PSDrive cmdlet'leri çağrıları desteklemek için yöntemleri.
Bu örnek sağlayıcısı sınıfında türetilen [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) sınıfı.

**AccessDBProviderSample03**

Üzerine gösterilmektedir [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) ve [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) Get-Item ve Set-Item cmdlet'leri çağrıları desteklemek için yöntemleri.
Bu örnek sağlayıcısı sınıfında türetilen [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) sınıfı.

**AccessDBProviderSample04**

Copy-Item, Get-Childıtem çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterilmektedir yeni öğe ve Kaldır-Item cmdlet'leri.
Veri deposu kapsayıcılar olan öğeler içeriyorsa, bu yöntemleri uygulanmalıdır.
Ortak bir üst öğenin altında bir alt öğe grubunu bir kapsayıcıdır.
Bu örnek sağlayıcısı sınıfında türetilen [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) sınıfı.

**AccessDBProviderSample05**

Taşıma öğesi ve birleştirme yolu cmdlet'leri çağrıları desteklemek için kapsayıcı yöntemleri üzerine nasıl yazılacağını gösterir.
Bu yöntemler, kullanıcı bir kapsayıcı içindeki öğeleri taşımak gerektiğinde ve veri depolama alanı iç içe geçmiş kapsayıcılar içeriyorsa uygulanmalıdır.
Bu örnek sağlayıcısı sınıfında türetilen [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) sınıfı.

**AccessDBProviderSample06**

Clear içerik çağrıları desteklemek için içerik yöntemleri üzerine gösterilmektedir Get-içerik ve Set-Content cmdlet'leri.
Bu yöntemler, kullanıcı içeriği veri deposuna'ndeki öğelerin kullanımını yönetmek gerektiğinde uygulanmalıdır.
Bu örnek sağlayıcısı sınıfında türetilen [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) sınıfı ve uygulayan [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) arabirimi.