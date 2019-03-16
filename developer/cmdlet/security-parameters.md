---
title: Güvenlik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057138"
---
# <a name="security-parameters"></a>Güvenlik Parametreleri

Aşağıdaki tabloda, sertifika anahtarı ve ayrıcalık bilgilerini belirtmek parametreleri gibi bir işlem için güvenlik bilgileri sağlamak için kullanılan parametreler için işlevselliği ve önerilen adlarını listeler.

|Parametre|İşlevsellik|
|---|---|
|**ACL**<br>Veri türü: Dize|Koruma için bir katalog veya bir Tekdüzen Kaynak Tanımlayıcısı (URI) için erişim denetimi düzeyini belirtmek için bu parametreyi uygulayın.|
|**CertFile**<br>Veri türü: Dize|Kullanıcı şunlardan birini içeren dosyanın adını belirtmek için bu parametreyi uygulayın:<br>Base64 veya Distinguished Encoding Rules (DER) kodlu x.509 sertifikası<br>-En az bir sertifika ve anahtar içeren bir genel anahtar şifreleme standartları (PKCS) #12 dosyası|
|**CertIssuerName**<br>Veri türü: Dize|Bu parametre, kullanıcı bir sertifikayı verenin adını belirtebilir veya kullanıcı bir alt dizesi belirtebilirsiniz böylece uygulayın.|
|**CertRequestFile**<br>Veri türü: Dize|Bir Base64 veya DER kodlu PKCS #10 sertifika isteğini içeren dosyanın adını belirlemek için bu parametreyi uygulayın.|
|**CertSerialNumber**<br>Veri türü: Dize|Sertifika yetkilisi tarafından verilmiş bir seri numarası belirtmek için bu parametreyi uygulayın.|
|**CertStoreLocation**<br>Veri türü: Dize|Kullanıcı sertifika depolama konumunu belirtmek için bu parametreyi uygulayın. Genellikle bir dosya yolu konumdur.|
|**CertSubjectName**<br>Veri türü: Dize|Bu parametre, kullanıcı bir sertifikayı veren belirtebilir veya kullanıcı bir alt dizesi belirtebilirsiniz böylece uygulayın.|
|**CertUsage**<br>Veri türü: Dize|Anahtar kullanımı veya Gelişmiş anahtar kullanımı belirtmek için bu parametreyi uygulayın. Anahtar biraz, biraz, bir nesne tanımlayıcı (OID) maske olarak veya bir dizeyi temsil edilebilir.|
|**Kimlik bilgisi**<br>Veri türü: [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Bu parametre, böylece cmdlet'i otomatik olarak bir kullanıcı adı veya parola girmesini ister uygulayın. Tam bir kimlik bilgisi doğrudan sağlanmazsa, her ikisi için de bir istem görüntülenir.|
|**CSPAdı**<br>Veri türü: Dize|Kullanıcı sertifika hizmeti sağlayıcısı (CSP) adını belirtmek için bu parametreyi uygulayın.|
|**CSPType**<br>Veri türü: Tamsayı|Kullanıcı, CSP türünü belirtmek için bu parametreyi uygulayın.|
|**Grup**<br>Veri türü: Dize|Bu parametre, kullanıcı için erişim ilkeleri koleksiyonunu belirtebilirsiniz böylece uygulayın. Daha fazla bilgi için açıklamasına bakın **asıl** parametresi.|
|**KeyAlgorithm**<br>Veri türü: Dize|Kullanıcı güvenlik için kullanılacak anahtar oluşturma algoritmasını belirtmek için bu parametreyi uygulayın.|
|**AnahtarKapsayıcıAdı**<br>Veri türü: Dize|Kullanıcı anahtar kapsayıcısı adını belirtmek için bu parametreyi uygulayın.|
|**KeyLength**<br>Veri türü: Tamsayı|Bu parametre, kullanıcının anahtar uzunluğunu bit cinsinden belirtebilirsiniz böylece uygulayın.|
|**İşlem**<br>Veri türü: Dize|Bu parametre, kullanıcı korumalı bir nesne üzerinde gerçekleştirilecek bir eylem belirtebilirsiniz böylece uygulayın.|
|**Asıl**<br>Veri türü: Dize|Kullanıcı erişimi için benzersiz bir tanımlanabilen varlık belirtmek için bu parametreyi uygulayın.|
|**ayrıcalık**<br>Veri türü: Dize|Bu parametre, kullanıcının bir cmdlet, belirli bir varlık için bir işlem gerçekleştirmesine gerek sağ belirtebilirsiniz böylece uygulayın.|
|**Ayrıcalıklar**<br>Veri türü: Ayrıcalıkları dizisi|Bu parametre, kullanıcının bir cmdlet, belirli bir giriş için kendi işlemi gerçekleştirmek için gereken hakları belirtebilirsiniz böylece uygulayın.|
|**Rol**<br>Veri türü: Dize|Bu parametre, kullanıcının bir varlık tarafından gerçekleştirilen işlemlerin bir dizi belirtebilirsiniz böylece uygulayın.|
|**SaveCred**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde kullanıcı tarafından daha önce kaydedilen kimlik bilgileri kullanılacak uygulayın.|
|**Kapsam**<br>Veri türü: Dize|Bu parametre, kullanıcının cmdlet'i için korunan nesnelerin grubunu belirtebilirsiniz böylece uygulayın.|
|**SID**<br>Veri türü: Dize|Bu parametre, kullanıcı sorumlu temsil eden benzersiz bir tanımlayıcı belirtebilirsiniz böylece uygulayın.|
|**Güvenilir**<br>Veri türü: SwitchParameter|Bu parametre, böylece parametresi belirtildiğinde güven düzeyleri desteklenir uygulayın.|
|**trustLevel**<br>Veri türü: Anahtar sözcüğü|Kullanıcı desteklenen güven düzeyini belirtmek için bu parametreyi uygulayın. Örneğin, internet, intranet ve fulltrust olası değerler içerir.|

## <a name="see-also"></a>Ayrıca bkz:

[Cmdlet parametreleri](./cmdlet-parameters.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
