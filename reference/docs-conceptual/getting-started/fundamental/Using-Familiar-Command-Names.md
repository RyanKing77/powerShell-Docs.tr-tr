---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Tanıdık komut adlarını kullanma"
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 5e72e721bdb9d48684092344a0169907e7e25d40
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="using-familiar-command-names"></a>Tanıdık komut adlarını kullanma
Bir mekanizma kullanılarak adlı *yumuşatma*, Windows PowerShell komutları için alternatif adlarına göre başvurmak kullanıcıların sağlar. Yumuşatma deneyimine sahip kullanıcıların Windows PowerShell'de benzer işlemleri gerçekleştirmek için kullanıcılarınızın zaten bildikleri ortak komut adlarının yeniden kullanmak için diğer Kabukları verir. Windows PowerShell diğer adlar ayrıntılı aşağıdakiler ele alınacaktır değil de, Windows PowerShell ile çalışmaya başlama gibi bunları kullanmaya devam edebilirsiniz.

Yumuşatma yazdığınız komut adı başka bir komutu ile ilişkilendirir. Örneğin, Windows PowerShell adlı bir iç işlev sahip **Clear-Host** çıktı penceresi temizler. Ya da yazarsanız **cls** veya **temizleyin** komutu bir komut isteminde, Windows PowerShell yorumlar için bir diğer ad budur **Clear-Host** işlev ve çalıştırır **Clear-Host** işlevi.

Bu özellik, Windows PowerShell öğrenmek için kullanıcıların yardımcı olur. İlk olarak, çoğu Cmd.exe ve UNIX kullanıcının kullanıcı adıyla zaten biliyor komutların büyük topluluğu vardır ve Windows PowerShell eşdeğeri aynı sonuçları vermeyebilir rağmen bunlar kullanıcılar bunları gerek kalmadan çalışmak için kullanabileceğiniz formunda yeterince Kapat ilk Windows PowerShell adları ezberleme. İkinci olarak, ana kullanıcı zaten başka bir kabuk ile alışkın olduğu zaman içinde yeni bir kabuk öğrenme sorun yaratabilir kaynağıdır "parmak bellekle" oluşan hatalar. Ne zaman çıktısını tam bir ekrana sahip ve bu reflexively yazarsınız temizlemek istediğiniz yıldır Cmd.exe kullandıysanız **cls** komut ve ENTER tuşuna basın. Diğer ad olmadan **Clear-Host** işlevi Windows PowerShell'de yalnızca hata iletisi elde edebileceğiniz "**'cls' cmdlet, işlev, çalıştırılabilir program veya komut dosyası tanınmıyor.**" ve çıktı temizlemek için hiçbir fikrini yapmanız gerekenler ile kalmış olabilir.

Windows PowerShell içinde kullanabileceğiniz ortak Cmd.exe ve UNIX komutları kısa bir listesi verilmiştir:

|||||
|-|-|-|-|
|Kat|Dir|bağlama|RM|
|CD|echo|Taşıma|rmdir|
|chdir|silme|popd|Uyku|
|Temizle|H|PS|Sıralama|
|CLS|Geçmişi|pushd|t|
|Kopyalama|sonlandırma|pwd|tür|
|DEL|LP|R|yazma|
|fark|Ls|ren||

Kendinizi bulursanız bunlardan birini kullanarak reflexively komutları ve yerel Windows PowerShell komutunu gerçek adını öğrenmek istiyorsanız, kullanabileceğiniz **Get-diğer** komutu:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Örnekler daha okunabilir hale getirmek için diğer adlar kullanarak Windows PowerShell Kullanıcı Kılavuzu genellikle önler. Rastgele parçacıkları başka bir kaynaktan Windows PowerShell kodu ile çalışma veya kendi diğer adlarını tanımlamak istiyorsanız ancak, diğer adları hakkında daha fazla bilerek bu erken hala yararlı olabilir. Bu bölümde rest standart diğer adlar ve kendi diğer adlarını tanımlamak nasıl ele alınacaktır.

### <a name="interpreting-standard-aliases"></a>Standart diğer adlar yorumlama
Ad-diğer arabirimleri ile uyumluluk için tasarlanmış, yukarıda açıklanan diğer adları farklı olarak Windows PowerShell içinde yerleşik diğer adlar genellikle kısaltma amacıyla tasarlanmıştır. Bu kısa adları hızlı bir şekilde yazılabilir, ancak, ne başvurdukları bilmiyorsanız okuma mümkün.

Windows PowerShell, bir dizi ortak fiilleri ve isimleri için Toplu özellik adları dayalı standart diğer adlar sağlayarak daha anlaşılır olması ve kısaltma arasında tehlikeye dener. Bu toplu adları bildiğinizde okunabilir ortak cmdlet'leri için diğer adlar çekirdek kümesini sağlar. Örneğin, standart diğer adlar içinde fiili **almak** olarak kısaltılır **g**, fiili **ayarlamak** olarak kısaltılır **s**, isim**Öğesi** olarak kısaltılır **ı**, isim **konumu** olarak kısaltılır **l**ve komut için kısaltılmışisim**cm**.

Aşağıda bunun nasıl çalıştığını göstermek için kısa bir örnek verilmiştir. Get-Item standart diğer birleştirme alanından gelir **g** get ve **ı** öğesi için: **GI**. Set-Item standart diğer Birleşen gelen gelen **s** kümesi için ve **ı** öğesi için: **si**. Get-Location standart diğer birleştirme alanından gelir **g** get ve **l** konumu **gl**. Set-Location için standart diğer ad alanından Birleşen gelen **s** kümesi için ve **l** konumu **sl**. Get-Command standart diğer birleştirme alanından gelir **g** get ve **cm** komutun **gcm**. Set-Command cmdlet'i yoktur, ancak olsaydı, biz standart diğer ad alanından gelir tahmin gerçekleştirebilir **s** kümesi için ve **cm** komutu için: **scm**. Ayrıca, karşılaştığınız Windows PowerShell yumuşatma ile tanıdık kişiler **scm** diğer adı ayarlama komutuna başvuruyor tahmin doğrulayamazsınız.

### <a name="creating-new-aliases"></a>Yeni takma adlar oluşturma
Set-diğer cmdlet'ini kullanarak kendi diğer adlar oluşturabilirsiniz. Örneğin, aşağıdaki deyimleri yorumlama standart diğer adlar ele alınan standart cmdlet diğer adlar oluşturma:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Dahili olarak, Windows PowerShell komutları başlangıç sırasında aşağıdaki gibi kullanır, ancak bu diğer adları değiştirilebilir değildir. Gerçekte, bu komutlardan çalıştırma denemesi diğer adı değiştirilemez açıklayan bir hata alırsınız. Örneğin:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```

