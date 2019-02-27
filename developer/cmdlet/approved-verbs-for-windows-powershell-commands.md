---
title: Fiiller PowerShell komutları için onaylanmış | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: d8a0561d6fbb4447a691c434e0518e3e16ce41e7
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56852181"
---
# <a name="approved-verbs-for-powershell-commands"></a>PowerShell komutları için onaylanmış fiiller

PowerShell fiil-isim çifti ve kendi türetilmiş Microsoft .NET Framework sınıfları için cmdlet'lerin adlarını kullanır.
Örneğin, `Get-Command` PowerShell tarafından sağlanan cmdlet'i, PowerShell içinde kayıtlı olan tüm komutları almak için kullanılır.
Fiili kısmını cmdlet gerçekleştirdiği eylemi tanımlar.
İsim kısmını gerçekleştirilecek varlığı tanımlar.

> [!NOTE]
> PowerShell kullanan terimi *fiil* sözcük İngilizce dilinde standart fiil olmasa bile bir eylem anlamına gelir. bir sözcük tanımlamak için.
> Örneğin, terim *yeni* olduğundan geçerli bir PowerShell fiili ad İngilizce dilinde fiil olmasa bile bir eylem anlamına gelir.

## <a name="verb-naming-rules"></a>Fiili adlandırma kuralları

Aşağıdaki listede, bir cmdlet adı için fiili seçtiğinizde dikkate alınması gereken yönergeler sağlar:

* Fiili belirttiğinizde, PowerShell tarafından sağlanan önceden tanımlanmış fiili adlarından birini kullanmanız önerilir (önceden tanımlanmış bu eylemler için diğer adlar aşağıdaki tablolarda eklenir).
  Önceden tanımlanmış bir fiil kullandığınızda, oluşturduğunuz cmdlet'leri PowerShell tarafından sağlanan cmdlet'ler ve başkaları tarafından tasarlanan cmdlet'ler arasında tutarlılık sağlamak.

* Genel eylem kapsamını tanımlamak için önceden tanımlanmış fiilleri kullanın ve daha fazla eylem cmdlet'inin iyileştirmek için parametreleri kullanın.

* Cmdlet'ler arasında tutarlılığı zorlamak için bir eşanlamlı onaylanmış bir fiil, kullanmayın.

* Yalnızca bu konuda listelenen her bir fiil biçimini kullanın.
  Örneğin, "Get" kullanın, ancak "Başlarken" veya "Alır" kullanmayın.

* Pascal kullanmak için fiilleri büyük/küçük harfleri.
  Pascal içinde her sözcüğün ilk harfini büyük/küçük harfleri, "ForEach" gibi büyük harfle.

* Aşağıdaki ayrılmış fiil veya diğer adları kullanmayın.
  Bu Eylemler, PowerShell dilinin veya PowerShell tarafından sağlanan özel durum cmdlet'leri kullanılır.
  - ForEach (foreach)
  - Biçimi (f)
  - Grup (gp)
  - Sıralama (sr)
  - Tee (metin)
  - Burada (ne)

## <a name="similar-verbs-for-different-actions"></a>Farklı eylemler için benzer fiiller

Aşağıdaki benzer fiillere farklı eylemler temsil eder.

### <a name="new-vs-set"></a>Yeni vs. Ayarla
`New` Fiil, yeni bir kaynak oluşturmak için kullanılır.
`Set` Fiili bunu, aşağıdaki gibi mevcut değilse, isteğe bağlı olarak kaynak oluşturma, mevcut bir kaynağı değiştirmek için kullanılan `Set-Variable` cmdlet'i.

### <a name="find-vs-search"></a>VS bulun. Ara
`Find` Fiil için bir nesne aramak için kullanılır.
`Search` Fiil, bir kapsayıcıda bir kaynağına başvuru oluşturmak için kullanılır.

### <a name="get-vs-read"></a>VS alın. Okuma
`Get` Fiili dosyası gibi bir kaynağı almak için kullanılır.
`Read` Fiili dosyası gibi bir kaynaktan bilgi almak için kullanılır.

