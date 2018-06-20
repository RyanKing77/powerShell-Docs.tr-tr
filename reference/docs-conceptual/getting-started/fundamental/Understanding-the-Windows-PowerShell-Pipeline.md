---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell Komut Zincirini Anlama
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951078"
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Windows PowerShell Komut Zincirini Anlama
Yöneltme neredeyse her yerde Windows PowerShell içinde çalışır. Ekranda metin karşın, Windows PowerShell komutları arasındaki metni kanal değil. Bunun yerine, nesneleri geçirir.

İşlem hatları için kullanılan gösterimi benzer kullanan için diğer Kabukları, bu nedenle ilk bakışta, bunu Windows PowerShell yeni bir şey tanıtır belirgin olmayabilir. Örneğin, kullanırsanız **dışarı barındırmak** çıkış sayfa tarafından görüntüsünü başka bir komuttan çıkış görünüyor yalnızca zorlamak için cmdlet'i ister sayfalarına parçalanmış ekranda görüntülenen normal metin:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

Out-Host-disk belleği komutu bir öğedir yararlı ardışık düzen yavaş görüntülemek istediğiniz uzun çıktıya sahip olduğunda. İşlemi çok CPU-yoğun ise özellikle yararlı olur. İşleme için aktarıldığından cmdlet dışarı ana bilgisayar tam bir sayfa görüntülemek için hazır olduğunda, sonraki sayfaya çıktı kullanılabilir hale gelene kadar ardışık düzeninde koyun cmdlet'leri işlemi durdurmak. Windows PowerShell CPU ve bellek kullanımı izlemek için Windows Görev Yöneticisi'ni kullanırsanız, bu görebilirsiniz.

Aşağıdaki komutu çalıştırın: **Get-Childıtem C:\\Windows-Recurse**. Bu komut için CPU ve bellek kullanımı karşılaştırın: **Get-Childıtem C:\\Windows-Recurse | -Disk belleği dışarı konak**. Metni ekranda görün, ancak konsol penceresinde metin olarak nesneleri temsil etmek gerekli olmasıdır. Bu nedir, yalnızca bir gösterimi olan Windows PowerShell içinde üzerinde gerçekten giderek. Örneğin, Get-Location cmdlet göz önünde bulundurun. Yazarsanız **Get-Location** geçerli konumunuz C sürücüsünün kök olsa da, aşağıdaki çıktı görmeniz:

```
PS> Get-Location

Path
----
C:\
```

Windows PowerShell metin ardışık, bir komut gibi veren **Get-Location | Dışarı konak**, gelen geçip geçmeyeceğini **Get-Location** için **dışarı konak** bunlar görüntülenir ekranda sırayla karakter kümesi. Diğer bir deyişle, başlık bilgilerinin olsaydı **dışarı konak** ilk karakter alacağı '**C'**, ardından karakter '**:'**, ardından karakter ' **\\'**. **Dışarı konak** cmdlet'i tarafından karakter çıktı ilişkilendirmek ne anlamı belirleyemedi **Get-Location** cmdlet'i.

Ardışık düzeninde komutları izin vermek için metin kullanmak yerine iletişim, Windows PowerShell, nesneleri kullanır. Kullanıcı açısından, nesneleri bir birim olarak bilgiyi işleyebilir kolaylaştırır bir forma ilgili bilgiler paketini ve gerek duyduğunuz belirli öğeleri ayıklayın.

**Get-Location** komutu geçerli yolunu içeren metin döndürmez. Adlı bilgi paketi döndüren bir **PATHINFO** bazı diğer bilgilerle birlikte geçerli yolu içeren nesne. **Dışarı konak** cmdlet ardından gönderir bu **PATHINFO** ekran ve Windows PowerShell nesnesine karar ne görüntülemek için bilgi ve görüntülemek nasıl biçimlendirme kendi kurallarına göre.

Aslında, başlık bilgileri çıkış olarak **Get-Location** cmdlet'i yalnızca işleminin sonunda ekranda görüntülemek için veri biçimlendirmeyi işleminin bir parçası olarak eklenir. Gördüğünüz bilgilerin özetini ve çıkış nesnesi değil eksiksiz bir gösterimini ekranda.

Olabilir koşuluyla, bir Windows PowerShell komut biz gördükleri konsol penceresinde görüntülenen daha nasıl kullanabilir daha fazla bilgi çıktısını görünür olmayan öğeleri almak? Ek veriler nasıl görüntüleyebilirim? Ve normal şekilde verileri bir Windows PowerShell farklı bir biçimde görüntülemek isterseniz kullanır?

Bu bölümde rest belirli öğeler seçme belirli Windows PowerShell nesnelerin yapısı nasıl bulabilir açıklanır ve onları daha kolay görüntüleme için ve bu bilgiyi alternatif çıkış konumlara gibi göndermek nasıl biçimlendirme dosyaları ve Yazıcılar.