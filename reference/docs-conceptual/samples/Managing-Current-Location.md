---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Geçerli Konumu Yönetme
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293195"
---
# <a name="managing-current-location"></a>Geçerli Konumu Yönetme

Dosya Gezgini'nde klasörü sistemleri gittiğinizde, genellikle belirli bir çalışma konumu - yani, geçerli açık klasör sahiptir. Geçerli klasördeki öğeleri tıklatarak kolayca yönetilebilir. Belirli bir dosya aynı klasörde işiniz Cmd.exe gibi komut satırı arabirimleri için tüm dosya yolunu belirtmeniz gerek yerine görece kısa bir ad belirterek erişebildiğinizi. Geçerli dizin, çalışma dizini olarak adlandırılır.

Windows PowerShell kullanan isim **konumu** çalışma dizini belirtmek için ve bir ailesi cmdlet'lerini incelemek ve işlemek, konumunuz için uygular.

## <a name="getting-your-current-location-get-location"></a>Geçerli konumunuz (Get-konumu)

Geçerli dizin konumunuzun yolunu belirlemek için girin **Get-Location** komutu:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get-Location cmdlet benzer **pwd** BASH kabuğunda komutu. Set-Location cmdlet benzer **cd** Cmd.exe içinde komutu.

## <a name="setting-your-current-location-set-location"></a>Geçerli konumunuzu (konum ayarlama) ayarlama

**Get-Location** komutu ile kullanıldığında **Set-Location** komutu. **Set-Location** komutu, geçerli dizin konumunu belirtmenize olanak verir.

```powershell
Set-Location -Path C:\Windows
```

Komutu girdikten sonra komut etkisi hakkında Geri bildirimlerinizi doğrudan almazsınız fark edeceksiniz. Çıkış her zaman kullanışlı olmadığı için bir eylem gerçekleştiren çoğu Windows PowerShell komutlarını çok az kayıpla veya hiç çıkış üretir. Girdiğiniz zaman başarılı dizin değişikliği oluştuğunu doğrulamak için **Set-Location** komutu, dahil **- PassThru** , girdiğinizde parametresi **Set-Location**komutu:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

**- PassThru** parametre kümesi komutların çoğu Windows PowerShell ile varsayılan çıkış olduğu durumlarda sonuç hakkında bilgi döndürmek için kullanılabilir.

Kabuklar çoğu Windows ve UNIX komutunu gibi aynı şekilde geçerli konumunuza göre yolu belirtebilirsiniz. Göreli yollar için standart gösteriminde bir süre (**.**) Geçerli klasörünüzü ve iki kat bir süre temsil eder (**..** ) geçerli konumunuzu üst dizinini temsil eder.

Örneğin, bulunduğunuz **C:\\Windows** klasörü, nokta (**.**) temsil eden **C:\\Windows** ve çift nokta (**..** ) temsil eden **C:**. Yazarak geçerli konumunuzdan C: sürücüsünün köküne değiştirebilirsiniz:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dosya sistemi sürücüleri gibi olmayan Windows PowerShell sürücülerini aynı tekniği çalışır **HKLM:**. Konumunuz için HKLM ayarlayabilirsiniz\\yazarak kayıt defteri anahtarında yazılım:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Windows PowerShell HKLM köküdür üst dizine dizin konumunu değiştirebilirsiniz: göreli yolu kullanarak sürücü:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Set-Location yazın veya Set-Location için (cd, chdir, sl) herhangi bir yerleşik Windows PowerShell diğer adları kullanın. Örneğin:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Kaydetme ve en son konumlar (anında iletme konumu ve bulunma noktası konumuna) geri çağırma

Konumları değiştirirken, burada size verilmiş olması, izlenmesi ve, önceki konumuna geri döndürmek için yararlıdır. **Anında iletme konumu** Windows PowerShell cmdlet'i, burada size verilmiş olması ve Tamamlayıcı kullanarak geri dizin yolları geçmişinde geçebilirsiniz dizin yolları sıralı geçmişini ("yığın") oluşturur  **Bulunma noktası konumuna** cmdlet'i.

Örneğin, Windows PowerShell, genellikle kullanıcının giriş dizininde başlar.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Word *yığın* .NET Framework dahil olmak üzere pek çok programlama Ayarları'nda özel bir anlamı vardır. Öğeleri fiziksel yığını gibi yığın üstüne koymak son öğeyi, yığının çekebilirsiniz ilk öğedir. Bir yığın için bir öğe eklemeye mikroişlemciye "öğesi yığına göndermek" adı verilir. Bir öğe yığından çekme mikroişlemciye "öğesi yığından pencerelerinin olarak" adı verilir.

Geçerli konumun yığına anında iletme ve ardından yerel ayarlar klasörüne taşımak için şunu yazın:

```powershell
Push-Location -Path "Local Settings"
```

Yerel ayarlar konumunu yığına gönderin ve yazarak Temp klasörüne taşıyın:

```powershell
Push-Location -Path Temp
```

Dizinleri girerek değiştiğini doğrulayın **Get-Location** komutu:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

En son ziyaret edilen dizine girerek ardından açılan **bulunma noktası konumuna** komutunu ve girerek değişikliği doğrulayın **Get-Location** komutu:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Olduğu gibi **Set-Location** cmdlet'ini içerebilir **- PassThru** , girdiğinizde parametresi **bulunma noktası konumuna** cmdlet'i girdiğiniz dizin görüntülemek için:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Ağ konumu cmdlet'leri de kullanabilirsiniz. Ortak adlı bir paylaşım ile FS01 adlı bir sunucu varsa, konumunuzu yazarak değiştirebilirsiniz

```powershell
Set-Location \\FS01\Public
```

veya

```powershell
Push-Location \\FS01\Public
```

Kullanabileceğiniz **anında iletme konumu** ve **Set-Location** herhangi bir kullanılabilir sürücü konumunu değiştirmek için komutları. Bir veri CD içeren D sürücü harfine sahip yerel bir CD-ROM sürücüsü varsa, örneğin, konum CD sürücüsüne girerek değiştirebileceğiniz **Set-Location D:** komutu.

Sürücü boş ise, aşağıdaki hata iletisini alırsınız:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Bir komut satırı arabirimi kullanırken, kullanılabilir fiziksel sürücüleri incelemek için dosya Gezgini'ni kullanmak uygun değil. Ayrıca, dosya Gezgini'nde, tüm Windows PowerShell sürücüsü göstermeniz gerekmez. Windows PowerShell sürücülerini yönetmek için Windows PowerShell komut kümesini sağlar ve biz bu sonraki hakkında Bahsediyor.
