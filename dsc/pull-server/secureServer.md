---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Çekme sunucusu en iyi uygulamaları
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079209"
---
# <a name="pull-server-best-practices"></a>Çekme sunucusu en iyi uygulamaları

Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Özet: Bu belge, işlem ve çözüm için hazırlama mühendislerine yardımcı olmak için genişletilebilirlik içerecek şekilde yöneliktir. En iyi müşteriler tarafından tanımlandığı gibi sağlaması gerekir ve ardından önerileri gelecekte kullanıma yönelik iş ve kararlı kabul emin olmak için ürün ekibi tarafından doğrulanması ayrıntıları.

| |Belge bilgileri|
|:---|:---|
Yazar | Michael Greene
Gözden Geçirenler | Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic
Yayımlanmış | Nisan 2015

## <a name="abstract"></a>Özet

Bu belge, herhangi bir Windows PowerShell Desired State Configuration çekme sunucusu uygulaması için planlama için resmi bir Rehber sunmak için tasarlanmıştır. Bir çekme sunucusu dağıtmak için yalnızca dakika süren basit bir hizmettir. Bu belgede bir dağıtımda kullanılan teknik nasıl yapılır kılavuzları sunar ancak bu belgenin en iyi yöntemler ve dağıtmadan önce dikkat etmeniz gerekenler için başvuru değerdir.
Okuyucular DSC temel olarak bilindiğini olmalıdır ve bileşenlerini açıklamak için kullanılan terimler, DSC dağıtımında yer alır. Daha fazla bilgi için [Windows PowerShell Desired State Configuration genel](/powershell/dsc/overview) konu.
DSC bulut temposunda gelişmesinin beklendiği gibi çekme sunucusu da dahil olmak üzere temel alınan teknoloji geliştirilebilen ve yeni özellikleri tanıtmak için de beklenmektedir. Bu belgenin önceki sürümlerine başvuruları ve başvurular forward-looking tasarımı teşvik etmek için gelecekteki görünümlü çözümler sağlayan ek bir sürüm tablosunu içerir.

Bu belgenin iki ana bölümü:

- Yapılandırma planlaması
- Yükleme Kılavuzu

### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework sürümleri

Bu belgedeki bilgiler için Windows Management Framework 5.0 uygulamak için tasarlanmıştır. WMF 5.0 dağıtmak için gerekli değildir ve bu belgenin odak olduğu bir çekme sunucusu sürüm 5.0 işletim olsa da.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

Desired State Configuration ' nı (DSC), ortak bilgi modeli (CIM) tanımlamak için Yönetilen Nesne Biçimi (MOF) adlı bir endüstri sözdizimini kullanarak dağıtma ve yönetme, yapılandırma verilerini sağlayan bir yönetim platformudur. Bu standartlar, geliştirme platformları arasında Linux da dahil olmak üzere daha fazla ve ağ donanım işletim sistemleri için açık Yönetim Altyapısı (OMI) açık kaynaklı proje yok. Daha fazla bilgi için [MOF belirtimlerine bağlama DMTF sayfa](https://www.dmtf.org/standards/cim), ve [OMI belgeler ve kaynak](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell Desired State Configuration oluşturmak ve bildirim temelli yapılandırmalar yönetmek için kullanabileceğiniz için dil uzantıları sunmaktadır.

### <a name="pull-server-role"></a>Çekme sunucusu rolü

Hedef düğümler için erişilebilir olacak yapılandırmaları depolamak için merkezi bir hizmete bir çekme sunucusu sağlar.

Çekme sunucusu rolü, bir Web sunucusu örneğine veya bir SMB dosya paylaşımı dağıtılabilir. Web sunucusu özelliği, bir OData arabirimi içerir ve yapılandırmaları uygulandıkça başarı veya başarısızlık onayı geri bildirmek hedef düğümler için özellikleri isteğe bağlı olarak içerebilir. Bu işlevsellik, ortamlarında yararlıdır bulunduğu çok sayıda hedef düğümleri.
Son yapılandırmayı çekme sunucusuna işaret etmek için bir hedef düğümü (bir istemci olarak da bilinir) yapılandırdıktan sonra verileri ve gerekli tüm betikleri indirilen uygulanan ve. Bu tek seferlik bir dağıtım veya değişiklik uygun ölçekte yönetmek için önemli bir varlık da çekme sunucusu olmasını sağlayan yeniden tekrarlanan bir iş olarak gerçekleşebilir. Daha fazla bilgi için [Windows PowerShell Desired State Configuration çekme sunucuları](/powershell/dsc/pullServer) ve