### <a name="invoke-vs-start"></a>VS çağırın. wps_2'yi
`Invoke` Fiil, genellikle bir komut çalıştırma gibi eşzamanlı bir işlem, bir işlemi gerçekleştirmek için kullanılır.
`Start` Fiil, genellikle bir işlem başlatmak gibi zaman uyumsuz bir işlem olan bir işlem başlatmak için kullanılır.

### <a name="ping-vs-test"></a>Ping vs. Test
Kullanım `Test` fiil.

## <a name="common-verbs"></a>Ortak fiiller

PowerShell kullanan [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) neredeyse herhangi bir cmdlet'i için uygulayabileceğiniz Genel eylemleri tanımlamak için sabit listesi sınıfı.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Ekleme](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Bir kaynak bir kapsayıcıya ekler veya başka bir öğe için bir öğe ekler. Örneğin, `Add-Content` cmdlet'i, bir dosyaya içerik ekler. Bu fiili ile eşleştirilmiş `Remove`.|Bu eylem için değil Append, Ekle, Concatenate gibi fiilleri kullanın veya ekleme.|
|[NET](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (CI)|Bir kapsayıcıdaki tüm kaynakları kaldırır ancak bu kapsayıcıyı silmez. Örneğin, `Clear-Content` cmdlet'i bir dosyanın içeriğini kaldırır ancak dosyanın silinmesine neden olmaz.|Bu eylem için temizleme, silme, yayın, işaretini, ayarlama veya Nullify gibi fiiller kullanmayın.|
|[Kapat](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Erişilemez, kullanılabilir veya kullanılamaz hale getirmek için bir kaynak durumunu değiştirir. Bu fiili ile eşleştirilmiş `Open.`||
|[Kopyalama](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Bir kaynak başka bir ad veya başka bir kapsayıcıya kopyalar. Örneğin, `Copy-Item` depolanan verilere erişmek için kullanılan cmdlet bir öğe başka bir konuma bir konumdan veri deposuna kopyalar.|Bu eylem için yinelenen, kopyalama, çoğaltma ve eşitleme gibi fiiller kullanmayın.|
|[Girin](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Bir kaynağa taşımak kullanıcıya izin veren bir eylem belirtir. Örneğin, `Enter-PSSession` cmdlet'i etkileşimli bir oturumda kullanıcı yerleştirir. Bu fiili ile eşleştirilmiş `Exit`.|Bu eylem için içine veya anında iletme gibi fiiller kullanmayın.|
|[Çıkış](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ör.)|En son kullanılan bağlamı için geçerli bir ortam veya bağlam ayarlar. Örneğin, `Exit-PSSession` cmdlet'i etkileşimli oturumu başlatmak için kullanılan oturumu kullanıcı yerleştirir. Bu fiili ile eşleştirilmiş `Enter`.|Bu eylem için fiilleri Pop gibi veya çıkış kullanmayın.|
|[Bulma](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Bilinmiyor, örtük, isteğe bağlı veya belirtilen bir kapsayıcıdaki bir nesne için görünür.||
|[Biçim](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Belirtilen form veya Düzen nesneler düzenler.||
|[Alma](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Bir kaynağı alır bir eylem belirtir. Bu fiili ile eşleştirilmiş `Set`.|Bu eylem için okuma, açık, kat, türü, Dir, elde edilir, döküm, alma, inceleyin, bulma veya bu eylem için arama gibi fiiller kullanmayın.|
|[Gizleme](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Bir kaynak algılanamayan yapar. Örneğin, Gizle fiili adını içeren bir cmdlet bir kullanıcı tarafından bir hizmet gizlemek. Bu fiili ile eşleştirilmiş `Show`.|Bu eylem için blok gibi fiil kullanmayın.|
|[Birleştirme](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Kaynakları bir kaynak birleştirir. Örneğin, `Join-Path` cmdlet'i tek bir yol oluşturmak için kendi alt yollardan birine sahip bir yol birleştirir. Bu fiili ile eşleştirilmiş `Split`.|Bu eylem için gibi birleştirme, Unite, bağlanma veya ilişkilendirin fiilleri kullanmayın.|
|[Kilit](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Bir kaynak güvenliğini sağlar. Bu fiili ile eşleştirilmiş `Unlock`.|Bu eylem için kısıtlama veya güvenli gibi fiiller kullanmayın.|
|[Taşıma](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Bir kaynak bir konumdan diğerine taşır. Örneğin, `Move-Item` cmdlet'i bir öğe başka bir konuma veri deposundaki bir konumdan taşır.|Bu eylem için Aktarım, ad veya geçiş gibi fiiller kullanmayın.|
|[Yeni](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Bir kaynak oluşturur. ( `Set` Fiil, ayrıca verileri, bir kaynak oluşturma gibi içerdiği durumlarda kullanılabilir `Set-Variable` cmdlet'ini.)|Bu eylem için Oluştur, oluşturma, derleme, oluşturma veya ayırma gibi fiiller kullanmayın.|
|[Açık](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (işlem)|Erişilebilir, kullanılabilir veya kullanılamaz hale getirmek için bir kaynak durumunu değiştirir. Bu fiili ile eşleştirilmiş `Close`.||
|[En iyi duruma getirme](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Bir kaynak verimliliğini artırır.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Bir öğeyi bir yığının üst kısmından kaldırır. Örneğin, `Pop-Location` cmdlet'i yığınına en son gönderildiği konum için geçerli konumunu değiştirir.||
|[Anında iletme](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Bir öğeyi bir yığının en üst kısmına ekler. Örneğin, `Push-Location` cmdlet geçerli konumu yığına iter.||
|[Yinele](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (yeniden)|Bir kaynağa geri durumuna sıfırlar.||
|[Kaldırma](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Bir kaynak, bir kapsayıcıyı siler. Örneğin, `Remove-Variable` cmdlet'i bir değişkenini ve değerini siler. Bu fiili ile eşleştirilmiş `Add`.|Bu eylem için kullanmayın fiilleri tür olarak temizleyin, Kes, atma, Dispose veya Sil.|
|[Yeniden adlandırma](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Bir kaynağın adını değiştirir. Örneğin, `Rename-Item` depolanan verilere erişmek için kullanılan cmdlet'i, veri deposundaki bir öğe adını değiştirir.|Bu eylem için değiştirme gibi fiil kullanmayın.|
|[Sıfırlama](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Bir kaynak özgün durumuna ayarlar.||
|[Arama](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Kapsayıcıda bir kaynağına başvuru oluşturur.|Bu eylem için bulma veya Bul gibi fiiller kullanmayın.|
|[Seçin](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Bir kaynak bir kapsayıcıda bulur. Örneğin, `Select-String` cmdlet'i metin dizelerini ve dosyaları bulur.|Bu eylem için bulma veya Bul gibi fiiller kullanmayın.|
|[Ayarlama](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Mevcut bir kaynak veri değiştirir veya bazı verileri içeren bir kaynak oluşturur. Örneğin, `Set-Date` cmdlet'i, yerel bilgisayardaki Sistem saatini değiştirir. ( `New` Fiili ayrıca bir kaynak oluşturmak için kullanılabilir.) Bu fiili ile eşleştirilmiş `Get`.|Bu eylem için yazma, sıfırlama, atama veya yapılandırma gibi fiiller kullanmayın.|
|[Göster](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (Göster)|Bir kaynak kullanıcıya görünür hale getirir. Bu fiili ile eşleştirilmiş `Hide`.|Bu eylem için görüntü veya üretim gibi fiiller kullanmayın.|
|[Skip](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Bir veya daha fazla kaynak ya da bir dizi noktaları atlar.|Bu eylem için geçiş ya da atlama gibi fiil kullanmayın.|
|[Bölünmüş](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (yükleme sl)|Bir kaynak bölümlerini ayırır. Örneğin, `Split-Path` cmdlet'i farklı kısımlarını bir yol döndürür. Bu fiili ile eşleştirilmiş `Join`.|Bu eylem için fiil gibi ayrı kullanmayın.|
|[Adım](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Sonraki noktası veya kaynak dizideki taşır.||
|[Anahtar](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (yazılım)|İki kaynak arasında iki konum, sorumlulukları veya durumları arasında değiştirme gibi diğerleri bir eylem belirtir.||
|[Geri](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (BM)|Bir kaynak, önceki durumuna ayarlar.||
|[Kilit açma](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (uk)|Kilitli olan bir kaynağı serbest bırakır. Bu fiili ile eşleştirilmiş `Lock`.|Bu eylem için yayın, Unrestrict veya güvenli olmayan'gibi fiiller kullanmayın.|
|[İzleme](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Sürekli olarak inceler veya bir kaynak değişiklikleri izler.||

## <a name="communications-verbs"></a>İletişim fiiller

PowerShell kullanan [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) iletişimler uygulanan eylemleri tanımlamak için sınıf.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Connect](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Bir kaynak ve hedef arasında bir bağlantı oluşturur. Bu fiili ile eşleştirilmiş `Disconnect`.|Bu eylem için katılma veya Telnet gibi fiiller kullanmayın.|
|[Bağlantı kesme](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Bir kaynak ve hedef arasındaki bağlantıyı keser. Bu fiili ile eşleştirilmiş `Connect`.|Bu eylem için kesme ya da oturum kapatma gibi fiiller kullanmayın.|
|[Okuma](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Bir kaynaktan bilgi edinir. Bu fiili ile eşleştirilmiş `Write`.|Bu eylem için değil edinme,'gibi fiiller komut istemi kullanın veya alın.|
|[Alma](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Bir kaynaktan gönderilen bilgiler kabul eder. Bu fiili ile eşleştirilmiş `Send`.|Bu eylem için değil okuma, kabul etme, gibi fiilleri kullanın veya Özet.|
|[Gönderme](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Bilgiler bir hedefe sunar. Bu fiili ile eşleştirilmiş `Receive`.|Bu eylem için Put, yayın, posta ya da faks gibi fiiller kullanmayın.|
|[Yazma](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Bilgileri bir hedefe ekler. Bu fiili ile eşleştirilmiş `Read`.|Bu eylem için Put veya yazdırma gibi fiiller kullanmayın.|

## <a name="data-verbs"></a>Veri fiiller

PowerShell kullanan [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) veri işleme uygulanan eylemleri tanımlamak için sınıf.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Eylem adı (diğer)|Eylem|Açıklamalar|
|-------------------------|------------|--------------|
|[Yedekleme](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Çoğaltma yaparak, verileri depolar.|Bu eylem için Kaydet, yazma, çoğaltma ve eşitleme gibi fiiller kullanmayın.|
|[Denetim noktası](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Geçerli durumu verilerin veya yapılandırmanın anlık görüntüsünü oluşturur.|Bu eylem için farkı gibi fiil kullanmayın|
|[Karşılaştırma](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Bir kaynak başka bir kaynaktan verilere karşı verileri değerlendirir.|Bu eylem için farkı gibi fiil kullanmayın|
|[Sıkıştırma](/dotnet/api/System.Management.Automation.VerbsData.Compress) (mm)|Veri kaynağının sıkıştırır. Özellikleriyle `Expand`.|Bu eylem için fiil gibi Compact kullanmayın.|
|[Dönüştürme](/dotnet/api/System.Management.Automation.VerbsData.Convert) (MS)|Verileri bir gösterimden cmdlet çift yönlü dönüştürme desteklediğinde veya cmdlet'ini birden çok veri türleri arasında dönüştürme desteklediğinde değiştirir.|Bu eylem için kullanmayın değişikliği, yeniden boyutlandırmak, gibi fiiller veya yeniden örnekle.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Bir birincil (cmdlet'i isim giriş gösterir) giriş türü için bir veya daha fazla desteklenen çıktı türleri dönüştürür.|Bu eylem için dışarı aktarma, çıkış veya çıkış gibi fiiller kullanmayın.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (u)|Bir veya daha fazla tür giriş (çıktı türü cmdlet'in isim gösterir) birincil çıkış türüne dönüştürür.|Bu eylem için içeri aktarma,'gibi fiiller kullanmayın giriş, veya.|
|[Çıkarma](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Adlandırılmış varlık bir konumdan ayırır. Bu fiili ile eşleştirilmiş `Mount`.|Bu eylem için çıkarma veya bağlantıyı Kaldır'gibi fiiller kullanmayın.|
|[Düzen](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Mevcut verileri ekleyerek veya kaldırarak içerik değiştirir.|Bu eylem için bu eylem için değişiklik, güncelleştirme ve değiştirme gibi fiiller kullanmayın.|
|[Genişletin](/dotnet/api/System.Management.Automation.VerbsData.Expand) (TR)|Sıkıştırılmış bir kaynağın verileri özgün durumuna geri yükler. Bu fiili ile eşleştirilmiş `Compress`.|Bu eylem için Aç ya da Sıkıştırılmışı Aç'gibi fiiller kullanmayın.|
|[Dışarı aktarma](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Bir dosya gibi kalıcı bir veri deposuna veya bir değişim biçimi birincil giriş kapsüller. Bu fiili ile eşleştirilmiş `Import`.|Bu eylem için ayıklama veya yedekleme gibi fiiller kullanmayın.|
|[Grup](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Yerleştirir veya bir veya daha fazla kaynak ilişkilendirir.|Bu eylem için değil gibi toplama, Düzenle, ilişkilendirin fiilleri kullanın veya ilişkilendirin.|
|[İçeri aktarma](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Kalıcı bir veri deposuna (örneğin, bir dosya) veya bir değişim biçiminde depolanmış verilerden bir kaynak oluşturur. Örneğin, `Import-CSV` cmdlet'i diğer cmdlet'ler tarafından kullanılabilir nesneler için bir virgülle ayrılmış değer (CSV) dosyasından veri aktarır. Bu fiili ile eşleştirilmiş `Export`.|Bu eylem için BulkLoad veya yük gibi fiiller kullanmayın.|
|[Başlatma](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (gelen)|Bir kaynak kullanıma hazırlar ve varsayılan durumuna ayarlar.|Bu eylem için silme, Init, yenileme, yeniden oluşturma, yeniden başlatın veya Kurulum gibi fiiller kullanmayın.|
|[Sınırı](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Bir kaynağa kısıtlamalarını uygular.|Bu eylem için kota gibi fiil kullanmayın.|
|[Birleştirme](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Birden çok kaynaklardan tek bir kaynak oluşturur.|Bu eylem için birleştirme veya birleştirme gibi fiiller kullanmayın.|
|[Bağlama](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Adlandırılmış varlık, bir konuma ekler. Bu fiili ile eşleştirilmiş `Dismount`.|Bu eylem için fiili Connect kullanmayın.|
|[Çıkış](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Ortam dışında verileri gönderir. Örneğin, `Out-Printer` cmdlet'i bir yazıcıya verileri gönderir.||
|[Publish](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Bir kaynak, diğerleri için kullanılabilir hale getirir. Bu fiili ile eşleştirilmiş `Unpublish`.|Bu eylem için kullanmayın dağıtma, Sürüm'gibi fiiller veya yükleyin.|
|[Geri yükleme](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Bir kaynak kümesi bir durumu gibi önceden tanımlanmış bir duruma ayarlar `Checkpoint`. Örneğin, `Restore-Computer` cmdlet'i, yerel bilgisayarda bir sistem geri yükleme başlar.|Bu eylem için onarım, iade, geri alma veya düzeltme gibi fiiller kullanmayın.|
|[Kaydet](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Veri kaybını önlemek için korur.||
|[Eşitleme](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|İki veya daha fazla kaynak aynı durumda olmasını sağlar.|Bu eylem için kullanmayın REPLICATE Coerce,'gibi fiiller veya eşleşen.|
|[Yayımdan](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (lt)|Bir kaynak başkalarına kullanılamaz hale getirir. Bu fiili ile eşleştirilmiş `Publish`.|Bu eylem için kullanmayın kaldırma, geri döndürme işlemi,'gibi fiiller veya gizleyin.|
|[Güncelleştirme](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Kaynak durumu, doğruluk, uyumluluk veya uyumluluk sağlamak için güncel getirir. Örneğin, `Update-FormatData` cmdlet güncelleştirir ve geçerli PowerShell konsoluna biçimlendirme dosyaları ekler.|Bu eylem için değil yenileme, yenileme, yeniden hesapla gibi'fiiller kullanabilir veya yeniden dizin.|

## <a name="diagnostic-verbs"></a>Tanılama fiiller

PowerShell kullanan [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) tanılama için uygulanan eylemleri tanımlamak için sınıf.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Hata ayıklama](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|İşletimsel sorunları tanılamak için kaynak inceler.|Bu eylem için Tanıla gibi fiil kullanmayın.|
|[Ölçü](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Bir kaynak hakkında istatistikler alır veya belirtilen bir işlem tarafından kullanılan kaynakları belirler.|Bu eylem için Calculate, belirleme ve analiz gibi fiiller kullanmayın.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Kullanım `Test` fiil.||
|[Onarım](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Bir kaynak kullanılabilir durumuna geri yükler.|Bu eylem için düzeltme veya geri yükleme gibi fiiller kullanmayın.|
|[Çözmek](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Bir kaynak bir toplu özellik gösterimi için daha eksiksiz bir gösterimi eşler.|Bu eylem için genişletme veya belirleme gibi fiiller kullanmayın.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|İstediğiniz işlemin veya bir kaynak tutarlılığını doğrular.|Bu eylem için tanılama, analiz, hurda veya doğrulama gibi fiiller kullanmayın.|
|[İzleme](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Bir kaynak etkinliklerini izler.|Bu eylem için kullanmayın fiilleri gibi izleme, izleme, inceleyin, veya inin.|

## <a name="lifecycle-verbs"></a>Yaşam döngüsü fiiller

PowerShell kullanan [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) kaynak yaşam döngüsü için uygulama eylemleri tanımlamak için sınıf.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Onaylama](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Onaylar veya bir kaynak veya işleme durumu için kabul eder.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (gibi)|Kaynak durumu'ni onaylar.|Bu eylem için fiil Certify gibi kullanmayın.|
|[Derleme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Bazı dizi girdi dosyalarını (genellikle kaynak kodu veya bildirim temelli belgeleri) dışında bir yapıtı (genellikle bir ikili ya da belge) oluşturur.|Bu eylem PowerShell v6 eklendi|
|[Tam](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Bir işlemi sonlandırır.||
|[Onayla](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Bildirir, doğrular ve bir kaynak veya işlem durumunu doğrular.|Bu eylem için kabul, kabul et, Certify, doğrulama veya doğrulama gibi fiiller kullanmayın.|
|[Reddetme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Reddediyor, nesneleri engeller ya da bir kaynak veya işlem durumunu opposes.|Bu eylem için değil gibi blok, nesne, geri çevirme fiilleri kullanın veya reddetme.|
|[Dağıtma](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Dağıtım tamamlandıktan sonra bu çözüm, bir tüketici erişebildiğinizi şekilde uzak hedef [s] bir uygulama, Web sitesi veya çözüm gönderir|Bu eylem PowerShell v6 eklendi|
|[Devre dışı](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Kaynak kullanılamıyor veya etkin olmayan bir duruma yapılandırır. Örneğin, `Disable-PSBreakpoint` cmdlet'i bir kesme noktası etkin olmayan yapar. Bu fiili ile eşleştirilmiş `Enable`.|Bu eylem için durdurmak veya gizleme gibi fiiller kullanmayın.|
|[Etkinleştirme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Bir kaynak kullanılabilir veya etkin durumuna yapılandırır. Örneğin, `Enable-PSBreakpoint` cmdlet'i bir kesme noktası etkin yapar. Bu fiili ile eşleştirilmiş `Disable`.|Bu eylem için başlangıç veya başlangıç gibi fiiller kullanmayın.|
|[Yükleme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (değer)|Bir kaynağı bir konuma yerleştirir ve isteğe bağlı olarak başlatır. Bu fiili ile eşleştirilmiş `Uninstall`.|Bu eylem için değil kullanım fiil gibi kurulumu yapın.|
|[Çağırma](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Bir komutu veya bir yöntem çalıştırma gibi bir eylem gerçekleştirir.|Bu eylem için farklı çalıştır veya başlatma gibi fiiller kullanmayın.|
|[Kayıt](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Bir veritabanı gibi bir depoda kaynak için bir giriş oluşturur. Bu fiili ile eşleştirilmiş `Unregister`.||
|[İstek](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Bir kaynak için soran veya izinlerini sorar.||
|[Yeniden](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (Başlangıç)|Bir işlemi durdurur ve yeniden başlatır. Örneğin, `Restart-Service` cmdlet'i durdurur ve ardından bir hizmetini başlatır.|Bu eylem için Geri Dönüşüm gibi fiil kullanmayın.|
|[Sürdürme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Askıya alındı bir işlem başlatır. Örneğin, `Resume-Service` cmdlet'i, askıya alındı bir hizmetini başlatır. Bu fiili ile eşleştirilmiş `Suspend`.||
|[Başlangıç](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Bir işlem başlatır. Örneğin, `Start-Service` cmdlet'i bir hizmetini başlatır. Bu fiili ile eşleştirilmiş `Stop`.|Bu eylem için başlatma, başlatma veya önyükleme gibi fiiller kullanmayın.|
|[Durdur](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Bir etkinlik sona erdirir. Bu fiili ile eşleştirilmiş `Start`.|Bu eylem için değil End, sonlandırma, sonlandırma gibi fiilleri kullanın, veya iptal edin.|
|[Gönderme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Onay için bir kaynak sunar.|Bu eylem için bir fiili Post gibi kullanmayın.|
|[Askıya alma](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Bir etkinlik duraklatır. Örneğin, `Suspend-Service` cmdlet'i bir service duraklatır. Bu fiili ile eşleştirilmiş `Resume`.|Bu eylem için duraklatma gibi fiil kullanmayın.|
|[Kaldırma](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Bir kaynak bir belirtilen konumdan kaldırır. Bu fiili ile eşleştirilmiş `Install`.||
|[Kaydını](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) ()|Bir kaynak için Giriş bir depodan kaldırır. Bu fiili ile eşleştirilmiş `Register`.|Bu eylem için Kaldır gibi'bir fiil kullanmayın.|
|[Bekleme](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Belirtilen olay gerçekleşene kadar bir işlemi duraklatır. Örneğin, `Wait-Job` cmdlet'i duraklatır operations kadar ya da daha fazla arka plan işleri tamamlandı.|Bu eylem için uyku veya duraklatma gibi fiiller kullanmayın.|

## <a name="security-verbs"></a>Güvenlik fiiller

PowerShell kullanan [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) uygulanan güvenlik eylemleri tanımlamak için sınıf.
Aşağıdaki tabloda tanımlanan fiilleri çoğunu listeler.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Blok](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (ma)|Bir kaynağa erişimi kısıtlar. Bu fiili ile eşleştirilmiş `Unblock`.|Bu eylem için engelle, sınırı veya reddetme gibi fiiller kullanmayın.|
|[GRANT](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Bir kaynağa erişim izni verir. Bu fiili ile eşleştirilmiş `Revoke`.|Bu eylem için fiillere izin verme veya etkinleştirme gibi kullanmayın.|
|[Koruma](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Bir kaynaktan saldırı veya kayıp korur. Bu fiili ile eşleştirilmiş `Unprotect`.|Bu eylem için şifreleme, korumaya veya korumalı gibi fiiller kullanmayın.|
|[İptal](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (işareti)|Bir kaynağa erişim izin vermeyen bir eylem belirtir. Bu fiili ile eşleştirilmiş `Grant`.|Bu eylem için Kaldır'ı veya devre dışı bırakma gibi fiiller kullanmayın.|
|[Engellemesini](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Bir kaynağa kısıtlamaları kaldırır. Bu fiili ile eşleştirilmiş `Block`.|Bu eylem için Clear veya izin gibi fiiller kullanmayın.|
|[Korumasını](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (en fazla)|Güvenlik önlemleri saldırısına ya da kaybını önlemek için eklenmiş olan bir kaynak kaldırır. Bu fiili ile eşleştirilmiş `Protect`.|Bu eylem için şifre çözme veya Unseal gibi fiiller kullanmayın.|

## <a name="other-verbs"></a>Diğer fiiller

PowerShell kullanan [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) ortak, iletişim, verileri, yaşam döngüsü gibi belirli fiili adı kategori içine uymayan kurallı fiili adlarını veya güvenlik fiili adlarını tanımlamak için sınıfı fiilleri.

|Fiili (diğer)|Eylem|Açıklamalar|
|--------------------|------------|--------------|
|[Kullanım](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Bir şey yapmak için bir kaynak içerir veya kullanır.||

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet bildirimi](./cmdlet-class-declaration.md)

[Windows PowerShell Programcı Kılavuzu](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
