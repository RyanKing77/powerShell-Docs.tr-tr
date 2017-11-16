---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Çekme Server en iyi uygulamalar"
ms.openlocfilehash: 66b97f4edb43926866b39731d720a2dc8c91eb2e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="pull-server-best-practices"></a>Çekme Server en iyi uygulamalar

>İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Özeti: Bu belgede işlem ve çözüm için hazırlama mühendisleri yardımcı olmak için genişletilebilirlik dahil olmak üzere tasarlanmıştır. En iyi yöntemler müşteriler tarafından tanımlandığı gibi sağlaması gerekir ve öneriler gelecekte kullanıma yönelik ve kararlı kabul emin olmak için ürün ekibi tarafından doğrulanmış ayrıntıları.

| |Belge bilgileri|
|:---|:---|
Yazar | Michael Greene  
Gözden Geçirenler | Ben Gelens, Ravikanth Chaganti Aleksandar Nikolic  
Yayımlanan | Nisan 2015

## <a name="abstract"></a>Özet

Bu belge, herkes için bir Windows PowerShell istenen durum yapılandırması çekme sunucu uygulama planlama için resmi bir kılavuz sağlamak için tasarlanmıştır. Bir çekme sunucusuna dağıtmak için yalnızca dakika sürer basit bir hizmettir. Bu belgede bir dağıtımda kullanılan teknik nasıl yapılır yönergeleri sunacaktır karşın, bu belgenin en iyi yöntemler ve ne dağıtmadan önce hakkında düşünmek için bir başvuru olarak değerdir.
Okuyucular DSC temel olarak bilindiğini olmalıdır ve bileşenleri açıklamak için kullanılan terimler bir DSC dağıtımda dahil edilen. Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırması genel bakış](https://technet.microsoft.com/en-us/library/dn249912.aspx) konu.
Bulut tempoyla gelişmesi DSC beklendiği gibi çekme sunucusuna da dahil olmak üzere temel alınan teknoloji gelişmesi ve yeni özellikleri tanıtan için de beklenmektedir. Bu belgenin önceki sürümlerden başvuruları ve forward-looking tasarımları teşvik eden gelecekteki görünümlü çözümler başvurular sağlayan ek bir sürüm tablosunu içerir.

Bu belgenin iki ana bölümleri:

 - Yapılandırmasını planlama
 - Yükleme Kılavuzu
 
### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework sürümleri 
Bu belgedeki bilgiler Windows Management Framework 5.0 uygulamak için tasarlanmıştır. WMF 5.0 dağıtma ve çekme sunucu işletim için gerekli olmamasına karşın, sürüm 5.0, bu belgenin odak noktasıdır.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell istenen durum yapılandırması
İstenen durum Yapılandırması'nı (DSC) ortak bilgi modeli (CIM) tanımlamak için Yönetilen Nesne Biçimi (MOF) adlı bir endüstri sözdizimini kullanarak dağıtma ve yönetme yapılandırma verilerini sağlayan bir yönetim platformudur. Bu standartlar geliştirilmesini Linux dahil olmak üzere platformları arasında daha ayrıntılı ve ağ donanım işletim sistemleri için açık Yönetim Altyapısı (OMI) açık kaynaklı proje yok. Daha fazla bilgi için bkz: [MOF belirtimlerine bağlama DMTF sayfa](http://dmtf.org/standards/cim), ve [OMI belgeler ve kaynak](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell oluşturmak ve bildirim temelli yapılandırmaları yönetmek için kullanabileceğiniz ve istenen durum yapılandırması için bir dizi dil uzantıları sağlar.

### <a name="pull-server-role"></a>Çekme sunucu rolü  
Bir çekme sunucu hedef düğümleri için erişilebilir yapılandırmaları depolamak için merkezi bir hizmet sunar.
 
Çekme sunucu rolü, Web sunucusu örneğine veya bir SMB dosya paylaşımı dağıtılabilir. Web sunucusu özelliği bir OData arabirimi içerir ve isteğe bağlı olarak hedef düğümleri yapılandırmaları uygulanmış olarak başarı veya başarısızlık onayı geri bildirmek için özellikleri içerebilir. Bu işlevsellik ortamlarda kullanışlıdır çok sayıda hedef düğümleri olduğu. En son yapılandırma çekme sunucusuna işaret etmek için (bir istemci olarak da bilinir) bir hedef düğümü yapılandırdıktan sonra veri ve tüm gerekli komut dosyalarını karşıdan uygulanan ve. Bu bir kerelik dağıtımı veya kılan de çekme sunucunun önemli bir varlık değişikliği ölçekte yönetmek için yeniden tekrarlanan bir iş olarak meydana gelebilir. Daha fazla bilgi için bkz: [Windows PowerShell istenen durum yapılandırma çekme sunucularına](https://technet.microsoft.com/en-us/library/dn249913.aspx) ve [anında iletme ve çekme yapılandırma modlarından](https://technet.microsoft.com/en-us/library/dn249913.aspx).

## <a name="configuration-planning"></a>Yapılandırmasını planlama

Tüm kurumsal yazılım dağıtımı için doğru mimari planlamanıza yardımcı olması için ve dağıtımını tamamlamak için gereken adımları için hazırlıklı olmak için önceden toplanan bilgileri yoktur. Aşağıdaki bölümler nasıl hazırlanacağı ve büyük olasılıkla önceden gerçekleşmesi gerekir kuruluş bağlantıları ile ilgili bilgiler sağlar.

### <a name="software-requirements"></a>Yazılım gereksinimleri

Bir çekme sunucusuna dağıtımını DSC hizmeti özelliği Windows Server'ın gerektirir. Bu özellik, Windows Server 2012'de sunulmuştur ve devam eden sürümleri Windows Management Framework (WMF) güncelleştirildi.

### <a name="software-downloads"></a>Yazılım yüklemeleri

Windows Update'ten en son içerik yüklemenin yanı sıra, bir DSC çekme sunucusuna dağıtmak için en iyi yöntem olarak kabul iki yüklemeleri vardır: Windows Management Framework ve DSC modülü sunucu çekme sağlama otomatik hale getirmek için en son sürümünü.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 DSC hizmeti adlı bir özellik içerir. DSC hizmeti özelliğini destekleyen OData uç noktasını ikili dosyaları dahil olmak üzere çekme sunucu işlevselliği sağlar. WMF Windows Server'a dahil edilmiştir ve Windows Server sürümleri arasında Çevik bir tempoyla üzerinde güncelleştirilir. [WMF 5.0 yeni sürümlerini](http://aka.ms/wmf5latest) DSC servis özelliği için güncelleştirmeleri içerebilir. Bu nedenle, bu en iyi WMF en son sürümü karşıdan yüklemek ve yayın DSC hizmeti özelliği için bir güncelleştirme içerip içermediğini belirlemek için sürüm notlarını gözden geçirmek için uygulamadır. Bir güncelleştirme veya senaryo için Tasarım Durumu kararlı veya Deneysel olarak listelenip listelenmediğini gösteren Sürüm Notları bölümünü incelemeniz de gerekir. Tek tek özellikleri kararlı bildirilebilir bir Çevik yayın döngüsü için izin vermek için özellik gösterir WMF Önizleme'de serbest bile olsa bir üretim ortamında kullanılmak üzere hazırdır.
Geçmişten bu yana güncelleştirilen diğer özellikleri (bkz. daha fazla ayrıntı için WMF sürüm notları) WMF sürümleri tarafından:

 - Windows PowerShell Windows PowerShell Tümleşik komut dosyası
 - (Yönetim OData ortamı (ISE) Windows PowerShell Web Hizmetleri
 - IIS uzantısı) Windows PowerShell istenen durum yapılandırması (DSC)
 - Windows Uzaktan Yönetim (WinRM) Windows Yönetim Araçları (WMI)

### <a name="dsc-resource"></a>DSC kaynağı

Bir çekme sunucu dağıtımı DSC yapılandırma betiği kullanarak hizmet sağlama tarafından basit hale getirilebilir. Bu belge, bir üretim hazır sunucu düğümü dağıtmak için kullanılan yapılandırma komut dosyaları içerir. Yapılandırma komut dosyaları kullanmak için DSC modülü diğer bir deyişle gereklidir Windows Server'da dahil değildir. Gerekli modül adı **xPSDesiredStateConfiguration**, DSC kaynağı içeren **xDscWebService**. XPSDesiredStateConfiguration modülü indirilebilir [burada](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Kullanım **yükleme-Module** cmdlet'inden **PowerShellGet** modülü.

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** modül için modülü yükleyin: 

`C:\Program Files\Windows PowerShell\Modules`

Görev Planlama|
---|
Windows Server 2012 R2 için yükleme dosyalarına erişimi?|
Dağıtım ortamı WMF ve modül çevrimiçi galeriden indirmek için Internet erişimi olacak mı?|
Nasıl işletim sisteminin yükledikten sonra en son güvenlik güncelleştirmelerini yükler mi?|
Ortam güncelleştirmeleri almak için Internet erişimine sahip olur veya yerel bir Windows Server Update Services (WSUS) sunucusu gerekir?|
Erişim zaten çevrimdışı ekleme işlemi aracılığıyla güncelleştirmeleri içeren Windows Server yükleme dosyalarını gerekiyor?|

### <a name="hardware-requirements"></a>Donanım gereksinimleri

Çekme sunucusuna dağıtımlar, hem fiziksel hem de sanal sunucularda desteklenir. Windows Server 2012 R2 için gereksinimlerle çekme server boyutlandırma gereksinimleri hizalayın.

CPU: 1,4 GHz 64-bit işlemci  
Bellek: 512 MB  
Disk alanı: 32 GB  
Ağ: Gigabit Ethernet Bağdaştırıcısı  

Görev Planlama|
---|
Fiziksel donanım üzerinde veya bir sanallaştırma platformunda dağıtacak mısınız?|
Hedef ortamınız için yeni bir sunucu isteği işlemi nedir?|
Bir sunucu kullanılabilir hale gelmesi için ortalama bir döngü süresi nedir?|
Hangi boyutu sunucu, ister?|

### <a name="accounts"></a>Hesaplar

Bir çekme server örneği dağıtmak için hizmet hesabı gereksinimi yoktur. Ancak, Web sitesi yerel bir kullanıcı hesabı bağlamında çalıştırdığı senaryo vardır. Örneğin, bir gereksinimi varsa Web sitesi içeriğini ve Windows Server veya depolama paylaşımı barındırma aygıtı için bir depolama paylaşmak erişimi olmayan etki alanına katılmış.

### <a name="dns-records"></a>DNS kayıtları

Bir çekme sunucu ortamı ile çalışmak için istemciler yapılandırırken kullanılacak bir sunucu adı gerekir. Sınama ortamlarında sunucusu konak adı genellikle kullanılan veya DNS ad çözümlemesi kullanılamıyorsa, sunucunun IP adresini kullanılabilir. Üretim ortamlarında ya da bir laboratuvar ortamında Üretim dağıtımı temsil etmek üzere tasarlanmıştır bir DNS CNAME kaydı oluşturmak için en iyi yöntem olacaktır.

Bir DNS CNAME, ana bilgisayar (A) kaydı başvurmak için bir diğer ad oluşturmanızı sağlar. Ek ad kaydı amacı, bir değişiklik gelecekte gerekip gerekmeyeceğini esneklik artırmaktır. CNAME değişiklikler çekme sunucusunu değiştirme ya ek çekme sunucuları ekleme gibi sunucu ortamınıza karşılık gelen bir istemci yapılandırmasında değişiklik gerektirmez istemci yapılandırmasını ayırmaya yardımcı olabilir.

DNS kaydı için bir ad seçerken, çözüm mimarisi göz önünde bulundurun. Kullanarak Yük Dengelemesi, trafik HTTPS üzerinden güvenli hale getirmek için kullanılan sertifikanın DNS kaydı olarak aynı adı paylaşan gerekecektir. 

Senaryo |En iyi uygulama
:---|:---
Sınama Ortamı |Planlanan bir üretim ortamına mümkünse yeniden oluşturun. Sunucu ana bilgisayar adı basit yapılandırmaları için uygundur. DNS kullanılamıyorsa, bir IP adresi yerine ana bilgisayar adı kullanılıyor olabilir.|
Tek düğüm dağıtım |Sunucu ana bilgisayar adı için işaret eden bir DNS CNAME kaydı oluşturun.|

Daha fazla bilgi için bkz: [yapılandırma DNS hepsini bir kez Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Görev Planlama|
---|
Kimin oluşturulan ve değiştirilen DNS kayıtları kişiye biliyor musunuz?|
Bir DNS kaydı için bir istek için ortalama döngü nedir?|
Sunucular için statik ana bilgisayar (A) kayıtları isteği gerekiyor mu?|
Ne bir CNAME isteyecek?|
Gerekirse, ne tür yük dengeleme çözümü, yararlanacak olan? (Ayrıntılar için Yük Dengeleme başlıklı bölüme bakın)|

### <a name="public-key-infrastructure"></a>Ortak anahtar altyapısı

Çoğu kuruluş, ağ trafiğini, özellikle gibi hassas verileri yapılandırılmış sunucuları nasıl gibi içeren trafiği gerekir doğrulandı ve/veya iletim sırasında şifrelenmiş olduğunu bugün gerektirir. Kolaylaştıran HTTP kullanarak bir çekme sunucusuna dağıtmak mümkün olmakla birlikte, istemci isteklerini metni silin, HTTPS kullanan güvenli trafiği için en iyi uygulama olur. Hizmet DSC kaynağı bir parametre kümesi kullanarak HTTPS kullanmak üzere yapılandırılan **xPSDesiredStateConfiguration**.

Çekme sunucusuna HTTPS trafiğinin güvenliğini sağlamak için sertifika gereksinimleri herhangi bir HTTPS web sitesini güvenli hale getirme daha farklı değildir. **Web sunucusu** şablonu bir Windows Server Sertifika Hizmetleri'nde gerekli yeteneklerin karşılar.

Görev Planlama|
---|
Sertifika isteklerini otomatik olarak yapılmaz, kimin sertifika isteklerini başvurun gerekecek mi?|
İstek için ortalama döngü nedir?|
Nasıl sertifika dosyası için aktarılır?|
Nasıl sertifika özel anahtarı size aktarılır?|
Varsayılan süre uzunluğu nedir?|
Sertifika adı için kullanabileceğiniz çekme sunucu ortamı için bir DNS adı üzerinde kapatılan mi?|

### <a name="choosing-an-architecture"></a>Bir mimari seçme

IIS veya bir SMB dosya paylaşımında barındırılan ya da bir web hizmetini kullanarak bir çekme sunucusuna dağıtılabilir. Çoğu durumda, web hizmeti seçeneği büyük esneklik sağlar. SMB trafiğini genellikle filtrelenmiş veya ağlar arasında engellenen ancak ağ sınırları geçiş yapmak HTTPS trafiği için seyrek değil. Web hizmeti ayrıca uyumluluk sunucu veya istemciler merkezi görünürlük sunucusuna geri durumu raporlamak için bir mekanizma sağlar bir Web raporlama Yöneticisi (Bu belgenin sonraki bir sürümde ele alınması gereken iki konuları) içerecek şekilde seçeneği de sunar. SMB burada İlkesi bir web sunucusu değil göstermesi belirler. ortamlar için ve bir web sunucusu rolü istenmeyen olun diğer çevre gereksinimleri için bir seçenek sağlar. İmzalama ve trafiği şifreleme gereksinimlerini değerlendirmek her iki durumda da unutmayın. HTTPS, SMB imzalama ve IPSec ilkelerini dikkate değer tüm seçeneklerdir.

#### <a name="load-balancing"></a>Yük dengeleme  
İstemciler web hizmetiyle etkileşmek tek bir yanıtta döndürülen bilgi isteğini olun. Yük Dengeleyici oturumları zamanında herhangi bir noktada tek bir sunucu üzerinde saklanır emin olmak için platform için gerekli değildir sıralı istekler gereklidir.

Görev Planlama|
---|
Yük Dengeleme trafiğini sunucular arasında hangi çözüm kullanılacak mı?|
Kimin yeni bir yapılandırma aygıt eklemek için bir istek sürer bir donanım yük dengeleyicisi kullanıyorsanız?|
Yeni bir yük yapılandırmak bir istek için ortalama döngü nedir web hizmeti dengeli?|
Hangi bilgilerin istek için gerekli olacak mı?|
Bir ek IP istemeniz gerekir veya yük dengelemeden sorumlu takım, kullanacak mı?|
Gereken DNS kayıtlarını var ve bu çözümü dengelemesini yapılandırmak için sorumlu ekibi tarafından gerekli?|
PKI aygıt tarafından işlenmesi Yük Dengeleme çözümüne ihtiyacı yoktur veya hiçbir oturum gereksinimleri vardır sürece HTTPS trafiği dengelemek yükleyebilir?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Yapılandırmaları ve modülleri çekme sunucusunda hazırlama

Yapılandırma planlaması kapsamında, hangi DSC hakkında modülleri ve yapılandırmaları çekme sunucu tarafından barındırılacak düşünmeniz gerekir. Yapılandırma planlama amacıyla hazırlamak ve içerik bir çekme sunucusuna dağıtmak nasıl temel bir anlayış olması önemlidir. 

Gelecekte, bu bölümde genişletilmiş ve DSC çekme sunucusu için bir işlemler Kılavuzu'nda bulunan.  Kılavuzu otomasyon ile zamanla modülleri ve yapılandırmaları yönetmek için günlük işlem ele alınacaktır. 

#### <a name="dsc-modules"></a>DSC modülleri  
Bir yapılandırma isteyen istemcilerin gerekli DSC modüllerini gerekir. Çekme sunucunun işlevselliğini isteğe bağlı bir dağıtım istemcilere DSC modüllerin otomatik hale getirmektir. Bir çekme sunucusuna ilk kez, belki de bir laboratuvar veya kavram kanıtı olarak dağıtıyorsanız, büyük olasılıkla PowerShell Galerisi gibi ortak depoları veya PowerShell.org GitHub depoları DSC modülleri için kullanılabilir DSC modülleri bağımlı olmaz .

Bile güvenilen çevrimiçi kaynakları için PowerShell Galerisi gibi ortak bir depodan indirilen herhangi bir modül biri tarafından PowerShell deneyimi ve modülleri burada olacaktır ortamının bilgi gözden geçirilmesi gereken olduğunu unutmamak önemlidir Üretimde kullanılan önce kullanılır. Bu görev tamamlanırken herhangi ek yükü belgeler ve örnek komut dosyaları gibi kaldırılabilir modülünde denetlemek için bir zamanıdır. Modülleri sunucudan istemciye ağ üzerinden yüklenen bu ilk talebinde istemcisinde başına ağ bant genişliğini azaltır.

Belirli bir biçimde, modül yükünü içeren ModuleName_Version.zip adlı bir ZIP dosyası modüllerin paketlenmiş gerekir. Dosyayı sunucuya kopyalandıktan sonra bir sağlama toplamı dosya oluşturulmalıdır. İstemcilerin sunucuya bağlandığınızda, sağlama toplamı yayımlandıktan sonra DSC modülü içeriğini değişmemiştir doğrulamak için kullanılır.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Görev Planlama|
---|
Bir test veya laboratuvar ortamında planlıyorsanız hangi senaryolarını doğrulamak için anahtar misiniz?|
Gereksinim duyduğunuz her şeyi karşılamak için kaynakları içeren genel kullanıma açık modülleri vardır veya kendi kaynaklarını Yazar gerekir?|
Ortamınızı ortak modüller almak için Internet erişimi olacak mı?|
Kimin DSC modülleri gözden geçirmek için sorumlu olacak?|
Bir üretim ortamında planlıyorsanız ne yerel depo olarak DSC modülleri depolamak için kullanacaksınız?|
Merkezi bir takım uygulama ekipleri DSC modüllerden kabul eder? İşlem ne olacak?|
Paketleme, kopyalama ve üretime hazır DSC modülleri için bir sağlama toplamı sunucuya, kaynak deposu oluşturma otomatikleştirmek?|
Ekibinizin Otomasyon platform de yönetmekten sorumlu olacak?|

#### <a name="dsc-configurations"></a>DSC yapılandırmaları

Bir çekme sunucusuna amacı, istemci düğümlere DSC yapılandırmaları dağıtmak için merkezi bir düzenek sağlamaktır. Yapılandırmaları sunucuda MOF belgeleri olarak depolanır. Her bir belgenin benzersiz bir GUID ile adlandırılacaktır. İstemciler, bir çekme sunucusuna bağlanmak üzere yapılandırıldığında, bunlar GUID isteği yapılandırma için de verilir. Bu sistem yapılandırmaları GUID tarafından başvuru genel benzersizliği garanti eder ve düğüm başına ya da aynı yapılandırmalara sahip olması çok sayıda sunucuya yayılan bir rol yapılandırma olarak ayrıntı düzeyi içeren bir yapılandırma uygulanabilir şekilde esnektir.

#### <a name="guids"></a>GUID

Yapılandırma GUID'lerini planlama ek dikkat bir çekme sunucu dağıtımı düşünürken, büyük. GUID'ler nasıl ele alınacağını için belirli bir gereksinimi yoktur ve büyük olasılıkla her ortam için benzersiz bir işlemdir. İşlem basitten için karmaşık değişebilir: merkezi olarak depolanmış bir CSV dosyası, basit bir SQL tablo, bir CMDB veya başka bir aracı ya da yazılım çözümü ile tümleştirme gerektiren karmaşık bir çözüm. İki genel yaklaşım vardır:

 - **Sunucu başına GUID'ler atama** — bir ölçü her sunucu yapılandırması ayrı ayrı kontrol güvence sağlar. Bu güncelleştirmeleri geçici duyarlılık düzeyi sağlar ve birkaç sunucularıyla ortamlarda da çalışabilir.
 - **Her sunucu rolü GUID'ler atama** — gerekli yapılandırma verileri başvurmak için web sunucuları gibi aynı işlevi gerçekleştirir tüm sunucuları aynı GUID'ye kullanın.  Birçok sunucuları aynı GUID'ye paylaşıyorsanız, yapılandırma değiştiğinde, bunların tümünün aynı anda güncelleştirilmesini unutmayın.

GUID sunucuları nasıl dağıtıldığını ve ortamınızda yapılandırıldığını hakkında Intelligence kazanmak için kötü amaçlı sahip biri tarafından işlevden çünkü, hassas verileri kabul şeydir. Daha fazla bilgi için bkz: [güvenli bir şekilde modunda PowerShell istenen durum yapılandırması çekme GUID'ler ayırma](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Görev Planlama|
---|
Kimin hazır olduğunuzda, yapılandırmalarında çekme sunucu klasörüne kopyalamak için sorumlu olacak?|
Yapılandırmaları bir uygulama ekibi tarafından yazılan varsa, bunları devre dışı elle ne işlem olacak?|
Bunlar, ekibin yazılan gibi yapılandırmaları depolamak için bir depo özelliğinden yararlanır?|
Sunucuya yapılandırmalarını kopyalama ve hazır olduğunuzda bir sağlama toplamı oluşturma işlemini otomatikleştirmek?|
Sunucuları veya rolleri için GUID'leri nasıl eşler ve bu depolanacağı?|
Ne bir işlem olarak istemci makineleri yapılandırmak için kullanacağınız ve nasıl oluşturma ve yapılandırma GUID'ler saklamak için işleminizi ile tümleştirecek?|

## <a name="installation-guide"></a>Yükleme Kılavuzu

*Bu belgede verilen komut kararlı örnektir. Her zaman komut dosyalarını dikkatle bir üretim ortamında yürütmeden önce gözden geçirin.*

### <a name="prerequisites"></a>Önkoşullar

PowerShell sürümü sunucunuzda doğrulamak için aşağıdaki komutu kullanın.

```powershell
$PSVersionTable.PSVersion
```

Mümkünse, Windows Management Framework'ün en son sürüme yükseltin.
Ardından, indirme `xPsDesiredStateConfiguration` aşağıdaki komutu kullanarak modülü.


```powershell
Install-Module xPSDesiredStateConfiguration
```

Komut modülü yüklemeden önce onayınız istenir.

### <a name="installation-and-configuration-scripts"></a>Yükleme ve yapılandırma komut dosyaları
-

Bir DSC çekme sunucusuna dağıtmak için en iyi yöntem DSC yapılandırma betiği kullanmaktır. Bu belgede yalnızca DSC web hizmeti yapılandırırsınız ve gelişmiş bir Windows Server uçtan uca dahil olmak üzere DSC web hizmeti yapılandırırsınız ayarları her iki temel ayarlar dahil olmak üzere komut dosyaları sunacaktır.

Not: Şu anda `xPSDesiredStateConfiguation` DSC modülü server'ın EN-US yerel olmasını gerektirir.

### <a name="basic-configuration-for-windows-server-2012"></a>Windows Server 2012 için temel yapılandırma
-------------------------------------------
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


### <a name="verify-pull-server-functionality"></a>Çekme sunucu işlevselliğini doğrulayın

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN' 

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


## <a name="additional-references-snippets-and-examples"></a>Ek başvurular, parçacıkları ve örnekler

Bu örnek, test etmek için el ile (WMF5 gerektirir) bir istemci bağlantı başlatmak nasıl gösterir. 

```powershell
Update-DSCConfiguration –Wait -Verbose
```

[Ekle DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet türü CNAME kaydı bir DNS bölgesine eklemek için kullanılır. 

PowerShell işlevi [bir sağlama toplamı oluşturup yayımlama DSC MOF SMB çekme sunucusuna](http://bit.ly/1E46BhI) gerekli sağlama toplamı otomatik olarak oluşturur ve ardından MOF yapılandırma ve sağlama toplamı dosyaları SMB çekme sunucusuna kopyalar.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Ek - anlama ODATA hizmeti verilerini dosya türleri

Bir veri dosyası, bilgileri bir OData web hizmetini içeren bir çekme sunucu dağıtımı sırasında oluşturmak için depolanır. Dosya türü aşağıda açıklandığı gibi işletim sistemine bağlıdır.

 - **Windows Server 2012**  
Dosya türü her zaman .mdb olacaktır
 - **Windows Server 2012 R2**  
Bir .mdb yapılandırmada belirtilmediği sürece dosya türü için .edb varsayılan olur

İçinde [örnek komut dosyası Gelişmiş](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) bir çekme sunucusuna yüklemek için tüm dosya türüne göre neden hata olasılığını önlemek için web.config dosyası ayarları otomatik olarak denetlemek nasıl bir örnek da bulacaksınız.

