---
title: Nasıl bir bakın bölümü için sağlayıcı Yardım konusunun da ekleyin. | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848457"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Sağlayıcı Yardım Konusuna Ayrıca Bakın Bölümü Ekleme

Bu bölümde doldurmak açıklanmaktadır **ayrıca** sağlayıcısı Yardım konusunun bölümü.

**Ayrıca** bölüm sağlayıcısıyla ilgili ya da daha iyi anlamanıza ve sağlayıcıyı kullanacak kullanıcı yardımcı olabilecek konuların listesini oluşur. Konu listesi cmdlet yardımını, sağlayıcı içerebilir ve kavramsal ("hakkında") Windows PowerShell Yardım konuları. Ayrıca, kitaplar, inceleme ve geçerli sağlayıcı Yardım konusunun çevrimiçi sürümünü de dahil olmak üzere çevrimiçi konuları başvuruları de içerebilir.

Çevrimiçi konulara bakın URI veya bir arama terimi düz metin biçiminde belirtin. `Get-Help` Cmdlet'i bağlantı etmez veya yeniden yönlendirmek için konularına listesinde. Ayrıca, `Online` parametresinin `Get-Help` cmdlet'i sağlayıcı yardımıyla çalışmaz.

Ayrıca bkz. bölümünde oluşturulur `RelatedLinks` öğesi ve içerdiği etiketler. Aşağıdaki XML etiket ekleme işlemi gösterilmektedir.

### <a name="to-add-see-also-topics"></a>"Ayrıca bkz:" konuları eklemek için

1. İçinde *AssemblyName*içinde help.xml .dll dosyası `providerHelp` öğe, Ekle bir `RelatedLinks` öğesi. `RelatedLinks` Öğesi içindeki son öğeden olmalıdır `providerHelp` öğesi. Yalnızca bir `RelatedLinks` öğesi her sağlayıcısı Yardım konusunda izin verilir.

   Örneğin:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Her bir konuda için **ayrıca** bölümünde, içinde `RelatedLinks` öğesi ekleme bir `navigationLink` öğesi. Ardından, her `navigationLink` öğesi, bir tane ekleyin `linkText` öğesi ve bir `uri` öğesi. Kullanmıyorsanız, `uri` öğesi ekleyebilirsiniz, boş bir öğe olarak (\<URI / >).

   Örneğin:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Konu adı arasında `linkText` etiketler. Bir URI sağlıyorsanız arasında yazın `uri` etiketler. Geçerli sağlayıcı Yardım konusunun çevrimiçi sürümünü arasında belirtmek için `linkText` etiketler, tür "çevrimiçi sürüm:" yerine konu adı. Genellikle, "çevrimiçi sürüm:" ilk konu ayrıca konu listesindeki bir bağlantıdır.

   Aşağıdaki örnek, üç ayrıca konuları içerir. İlk geçerli konuyu çevrimiçi sürümüne bakın. İkinci bir Windows PowerShell cmdlet Yardım konusunun için ifade eder. Üçüncü için başka bir çevrimiçi konusuna ifade eder.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```