[Gönderme ve çekme yapılandırma modlarından](/powershell/dsc/pullServer).

## <a name="configuration-planning"></a>Yapılandırma planlaması

Tüm kurumsal yazılım dağıtımı için doğru mimari planlamanıza yardımcı olacak ve dağıtımını tamamlamak için gereken adımları için hazırlıklı olmak için önceden toplanan bilgileri yoktur. Aşağıdaki bölümler, hazırlama ve büyük olasılıkla önceden yapılması gereken Kurumsal bağlantıları ile ilgili bilgi sağlar.

### <a name="software-requirements"></a>Yazılım gereksinimleri

Bir çekme sunucusu dağıtımını DSC hizmeti özelliği Windows Server'ın gerektirir. Bu özellik, Windows Server 2012'de kullanıma sunulmuştur ve devam eden yayınlar Windows Management Framework (WMF) güncelleştirildi.

### <a name="software-downloads"></a>Yazılım yüklemeleri

Windows Update'ten en yeni içerik yüklemenin yanı sıra, bir DSC çekme sunucusuna dağıtmak için en iyi uygulama olarak kabul iki yüklemeleri vardır: Windows Management Framework'ün en son sürümünü ve otomatik hale getirmek için DSC modülünü sunucu sağlama çekin.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 DSC hizmeti adlı bir özellik içerir. DSC hizmeti özelliğini destekleyen OData uç noktasını ikili dosyaları dahil olmak üzere çekme sunucusu işlevselliği sağlar.
WMF Windows Server'a dahil edilmiştir ve Windows Server sürümleri arasında bir Çevik temposu güncelleştirilir. [WMF 5.0 yeni sürümlerini](https://www.microsoft.com/en-us/download/details.aspx?id=54616) DSC hizmeti özelliği için güncelleştirmeleri içerebilir. Bu nedenle, buna WMF'ın en son sürümünü indirin ve yayın DSC hizmeti özelliği için bir güncelleştirme içerip içermediğini belirlemek için sürüm notlarını gözden geçirmek için en iyi yöntem var. Bir güncelleştirme veya senaryo için Tasarım Durumu kararlı veya Deneysel olarak listelenip listelenmediğini gösterir sürüm notlarını bölümünü de gözden geçirmelisiniz.
Tek tek özellikler kararlı bildirilebilir bir Çevik sürüm döngüsü için izin vermek için özellik gösteren WMF önizlemede bile yayımlanır ancak bir üretim ortamında kullanılmak üzere hazırdır.
Tarihsel olarak güncelleştirilip güncelleştirilmediğini diğer özellikler tarafından WMF sürümleri (daha fazla ayrıntı için WMF sürüm notlarına bakın):

- Windows PowerShell Windows PowerShell Tümleşik komut dosyası
- Ortamı (ISE) Windows PowerShell Web Hizmetleri (Yönetim OData
- IIS uzantısı) Windows PowerShell Desired State Configuration (DSC)
- Windows Uzaktan Yönetim (WinRM) Windows Yönetim Araçları (WMI)

### <a name="dsc-resource"></a>DSC kaynak

Bir çekme sunucusu dağıtımı, sağlama hizmetini kullanarak bir DSC yapılandırma betiği tarafından basitleştirilebilir. Bu belge, üretime hazır sunucu düğümünü dağıtmak için kullanılan yapılandırma betiklerini içerir. Yapılandırma komut dosyaları kullanmak için bir DSC modülünü diğer bir deyişle gereklidir Windows Server'a dahil değildir. Gerekli modül adı **xPSDesiredStateConfiguration**, DSC kaynağı içeren **xDscWebService**. XPSDesiredStateConfiguration modülü indirilebilir [burada](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Kullanım `Install-Module` cmdlet'inden **PowerShellGet** modülü.

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** modül modülünü yükleyin:

`C:\Program Files\Windows PowerShell\Modules`

Görev Planlama|
---|
Windows Server 2012 R2 için yükleme dosyalarına erişimi?|
Dağıtım ortamı WMF ve modülü çevrimiçi galeriden indirmek için Internet erişimi gerekir?|
Nasıl işletim sistemi yüklendikten sonra en son güvenlik güncelleştirmelerini yükler mi?|
Ortam, güncelleştirmeleri almak için Internet erişimi gerekir veya yerel bir Windows Server Update Services (WSUS) sunucu gerekir?|
Çevrimdışı ekleme aracılığıyla güncelleştirmeleri içeren Windows Server yükleme dosyalarını erişim zorunda mıyım?|

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Çekme sunucusuna dağıtımlar, sanal ve fiziksel sunucularda desteklenir. Çekme sunucusu boyutlandırma gereksinimlerini, Windows Server 2012 R2 gereksinimleri ile hizalar.

