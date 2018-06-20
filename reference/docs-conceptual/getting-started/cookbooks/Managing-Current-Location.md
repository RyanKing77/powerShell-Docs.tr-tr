---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Geçerli Konumu Yönetme
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952231"
---
# <a name="managing-current-location"></a>Geçerli Konumu Yönetme

Dosya Gezgini'nde klasörü sistemleri gezinirken genellikle belirli bir çalışma konumu - yani, geçerli klasör Aç sahiptir. Geçerli klasöründeki öğeler tıklatarak kolayca yönetilebilir. Belirli bir dosya ile aynı klasörde olduğunda Cmd.exe gibi komut satırı arabirimlerinden için onu tüm dosyasının yolunu belirtmek gerek yerine daha kısa bir adı belirterek erişebilir. Geçerli dizin çalışma dizini olarak adlandırılır.

Windows PowerShell kullanan isim **konumu** çalışma dizini belirtmek için ve bir ailesi cmdlet'lerini inceleyin ve konumunuz işlemek için uygular.

### <a name="getting-your-current-location-get-location"></a>Geçerli konumunuz (Get-konum) alma

Geçerli dizin konumun yolunu belirlemek için girdiğiniz **Get-Location** komutu:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get-Location cmdlet benzer **pwd** BASH kabuğunda komutu. Set-Location cmdlet benzer **cd** Cmd.exe içinde komutu.

### <a name="setting-your-current-location-set-location"></a>Geçerli konumunuz (Set-Location) ayarlama

**Get-Location** komutu ile kullanıldığında **Set-Location** komutu. **Set-Location** komutu, geçerli dizin konumunu belirtmenize olanak verir.

```powershell
Set-Location -Path C:\Windows
```

Komutu girdikten sonra komutun etkisini hakkında doğrudan Microsoft'a almazsınız fark edeceksiniz. Çıktı her zaman yararlı olmadığından bir eylem gerçekleştirmek çoğu Windows PowerShell komutlarını çok az kayıpla veya hiç çıktı üretir. Girdiğiniz zaman başarılı dizin değişikliği oluştuğunu doğrulamak için **Set-Location** içeriyor, komut **- PassThru** , girdiğiniz zaman parametresi **Set-Location**komutu:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

**- PassThru** parametresi birçok Set komutları Windows PowerShell ile hiçbir varsayılan çıkış olduğu durumlarda sonucu hakkında bilgi döndürmek için kullanılabilir.

Kabukları çoğu UNIX ve Windows komut gibi aynı şekilde, geçerli konumuna göre yol belirtebilirsiniz. Standart gösteriminde göreli yollar için bir süre (**.**) iki kat süre ve geçerli klasörünüzü temsil eder (**..** ) geçerli konumunuz üst dizini temsil eder.

Örneğin, içinde olup olmadığını **C:\\Windows** klasörü, bir süre (**.**) temsil eden **C:\\Windows** ve çift nokta (**..** ) temsil eden **C:**. Yazarak C: sürücüsünün kökündeki geçerli konumundan değiştirebilirsiniz:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dosya sistemi sürücülerine gibi olmayan Windows PowerShell sürücülerde aynı tekniği çalışır **HKLM:**. Konumunuz HKLM ayarlayabilirsiniz\\yazarak kayıt defteri anahtarında yazılım:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Windows PowerShell HKLM köküdür üst dizini için dizin konumunu değiştirebilirsiniz: göreli bir yol kullanarak sürücü:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Set-Location yazın ya da yerleşik Windows PowerShell diğer adlar birini Set-Location için (cd, chdir, sl) kullanın. Örneğin:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Kaydetme ve yeni konumlar (anında iletme-konumu ve Pop konumları) geri çağırma

Konumları değiştirirken, burada size verilmiş olması izlenmesi ve önceki konumuna geri döndürmek için yardımcı olur. **İtme konumu** Windows PowerShell cmdlet oluşturur burada size verilmiş olması ve Tamamlayıcı kullanarak geri dizin yolları geçmişinde geçebilirsiniz dizin yolları sıralı geçmişini (bir "yığını")  **POP-Location** cmdlet'i.

Örneğin, Windows PowerShell, genellikle kullanıcının giriş dizininde başlar.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Word *yığın* .NET Framework dahil olmak üzere pek çok programlama ayarlarında, özel bir anlamı yoktur. Öğeleri gibi bir fiziksel yığını yığına put son öğeyi yığın çekebilir ilk öğesidir. Bir öğe için yığın ekleme mikroişlemciye "yığına öğesi Ftp'den olarak" adı verilir. Bir öğe yığından çekme mikroişlemciye "yığından öğesi pencerelerinin olarak" adı verilir.

Geçerli konumu yığına itme ve yerel ayarlar klasörüne taşımak için şunu yazın:

```powershell
Push-Location -Path "Local Settings"
```

Ardından yerel ayarları konumun yığına gönderebilir ve ve yazarak Temp klasöre gidin:

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

En son ziyaret edilen dizine girerek sonra pop **Pop-Location** komut ve değişikliği girerek doğrulayın **Get-Location** komutu:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

İle olarak yalnızca **Set-Location** cmdlet'ini içerebilir **- PassThru** , girdiğiniz zaman parametresi **Pop-Location** cmdlet girdiğiniz dizini görüntülemek için:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Ağ yolları ile konum cmdlet'leri de kullanabilirsiniz. Ortak adlı bir paylaşım ile FS01 adlı bir sunucunuz varsa, yazarak konumunuzu değiştirebilirsiniz

```powershell
Set-Location \\FS01\Public
```

veya

```powershell
Push-Location \\FS01\Public
```

Kullanabileceğiniz **itme konumu** ve **Set-Location** komutların herhangi bir kullanılabilir sürücüye konumu değiştirmek için. Bir veri CD içeren D sürücü harfine sahip yerel bir CD-ROM sürücüsü varsa, örneğin, konumun CD sürücüsüne girerek değiştirebileceğiniz **Set-Location D:** komutu.

Sürücü boş ise, aşağıdaki hata iletisini alırsınız:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Bir komut satırı arabirimi kullanırken, kullanılabilir fiziksel sürücüleri incelemek için dosya Gezgini'ni kullanmak uygun değil. Ayrıca, dosya Gezgini'nde, Windows PowerShell sürücüsü tüm göstermeniz gerekmez. Windows PowerShell sürücülerini yönetmek için Windows PowerShell komut kümesini sağlar ve biz bu sonraki hakkında konuşur.