---
title: Kaynak parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251209"
---
# <a name="resource-parameters"></a>Kaynak Parametreleri

Aşağıdaki tabloda, kaynak parametreleri için işlevselliği ve önerilen adlarını listeler. Bu parametreler için cmdlet'i sınıf ya da cmdlet'in çalıştığı ana bilgisayar uygulaması içeren derleme kaynakları olabilir.

|Parametre|İşlevsellik|
|---|---|
|**Uygulama**<br>Veri türü: Dize|Bu parametre, kullanıcı bir uygulama belirtebilirsiniz böylece uygulayın.|
|**Derleme**<br>Veri türü: Dize|Kullanıcı bir derlemeyi belirtmek için bu parametreyi uygulayın.|
|**Özniteliği**<br>Veri türü: Dize|Bu parametre, kullanıcının bir öznitelik belirtebilirsiniz böylece uygulayın.|
|**Sınıfı**<br>Veri türü: Dize|Bu parametre, kullanıcının bir Microsoft .NET Framework sınıfı belirtebilirsiniz böylece uygulayın.|
|**Küme**<br>Veri türü: Dize|Bu parametre, kullanıcı bir küme belirtebilirsiniz böylece uygulayın.|
|**Kültür**<br>Veri türü: Dize|Bu parametre, kullanıcının cmdlet'ini çalıştırmak için kullanılan kültür belirtebilirsiniz böylece uygulayın.|
|**Etki alanı**<br>Veri türü: Dize|Kullanıcı etki alanı adını belirtmek için bu parametreyi uygulayın.|
|**Sürücü**<br>Veri türü: Dize|Kullanıcı bir sürücü adı belirtmek için bu parametreyi uygulayın.|
|**Olay**<br>Veri türü: Dize|Kullanıcı bir olay adı belirtmek için bu parametreyi uygulayın.|
|**Arabirimi**<br>Veri türü: Dize|Kullanıcı bir ağ arabirimi adı belirtmek için bu parametreyi uygulayın.|
|**IP adresi**<br>Veri türü: Dize|Bu parametre, kullanıcının IP adresi belirtebilirsiniz böylece uygulayın.|
|**İşi**<br>Veri türü: Dize|Kullanıcı, bir işi belirtmek için bu parametreyi uygulayın.|
|**LiteralPath**<br>Veri türü: Dize|Joker karakterler desteklenmediği durumlarda kullanıcı bir kaynağın yolunu belirtmek için bu parametreyi uygulayın. (Kullanım **yolu** parametre joker karakterleri desteklenir.)|
|**Mac**<br>Veri türü: Dize|Kullanıcı bir ortam erişim denetleyicisi (MAC) adresini belirtmek için bu parametreyi uygulayın.|
|**parentId**<br>Veri türü: Dize|Bu parametre, kullanıcının üst tanımlayıcı belirtebilirsiniz böylece uygulayın.|
|**Yolu**<br>Veri türü: Dize, String]|Joker karakterler desteklendiğinde, kullanıcı bir kaynak yolları belirtmek üzere bu parametreyi uygulayın. (Kullanım **LiteralPath** parametre joker karakterler desteklenmez.) Bu parametre tam destekler, böylece geliştirme öneririz `provider:path` sağlayıcıları tarafından kullanılan sözdizimi. Mümkün olduğu kadar çok sağlayıcıları ile çalışır, böylece onu geliştirme öneririz.|
|**Bağlantı noktası**<br>Veri türü: Tamsayı, dize|Kullanıcı ağ için bir tamsayı değeri veya bağlantı noktası, diğer türler için "biztalk" gibi bir dize değeri belirtmek için bu parametreyi uygulayın.|
|**Yazıcı**<br>Veri türü: Tamsayı, dize|Bu parametre, kullanıcı kullanmak cmdlet için yazıcının belirtebilirsiniz böylece uygulayın.|
|**Boyutu**<br>Veri türü: Int32|Bu parametre, kullanıcının bir boyut belirtebilirsiniz böylece uygulayın.|
|**TID**<br>Veri türü: Dize|Bu parametre, kullanıcı cmdlet'i için işlem tanımlayıcısını (TID) belirtebilirsiniz böylece uygulayın.|
|**Tür**<br>Veri türü: Dize|Bu parametre, kullanıcının kaynak üzerinde çalışacağı türünü belirtebilirsiniz böylece uygulayın.|
|**URL**<br>Veri türü: Dize|Bu parametre, kullanıcı bir Tekdüzen Kaynak Konum Belirleyicisi (URL) belirtebilirsiniz böylece uygulayın.|
|**Kullanıcı**<br>Veri türü: Dize|Kullanıcı adlarının veya başka bir kullanıcının adını belirtmek için bu parametreyi uygulayın.|

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
