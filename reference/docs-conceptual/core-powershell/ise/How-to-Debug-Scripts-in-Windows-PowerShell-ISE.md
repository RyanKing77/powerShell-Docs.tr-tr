---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Betiklerde Hata Ayıklama
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953414"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Windows PowerShell ISE’de Betiklerde Hata Ayıklama

Bu makalede, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) visual hata ayıklama özelliklerini kullanarak komut dosyalarını yerel bir bilgisayarda hata ayıklama açıklar.

## <a name="how-to-manage-breakpoints"></a>Kesme noktaları yönetme

Bir kesme noktası işlemi değişkenler ve komut dosyanızı çalıştığı ortam geçerli durumunu inceleyebilirsiniz duraklatmak oluşturulacağı yeri bir belirlenmiş bir betik içinde yerdir. Komut bir kesme noktası tarafından duraklatıldı sonra kodunuzu durumunu incelemek için konsol bölmesinde komutları çalıştırabilirsiniz.  Değişkenleri çıktı veya diğer komutları çalıştırın. Şu anda çalışan betik bağlamına görünür olan tüm değişkenlerin değerini bile değiştirebilirsiniz. Görmek istediğiniz inceleyen sonra betiğin çalışmasını devam edebilirsiniz.

Windows PowerShell hata ayıklama ortamında üç tür kesme noktaları ayarlayabilirsiniz:

1. **Satır kesme noktası**. Komut dosyası işlemi sırasında belirlenen satır ulaşıldığında betik duraklatır

2. **Değişken kesme noktası.** Belirtilen değişken değeri değiştiğinde betik duraklatır.

3. **Kesme noktası komutu.** Belirtilen komut komut dosyası işlemi sırasında hakkında çalıştırılacak olduğunda betik duraklatır. Daha fazla kesme noktası yalnızca işleme filtrelemek için parametreleri içerebilir. Komutu, oluşturduğunuz bir işlevi olarak da olabilir.