CPU: 1,4 GHz 64 bit işlemci bellek: 512 MB Disk alanı: 32 GB ağ: Gigabit Ethernet Bağdaştırıcısı

Görev Planlama|
---|
Fiziksel donanım üzerinde veya bir sanallaştırma platformunda dağıtacak mısınız?|
Hedef ortamınız için yeni bir sunucu isteği işlemi nedir?|
Bir sunucu kullanılabilir hale gelmesi için ortalama amortisman süresini nedir?|
Hangi boyutu sunucu, ister?|

### <a name="accounts"></a>Hesaplar

Bir çekme sunucusu örneği dağıtmak için hizmet hesabı gereksinimi yoktur.
Bununla birlikte, burada Web sitesi bir yerel kullanıcı hesabının bağlamında çalıştırabilirsiniz senaryo vardır.
Örneğin, bir gereksinimi varsa Web sitesi içeriğini ve Windows Server veya depolama paylaşımı barındıran cihaz için bir depolama paylaşmak erişimi olmayan etki alanına katılmış.

### <a name="dns-records"></a>DNS kayıtları

Bir çekme sunucusu ile çalışacak şekilde istemciler yapılandırırken kullanılacak bir sunucu adı gerekir.
Test ortamları genellikle sunucusu konak adı kullanılır veya sunucunun IP adresini DNS ad çözümleme mevcut değilse kullanılabilir.
Üretim ortamlarında ya da bir laboratuvar ortamında Üretim dağıtımı temsil etmesi hedeflenen bir DNS CNAME kaydı oluşturmak için en iyi yöntem olacaktır.

Bir DNS CNAME için konak (A) kaydı başvurmak için bir diğer ad oluşturmanızı sağlar.
Ek ad kaydı amacı esneklik bir değişiklik gelecekte gerekli olmalıdır artırmaktır.
CNAME değişikliği bir çekme sunucusu değiştirmek veya ek çekme sunucuları ekleme gibi sunucu ortamı için istemci yapılandırması için karşılık gelen değişiklik yapılması gerekmez, istemci yapılandırması yalıtmaya yardımcı olabilir.

DNS kaydı için bir ad seçerken çözüm mimarisini göz önünde bulundurun.
Kullanarak Yük Dengelemesi, trafik HTTPS üzerinden güvenli hale getirmek için kullanılan sertifikanın DNS kayıt olarak aynı adı paylaşan gerekecektir.

Senaryo |En iyi uygulama
:---|:---
Test ortamı |Planlı bir üretim ortamına mümkünse yeniden oluşturun. Bir sunucu ana bilgisayar adı, basit yapılandırmaları için uygundur. DNS kullanılamıyorsa, bir IP adresi yerine ana bilgisayar adı kullanılabilir.|
Tek düğümlü dağıtım |Sunucu ana bilgisayar adı için bir DNS CNAME kaydı oluşturun.|

