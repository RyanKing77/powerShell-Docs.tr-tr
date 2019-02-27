---
title: Cmdlet adı ve özeti için Cmdlet Yardım konusunun ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850893"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Cmdlet Yardım Konularına Cmdlet Adı ve Özet Ekleme

Bu bölümde, cmdlet yardımına adı ve özeti bölümlerinde gösterilen içeriği eklemeyi açıklar. Yardım dosyasında, bu içerik, her cmdlet için komut düğümüne eklenir.

> [!NOTE]
> Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için. Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Cmdlet adı ve doğrulanır eklemek için

- Cmdlet Yardım cmdlet'i için iki açıklama görüntüleyebilirsiniz. İlk özeti denir kısa bir açıklama açıklamasıdır. İçinde açıklanan daha ayrıntılı bir açıklama ikinci açıklamasıdır [ayrıntılı bir açıklaması için Cmdlet Yardım konusunun ekleme](./how-to-add-a-cmdlet-description.md). Hem bu açıklamalar, tek bir paragraf olarak yazılmalıdır.

- Cmdlet adı özeti tekrarlamayın. Cmdlet Get-Server'ın bir sunucu alır kullanıcı bildiren kısa, ancak değil bilgilendirici değildir. Bunun yerine, eş anlamlı sözcükler kullanın ve Ayrıntılar için bir açıklama ekleyin.

  Örnek: "Yerel veya uzak bir bilgisayarı temsil eden bir nesne alır."

- "Get", "oluşturma" ve "içinde doğrulanır Değiştir" gibi basit fiilleri kullanın. "Set", belirsiz olduğundan ve başvurmaktan sözcükler gibi "değiştirin." kullanmaktan kaçının

  Örnek: "Bir dosyada Authenticode imzası hakkındaki bilgileri alır."

- İçinde etkin ses yazın. Örneğin, "TimeSpan nesne kullan …" "TimeSpan nesne için kullanılabilecek olandan..." çok nettir

- Nesneleri Al cmdlet'leri anlatırken "display" fiili kaçının. Windows PowerShell cmdlet'i verileri görüntüler ancak kullanıcılar cmdlet verisini görüntülenmeyebilir .NET Framework nesneleri döndüren kavramı tanıtmak önemlidir. Görüntü vurgulamak, kullanıcı cmdlet diğer birçok yararlı özellik ve görüntülenmez yöntemleri döndürmüş, farkına varmazsınız.

## <a name="see-also"></a>Ayrıca bkz:

 [Windows PowerShell SDK'sı](../windows-powershell-reference.md)