Bu, Windows PowerShell ISE hata ayıklama ortamında yalnızca satır kesme noktaları menüsü veya klavye kısayolları kullanılarak ayarlanabilir. Kesme noktaları diğer iki tür ayarlanabilir, ancak konsol bölmesinden kullanarak ayarlandıktan [kümesi PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet'i. Bu bölümde, nasıl kullanılabiliyorsa menüleri kullanarak Windows PowerShell ISE hata ayıklama görevleri gerçekleştirmek ve komut dosyası kullanarak konsol bölmesinden komutları daha geniş ölçüdeki gerçekleştirmek açıklanmaktadır.

### <a name="to-set-a-breakpoint"></a>Bir kesme noktası ayarlamak için

Yalnızca kaydedildikten sonra bir kesme noktası komut dosyasında ayarlayabilirsiniz. Bir satır kesme noktası ayarlayın ve ardından istediğiniz satıra sağ **kesme**. Veya, bir satır kesme noktası ayarlamak istediğiniz satırı tıklatın ve tuşuna basın **F9** veya **hata ayıklama** menüsünde tıklatın **kesme**.

Aşağıdaki betik nasıl değişken bir kesme noktası konsol bölmesinden kullanarak ayarlayabileceğiniz bir örnektir [kümesi PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet'i.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Tüm kesme noktaları listesi

Tüm kesme noktaları geçerli Windows PowerShell oturumunda görüntüler.

Üzerinde **hata ayıklama** menüsünde tıklatın **listesi kesme noktaları**. Aşağıdaki komut dosyası kullanarak Konsol bölmesinde tüm kesme noktalarını nasıl listeleyebilirsiniz bir örnektir [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet'i.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Kesme noktası kaldırma

Bir kesme noktası kaldırma siler.

Daha sonra yeniden kullanmak için göz önünde bulundurun isteyebileceğiniz düşünüyorsanız [bir kesme noktası devre dışı](#disable-a-breakpoint) , bunun yerine.
Bir kesme noktası kaldırın ve ardından istediğiniz satıra sağ **kesme**.
Veya, bir kesme noktası kaldırmak istediğiniz satırı tıklatın ve **hata ayıklama** menüsünde tıklatın **kesme**.
Aşağıdaki komut dosyası kullanarak belirtilen Kimliğe sahip bir kesme noktası konsol bölmesinden kaldırmak nasıl örneğidir [Kaldır PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Tüm kesme noktalarını kaldırır

Geçerli oturumdaki tanımlanan tüm kesme noktalarını kaldırmak için **hata ayıklama** menüsünde tıklatın **tüm kesme noktalarını Kaldır**.

Aşağıdaki komut dosyası kullanarak ve konsol bölmesinde tüm kesme noktalarını kaldırmak nasıl örneğidir [Kaldır PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Bir kesme noktası devre dışı bırak

Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.  Belirli satır kesme noktası devre dışı bırakmak için istediğiniz bir kesme noktası devre dışı bırakın ve ardından satır sağ **devre dışı kesme noktası**. Veya, bir kesme noktası devre dışı bırakmak istediğiniz satırı tıklatın ve tuşuna basın **F9** veya **hata ayıklama** menüsünde tıklatın **kesme noktası devre dışı**. Aşağıdaki komut dosyası ve konsol bölmesinde kullanarak belirtilen Kimliğe sahip bir kesme noktası nasıl kaldırabileceğiniz bir örnektir [devre dışı bırakma PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Tüm kesme noktaları devre dışı bırak

Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.  Üzerinde geçerli oturumdaki tüm kesme noktaları devre dışı bırakmak için **hata ayıklama** menüsünde tıklatın **tüm kesme noktaları devre dışı**. Aşağıdaki betik nasıl, konsol bölmesinde tüm kesme noktalarını kullanarak devre dışı bırakabilirsiniz, bir örnek verilmiştir [devre dışı bırakma PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Bir kesme noktası etkinleştir

Belirli bir kesme noktası etkinleştirmek için istediğiniz bir kesme noktası etkinleştirin ve ardından satır sağ **etkinleştirmek kesme noktası**. Veya tuşuna basın ve bir kesme noktası etkinleştirmek istediğiniz çizgi **F9** veya **hata ayıklama** menüsünde tıklatın **etkinleştirmek kesme noktası**. Aşağıdaki komut dosyası kullanarak belirli kesme noktaları Konsol bölmesinde nasıl etkinleştirebilirsiniz bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Tüm kesme noktalarını etkinleştirin

Geçerli oturumdaki tanımlanan tüm kesme noktaları etkinleştirmek için **hata ayıklama** menüsünde tıklatın **tüm kesme noktalarını etkinleştir**. Aşağıdaki komut dosyası kullanarak Konsol bölmesinde tüm kesme noktalarını nasıl etkinleştirebilirsiniz bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Hata ayıklama oturumu yönetme

Hata ayıklama başlamadan önce bir veya daha fazla kesme noktaları ayarlamanız gerekir. Hata ayıklamak istediğiniz komut dosyasını kaydettiğiniz sürece bir kesme noktası ayarlanamıyor. Yönleri üzerinde bir kesme noktası ayarlama için bkz: [kesme noktaları yönetme](#how-to-manage-breakpoints) veya [kümesi PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Hata ayıklama başlattıktan sonra bir komut dosyası hata ayıklamayı durdurun kadar düzenleyemezsiniz. Bunu çalıştırılmadan önce ayarlanmış bir veya daha fazla kesme noktaları olan bir komut dosyası otomatik olarak kaydedilir.

### <a name="to-start-debugging"></a>Hata ayıklama başlatılamıyor

Tuşuna **F5** veya araç çubuğunda tıklatın **komut dosyasını Çalıştır** simge veya **hata ayıklama** menüsünü tıklatın **Çalıştır/devam**. İlk kesme bulduğu kadar komut dosyasını çalıştırır. İşlemi ortada duraklatır ve üzerinde duraklatıldı satır vurgular.

### <a name="to-continue-debugging"></a>Hata ayıklama devam etmek için

Basın **F5** veya araç çubuğunda tıklatın **komut dosyasını Çalıştır** simgesi, veya **hata ayıklama** menüsünde tıklatın **Çalıştır/devam** veya Konsol bölmesinde, yazın **C** ve tuşuna basarak **ENTER**. Bu, başka hiçbir kesme noktaları karşılaştıysanız sonraki kesme veya komut dosyasının sonuna çalıştırmaya devam etmek komut dosyası neden olur.

### <a name="to-view-the-call-stack"></a>Çağrı yığınını görüntülemek için

Çağrı yığını konumu betik çalıştırmak geçerli görüntüler. Komut dosyası, farklı bir işlev tarafından çağrıldı bir işlev çalışıyorsa, ardından, görüntüde çıkış ek satır temsil edilir. En alttaki satır özgün komut dosyasını ve satır içinde bir işlev çağrıldı görüntüler. Sonraki satır programları bu işlev ve satır, içinde başka bir işlev çağrılmış.  En üstteki satır kesme ayarlanan geçerli satır geçerli bağlamı gösterir.

Duraklatıldı olsa da, geçerli çağrı yığını görmek için basın **CTRL + SHIFT + D** veya **hata ayıklama** menüsünde tıklatın **görüntü çağrı yığını** veya Konsol bölmesinde yazın **K**  ve tuşuna basarak **ENTER**.

### <a name="to-stop-debugging"></a>Hata ayıklamayı durdurmak için

Basın **SHIFT + F5** veya **hata ayıklama** menüsünde tıklatın **durdurma hata ayıklayıcı**, veya Konsol bölmesinde yazın **Q** ve tuşuna basın  **GİRİN**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Nasıl üzerinden adım, adımla ve hata ayıklama sırasında adım

Atlama bir seferde bir deyim çalıştırma işlemidir. Kod satırında durdurun ve değişkenleri ve sistem durumunu değerlerini inceleyin. Aşağıdaki tabloda üzerinden Adımlama, içine adımlama ve atlama gibi ortak hata ayıklama görevler açıklanmaktadır.

| Hata ayıklama görevi | Açıklama | PowerShell ISE gerçekleştirmek nasıl |
| --- | --- | --- |
| **Girme** | Geçerli deyimini yürütür ve ardından sonraki deyimde durdurur. Aksi takdirde geçerli deyimi bir işlev veya komut dosyası çağrısı, bu işlev veya komut dosyası hata ayıklayıcı adımları ise, sonraki deyimde durdurur. | Basın **F11** veya **hata ayıklama** menüsünde tıklatın **Step Into**, konsol bölmesinde yazın veya **S** tuşuna basın **ENTER**. |
| **Adımlama** | Geçerli deyimini yürütür ve ardından sonraki deyimde durdurur. Geçerli deyimi ise bir işlev veya komut dosyası çağrısı sonra hata ayıklayıcı tüm işlev veya komut çalıştırır ve next deyimi işlev çağrısı sonra aşamasında durur. | Basın **F10** veya **hata ayıklama** menüsünde tıklatın **Step Over**, konsol bölmesinde yazın veya **V** ve tuşuna basın **ENTER**. |
| **Dışarı Adım** | Adımlar geçerli işlevi dışında ve işlevini iç içe yerleştirilmiş ise bir düzey yukarı. Ana gövdesinde komut dosyasının sonuna veya sonraki kesme yürütülürse. Atlanan deyimleri yürütüldü, ancak üzerinden adım adım değil. | Basın **SHIFT + F11**, veya **hata ayıklama** menüsünde tıklatın **Step Out**, konsol bölmesinde yazın veya **O** tuşuna basın **ENTER**. |
| **Devam etmek** | Yürütme bitiş veya sonraki kesme devam eder. Atlanan işlevler ve çağrılarını yürütüldü, ancak üzerinden adım adım değil. | Tuşuna basın **F5** veya **hata ayıklama** menüsünde tıklatın **Çalıştır/devam**, konsol bölmesinde yazın veya **C** ve tuşuna basın **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Hata ayıklama sırasında değişkenlerin değerlerini görüntüleme

Kod üzerinden adım olarak komut dosyasındaki değişkenlerin geçerli değerlerini görüntüleyebilirsiniz.

### <a name="to-display-the-values-of-standard-variables"></a>Standart değişkenlerin değerleri görüntülemek için

Aşağıdaki yöntemlerden birini kullanın:

- Betik bölmesinde araç ipucu olarak değerini görüntülemek için değişken üzerine gelerek.

- Konsol bölmesinde, değişken adını yazıp tuşuna basın **ENTER**.

İşe tüm bölmeleri her zaman aynı kapsamda olur. Bu nedenle, bir komut dosyası hata ayıklarken, komut dosyası kapsamda Konsol bölmesinde yazdığınız komutları çalıştırın. Bu değişkenlerin değerleri bulmak ve yalnızca komut dosyasında tanımlanan işlevleri çağırmak için konsol bölmesinde kullanmanıza olanak sağlar.

### <a name="to-display-the-values-of-automatic-variables"></a>Otomatik değişkenlerin değerleri görüntülemek için

Bir komut dosyası hata ayıklarken neredeyse tüm değişkenlerin değerini görüntülemek için yukarıdaki yöntemi kullanabilirsiniz. Ancak, bu yöntemler aşağıdaki otomatik değişkenleri çalışmaz.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Bu değişkenlerin değerini görüntülemek çalışırsanız değil değişkenin değeri olarak komut dosyasında hata ayıklayıcı iç ardışık düzeninde kullanması için bu değişkenin değerini alın. Bu sorunu birkaç değişkenleri ($_, $Input, $MyInvocation, $PSBoundParameters ve $Args) aşağıdaki yöntemi kullanarak çalışabilirsiniz:

1. Komut dosyasında otomatik değişkenin değerini yeni bir değişkene atayın.

2. Betik bölmesine yeni değişken üzerine gelerek veya onları veya Konsol bölmesinde yeni değişken yazarak yeni değişken değerini görüntüleyin.

Örneğin, komut dosyasında $MyInvocation değişkenin değerini görüntülemek için $scriptname gibi yeni bir değişken değeri atamak ve ardından üzerine gelerek veya değerini görüntülemek için $scriptname değişkeni yazın.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE’yi Keşfetme](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)