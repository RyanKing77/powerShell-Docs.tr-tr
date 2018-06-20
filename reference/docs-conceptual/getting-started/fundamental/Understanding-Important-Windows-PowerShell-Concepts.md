---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Önemli Windows PowerShell Kavramlarını Anlama
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951095"
---
# <a name="understanding-important-windows-powershell-concepts"></a>Önemli Windows PowerShell Kavramlarını Anlama
Windows PowerShell tasarım kavramları birçok farklı ortamlarından tümleştirir. Birkaç kişiye belirli Kabukları veya programlama ortamlarının deneyimi sahibiyseniz, ancak bunların tümünün hakkında çok az İnsan öğrenmiş olacaksınız. Bu kavramların bazıları arayan Kabuk yararlı bir genel bakış sağlar.

### <a name="commands-are-not-text-based"></a>Komutları metin tabanlı değildir
Geleneksel komut satırı arabirimi komutları, Windows PowerShell cmdlet'leri - nesneleriyle ilgili için tasarlanmıştır aksine daha fazlasını ekranda görünen karakter dizesi bilgilerini yapılandırılmış. Komut çıktısında her zaman ihtiyacınız olursa, kullanabileceğiniz ek bilgileri taşır. Bu konu, bu belgedeki derinlemesine aşağıdakiler ele alınacaktır.

Geçmişte komut satırı verileri işlemek için metin işleme araçları kullandıysanız, Windows PowerShell'de kullanmayı denerseniz farklı davranırlar olduğunu bulabilirsiniz. Çoğu durumda, belirli bilgileri ayıklamak için metin işleme araçları gerekmez. Veri kısımlarını, standart Windows PowerShell nesnesi işleme komutlarını kullanarak doğrudan erişebilirsiniz.

### <a name="the-command-family-is-extensible"></a>Komut ailesi Genişletilebilir
Cmd.exe gibi arabirimleri doğrudan yerleşik komut kümesini genişletmek bir yol sağlamaz. Cmd.exe içinde çalıştırmak dış komut satırı araçları oluşturabilirsiniz, ancak bu dış Araçları Yardım tümleştirmesi gibi hizmetleri yoktur ve geçerli komutları oldukları Cmd.exe otomatik olarak bilmez.

Yerel ikili komutları olarak bilinen Windows PowerShell'de *cmdlet'leri* (okunur command-lets), Genişletilebilir, oluşturduğunuz ve ek bileşenler kullanarak Windows PowerShell için eklediğiniz cmdlet'leri tarafından. Windows PowerShell *ek bileşenler* gibi diğer arabirimi ikili araçlarında derlenir. Kabuk yanı için yeni cmdlet'ler Windows PowerShell sağlayıcıları eklemek için kullanabilirsiniz.

Windows PowerShell iç komutlarını özel yapısı nedeniyle, biz bunlara başvurur *cmdlet'leri*.

> [!NOTE]
> Windows PowerShell cmdlet'leri dışında komutları çalıştırabilirsiniz. Biz bunları Windows PowerShell Kullanıcı Kılavuzu'nda ayrıntılı ele değil, ancak komut türleri kategoriler olarak hakkında bilmek yararlı oldukları. Windows PowerShell UNIX Kabuk komut dosyalarını ve Cmd.exe toplu iş dosyaları benzer, ancak bir .ps1 dosya adı uzantısına sahip komut dosyalarını destekler. Windows PowerShell doğrudan arabirimi veya komut dosyalarında kullanılan iç işlevler oluşturmanıza olanak sağlar.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell tanıtıcıları konsol giriş ve görüntüleme
Bir komut yazdığınızda, Windows PowerShell komut satırı girişi her zaman doğrudan'e işler. Windows PowerShell Ayrıca ekranda görün çıkış biçimlendirir. Bu önemlidir, çünkü her cmdlet gereken iş azaltır ve hangi cmdlet bağımsız olarak, kullandığınız aynı şekilde her zaman şeyler yapabilirsiniz sağlar. Komut satırı Yardım nasıl bu yaşam aracı geliştiriciler ve kullanıcılar için kolaylaştırır, bir örnek verilmiştir.

Geleneksel komut satırı araçları, isteme ve Yardım görüntüleme için kendi şemaları sahiptir. Bazı komut satırı araçlarını kullanma **/?** Yardım görüntüleme tetiklemek için; Başkalarının kullanmak **-?**, **/H**, hatta **//**. Bazı Yardım konsol görünümünde değil, bir GUI penceresinde görüntüler. Uygulama güncelleştiriciler gibi karmaşık bazı araçlar, kendilerine Yardım görüntülemeden önce iç dosyaları ayıklayın. Yanlış parametre kullanırsanız, aracı neleri yazılan ve otomatik olarak bir görevi gerçekleştirme başlamak yoksay.

Windows PowerShell'de komut girdiğinizde, girdiğiniz her şeyi otomatik olarak ayrıştırılır ve önceden Windows PowerShell tarafından işlenir. Kullanırsanız **-?** bir Windows PowerShell cmdlet parametresi, bu her zaman "Yardım için bu komutu Göster" anlamına gelir. Cmdlet geliştiriciler komutu ayrıştırma gerekmez; Bunlar yalnızca Yardım metni sağlamanız gerekir.

Bile, Windows PowerShell'de geleneksel komut satırı araçları'ı çalıştırdığınızda, Windows PowerShell Yardımı özelliklerini kullanılabilir olduğunu anlamak önemlidir. Windows PowerShell parametreleri işler ve sonuçları için dış araçları geçirir.

> [!NOTE]
> Windows PowerShell'de grafik uygulama çalıştırırsanız, uygulama için penceresi açılır. Windows PowerShell, yalnızca zaman komut satırı işleme, kaynağı veya konsol penceresine döndürülen uygulama çıktısı giriş müdahalesi; Uygulama dahili olarak şeklini etkilemez.

### <a name="windows-powershell-uses-some-c-syntax"></a>Windows PowerShell, bazı C# sözdizimi kullanır.
Windows PowerShell sözdizimi özellikleri ve çok benzer kullanılan C# programlama dili, Windows PowerShell kullanarak .NET Framework üzerinde bağlı olduğu anahtar sözcükleri vardır. Dille ilgileniyorsanız Windows PowerShell öğrenme, C# öğrenme çok daha kolay hale getirir.

C# Programcı emin değilseniz, bu önemli değildir. Ancak, C# ile bilginiz varsa, benzerlikleri çok daha kolay Windows PowerShell öğrenme yapabilirsiniz.