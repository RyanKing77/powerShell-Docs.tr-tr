---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de Betiklerde Hata Ayıklama
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086876"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Windows PowerShell ISE’de Betiklerde Hata Ayıklama

Bu makalede, betikleri yerel bir bilgisayardaki Windows PowerShell Tümleşik komut dosyası ortamı (ISE) visual hata ayıklama özelliklerini kullanarak hata ayıklama açıklar.

## <a name="how-to-manage-breakpoints"></a>Kesme noktaları yönetme

Bir kesme noktası işlemi değişkenler ve betiğinizi çalıştırıldığı ortamın geçerli durumu inceleyebilirsiniz duraklatmak için istediğiniz bir belirtilen bir betikte yerdir. Betiğinizi bir kesme noktası tarafından duraklatıldı sonra konsol bölmesinde betiğinizi durumunu incelemek için komutları çalıştırabilirsiniz.  Çıkış değişkenleri veya diğer komutları çalıştırın. Hatta, şu anda çalışan betik bağlamı için görünür olan tüm değişkenler değerini değiştirebilirsiniz. Görmek istediğiniz inceledikten sonra betiğin devam edebilir.

Windows PowerShell hata ayıklama ortamında üç tür kesme noktaları ayarlayabilirsiniz:

1. **Satır kesme noktası**. Komut dosyası işlemi sırasında belirtilen satırın ulaşıldığında betik duraklatır.

2. **Değişken kesme noktası.** Belirtilen değişken değerini değiştiğinde betik duraklatır.

3. **Kesme noktası komutu.** Belirtilen komut hakkında komut dosyası işlemi sırasında çalıştırılacak olduğunda betiği duraklatır. Bu, daha fazla kesme noktası yalnızca, istediğiniz işlemi için filtre uygulamak için parametre içerebilir. Komut, oluşturduğunuz bir işlev de olabilir.

