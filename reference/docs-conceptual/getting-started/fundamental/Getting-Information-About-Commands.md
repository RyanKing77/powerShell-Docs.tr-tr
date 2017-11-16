---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Komutlar hakkında bilgi alma"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a>Komutlar hakkında bilgi alma
Windows PowerShell **Get-Command** cmdlet'i Geçerli oturumunuzda kullanılabilir tüm komutları alır. Yazdığınızda **Get-Command** bir Windows PowerShell komut isteminde, aşağıdakine benzer bir çıktı göreceksiniz:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Bu görünüm Cmd.exe Yardım çıktısı gibi çok çıktı: iç komutları tablo özetini. Alıntı içinde **Get-Command** yukarıda gösterilen her komut gösterilen çıktıyı içerir, bir CommandType Cmdlet komutu. Windows PowerShell'in iç komut türü - kabaca için karşılık gelen bir cmdlet'tir **dir** ve **cd** komutları Cmd.exe ve UNIX Kabukları BASH gibi öğelerin.

Çıktısı olarak **Get-Command** komut, tüm tanımları bitiş PowerShell tüm içeriği görüntülenemiyor göstermek için üç nokta ile (...) kullanılabilir alanı. Windows PowerShell çıkış görüntülediğinde, çıktı metin olarak biçimlendirir ve düzgün bir şekilde penceresine sığacak veri olmak için düzenler. Biz bu konuda daha sonra bölümünde biçimlendiricileri üzerinde konuşur.

**Get-Command** cmdlet sahip bir **sözdizimi** her cmdlet sözdizimi alır parametresi. Get-Help cmdlet sözdizimi almak için aşağıdaki komutu kullanın:

**Get-Help Get-Command-sözdizimi**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a>Kullanılabilir komut türlerinden görüntüleme
**Get-Command** komutu, Windows PowerShell içinde kullanılabilir olan her komut listesinde değil. Bunun yerine, **Get-Command** komutu geçerli oturumdaki yalnızca cmdlet'leri listeler. Windows PowerShell gerçekte birkaç komut türlerini destekler. Windows PowerShell Kullanıcı Kılavuzu'nda ayrıntılı açıklanmamaktadır diğer adları, işlevleri ve komut dosyaları da Windows PowerShell komutları, ancak. Yürütülebilir dosya veya bir kayıtlı dosya türü işleyicisi olan dış dosyalar da komutları olarak sınıflandırılır.

Tüm komutlar oturumda almak için şunu yazın:

```
Get-Command *
```

Bu liste, arama yolunuzda dış dosyalar içerdiğinden, binlerce öğeye içerebilir. Azaltılmış bir grup komutları aramak daha kullanışlıdır.

Diğer türleri yerel komutları almak için **CommandType** parametresinin **Get-Command** cmdlet'i.

> [!NOTE]
> Yıldız işareti (\*) joker karakter eşleştirme Windows PowerShell komut bağımsız değişkenleri için kullanılır. \* "Eşleştirilmez ve bir veya daha fazla herhangi bir karakter". Yazabilirsiniz **Get-Command bir\&#42;** harfiyle başlayan tüm komutları bulmak için "a". Joker karakter cmd.exe eşleştirme Windows PowerShell'in joker ayrıca bir süre eşleşir.

Atanan takma adlar komutların olan komut diğer adları almak için aşağıdakileri yazın:

```
Get-Command -CommandType Alias
```

Geçerli oturumdaki işlevleri almak için şunu yazın:

```
Get-Command -CommandType Function
```

Windows PowerShell'in arama yolunda komut dosyalarını görüntülemek için şunu yazın:

```
Get-Command -CommandType Script
```

