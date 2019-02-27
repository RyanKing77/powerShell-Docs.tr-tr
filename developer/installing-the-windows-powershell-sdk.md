---
title: Windows PowerShell SDK’sını Yükleme
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845384"
---
# <a name="installing-the-windows-powershell-sdk"></a>Windows PowerShell SDK’sını Yükleme

Şunun için geçerlidir: Windows PowerShell 2.0, Windows PowerShell 3.0

Aşağıdaki konuda farklı Windows sürümleri üzerinde PowerShell SDK'yı yüklemeyi açıklar.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 yükleme Windows 8 ve Windows Server 2012 için SDK'sı

Windows PowerShell 3.0, Windows 8 ve Windows Server 2012 ile otomatik olarak yüklenir. Ayrıca, indirin ve başvuru bütünleştirilmiş kodları için Windows PowerShell 3.0 Windows 8 SDK'ın bir parçası olarak yükleyin. Bu derlemeler cmdlet'leri ve sağlayıcıları ana program için Windows PowerShell 3.0 yazmanıza olanak sağlar. Windows 8 için Windows SDK'yı yüklediğinizde, Windows PowerShell derlemeleri başvurusu derleme klasöründe \Program dosyaları (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0 otomatik olarak yüklenir. Daha fazla bilgi için Windows 8 SDK yükleme sitesine bakın. Windows PowerShell kod örnekleri geliştirme Merkezi'nden de mevcuttur.
Daha fazla bilgi için Geliştirme Merkezi sitesi masaüstü kod örnek sayfasına bakın.

Ayrıca, Windows PowerShell 3.0 geriye dönük olarak uyumludur Windows PowerShell 2.0 SDK kod örnekleri sayısını içerir. Windows PowerShell 2.0 SDK'sını indirme hakkında daha fazla bilgi için aşağıya bakın. (2.0 kod örnekleri Windows 8 ve Windows PowerShell 3.0 ile uyumlu olsa da, Windows 8 platformu üzerinde Windows PowerShell 2.0 uygulamasını yükleyemezsiniz unutmayın.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 yüklenmesi Windows 7 ve Windows Server 2008 R2 için SDK'sı