Bu, Windows PowerShell ISE hata ayıklama ortamında, yalnızca satır kesme noktaları menüsünü veya klavye kısayolları kullanılarak ayarlanabilir. Diğer iki tür kesme noktaları ayarlayın, ancak ve konsol bölmesinde kullanarak ayarlanırlar [kümesi PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet'i. Bu bölümde, nasıl kullanılabiliyorsa menüleri kullanarak Windows PowerShell ISE'de hata ayıklama görevlerini gerçekleştirmek ve komut dosyası kullanarak bir yelpazede komutları ve konsol bölmesinde gerçekleştirmek açıklanmaktadır.

### <a name="to-set-a-breakpoint"></a>Bir kesme noktası ayarlamak için

Yalnızca kaydedildikten sonra bir kesme noktası komut dosyasında ayarlayabilirsiniz. Bir satır kesme noktası ayarlayın ve ardından istediğiniz satıra sağ tıklayın **iki durumlu kesme noktası**. Veya bir satır kesme noktası ayarlamak istediğiniz satıra tıklayın ve basın **F9** veya **hata ayıklama** menüsünde tıklayın **iki durumlu kesme noktası**.

Aşağıdaki betik ve konsol bölmesinde kullanarak değişken bir kesme noktası nasıl ayarlayabilirsiniz ilişkin bir örnektir [kümesi PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet'i.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Tüm kesme noktalarını listeleyin

Tüm kesme noktalarını, geçerli Windows PowerShell oturumunda görüntüler.

Üzerinde **hata ayıklama** menüsünde tıklatın **listesi kesme noktaları**. Aşağıdaki betiği kullanarak tüm kesme noktalarını Konsol bölmesinde nasıl listeleyebilirsiniz ilişkin bir örnektir [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet'i.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Bir kesme noktasını Kaldır

Bir kesme noktası kaldırma siler.

Daha sonra yeniden kullanmak için göz önünde bulundurun isteyebilirsiniz düşünüyorsanız [bir kesme noktası devre dışı](#disable-a-breakpoint) , bunun yerine.
Bir kesme noktası kaldırın ve ardından istediğiniz satıra sağ tıklayın **iki durumlu kesme noktası**.
Veya, bir kesme noktasını kaldırmak istediğiniz satırına tıklayın ve **hata ayıklama** menüsünde tıklayın **iki durumlu kesme noktası**.
Aşağıdaki betiği kullanarak belirtilen Kimliğe sahip bir kesme noktası konsol bölmesinden kaldırma örneğidir [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Tüm kesme noktalarını Kaldır

Geçerli oturumda tanımlanan tüm kesme noktalarını kaldırmak için **hata ayıklama** menüsünü tıklatın **tüm kesme noktalarını Kaldır**.

Aşağıdaki betiği kullanarak tüm kesme noktalarını ve konsol bölmesinde kaldırma örneğidir [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet'i.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Bir kesme noktası devre dışı bırak

Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.  Belirli satıra bir kesme noktasını devre dışı bırakmak için bir kesme noktası devre dışı bırakın ve ardından istediğiniz satıra sağ tıklayın **devre dışı kesme noktası**. Ya da bir kesme noktasını devre dışı bırakmak istediğiniz satıra tıklayın ve basın **F9** veya **hata ayıklama** menüsünde tıklayın **devre dışı kesme noktası**. Aşağıdaki betik ve konsol bölmesinde kullanarak belirtilen Kimliğe sahip bir kesme noktası nasıl kaldırabilirsiniz ilişkin bir örnektir [devre dışı bırak PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Tüm kesme noktalarını devre dışı bırak

Bir kesme noktası devre dışı bırakma kaldırmaz; etkinleştirilene kadar bu kapanır.  Tüm kesme noktalarını devre dışı geçerli oturum için **hata ayıklama** menüsünde tıklayın **tüm kesme noktalarını devre dışı**. Aşağıdaki komut dosyasını nasıl, konsol bölmesinde tüm kesme noktalarını kullanarak devre dışı bırakabilirsiniz, bir örnektir [devre dışı bırak PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet'i.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Bir kesme noktasını etkinleştir

Belirli bir kesme noktası etkinleştirmek için bir kesme noktasını etkinleştir ve ardından istediğiniz satıra sağ tıklayın **kesme noktasını etkinleştir**. Ya da bir kesme noktasını etkinleştir ve ENTER tuşuna basın istediğiniz satıra tıklayın **F9** veya **hata ayıklama** menüsünde tıklatın **kesme noktasını etkinleştir**. Aşağıdaki betiği kullanarak belirli kesme noktaları Konsol bölmesinde nasıl olanak sağlayabileceğiniz ilişkin bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Tüm kesme noktalarını etkinleştir

Geçerli oturumda tanımlanan tüm kesme noktalarını etkinleştirmek için **hata ayıklama** menüsünü tıklatın **tüm kesme noktalarını etkinleştir**. Aşağıdaki betiği kullanarak tüm kesme noktalarını Konsol bölmesinde nasıl olanak sağlayabileceğiniz ilişkin bir örnektir [etkinleştir PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet'i.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Hata ayıklama oturumu yönetme

Hata ayıklamaya başlamadan önce bir veya daha fazla kesme noktası ayarlamanız gerekir. Hata ayıklamak istediğiniz komut kaydedilmezse bir kesme noktası ayarlanamıyor. Yönleri üzerinde nasıl bir kesme noktası ayarlamak için bkz: [kesme noktaları yönetme](#how-to-manage-breakpoints) veya [kümesi PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Hata ayıklamayı başlattıktan sonra bir komut dosyası hata ayıklamayı durdurmak kadar düzenleyemezsiniz. Çalıştırmadan önce ayarlanan bir veya daha fazla kesme noktaları olan bir komut dosyası otomatik olarak kaydedilir.

### <a name="to-start-debugging"></a>Hata ayıklamayı başlatmak için

Tuşuna **F5** veya araç çubuğunda **betiğini Çalıştır** simgesini veya **hata ayıklama** menüsünü tıklatın **Çalıştır/Continue**. İlk kesme noktasına karşılaşana kadar betiği çalıştırır. Bu işlemi burada duraklatır ve üzerinde duraklatıldı satırı vurgular.

### <a name="to-continue-debugging"></a>Hata ayıklamaya devam etmek için

Tuşuna **F5** veya araç çubuğunda **betiğini Çalıştır** simgesini veya **hata ayıklama** menüsünde tıklayın **Çalıştır/devam** veya Konsol bölmesinde, yazın **C** ve tuşuna **ENTER**. Bu, kodun sonraki kesme noktasına veya betiğin sonundaki başka hiçbir kesme noktası karşılaşıldığında çalışmaya devam etmesine neden olur.

### <a name="to-view-the-call-stack"></a>Çağrı yığınını görüntülemek için

Betik konumu çalıştırmak geçerli çağrı yığınını görüntüler. Betik farklı bir işlev tarafından çağrılan bir işlevde çalışıyorsa, ardından, ekranda ek satır çıktıda gösterilir. En alttaki satır özgün komut dosyası ve satır bir işlev çağrıldı görüntüler. Bu işlev ve bunu, başka bir işleve çağrılmış bir satırda sonraki satır gösterileceğini.  En üst satır üzerinde Kesme noktasının ayarlandığını geçerli satırın geçerli bağlam gösterir.

Geçerli çağrı yığınını görmek için duraklatıldığı sırada basın **CTRL + SHIFT + D** veya **hata ayıklama** menüsünde, tıklayın **görünen çağrı yığını** veya Konsol bölmesinde, yazın **K**  ve tuşuna **ENTER**.

### <a name="to-stop-debugging"></a>Hata ayıklamayı durdurmak için

Basın **SHIFT + F5** veya **hata ayıklama** menüsünde, tıklayın **durdurma hata ayıklayıcı**, ya da konsol bölmesinde, yazın **Q** ve tuşuna  **GİRİN**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Nasıl Atla, adımlama ve hata ayıklama sırasında dışına adımla

Adımlama aynı anda çalıştırılan bir deyim işlemidir. Bir kod satırının durdurun ve değişkenleri ve sistem durumunu inceleyin. Aşağıdaki tablo üzerinden Adımlama, içine adımlama ve Adımlama gibi yaygın hata ayıklama görevlerini açıklar.

| Görev hata ayıklama | Açıklama | PowerShell ISE'de yerine getirmeyi |
| --- | --- | --- |
| **Adımla** | Geçerli deyimi yürütür ve ardından sonraki deyimi durdurur. Geçerli deyimi bir işlev veya komut dosyası çağrısı, sonra da, işlev veya komut dosyası hata ayıklayıcı adımlamayla ise, aksi halde sonraki deyimi durdurur. | Basın **F11** veya **hata ayıklama** menüsünde, tıklayın **içine adımla**, veya Konsol bölmesinde, **S** basın **ENTER**. |
| **Üzerinden adımla** | Geçerli deyimi yürütür ve ardından sonraki deyimi durdurur. Geçerli deyimi ise bir işlev veya betiği çağrı ve hata ayıklayıcı tüm işlev veya betiği çalıştırır ve sonraki deyim işlev çağrısından sonra durakları. | Basın **F10** veya **hata ayıklama** menüsünde, tıklayın **Step Over**, veya Konsol bölmesinde, **V** basın **ENTER**. |
| **Dışına adımla** | Geçerli işlev ve işlev iç içe bir düzey adımlar. Ana gövdesinde, komut sonuna ya da sonraki kesme noktasına yürütülürse. Atlanan deyimleri yürütülür, ancak aracılığıyla basamaklı değil. | Basın **SHIFT + F11**, veya **hata ayıklama** menüsünde tıklatın **Step Out**, veya Konsol bölmesinde, **O** tuşuna basın **ENTER**. |
| **Continue** | Sonuna ya da sonraki kesme noktasına yürütme devam eder. Atlanan işlevleri ve çağrılarını yürütülür, ancak aracılığıyla basamaklı değil. | Basın **F5** veya **hata ayıklama** menüsünde, tıklayın **Çalıştır/devam**, veya Konsol bölmesinde, **C** basın **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Hata ayıklama sırasında değişkenlerin değerlerini görüntüleme

Kodunuz içinde adım adım olarak, betikte değişkenlerin geçerli değerleri görüntüleyebilirsiniz.

### <a name="to-display-the-values-of-standard-variables"></a>Standart değişkenlerin değerleri görüntülemek için

Aşağıdaki yöntemlerden birini kullanın:

- Betik bölmesinde bir araç ipucu değerini görüntülemek için değişkenin üzerine gelin.

- Konsol bölmesinde, tuşuna basın ve değişken adını yazın **ENTER**.

ISE tüm bölmelerde aynı kapsam içinde her zaman olur. Bu nedenle, bir komut dosyası hata ayıklama sırasında kod kapsamında Konsol bölmesinde yazdığınız komutları çalıştırın. Bu değişkenlerin değerleri bulmak ve yalnızca komut dosyasında tanımlanan işlevleri çağırmak için konsol bölmesinde kullanmanıza olanak sağlar.

### <a name="to-display-the-values-of-automatic-variables"></a>Otomatik değişkenlerin değerleri görüntülemek için

Bir komut dosyası hata ayıklama sırasında neredeyse tüm değişkenlerin değerini görüntülemek için yukarıdaki yöntemi kullanabilirsiniz. Ancak, bu yöntemler aşağıdaki otomatik değişkenleri çalışmaz.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Bu değişkenlerin değerini görüntülemek çalışırsanız, hata ayıklayıcı bir iç işlem hattında kullandığı için değildir komut dosyasında değişkeninin değeri değişken değerini alın. Bu sorunu ($_, $Input, $MyInvocation, $PSBoundParameters ve $Args) birkaç değişkenleri aşağıdaki yöntemi kullanarak çalışabilirsiniz:

1. Betik, otomatik değişkeninin değerini yeni bir değişkene atayın.

2. Betik bölmesine yeni değişkenin üzerine geldiğinizde veya Konsol bölmesinde yeni bir değişken yazarak yeni bir değişkenin değerini görüntüler.

Örneğin, betikte $MyInvocation değişkenin değerini görüntülemek için $scriptname gibi yeni bir değişken bir değer atayın ve ardından üzerine gelin veya $scriptname değişkenin değerini görüntülemek için yazın.

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