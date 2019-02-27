---
title: Cmdlet modüllerini kullanarak içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849017"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Modül Kullanarak Cmdlet’i İçeri Aktarma

Bu konuda, ikili modül kullanarak bir Windows PowerShell oturumuna cmdlet'leri içe aktarmayı açıklar.

> [!NOTE]
> Üyeleri modülleri, cmdlet'leri, sağlayıcıları, İşlevler, değişkenler, diğer adlar ve çok daha fazlasını içerebilir. Ek bileşenler, yalnızca cmdlet'lerini ve sağlayıcıları içerebilir.

## <a name="how-to-load-cmdlets-using-a-module"></a>Bir modül kullanarak cmdlet'leri yükleme

1. Cmdlet'ler uygulanan derleme dosyası aynı ada sahip bir modül klasörü oluşturun. Bu yordamda, modül klasöründe oluşturulan `system32` klasör.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Emin olun `PSModulePath` ortam değişkeni, yeni modül klasörün yolunu içerir. Varsayılan olarak, sistem klasörü zaten eklenir `PSModulePath` ortam değişkeni.

3. Cmdlet derleme modülü klasöre kopyalayın.

4. Cmdlet'lerini oturumuna eklemek için aşağıdaki komutu çalıştırın:

   `import-module [Module_Name]`

   Bu yordam, cmdlet'lerinizi test etmek için kullanılabilir. Oturuma derlemedeki tüm cmdlet'ler ekler. Modüller hakkında daha fazla bilgi için farklı türlerdeki modüllerin, modüller ve verilen, bir modül öğelerini kısıtlamak nasıl yük farklı yollarını görmek [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Modülleri yükleme](../module/installing-a-powershell-module.md)