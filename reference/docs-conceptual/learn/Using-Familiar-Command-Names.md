---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Tanıdık Komut Adlarını Kullanma
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: b61d647d882d4b2f7ea423a48319e3c104ce96c7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795683"
---
# <a name="using-familiar-command-names"></a>Tanıdık komut adlarını kullanma

PowerShell komutları için diğer adlar tarafından başvurmak için diğer adlar destekler. Diğer ad kullanımı deneyimi kullanıcılarla PowerShell de benzer işlemler için kullanıcılarınızın zaten bildikleri ortak komut adlarını kullanmak için diğer Kabukları sağlar.

Diğer ad kullanımı, yeni bir ad ile başka bir komuta ilişkilendirir. Örneğin, adında bir iç işlev PowerShell sahip `Clear-Host` , çıktı penceresini temizler. Yazabilirsiniz `cls` veya `clear` diğer bir komut isteminde. PowerShell, bu diğer adlar yorumlar ve çalışan `Clear-Host` işlevi.

Bu özelliği PowerShell öğrenmek için kullanıcılara yardımcı olur. İlk olarak, çoğu **cmd.exe** ve UNIX kullanıcıları kullanıcılar adına göre zaten bildiğiniz komut büyük bir topluluğu. PowerShell eşdeğeri aynıdır sonuçları vermeyebilir. Ancak, sonuçları Kapat kullanıcıların yeterli PowerShell komut adını bilmeden çalışmıyor. "Finger bellek" yeni bir komut kabuğunu öğrenme sıkıntıya başlıca kaynaklarından başka bir durumdur. Kullandıysanız **cmd.exe** reflexively yazabilir, yıllardır `cls` ekranı temizlemek için komutu. Diğer olmadan `Clear-Host`, bir hata iletisi alır ve çıktıyı temizlemek için yapmanız gerekenler bilemezsiniz.

Aşağıdaki listede, birkaç ortak gösterilir **cmd.exe** ve PowerShell'de kullanabilirsiniz UNIX komutları:

|||||
|-|-|-|-|
|Cat|dizini|Bağlama|RM|
|CD|echo|Taşıma|rmdir|
|chdir|silme|popd|Uyku|
|Temizle|H|ps|Sıralama|
|CLS|geçmiş|pushd|Tee|
|kopyalama|sonlandırma|Parola|tür|
|DEL|LP|r|Yazma|
|Fark|Ls|ren||

`Get-Alias` Cmdlet'i bir diğer ad ile ilişkili yerel PowerShell komutunu gerçek adını gösterir.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Standart diğer adlar yorumlama

Daha önce açıklanan diğer adı-diğer komut Kabuk ile uyumluluk için tasarlanmıştır.
PowerShell'de yerleşik çoğu diğer adlar, konuyu uzatmamak amacıyla tasarlanmıştır. Daha kısa adları, tür, ancak bunlar ne başvuruda bulunulan tanımadığınız varsa okunması zor kolaydır.

PowerShell diğer adları arasında netlik ve kısaltma tehlikeye deneyin. PowerShell, diğer adlar standart bir dizi ortak adlar ve fiiller için kullanır.

Örnek kısaltmalar:

| İsim veya fiili | Kısaltması |
|--------------|--------------|
| Alma          | G            |
| Ayarla          | s            |
| Öğe         | Ben            |
| Konum     | m            |
| Komut      | cm           |
| Diğer Ad        | Al           |

Kısaltılmış bildiğinizde bu diğer adlar anlaşılabilir.

| Cmdlet adı    | Diğer Ad |
|----------------|-------|
| `Get-Item`     | GI    |
| `Set-Item`     | sı    |
| `Get-Location` | GL    |
| `Set-Location` | SL    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | Gal   |

PowerShell diğer ad kullanımı ile ilgili bilgi sahibi olduğunuzda, tahmin edilmesi kolaydır **sal** diğer başvurduğu `Set-Alias`.

## <a name="creating-new-aliases"></a>Yeni takma adlar oluşturma

Kendi diğer adları kullanarak oluşturabileceğiniz `Set-Alias` cmdlet'i. Örneğin, aşağıdaki deyimleri, daha önce bahsedilen standart cmdlet diğer adlar oluşturma:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Dahili olarak, başlatma sırasında benzer komutlarda PowerShell kullanır, ancak bu diğer adlar takımdaki herhangi biri değildir.
Bu komutlardan birini yürütün çalışırsanız, diğer adı değiştirilemez açıklayan bir hata alırsınız. Örneğin:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
