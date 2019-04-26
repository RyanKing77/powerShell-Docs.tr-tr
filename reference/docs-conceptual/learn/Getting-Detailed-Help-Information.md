---
ms.date: 08/27/2018
keywords: PowerShell cmdlet'i
title: Ayrıntılı Yardım Bilgisi Alma
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086536"
---
# <a name="getting-detailed-help-information"></a>Ayrıntılı yardım bilgisi alma

PowerShell, PowerShell kavramlarını ve PowerShell dil açıklayan ayrıntılı yardım makaleleri içerir. Pek çok işlev ve betik ve her cmdlet sağlayıcısı için Yardım makaleleri de vardır.

Komut isteminde bu Yardım makaleleri görüntüleyebilir veya görünümü en son güncelleştirilmiş aşağıdaki makalelerde sürümlerini [PowerShell](/powershell/scripting/overview) belgelerine bakın.

## <a name="getting-help-for-cmdlets"></a>Cmdlet'leri için Yardım alma

PowerShell cmdlet'leri hakkında Yardım almak için kullanın [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet'i. Örneğin, Yardım almak için `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem
```

veya

```powershell
Get-ChildItem -?
```

Hatta, Get-Help cmdlet'i hakkında Yardım alabilirsiniz. Örneğin:

```powershell
Get-Help Get-Help
```

Tüm cmdlet listesi Yardım makaleleri oturumunuzda almak için şunu yazın:

```powershell
Get-Help -Category Cmdlet
```

Bir kerede bir sayfa her Yardım makalesinin görüntülemek için kullanın `help` işlevi veya diğer adıyla `man`.
Örneğin, Yardım için görüntülenecek `Get-ChildItem` cmdlet'i, türü

```powershell
man Get-ChildItem
```

veya

```powershell
help Get-ChildItem
```

Ayrıntılı bilgi görüntülemek için kullanın **ayrıntılı** parametresinin `Get-Help` cmdlet'i. Örneğin, hakkında ayrıntılı bilgi almak için `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem -Detailed
```

Yardım makalesi tüm içeriği görüntülemek için kullanın **tam** parametresinin `Get-Help` cmdlet'i. Örneğin, Yardım makalesi için tüm içeriği görüntülemek için `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem -Full
```

Almak için Yardım kullanımı bir cmdlet parametreleri hakkında ayrıntılı **parametre** parametresinin `Get-Help` cmdlet'i. Örneğin, almak için ayrıntılı yardım almak için tüm parametreleri `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Bir Yardım makalesinde yalnızca örnekleri görüntülemek için kullanın **örnekler** parametresinin `Get-Help`.
Örneğin, Yardım makalesi için yalnızca örnekleri görüntülemek için `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem -Examples
```

Yazdığınız cmdlet'leri için Yardım makaleleri yazma hakkında daha fazla bilgi için bkz: [yazma Cmdlet Yardım nasıl](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Kavramsal Yardım alma

`Get-Help` Cmdlet ayrıca görüntüler kavramsal makaleleri hakkında bilgi PowerShell, PowerShell dilinin hakkında makaleler de dahil olmak üzere. Kavramsal Yardım makaleleri başlamak about_line_editing gibi "about_" ön ekine sahip. (Makale adı İngilizce PowerShell bile İngilizce olmayan sürümleri üzerinde girilmesi gerekir.)

Kavramsal makaleleri listesini görüntülemek için şunu yazın:

```powershell
Get-Help about_*
```

Belirli bir Yardım makalesi görüntülemek için örneğin makale adı yazın:

```powershell
Get-Help about_command_syntax
```

Parametreleri `Get-Help`, gibi **ayrıntılı**, **parametre**, ve **örnekler**, kavramsal Yardım makaleleri görüntülenmesini üzerinde hiçbir etkisi yoktur.

## <a name="getting-help-about-providers"></a>Sağlayıcılar hakkında Yardım alma

`Get-Help` Cmdlet'i, PowerShell sağlayıcıları hakkında daha fazla bilgi görüntüler. Sağlayıcı için Yardım almak için şunu yazın `Get-Help` ardından sağlayıcı adı. Örneğin, kayıt defteri sağlayıcısı için Yardım almak için şunu yazın:

```powershell
Get-Help registry
```

Sağlayıcı listesi Yardım makaleleri oturumunuzda almak için yazın

```powershell
Get-Help -Category provider
```

Parametreleri `Get-Help`, gibi **ayrıntılı**, **parametre**, ve **örnekler**, sağlayıcı Yardım makaleleri görüntülenmesini üzerinde hiçbir etkisi yoktur.

## <a name="getting-help-about-scripts-and-functions"></a>Betik ve işlevlerde hakkında Yardım alma

Birçok betik ve işlevlerde PowerShell'de Yardım makaleleri sahip. Kullanım `Get-Help` betik ve işlevlerde kullanılan Yardım makaleleri görüntülemek için cmdlet'i.

Bir işlev için Yardım görüntülemek üzere şunu yazın `Get-Help` ardından işlevi adı. Örneğin, Yardım almak için `Disable-PSRemoting` işlev, yazın:

```powershell
Get-Help Disable-PSRemoting
```

Bir komut için Yardım görüntülemek için betik dosyasının yolunu yazın. Betiği, Path ortam değişkeninde listelenen bir yol değil, tam yolu kullanmanız gerekir.

Örneğin, C: "TestScript.ps1" adlı bir komut dosyası varsa\\Yardım makalesi betik, tür için görüntülenecek PS Test dizini:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Betik ve işlevi için cmdlet Yardım iş görüntülemek için tasarlanmış parametreleri, çok yardımcı olur. Programını çalıştırdığınızda işlev ve betik Yardımı ancak gösterilmez `Get-Help *`.

Yardım makaleleri işlev ve betik yazma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Çevrimiçi Yardım alma

Çevrimiçi Yardım makaleleri görüntüleme konusunda yardım almak için en iyi yollarından biridir. Çevrimiçi makaleler, güncelleştirmek ve en güncel içeriği sağlamak daha kolay.

Çevrimiçi Yardım almak için kullanın **çevrimiçi** parametresinin `Get-Help` cmdlet'i. Sağlayıcı Yardım dahil olmak üzere PowerShell ile gelen tüm Yardım makaleleri ve kavramsal (hakkında) Yardım makaleleri çevrimiçi kullanılabilir [PowerShell](/powershell/scripting/powershell-scripting) belgeleri.

> [!NOTE]
> Kullanamazsınız **çevrimiçi** kavramsal parametresiyle (about_\*) ya da sağlayıcı Yardım makaleleri.
> Çevrimiçi Yardım, isteğe bağlı olduğundan her cmdlet, işlev veya betiği için çalışmaz.

Örneğin, hakkında Yardım makalesi'nın çevrimiçi sürümünü almak için `Get-ChildItem` cmdlet'i, türü:

```powershell
Get-Help Get-ChildItem -Online
```

Makalede, PowerShell varsayılan tarayıcınızda açılır. Çevrimiçi Yardım için Yardım makalesine destekleniyorsa, Yardım makalesi URL'sini de görüntüleyebilirsiniz. URL, bir Yardım makalesinin ilgili bağlantılar bölümünde görüntülenir.

Örneğin, Add-Computer cmdlet'ın çevrimiçi sürümünü URL'sini görmek için aşağıdakileri yazın:

```powershell
Get-Help Add-Computer
```

Makalenin ilgili bağlantılar bölümüne ilk satırı aşağıda gösterilmiştir.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Çevrimiçi destek için Yardım makaleleriniz sağlama hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Ayrıca bkz.

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
