---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell SDK’sını Yükleme
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893547"
---
# <a name="installing-the-windows-powershell-sdk"></a>Windows PowerShell SDK’sını Yükleme

Aşağıdaki konuda farklı Windows sürümleri üzerinde PowerShell SDK'yı yüklemeyi açıklar.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 yükleme Windows 8 ve Windows Server 2012 için SDK'sı

Windows PowerShell 3.0, Windows 8 ve Windows Server 2012 ile otomatik olarak yüklenir.
Ayrıca, indirin ve başvuru bütünleştirilmiş kodları için Windows PowerShell 3.0 Windows 8 SDK'ın bir parçası olarak yükleyin.
Bu derlemeler cmdlet'leri ve sağlayıcıları ana program için Windows PowerShell 3.0 yazmanıza olanak sağlar.
Windows 8 için Windows SDK'yı yüklediğinizde, Windows PowerShell derlemeler otomatik olarak başvuru derleme klasöründe yüklendiği `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Daha fazla bilgi için [Windows 8 SDK indirme sitesi](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Windows PowerShell kod örnekleri geliştirme Merkezi'nden de mevcuttur.
Daha fazla bilgi için masaüstü kod örnek sayfasına bakın [Geliştirme Merkezi sitesi](https://code.msdn.microsoft.com:443/windowsdesktop/).

Ayrıca, Windows PowerShell 3.0 geriye dönük olarak uyumludur Windows PowerShell 2.0 SDK kod örnekleri sayısını içerir.
Windows PowerShell 2.0 SDK'sını indirme hakkında daha fazla bilgi için aşağıya bakın.
(2.0 kod örnekleri Windows 8 ve Windows PowerShell 3.0 ile uyumlu olsa da, Windows 8 platformu üzerinde Windows PowerShell 2.0 uygulamasını yükleyemezsiniz unutmayın.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 yüklenmesi Windows 7 ve Windows Server 2008 R2 için SDK'sı

Otomatik olarak Windows 7 ve Windows Server 2008 R2 PowerShell 2.0 yüklü.
Ayrıca, PowerShell 3.0 Bu sistemlerin tümünde yükleyebilirsiniz.
(Daha fazla bilgi için [Windows PowerShell'i yükleme](Installing-Windows-PowerShell.md).).
Yukarıda açıklandığı gibi Windows 7 ve Windows Server 2008 R2'de Windows 8 SDK'sını yükleyebilirsiniz.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows PowerShell 2.0 yükleme için Windows 7, Vista, XP, Server 2003 ve Server 2008 SDK'sı

Windows PowerShell 2.0 SDK'sını cmdlet'leri ve sağlayıcıları barındırma uygulamaları yazmak için gereken başvuru derlemelerini sağlar ve kod yazmaya başladığınızda, başlangıç noktası olarak kullanılacak C# örnek kodu sağlar.

Bu SDK'yı yüklemek için bkz [Windows PowerShell 2.0 SDK'sını](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Başvuru bütünleştirilmiş kodları

Başvuru bütünleştirilmiş kodları, varsayılan olarak şu konuma yüklenir: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Windows PowerShell 2.0 derlemeleri karşı derlenmiş kod, Windows PowerShell 1.0 yüklemelerde yüklenemiyor.
> Ancak, Windows PowerShell 1.0 derlemelere karşı derlenmiş kod, Windows PowerShell 2.0 yüklemelerde yüklenebilir.

## <a name="samples"></a>Örnekler

Kod örnekleri, varsayılan olarak şu konuma yüklenir: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Aşağıdaki bölümlerde, her örnek yapar, kısa bir açıklama sağlayın.

## <a name="cmdlet-samples"></a>Cmdlet örnekleri

### <a name="getprocesssample01"></a>GetProcessSample01

Tüm işlemler yerel bilgisayarda alır basit bir cmdlet yazma işlemi gösterilmektedir.

### <a name="getprocesssample02"></a>GetProcessSample02

Cmdlet'e parametre ekleme işlemi gösterilmektedir.
Cmdlet'i, bir veya daha fazla işlem adlarını alır ve eşleşen işlem döndürür.

### <a name="getprocesssample03"></a>GetProcessSample03

Ardışık düzendeki girişi kabul parametreleri ekleme işlemi gösterilmektedir.

### <a name="getprocesssample04"></a>GetProcessSample04

Olmak üzere sonlandırmasız hatalar nasıl ele alınacağını gösterir.

### <a name="getprocesssample05"></a>GetProcessSample05

Belirtilen işlemlerin bir listesini görüntüleme işlemini göstermektedir.

### <a name="selectobject"></a>SelectObject

Yalnızca belirli nesneleri seçmek için bir filtre yazma işlemi gösterilmektedir.

### <a name="selectstring"></a>SelectString

Belirtilen desenle dosyalarını aramak gösterilmektedir.

### <a name="stopprocesssample01"></a>StopProcessSample01

Nasıl uygulayacağınızı gösteren bir *PassThru* parametresi ve yapılan çağrılar tarafından kullanıcı geri bildirimi nasıl [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) ve [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) yöntemleri.
Kullanıcının belirttiği *PassThru* nesneyi döndürmek için cmdlet zorlamak istediğinizde parametresi

### <a name="stopprocesssample02"></a>StopProcessSample02

Belirli bir işlem durdurma işlemi gösterilmektedir.

### <a name="stopprocesssample03"></a>StopProcessSample03

Joker karakterleri destekleme ve parametreler için diğer ad bildirmek nasıl gösterir.

### <a name="stopprocesssample04"></a>StopProcessSample04

Parametre kümesine nasıl gösterir cmdlet'i, girdi ve nasıl belirtileceğini kullanacak şekilde varsayılan parametre olarak alan nesne.

## <a name="remoting-samples"></a>Uzaktan iletişimini örnekleri

### <a name="remoterunspace01"></a>RemoteRunspace01

Uzak bağlantı kurmak için kullanılan bir uzak çalışma alanı oluşturma işlemi gösterilmektedir.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Bu havuzu kullanarak aynı anda birden çok komut çalıştırma ve bir uzak çalışma alanı havuzu oluşturmak nasıl gösterir.

### <a name="serialization01"></a>Serialization01

Mevcut bir .NET sınıfı arayın ve bu sınıfın seçilen genel özelliklerin bilgilerinden serileştirme/seri durumdan çıkarma işlemi korunur emin olmak nasıl gösterir.

### <a name="serialization02"></a>Serialization02

Mevcut bir .NET sınıfına bakın ve bilgileri sınıfın genel özelliklerini mevcut olmadığında bu sınıfın örneğini bilgilerinden serileştirme/seri durumundan çıkarma arasında korunmasını sağlayın gösterilmektedir.

### <a name="serialization03"></a>Serialization03

Mevcut bir .NET sınıfına bakın ve bu sınıfın ve türetilen sınıfların örnekleri (Canlı .NET nesnelerini rehydrated) durumdan emin emin olmak nasıl gösterir.

## <a name="event-samples"></a>Olay örnekleri

### <a name="event01"></a>Event01

Bir cmdlet için etkinlik kaydı ObjectEventRegistrationBase türetme tarafından oluşturma işlemi gösterilmektedir.

### <a name="event02"></a>Event02

Gösterir nasıl uzak bilgisayarlarda oluşturulan Windows PowerShell olay bildirimleri almak nasıl gösterir.
Aracılığıyla kullanıma PSEventReceived olay kullanan [çalışma](/dotnet/api/system.management.automation.runspaces.runspace) sınıfı.

## <a name="hosting-application-samples"></a>Barındırma uygulaması örnekleri

### <a name="runspace01"></a>Runspace01

Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i zaman uyumlu olarak.
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) nesneler yerel bilgisayarda çalışan her işlem için.

### <a name="runspace02"></a>Runspace02

Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) ve [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet'leri zaman uyumlu olarak.
[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet döndürür [işlem](https://technet.microsoft.com/library/system.diagnostics.process.aspx) yerel bilgisayarda çalışan her işlem için nesneleri ve `Sort-Object` nesneleri göre sıralar, [kimliği](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) özellik.
Sonuçları aşağıdaki komutlardan birini kullanarak görüntülenen bir [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) denetimi.

### <a name="runspace03"></a>Runspace03

Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) zaman uyumlu olarak bir betik çalıştırmak için sınıf ve sonlandırıcı olmayan hatalara nasıl ele alınacağını.
Betik işlem adları listesini alır ve ardından bu işlemleri alır.
Komut dosyası çalıştırılırken oluşturulan sonlandırmayan hatalar dahil olmak üzere betik sonuçlarını konsol penceresinde görüntülenir.

### <a name="runspace04"></a>Runspace04

Nasıl kullanılacağını gösterir [PowerShell](/dotnet/api/system.management.automation.powershell) komutlarını çalıştırmak için sınıf ve komutlarını çalıştırırken oluşturulan catch Sonlandırıcı hataları.
İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişkeni olarak geçirilir.
Sonuç olarak, hiçbir nesne döndürülür ve bir sonlandırma hatası oluşturulur.

### <a name="runspace05"></a>Runspace05

Bir ek bileşenine ekleme işlemi açıklanır bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) böylece çalışma açıldığında, ek cmdlet kullanılabilir nesne.
Ek bir Get-Proc cmdlet sağlar (tarafından tanımlanan [GetProcessSample01 örnek](https://technet.microsoft.com/library/ff602028.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.

### <a name="runspace06"></a>Runspace06

Bir modüle ekleneceği gösterilmiştir bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) modülü bir çalışma açıldığında yüklenmesi nesne.
Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](https://technet.microsoft.com/library/ff602027.aspx)) çalıştırılan zaman uyumlu olarak kullanarak bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.

### <a name="runspace07"></a>Runspace07

Bir çalışma alanı oluşturun ve ardından iki cmdlet kullanarak zaman uyumlu olarak çalıştırmak için bu çalışma alanı kullanma gösteren bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne.

### <a name="runspace08"></a>Runspace08

Komut ve bağımsız değişkenler için işlem hattı eklemeyi gösterir bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne ve zaman uyumlu olarak komutları çalıştırmayı öğrenin.

### <a name="runspace09"></a>Runspace09

İşlem hattı için bir komut dosyası eklemeyi gösterir bir [PowerShell](/dotnet/api/system.management.automation.powershell) nesne ve komut zaman uyumsuz olarak çalıştırmayı öğrenin.
Olaylar, komut çıktısı işlemek için kullanılır.

### <a name="runspace10"></a>Runspace10

Bir varsayılan ilk oturum durumu oluşturulacağını gösterir bir cmdlet'e ekleme [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), ilk oturum durumu kullanan bir çalışma alanı oluşturma ve komutu çalıştırmak amacıyla kullanmak üzere nasıl bir [PowerShell](/dotnet/api/system.management.automation.powershell)nesne.

### <a name="runspace11"></a>Runspace11

Nasıl kullanılacağını gösterir [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) var olan bir cmdlet'i çağırır, ancak kullanılabilir parametreleri kümesini sınırlayan bir ara sunucu komutu oluşturmak için sınıf.
Ara sunucu komutunu kısıtlı bir çalışma alanı oluşturmak için kullanılan bir ilk oturum durumunu daha sonra eklenir.
Bu, kullanıcının yalnızca ara sunucu komutu cmdlet işlevselliğini erişebileceği anlamına gelir.

### <a name="powershell01"></a>PowerShell01

Kullanarak bir kısıtlı çalışma alanı oluşturma işlemi gösterilmektedir bir [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) nesne.

### <a name="powershell02"></a>PowerShell02

Aynı anda birden çok komut çalıştırmak için bir çalışma alanı havuzu kullanmayı gösterir.

## <a name="host-samples"></a>Konak örnekleri

### <a name="host01"></a>Host01

Özel bir ana bilgisayar kullanan bir konak uygulamanın nasıl uygulanacağını gösterir.
Özel ana bilgisayarı kullanan bu örnekte bir çalışma alanı oluşturulur ve ardından [PowerShell](/dotnet/api/system.management.automation.powershell) API "çıkış" çağıran bir betik çalıştırmak için kullanılır.
Konak uygulama betiği çıktısına arar ve sonuçları yazdırır.

### <a name="host02"></a>Host02

Özel ana bilgisayar uygulaması ile birlikte Windows PowerShell'i çalışma zamanı kullanan bir ana bilgisayar uygulaması yazma işlemi gösterilmektedir.
Ana bilgisayar uygulaması çalışır Almanca için konak kültürü ayarlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet ve aynı sonuçları görüntüler bkz bunları pwrsh.exe ve geçerli veri ve saat sonra yazdırır Almanca kullanarak.

### <a name="host03"></a>Host03

Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.

### <a name="host04"></a>Host04

Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.
Bu ana bilgisayar uygulaması birden çok seçenek belirtmesini sağlayan görüntüleme yönergeleri de destekler.

### <a name="host05"></a>Konak05

Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.
Ayrıca bu ana bilgisayar uygulaması kullanarak uzak bilgisayarlara çağrıları destekleyen [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) ve [çıkış-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet'leri.

### <a name="host06"></a>Host06

Komutları komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.
Ayrıca, bu örnek, kullanıcı tarafından girilen metin rengi belirtmek için belirteç Oluşturucu API kullanır.

## <a name="provider-samples"></a>Sağlayıcısı örnekleri

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Doğrudan öğesinden türetilen bir sağlayıcı sınıfı bildirmek gösterilmektedir [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) sınıfı.
Burada yalnızca bütünlük açısından dahil edilmiştir.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Üzerine yazma işlemi gösterilmektedir [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) ve [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) çağrıları desteklemek için yöntemler `New-PSDrive` ve `Remove-PSDrive` cmdlet'leri.
Bu örnekteki sağlayıcı sınıfın türetildiği [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) sınıfı.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Üzerine yazma işlemi gösterilmektedir [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) ve [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) çağrıları desteklemek için yöntemler `Get-Item` ve `Set-Item` cmdlet'leri.
Bu örnekteki sağlayıcı sınıfın türetildiği [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) sınıfı.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterilmektedir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri.
Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır.
Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır.
Bu örnekteki sağlayıcı sınıfın türetildiği [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) sınıfı.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Çağrıları desteklemek için kapsayıcı yöntemleri üzerine gösterilmektedir `Move-Item` ve `Join-Path` cmdlet'leri.
Bu yöntemler, bir kapsayıcı içindeki öğeleri taşımak gerektiğinde ve veri depolama alanı iç içe geçmiş kapsayıcılar varsa uygulanmalıdır.
Bu örnekteki sağlayıcı sınıfın türetildiği [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) sınıfı.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Çağrıları desteklemek için içerik yöntemleri üzerine gösterilmektedir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri.
Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır.
Bu örnekteki sağlayıcı sınıfın türetildiği [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) sınıf ve uyguladığı [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) arabirimi.