Otomatik olarak Windows 7 ve Windows Server 2008 R2 PowerShell 2.0 yüklü. Ayrıca, PowerShell 3.0 Bu sistemlerin tümünde yükleyebilirsiniz. (Daha fazla bilgi için Windows PowerShell'i yükleme bakın.). Yukarıda açıklandığı gibi Windows 7 ve Windows Server 2008 R2'de Windows 8 SDK'sını yükleyebilirsiniz.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows PowerShell 2.0 yükleme için Windows 7, Vista, XP, Server 2003 ve Server 2008 SDK'sı

Windows PowerShell 2.0 SDK'sını cmdlet'leri ve sağlayıcıları barındırma uygulamaları yazmak için gereken başvuru derlemelerini sağlar ve sağladığı C# örnek kod, kod yazmaya başladığınızda, başlangıç noktası olarak kullanılabilir.

Bu SDK'yı yüklemek için Windows PowerShell 2.0 SDK'sını bakın.

### <a name="reference-assemblies"></a>Başvuru bütünleştirilmiş kodları

Başvuru bütünleştirilmiş kodları, varsayılan olarak şu konuma yüklenir: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Windows PowerShell 2.0 derlemeleri karşı derlenmiş kod, Windows PowerShell 1.0 yüklemelerde yüklenemiyor. Ancak, Windows PowerShell 1.0 derlemelere karşı derlenmiş kod, Windows PowerShell 2.0 yüklemelerde yüklenebilir.


### <a name="samples"></a>Örnekler

Kod örnekleri, varsayılan olarak şu konuma yüklenir: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. Aşağıdaki bölümlerde, her örnek yapar, kısa bir açıklama sağlayın.

#### <a name="cmdlet-samples"></a>Cmdlet örnekleri

- GetProcessSample01 - nasıl tüm işlemler yerel bilgisayarda alır basit bir cmdlet yazılacağını gösterir.
- GetProcessSample02 - cmdlet'e parametre eklemek nasıl gösterir. Cmdlet'i, bir veya daha fazla işlem adlarını alır ve eşleşen işlem döndürür.
- GetProcessSample03 - ardışık düzendeki girişi kabul parametreleri ekleme gösterir.
- GetProcessSample04 - olmak üzere sonlandırmasız hatalar nasıl ele alınacağını gösterir.
- GetProcessSample05 - belirtilen işlemlerin listesini görüntülemek nasıl gösterir.
- SelectObject - nasıl belirli nesneleri seçmek için bir filtre yazılacağını gösterir.
- SelectString - belirtilen desenle dosyalarını aramak nasıl gösterir.
- StopProcessSample01 - PassThru parametresini gerçekleştirme ve ShouldProcess ve ShouldContinue yöntemlere yapılan çağrılar tarafından kullanıcı geri bildirim istemek nasıl gösterir. Bir nesneyi döndürmek için cmdlet zorlamak istediğinizde kullanıcıları PassThru parametresini belirtin,
- StopProcessSample02 - belirli bir işlemini durdurmak nasıl gösterir.
- StopProcessSample03 - parametreleri için diğer adlar bildirmeyi ve joker karakterleri destekleme gösterir.
- StopProcessSample04 - göstermektedir parametre kümeleri bildirmek cmdlet'i, girdi ve nasıl belirtileceğini kullanacak şekilde varsayılan parametre olarak alan nesne.

#### <a name="remoting-samples"></a>Uzaktan iletişimini örnekleri

- RemoteRunspace01 - uzak bağlantı kurmak için kullanılan bir uzak çalışma alanı oluşturma işlemini gösterir.
- RemoteRunspacePool01 - nasıl bir uzak çalışma alanı havuzu oluşturun ve bu havuzu kullanarak aynı anda birden çok komut çalıştırmak nasıl gösterir.
- Serialization01 - mevcut bir .NET sınıfı arayın ve bu sınıfın seçilen genel özelliklerin bilgilerinden serileştirme/seri durumdan çıkarma işlemi korunur emin olmak nasıl gösterir.
- Serialization02 - mevcut bir .NET sınıfına bakın ve bilgiler sınıfın genel özelliklerini mevcut olmadığında bu sınıfın örneğini bilgilerinden serileştirme/seri durumdan çıkarma işlemi korunur emin olmak nasıl gösterir.
- Serialization03 - mevcut bir .NET sınıfına bakın ve bu sınıfın ve türetilen sınıfların örnekleri (Canlı .NET nesnelerini rehydrated) durumdan emin emin olmak nasıl gösterir.

#### <a name="event-samples"></a>Olay örnekleri

- Event01 - ObjectEventRegistrationBase türetilen bir cmdlet için etkinlik kaydı oluşturma işlemini gösterir.
- Event02 - gösterir nasıl uzak bilgisayarlarda oluşturulan Windows PowerShell olay bildirimleri almak nasıl gösterir. Çalışma alanı sınıfı aracılığıyla kullanıma sunulan PSEventReceived olay kullanır.

#### <a name="hosting-application-samples"></a>Barındırma uygulaması örnekleri

- Runspace01 - çalıştırılacak PowerShell sınıfını kullanmayı gösterir `Get-Process` cmdlet'i zaman uyumlu olarak.
`Get-Process` Cmdlet'i, yerel bilgisayarda çalışan her işlem için işlem nesneleri döndürür.
- Runspace02 - çalıştırılacak PowerShell sınıfını kullanmayı gösterir `Get-Process` ve `Sort-Object` cmdlet'leri zaman uyumlu olarak. `Get-Process` Cmdlet'i, yerel bilgisayarda çalışan her işlem için işlem nesneleri döndürür ve `Sort-Object` kendi kimliği özelliğini temel alarak nesneleri sıralar. DataGridView denetimi kullanarak aşağıdaki komutlardan birini sonuçları görüntülenir.
- Runspace03 - zaman uyumlu olarak bir betik çalıştırmak için PowerShell sınıfı kullanmayı ve sonlandırıcı olmayan hatalara nasıl ele alınacağını gösterir. Betik işlem adları listesini alır ve ardından bu işlemleri alır. Komut dosyası çalıştırılırken oluşturulan sonlandırmayan hatalar dahil olmak üzere betik sonuçlarını konsol penceresinde görüntülenir.
- Komutları çalıştırmak için PowerShell sınıfını kullanmayı ve yakalamak nasıl Runspace04 - gösterir komutlarını çalıştırırken oluşan hatalar sonlandırılıyor. İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişkeni olarak geçirilir. Sonuç olarak, hiçbir nesne döndürülür ve bir sonlandırma hatası oluşturulur.
- Runspace05 - böylece çalışma açıldığında, ek cmdlet kullanılabilir ek InitialSessionState nesneye nasıl ekleneceğini gösterir. Ek bir PowerShell nesnesi kullanarak zaman uyumlu olarak çalıştırılan bir Get-Proc cmdlet (GetProcessSample01 örnek tarafından tanımlanan) sağlar.
- Runspace06 - çalışma açıldığında modül yüklendiğinde InitialSessionState nesneye bir modül eklemek nasıl gösterir. Bir PowerShell nesnesi kullanarak zaman uyumlu olarak çalıştırılan (GetProcessSample02 örnek tarafından tanımlanan) bir Get-Proc cmdlet modülü sağlar.
- Runspace07 - bir çalışma alanı oluşturun ve ardından iki cmdlet, zaman uyumlu olarak bir PowerShell nesnesi kullanarak çalıştırmak için bu çalışma alanı kullanma gösterilmektedir.
- Runspace08 - komut ve bağımsız değişkenler işlem hattının bir PowerShell nesnesi ekleme ve komutları eşzamanlı çalışacak biçimde nasıl gösterir.
- Runspace09 - bir PowerShell nesnesi işlem hattı için bir betik ekleme ve betiği zaman uyumsuz olarak çalıştırmak nasıl gösterir. Olaylar, komut çıktısı işlemek için kullanılır.
- Runspace10 - varsayılan ilk oturum durumu oluşturma, bir cmdlet için InitialSessionState ekleme, ilk oturum durumu kullanan bir çalışma alanı oluşturma ve bir PowerShell nesnesi komutu çalıştırmak amacıyla kullanmak üzere nasıl gösterir.
- Runspace11 - var olan bir cmdlet'i çağırır, ancak kullanılabilir parametreleri kümesini sınırlayan bir ara sunucu komutu oluşturmak için ProxyCommand sınıfını kullanmayı gösterir. Ara sunucu komutunu kısıtlı bir çalışma alanı oluşturmak için kullanılan bir ilk oturum durumunu daha sonra eklenir. Bu, kullanıcının yalnızca ara sunucu komutu cmdlet işlevselliğini erişebileceği anlamına gelir.
- PowerShell01 - InitialSessionState nesnesini kullanarak kısıtlı bir çalışma alanı oluşturma işlemini gösterir.
- PowerShell02 - eşzamanlı olarak birden çok komut çalıştırmak için bir çalışma alanı havuzu kullanmayı gösterir.

#### <a name="host-samples"></a>Konak örnekleri

- Host01 - özel bir ana bilgisayar kullanan bir konak uygulamanın nasıl uygulanacağını gösterir. Özel ana bilgisayarı kullanan bir çalışma alanı oluşturulur, bu örnekte, ve ardından PowerShell API'si "çıkış" çağıran bir betik çalıştırmak için kullanılır Konak uygulama betiği çıktısına arar ve sonuçları yazdırır.
- Host02 - özel ana bilgisayar uygulaması ile birlikte Windows PowerShell'i çalışma zamanı kullanan bir ana bilgisayar uygulaması yazma gösterir. Ana bilgisayar uygulaması çalışır Almanca için konak kültürü ayarlar `Get-Process` cmdlet ve aynı sonuçları görüntüler bkz bunları pwrsh.exe ve geçerli veri ve saat sonra yazdırır Almanca kullanarak.
- Host03 - komutlarını komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir.
- Host04 - komutlarını komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir. Bu ana bilgisayar uygulaması birden çok seçenek belirtmesini sağlayan görüntüleme yönergeleri de destekler.
- Konak05 - komutlarını komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir. Ayrıca bu ana bilgisayar uygulaması kullanarak uzak bilgisayarlara çağrıları destekleyen `Enter-PsSession` ve `Exit-PsSession` cmdlet'leri.
- Host06 - komutlarını komut satırından okur, komutları yürütür ve ardından sonuçları konsolda görüntüler etkileşimli konsol tabanlı konak uygulamanın nasıl oluşturulacağını gösterir. Ayrıca, bu örnek, kullanıcı tarafından girilen metin rengi belirtmek için belirteç Oluşturucu API kullanır.

#### <a name="provider-samples"></a>Sağlayıcısı örnekleri

- AccessDBProviderSample01 - doğrudan CmdletProvider sınıfından türetilen bir sağlayıcı sınıfı nasıl gösterir. Burada yalnızca bütünlük açısından dahil edilmiştir.

- AccessDBProviderSample02 - çağrıları desteklemek için NewDrive ve RemoveDrive yöntemlerini üzerine nasıl gösterir `New-PSDrive` ve `Remove-PSDrive` cmdlet'leri. Bu örnekteki sağlayıcı sınıfı DriveCmdletProvider sınıfından türetilir.

- AccessDBProviderSample03 - çağrıları desteklemek için GetItem ve SetItem yöntemlerini üzerine nasıl gösterir `Get-Item` ve `Set-Item` cmdlet'leri. Bu örnekteki sağlayıcı sınıfı ItemCmdletProvider sınıfından türetilir.

- AccessDBProviderSample04 - çağrıları desteklemek için kapsayıcı yöntemleri üzerine nasıl gösterir `Copy-Item`, `Get-ChildItem`, `New-Item`, ve `Remove-Item` cmdlet'leri. Veri deposu kapsayıcılar olan öğeleri içerdiğinde, bu yöntemleri uygulanmalıdır. Ortak bir üst öğe altında bir alt öğe grubunu bir kapsayıcıdır. Bu örnekteki sağlayıcı sınıfı ItemCmdletProvider sınıfından türetilir.

- AccessDBProviderSample05 - çağrıları desteklemek için kapsayıcı yöntemleri üzerine nasıl gösterir `Move-Item` ve `Join-Path` cmdlet'leri. Bu yöntemler, bir kapsayıcı içindeki öğeleri taşımak gerektiğinde ve veri depolama alanı iç içe geçmiş kapsayıcılar varsa uygulanmalıdır. Bu örnekteki sağlayıcı sınıfı NavigationCmdletProvider sınıfından türetilir.

- AccessDBProviderSample06 - çağrıları desteklemek için içerik yöntemleri üzerine nasıl gösterir `Clear-Content`, `Get-Content`, ve `Set-Content` cmdlet'leri. Veri deposundaki öğelerinin içeriğini yönetmek gerektiğinde bu yöntemleri uygulanmalıdır. Bu örnekteki sağlayıcı sınıfı NavigationCmdletProvider sınıftan türetilen ve IContentCmdletProvider arabirimini uygular.