Daha fazla bilgi için [yapılandırma DNS hepsini bir kez deneme Windows Server'da](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Görev Planlama|
---|
Oluşturulan ve değiştirilen DNS kayıtları kişiye kimin biliyor musunuz?|
DNS kaydı için bir istek için ortalama bir döngü nedir?|
Sunucular için statik bir ana bilgisayar (A) kayıt isteği gerekiyor mu?|
Ne bir CNAME ister?|
Gerekli olursa, ne tür yük dengeleme çözümü, yararlanacaktır? (Ayrıntılar için Yük Dengeleme başlıklı bölümüne bakın)|

### <a name="public-key-infrastructure"></a>Ortak anahtar altyapısı

Çoğu kuruluş, ağ trafiğini, özellikle nasıl sunucuları yapılandırılır, bu gibi hassas veriler içeren trafiği gerekir doğrulandı ve/veya aktarım sırasında şifrelenir, bugün gerektirir.
Kolaylaştıran HTTP kullanarak bir çekme sunucusu dağıtmayı mümkün olmakla birlikte istemci isteklerinde metni silin, HTTPS kullanan güvenli trafiği için en iyi bir yöntemdir. Hizmet, DSC kaynak parametreleri kümesini kullanarak HTTPS kullanacak şekilde yapılandırılabilir **xPSDesiredStateConfiguration**.

Çekme sunucusu için HTTPS trafiğinin güvenliğini sağlamak için sertifika gereksinimleri, herhangi bir HTTPS web sitesini güvenli hale getirme değerinden farklı değildir. **Web sunucusu** şablon bir Windows Server Sertifika Hizmetleri'nde gerekli yeteneklerin karşılar.

Görev Planlama|
---|
Sertifika isteklerini otomatik olarak yapılmaz, kimin bir sertifika isteklerini başvurun gerekecek mi?|
İstek için ortalama bir döngü nedir?|
Nasıl sertifika dosyası için aktarılır?|
Nasıl sertifika özel anahtarını size aktarılır?|
Varsayılan zaman aşımı süresi ne kadardır?|
Sertifika adı için kullanabileceğiniz çekme sunucusu ortamı için bir DNS adı kapatılan?|

### <a name="choosing-an-architecture"></a>Bir mimari seçme

Bir çekme sunucusu, IIS veya bir SMB dosya paylaşımında barındırılan ya da bir web hizmeti kullanılarak dağıtılabilir. Çoğu durumda, web hizmeti seçeneği daha fazla esneklik sağlar. SMB trafiği genellikle filtrelendiğine veya ağlar arasında engellenen ise ağ sınırlarını geçmesini HTTPS trafiği için sık karşılaşılan bir durum değil. Web hizmeti ayrıca uyumluluk sunucu veya istemciler merkezi görünüm için bir sunucuya geri durumu raporlamak için bir mekanizma sağlar. bir Web raporlama Yöneticisi (Bu belgenin ileriki bir sürümde ele alınması için iki konuları) içerecek şekilde seçeneği de sunar.
SMB, bir web sunucusu rolü istenmeyen olun diğer ortam gereksinimleri yanı sıra, burada bir web sunucusu kullanılmadı ilke belirleyen ortamları için bir seçenek sunar.
İmzalama ve trafiği şifreleme gereksinimlerini değerlendirmek her iki durumda da unutmayın. HTTPS, SMB imzalama ve IPSec ilkelerini dikkate değer tüm seçenekler değildir.

#### <a name="load-balancing"></a>Yük Dengeleme

Web hizmetiyle etkileşim kurmanın istemciler, tek bir yanıtta döndürülen bilgileri için bir istek olması. Yük Dengeleme oturumları zaman içinde herhangi bir noktada tek bir sunucuda tutulur emin olmak için platform için gerekli olmadığından sıralı istek gereklidir.

Görev Planlama|
---|
Yükü sunucular arasında trafiği Dengeleme için çözümün ne kullanılacak mı?|
Yeni bir yapılandırma için bir cihaz eklemek için bir istek sürecek olan bir donanım yük dengeleyicisi kullanıyorsanız?|
Yeni bir yük yapılandırmak bir istek için ortalama bir döngü nedir, web hizmeti dengeli?|
Hangi bilgilerin istek için gerekli olacak mı?|
Yük dengelemeden sorumlu takım, işleyecek veya ek IP istemek gerekir?|
Gerekli DNS kayıtlarını var ve bu, yük dengeleme çözümü yapılandırmak için sorumlu ekip tarafından gerekir?|
Yük Dengeleme çözümü PKI cihaz tarafından ele alınması gerekmez veya hiçbir oturum gereksinimleri var olduğu sürece, HTTPS trafiği Dengeleme yükleyebilir?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Yapılandırmaları ve modülleri çekme sunucusunda hazırlama

Yapılandırma planlaması kapsamında, hangi DSC hakkında modülleri ve yapılandırmaları çekme sunucusu tarafından barındırılacak düşünmeniz gerekir. Yapılandırmayı planlamak amacıyla hazırlamak ve içeriği bir çekme sunucusuna dağıtmak nasıl temel bir anlayış sağlamak önemlidir.

İleride bu bölümde genişletilmiş ve DSC çekme sunucusu için bir işlemler Kılavuzu'nda dahil.  Otomasyon ile zaman içinde modülleri ve yapılandırmaları yönetmek için günlük işlem kılavuzu ele alınacaktır.

#### <a name="dsc-modules"></a>DSC modülleri

Bir yapılandırma isteyen istemcilerin gerekli DSC modülleri gerekir. Bir çekme sunucusu isteğe bağlı bir dağıtım istemcilere DSC modüllerinin otomatikleştirmek için bir işlevdir. İlk kez, belki de bir laboratuvar veya kavram kanıtı olarak bir çekme sunucusu dağıtıyorsanız, büyük olasılıkla PowerShell Galerisi gibi genel depolar veya PowerShell.org GitHub depoları DSC modüller için kullanılabilir olan DSC modülleri bağlıdır oluşturacağınız .

Bile güvenilir çevrimiçi kaynakları için PowerShell Galerisi gibi genel bir depodan indirilen herhangi bir modülü kişi tarafından PowerShell deneyimini ve modülleri olduğu ortamın bilgi ile incelenmelidir olduğunu unutmamak önemlidir Üretim ortamında kullanılan önce kullanılır. Bu görevi tamamlanırken herhangi ek belgeler ve örnek betikler gibi kaldırılabilir modül yükünde denetlemek için zamanı geldi. Modüller, sunucudan istemciye ağ üzerinden indirilecek olduğunda bu ilk talebinde istemci başına ağ bant genişliğini azaltır.

Her modülü, belirli bir biçimde, modül yükünü içeren ModuleName_Version.zip adında bir ZIP dosyasına paketlenmesi gerekir. Dosyayı sunucuya kopyalandıktan sonra bir sağlama toplamı dosyasına oluşturulmalıdır. İstemcilerin sunucuya bağlandığınızda, sağlama toplamını yayımlandıktan sonra DSC modülünün içerik değiştirilmedi doğrulamak için kullanılır.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Görev Planlama|
---|
Bir test veya Laboratuvar ortamına planlıyorsanız hangi senaryolarını doğrulamak için anahtar misiniz?|
İhtiyacınız olan her şey karşılamak için kaynakları içeren genel olarak kullanılabilir modüllerin vardır veya kendi kaynaklarını Yazar gerekir?|
Ortamınızı ortak modüller almak için Internet erişimi gerekir?|
Kimin DSC modülleri gözden geçirmek için sorumlu olacak?|
Bir üretim ortamında planlıyorsanız ne yerel bir depo DSC modülleri depolamak için kullanacağınız?|
Merkezi bir ekip, uygulama ekipleri DSC modüllerden kabul eder? Hangi işlem olacak mı?|
Paketleme, kopyalama ve üretime hazır DSC modüller için sağlama toplamı sunucusuna kaynak deponuzdan oluşturma otomatik hale?|
Takım, Otomasyon platformu da yönetmekten sorumlu olacak?|

#### <a name="dsc-configurations"></a>DSC yapılandırmaları

Bir çekme sunucusu amacı, DSC yapılandırmaları istemci düğümlerine dağıtmak için merkezi bir mekanizma sağlamaktır. Yapılandırma sunucusunda MOF belgeleri olarak depolanır.
Her belgenin benzersiz bir ile adlandırılacağını **GUID**. İstemciler, bir çekme sunucusuna bağlanmak üzere yapılandırıldığında, kendisine de verilir **GUID** istek yapılandırması. Bu sistem yapılandırmaları tarafından başvuru **GUID** genel benzersizliği garanti eder ve düğüm başına ya da kapsayan olması gereken birçok sunucusu rolü yapılandırması ayrıntı düzeyi içeren bir yapılandırma uygulanabilir olduğunu esnektir aynı yapılandırmaları.

#### <a name="guids"></a>GUID'ler

İçin yapılandırma planlaması **GUID'leri** ek dikkat çekme sunucu dağıtımı düşünürken, büyük. İşlemek nasıl özel bir gereksinimi yoktur **GUID'leri** ve büyük olasılıkla her ortam için benzersiz bir işlemdir. İşlem basitten için karmaşık değişebilir: merkezi olarak depolanan bir CSV dosyası, basit bir SQL tablosunu, bir CMDB veya başka bir aracı ya da yazılım çözümü ile tümleştirme gerektiren karmaşık bir çözüm. İki genel yaklaşım vardır:

- **Sunucu başına GUID'leri atama** — bir ölçü her sunucu yapılandırması ayrı ayrı kontrol güvence sağlar. Bu güncelleştirmeleri etrafında duyarlılık düzeyi sağlar ve bazı sunucularla ortamlarda da çalışabilir.
- **GUID'ler her sunucu rolü atama** — web sunucuları gibi aynı işlevi gerçekleştirir tüm sunucuların gerekli yapılandırma verileri başvurmak için aynı GUID'ni kullanın.  Birçok sunucuya aynı GUID paylaşıyorsanız, yapılandırma değiştiğinde tümünün aynı anda güncelleştirilecek olduğunu unutmayın.

  GUID zeka nasıl sunucularına dağıtılır ve ortamınızda yapılandırılmış hakkında sağlamaya kötü amaçlı bir eyleme sahip biri tarafından kullanılabilir çünkü, hassas verileri düşünülmesi gereken bir şeydir. Daha fazla bilgi için [güvenli bir şekilde PowerShell Desired State Configuration çekme modunda GUID'leri ayrılırken](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Görev Planlama|
---|
Kimin hazır olduğunuzda, yapılandırma çekme sunucu klasörüne kopyalamak için sorumlu olacak?|
Bir uygulama ekibi tarafından yapılandırmaları yazılmışsa ne işlemi bunları devre dışı el olacak?|
Bunlar, takımlar arasında yazılmış iş olarak yapılandırmaları depolamak için bir depo özelliğinden yararlanır?|
Yapılandırmaları sunucuya kopyalamak ve hazır olduğunuzda, bir sağlama toplamı oluşturma işlemini otomatik hale?|
Sunucular veya roller için GUID'leri nasıl eşler ve bu depolanacağı?|
Neler işlem olarak istemci makineleri yapılandırmak için kullanacağınız ve bu işlemle oluşturma ve yapılandırma, GUID'leri depolama için nasıl tümleştirilecek?|

## <a name="installation-guide"></a>Yükleme Kılavuzu

*Bu belgede verilen komut kararlı verilebilir. Her zaman betikleri dikkatle bir üretim ortamında yürütmeden önce gözden geçirin.*

### <a name="prerequisites"></a>Önkoşullar

Sunucunuzdaki PowerShell sürümünü doğrulamak için aşağıdaki komutu kullanın.

```powershell
$PSVersionTable.PSVersion
```

Mümkünse, Windows Management Framework'ün en son sürüme yükseltin.
Ardından, indirme `xPsDesiredStateConfiguration` aşağıdaki komutu kullanarak modülü.

```powershell
Install-Module xPSDesiredStateConfiguration
```

Komut modülünü yüklemeden önce onay ister.

### <a name="installation-and-configuration-scripts"></a>Yükleme ve yapılandırma betikleri

DSC çekme sunucusunu dağıtmak için en iyi yöntem, bir DSC yapılandırma betiği kullanmaktır. Bu belge her iki temel ayarları yalnızca DSC web hizmeti yapılandırırsınız ve gelişmiş bir Windows Server uçtan uca dahil olmak üzere DSC web hizmeti yapılandırdığınız ayarlar dahil olmak üzere komut dosyaları sunar.

Not:  Şu anda `xPSDesiredStateConfiguration` DSC modülü, sunucunun EN-US yerel ayarını olmasını gerektirir.

### <a name="basic-configuration-for-windows-server-2012"></a>Windows Server 2012 için temel yapılandırma

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Windows Server 2012 R2 için Gelişmiş Yapılandırma

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>Çekme sunucusu işlevselliği doğrulayın

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>İstemcilerini yapılandırma

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>Ek başvurular, kod parçacıkları ve örnekleri

Bu örnek, test etmek için (WMF5 gerektirir) istemci bağlantısı manuel olarak başlatmak nasıl gösterir.

```powershell
Update-DscConfiguration –Wait -Verbose
```

[Ekle DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet'i, bir tür CNAME kaydı bir DNS bölgesine eklemek için kullanılır.

PowerShell işleve [sağlama toplamı ve DSC MOF yayımlama SMB çekme sunucusu oluşturma](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) gerekli sağlama toplamı otomatik olarak oluşturur ve sonra MOF yapılandırma ve sağlama toplamı dosyaları SMB çekme sunucusuna kopyalar.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Ek - anlama ODATA hizmeti verilerini dosya türleri

Bir veri dosyası, bilgi OData web hizmetini içeren bir çekme sunucusu dağıtımı sırasında oluşturulacak depolanır. Dosya türü aşağıda açıklandığı gibi işletim sistemine bağlıdır.

- **Windows Server 2012** dosya türü her zaman .mdb olur
- **Windows Server 2012 R2** yapılandırmada bir .mdb belirtilmediği sürece, dosya türü için .edb varsayılan olur

İçinde [örnek betiğini Gelişmiş](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) bir çekme sunucusu yüklemek için otomatik olarak her dosya türüne göre neden olduğu hata olasılığını önlemek için web.config dosyası ayarlarını denetlemek nasıl bir örnek de bulabilirsiniz.
