---
title: Modüller kullanılarak cmdlet 'Leri Içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215268"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Modül Kullanarak Cmdlet’i İçeri Aktarma

Bu makalede, ikili bir modül kullanılarak cmdlet 'leri bir PowerShell oturumuna nasıl içeri aktarılacağı açıklanır.

> [!NOTE]
> Modül üyeleri cmdlet 'leri, sağlayıcıları, işlevleri, değişkenleri, diğer adları ve çok daha fazlasını içerebilir. Ek bileşenler yalnızca cmdlet 'ler ve sağlayıcılar içerebilir.

## <a name="how-to-load-cmdlets-using-a-module"></a>Modül kullanarak cmdlet 'leri yükleme

1. Cmdlet 'lerinin uygulandığı derleme dosyasıyla aynı ada sahip bir modül klasörü oluşturun. Bu yordamda modül klasörü Windows `system32` klasöründe oluşturulur.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. `PSModulePath` Ortam değişkeninin yeni modül klasörünüzün yolunu içerdiğinden emin olun. Varsayılan olarak, sistem klasörü `PSModulePath` ortam değişkenine zaten eklenir. Görüntülemek `PSModulePath`için şunu yazın: `$env:PSModulePath`.

1. Cmdlet derlemesini modül klasörüne kopyalayın.

1. Modülün kök klasörüne bir modül bildirim`.psd1`dosyası () ekleyin. PowerShell, modülünüzü içeri aktarmak için modül bildirimini kullanır. Daha fazla bilgi için bkz. [PowerShell modülü bildirimi yazma](../module/how-to-write-a-powershell-module-manifest.md).

1. Cmdlet 'leri oturuma eklemek için aşağıdaki komutu çalıştırın:

   `Import-Module [Module_Name]`

   Bu yordam, cmdlet 'lerinizi test etmek için kullanılabilir. Derlemedeki tüm cmdlet 'leri oturuma ekler. Modüller hakkında daha fazla bilgi için bkz. [Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell modülü bildirimi yazma](../module/how-to-write-a-powershell-module-manifest.md)

[PowerShell modülünü içeri aktarma](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Modüller yükleniyor](../module/installing-a-powershell-module.md)

[PSModulePath yükleme yolunu değiştirme](../module/modifying-the-psmodulepath-installation-path.md)

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)
