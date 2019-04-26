---
title: Bir Windows PowerShell modülü yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082065"
---
# <a name="writing-a-windows-powershell-module"></a>Windows PowerShell Modülü Yazma

Bu belge, Yöneticiler, betik geliştiriciler ve paketlemek ve kendi Windows PowerShell cmdlet'leri dağıtmak için gereken cmdlet'i geliştiriciler için yazılır. Windows PowerShell modüllerini kullanarak, paketleyebilir ve Windows PowerShell çözümlerinizi olmadan derlenmiş bir dili kullanarak dağıtın.

Windows PowerShell modülleri bölüme etkinleştirmek, düzenlemek ve Windows PowerShell kodunuzu müstakil, yeniden kullanılabilir birimler halinde soyut. Yeniden kullanılabilir bu birimleri ile kolayca modüllerinizi doğrudan diğer kişilerle paylaşabilirsiniz. Betik geliştiriciyseniz de özel betik tabanlı uygulamalar oluşturmak amacıyla üçüncü taraf modülleriyle paketleyebilirsiniz. Modüller, benzer modüllerine Perl ve Python gibi diğer komut dosyası dilleri içinde yeniden kullanılabilir, yeniden dağıtılabilir bileşenleri ile yeniden paketleyin ve birden çok bileşeni için soyut etkinleştirme avantajını kullanan üretime hazır betik çözümlerle özel çözümler oluşturun.

Konumunda, en temel, Windows PowerShell bir modül bir .psm1 dosyasında kaydedilen herhangi bir geçerli Windows PowerShell komut dosyası kodu kabul. PowerShell, bir modül olarak herhangi bir ikili cmdlet'i derleme da otomatik olarak değerlendirir. Ancak, bütün bir çözüm gruplamak için bir modül (veya daha açık belirtmek gerekirse bir modül bildirimi) da kullanabilirsiniz. Windows PowerShell modülleri için genel kullanımlar aşağıdaki senaryolar açıklanmaktadır.

### <a name="libraries"></a>Kitaplıkları

Modüller, paket ve ortak görevleri gerçekleştirmek işlevlerin cohesive kitaplıkları dağıtmak için kullanılabilir. Genellikle, bu işlevlerin adlarını yansıtmak için kullanılan yaygın görev bir veya daha fazla isimleri paylaşın. Genel ve özel üyelere sahip olabilir, bu işlevler de .NET Framework sınıfları benzer olabilir. Örneğin, bir kitaplık, dosya aktarımları için bir işlevler kümesi içerebilir. Bu durumda, görevinin yansıtan isim "dosya" olabilir

### <a name="configuration"></a>Yapılandırma

Modüller, bazı cmdlet'ler, sağlayıcıları, İşlevler ve değişkenler ekleyerek ortamınızı özelleştirmek için kullanılabilir.

### <a name="compiled-code-development-and-distribution"></a>Derlenmiş kod geliştirme ve dağıtma

Cmdlet ve sağlayıcı geliştiriciler, test ve ek bileşenler oluşturmaya gerek kalmadan kendi derlenmiş kod dağıtmak için modülleri kullanabilir. Oluşturma ve ek bileşenler kaydetme gerek kalmadan bir modül (ikili Modülü) olarak derlenmiş kodunu içeren bütünleştirilmiş kodun aktarabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü anlama](./understanding-a-windows-powershell-module.md)

[Modul Skriptu Powershellu yazma](./how-to-write-a-powershell-script-module.md)

[Bir ikili PowerShell modülü yazma](./how-to-write-a-powershell-binary-module.md)

[Bir PowerShell modül bildirimi yazma](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[PSModulePath yükleme yolunu değiştirme](./modifying-the-psmodulepath-installation-path.md)

[Bir PowerShell modülü içeri aktarma](./importing-a-powershell-module.md)

[Bir PowerShell modülü yükleniyor](./installing-a-powershell-module.md)
